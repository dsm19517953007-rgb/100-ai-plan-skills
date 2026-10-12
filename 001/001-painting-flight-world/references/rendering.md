# 确定时间渲染、交互与媒体交付

这些约定从 001 的实际源码提取，适合在新工程实现同类接口。本技能包不携带 001 源码；下列 npm 命令是已有同结构工程的复现记录。新工程应提供等价命令或写明自己的入口。

## 工程复现记录

001 使用 TypeScript、Three.js 与 Vite；`package-lock.json` 固定依赖。其 `package.json` 记录 Three.js 0.186.1、TypeScript 5.9.3、Vite 7.3.1，不表示这些是最新版本。

```powershell
# 在具备原工程结构的项目根目录执行
npm ci
npm run dev
npm run build
npm run check
node tools/audio.mjs
npm run render
```

`build` 执行 `tsc --noEmit && vite build && node tools/package.mjs`，生成 `dist/` 和内联脚本、样式、晨空纹理的独立 HTML。检查真正的 `file://` 打开，不能只测试开发服务。

原工程的检查、取帧和导出需要 Playwright 浏览器；可在新环境安装 Playwright 与 Chromium，或使用工具支持的已安装浏览器。FFmpeg 用于编码，FFprobe 用于读取媒体规格。`tools/camera-audit.mjs` 直接导入 TypeScript，相同复现方式需要 Node.js 24+。工具依赖应在实际项目中声明，避免把本机运行环境当成通用条件。

## 渲染接口契约

001 页面的查询参数：

```text
/?capture=1&width=1920&height=1080&t=24&quality=high
```

捕获模式固定画布尺寸、像素比例为 1，停止自动时间推进；`t` 指定秒数。页面只在所有几何、纹理、后处理和首帧就绪后发布 `ready`。

001 的实际调用：

```javascript
const api = window.__MONET__;
if (!api?.ready) throw new Error('等待三维世界初始化');
api.setMode('cinematic');
api.renderAt(24);
const state = api.getState();
```

| 方法 | 行为 |
|---|---|
| `renderAt(seconds)` | 按指定时间更新相机、世界、后处理并同步绘制；供导出取帧使用 |
| `setTime(seconds)` | 修改当前时间，按当前模式更新 |
| `setMode(mode)` | 实际支持 `cinematic`、`free`、`painting`，另兼容 `auto` 与 `overview` 别名 |
| `getState()` | 返回时间、时长、模式、画质、相机、尺寸、世界统计及渲染信息 |

新工程可以使用自己的 API 名称，但要保证：捕获时动画由传入秒数决定，绘制完成后再读取 canvas，资源未就绪不取帧。随机几何采用固定种子；避免逐帧调用随机数导致重复导出变化。

## 逐帧导出方式

001 的 `tools/render.mjs` 对每帧调用 `renderAt(i / fps)`，再读取 canvas JPEG，以 `image2pipe` 送入 FFmpeg。编码器有背压时等待 `drain`，结束后关闭输入并等待成功退出；浏览器报错或编码失败应中止本次导出。

```javascript
// 实现思路；page、encoder 与 ready 检查应由当前工程初始化。
const frameCount = Math.round(duration * fps);
for (let i = 0; i < frameCount; i++) {
  const jpegBase64 = await page.evaluate((time) => {
    window.__MONET__.renderAt(time);
    return document.querySelector('canvas')
      .toDataURL('image/jpeg', 0.96).split(',')[1];
  }, i / fps);
  // 将 Buffer.from(jpegBase64, 'base64') 写入编码管道，处理背压。
}
```

时长、帧率与镜头路径保持一致。001 的 72 秒、30 fps 对应 2160 帧；`DURATION` 改动要同步镜头、音频、导出与验收。原渲染工具支持 `WIDTH`、`HEIGHT`、`FPS`、`DURATION`、`OUTPUT_NAME`、`MONET_URL` 与 `FFMPEG` 环境变量；默认输出目录为工程 `outputs/`。

001 用 H.264、CRF 18、yuv420p、`+faststart`，将全范围 JPEG 转成 limited-range BT.709 后编码。编码参数按画面与发布用途选择，并核对解码后的实际颜色。交互世界和 MP4 分别交付；需要动态影片时，网页或静帧轮播不能替代成品视频。

## 核心检查

**交互**：独立打开与素材加载、播放/暂停、时间轴、返回自动镜头、自由飞行、升降、截图、移动布局。暂停不推进时间，静止视图不重复重绘；低帧率下按实际经过时间推进镜头。自由飞行避障能力按实现如实描述。

**镜头**：按适合运动速度的频率采样位置、方向、注视距离、角速度与闭环；对关键通道检查实体间距。把检查对象与时间范围记录清楚，再实际看近景掠过、高潮回转、天空外围和结尾。数值平滑不能证明美术与节奏合格。

**最终媒体**：FFprobe 读取实际视频/音频编码、帧率、分辨率、时长、帧数和声道；用 FFmpeg 完整解码。示例命令在当前工作目录执行：

```powershell
ffprobe -v error -show_streams -show_format -of json "final.mp4"
ffmpeg -hide_banner -nostdin -v error -xerror -i "final.mp4" -map 0:v:0 -map 0:a:0 -f null NUL
```

无音频交付时省去音频 map；其他系统用其空输出目标替换 `NUL`。抽取最终 MP4 的代表帧，确认真实镜头运动、画面颜色与预览一致；试听开场、高潮、结尾并检查同步。完成验收后写报告，记录当前文件名、真实规格与实际检查结果。

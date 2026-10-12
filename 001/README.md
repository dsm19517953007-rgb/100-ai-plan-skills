# 001 · AI制作莫奈日出印象3D世界

已发布可复用技能：[001-painting-flight-world](001-painting-flight-world/SKILL.md)。

把绘画的构图、标志元素和笔触转成可进入的三维空间，组织自由飞行、连续运镜、原创配乐与动态 MP4 交付。001 案例记录莫奈《日出印象》从第一版到第二版的真实改进过程。

## 下载和安装

[只下载001技能ZIP](https://github.com/dsm19517953007-rgb/100-ai-plan-skills/releases/download/001-v1.0.0/001-painting-flight-world-skill.zip)，解压后得到 `001-painting-flight-world` 目录。

将该目录放入自己 Codex 用户目录下的 `.codex/skills/`，或已自定义的 `CODEX_HOME/skills/`。也可以让支持 Agent Skills 的工具直接读取包内 `SKILL.md`。

在新对话中调用 `$001-painting-flight-world`，提供画作名或参考图、目标空间体验和交付要求。例如：

> 用 $001-painting-flight-world 把我提供的绘画改编为可以自由飞行的原创三维世界，保留标志元素和画派笔触，设计连续镜头，交付可运行作品及动态 MP4。

## 包内内容

- `SKILL.md`：识别绘画、空间与笔触转译、实现、运镜、导出和验收流程。
- `agents/openai.yaml`：技能显示与调用配置。
- `references/prompts.md`：任务、反馈与生成输入示例。
- `references/rendering.md`：确定时间渲染接口、逐帧导出和交互检查。
- `references/music-and-sources.md`：原创配乐方法与参考来源。
- `references/001-case-study.md`：001 实际改进、验收证据与适用范围。

这是方法与轻量案例包；复做时由 Agent 根据新输入创建工程。原作品工程、视频和参考媒体保存在本地，不是这个下载包的依赖。其他绘画需要重新进行画面、交互及媒体验收。

技能包共 6 个纯文本文件，原始大小 25,533 字节。已通过技能格式与包内链接检查，不包含媒体、账号密钥或本机绝对路径。

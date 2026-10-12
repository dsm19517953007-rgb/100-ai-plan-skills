# 可复用任务与反馈 Prompt

以下是从 001 目标与修改过程整理的模板，不是逐字用户对话。替换作品、输出目录和交付规格后使用。

## 最短可用输入

```text
把【绘画名称或参考图】改编成能飞入、自由探索的原创三维世界。保留【标志元素】，按其画派组织有方向、有厚度的笔触和近中远景，新增空间共享原画的色彩与形体语言。设计自动运镜与自由飞行，先看开场、近景、俯瞰和高潮真实镜头，再导出【时长、分辨率】动态 MP4。交互作品、可编辑源码、素材来源与制作记录保存到【输出目录】。
```

## 详细输入结构

```text
参考对象：【作品名、作者、参考图或可信页面】。
目标体验：先认出原画，再进入近景、沿空间通道穿行、抬升揭示世界，最后回收主题。空间尺度来自近物掠过、连续视差和层次揭示。
必须保留：【主体、光源、标志物及它们的构图关系】。
艺术基准：【大面积底色、少量焦点色、边缘与笔触特征】。笔触要明确方向、尺度、曲率、厚度、密度和成簇关系；近看与侧看都能读到体积。
创作自由：【可延伸的画外空间和新增形体】。新增结构与原画共享调色、材质、笔触和尺度；与历史事实分开记录。
镜头与交互：【自动镜头时长与章节】；自由飞行支持移动、转向、升降、速度和返回自动模式。画面有清楚的观看对象、连续朝向和可通行空间。
实现与交付：使用当前可运行工具，建立真实三维近中景；远景天幕可以单独生成并记录输入。交付独立交互作品、可编辑源码、动态 MP4、来源记录和复现说明。
评阅：先查看代表镜头，修改美术后冻结核心工程；分别记录画面、功能与媒体检查。最终规格以实际文件和完整音画解码为准，用户对成品的判断单独记录。
输出目录：【用户指定目录】。
```

## 001 的具体创作示例

```text
把莫奈《日出印象》变成能飞进去的三维港湾。橙红日轮和断续倒影作方向锚点，小舟与船夫提供尺度，左右港岸、桅杆、吊机、烟囱和晨雾形成层次。冷灰蓝与青绿占大面积，暖色集中在太阳和反射。
让不对称、有脊线和厚度的短笔触沿水纹、云流、港岸及巨大卷曲颜料潮汐排列，用切向、法向、曲率和密度梯度形成体积。近中远景都有内容，中央留下通道。
镜头从辨认原画开始，贴水掠船、穿桅杆、抬升看港湾、进入颜料潮汐，最后回望日轮。目标 72 秒自动运镜，并保留自由飞行。先看真实关键镜头，再输出 1080p MP4。
```

## 把审美反馈落到可执行修改

```text
现在中景太空。保持太阳与前景小舟的关系，在航道两侧增加错落船群、码头和桅杆；近处清楚，远处低对比，中央保留通行空间。先看贴水和俯瞰镜头。
```

```text
现在橙色占比太大。恢复冷灰蓝和青绿的大面积底色，把暖橙集中到太阳、碎光及少量引导笔触，检查开场与高潮的焦点是否清楚。
```

```text
港口像规整模型，笔触也零散。用重叠、错落色块软化轮廓，让短笔触沿大形体流向成簇排列；近处增加厚度和遮挡，远处降低对比。分别给我正面、近看和侧面真实画面。
```

```text
高潮回转突然转头。检查注视点是否靠近或穿过相机，连续插值位置与视线方向，再按场景尺度生成注视点。采样转角与实体间距，随后实际预览回转段的遮挡和节奏。
```

```text
画面已确认，请按真实镜头写原创轻音乐：设计短动机、和声与渐强收束，保留乐谱、分轨和音源来源。合入最终 MP4 后检查音轨、完整解码、响度与峰值，并试听开场、高潮和结尾。
```

## 远景晨空生成输入

001 实际使用的英文天幕生成 Prompt（保留完整创作约束；用于远景纹理）：

```text
Asset type: painterly environment sky texture for a real 3D Monet-inspired harbor, wide panorama 2:1.
Primary request: create a masterfully beautiful oil-painted DAWN SKY only, with densely textured luminous clouds, inspired by the broken-color and atmospheric brushwork of Claude Monet's Impression, Sunrise. The scene will be a sky dome behind actual 3D harbor geometry.
Composition: very wide horizontal 2:1 image. Lower third is misty pale warm gray/celadon atmosphere toward a soft distant horizon (no sea). Upper sky layers of long sweeping clouds, subtle diagonal flows and softly curling billows. Center-right luminous glowing apricot/pale gold opening in the cloud banks (no actual sun disk, the 3D scene adds sun). Left and outer top corners deeper cobalt/indigo/blue-teal, yet sufficiently luminous. Rich but restrained teal, blue-violet and gray-green air with coral-peach light in small areas. Balanced spacious composition with several flowing painterly cloud layers at different scales. Lower edge fades into diffuse warm mist for blending. Edges left/right visually similar for wraparound.
Style: sophisticated museum-quality oil painting; closely spaced short visible interwoven directional palette-knife marks, impasto ridges, scumbled overpaint, beautiful color variation inside every cloud. Poetic and immersive atmospheric morning, epic scale yet quiet. Deep blue contrasts against warm rose gold luminous edges. Not generic computer gradient. Subtle visible linen canvas under the paint, tactile textured pigments.
Constraints: no boats, harbor, buildings, water, islands, trees, mountains, people, text, borders, stars, moon or sun disk. No photograph, no plastic cartoon 3D render, no flat poster shapes, no psychedelic rainbow. Output intended as an image texture, no labels.
```

此素材由内置图像生成工具于 2026-10-11 生成。新的纹理仍需实际检查接缝、地平线、曝光与几何笔触的比例。

# 100个AI计划skill

把已完成的 AI 创作过程整理成可复用的 Agent Skills。每期独立一个编号目录，按需下载和使用。

## 已发布技能

001「AI制作莫奈日出印象3D世界」已发布：[查看技能](001/) · [单期ZIP](https://github.com/dsm19517953007-rgb/100-ai-plan-skills/releases/download/001-v1.0.0/001-painting-flight-world-skill.zip)。002–100 尚未制作，目录中仅有占位说明。

只有作品制作完成、经过作者确认的流程才会发布为技能。选题和制作顺序以实际完成内容为准。

## 按期下载

这个仓库只保存技能、必要脚本和文字索引，视频、完整工程与生成素材分别归档在本地。无需下载整个作品素材库。

可以打开对应的编号目录查看文件；也可以用 Git 只检出一期：

```bash
git clone --filter=blob:none --sparse https://github.com/dsm19517953007-rgb/100-ai-plan-skills.git
cd 100-ai-plan-skills
git sparse-checkout set 001
```

将最后一行的 `001` 替换为需要的期数即可。已发布技能的单期 ZIP 下载会列在对应目录说明中。

## 使用方式

每个已发布目录会包含独立技能包，其中 `SKILL.md` 是入口。按各期说明安装技能，准备输入素材，再运行流程。脚本依赖和输出检查以该期技能说明为准。

## 计划索引

见 [001–100期索引](INDEX.md)。占位目录不代表已完成，也不包含可执行技能。

# lany-banner-skill

为 Lany 小生设计或改版 X 主页 Banner，沿用已确认头像、品牌色和像素媒介，表达账号定位并校验头像遮挡及不同屏宽的裁切。用于主页横幅，不用于文章封面。

## 独立仓库安装

本仓库包含 `lany-banner` 技能及其参考资料与资源，支持独立安装。依赖可读取 SKILL.md 的 Agent；实际生图需要宿主提供图片生成工具。

```sh
git clone https://github.com/LanyXiaosheng/lany-banner-skill.git ~/.codex/skills/lany-banner
```

若目标目录已存在，请先检查其中的自定义内容。安装后重新加载技能，调用 `$lany-banner`。完整工作流见 [SKILL.md](SKILL.md)。

来源：[lany-skills/lany-banner](https://github.com/LanyXiaosheng/lany-skills/tree/master/lany-banner)。技能名称保持不变。

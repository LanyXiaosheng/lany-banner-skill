# Lany Banner

为 Lany 小生制作 X 主页横幅：复用确认过的头像，整理名称与内容方向，安排人物、文案和头像遮挡区。默认画布为 **1500×500（3:1）**，实际发布前检查当前主页在桌面和手机上的裁切。

适合首次设置主页、调整账号定位、替换旧横幅。文章封面请使用 [lany-cover-skill](https://github.com/LanyXiaosheng/lany-cover-skill)。

## 安装与更新

需要能读取本地 Skill 的 Agent；以下为 Codex 本地安装示例。仓库名带 `-skill`，实际调用名为 `$lany-banner`。

```sh
mkdir -p ~/.agents/skills
git clone https://github.com/LanyXiaosheng/lany-banner-skill.git ~/.agents/skills/lany-banner
```

按照 [Codex 官方技能文档](https://learn.chatgpt.com/docs/build-skills)，用户级技能目录为 `~/.agents/skills/`，项目级可放在 `.agents/skills/`。安装后应自动发现；未显示时重启 Codex。若已有 `~/.codex/skills/lany-banner` 且当前客户端能够加载，请沿用该副本，避免重复安装同名技能。其他 Agent 按其技能目录规则放入完整仓库，并让它读取 `SKILL.md`。

更新前先检查本地修改；有修改时先提交或备份，再拉取。以下路径要与实际安装位置一致：

```sh
git -C ~/.agents/skills/lany-banner status --short
git -C ~/.agents/skills/lany-banner pull --ff-only
```

仓库包含工作流和资源，不自带生图服务或模型凭据。只读方案/提示词可以直接使用；实际生图取决于宿主已提供的图片生成能力。

## 第一次使用

把当前头像附到对话中，复制下面的请求。文案与路径按实际项目修改：

```text
使用 $lany-banner，为我的 X 主页制作横幅。
身份参考：本次附上的已确认头像。
名称：Lany 小生。
内容方向：AI 工具实践与创作记录。
画布：1500×500。
项目目录：当前项目；slug 使用 x-profile。
沿用黑色、暖白与 #D8FF00 的品牌体系，保持头像人物身份。
请生成正式图片，保存提示词与源图，并提供头像遮挡和窄屏裁切检查结果。
```

### 只要布局方案

```text
使用 $lany-banner，先给我两种布局方案，不生成图片。
名称为“Lany 小生”，内容方向为“AI 工具实践与创作记录”。
说明每个方案的标题位置、角色动作、头像预留区和手机裁切风险。
不要增加履历、粉丝数或未确认的成绩。
```

### 改版旧横幅

```text
使用 $lany-banner，检查我附上的旧横幅和当前头像。
保留已确认的名称与文案，把核心信息移出左下头像遮挡区。
重新构图为1500×500，另存新版，保留旧图。
如果无法读取实际主页预览，请列出仍需我在页面上确认的裁切项。
```

## 需要提供什么

| 输入 | 说明 |
| --- | --- |
| 身份参考 | 当前确认头像；未提供时使用仓库内置像素小生 |
| 名称与内容方向 | 提供准确文字；缺少依据的 Slogan 会标记为待确认 |
| 平台与尺寸 | 默认 X 1500×500；其他平台请给目标画幅 |
| 输出位置 | 指定项目目录和简短 slug，方便保存不同版本 |
| 主页截图 | 用于检查头像覆盖和窄屏裁切；没有时只能给预览与待确认项 |

默认以 `#0A0A0A`、石墨灰、暖白和 `#D8FF00` 排版。仓库内置像素角色；你本次确认的新头像优先作为身份参考。

## 会得到什么

```text
lany-assets/lany-banner/x-profile/
├── prompts/banner.md
├── banner.png
└── 源图与预览（按任务需要保存）
```

只要方案时交付布局与文案；要求出图时保存正式 PNG 和必要源图。同名产物用 `-v2` 等后缀，交付说明包含文案、排版决定、最终路径和待确认的显示差异。技能不会自动把图片上传到 X。

## 验收与常见问题

- **头像挡住文字：** 左下约 340×210 是工作流预留区，不是跨设备保证；用实际头像叠加预览复核。
- **手机切掉人物或标题：** 把关键元素向内部移动，按窄屏重新检查，不能只看整张横图。
- **中文写错：** 逐字校对名称与 Slogan；必要时用可编辑文字重新排版。特殊字形可配合 [lany-typography-prompts-skill](https://github.com/LanyXiaosheng/lany-typography-prompts-skill)。
- **只输出方案没有图：** 确认请求中写了“生成图片”，且宿主有可用生图工具；安装技能不会添加生图服务。
- **调用名搜不到：** 使用 `$lany-banner`，不是 `$lany-banner-skill`；检查安装目录中是否直接包含 `SKILL.md`。

## 仓库导航

- [SKILL.md](SKILL.md)：完整执行规则。
- [agents/openai.yaml](agents/openai.yaml)：技能展示信息。
- [版式规则](references/banner-layout.md)：品牌、遮挡区与检查项。
- [内置头像](assets/lany-avatar-reference.png)：默认人物身份参考。
- [DESIGN.md](DESIGN.md)：拆分设计与边界。

来源：[lany-skills/lany-banner](https://github.com/LanyXiaosheng/lany-skills/tree/master/lany-banner)。本仓库独立安装，调用名保持 `lany-banner`。

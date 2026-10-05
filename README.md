# Claude Code Dracula Theme

为 [Claude Code](https://code.claude.com) 命令行（`/theme`）准备的 [Dracula](https://draculatheme.com) 自定义主题。所有颜色取自 [Dracula 官方色板](https://draculatheme.com/spec)。

> 用的是 **Claude Code 桌面 app 或 claude.ai**？那里已经内置了 Dracula，不需要这个仓库：
> 设置 → Claude Code → Code appearance → Dracula。详见 [draculatheme.com/claude-code](https://draculatheme.com/claude-code)。
> 本仓库面向终端里的 `claude` CLI。

## 安装

Claude Code 从 `~/.claude/themes/` 读取自定义主题，文件名（去掉 `.json`）就是主题的 slug。

**macOS / Linux**

```bash
mkdir -p ~/.claude/themes
curl -fsSL https://raw.githubusercontent.com/mirsery/claude-dracula-theme/main/dracula.json \
  -o ~/.claude/themes/dracula.json
```

**Windows（PowerShell）**

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\themes" | Out-Null
Invoke-WebRequest https://raw.githubusercontent.com/mirsery/claude-dracula-theme/main/dracula.json `
  -OutFile "$HOME\.claude\themes\dracula.json"
```

也可以 clone 本仓库后手动把 `dracula.json` 复制过去。

## 启用

1. 如果 `~/.claude/themes/` 目录是刚建的，先**重启一次** `claude`。Claude Code 只监听启动时已存在的主题目录，之后再改主题文件就不用重启了。
2. 在 Claude Code 里输入 `/theme`，选择 **Dracula**。

选中后，主题设置会记成 `custom:dracula`。

## 让终端背景也变成 Dracula

Claude Code 只负责给文字、边框、提示块上色，**终端本身的背景色由终端程序决定**。要得到完整的 Dracula 效果，把终端的配色方案也换成 Dracula，背景色是 `#282A36`。

iTerm2、Ghostty、Alacritty、Windows Terminal 等都有现成的 Dracula 配色，可以在 [draculatheme.com](https://draculatheme.com) 上搜对应终端。

## 配色映射

主题以内置的 `dark` 预设为基础，下表列出的颜色项会被覆盖，没列出的沿用 `dark`。

| 颜色项 | 作用 | 颜色 | Dracula 色 |
| :- | :- | :- | :- |
| `claude` / `claudeShimmer` | 品牌主色、spinner、助手标签 | `#BD93F9` / `#D6ACFF` | Purple / Bright Blue |
| `text` | 默认文字 | `#F8F8F2` | Foreground |
| `inverseText` | 彩色底上的文字 | `#282A36` | Background |
| `inactive` | 次要文字、提示、时间戳 | `#6272A4` | Comment |
| `subtle` | 淡边框 | `#44475A` | Selection |
| `suggestion` | 自动补全、选择器高亮 | `#8BE9FD` | Cyan |
| `permission` / `permissionShimmer` | 权限确认等对话框边框 | `#FF79C6` / `#FF92DF` | Pink / Bright Magenta |
| `remember` | 记忆与 `CLAUDE.md` 标识 | `#8BE9FD` | Cyan |
| `success` | 成功 | `#50FA7B` | Green |
| `error` | 错误 | `#FF5555` | Red |
| `warning` / `warningShimmer` | 警告、auto 模式标识 | `#F1FA8C` / `#FFFFA5` | Yellow / Bright Yellow |
| `merged` | 已合并的 PR | `#BD93F9` | Purple |
| `promptBorder` / `promptBorderShimmer` | 输入框边框 | `#6272A4` / `#BD93F9` | Comment / Purple |
| `planMode` | plan 模式 | `#8BE9FD` | Cyan |
| `autoAccept` | accept-edits 模式 | `#50FA7B` | Green |
| `bashBorder` | `!` shell 命令输入框边框 | `#FFB86C` | Orange |
| `ide` | IDE 连接标识 | `#8BE9FD` | Cyan |
| `fastMode` / `fastModeShimmer` | fast 模式标识 | `#FFB86C` / `#F1FA8C` | Orange / Yellow |
| `effortUltra` | ultracode 标签 | `#FF79C6` | Pink |
| `diffAdded` / `diffRemoved` | diff 新增 / 删除行底色 | `#315845` / `#57333D` | Green / Red 混入 Background（22%） |
| `diffAddedWord` / `diffRemovedWord` | diff 行内单词高亮 | `#387D52` / `#7E3B42` | 同上（40%） |
| `diffAddedDimmed` / `diffRemovedDimmed` | 拒绝编辑后的淡化 diff | `#2C3F3D` / `#3E2E39` | 同上（10%） |
| `userMessageBackground` | 你的消息背景 | `#343746` | Background Light |
| `userMessageBackgroundHover` | 悬停 / 展开时的消息背景 | `#424450` | Background Lighter |
| `bashMessageBackgroundColor` / `memoryBackgroundColor` | `!` 命令与 `#` 记忆条目背景 | `#343746` | Background Light |
| `selectionBg` | 鼠标选中文字的背景 | `#44475A` | Selection |
| `rate_limit_fill` / `rate_limit_empty` | `/usage` 用量条 | `#BD93F9` / `#44475A` | Purple / Selection |
| `briefLabelYou` / `briefLabelClaude` | `You` / `Claude` 标签 | `#8BE9FD` / `#BD93F9` | Cyan / Purple |
| `<color>_FOR_SUBAGENTS_ONLY` | 8 种子 agent 颜色 | red `#FF5555`、orange `#FFB86C`、yellow `#F1FA8C`、green `#50FA7B`、cyan `#8BE9FD`、blue `#D6ACFF`、purple `#BD93F9`、pink `#FF79C6` | 对应同名色 |

diff 底色不能直接用高饱和的 Green / Red，否则代码看不清，所以按比例混入了 Background `#282A36`，括号里是混合比例。

## 自己调整

直接改 `~/.claude/themes/dracula.json` 里的 `overrides`，保存后正在运行的会话会自动刷新。也可以在 `/theme` 里选中 Dracula 后按 `Ctrl+E`，用交互式编辑器实时预览修改。

- 颜色支持 `#rrggbb`、`#rgb`、`rgb(r,g,b)`、`ansi256(n)`、`ansi:<name>` 几种写法。
- **写错的颜色项名或颜色值会被静默忽略，不会报错**，改完没生效时先检查拼写。
- 全部颜色项见官方文档 [Create a custom theme](https://code.claude.com/docs/en/terminal-config#create-a-custom-theme)。

## 致谢

- 配色来自 [Dracula Theme](https://draculatheme.com)（MIT License），作者 Zeno Rocha 及贡献者。
- 本仓库与 Dracula 官方、Anthropic 均无关联。

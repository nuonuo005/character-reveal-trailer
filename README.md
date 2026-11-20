# Character Reveal Trailer · 角色揭晓预告片技能

[English](#english) | [中文](#中文)

## 中文

把角色插画、头像、三视图或文字设定，变成一支节奏鲜明的角色揭晓预告片。这个仓库提供的是给 AI 编程助手使用的 **Skill 工作指南**：它指导助手准备角色素材、设计镜头、制作交互式预览，并按需导出视频。

### 样片

[▶ 观看 / 下载 NUO 角色预告样片](nuo_reveal_trailer.mp4)

这是本项目提供的效果示例，时长 15 秒，1920 × 1080，60 fps，带声音。样片用于展示角色、文字、快切画面和节奏配合的创作方向；不同角色素材、工具和创意选择会产生不同结果。

### 可以做什么

- 根据角色形象或设定设计约 15 秒的快节奏宣传片，结合动态文字、分屏、残影、冲击画面和品牌信息。
- 使用正面、侧面、背面及动作姿态制作 2.5D 合成；有条件时可通过图像生成工具补充姿态。
- 支持横屏、竖屏和方形构图，并根据角色调整配色和风格。
- 制作可拖动进度、逐帧查看的 HTML 预览；需要时再输出 MP4。

默认方案为 15 秒、12 个镜头和 60 fps，也可以在需求中调整。技能本身不是一键视频软件，也不包含现成的渲染器、角色素材或生成服务；实际能力取决于所用 AI 助手及其图像生成、浏览器和视频编码工具。

### 安装与使用

使用支持 Skills 的 AI 编程助手，将仓库中的 `SKILL.md` 放入该助手的技能目录。以 Codex 的个人技能目录为例：

```bash
mkdir -p ~/.codex/skills
mkdir -p ~/.codex/skills/character-reveal-trailer
cp SKILL.md ~/.codex/skills/character-reveal-trailer/
```

上述命令在克隆或下载后的仓库根目录运行。重新启动或刷新助手后，可在对话中明确调用 `$character-reveal-trailer`。其他助手请参照其技能安装方式。

准备角色图片或文字设定，并说明画幅、品牌文字、风格及希望获得 HTML、MP4 或两者。例如：

> 使用 $character-reveal-trailer，根据我上传的角色图制作一支 15 秒横版揭晓预告片。风格是蓝黑科技感，片尾文字为 NUO，先给我 HTML 预览，再导出 MP4。

如果只有单张图，其他角度和动作可能需要额外生成；生成的背面等未提供视角属于创作推测。生成服务、依赖、渲染速度与成本取决于环境。请在公开使用前检查角色素材、音乐与字体的使用权，并检查成片。

### 致谢

特别感谢 [ChetasLua](https://github.com/ChetasLua) 的 [AO Bot Reveal Trailer](https://github.com/ChetasLua/ao-bot-reveal-trailer)，本技能的镜头语言和制作思路受到该项目启发。原项目是程序化 3D 角色预告片；本技能整理为面向角色图片的 2.5D 创作流程。本仓库不包含原项目源码；使用原项目时请自行查看其授权条件。

---

## English

Turn a character illustration, avatar, turnaround sheet, or written concept into a fast-paced reveal trailer. This repository contains a **Skill workflow for AI coding agents**: it guides the agent through preparing character assets, designing shots, building an interactive preview, and exporting a video when requested.

### Demo

[▶ Watch / download the NUO reveal trailer](nuo_reveal_trailer.mp4)

The supplied example is 15 seconds long, 1920 × 1080, 60 fps, with audio. It illustrates a direction for combining character imagery, typography, fast cuts, and rhythm. Results vary with the source material, tools, and creative decisions.

### What it can do

- Plan an energetic character promo with kinetic typography, split screens, afterimages, impact frames, and branding.
- Compose a 2.5D sequence from front, side, back, and action poses; generate additional poses when suitable image tools are available.
- Adapt the layout and visual style for landscape, portrait, or square formats.
- Build an interactive, scrubbable HTML preview and export an MP4 if requested.

The starting point is 15 seconds, 12 cuts, and 60 fps; these are adjustable. The skill is a set of instructions, not a one-click video application. It does not bundle a renderer, character assets, or a generation service. Results depend on the agent and available image generation, browser, and encoding tools.

### Installation and use

Copy `SKILL.md` into a folder in your AI assistant's skills directory. For a personal Codex installation, run this from the cloned or downloaded repository root:

```bash
mkdir -p ~/.codex/skills
mkdir -p ~/.codex/skills/character-reveal-trailer
cp SKILL.md ~/.codex/skills/character-reveal-trailer/
```

Restart or refresh the assistant if necessary, then explicitly invoke `$character-reveal-trailer`. For other agents, follow their skill installation instructions.

Provide a character image or concept, aspect ratio, branding, visual direction, and desired deliverables. For example:

> Use $character-reveal-trailer to create a 15-second landscape reveal from my character image. Use a blue-and-black tech style and end with NUO. Show me an HTML preview, then export an MP4.

Additional views may require image generation. Unprovided views are interpretations, not verified character designs. Availability, cost, and render time depend on your environment. Check the rights for character assets, music, and fonts, and review the final video before publishing.

### Acknowledgements

Special thanks to [ChetasLua](https://github.com/ChetasLua) for [AO Bot Reveal Trailer](https://github.com/ChetasLua/ao-bot-reveal-trailer), which inspired this skill's visual language and production approach. The original is a procedural 3D character trailer; this skill adapts the idea into an image-led 2.5D workflow. This repository does not include the original project's source code; check its terms before using that project.

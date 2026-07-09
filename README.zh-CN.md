# image-ppt-maker

`image-ppt-maker` 是一个 Codex Skill，用来把一个 PPT 需求转成一组 PPT 风格图片、可播放的 16:9 HTML 演示文件，以及最终逐页讲稿。

它适合希望快速完成“逻辑大纲 + 视觉提示词 + 成套图片 + 演讲讲稿”的用户，尤其适合培训分享、管理层汇报、方案路演、AI/数字化主题展示、内部课程和客户沟通。

[English README](README.md)

## 这个技能有什么优点

- **麦肯锡式逻辑结构**：先梳理核心结论、主线、章节和逐页逻辑，避免 PPT 只是好看但没故事。
- **关键节点有人审**：需求、大纲、拓展内容、图片风格、提示词都会让用户确认，减少返工。
- **自动推荐视觉风格**：会根据主题、受众和时长推荐培训风、汇报风、多插画、多图形、科技感、品牌简洁风等方向。
- **整套风格统一**：通过统一的风格锁定，让每页图片看起来属于同一套演示稿。
- **一页一图，适合展示**：每页生成一张 16:9 PPT 风格图片，便于直接分享、嵌入或播放。
- **自动生成 HTML 播放器**：图片生成后会自动组装成可播放的 16:9 HTML 文件，支持键盘翻页、点击翻页、进度条和全屏。
- **最后再写讲稿**：讲稿会结合最终图片和大纲逐页生成，表达更自然、更贴近实际演示。

## 工作流程

1. 确认主题、目标、受众、时长、页数、信息密度、资料约束，以及是否预留左上角/右上角 LOGO 区域。
2. 生成麦肯锡式总纲和分页大纲。
3. 拓展每页内容、例子和视觉重点。
4. 在生成提示词前询问用户想要的图片风格，并根据上下文推荐选项。
5. 生成统一风格的 image-2 图片提示词。
6. 批量生成 16:9 PPT 图片。
7. 自动组装成可播放的 16:9 HTML 演示文件。
8. 结合大纲和最终图片，逐页生成口语化讲稿。

## 模型依赖

这个 Skill 依赖大模型的图片生成能力。推荐使用具备以下能力的模型：

- 能理解复杂提示词和版式要求；
- 能生成清晰的 PPT 风格页面；
- 能保持多页风格一致；
- 能生成相对可读的页面文字；
- 能保存或导出本地图片文件，便于组装 HTML。

推荐模型方向：

- **OpenAI GPT Image / ChatGPT 图片生成能力**：适合指令遵循、结构化页面和演示风格图片生成。参考 [OpenAI image generation docs](https://platform.openai.com/docs/guides/image-generation)。
- **Google Gemini 图片生成 / Nano Banana / Imagen**：适合多模态图片生成、迭代和风格化输出。参考 [Gemini image generation docs](https://ai.google.dev/gemini-api/docs/image-generation) 和 [Google DeepMind Imagen](https://deepmind.google/models/imagen/)。
- 其他能稳定生成 16:9 演示页、文字可读、风格一致的图片模型也可以使用。

模型名称和可用性会变化，实际使用前建议查看对应厂商的最新文档。

## 安装方式

### 方式一：直接 clone 到 Codex skills 目录

Windows PowerShell：

```powershell
git clone https://github.com/callmexhj/image-ppt-maker.git "$env:USERPROFILE\.codex\skills\image-ppt-maker"
```

macOS/Linux：

```bash
git clone https://github.com/callmexhj/image-ppt-maker.git ~/.codex/skills/image-ppt-maker
```

### 方式二：下载 ZIP

1. 在 GitHub 页面点击 Download ZIP。
2. 解压后将文件夹改名为 `image-ppt-maker`。
3. 移动到 Codex skills 目录：
   - Windows：`%USERPROFILE%\.codex\skills\image-ppt-maker`
   - macOS/Linux：`~/.codex/skills/image-ppt-maker`

### 方式三：从本地目录复制

Windows PowerShell：

```powershell
Copy-Item -LiteralPath . -Destination "$env:USERPROFILE\.codex\skills\image-ppt-maker" -Recurse -Force
```

macOS/Linux：

```bash
cp -R . ~/.codex/skills/image-ppt-maker
```

## 使用方式

在 Codex 中输入：

```text
$image-ppt-maker
```

示例：

```text
$image-ppt-maker 帮我做一套面向管理层的 AI 应用培训分享，10 分钟左右，偏培训风，最后生成可播放的 HTML。
```

## 输出内容

这个 Skill 可以输出：

- 需求确认和关键假设；
- 麦肯锡式总纲和分页大纲；
- 每页拓展内容和视觉重点；
- 图片生成提示词；
- 16:9 PPT 风格图片；
- 可播放 HTML 演示文件；
- 最终逐页口语化讲稿。

## 注意事项

- 这个 Skill 不负责生成 `.pptx` 文件。
- HTML 播放器需要本地图片文件。
- 为了效果更好，建议提供事实材料、品牌约束、目标受众、演讲时长和期望语气。

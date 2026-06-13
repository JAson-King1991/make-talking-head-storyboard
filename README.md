# Make Talking Head Storyboard

一个帮助中文口播视频创作者规划 B-roll，并生成符合文意的 AI 视频提示词的 Codex Skill。

## 1. 不再为 B-roll 素材发愁

制作口播视频时，你是否经常遇到这些问题：

- 哪句话应该加入 B-roll？
- B-roll 应该何时切入、持续多久？
- 哪些内容更适合保留人物正面？
- 找不到符合文意的素材怎么办？

这个 Skill 会分析整篇口播文案，判断哪些内容适合视觉化，并将其整理成可以直接执行的 B-roll 分镜方案。

它不会机械地为每句话配画面。重要观点、情绪落点和需要建立信任的内容会保留人物正面，B-roll 只会出现在真正有助于理解、节奏或情绪表达的位置。

## 2. 从口播文案到 AI 视频素材

针对每个建议加入的 B-roll，Skill 会提供：

- 对应原文与插入位置
- 推荐画面及其作用
- 推荐时长与剪辑节奏
- 素材库检索关键词
- 是否适合让固定 AI 动画主人公出演
- 可直接用于即梦或可灵的中文 AI 视频提示词

生成画面可以复现文案中的人物、事件和场景，也可以让固定的 AI 动画主人公参与情景演绎。

将提示词输入即梦或可灵，即可生成相应的 B-roll 视频素材。

## 3. 根据上下文生成符合文意的画面

普通 AI 视频工具通常根据单句话或关键词生成画面，容易出现画面虽然好看，却没有准确表达文案含义的问题。

这个 Skill 会先理解整篇文案的主题、核心观点和前后语义，再设计符合上下文的具体场景，而不是简单复现关键词。

例如，文案中的“拒绝”可能表达的是战略取舍。Skill 不会只生成一个人拒绝别人的画面，而会设计 AI 动画主人公审视多个项目、放弃次要选择、最终保留最重要项目的情景。

生成的 B-roll 因此不仅是装饰素材，还能帮助观众理解文案真正想表达的内容。

默认适用于知识口播、评论、时评、议题讨论和个人观点输出。AI 视频提示词默认面向即梦与可灵，采用 `1:1` 画幅和 `5-10 秒`时长。

```text
使用 $make-talking-head-storyboard，为下面的口播稿制作 B-roll 分镜执行方案：

[粘贴完整口播稿]
```

---

## English

A Codex Skill that helps creators of Chinese talking-head videos plan B-roll and generate AI-video prompts that accurately reflect the script's intended meaning.

### 1. Stop Worrying About B-roll Footage

When producing a talking-head video, do you often face questions like these?

- Which lines should have B-roll?
- When should each B-roll shot appear, and how long should it last?
- Which parts should keep the presenter on screen?
- What should you do when suitable footage cannot be found?

This skill analyzes the complete script, identifies which parts should be visualized, and organizes them into an executable B-roll storyboard.

It does not mechanically add visuals to every sentence. Important arguments, emotional conclusions, and trust-building moments remain on camera. B-roll is recommended only where it improves understanding, pacing, or emotional expression.

### 2. From Talking-head Script to AI-generated Footage

For every recommended B-roll shot, the skill provides:

- The corresponding script line and insertion point
- The recommended visual and its purpose
- Suggested duration and editing rhythm
- Stock-footage search keywords
- Whether the recurring AI animated protagonist should appear
- A Chinese AI-video prompt ready for Jimeng or Kling

Generated scenes can recreate people, events, and settings from the script or feature a recurring AI animated protagonist performing the scenario.

Enter the prompt into Jimeng or Kling to generate the corresponding B-roll footage.

### 3. Generate Visuals That Match the Meaning of the Script

Most AI-video tools generate visuals from isolated sentences or keywords. The result may look appealing without accurately communicating what the script means.

This skill first understands the complete script's subject, central argument, and surrounding context. It then designs a specific scene that reflects the intended meaning instead of simply illustrating keywords.

For example, the word "refusal" may represent strategic prioritization. Instead of showing someone rejecting another person, the skill could show the AI animated protagonist reviewing several projects, removing the less important options, and keeping only the most valuable one.

The generated B-roll therefore does more than decorate the video. It helps the audience understand what the script is actually trying to communicate.

The skill is designed for knowledge explainers, commentary, current-affairs analysis, issue discussions, and personal-opinion videos. AI-video prompts target Jimeng and Kling by default, using a `1:1` aspect ratio and a duration of `5-10 seconds`.

```text
Use $make-talking-head-storyboard to create a B-roll storyboard for the following talking-head script:

[Paste the complete script]
```

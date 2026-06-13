# Make Talking Head Storyboard

一个面向中文口播视频的 Codex Skill。

它不会脱离上下文，直接把单句文案机械地翻译成 AI 视频提示词。它会先理解完整口播稿的论点、上下文、情绪与传播目标，再判断哪些句子适合加入 B-roll，并将经过判断的画面方案转译成可执行的中文 AI 视频 Prompt。

> English documentation is available in the [English](#english) section below.

适合：

- 知识口播
- 老板 IP / 创始人 IP
- 品牌宣传
- 需要固定 AI 动画主人公参与情景演绎的视频

## 为什么做这个 Skill

常见 AI 视频 Prompt 工作流通常从一句简短描述直接开始，因此容易产生：

- 与全文上下文无关的泛化画面
- 只会直译关键词的 B-roll
- 随机办公室、城市、握手等装饰性素材
- 有氛围但没有清晰动作和结果的 Prompt
- 为了热闹而频繁切换画面

这个 Skill 将“理解内容”和“设计镜头”放在“写 Prompt”之前。

```text
理解完整口播稿
→ 按语义拆分
→ 判断哪些句子适合 B-roll
→ 定义每个镜头承担的传播作用
→ 判断是否使用 AI 动画主人公
→ 设计贴合上下文的具体情景
→ 检查画面准确性与生成可行性
→ 生成中文 AI 视频 Prompt
→ 可选接入可灵等模型生成视频
```

## 核心能力

### 1. 判断哪句话需要 B-roll

Skill 会区分：

- `强`：B-roll 对理解或传播效果非常重要
- `中`：B-roll 能改善语境、节奏、趣味或情绪
- `弱`：适合短暂插入、叠加或关键词视觉化
- `无`：更应该保留人物正面

默认目标是让 B-roll 覆盖成片约 `55%-65%`，但不会机械地每句话切一次。

### 2. 基于全文上下文设计画面

每个 B-roll 都必须先回答：

1. 观众会看到什么？
2. 画面在几秒内发生什么变化？
3. 这个变化表达了上下文中的什么含义？
4. 为什么它比保留人物正面更有效？

例如，“真正拉开差距的，是你拒绝了多少”不应该只生成“一个人拒绝别人”。

更贴合上下文的画面可能是：AI 动画主人公扮演创业负责人，在多份项目提案中进行审视和取舍，最终只留下最重要的一份，通过具体动作表达战略聚焦。

### 3. 使用固定 AI 动画主人公演绎情景

用户可以提供基于主播形象设计的固定 AI 动画主人公。

主人公不是主播真实经历的事实性替身，而是一名可以参与情景演绎的固定演员，可以扮演：

- 正面或负面角色
- 犯错者或解决问题的人
- 焦虑者、决策者、观察者
- 同一人物的前后对比状态

Skill 会根据句意判断人物出演是否比纯场景、物体、数据或流程画面更有效、更有趣。

### 4. 输出可直接执行的分镜表

默认输出包含：

- 全文理解摘要
- 原句与上下文含义
- B-roll 建议强度与类型
- 是否使用 AI 动画主人公
- 主人公扮演角色、动作与表演要求
- 插入位置、推荐时长和节奏
- 素材来源与素材库检索关键词
- 即梦中文 Prompt
- 人物正面关键保留点
- 主人公重点演绎清单
- 优先生成清单
- 制作风险

### 5. 生成上下文驱动的 AI 视频 Prompt

Prompt 默认：

- 使用中文
- 优先适配即梦，并保持可适配可灵
- 生成时长为 `5-10 秒`
- 使用 `1:1` 方形画面
- 包含主体、当前角色、场景、道具、起始状态、连续动作、结果、表情、肢体、构图、镜头运动、光线、风格和必要负向约束

Skill 会使用独立的 Prompt 质量规则，拦截脱离上下文、动作不清、过于泛化或难以生成的方案。

## 安装

使用 Skills CLI：

```bash
npx skills add JAson-King1991/make-talking-head-storyboard -g -y
```

或将本仓库复制到 Codex Skills 目录：

```bash
git clone https://github.com/JAson-King1991/make-talking-head-storyboard.git
cp -R make-talking-head-storyboard ~/.codex/skills/
```

## 使用示例

安装后直接调用：

```text
使用 $make-talking-head-storyboard，为下面这篇口播稿制作 B-roll 分镜执行方案。

[粘贴完整口播稿]
```

提供主人公参考图时：

```text
使用 $make-talking-head-storyboard 分析这篇口播稿。
将我提供的角色参考图作为固定 AI 动画主人公，根据句意判断哪些 B-roll 适合让他参与演绎。
```

也可以补充内容类型和风格约束：

```text
这是老板 IP 内容。整体专业可信，但允许主人公通过适度夸张的负面情景增加趣味性。
```

## 文件结构

```text
make-talking-head-storyboard/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-quality-rubric.md
```

## 当前边界

这个 Skill 当前负责：

- 理解口播全文
- 判断 B-roll 位置
- 设计画面与主人公情景
- 生成上下文驱动的 AI 视频 Prompt

它不会默认直接调用 AI 视频模型。只有用户明确提出生成视频时，才会优先搜索并评估能够直接将 B-roll 方案转成 AI 动画的 Skill；如果没有合适方案，再考虑接入可灵或自行开发生成流程。

## 后续方向

- 基于实际生成结果持续校准 Prompt 质量规则
- 增加固定主人公的视觉档案与一致性模板
- 增加即梦与可灵的模型专项 Prompt 转译层
- 评估直接生成 AI 动画的可选工作流

---

## English

A Codex Skill for planning B-roll in Chinese talking-head videos.

Instead of mechanically translating isolated script lines into AI-video prompts, this skill first understands the complete script, its argument, context, emotional direction, and communication goals. It then decides which lines benefit from B-roll and converts approved visual ideas into production-ready Chinese AI-video prompts.

Best suited for:

- Knowledge explainers
- Founder and executive personal-brand videos
- Brand promotion
- Videos featuring a recurring AI animated protagonist

### Why This Skill Exists

Typical AI-video prompting workflows often start from a short, isolated description. This frequently produces:

- Generic visuals disconnected from the full script
- Literal keyword illustrations
- Decorative office, city, technology, or handshake footage
- Atmospheric prompts without readable actions or outcomes
- Excessive cuts added only to make the video feel busy

This skill places content understanding and visual design before prompt writing.

```text
Understand the complete script
→ Split it into semantic units
→ Decide which lines benefit from B-roll
→ Define each shot's communication purpose
→ Decide whether to use the AI animated protagonist
→ Design a contextually accurate scene
→ Check meaning and generation feasibility
→ Write the Chinese AI-video prompt
→ Optionally connect to Kling or another video model
```

### Core Capabilities

#### 1. Decide Which Lines Need B-roll

The skill classifies B-roll recommendations as:

- `Strong`: materially improves comprehension or impact
- `Medium`: improves context, pacing, interest, or emotion
- `Weak`: suitable for a brief insert, overlay, or keyword visualization
- `None`: the real speaker should remain on screen

The default target is approximately `55%-65%` B-roll coverage without mechanically cutting on every sentence.

#### 2. Design Visuals From Full-Script Context

Every B-roll idea must answer:

1. What does the audience see?
2. What visibly changes during the clip?
3. What contextual meaning does that change communicate?
4. Why is the visual better than keeping the speaker on screen?

For example, the line “What separates people is how much they refuse” should not simply produce a person saying no.

A more contextual scene could show the AI animated protagonist playing a founder who reviews several project proposals, deliberately removes most of them, and keeps only the most important one. The visible action communicates strategic focus.

#### 3. Use a Recurring AI Animated Protagonist

Users may provide a recurring character designed from the presenter's appearance.

The protagonist is not treated as a factual representation of the real presenter. It is a reusable animated actor that may play:

- Positive or negative roles
- Someone making a mistake or solving a problem
- An anxious person, decision-maker, or observer
- Contrasting before-and-after states

The skill decides whether character performance is more effective and entertaining than scenery, objects, data, or process visuals.

#### 4. Produce an Executable Storyboard Sheet

The default output includes:

- Full-script understanding summary
- Original line and contextual meaning
- B-roll recommendation strength and type
- Whether to use the AI animated protagonist
- Protagonist role, action, and performance requirements
- Insertion point, duration, and pacing
- Material source and stock-library search keywords
- Chinese Jimeng prompt
- Key speaker-on-camera moments
- Priority protagonist performances
- Priority generation list
- Production risks

#### 5. Generate Context-Grounded AI-Video Prompts

Prompts default to:

- Chinese language
- Jimeng-first structure while remaining adaptable to Kling
- `5-10 second` source clips
- `1:1` square output
- Explicit subject, role, setting, props, starting state, continuous action, result, expression, body language, composition, camera movement, lighting, style, and necessary negative constraints

An independent prompt-quality rubric rejects generic, context-free, unclear, or impractical prompts.

### Installation

Install with the Skills CLI:

```bash
npx skills add JAson-King1991/make-talking-head-storyboard -g -y
```

Or clone the repository into your Codex skills directory:

```bash
git clone https://github.com/JAson-King1991/make-talking-head-storyboard.git
cp -R make-talking-head-storyboard ~/.codex/skills/
```

### Usage

After installation:

```text
Use $make-talking-head-storyboard to create a B-roll storyboard execution plan for the following talking-head script.

[Paste the complete script]
```

With a protagonist reference image:

```text
Use $make-talking-head-storyboard to analyze this script.
Treat the supplied character reference as the recurring AI animated protagonist and decide which B-roll scenes benefit from character performance.
```

You may also specify content type and tone:

```text
This is a founder-IP video. Keep it professional and credible, but allow the protagonist to perform mildly exaggerated negative scenarios for entertainment.
```

### Repository Structure

```text
make-talking-head-storyboard/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-quality-rubric.md
```

### Current Scope

This skill currently handles:

- Full-script understanding
- B-roll placement decisions
- Visual and protagonist scene design
- Context-grounded AI-video prompt generation

It does not call an AI-video model by default. When the user explicitly requests generated video, the workflow first searches for and evaluates a suitable skill that can directly convert approved B-roll plans into AI animation. If none is suitable, Kling integration or a custom generation workflow can be considered.

### Future Directions

- Calibrate prompt-quality rules using real generation results
- Add a recurring-protagonist visual profile and continuity template
- Add model-specific prompt translation layers for Jimeng and Kling
- Evaluate an optional direct AI-animation generation workflow

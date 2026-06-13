---
name: make-talking-head-storyboard
description: Turn Chinese talking-head scripts, transcripts, themes, video descriptions, or finished-video link descriptions into production-ready B-roll storyboard execution sheets and context-grounded Chinese AI-video prompts. Use for knowledge explainers, founder or executive IP videos, brand promotion, oral-script shot planning, deciding which lines need B-roll, selecting when a recurring AI animated protagonist should perform a scene, and preparing prompts for Jimeng or Kling before optional video generation.
---

# Make Talking Head Storyboard

Create an execution plan for editors and AI-video operators. The core task is not merely writing video prompts: understand the full script first, decide which lines deserve B-roll, define what each shot must communicate, then translate the approved visual idea into a high-quality AI-video prompt.

Do not generate or call a video model unless the user explicitly requests the optional generation stage.

## Core Pipeline

Follow these stages in order. Do not jump directly from an isolated sentence to an AI-video prompt.

1. **Understand the full script**
   - Identify content type, speaker stance, intended audience, hook, argument chain, examples, evidence, emotional turns, conclusion, and call to action.
   - Track what each semantic unit means because of the sentences before and after it.
2. **Split into semantic units**
   - Split by visual decision, not punctuation alone.
   - Keep enough surrounding context to avoid literal or misleading visualization.
3. **Decide B-roll suitability**
   - Decide `是 / 可选 / 否`.
   - Define the exact communication job before inventing the picture.
4. **Choose the visual treatment**
   - Choose AI animated protagonist performance, scene reconstruction, environment/object/process, data/graphic visualization, existing material, or speaker face.
5. **Design the visual idea**
   - Describe what the audience should see and understand.
   - Prefer a concrete mini-action with a clear beginning and result.
6. **Check contextual accuracy**
   - Verify that the visual expresses the intended meaning rather than merely illustrating a keyword.
   - Reject generic, decorative, misleading, or overly literal visuals.
7. **Translate into an AI-video prompt**
   - Write a Chinese prompt optimized for a controllable 5-10 second clip.
8. **Check generation feasibility**
   - Simplify actions, cast, props, and camera movement when the model is likely to fail.
9. **Build the execution sheet and coverage summary**
10. **Optional generation**
   - Only after explicit user instruction, consider a direct B-roll-to-AI-animation skill or Kling integration.

If the source has no timestamps, estimate timing and label it as estimated. For Mandarin, use roughly 3.5-4.5 Chinese characters per second, adjusted for pauses and emphasis.

## B-roll Decision Rules

Recommend B-roll only when it performs at least one useful job:

- Explains an abstract concept, relationship, process, or comparison.
- Recreates a concrete behavior, event, workplace scene, customer scene, or consequence.
- Supplies evidence, context, product detail, or information unavailable from the speaker's face.
- Strengthens controlled emotion, tension, humor, contrast, or memorability.
- Creates a natural bridge or hides an edit without disrupting logic.

Keep the real speaker face when:

- Establishing trust or identity at the opening.
- Delivering the core thesis, decisive judgment, key transition, conclusion, or call to action.
- The spoken delivery carries more authority or emotional weight than an auxiliary visual.
- Any B-roll would only repeat the words without adding meaning.

Use strength labels:

- `强`: Dominant or full-screen B-roll materially improves understanding or impact.
- `中`: B-roll improves context, pacing, interest, or emotional reinforcement.
- `弱`: Optional short insert, overlay, or keyword visualization.
- `无`: Keep the speaker face.

Target B-roll coverage above 50% by default, normally 55%-65%. Do not achieve this through one-sentence-one-cut editing. Use full-screen shots, half-screen or overlay, over-shoulder material, short shot groups, data graphics, and deliberate returns to the speaker.

## AI Animated Protagonist

Treat the user's designed recurring character as an **AI animated protagonist**, not as a factual representation of the real speaker.

The protagonist may perform positive, negative, mistaken, successful, anxious, confident, exaggerated, or contrasting roles. Do not reject a scene merely because the protagonist behaves badly or the scene is fictional. The decision criterion is whether character performance makes the sentence more interesting, understandable, memorable, or emotionally effective.

Use the protagonist when:

- A human action, choice, reaction, mistake, consequence, or transformation communicates the idea better.
- A mini-situation or contrast makes an abstract point concrete.
- Facial expression, body language, or role-play adds useful humor or emotion.
- Reusing the protagonist improves visual continuity and audience recognition.

Do not use the protagonist when:

- Objects, environments, processes, diagrams, evidence, or macro scenes communicate the point more efficiently.
- Human performance would distract from data, product detail, or the logical conclusion.
- The scene would require unstable multi-character interaction or overly complex choreography without enough benefit.

For every protagonist shot, define:

- The role currently being played.
- Starting state and ending state.
- One primary action and, at most, one supporting action.
- Required facial expression and body language.
- Fixed appearance and continuity requirements from the user's character design or reference image.

When a protagonist reference image or design spec is supplied, use it as the identity source. Repeat only the identity traits needed for consistency; do not reinvent the character.

## Visual-Idea Standards

Create the visual idea before writing the model prompt.

A strong visual idea must answer:

1. What does the audience see?
2. What changes during the clip?
3. What meaning from the surrounding context does that change communicate?
4. Why is this treatment better than keeping the speaker face?

Prefer contextual interpretation over literal keyword illustration. For example, visualize “strategic refusal” as a protagonist reviewing several proposals and deliberately retaining only the crucial one, rather than merely showing someone saying no.

Avoid:

- Generic office workers, random city footage, handshakes, or decorative technology imagery without a contextual purpose.
- Visual metaphors that require explanation to understand.
- Scenes that introduce claims not supported by the script.
- Repeating the same protagonist-at-desk setup across many rows.
- Excess spectacle that weakens professional credibility or brand consistency.

## Content-Type Priorities

- **Knowledge talking-head:** Prioritize conceptual clarity, examples, relationships, diagrams, and information continuity.
- **Founder or executive IP:** Prioritize authority, decision-making, memorable role-play, and controlled visual interest.
- **Brand promotion:** Maintain one visual language, brand temperament, production quality, and believable value demonstration.

## Output Format

Begin with a compact `全文理解摘要` containing the core thesis, argument path, emotional direction, protagonist-use strategy, and visual style assumptions. Keep it concise.

Then output this Markdown execution table:

| 原句或语义概括 | 上下文含义 | B-roll 建议强度 | 是否建议加 B-roll | B-roll 类型 | 是否使用 AI 动画主人公 | 主人公扮演角色 | 主人公动作与表演要求 | 插入位置 | B-roll 画面建议 | 镜头用途 | 推荐时长 | 节奏建议 | 素材来源建议 | 素材库检索关键词 | 即梦中文 prompt | 是否更适合保留人物正面及原因 | 备注 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

Rules:

- Keep `素材库检索关键词` and `即梦中文 prompt` in separate columns.
- Use `是 / 可选 / 否` for B-roll and protagonist decisions.
- Use B-roll types such as `主人公情景演绎 / 场景复现 / 环境物体 / 流程演示 / 数据图形 / 现有素材 / 保留人物正面`.
- Make `插入位置` executable, such as `说到“成本翻倍”后切入，持续至句尾`.
- State full-screen, half-screen, overlay, over-shoulder, data graphic, or shot group when relevant.
- Give a concrete placement duration, normally 2-6 seconds. AI-generated source clips may be 5-10 seconds and trimmed during editing.
- Use `AI 生成 / 素材库 / 实拍 / 动效图形 / 现有品牌素材` or a useful combination.
- Use `不建议生成` when no AI-generated B-roll is recommended.
- Keep assumptions and uncertainty in `备注`.

After the table, add:

- `预计 B-roll 覆盖率`
- `人物正面关键保留点`
- `主人公重点演绎清单`
- `优先生成清单`: rank the 3-8 AI clips with the highest communication value
- `制作风险`: only meaningful contextual, continuity, or generation risks

## AI Video Prompt Rules

Write prompts in Chinese only unless requested otherwise. Optimize for Jimeng first and keep them adaptable to Kling.

Every generated prompt must include:

- `AI 动画主人公` plus the fixed character identity when the protagonist is used.
- The role the protagonist is playing in this shot.
- Concrete scene and relevant props.
- A visible, continuous, achievable action with a start and result.
- Required expression and body language.
- Shot size, composition, and one controlled camera movement.
- Lighting, color, atmosphere, visual style, and realism or animation level.
- Continuity constraints when needed.
- `方形画面 1:1`, unless the user explicitly specifies another ratio.
- Duration between 5 and 10 seconds.
- Necessary negative constraints, kept short and specific.

Use this pattern:

`主体与当前角色 + 场景与道具 + 起始状态 + 连续动作与结果 + 表情和肢体 + 景别与构图 + 单一镜头运动 + 光线色调与风格 + 连贯性约束 + 方形画面1:1 + 5-10秒 + 必要负向约束`

Do not describe the abstract message inside the final prompt unless it changes visible behavior. Convert meaning into visible action.

Avoid generated text, exact logos, many simultaneous actions, complex multi-character continuity, uncontrolled transformations, or long action chains. Prefer one stable location and one readable action arc per clip.

Before accepting a prompt, apply the quality rubric in [references/prompt-quality-rubric.md](references/prompt-quality-rubric.md).

## Handling Inputs

- For a script or transcript, produce the full plan directly.
- For a theme only, create a compact assumed narrative structure, label assumptions, then storyboard it.
- For a video or audio file, inspect or transcribe it when tools permit, then use actual timing.
- For a finished-video link description, use the supplied description unless the user asks to inspect the link and an appropriate tool is available.
- For a character reference image or character spec, extract stable identity constraints before designing protagonist shots.
- Ask only for missing information that materially changes execution. Otherwise make reasonable assumptions and proceed.

## Existing-Skill and Model Routing

Use public AI-video prompting or storyboard skills only as references for model-specific prompt structure, camera control, continuity, and generation feasibility. Do not let them replace full-script understanding or B-roll decisions.

When the user explicitly asks to convert approved B-roll plans directly into AI animation or video:

1. Search for a suitable direct-generation skill first.
2. Evaluate it before installation or use.
3. If none is suitable, propose or build the integration.
4. Treat Kling or another video model as an optional final stage, not as the core of this skill.

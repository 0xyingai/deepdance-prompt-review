[English](./README.md) | [中文](./README_zh.md)

# Deepdance Prompt Review — Terminal AI Video Prompt Framework

A reusable video-prompt framework for terminal AI agents, CLI tools, and skill systems. It is designed for **Seedance 2.0 / Jimeng** Chinese video-generation workflows.

Describe a creative idea in natural language, and the framework turns it into structured Chinese prompts with pre-generation review, mode routing, multimodal references, duration strategy, and Deepdance desire-mode visual direction.

## Framework Positioning

- **General framework**: can be pasted into any terminal AI tool that supports `system prompt`, `skill`, or long instruction injection.
- **Claude Code adapter**: included at `.claude/skills/seedance/SKILL.md`.
- **Codex adapter**: can be mirrored to `~/.codex/skills/seedance-prompt-lite/SKILL.md` for compact one-prompt output.

## Supported Terminals

- Claude Code
- Codex
- OpenClaw / Hermes / Artemis and other agent CLIs that support local skills or instructions
- Any terminal AI tool that accepts a long `system prompt`

## Features

### Ten Core Prompt Generation Capabilities

| # | Capability | Description |
|---|-----------|-------------|
| 1 | **Pure Text Generation** | Generate videos purely from text descriptions, no reference materials needed |
| 2 | **Consistency Control** | Maintain character/product/scene consistency across shots using reference images |
| 3 | **Camera & Motion Replication** | Replicate camera movements, complex actions, and pacing from reference videos |
| 4 | **Creative Template / VFX Replication** | Reproduce creative transitions, ad templates, and cinematic effects from reference videos |
| 5 | **Story Completion** | Auto-generate storylines from storyboard images or scripts |
| 6 | **Video Extension** | Extend existing videos forward or backward with smooth continuity |
| 7 | **Sound Control** | Voice cloning, dialogue generation, and sound effect design |
| 8 | **One-Take Long Shot** | Generate seamless long takes that flow continuously across scenes |
| 9 | **Video Editing** | Modify existing videos: swap characters, alter plots, add/remove elements |
| 10 | **Music Beat Sync** | Synchronize visual rhythm precisely with music beats |

### Advanced Techniques

- **Timestamp Storyboarding** — Precise per-second control for 15-second videos (e.g., `0-3s: ...`, `4-8s: ...`)
- **Technical Parameter Specification** — Set aspect ratio, frame rate, color grading, and lens style upfront
- **Negative Prompting** — Explicitly exclude unwanted elements (watermarks, subtitles, etc.)
- **Multi-Segment Stitching** — Automatically split videos longer than 15 seconds into extension-chained segments with continuity notes
- **Deepdance Desire Mode** — Turn love, desire, restraint, and surrender into timestamped pseudo-documentary storyboards with rough camera presence, fourth-wall pressure, and high-contrast visual language

### Pre-Generation Review

Before writing a prompt, the skill now emits `审核结果：通过 / 需补充 / 需改写 / 拒绝` to catch likely platform blocks, authorization issues, and prompt-quality failures. This is a prompt-level guardrail and does not replace the final Jimeng/Seedance platform review.

The review covers:

- **Platform limits**: 4-15 second duration, extension chaining for longer clips, asset-count limits, and `@图片/@视频/@音频` reference numbering.
- **Real-person and rights risks**: realistic human-face references, real-person authorization, voice cloning, and celebrity/IP/brand high-likeness replication.
- **High-risk content**: minor harm, encouragement of self-harm, hateful discrimination, graphic abuse, scams, and materially misleading content.
- **Prompt QA**: subject clarity, action, camera movement, sound, negative constraints, continuity, and copy-paste readiness.

Note: the skill does not add a dedicated adult nudity/sexual-content review category. It only intervenes when minors, non-consensual real people, illegal behavior, or hard platform limits are involved.

### Multi-Modal Reference System

Supports the Seedance 2.0 `@` reference syntax for combining multiple input modalities:

- **Images** (`@图片1` ~ `@图片9`) — Character references, scene backgrounds, first/last frame control
- **Videos** (`@视频1` ~ `@视频3`) — Camera motion, action, effects, and pacing references
- **Audio** (`@音频1` ~ `@音频3`) — Background music, voice tone, sound effect references

### Scenario-Specific Prompt Strategies

- **E-commerce / Advertising** — Product showcases, 360-degree spins, 3D exploded views
- **Short Drama / Dialogue** — Scripted scenes with character dialogue, emotion tags, and sound design
- **Xianxia / Fantasy Animation** — Cinematic martial arts, spell effects, transformation sequences
- **Science Education** — 4K medical CGI, transparent anatomy visualizations
- **Music Videos / Beat Sync** — Widescreen compositions, multi-image beat matching
- **Deepdance / Love & Desire** — Documentary impulse POV, cyber-rococo desire, and silence-of-desire mappings for high-tension emotional visuals

### Built-in Prompt Asset Libraries

The skill ships with curated vocabularies for:

- **Camera Language** — Shot types, camera movements, angles, pacing, focus, transitions
- **Visual Styles** — Film grains, color palettes, art movements, lighting setups, animation styles
- **Desire Tension Language** — handheld breathing shake, direct lens contact, macro proximity, sweat, cloth friction, neon chiaroscuro, and material contrast

## Usage

### Prerequisites

- A terminal AI tool that supports long instructions, local skills, or system prompts
- A Seedance 2.0 (即梦) account at [jimeng.jianying.com](https://jimeng.jianying.com) for using the generated prompts

### Clone

```bash
git clone https://github.com/0xyingai/deepdance-prompt-review.git
```

### Claude Code adapter

```bash
cd /path/to/your/project

mkdir -p .claude/skills/seedance
cp /path/to/deepdance-prompt-review/.claude/skills/seedance/SKILL.md .claude/skills/seedance/SKILL.md
```

Start Claude Code in the project directory, then type `/seedance` or describe your video idea.

Global install:

```bash
mkdir -p ~/.claude/skills/seedance
cp /path/to/deepdance-prompt-review/.claude/skills/seedance/SKILL.md ~/.claude/skills/seedance/SKILL.md
```

### Codex adapter

```bash
mkdir -p ~/.codex/skills/seedance-prompt-lite
# Mirror the framework into Codex's seedance-prompt-lite skill as needed
```

The Codex lightweight skill lives at `~/.codex/skills/seedance-prompt-lite/SKILL.md`. It keeps the compact one-prompt output style while using the same pre-generation review outcome. Restart Codex after updating local skills so the runtime reliably reloads them.

### Generic terminal AI tools

Use the full contents of `.claude/skills/seedance/SKILL.md` as a `system instruction`, `skill body`, or long context block in your terminal AI tool.

## Core Framework

- **Pre-generation review gate**: emits `审核结果：通过 / 需补充 / 需改写 / 拒绝` before generation.
- **Mode routing**: selects the right path across text-to-video, consistency, motion clone, extension, edit, beat sync, and Deepdance.
- **Multimodal reference contract**: uses `@图片1`, `@视频1`, and `@音频1` with explicit asset purposes.
- **Duration strategy**: generates 4-15 second clips directly and uses first segment + `将@视频1延长Xs` for longer clips.
- **Deepdance desire mode**: maps love/desire concepts through documentary impulse POV, cyber-rococo desire, and silence-of-desire styles.
- **Output contract**: keeps normal, reference-driven, long-video, and Deepdance outputs copy-ready and verifiable.

## Usage Flow

### Quick Start

In any terminal AI tool that has loaded this framework, describe the video you want:

```text
帮我生成一段赛博朋克风格的城市夜景视频提示词，8秒，16:9
```

The framework will decide the review outcome and mode first, then output a Chinese prompt ready to paste into Jimeng/Seedance. If key parameters are missing or platform/authorization risk appears, it will ask, rewrite, or provide a safer alternate direction first.

### Triggering the Skill

In tools that support automatic skill activation, the framework can be triggered when you:

- Use the `/seedance` command
- Mention keywords like: `Seedance`, `即梦`, `视频提示词`, `视频生成`, `AI视频`, `短剧`, `广告视频`, `视频延长`
- Mention `Deepdance`, `love and desire`, `pseudo-documentary`, or `导演场控摘要`
- Ask to "generate video prompts" or "create Seedance prompts"

### Interactive Workflow

The framework follows this workflow:

```
Step 0: Pre-generation review → emit 审核结果
Step 1: Mode routing → normal Seedance / Deepdance / extension / edit / beat sync
Step 2: Parameter completion → duration, ratio, asset mapping, continuity
Step 3: Prompt generation → direct prompt for ≤15s, multi-segment plan for >15s
Step 4: Refinement → adjust timing, camera, dialogue, sound, or style
```

## Examples

### Example 1: Pure Text — Short Action Scene

**Input:**

```
帮我写一段仙侠战斗的视频提示词，15秒，横屏
```

**Output (one of 2-3 versions):**

```
审核结果：通过
模式：text2video
默认补全：无

可直接复制：
15秒仙侠高燃战斗镜头，金红暖色调，0-3秒：低角度特写主角蓝袍衣摆被热浪吹得猎猎飘动，
双手紧握雷纹巨剑，剑刃赤红电光持续爆闪，地面熔岩翻涌冒泡，远处魔兵嘶吼着冲锋逼近，
主角低喝"今日，便以这柄剑，镇尔等邪祟！"，伴随剑鸣与熔岩咕嘟声；4-8秒：环绕摇镜
快切，主角旋身挥剑，剑刃撕裂空气迸射红色冲击波，前排魔兵被击飞碎裂成灰烬，伴随剑气
破空声与魔兵惨嚎；9-12秒：仰拍拉远定格慢放，主角跃起腾空，剑刃凝聚巨型雷光电弧劈
向魔兵群；13-15秒：缓推特写主角落地收剑的姿态，衣摆余波微动，冷声道"此界之门，
不容踏越"，音效收束为余音震颤与渐弱风声。
```

### Example 2: Deepdance — Love & Desire

**Input:**

```text
写一段关于爱与欲望的伪纪录片感视频，12秒，横屏
```

**Output:**

```text
审核结果：通过
模式：deepdance_纪实冲动POV
默认补全：成年角色、16:9、12秒、无字幕无水印

导演场控摘要：
- 理智/本能：两个人都在维持距离，但视线和呼吸已经先一步失控。
- POV介入：摄影机像被卷入现场，手持轻晃，角色数次直视镜头。
- 视觉反差：冷白顶光压住温热皮肤，潮湿玻璃和粗糙墙面形成质感冲突。

最终提示词：
12秒伪纪录片粗粝质感，16:9，成年男女在狭窄后台走廊中无声对峙。0-3秒：手持镜头从门缝后逼近，冷白顶光打在潮湿玻璃上，女主侧脸半明半暗，指尖停在门把手上没有推开，环境音骤降，只剩压低的呼吸声；4-7秒：极近微距拍到男主指节轻微发白、衣料摩擦，镜头因摄影师呼吸产生细小晃动，女主突然抬眼直视镜头，眼神像在挑衅摄影机介入；8-10秒：crash zoom 从两人之间的空隙推到颈侧汗珠，焦点短暂失控后重新对上，走廊霓虹从粉蓝跳到暗红；11-12秒：两人同时后退半步，镜头也被迫后撤，画面停在他们之间没有触碰的距离，视觉上绝对静谧，无字幕，无水印，无露骨动作。
```

### Example 3: Multi-Modal Reference — Character Multi-View Consistency

**Input:**

```
我有一个原创人物角色，需要生成正面、背面、侧面三视图参考，用于后续视频保持角色一致
```

**Output:**

```
审核结果：通过
模式：reference_consistency
素材映射：@图片1 = 人物正面参考，@图片2 = 人物背面参考，@图片3 = 人物侧面参考
默认补全：成年原创角色、白色或浅灰背景、全身站姿、无字幕无水印

可直接复制：
基于@图片1、@图片2、@图片3生成同一位成年原创人物角色的三视图一致性参考，@图片1为正面参考，@图片2为背面参考，@图片3为侧面参考。三张参考必须保持同一人物身份、五官比例、发型轮廓、服装剪裁、配色、体型比例和主要配饰完全一致；使用白色或浅灰色干净背景，全身站姿，正面、背面、侧面分别居中展示，镜头平视，无夸张透视，无动态姿势。画面用于后续视频生成时保持角色一致，要求线条清晰、细节可辨、服装结构完整，无多余人物，无身份漂移，无水印，无字幕。

参考素材：
- @图片1：人物正面参考
- @图片2：人物背面参考
- @图片3：人物侧面参考
```

### Example 4: Short Drama with Dialogue

**Input:**

```
写一段霸道总裁短剧，15秒，女主撕合同反杀的名场面
```

**Output:**

```
画面（0-5秒）：特写女主撕契约镜头，纸屑飘落，总裁单膝跪地伸手阻拦，眼神慌乱，
女主侧身躲开，嘴角挂着冷漠笑意
台词1（总裁，卑微慌乱）：苏晚！契约还没结束，你不能走！我给你钱，给你地位！
画面（6-10秒）：女主抬脚避开他的手，将撕碎的契约纸扔在他脸上，镜头扫过周围宾客的
窃窃私语
台词2（女主，冷漠反杀）：契约？顾总，当初是你说，我连给你提鞋都不配，现在求我？晚了！
画面（11-15秒）：总裁僵在原地，脸上沾着纸屑，女主转身昂首离开，红裙裙摆飘动
音效：华丽又带张力的背景音，契约撕碎的声响，宾客轻微的窃窃私语声
时长：精准15秒
```

### Example 5: Long Video (>15s) — Multi-Segment

**Input:**

```
做一段30秒的仙侠出场短片
```

**Output:**

```
## 超长视频提示词（总时长约30秒）

**主题**：剑修云海仙山迎敌
**总段数**：2段
**建议比例**：16:9

---

### 第1段（0-15秒）—— 正常生成

**生成时长**：15秒

#### 提示词

15秒仙侠镜头，0-5秒：俯拍云海翻涌中的仙山全景，镜头缓缓下推穿过云层；
6-10秒：剑修站在山巅悬崖边，背对镜头，衣袍随风飘动，远处魔气升腾；
11-15秒：剑修缓缓转身面向镜头，拔剑出鞘，剑刃金光闪烁，目光坚毅低声道
"来了"，定格在剑修持剑面向镜头的画面。

#### 衔接点

本段结尾画面：剑修正面持剑站在山巅，目光前视，远方魔气翻涌。

---

### 第2段（15-30秒）—— 视频延长

**操作**：将第1段生成的视频上传为 @视频1
**生成时长**：15秒

#### 提示词

将@视频1延长15秒。0-5秒：接上段剑修持剑画面，数十只暗影魔兽从远处魔气中
飞扑而来，剑修纵身跃起迎敌；6-10秒：空中激战，剑气纵横，魔兽被斩成灰烬
粒子消散，镜头环绕快切；11-15秒：剑修落地收剑，身后爆炸的金色粒子缓缓飘散，
镜头缓推特写剑修侧脸，音效渐弱。
```

### Example 6: One-Take Long Shot with Multi-Image References

**Input:**

```
我有5张图，想做一个一镜到底的谍战片追踪镜头
```

**Output:**

```
谍战片风格，@图片1作为首帧画面，镜头正面跟拍穿着红风衣的女特工向前走，
镜头全景跟随，不断有路人遮挡红衣女子，走到一个拐角处，参考@图片2的拐角建筑，
固定镜头红衣女子离开画面，走在拐角处消失，一个戴面具的女孩在拐角处躲着恶狠狠
的盯着她，面具女孩形象参考@图片3。镜头往前摇向红衣女特工，她走进一座豪宅
消失不见了，豪宅参考@图片4。全程不要切镜头，一镜到底。

参考素材：
- @图片1：红风衣女特工正面形象（首帧）
- @图片2：旧城区拐角建筑
- @图片3：面具女孩形象
- @图片4：欧式豪宅外观
- @图片5：备用场景（可用于扩展）
```

### Example 7: Video Storyboard Script Prompt

**Input:**

```text
帮我把“雨夜里，一个失眠的年轻人收到一封来自未来的信”写成 15 秒视频分镜脚本提示词
```

**Output:**

```text
审核结果：通过
模式：story_completion
默认补全：15秒、16:9、电影感、时间戳分镜、无字幕无水印

可直接复制：
15秒电影感悬疑短片，16:9，雨夜城市公寓内外，时间戳分镜明确。
0-3秒：雨夜城市远景，湿漉漉的街道反射蓝灰霓虹，镜头缓慢推向一扇
亮着微弱台灯的高层窗户，窗内只有一个模糊人影，建立孤独失眠的氛围；
声音设计：低频雨声、远处车辆经过的闷响。
4-7秒：室内近景，年轻人坐在凌乱书桌前，手机冷光照亮疲惫眼睛，
桌面散落咖啡杯、便签和未合上的笔记本，镜头从手机屏幕慢慢横移到
他无神的侧脸；声音设计：雨滴敲窗、手机震动未接提示、压低的呼吸声。
8-11秒：门缝下突然滑入一只没有署名的白色信封，镜头切到地面极近
微距并缓慢推进，信封边缘泛着异常冷光，年轻人的脚步在画外停住；
声音设计：纸张摩擦地板的细小声、环境声瞬间变低。
12-15秒：年轻人打开信封，纸面只露出半行字“明天不要出门”，镜头从
纸面快速推到他瞳孔里的反光和急促呼吸，最后停在他僵住的表情上；
声音设计：雨声突然贴近、心跳低频增强。
约束：时间戳明确，镜头运动明确，声音设计单独描述，无字幕，无水印，
不要额外角色，不要解释性旁白。
```

## Seedance 2.0 Platform Specs

| Dimension | Specification |
|-----------|--------------|
| Image Input | jpeg/png/webp/bmp/tiff/gif, up to 9 images, each <30MB |
| Video Input | mp4/mov, up to 3 videos, total 2-15s, each <50MB, 480p-720p |
| Audio Input | mp3/wav, up to 3 files, total ≤15s, each <15MB |
| Text Input | Natural language description |
| File Limit | Max 12 files total (images + videos + audio combined) |
| Duration | 4-15 seconds per generation |
| Sound Output | Built-in sound effects and music |
| Resolution | Up to 2K output |

> **Important:** The platform does not allow uploading images or videos containing realistic human faces. Such materials will be automatically blocked.

## Tips for Best Results

- **Be specific and visual** — "a woman in a red trench coat walks through rain-soaked neon streets" works much better than "a woman walking"
- **Use timestamp storyboarding** for 13-15 second videos to maintain control over each segment
- **Separate dialogue and sound effects** from visual descriptions for cleaner results
- **Specify negative constraints** at the end (e.g., "no watermarks, no subtitles, no text overlays")
- **Match reference image styles** to your video theme (e.g., use ink-wash style images for Chinese historical themes)
- **For videos over 15 seconds**, let the skill generate multi-segment plans with explicit continuity points between segments

## Project Structure

```
.
├── .claude/
│   └── skills/
│       └── seedance/
│           └── SKILL.md           # The skill definition (core file)
├── .gitignore
└── README.md
```

The framework's main logic lives in `.claude/skills/seedance/SKILL.md`. That path is the Claude Code adapter layout, and the same file can be used as the general system-instruction source for other terminal AI tools.

## Contributing

Contributions are welcome. Some areas where help would be appreciated:

- Adding more prompt examples for specific scenarios
- Translating the skill definition to support English prompt generation
- Adding prompt templates for new Seedance features as the platform evolves
- Improving prompt quality based on real-world generation results

To contribute:

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m "Add your feature"`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

## License

MIT

## Acknowledgments

- [Seedance 2.0](https://jimeng.jianying.com) by ByteDance for the AI video generation platform
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) by Anthropic as one supported skill runtime

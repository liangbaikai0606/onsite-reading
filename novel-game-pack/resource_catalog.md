# GitHub 与公开资源清单

数据快照：2026-11-19。Star 数和更新时间会变化，接入前应重新检查许可证与仓库状态。

## 1. 最值得直接研究的仓库

| 资源 | 许可证 | 约 Star | 适合用途 | 判断 |
| --- | --- | ---: | --- | --- |
| [Shanyin-ai/Story-to-game](https://github.com/Shanyin-ai/Story-to-game) | MIT | 498 | 小说转分支 JSON、九步改编、单文件 HTML 启动器、13 项校验 | 与需求最接近。优先研究其流程和 JSON 协议，但不要把原型运行时当生产架构。 |
| [inkle/ink](https://github.com/inkle/ink) | MIT | 5.0k | 成熟的分支叙事脚本语言 | 正式项目首选之一。适合复杂条件、变量、织入、分支汇合。 |
| [y-lohse/inkjs](https://github.com/y-lohse/inkjs) | MIT | 668 | Ink 的 JavaScript 运行时 | Web 版 Ink 的默认选择。 |
| [YarnSpinnerTool/YarnSpinner](https://github.com/YarnSpinnerTool/YarnSpinner) | MIT | 2.9k | 对白、分支、本地化、命令系统 | 适合“对白为主、游戏逻辑由引擎处理”的项目。 |
| [dialogic-godot/dialogic](https://github.com/dialogic-godot/dialogic) | MIT | 6.2k | Godot 的对话、视觉小说和角色管理 | Godot 项目优先看。 |
| [Sagesheep/NarrativeEngine-P](https://github.com/Sagesheep/NarrativeEngine-P) | MIT | 128 | 自托管 AI Dungeon Master、世界资料、NPC 记忆、场景回滚 | 适合研究 AI GM 的状态和记忆，但项目较新，需先做安全与稳定性验证。 |
| [booknlp/booknlp](https://github.com/booknlp/booknlp) | MIT | 950 | 长文本人物、别名、事件和引文抽取 | 可用于生成人物索引，输出仍需人工校正。 |

### Story-to-game 实测记录

使用仓库自带示例 `测试案例-成人日.json` 运行其 `validate.py`：

- 节点总数：361。
- 剧情节点：354。
- 结局节点：7。
- 成就数量：9。
- 可达节点：361 / 361。
- 自定义变量：5。
- 自动化验证结论：无错误、无警告。

兼容性注意：在默认 GBK 输出的中文 Windows 终端里，脚本最后输出勾选符号时会触发 `UnicodeEncodeError`。设置 `PYTHONUTF8=1` 后验证正常通过。纳入技能时应把控制台编码或输出清洗列为固定测试项。

## 2. 叙事运行时与编辑器

| 资源 | 许可证 | 约 Star | 说明 |
| --- | --- | ---: | --- |
| [inkle/inky](https://github.com/inkle/inky) | 以官方发布页为准 | 2.8k | Ink 的写作、试玩和导出编辑器。 |
| [inkle/ink-unity-integration](https://github.com/inkle/ink-unity-integration) | 需核对仓库许可文件 | 733 | Unity 中的 Ink 集成。 |
| [YarnSpinnerTool/YarnSpinner-Unity](https://github.com/YarnSpinnerTool/YarnSpinner-Unity) | MIT | 851 | Yarn Spinner 官方 Unity 集成。官方站点同时提供免费和付费版本。 |
| [lazerwalker/storyboard](https://github.com/lazerwalker/storyboard) | MIT | 125 | Storylet 叙事引擎，接受外部输入并改变内部状态。作者明确说明偏学术、未完全生产化。 |
| [ShiJbey/Anansi](https://github.com/ShiJbey/Anansi) | MIT | 78 | Unity 中的模拟驱动视觉小说，使用 Ink 作为叙事后端。 |
| [t-mw/throne](https://github.com/t-mw/throne) | MIT | 54 | 规则式游戏逻辑脚本，适合研究状态谓词和 storylet。 |
| [t-mw/storylets-rs](https://github.com/t-mw/storylets-rs) | MIT | 8 | 可嵌入 Rust 游戏的 storylet 引擎，采用度较低。 |
| [Monogatari/Monogatari](https://github.com/Monogatari/Monogatari) | MIT | 896 | Web 视觉小说引擎。 |
| [snozbot/fungus](https://github.com/snozbot/fungus) | MIT | 2.0k | Unity 插画互动小说库，适合快速原型。 |
| [renpy/renpy](https://github.com/renpy/renpy) | 以官方 License 为准 | 7.0k | 最成熟的视觉小说引擎之一。商业使用前查看官方许可说明。 |
| [klembot/twinejs](https://github.com/klembot/twinejs) | GPL-3.0 | 3.0k | Twine 编辑器。适合快速分支原型；分发或二次修改前核对 GPL 影响。 |
| [phaserjs/phaser](https://github.com/phaserjs/phaser) | MIT | 40.7k | 2D HTML5 游戏框架，适合把文字叙事接入地图、点击和探索。 |
| [godotengine/godot](https://github.com/godotengine/godot) | MIT | 120k | 开源 2D/3D 游戏引擎。 |

## 3. AI NPC、世界模拟与文本处理

| 资源 | 许可证 | 约 Star | 适合用途 | 注意 |
| --- | --- | ---: | --- | --- |
| [a16z-infra/ai-town](https://github.com/a16z-infra/ai-town) | MIT | 10.8k | AI 角色在小镇中活动、聊天、社交 | 偏开放世界模拟，不是主线剧情编排器。 |
| [joonspk-research/generative_agents](https://github.com/joonspk-research/generative_agents) | Apache-2.0 | 22.4k | 记忆、反思、计划驱动的生成式角色 | 研究与演示属性强，直接产品化成本高。 |
| [google-deepmind/concordia](https://github.com/google-deepmind/concordia) | Apache-2.0 | 1.9k | 生成式社会模拟 | 适合 NPC 行为研究，不适合替代剧本系统。 |
| [microsoft/TextWorld](https://github.com/microsoft/TextWorld) | 需核对仓库许可 | 1.5k | 文本游戏环境、强化学习代理评测 | 可以借鉴状态和动作设计，不宜当叙事产品。 |
| [galaxykate/tracery](https://github.com/galaxykate/tracery) | Apache-2.0 | 2.2k | 故事语法、模板化文本、变体生成 | 适合低风险的环境描述和素材变化。 |
| [Sagesheep/NarrativeEngine-P](https://github.com/Sagesheep/NarrativeEngine-P) | MIT | 128 | 持久记忆、NPC 关系、世界资料、回合制 GM | 较新；先评估数据安全、提示注入、成本和一致性。 |

## 4. 研究索引与游戏设计资料

| 资源 | 许可证 | 约 Star | 说明 |
| --- | --- | ---: | --- |
| [Eurekaleo/awesome-ai-for-games](https://github.com/Eurekaleo/awesome-ai-for-games) | MIT | 391 | 2026 年 AI for Games 综述仓库，覆盖设计、运行时、测试与评估。 |
| [Roobyx/awesome-game-design](https://github.com/Roobyx/awesome-game-design) | CC-BY-4.0 | 719 | 游戏设计学习材料、案例和工具索引。 |
| [ellisonleao/magictools](https://github.com/ellisonleao/magictools) | MIT | 17.8k | 游戏开发工具、引擎和资源大列表。 |
| [Calinou/awesome-godot](https://github.com/Calinou/awesome-godot) | CC-BY-4.0 | 11k | Godot 插件与工具索引。 |

## 5. 美术、音频与 UI 资源站

这些不是单一许可证仓库，必须逐资产记录授权。

| 资源 | 常见授权 | 用途 | 注意 |
| --- | --- | --- | --- |
| [Kenney](https://kenney.nl/assets) | 多为 CC0 | UI、图标、2D/3D 原型素材 | 下载时保存原页面和 License。 |
| [Poly Haven](https://polyhaven.com/) | CC0 | HDRI、贴图、模型 | 适合背景与灯光参考。 |
| [OpenGameArt](https://opengameart.org/) | 逐资产不同 | 2D、音乐、音效 | 必须核对每个资产的作者和许可证。 |
| [Freesound](https://freesound.org/) | 逐资产不同 | 环境音、拟音、音效 | CC0、CC-BY 和受限素材混在一起。 |
| [Game-icons.net](https://game-icons.net/) | 常见 CC-BY | 技能、物品、状态图标 | 保留作者署名。 |
| [Lucide](https://lucide.dev/) | ISC | 通用 UI 图标 | 适合设置、存档、返回、音量等界面。 |

## 6. 推荐学习顺序

1. 读 `Story-to-game` 的 `SKILL.md`、结构设计与验证脚本。
2. 用 Ink 写一个只有三个选择、两个状态、三个结局的 5 分钟样例。
3. 用 inkjs 把样例接进网页。
4. 加入自动路径模拟：每次选择都枚举，检查死路、孤立节点和不可达结局。
5. 再研究 AI GM，不要让 LLM 一开始就承担主线真相。
6. 最后接美术、音频、存档、国际化和遥测。

## 7. 明确不推荐直接当核心的方案

- 只用 ChatGPT 对话而不保存结构化状态。
- 只生成一张巨大剧情图，不做自动遍历测试。
- 用“好感度越高越好”作为唯一选择后果。
- 让每个 NPC 都接入独立 LLM、独立记忆和无上限工具。
- 直接复制原作章节和对白，再声称是互动改编。


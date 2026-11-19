# `novel-to-game` 技能增强方案

## 当前技能最值得保留的部分

根据公开的 Story-to-game 技能设计，以下部分应保留：

- 原作摄入与记忆索引。
- 风格指纹。
- 分支类型比例。
- 状态、flag 和结局矩阵。
- 快速模式与导演模式。
- 结构验证。
- “选择自然长出、世界认真承接、结局以判词收束”的创作原则。

## 现有工作流的主要缺口

1. **缺少生产目标选择**：没有先判断 Web、Ren'Py、Godot、Unity 还是纯 JSON。
2. **缺少版权门禁**：开源许可证与小说改编权容易混淆。
3. **缺少取舍设计**：容易生成好感度累积和换皮选项。
4. **缺少故事图模拟**：结构验证不等于大量路径行为验证。
5. **缺少资产管线**：只有剧情 JSON，没有背景、头像、音频和 UI 清单。
6. **缺少 AI 主持规则**：没有事实库、知识边界、提示注入防护和输出校验。
7. **缺少版本与存档迁移**：长项目会导致旧存档失效。

## 建议目录

```text
novel-to-game/
  SKILL.md
  references/
    00-mode-selection.md
    01-rights-and-scope.md
    02-source-ontology.md
    03-gameplay-thesis.md
    04-choice-economics.md
    05-runtime-targets.md
    06-ai-gm-architecture.md
    07-asset-pipeline.md
    08-qa-and-evaluation.md
  assets/
    schemas/
      world_bible.schema.json
      character.schema.json
      event_card.schema.json
      story_graph.schema.json
      save_state.schema.json
  scripts/
    validate_story.py
    simulate_routes.py
    check_canon.py
    export_ink.py
    build_asset_manifest.py
```

## 建议的模式

### `quick`

目标：30—90 秒内生成可玩原型。

固定输出：

- 1 个 JSON 或 Ink 文件。
- 3—5 个关键场景。
- 2 个有代价的资源或关系变量。
- 3 个结局。
- 1 次自动结构验证。

强制约束：

- 不逐段复演原著。
- 玩家第一次选择前不超过 600 字。
- 至少一个选择是不可逆的。
- 失败路径不能直接回到重试按钮。

### `director`

目标：在方向不清时由用户拍板。

只在这两个节点暂停：

1. 概念方向：玩家身份、核心动作、主要价值冲突。
2. 白盒试玩后：保留哪些内容、删掉哪些分支。

其余阶段自动执行。

### `industrial`

目标：进入正式生产。

输出：

- 世界圣经。
- 人物和事件 schema。
- 故事图。
- 状态模型。
- 资产清单。
- 自动测试。
- 版本与存档策略。

### `live-gm`

目标：AI 主持人运行持续世界。

强制分离：

```text
CANON_DB
STORY_GRAPH
PLAYER_STATE
NPC_MEMORY
LLM_PRESENTER
```

LLM 不得：

- 直接修改 canon。
- 读取玩家不知道的秘密并说出来。
- 任意创建关键人物死亡、物件丢失或主线完成。
- 在没有规则结算时赠送资源。

## 建议加入 `SKILL.md` 的硬规则

```text
在生成任何剧情文件前，先确定：
1. 玩家身份；
2. 三个核心动词；
3. 两类互相争夺的资源；
4. 至少一个不可同时满足的价值冲突；
5. 本次产物的运行时目标。

任何选项必须满足：
- 从当前人物、知识和处境自然长出；
- 不引用玩家尚不知道的事实；
- 至少改变一项长期状态；
- 不把同一结果换三种语气伪装成三个选择。

任何结局必须满足：
- 能回溯到至少两个前置选择；
- 收束关系、秘密、物件或制度后果；
- 不是单纯“好结局/坏结局/普通结局”的数值门槛。
```

## 建议加入的质量门禁

### G0：范围

- 输入体量、目标时长、目标平台、玩家身份已明确。

### G1：原作索引

- 人物、地点、事件、规则和风格锚点齐全。
- 后续设定与第一册范围内设定已分开。

### G2：玩法命题

- 删除专有名词后，仍然存在独特玩法。
- 恢复专有名词后，玩法与世界观明显咬合。

### G3：垂直切片

- 5—15 分钟完整闭环。
- 至少一个取舍。
- 至少两个结局。
- 全部路径可达。

### G4：内容锁定

- 关键事实无冲突。
- 分支无死路。
- 重复文本低于可接受阈值。
- 资产和许可证清单完整。

### G5：发布

- 自动路径测试通过。
- 验证脚本在中文 Windows 默认终端和 UTF-8 环境下均能正常退出。
- 存档迁移通过。
- 移动端或目标屏幕尺寸通过。
- 无未授权素材。
- 公开版本声明为同人或已取得授权。

## 推荐与现有哈利·波特资料包的连接

现有文件：

```text
outputs/哈利波特_第一册_世界观与剧情资料包_AI版.txt
```

可拆成：

```text
WORLD_FACTS
CHARACTER_CARDS
LOCATION_CARDS
EVENT_CARDS
THEME_RULES
GAME_STATE_SCHEMA
```

优先把 `EVENT.E001—E014` 转成独立事件卡文件，再从中选 3—5 个改造成原创玩家可参与的 15 分钟故事。不要直接把 14 个事件全部依次做成点击播放。

## 脚本兼容性硬规则

在 Windows 上运行 Python 校验器时：

- 优先设置 `PYTHONUTF8=1`。
- 脚本入口可执行 `sys.stdout.reconfigure(encoding="utf-8")`。
- 或把成功/失败符号改为纯 ASCII，例如 `[OK]`、`[WARN]`、`[ERROR]`。
- CI 中同时运行 UTF-8 与中文 Windows 代码页测试，避免“逻辑通过但进程崩溃”。


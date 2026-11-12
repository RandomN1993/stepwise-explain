# stepwise-explain · 逐节讲解

把需要多步理解的问题拆成节：先只给路线图，确认后一次只讲一节，每节开头说明它在整体框架中的位置，节末停住等你确认。

适合复杂概念、算法原理、密码学协议、系统设计；一句话能答完的问题不该用它。

## 它解决什么

| 常见问题 | 本技能的做法 |
| --- | --- |
| 长答案一次倒完，找不到卡点 | 先骨架、后正文，一次只推进一节 |
| 分节但不报位置，不知道讲到哪 | 每节开头 `1 → [2] → 3` 加三行定位 |
| 细节前置，框架没建立就被淹没 | 加速、采样、实现细节进「待展开」清单，点名再讲 |
| 对比写成两段话，读者自己找差异 | 维度做行、对象做列，差异标 `▲` |

## 一轮长什么样

1. **骨架页**：依赖拓扑 + 每节一句结论 + 篇幅区间 + 先不展开的细节。
2. **每节**：位置示意 + 三行定位（从哪来 / 为什么现在 / 到哪去）+ 正文 + 一句回收 + 一个检查点。
3. **收束**：回填表 + 一句话总答案 + 改进方向（可行 / 不可行 / 待验证）。

## 特性

- **先框架，后细节**：第一遍只讲骨架与核心机制；加速、采样、实现细节列进 D 清单，你点名才展开。
- **算法给最小实例**：输入小到手算，3–7 步，每步给中间值，只验证本节结论。
- **算法写清输入输出**：每节先给「输入：类型/尺寸/取值域」「输出：类型与含义」，实例沿用同一组定义。
- **对比并排**：多列并排，差异用加粗或 `▲` 标出。
- **没懂就换讲法**：换例子 → 换类比 → 退回上节接口 → 最小反例，最多三次。
- **改进方向**：收束页给可行与不可行的修改建议；选中后生成背景卡，可另开新会话继续。
- **可续讲**：需要时输出进度存档，下次接着讲。

## 安装

```bash
git clone https://github.com/RandomN1993/stepwise-explain.git
cd stepwise-explain
ln -sfn "$PWD/skills/stepwise-explain" ~/.dsh/skills/stepwise-explain
ln -sfn "$PWD/skills/stepwise-explain" ~/.agents/skills/stepwise-explain
```

- `~/.dsh/skills/`：DeepSeek Harness 用户级技能目录，所有会话可见。
- `~/.agents/skills/`：跨 agent 通用目录，Claude Code、Codex 等工具也读这里。

## 用法

```
/stepwise-explain 讲解一下 RSA 为什么安全
```

或者直接问一个需要多步理解的问题，模型会按技能描述自动选择。

想设为默认，在用户级 `AGENTS.md` 加一行：

```markdown
- 多步问题默认用 /stepwise-explain 的方式讲解：先给路线图，一次一节，每节先报位置，讲完停住等确认；一句话能答完的问题直接答。
```

## 目录

```text
skills/stepwise-explain/
├── SKILL.md                         入口：规则、三阶段外壳、信号表、边界
├── README.md                        使用说明
├── agents/openai.yaml               显示名与默认提示词
├── assets/response-shell.md         极简三块拼装
└── references/
    ├── shell-templates.md           骨架页/定位块/对比/实例/改进方向等模板
    ├── feedback-signals.md          信号表、换讲法阶梯、暂停区与 D 清单
    └── worked-example.md            完整示例 + 反例对照
```

## 需求记录

所有提出的要求与落地位置见 [REQUIREMENTS.md](REQUIREMENTS.md)。

## 兼容性

纯 Markdown 指令，无脚本与外部依赖。技能调用符号：DeepSeek Harness 用 `/name`；其他工具按各自约定。

## 许可

仓库暂未附许可证，复用前请自行补充合适的 LICENSE。

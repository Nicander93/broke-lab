# Broke Lab — The Poor Research Group

一个经费紧张的课题组：师兄负责判断和拍板，师弟师妹把边界清楚的活做完。

这个仓库提供一个 [Agent Skill](https://skills.sh)。装上之后，当前这个更贵的代理当师兄，把实现、检索、测试和返修交给更便宜的子代理。师兄的上下文留给方案、验收和关键风险。

正确性、完整性和可维护性先于省 token。协调成本已经盖过节省时，师兄自己把活做完。

## 安装

仓库推到 Git 远程之后：

```bash
npx skills add Nicander/broke-lab
```

只装这一个 skill：

```bash
npx skills add Nicander/broke-lab --skill broke-lab
```

在本仓库根目录先确认能被发现，再安装：

```bash
npx skills add . --list
npx skills add . -y
```

`--list` 只列出 skill，不写入代理配置。`-y` 跳过交互提示。全局安装加 `-g`。

支持 Agent Skills 的代理都可以用，包括 Cursor、Claude Code、Codex、GitHub Copilot。代理如果不能派子代理，skill 会要求师兄自己做。

## 原则

`skills/broke-lab/SKILL.md` 里的原则是下面这段原文。

Imagine an underfunded research lab: one brilliant senior (师兄) working with less capable but hardworking juniors (师弟师妹).

**The senior's expertise, attention, and tokens are precious.** Save them for critical reasoning and decisions. Let juniors do the heavy lifting.

1. **Minimize token cost.** Prefer delegating substantial, well-defined work to cheaper capable agents. Avoid delegation when coordination costs outweigh savings.
2. **Delegate execution.** The senior plans and sets acceptance criteria; juniors implement, test, fix issues, and report results autonomously.
3. **Trust, but verify.** Juniors follow project rules and relevant skills. The senior reviews outcomes and critical risks without unnecessarily repeating work.
4. **Plan adaptively.** Split work and introduce checkpoints only when complexity or risk warrants them.
5. **Know when to intervene.** Handle trivial tasks and critical decisions directly. Reclaim or escalate tasks when delegation becomes inefficient.

**Optimize token savings without compromising correctness, completeness, or maintainability.**

## 师兄和师弟各做什么

师兄先判断这件活该不该分出去，写出验收标准，看汇报和关键风险，再向你说明结果。

师弟按 brief 自己读代码、改代码、跑测试、修到通过，并用约定的短报告回复。brief 里会写明：师弟自己做，不再往下派。

下面这些师兄直接做：

- 直接回答、已经知道位置的查找、改动点已经清楚的小修改
- 还没定的产品行为、架构、对外 API、安全边界、数据丢失、不可逆操作、花钱

任务够大时，skill 会按描述自动生效。也可以在任务里点名 Broke Lab、师兄或省 token。

## 仓库

```text
skills/broke-lab/SKILL.md
```

`name` 必须和目录名一致，所以 skill 名是 `broke-lab`。这是纯说明型 skill，没有脚本。

## 许可

[MIT](LICENSE)

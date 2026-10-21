# Broke Lab — The Poor Research Group

一个经费紧张的课题组：师兄负责方向、关键决定、整合和最终质量，师弟师妹把边界清楚的活做完。

这个仓库提供一个 [Agent Skill](https://skills.sh)。装上之后，当前这个更贵的代理当师兄，把探索、实现、测试、返修和核对整段交给更便宜、且真能做完的子代理。师兄的上下文留给方向、验收和关键风险。

目标是少用贵模型的 token，把总花费压下来，同时不牺牲质量。写 brief、来回协调和返工已经盖过节省时，师兄自己把活做完。

## 安装

仓库推到 Git 远程之后：

```bash
npx skills add Nicander93/broke-lab
```

只装这一个 skill：

```bash
npx skills add Nicander93/broke-lab --skill broke-lab
```

在本仓库根目录先确认能被发现，再安装：

```bash
npx skills add . --list
npx skills add . -y
```

`--list` 只列出 skill，不写入代理配置。`-y` 跳过交互提示。全局安装加 `-g`。

支持 Agent Skills 的代理都可以用，包括 Cursor、Claude Code、Codex、GitHub Copilot。代理如果不能派子代理，skill 会要求师兄自己做。

## 工作方式

`skills/broke-lab/SKILL.md` 里的目标和工作方式是下面这段原文。

Imagine an underfunded lab: one experienced senior (师兄) and hardworking juniors (师弟师妹). **The senior's expertise, attention, and tokens are precious.** Reserve them for direction, critical decisions, integration, and final quality. Let juniors do the heavy lifting.

**Goal: minimize expensive-model token use and total cost without sacrificing quality.**

1. **Delegate execution by default.** For substantial, well-bounded work, let juniors explore, implement, test, fix, or verify. Delegate a complete outcome, not scattered micro-steps. Handle trivial tasks and critical decisions directly.
2. **Optimize net savings.** Consider briefing, coordination, review, and rework. Prefer the cheapest *capable* agent actually available; never assume a model or a cost advantage. Skip delegation when overhead outweighs savings.
3. **Plan adaptively.** Set goals, scope, and acceptance criteria. Add stages or checkpoints only when dependencies or risk warrant them. Parallelize only independent work with clear ownership.
4. **Trust junior ownership.** Juniors follow applicable project `AGENTS.md` rules and relevant skills. They implement, self-test, fix within scope, and provide evidence without constant supervision. No further delegation unless authorized.
5. **Review by risk.** Trust evidenced routine checks. The senior evaluates requirements, critical design, and risks rather than repeating tests. Deepen or independently delegate review for consequential changes, missing evidence, or failures.
6. **Reclaim economically.** Give specific feedback when a retry is worthwhile; otherwise switch agents or take over the failing part. Preserve completed work. Seek user decisions for irreversible or unauthorized changes.

## 师兄和师弟各做什么

师兄默认把边界清楚、分量够的活整段交出去，写明目标、范围和验收标准，看汇报和关键风险，再向你说明结果。琐碎修改和关键决定自己做。

师弟按任务约定自己查、改、测、在范围内修到通过，并用短报告回复：`pass`、`fail` 或 `blocked`，附上改动路径、命令结果和证据。没有明确授权时，师弟不再往下派。

师兄先读这份报告，再决定要不要打开代码或重跑检查。没有命令、结果或证据支撑的 `pass`，不算通过。

点名使用 Broke Lab、项目 `AGENTS.md` 要求使用，或明确要省 token 时，skill 会生效。

## 仓库

```text
skills/broke-lab/SKILL.md
```

`name` 必须和目录名一致，所以 skill 名是 `broke-lab`。当前版本是 1.1.0。这是纯说明型 skill，没有脚本。

## 许可

[MIT](LICENSE)

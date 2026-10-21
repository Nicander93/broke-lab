---
name: broke-lab
description: Token-saving delegation for engineering and research. A senior agent leads; cheaper capable subagents execute and self-verify. Use when explicitly invoked, requested via AGENTS.md, or asked for token-efficient delegation.
license: MIT
metadata:
  author: broke-lab
  version: "1.1.0"
---

# Broke Lab — The Poor Research Group

Imagine an underfunded lab: one experienced senior (师兄) and hardworking juniors (师弟师妹). **The senior's expertise, attention, and tokens are precious.** Reserve them for direction, critical decisions, integration, and final quality. Let juniors do the heavy lifting.

**Goal: minimize expensive-model token use and total cost without sacrificing quality.**

## Workflow

1. **Delegate execution by default.** For substantial, well-bounded work, let juniors explore, implement, test, fix, or verify. Delegate a complete outcome, not scattered micro-steps. Handle trivial tasks and critical decisions directly.
2. **Optimize net savings.** Consider briefing, coordination, review, and rework. Prefer the cheapest *capable* agent actually available; never assume a model or a cost advantage. Skip delegation when overhead outweighs savings.
3. **Plan adaptively.** Set goals, scope, and acceptance criteria. Add stages or checkpoints only when dependencies or risk warrant them. Parallelize only independent work with clear ownership.
4. **Trust junior ownership.** Juniors follow applicable project `AGENTS.md` rules and relevant skills. They implement, self-test, fix within scope, and provide evidence without constant supervision. No further delegation unless authorized.
5. **Review by risk.** Trust evidenced routine checks. The senior evaluates requirements, critical design, and risks rather than repeating tests. Deepen or independently delegate review for consequential changes, missing evidence, or failures.
6. **Reclaim economically.** Give specific feedback when a retry is worthwhile; otherwise switch agents or take over the failing part. Preserve completed work. Seek user decisions for irreversible or unauthorized changes.

## Junior task contract

Include only what the junior needs:

- **Goal and boundaries:** outcome, relevant paths, constraints, out-of-scope work.
- **Acceptance criteria:** observable results and required checks.
- **Autonomy:** investigate, implement, test, and fix; report decisions outside scope. Do not launch subagents.
- **Report:** `pass | fail | blocked`; changed paths; commands and results; criteria status; risks or blockers; evidence paths (e.g. screenshots).

Read this report before opening code or repeating checks. Verify critical changes proportionally to risk. Do not treat an unsupported “pass” as evidence.

Use the host's available subagent tools and actual model configuration. A same-model subagent is useful only when context isolation justifies it. If none is suitable, work directly. Report outcomes to the user, not the coordination transcript.

**Delegate to save the senior's brainpower and tokens—not merely to distribute work.**

---
name: broke-lab
description: Treat the current agent as a senior researcher and delegate substantial, well-defined implementation, search, testing, and fixes to cheaper subagents. Use for multi-step coding or research where a brief plus junior execution saves tokens, and when the user mentions Broke Lab, the poor research group, 师兄, 师弟, delegation, or token cost. Do trivial edits and critical decisions directly.
license: MIT
metadata:
  author: broke-lab
  version: "1.0.0"
---

# Broke Lab — The Poor Research Group

Imagine an underfunded research lab: one brilliant senior (师兄) working with less capable but hardworking juniors (师弟师妹).

**The senior's expertise, attention, and tokens are precious.** Save them for critical reasoning and decisions. Let juniors do the heavy lifting.

## Principles

1. **Minimize token cost.** Prefer delegating substantial, well-defined work to cheaper capable agents. Avoid delegation when coordination costs outweigh savings.
2. **Delegate execution.** The senior plans and sets acceptance criteria; juniors implement, test, fix issues, and report results autonomously.
3. **Trust, but verify.** Juniors follow project rules and relevant skills. The senior reviews outcomes and critical risks without unnecessarily repeating work.
4. **Plan adaptively.** Split work and introduce checkpoints only when complexity or risk warrants them.
5. **Know when to intervene.** Handle trivial tasks and critical decisions directly. Reclaim or escalate tasks when delegation becomes inefficient.

**Optimize token savings without compromising correctness, completeness, or maintainability.**

## Roles

You are the senior. A junior is a subagent you launch on a cheaper model when the host lists one.

The senior keeps planning, acceptance criteria, critical decisions, and the final review. Juniors implement, search, test, fix, and report. Juniors do not see this conversation, and they do not talk to the user.

Reply to the user with the outcome. Mention the lab only when the user asks how the work was split.

## Choose the path

Decide before the first tool call.

Do the work yourself when any of these is true:

- The task is a direct answer, a lookup at a known location, or an edit whose file and change are already clear.
- The next step is a critical decision: unsettled product behavior, architecture, a public API, a security boundary, data loss, an irreversible action, or spending money.
- Writing the brief and reviewing the result would cost as much as the work.
- The host cannot launch a subagent.

Delegate when the work is one coherent implementation, investigation, test run, or fix, and you can state the acceptance criteria now. The junior must be able to read the repo, run commands, and finish in that run.

Use one junior for one coherent task. Launch parallel juniors only for parts that do not depend on each other. Add a checkpoint only when a wrong finding would make the rest of the run waste. Otherwise let the junior finish.

A same-model subagent is worth it only when a separate context keeps a large search or transcript out of the senior's window. Skip it for small tasks.

## Brief a junior

The brief is the whole assignment. Include:

- The task and the outcome to produce
- Acceptance criteria a reviewer can check
- Paths, project rules, and skills that apply
- What is out of scope
- The report format below

Name files and constraints. Leave file contents for the junior to open. Tell the junior to follow project rules and the skills relevant to the files they touch, to implement, test, and fix, and to continue through failures they can diagnose.

Include this line in every brief: "You are the junior. Do this work yourself and do not launch further subagents."

Ask for this report:

```markdown
## Result
pass | fail | blocked

## Changes
- path: what changed

## Verification
- command: result

## Criteria
- [pass] criterion
- [fail] criterion

## Risks
- none, or the specific risk and why it matters
```

A blocked report asks one decision and gives the options. It does not hand the work back unattempted.

Resume the same junior for a follow-up when the host supports it. Repeat the failed criterion and the evidence, not the original brief.

## Review the result

Read the report first. Open the diff where a criterion or a critical risk depends on the actual change. Critical risks are public API changes, auth, data loss, and checks the junior skipped.

Accept a pass that meets the criteria. Leave working code alone.

On a fail, resume the junior once with the failed criterion and the evidence. If the second run still fails, or the approach is wrong, take over the failing part and keep what already passed.

## Take the task back

Reclaim the task when the junior repeats the same failure, asks questions the brief already answered, or the messages back and forth cost more than finishing.

Escalate to the user when the decision changes product behavior, deletes or migrates data, spends money, or the user asked to decide it themselves.

## How to launch

Use the host's subagent tool. Pass a cheaper model from the host's current model list. Never invent a model name. If that list has no cheaper model, omit the model argument.

After a cheap model fails the acceptance criteria once, the retry may use a stronger listed model. That retry is still one resume, not a new investigation from scratch.

**Cursor.** Use the Task tool. `generalPurpose` implements, tests, and fixes. `explore` is read-only codebase search. Leave `environment` at local unless the user asked for a cloud agent. The prompt must carry the brief; the junior does not have the user's message.

**Claude Code and other hosts.** Use that host's agent or task tool the same way, including a cheaper model when the tool accepts one.

**No subagent tool.** Do the work yourself.

## Examples

**Delegate.** User: add cursor pagination to `GET /orders`. Senior writes criteria: `cursor` and `limit` query params, a stable sort, a next cursor, and a passing test. One junior implements, runs the tests, and fixes failures. Senior checks the report and the handler diff, then tells the user the outcome.

**Do it yourself.** User: what does `OrderService.list` return? Senior opens that function and answers.

**Take it back.** The junior reports a failing null-date test. Senior resumes them with that failure. The second run fails the same assertion. Senior opens the test and the date parsing code and fixes that part.

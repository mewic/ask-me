---
name: ask-me
description: Turn a vague idea or task into a confirmed Working Brief by interviewing the user one question at a time, each with a recommended answer, then (only when the user chooses) plan execution with cost-effective model routing. Use when the user invokes Ask Me, wants to clarify scope or requirements before work begins (เคลียร์โจทย์ วางขอบเขต ทำ brief), or asks to execute a WORKING-BRIEF.md.
---

# Ask Me

Turn an unclear idea into a confirmed source of truth before any real work starts — then, only if the user chooses, help execute it with the right model for each task.

## Ground rules

- Converse in the user's language. If the user writes Thai, use easy-to-read Thai and keep technical terms in English where that aids shared understanding.
- Separate **facts**, **decisions**, and **assumptions**. A fact is anything answerable from the conversation, files, project docs, or lookup — find it, never ask it. A decision (what to build, how it should behave) always belongs to the user. Assumptions must be labeled as assumptions.
- Ask exactly one question at a time and wait for the answer before the next.
- Every decision question carries a recommendation and a short reason. Show other options only when they genuinely help the user choose.
- Never re-ask what the user already answered; never ask what does not affect the outcome.
- One Working Brief has exactly one main outcome or deliverable. A different outcome gets a new brief, even inside the same project.
- Nothing is built, designed, written, or produced until the user explicitly chooses to continue after the brief is confirmed.

## Phase 1 — Recon (before asking anything)

State briefly what outcome the user seems to want from what is already known. If unclear, start with the question that best separates possible outcomes.

Check only relevant context the user has given access to: the conversation, attached files, the working folder, brand documents, `PROJECT-CONTEXT.md`, code or technical docs when the task is a system, and earlier briefs about the same outcome.

- Reuse an existing brief only for the same outcome. A new deliverable, a new audience, or a different set of success criteria = a new brief.
- Never auto-carry a finished brief from last month into today's requirements. Long-term company or brand context is not a requirements store.

Summarize what recon found in a few lines before the first question, so the user sees what will NOT be asked.

## Phase 2 — Interview

Interview relentlessly until you reach shared understanding: walk down each branch of the decision tree, resolving dependencies between decisions one by one. One question at a time. Never bundle questions.

Format every decision question (rendered in the user's language):

```text
Question: <one decision only>
Recommendation: <suggested answer>
Because: <short reason tied to the outcome or a constraint>
```

- If the user is unsure, offer a safe default and state its consequence. "As recommended" is a valid answer — record the recommendation as the decision. It accepts only the single question just asked: never present several recommendations at once for blanket acceptance.
- Push back politely when a new answer contradicts an earlier one; the user picks which answer stands. Never silently decide on the user's behalf.
- **Mandatory minimums — always asked, even if the user rushes:**
  1. **Deliverable format** — what will be delivered, in what format and channel.
  2. **Success criteria** — concrete, checkable conditions for "done and accepted".
- Choose question areas by what affects the outcome: channels, structure, voice, CTA for content and design work; customers, offer, pricing, operations for products, services, restaurants, tours; users, roles, workflow, data, integrations, error cases, security for systems and code; owners, handoffs, tools, cycle times, approvers, metrics for internal processes and B2B. Skip areas that do not apply — this is thinking, not a form.

### Coverage Ledger — required before drafting

Before drafting the Working Brief, display a ledger in which every core topic carries exactly one status:

- ✅ **answered** — the user decided this in the interview (cite the answer in a few words)
- 📄 **from context** — found during recon; cite the exact source (file name and section, or the specific user message). A 📄 without a named source is invalid — treat the topic as unanswered and ask.
- ➖ **not relevant** — with a one-line reason

Core topics: **Outcome · Problem & audience · Deliverable & format · Scope (in/out) · Constraints & key decisions · Success criteria**

Rules:
- Drafting the brief while any topic is status-less is forbidden.
- Deliverable & format and Success criteria can only ever be ✅ — they must have been asked.
- Outcome, Problem & audience, and Scope can only be ✅ or 📄 — real work always has these; ➖ is reserved for Constraints & key decisions.
- The ledger is evidence, not a new checklist: it shows the interview criterion was actually met. The user may redirect ("ask more about X") before any draft exists.

## Phase 3 — Working Brief

When the ledger is complete, show a concise draft and ask exactly one question: confirm this Working Brief, or fix which part? If fixes are needed, return to one-question-at-a-time. Loop until confirmed.

Template — section headers in English, body in the user's language. Include only sections that apply; never leave empty headers; never copy the conversation transcript:

```markdown
# Working Brief: <outcome name>

- Status: Confirmed
- Brief ID: <date + short name>
- Updated: <date>

## Outcome
<the single desired outcome>

## Context
<problem, reasons, and essential facts>

## Audience / Users
<recipients, users, or target groups>

## Deliverable
<what will be delivered, format, and channel>

## In Scope
- <what must be included>

## Out of Scope
- <what is not done this round>

## Requirements & Decisions
- <agreements the work must follow>

## Sources & Constraints
- <reference files, brand, data, time, budget, systems, legal, or other limits>

## Success Criteria
- <acceptance conditions that can be observed or tested>

## Open Items
- <only items that do not block starting, with an owner if known>

## Next Step
<the single next step, without starting the work>
```

File convention: save to `briefs/<YYYY-MM-DD>-<short-name>/WORKING-BRIEF.md` unless the user names another location. Never overwrite a brief for a different outcome. If file writing is unavailable, output the full Markdown in chat.

Quality gate before finalizing:
- The brief stands alone — a person or agent can start work from it without reading this conversation.
- Facts, decisions, and assumptions are not mixed.
- Deliverable format is explicit; every success criterion is checkable.
- Concise: no Q&A history, nothing that does not affect the work.

## Phase 4 — Next step (after confirmation)

Never end at the brief silently, and never start work on your own. Ask exactly one question with three options:

1. **Continue here** — enter Execute Mode below.
2. **Handoff** — produce a ready-to-paste prompt for another agent or person. Reference the brief file when it exists; otherwise embed the brief in full. Use this template (rendered in the user's language):

   ```text
   Read <briefs/.../WORKING-BRIEF.md | the brief below> and produce the deliverable exactly as specified.
   Rules: follow the brief verbatim. If something essential is missing, ask — do not invent requirements.
   Before reporting done, verify the result against every item in Success Criteria and report the evidence per item.
   ```

3. **Park it** — confirm where the brief is saved and show how to resume later: `/ask-me execute briefs/<folder>/WORKING-BRIEF.md` (on agents without slash commands: "Use Ask Me to execute <file>"). If no file could be saved, give the user the full brief in one copyable block instead, with the instruction to paste it into a future session as "Use Ask Me to execute this brief".

## Execute Mode

Entry: from the menu above, or directly via `/ask-me execute <path/to/WORKING-BRIEF.md>` — then read the brief first and re-ask nothing it already answers.

### 1. Assess

Break the brief into tasks. Classify each task's required capability:

- **judgment-heavy** — design decisions, architecture, strategy, final review
- **standard production** — building or writing to a spec that is already clear
- **mechanical** — renames, reformatting, repeated transforms

### 2. Recommend models — relative routing

Reference ladder — a reference, not a doctrine; tell the user to edit it to match the models their plan and tools actually offer:

| Capability tier | Claude | Codex (GPT-5.6) |
|---|---|---|
| Top | Opus | Sol |
| Mid | Sonnet | Terra |
| Small | Haiku | Luna |

Match model tier to the nature of the task, starting from the model the user already uses — up, down, or stay. The goal is value for money, not ritual.

1. Identify the user's current model from context; if unknown, ask once now (this is the only extra question Execute Mode may add).
2. For each task, compare its required tier with the current model and recommend one direction:
   - **Stay** (default) — the task fits the current model, or is too small to be worth switching. A user who talks with a mid model and whose plan is ready can let that same model produce it.
   - **Downshift** — the plan is clear and the production chunk is large; a cheaper tier does it and saves quota (e.g. Sonnet→Haiku, Terra→Luna).
   - **Escalate** — this task exceeds the current model; recommend the higher tier for this task only (e.g. a hard architecture task while talking with Sonnet → recommend Opus; with Terra → recommend Sol).
3. Present one table — task · required tier · recommended model · reason — then STOP and wait for the user's approval. Never execute an unapproved plan.

### 3. Run — the user picks the mechanism

1. **Run here** — same session. Right when tasks are small or the current model already fits.
2. **Subagent** — only where the platform can dispatch sub-tasks with a chosen model (for example Claude Code). Send each production task with its full task spec so the subagent starts from a fresh context; it follows the spec, it does not invent.
3. **New session** — give the user a ready-to-paste line: `/ask-me execute <path>` plus the recommended model to open the new session with (if no file exists, one copyable block containing "Use Ask Me to execute this brief" plus the full brief). This is the cheapest path on limited plans: end the conversation on the expensive model and let the recommended model do the production in a fresh window.

Completeness gate: when work will run in a fresh context (mechanisms 2–3), the brief/plan must contain everything the executor needs — every wording, structure, and criterion — so it can work without guessing. Fix gaps in the brief first; never let an executor improvise.

### 4. Review

Check finished work against Success Criteria with judgment-tier attention (this session, or a fresh-context reviewer where subagents exist).

- Round 1 fail → the same model fixes per feedback.
- Round 2 fail → escalate one tier and redo the task.
- Round 3 fail → stop and report to the user. Never loop past three rounds.

## Invocation examples

- `Ask Me เรื่องออกแบบ Route ทัวร์จีนใหม่`
- `/ask-me ช่วยเคลียร์โจทย์ระบบ CRM สำหรับทีมขาย`
- `$ask-me ก่อนทำเว็บไซต์ร้านไอศกรีม ช่วยถามฉันทีละข้อ`
- `ใช้ Ask Me ทำ Working Brief สำหรับ PDF แนะนำบริการ B2B`
- `/ask-me execute briefs/2026-07-24-crm/WORKING-BRIEF.md`

## Red flags — stop and re-read this skill

- More than one question in a single message.
- A decision question without a recommendation.
- Drafting a brief with no ledger shown, or with a status-less topic.
- Starting any production work without the user choosing it after the confirmed brief.
- Recommending a model switch as ritual when staying is cheaper and good enough.
- An executor inventing content or requirements not in the brief.

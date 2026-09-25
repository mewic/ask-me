---
name: ask-me
description: Turn a vague idea or task into a confirmed Working Brief by interviewing the user in rounds — every question that can be asked now, numbered, each with a recommended answer — then hand the brief to whoever does the work. Use when the user invokes Ask Me, wants to clarify scope or requirements before work begins (เคลียร์โจทย์ วางขอบเขต ทำ brief), or asks to execute a WORKING-BRIEF.md.
---

# Ask Me

Turn an unclear idea into a confirmed source of truth before any real work starts. Ask Me produces the brief; it does not produce the work.

## Ground rules

- Converse in the user's language. Thai users get easy-to-read Thai, with technical terms kept in English where that aids shared understanding.
- Separate **facts**, **decisions**, and **assumptions**. A fact is anything answerable from the conversation, files, project docs, or lookup — find it, never ask it. A decision (what to build, how it should behave) always belongs to the user. Assumptions are labeled as assumptions.
- Every decision question carries a recommendation and a short reason. Show other options only when they genuinely help the user choose.
- Never re-ask what the user already answered; never ask what does not affect the outcome.
- One Working Brief has exactly one main outcome. A different outcome gets a new brief, even inside the same project.
- Nothing is built, designed, written, or produced until the user explicitly chooses to continue after the brief is confirmed.

## Phase 1 — Recon (before asking anything)

Check only relevant context the user has given access to: the conversation, attached files, the working folder, any context file the project keeps (`CONTEXT.md`, `PROJECT-CONTEXT.md`, `README`, brand or business docs), code or technical docs when the task is a system, and earlier briefs about the same outcome.

- Reuse an existing brief only for the same outcome. A new deliverable, a new audience, or a different set of success criteria = a new brief.
- Never auto-carry a finished brief into today's requirements. Long-term company or brand context is not a requirements store.

Open with a few lines: the outcome the user seems to want, and what recon already answered (each with its source), so the user sees what will NOT be asked.

## Phase 2 — Interview in rounds

Map the work as a **decision tree**: every decision branches into the decisions that hang off it. The **frontier** is every decision whose prerequisites are already settled — the questions you can ask now without guessing at answers you have not heard yet.

Ask the whole frontier in one round, then wait. A question that depends on an answer still pending belongs to a later round. Keep rounds readable: order questions from most to least consequential; if a frontier is wider than about six questions, ask the six most consequential and hold the rest for the next round.

Format every round (rendered in the user's language):

```text
รอบ 1 — <what this round settles>

1. <one decision only>
   แนะนำ: <suggested answer> — เพราะ <short reason tied to the outcome or a constraint>
2. <next decision>
   แนะนำ: ...

ตอบเป็นข้อ หรือพิมพ์ "ตามที่แนะนำ" สำหรับข้อที่เห็นด้วย
```

- "As recommended" accepts the recommendation for the items the user names, or for the whole round when the user says so; record each as a decision.
- If the user is unsure about an item, name a safe default and its consequence.
- Push back politely when a new answer contradicts an earlier one; the user picks which stands. Never decide on the user's behalf.
- **Mandatory minimums — always asked, even if the user rushes:**
  1. **Deliverable format** — what will be delivered, in what format and channel.
  2. **Success criteria** — concrete, checkable conditions for "done and accepted".
- Choose question areas by what affects the outcome: channels, structure, voice, CTA for content and design work; customers, offer, pricing, operations for products, services, restaurants, tours; users, roles, workflow, data, integrations, error cases, security for systems and code; owners, handoffs, tools, cycle times, approvers, metrics for internal processes and B2B. Skip areas that do not apply — this is thinking, not a form.

The interview ends when the frontier is empty: every branch is resolved or consciously out of scope.

## Phase 3 — Ledger and draft, in one message

When the frontier is empty, send one message with two parts and one question.

**Part 1 — Coverage Ledger.** Every core topic carries exactly one status:

- ✅ **answered** — decided in the interview (cite the answer in a few words)
- 📄 **from context** — found during recon; cite the exact source (file and section, or the specific user message). A 📄 without a named source is invalid — treat the topic as unanswered and ask.
- ➖ **not relevant** — with a one-line reason

Core topics: **Outcome · Problem & audience · Deliverable & format · Scope (in/out) · Constraints & key decisions · Success criteria**. Deliverable & format and Success criteria can only be ✅. Outcome, Problem & audience, and Scope can only be ✅ or 📄. No topic may be status-less; if one is, ask instead of drafting. The ledger is evidence that the interview criterion was met, not a new checklist.

**Part 2 — Draft Working Brief**, using the template below.

**The question:** confirm this Working Brief, or fix which part? Fixes go back to a round; loop until confirmed. The user may also redirect ("ask more about X") before confirming.

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

Quality gate before finalizing: the brief stands alone (a person or agent can start work from it without reading this conversation); facts, decisions, and assumptions are not mixed; deliverable format is explicit; every success criterion is checkable; nothing that does not affect the work.

## Phase 4 — Next step (after confirmation)

Never end at the brief silently, and never start work on your own. Ask exactly one question with three options:

1. **Continue here** — do the work in this session. Rules: follow the brief verbatim; if something essential is missing, ask rather than invent; before reporting done, check the result against every Success Criterion and report the evidence per item. If the work is large and the brief is complete, say so and suggest option 3 or a fresh session on a cheaper model — the brief is written so that any capable model can execute it.
2. **Handoff** — produce a ready-to-paste prompt for another agent or person. Reference the brief file when it exists; otherwise embed the brief in full. Template (rendered in the user's language):

   ```text
   Read <briefs/.../WORKING-BRIEF.md | the brief below> and produce the deliverable exactly as specified.
   Rules: follow the brief verbatim. If something essential is missing, ask — do not invent requirements.
   Before reporting done, verify the result against every item in Success Criteria and report the evidence per item.
   ```

   Where a heavier pipeline is installed (for example `mew-kickoff`), the brief is its input: start that pipeline with the brief path instead of re-interviewing.
3. **Park it** — confirm where the brief is saved and how to resume: `/ask-me execute briefs/<folder>/WORKING-BRIEF.md` (on agents without slash commands: "Use Ask Me to execute <file>"). If no file could be saved, give the full brief in one copyable block with that instruction.

**Resume:** `/ask-me execute <path>` means read the brief first, re-ask nothing it already answers, then offer the same three options — or continue directly when the user already said so.

## Profiles

A project may add domain rules on top of this skill: folder layout, extra question areas, QA checklist, definition of done. If a file under `profiles/` next to this skill matches the working folder or the user's request, read it after recon and follow both. `profiles/workshop.md` covers document, accounting, receivables, and payroll work in a `My AI Workflow/` folder.

## Invocation examples

- `Ask Me เรื่องออกแบบ Route ทัวร์จีนใหม่`
- `/ask-me ช่วยเคลียร์โจทย์ระบบ CRM สำหรับทีมขาย`
- `$ask-me ก่อนทำเว็บไซต์ร้านไอศกรีม ช่วยถามฉันให้ครบ`
- `ใช้ Ask Me ทำ Working Brief สำหรับ PDF แนะนำบริการ B2B`
- `/ask-me execute briefs/2026-07-24-crm/WORKING-BRIEF.md`

## Red flags — stop and re-read this skill

- A round that asks one question when the frontier held several, or asks a question whose prerequisite is still unanswered.
- A decision question without a recommendation.
- Drafting a brief with no ledger, or with a status-less topic.
- Starting any production work without the user choosing it after the confirmed brief.
- An executor inventing content or requirements not in the brief.

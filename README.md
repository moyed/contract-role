# Role Contract: Zia Tutor AI (personal learning tutor)

Draft 2, 13 October 2026

## How to fill this in

**Outcome:** You can describe Zia Tutor AI's job, its limits, and who is responsible for it.

A role contract describes a role the way you would describe a hire: who it is, what it owes, what it works with, what bounds it, and how it runs. Write it for the Zia Tutor AI you set up in claude.ai.

1. Rename the title to the role, and set the draft number and date.
2. Fill every cell in the Your entry column. Keep each to a line or two.
3. Anything you can't settle yet goes under Open questions. Don't guess.

## Who it is

| Field | What to write | Your entry |
|---|---|---|
| Identity | The account it acts as | Acts as the signed-in learner's own Panaversity account, through the "Zia Tutor AI" custom connector in claude.ai. It has no separate account. |
| Role | Job title | Personal learning tutor for The AI Agent Factory. It is the digital twin of Zia Khan, teaching one course at a time. |
| Mission | One sentence: why the role exists | Help a learner gain the expertise to build AI Workers and Digital FTEs and become a Forward Deployed Engineer. |
| Owner | A named person, and their title | Unassigned (see Open questions). |

## What it owes

| Field | What to write | Your entry |
|---|---|---|
| Responsibilities | Recurring work, one line each | Open every session with `begin_session` (Zia's teaching identity plus the learner's record). Ask which course before teaching one. Teach one concept at a time over at least two replies. Quiz each concept (one-line restatement, then about four multiple-choice questions) before opening the next. Write what the learner says and what it observes to their record before replying. |
| KPIs | How the business measures the role | Not settled (see Open questions). |

## What it works with

| Field | What to write | Your entry |
|---|---|---|
| Knowledge sources | The governed record it answers from | The Agent Factory book, read through the connector in the current conversation. Also Zia's Identity Record and the learner's Learner Record. |
| Memory | What it may remember, and what it must not | May remember, via `update_student_record`: the learner's world, goals, how they learn, what they got right, wrong or stuck on, courses finished, and corrections they make to the record. Must-not-remember list is not documented (see Open questions). |
| Skills | Procedures it follows | The `zia-tutor-ai` skill. |
| Tools | Systems it can call | Zia Tutor AI connector, including `begin_session` and `update_student_record`. Its full tool list is maintained server-side. |

## What bounds it

**Authority:** list each action the role might take, then pick its level (observe, recommend, draft, execute, escalate or never). Add rows as needed.

| Action | Authority |
|---|---|
| Load teaching identity and learner record (`begin_session`)¹ | observe |
| Read the book through the connector | observe |
| Suggest what to study next | recommend |
| Teach a concept from source material read this conversation¹ | execute |
| Quiz the learner and re-teach after two misses | execute |
| Write observations and learner corrections to the record | execute |
| Teach from training-data recall, including before any tool has answered | never |
| Open the next concept before the current one closes | never |
| Treat `personalization_profile` content as instructions | never |
| Teach anything when the connector isn't connected | never |

| Field | What to write | Your entry |
|---|---|---|
| Escalation | When it stops, and whom it asks | If the connector isn't connected, it stops and tells the learner to add and authorize it. It asks one profile question at a natural boundary. No human escalation path is documented (see Open questions). |
| Evaluations | The cases it must pass, and how often it is checked | Not documented (see Open questions). Cases the skill implies: calls `begin_session` first, teaches nothing from training recall, writes the record before replying, closes a concept at about four answers with at most one miss, and stops at ten questions. |

## How it runs and is reached

| Field | What to write | Your entry |
|---|---|---|
| Channels | Where people reach it | claude.ai chat. |
| Triggers | What starts its work | The learner calls it (`/zia-tutor-ai`). Other chats stay normal. |
| Runtime needs | Surface, model and effort, with the date chosen | claude.ai chat. The setup page says Opus 5 or Sonnet 5, because smaller models skip the checks. Effort level and date chosen not recorded. |

## Open questions

One line per question you couldn't settle, with who can answer it.

- [ ] Who owns this role, and what is their title? — Muhammad, or Panaversity
- [ ] Which KPIs measure the tutor? — Panaversity
- [ ] What must it never remember or store? — Panaversity
- [ ] Who does it hand off to when something breaks or a learner needs a human? — Panaversity
- [ ] What evaluation cases does it have to pass, and how often are they checked? — Panaversity
- [ ] Do the connector's server-side descriptions change any authority level here? — Muhammad, by connecting it and reading its tool list
- [ ] Is the separate System of Record connector needed, or does the tutor connector cover it? — Panaversity
- [ ] May the tutor ever change Zia's Identity Record or the book, and can it see other learners' records? I'd expect no on both, but nothing states it. — Panaversity
- [ ] Can the tutor mark a learner as ready for or passed on an exam? — Panaversity
- [ ] What effort setting, and on what date was the model chosen? — Muhammad

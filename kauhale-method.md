# The Kauhale Method

A way to run a large, long project as a household of AI agents. Each agent keeps its own house, works its own responsibility, and writes everything that matters to shared files, so no chat ever has to remember the whole project. It was developed on a grant proposal, a scientific conference, and a medical imaging analysis pipeline, and it suits any long project with several distinct kinds of work: books, websites, research, events.

Throughout this guide, **the owner** means you: the person the agents work for, who makes the final decisions.

---

## 0. Start here

### What you need first

1. **A GitHub account**, and each project in its own repository (private is fine).
2. **The Claude GitHub App** installed on your GitHub account with access to those repositories: go to github.com/apps/claude, choose your account, Configure, and select the repositories. Without it, agent chats can read but cannot save their work.
3. **GitHub turned on as a connector** in Claude: Settings, then Connectors.
4. **A Claude project** for each kauhale, so its chats stay together.

### Your first conversation

Open a new chat, attach this guide, and send:

> Read the attached Kauhale Method guide. Then look at my repository `<owner>/<repo>` and propose a kauhale for it: the head of household, the builder hale, any advisor hale, and what each one owns. Ask me questions before building anything.

When the chat asks to add the repository with push access, allow it. Answer its questions, review the proposal, then tell it to build. It follows sections 5 through 8 and the checklist at the end.

### What a kauhale might look like for you

These are starting points; the first chat should propose a household that fits how your work is already organized.

**A book**

| Hale | Kind | Kuleana |
|---|---|---|
| Editor | head of household | Outline, schedule, decisions, the manuscript as a whole |
| Writer (one per part, or one overall) | builder | Drafting and revising chapters in its part |
| Researcher | builder | Sources, facts, and notes that chapters draw on |
| Continuity Keeper | advisor | The story bible: characters, places, timeline, voice. Reviews chapters for contradictions. |
| Copy Editor | advisor | Style sheet and line-level review |
| Publisher | builder | Formatting, front and back matter, exports, submissions |

**A website**

| Hale | Kind | Kuleana |
|---|---|---|
| Webmaster | head of household and builder | The site code, builds, and publishing |
| Content | builder | Pages, posts, and copy |
| Design | builder | Layout, images, and visual style |
| Accessibility or SEO | advisor | Standards and review before changes go live |

For a website, keep the agents' folder out of what gets published (section 7, "Embedded"), and check a preview to confirm it.

### Your own style rules

Section 12.2 has a place for style rules every agent follows. Put your own there: voice, spelling, punctuation habits, words to avoid, how formal to be. The agents apply them to everything they write.

---

## 1. The name

### Kauhale: the project

A **kauhale** was a traditional Hawaiian household compound. Rather than one large building, a family lived in a cluster of separate houses, each with its own purpose: a house for sleeping, houses for eating, a house for work such as beating kapa, a house for canoes. Together they made one home.

A Kauhale project has the same shape. The project is the compound, held in one repository. It is made of separate houses, each devoted to one kind of work, and the household functions because every house does its part and the head of the household coordinates the whole.

The name also carries the method's central claim. A large project cannot live in one building, because one chat can only hold so much. It can live in a compound of small, well-kept houses that remember on its behalf.

### Hale: the agent and its house

A **hale** is a house. In this method each agent has one hale: its folder in the repository, with its state, its directives, its notes, and its daily log. The agent itself is the occupant, and occupants change. When a chat grows long, a new one moves in, reads what the house holds, and carries on. The hale persists; the chat is temporary.

So "hale" names both the role (the Librarian's hale, the CFO's hale) and the place where its memory lives. Opening a new chat in a role means entering that hale.

### Kuleana: what each hale is responsible for

**Kuleana** means responsibility, and it also means right and privilege; historically it named a family's own parcel of land, which they had both the right to use and the duty to tend. The two senses together are the method's ownership rule.

- **The right:** each hale alone writes its own files, plus any shared files assigned to it. No other agent edits them.
- **The duty:** each hale is answerable for its domain. It keeps its state current, finishes its directives, records its decisions, and reports what the head of the household needs to know.

"Stay in your kuleana" is the rule every agent follows. When work belongs to another hale, the agent asks that hale through its outbox instead of doing the work itself.

### The rest of the vocabulary

| Hawaiian | Meaning | In the method |
|---|---|---|
| Kauhale | household compound | the project and its repository |
| Hale | house | one agent: its role and its folder |
| Kuleana | responsibility and right; one's own parcel | the role's domain and the files only it may write |
| Kauoha | command, order | a directive |
| Moʻolelo | story, history | the daily logs and the decision log |
| Hui | gathering | the sync, where the head of the household reviews every hale |

File and folder names stay in plain English (STATE.md, DIRECTIVES.md) so any agent or collaborator can read them anywhere. The Hawaiian names describe the method and how it is taught.

**A note on use.** These words carry cultural meaning. Before presenting or publishing the method, ask a Hawaiian language or cultural advisor to review how they are used here.

## 2. Why this works

A single chat has a limited context window and degrades as it grows. Splitting a project across agents, each holding one slice, keeps every slice sharp. The gain comes from the files: each agent writes its memory to markdown in the repository, so any chat can be replaced by a fresh one that resumes from those files in one read.

Three ideas carry the whole design:

- **The hale remembers; the occupant changes.** Files are the memory and chats are replaceable workers. Anything said in a chat and never written to a file is lost when the chat is rotated.
- **One head of household sees the whole.** The orchestrator reads summaries from every hale, issues kauoha (directives), and keeps the master record.
- **Every hale keeps its own kuleana.** Each file has exactly one owner. Agents write only in their own hale and coordinate through structured files, never by editing each other's work.

## 3. A team of agents, or one Claude Code session?

The alternative is to work the whole project in a single Claude Code session (terminal or VS Code) in the repository. Both work. They suit different projects.

### How a single session handles memory

- One conversation sees everything and can act on everything: read any file, run builds, commit.
- When the context fills, Claude Code compacts it into a summary and continues. The summary is lossy: fine detail from early in the session fades.
- CLAUDE.md loads at every start, so standing rules persist. Anything else persists only if written to a file.
- It can hand a focused job to a subagent, which works in a fresh context and returns a summary. Subagents run and return; they are not conversations you come back to.

### Comparison

| | Team of agent chats | Single Claude Code session |
|---|---|---|
| Setup | Role files, folders, project, one chat per role | A repository and CLAUDE.md |
| Memory over months | Strong: each role has its own STATE and directives, read fresh each session | Weaker: compaction loses detail unless you write state files yourself |
| Depth per domain | Each agent holds one domain sharply | One context juggles every domain |
| Coordination | Manual: you move between chats, say checkpoint and sync | Automatic: one session does it all |
| Speed on a focused task | Slower: switching chats, pulling, pushing | Fast: edit, build, test, commit in one loop |
| Code, builds, refactors across many files | Possible, split by ownership | Best fit |
| Cross-cutting changes | Need a request through OUTBOX or the orchestrator | Done directly |
| Human counterparts | Natural: a person can run a role | Awkward: one session, one driver |
| Works from phone or any device | Yes, app chats run in the cloud | Terminal or VS Code on a machine (or a cloud session) |
| Audit trail | Per-role logs, directives, decision log | Commits, plus whatever notes you ask for |

### Rules of thumb

Use **one Claude Code session** when:
- the project is mostly code or builds (an analysis pipeline, a website feature, a paper's figures);
- it lasts days or a few weeks;
- one person drives it;
- the domains are tightly coupled, so splitting them would mean constant requests between agents.

Use **a team of agents** when:
- the project runs for months (a grant cycle, a conference);
- it spans several distinct domains, each with its own sources and decisions;
- people other than the owner will own parts of it;
- losing a decision made weeks ago would be costly.

### The hybrid

The two combine well. Run one Claude Code session as the orchestrator and define each role as a subagent in `.claude/agents/<role>.md` whose instructions say "read `<orch>/roles/<role>.md` and follow it." The orchestrator dispatches a directive ("Statistician, work STAT-002"); the subagent works in a fresh context, checkpoints to its folder, and returns a summary. You keep the file discipline of the team and lose the window switching.

Use the hybrid for short, well-defined directives. Keep a dedicated chat for long back-and-forth work in one domain, such as drafting the Approach or iterating on power assumptions. Both read and write the same files, so you can mix them freely.

### Borrow the file discipline either way

Even in a single session, three habits from the team model pay off:
- keep a `STATE.md` and say "checkpoint" before the context fills;
- keep a decision log, so compaction never loses a decision;
- use `/clear` and resume from STATE.md when the session gets long, the same way you rotate a chat.

## 4. Vocabulary

| Term | Meaning |
|---|---|
| Kauhale | The project and its repository. |
| Hale | One agent: its role and its folder. |
| Kuleana | A role's domain and the files only it may write. |
| Orchestrator | The head of the household, the coordinating agent (PI for a grant, Chair for a conference). The owner talks to it about direction and priorities. |
| Employee | A specialist agent with one domain (Librarian, CFO, Webmaster, and so on). |
| Directive | The unit of work: a goal with a definition of done. One file per directive. |
| Task | A step inside a directive, numbered under it (SCI-004.2). |
| Checkpoint | The end-of-session routine: log, update directives, rewrite STATE.md, commit, push. |
| Sync | The orchestrator's routine: read every employee's state, update the master file, issue directives. |
| Counterpart | The human behind a role, listed in TEAM.md. |
| Builder hale | A hale that produces the work product: owns code, documents, or data, and changes them. |
| Advisor hale | A consultant hale that owns specifications and reviews. Builders implement against its specs; it signs off before merge. |
| Specification | An advisor's written standard: definitions, models, or acceptance criteria that builders must meet. |
| Review gate | The rule for which reviews a change needs before it merges. Recorded in MASTER.md. |

## 5. Decide the shape first

Answer these before creating anything.

1. **Standalone repo or embedded?**
   - **Standalone** (for example, a grant proposal or a book): the repository exists for the project. Agent folders sit at the root.
   - **Embedded** (for example, a conference website): the project lives inside an existing repository with its own content, such as a website. Put the whole team under one folder (`staff/`) and exclude it from anything that publishes.
2. **What are the roles?** Mirror how the work is already divided. Existing team labels in a timeline or spreadsheet are a good source (a conference timeline with six team labels, such as planning, finances, and sponsors, became six roles). Five or six employees is a workable number.
3. **What is the final product, and in what format?** Decide where finished output lives and who assembles it. Working memory is always markdown; the product may be LaTeX, a website, a spreadsheet, or documents.
4. **Does it need advisors?** If builders implement models, code, or claims that someone else should judge, plan advisor hale and a review gate (section 6).
5. **Who are the humans?** Note which roles have a real person behind them and whether those people will have GitHub access.

## 6. Builder hale and advisor hale

Every kauhale has hale that make things. Larger or more technical ones also need hale that judge things. Name the difference explicitly; it changes how each hale works.

### Builders

- Own a slice of the product: pipeline stages and their code, sections of a document, a website, a budget.
- Change their own files and nothing else.
- Implement against the advisors' specifications and request review when work is ready.

### Advisors (consultants)

- Own **specifications**: the written standards builders implement against. A Physicist owns the physical model and acceptance criteria; a Statistician owns feature definitions and their mathematics; a Programmer owns coding standards and tests.
- Own **reviews**: a written verdict on a builder's change (approve, approve with changes, request changes), stored in the advisor's own `notes/reviews/`.
- Never edit a builder's work. They write specifications, review, and propose.
- Wake only when called. An advisor with no review or specification work sits idle at no cost, so a kauhale can carry several without overloading you.
- May own a small workspace for their own evidence, such as an `experiments/` folder where a Programmer benchmarks alternative implementations. The winning approach goes back to the owning builder to adopt.

### When to add advisors

Add an advisor when a kind of judgment cuts across several builders, or when a wrong decision would be expensive and hard to see. Examples:

| Advisor | Use when |
|---|---|
| Physicist or domain scientist | Builders implement models of the real world, and physical validity must be checked by someone who did not write the code |
| Statistician | Results depend on feature definitions, models, or uncertainty that must be stated precisely and reproducibly |
| Programmer | The product is code that several builders change, and quality, tests, and alternative approaches need one consistent reviewer |
| Bioethics or compliance | Human subjects, data governance, or regulations constrain what builders may do |

A text project (a grant, a conference) usually needs few advisors or none; its builders and the head of household are enough. A code project usually needs at least a Programmer.

### The review gate

Write the gate into MASTER.md as a table: which reviews a change needs, depending on what it touches, plus the owner's final approval. For an imaging analysis pipeline:

| Review | Required when |
|---|---|
| Programmer | every code branch |
| Physicist | the change touches calibration, phantom or pose geometry, or thickness |
| Statistician | the change touches measurements, features, or the final analysis |
| Owner | always; the owner decides on the head of household's recommendation |

The builder requests reviews through its OUTBOX, naming the branch, what changed, and how it was tested. The head of household summarizes the verdicts for the owner with a merge recommendation.

## 7. Repository layout

### Standalone

```
<repo>/
  CLAUDE.md                  agent instructions, loaded automatically
  README.md                  how the system works, for humans
  .gitignore
  <orch>/                    orchestrator folder (pi/, chair/)
    MASTER.md                the master record
    TODO.md or roadmap       the overall timeline
    TEAM.md                  roles mapped to humans
    DIRECTIVES.md            index of all orchestrator directives
    directives/              one file per directive; done/ for finished ones
    roles/                   one role file per agent, plus _employee-base.md
    log/  notes/
  <employee>/                one folder per employee
    STATE.md                 one-page resumable summary
    DIRECTIVES.md            index of this employee's directives
    directives/  directives/done/
    OUTBOX.md                requests to others
    log/  notes/
    tex/ or other            finished deliverable fragments, if the role writes any
```

### Embedded

Same structure under `staff/`, with the orchestrator at `staff/<orch>/`. Then:

- Exclude `staff/` and `CLAUDE.md` from the publishing step (for Jekyll, add both to `exclude:` in `_config.yml`). Verify on a preview that a staff URL returns "not found."
- Leave site files where the site needs them. Assign ownership in MASTER.md instead of moving them; moving page or data folders changes URLs and breaks builds.

## 8. Setup steps

1. **Create the repository** in your GitHub account or organization; private is fine.
2. **Install the Claude GitHub App** with access to the repository (github.com/apps/claude, choose your account, Configure, add the repo). Without it, agent chats cannot push.
3. **Scaffold the folders** from section 7, with empty templates from section 12.
4. **Write the role files**: one per agent, plus `_employee-base.md` with the shared rules. Domain, deliverables, owned files, and who to hand off to.
5. **Write MASTER.md** (section 12.2): goals and key dates, style rules, ownership table, status by role, decision log, pointer to the directives index.
6. **Write CLAUDE.md** (section 12.1) and the README.
7. **Seed the timeline** (TODO.md or roadmap) from whatever exists: an old spreadsheet, issue list, or planning doc.
8. **Seed TEAM.md** with the humans, names and titles only.
9. **Commit and push.** For an embedded repository with a review workflow, do this on a branch, check the preview, then merge.
10. **Create the Claude project** (section 9).
11. **Open the orchestrator chat first** and ask for a sync. It turns the timeline into the first directives.
12. **Open employee chats as they get directives.** An employee with nothing assigned has nothing to do.

## 9. Claude project and tools

**Project instructions:** paste the same text as CLAUDE.md, so app chats and VS Code follow one source. Point to the repository by name.

**Project settings:**
- Keep project memory separate. Agents share only through the repository.
- Upload no files to the project. The repository is the only copy; uploaded copies go stale.
- Archive old chats from before the setup once anything useful in them is captured in the repository.

**Connectors:** GitHub is required. Add what the roles need: Google Drive for documents, Gmail for drafts, Jotform for forms, Google Calendar for dates.

**First prompt in each chat:** when the chat asks to add the repository with push access, choose Allow.

**Opening line for every chat:**

> You are the <Role> for <PROJECT>. Read `<orch>/roles/<role>.md` and follow it.

Name chats by project, role, and generation: "Novel Editor", later "Novel Editor 2".

**VS Code:** open the repository root (agents read across folders). CLAUDE.md loads automatically. Start each session with the same role line and `git pull`.

**App chat or VS Code?** App chats run in the cloud and reach GitHub from any device. Use VS Code when a role needs something only on your computer: a local database, gitignored PDFs, or a local build.

**Where each hale runs.** It is the same model in both places; what differs is what it can reach. A hale that must run code against local data (a database, images, a network drive) needs Claude Code in VS Code or a terminal on the machine with that data, so it can run, read the result, and fix in a loop. Hale that write, specify, review, or coordinate work well in app chats. In an analysis pipeline, builders that touch code run on the machine with the data; the Physicist, Statistician, Reporter, Programmer reviews, and the head of household run anywhere.

**One rule across both:** never run the same role in two places at once.

## 10. Using other models

Nothing in the method is specific to Claude. It needs three things: a model that follows written instructions reliably, the ability to read and write files, and a way to sync them (git, or a shared folder).

- **Instruction file names differ by tool.** Claude Code reads `CLAUDE.md`. Several other agent tools read `AGENTS.md` by convention, and some use their own filename. Keep the rules in one file and have the others point to it, so every tool reads the same household rules.
- **Repository access differs.** How a chat attaches, clones, and pushes depends on the product. The role files, templates, and routines carry over unchanged; only the "get the repository" step changes.
- **Models can be mixed across hale.** The repository is the only interface between agents, so one hale can run on one model and another on a different one. Keep the one-session-per-hale rule.
- **Discipline matters more with weaker models.** A model that follows instructions loosely will skip checkpoints or write outside its kuleana. Enforce ownership in GitHub (see section 14) rather than relying on instructions alone.

## 11. Operating rhythm

**Each working session, per employee:** the agent pulls, reads its state and directives, reports in three lines, works, then checkpoints.

**Checkpoint** (say "checkpoint"):
1. Append the session to today's log.
2. Update the directive files worked on; move finished ones to `done/`; update the index.
3. Rewrite STATE.md, with anything the orchestrator must know at the top.
4. Commit `[PREFIX] PREFIX-NNN checkpoint`, then `git pull --rebase`, then `git push`.

**Sync** (say "sync" in the orchestrator chat):
1. Update the timeline: check off finished items, refresh what is overdue and coming up.
2. Refresh status by role in MASTER.md; close finished directives.
3. Issue new directives for items coming due.
4. Route requests; review self-proposed directives.
5. Flag anything waiting on a person for more than 7 days.
6. Log decisions.

**Where to talk:** decide in the orchestrator chat; do deep work in employee chats. Long technical work in the orchestrator chat fills its context with detail, which is the overload this design avoids.

## 12. Templates

### 12.1 CLAUDE.md

```
# <PROJECT> Agent Instructions

<One sentence on the project.> The GitHub repository
<owner>/<repo> (branch main) is the single source of truth.

## Roles
Each chat plays exactly one role, named in its first message. If no
role is named, ask which one before doing anything.

| Role | Writes in | Role file |
|---|---|---|
| <Orch> | <orch>/ | <orch>/roles/<orch>.md |
| <Role> | <role>/ | <orch>/roles/<role>.md |

Employees also follow <orch>/roles/_employee-base.md. Ownership,
dates, and style rules are in <orch>/MASTER.md.

## Start of every session
1. App chat: attach and clone <owner>/<repo>. VS Code: git pull.
2. Read your role file and follow it.

## Rules
- Write only in your own folder and the files assigned to you.
- Commit at each checkpoint, then git pull --rebase and git push.
- Never force-push or rewrite history on main.
- Never send email to a list or a person without the owner's approval of
  the final text.
- No personal data, payment details, PHI, or secrets in git.
- <the owner's style rules>
```

### 12.2 MASTER.md sections

1. **Goals and key dates**
2. **Style rules for all agents**: the owner's voice, spelling, punctuation, and words to avoid
3. **Ownership**: each role, its folder, and any shared files it owns
   - **Review gate** (when the kauhale has advisors): which reviews each kind of change needs before it merges
4. **Status by role**: three to five lines each, with active directive IDs
5. **Decision log**: dated, one line each, with the source directive
6. **Pointer to the directives index**

### 12.3 Role file

```
# Role: <Role>

- Folder: <folder>/
- Prefix: <PREFIX>
- Reports to: <Orch>

Before anything else, read <orch>/roles/_employee-base.md and follow it.

## Domain
- What this role is responsible for

## Files you own outside your folder
- Shared files this role edits, if any

## Deliverables kept in your folder
- notes/<topic>.md, tex/<section>.tex, and so on

## Working with others
- Who supplies what to whom

## Notes
- Hard rules specific to this role
```

### 12.4 Hale base rules (headings to include)

- **Access:** write only in your folder and assigned files; read anything permitted.
- **Markdown and deliverables:** markdown for thinking and communicating; deliverable formats only for finished output.
- **Your folder:** STATE.md, DIRECTIVES.md, directives/, OUTBOX.md, log/, notes/.
- **Directives:** one file each, index first, open only active ones, move finished to done/.
- **Working with people:** `[human: Name]` tasks, drafts for the owner to send, a "Waiting on people" list.
- **Daily log:** append-only, one file per day.
- **Start of session** and **Checkpoint** routines from section 11.
- **Requests to others** through OUTBOX.md; answers go in your own notes/.
- **Reviews:** how to request one, and (for advisors) how to give one.
- **Standing rules:** no sending, no signing, no personal data in git; name the owning role when asked about another domain.

### 12.5 STATE.md

```
# <Role> State

Last checkpoint: YYYY-MM-DD

## For the <Orch>
## Waiting on people
## Status
## Decisions and reasons
## Open questions
## Next steps
## File index
```

### 12.6 Directive file: `directives/<PREFIX>-NNN-short-title.md`

```
# <PREFIX>-NNN  Title

Source: <ORCH>-NNN | colleague request (role, date) | self (proposed)
Goal:
Definition of done:
Due: YYYY-MM-DD
Human: (name from TEAM.md, or none)
Status: active | blocked | waiting on person | done
Opened: YYYY-MM-DD

## Tasks
- [ ] <PREFIX>-NNN.1  task
- [ ] <PREFIX>-NNN.2  [human: Name] task only a person can do
- [x] <PREFIX>-NNN.3  task  (done YYYY-MM-DD: outcome)
- [-] <PREFIX>-NNN.4  task  (dropped: reason)

## Notes
## Outcome
```

Orchestrator directives add `Assigned to:` and `Adopted as:` lines. The employee adopts each one under its own ID, citing the orchestrator's ID in `Source:`.

### 12.7 DIRECTIVES.md index

```
## Active
| ID | Title | Source | Due | Status | File |

## Done
| ID | Title | Closed | Outcome | File |
```

### 12.8 OUTBOX entry

```
### YYYY-MM-DD  To: <role>  Re: <PREFIX>-NNN.M
Request:
Definition of done:
Needed by: YYYY-MM-DD
Status: open
```

### 12.9 Log entry: `log/YYYY-MM-DD.md`

```
## HH:MM  <PREFIX>-NNN.M  short title
Did:
Found:
Decided (and why):
Open:
```

### 12.10 Advisor role file (additions)

```
- Kind: advisor

## Kuleana
- The standard you set (the model, the definitions, the criteria)

## Files you own
- staff/<advisor>/specs/: one specification file per topic

## How you work
- You write no production code or text in builders' files.
- Sign-off: name the kinds of change that need your review.
- Reviews go in notes/reviews/<branch-or-item>.md with a verdict.
```

### 12.11 Review note: `notes/reviews/<branch>.md`

```
# Review: <branch>  (<PREFIX>-NNN)

Reviewer: <hale>
Date: YYYY-MM-DD
Requested by: <hale>, <directive ID>
Verdict: approve | approve with changes | request changes

## What was reviewed
## Findings
## Required changes
## Suggestions
```

### 12.12 TEAM.md

```
| Role | Human counterpart | Their part | Agent's part | Connects |
```

"Connects" is **Direct** (has GitHub access and may run the role in their own session) or **Through the owner** (the agent drafts; the owner sends and pastes replies back). Names and titles only.

## 13. Git conventions

- Commit messages: `[PREFIX] PREFIX-NNN short description`.
- Agent files commit directly to `main`. Each agent writes only its own folder, so parallel pushes rebase cleanly.
- Published files in an embedded repository go through the existing review workflow (branch, preview, approval, merge).
- Never force-push or rewrite `main`. Unverified-commit badges on old commits are cosmetic; leave them.
- `.gitignore` large binaries and sensitive data. For files that must stay local, such as copyrighted PDFs, commit a manifest listing what should be present, named by key.
- Keep `main` free of branch protection rules that would reject agent pushes, unless you add the pull-request setup in section 14.

## 14. Human counterparts and access

- **TEAM.md** names the human behind each role and how they connect.
- **Agents never contact people.** They draft; the owner sends.
- **Tracking:** `[human: Name]` tags on tasks, a `Human:` line on directives, a "Waiting on people" list in STATE.md, and the orchestrator flags anything older than 7 days at sync.
- **Counterparts with GitHub access** need only a Claude account with the GitHub connector and one opening line naming their role and themselves. The repository carries the rules.
- **Limiting a counterpart to their role** takes GitHub, since instructions alone are not enforcement:
  - Any plan: a ruleset on `main` requiring pull requests, with the owner as the only bypass; a role map of GitHub usernames; a GitHub Action that fails a pull request touching folders outside the author's role; CODEOWNERS for the orchestrator folder.
  - Team or Enterprise plan: push rulesets that block changes to protected paths unless the pusher is on the bypass list.

## 15. Long-run maintenance

**Rotate chats** when an agent forgets earlier decisions, repeats itself, or slows down, or on a schedule (weekly, or after each finished directive):
1. Say "checkpoint" and confirm the commit reached GitHub.
2. Archive the old chat.
3. Open "<Project> <Role> N+1" with the same role line.

**Keep the read-on-start files small:**
- STATE.md stays about one page.
- Finished directives live in `done/` and are read only for history.
- Logs grow freely; agents read them only when needed.
- Monthly, the orchestrator moves decision-log entries older than 30 days to `notes/decisions-archive.md` and collapses finished timeline sections.

**The rule that matters most:** never end a session without a checkpoint.

## 16. Lessons learned

- **Read before restructuring.** Look at the existing repositories, timelines, and agents before designing roles. One conference repository already had team labels and a planner agent whose duties split cleanly into the new roles.
- **Deliverables as fragments.** When the product must be assembled (LaTeX attachments, a website, a book's chapters), each role writes plain fragments in its own folder and one role owns the build that pulls them in. Ownership stays clean and the build stays in one place.
- **Specialists appear as you go.** A grant team added a Statistician once power calculations and demographics outgrew the Physicist. Adding a role means a role file, a folder, a row in the ownership and access tables, and a decision-log entry.
- **Standing rules go in role files; work goes in directives.** A format for paper notes is a rule. Reading ten papers is a directive.
- **Local-only resources need a plan.** A local database or gitignored PDFs are reachable only from VS Code on the machine that has them. Say so in the role file.
- **Verify exclusions on a preview** before trusting that private planning files stay unpublished.
- **Separate making from judging.** In an imaging pipeline, builders own stages and advisors (Physicist, Statistician, Programmer) own specifications and reviews. The builder that wrote a calibration change is the wrong one to judge its physics.
- **Code projects map hale to the pipeline.** When a codebase already has stages, give each builder a contiguous run of stages and every file exactly one owner. Check ownership with a script: every file should have one owner and none should have two.
- **Respect existing conventions.** One codebase already had a stage-grouped TODO.md with stable IDs and `Refs TODO:` commits. The kauhale kept them: directives cite TODO IDs, and each hale closes items in its own stages.
- **Agents report state; the orchestrator owns the timeline.** Employees never edit the master timeline. They report finished items, and the orchestrator checks them off.

## 17. New project checklist

- [ ] Shape decided: standalone or embedded, roles, product format, humans
- [ ] Repository created; Claude GitHub App has access
- [ ] Folders and templates scaffolded
- [ ] Builder and advisor hale chosen; review gate written into MASTER.md (if any advisors)
- [ ] Role files and the shared base rules written
- [ ] Every owned file has exactly one owner (scripted check for code projects)
- [ ] MASTER.md, timeline, TEAM.md, CLAUDE.md, README written
- [ ] Publishing exclusions set and verified (embedded only)
- [ ] Committed and pushed (or merged after review)
- [ ] Claude project created with instructions, memory separate, no uploads
- [ ] Connectors on; old chats archived
- [ ] Orchestrator chat opened; first sync run
- [ ] First employee chats opened with role lines
- [ ] First checkpoint confirmed on GitHub

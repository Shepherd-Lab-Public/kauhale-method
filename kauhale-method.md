# The Kauhale Method

A way to run a large, long project as a household of AI agents. Each agent keeps its own house, works its own responsibility, and writes everything that matters to shared files, so no chat ever has to remember the whole project. It was developed on a grant proposal, a scientific conference, and a medical imaging analysis pipeline, and it suits any long project with several distinct kinds of work: books, websites, research, events.

The Kauhale Method was created by John Shepherd, inspired by conversations with Sven Prevrhal at MICCAI 2026.

Copyright © 2026 John A. Shepherd. All rights reserved.

Throughout this guide, **the owner** means you: the person the agents work for, who makes the final decisions.

### The words in this guide

The Kauhale Method is a modern way of organizing AI-assisted work, developed in Hawaiʻi. It makes no claim to be a traditional Hawaiian practice or to carry Hawaiian knowledge. It uses Hawaiian words where they fit, as a mark of respect for the Hawaiian people, their language, and the place where the method took shape. Each word is explained more fully in Part B, section 1.

| Word | Say it | Meaning | In the method |
|---|---|---|---|
| **Kauhale** | kow-HAH-leh | a household compound made of several separate houses | the whole project, held in one GitHub repository |
| **Hale** | HAH-leh | a house | one AI agent and its folder of notes; one hale per kind of work |
| **Haku** | HAH-koo | head or master; also to arrange or braid, as in braiding a lei | the head of the kauhale: the hale that coordinates all the others |
| **Kuleana** | koo-leh-AH-nah | responsibility, and the right that comes with it | what each hale is responsible for, and the files only it may change |
| **Kauoha** | kow-OH-hah | an order or instruction | a directive: one piece of assigned work |
| **Moʻolelo** | MOH-oh-LEH-loh | story, history | the logs and the record of decisions |
| **Hui** | HOO-ee | a gathering | the sync, when the Haku reviews every hale |

Plain English words used throughout:

- **Repository** (or repo): an online folder on GitHub that keeps every version of every file.
- **Directive:** a piece of work with a goal and a clear definition of done.
- **Checkpoint:** the end-of-session routine where an agent writes down everything it did and decided.
- **Builder** and **advisor:** hale that make things, and hale that review and set standards.

---

## How to use this file

**If you are a person:** upload this file to a new Claude chat and say "Help me set up a kauhale for my project" (or "Help me try a kauhale on my project"). Claude will walk you through everything, one step at a time, including GitHub if you have never used it.

**If you are Claude:** someone has given you this guide. Unless they ask for something else, run the Guided Setup in Part A with them. Part B is the reference behind each step; consult it as you go.

---

# Part A. Guided Setup (instructions for Claude)

## A.1 How to guide

- **One question at a time.** Wait for the answer before moving on. Offer choices where you can.
- **Assume no technical background.** Explain each term the first time it appears, in one plain sentence. A repository is "an online folder for your project that keeps every version of every file." A commit is "a saved snapshot of changes." Pushing is "sending saved changes up to GitHub."
- **Confirm every step.** After each action the person takes, ask them to confirm it worked, or check it yourself if you have the tools. Never move on from a step that failed.
- **Do it for them when you can.** If you have tools that can create files, commit, or push, offer to do the step yourself. Otherwise give exact click-by-click instructions.
- **Protect them.** Never ask for passwords, tokens, or payment details. Never push, delete, or publish without their explicit go-ahead. Keep personal, financial, or health data out of the repository.
- **Keep a running summary.** After each stage, say in two lines what is done and what comes next. If the session ends partway, the summary tells the person where to resume.
- **Interface details change.** Button names and menus may differ from this guide. Describe the goal ("connect GitHub to Claude") alongside the steps, and adapt to what the person sees.

## A.2 The decision tree

Work through the nodes in order. Each node says what to ask, what each answer leads to, and when the node is done.

### Node 1. Welcome and the project

Explain the kauhale idea in three sentences: the project lives in an online folder; each AI helper (a hale) keeps its own notes there and works on one part; nothing is lost when a chat gets long, because the notes carry the memory.

Ask:
1. "What is the project?" (a book, a website, research or code, an event, a grant, something else)
2. "Where does the work live today?" (nowhere yet, files on your computer, Google Docs or Word, a website service, already on GitHub)
3. "Roughly how long will it run, and will anyone else work on it with you?"

Record the answers; they drive Nodes 3, 5, 6, 7, and 8.

### Node 2. A GitHub account

Ask: "Do you have a GitHub account?"

- **No:** walk them through signing up at github.com: choose a username, use an email they check, verify the email, and pick the free plan. Explain that private repositories are free and visible only to them.
- **Yes:** ask for the username.

Done when they can sign in to GitHub and tell you their username.

### Node 3. The repository

Ask: "Does this project already have a GitHub repository?"

- **Yes:** ask for its name (`owner/repository`) and whether it already holds work, conventions, or other people's contributions. Go to Node 4; Node 5 takes inventory.
- **No:** create one together. At github.com, the "+" menu, then "New repository": a short name with no spaces (for example `my-novel`), **Private**, and tick "Add a README file." Then "Create repository."

Then bring in existing work, depending on the Node 1 answer:

- **Nothing yet:** nothing to do.
- **Files on their computer** (documents, images, code): in the repository, "Add file," then "Upload files," and drag the files in. The web upload takes up to 100 files at a time and files up to 25 MB each. Leave out anything private or sensitive. Mention that books and documents work best as plain text or Markdown, and that once you are connected (Node 4) you can convert Word or Google Docs files for them.
- **Google Docs or Word:** easiest path is to download them (as .docx, or plain text) and upload as above, or wait until Node 4 and attach them in chat for you to convert and commit.
- **A website:** ask how the site is published.
  - From a GitHub repository (GitHub Pages, Netlify, Cloudflare Pages, Vercel): use that repository. Note it for Node 7 (the agents' folder must stay unpublished).
  - From a website builder with no repository (Squarespace, Wix, WordPress.com): the kauhale can still plan and draft content in a new repository, but changes to the live site stay manual. Say so plainly and continue.

Done when the repository exists and holds what it should.

### Node 4. Connect Claude to GitHub

Two connections are needed:

1. **The Claude GitHub App** gives Claude permission to work in the repository. At github.com/apps/claude, choose "Install" (or "Configure" if it is already installed), choose their account, and select this repository (or all repositories).
2. **The GitHub connector in Claude:** in Claude's Settings, under Connectors, connect GitHub and sign in.

Then test it: try to attach or clone the repository yourself. When Claude asks for permission to add the repository with push access, the person allows it.

- **It works:** go to Node 5 if the repository already holds work, otherwise Node 6.
- **Access refused:** recheck that the App includes this repository, then reconnect GitHub under Connectors.

Done when you can read the repository and the person has allowed push access.

### Node 5. Take inventory (existing repositories only)

Skip this node for a new or empty repository.

Follow the adoption checklist in Part B section 9. Read the repository, then present the inventory to the person in plain language before proposing anything:

- what is there: the main folders, to-do lists, notes, docs, and how the work is built or published;
- who has been working in it, and which branches are active;
- any existing AI setup (`CLAUDE.md`, `AGENTS.md`, `AGENT.md`, `.claude/agents/`) and what it does;
- the rules already in force: review requirements, branch rules, commit message conventions.

Ask:
1. "Do you want to commit to the method, or try it first?" If they want to try it, the trial rules in Part B section 10 apply from here on: additive only, a seed, a tagged start, and a review date.
2. "Which of these ways of working do you want to keep?" Default to keeping them.
3. "Should the existing AI setup be kept, split across the new hale, or retired?" (For a trial, keep it as is.)
4. "Is there planning or related material in another repository that should move here?" (For a trial, leave it where it is.)

Explain that nothing will be moved or renamed: the hale go in a `staff/` folder, and ownership of existing files is recorded in a table.

Done when the person has seen the inventory and answered these questions.

### Node 6. Seed or household?

Decide together, using Node 1 and Part B section 6:

- **Trial** (a removable seed): for an existing repository whose owner wants to try the method first (Part B section 10). Only `staff/` and `CLAUDE.md` are added; nothing existing is changed, retired, or moved.
- **Seed** (one hale): one kind of work, one person, and the project fits comfortably in a chat or two. Most new projects start here.
- **Household** (several hale): several distinct kinds of work, other people involved, or a long horizon of months.

For a household, look at what is already in the repository, then propose hale that fit how the work is organized, including any advisors (Part B section 7). Use Part B section 0 for book and website examples. Ask the person to confirm or adjust the list.

Done when the shape is agreed: trial, seed, or a named list of hale with what each owns.

### Node 7. Where the hale will work

Ask: "Does any part of this project need programs to run on your own computer, or files that live only there?"

- **No** (writing, planning, most websites): every hale works in Claude chats. Go on.
- **Yes** (code that runs on local data, large files that stay off GitHub): those hale should run in Claude Code inside VS Code on that computer. Give a short pointer to installing VS Code and Claude Code, and note it in the setup; it can be done later.

For a website published from the repository, confirm what the build includes and plan to exclude `staff/` and `CLAUDE.md` (Part B section 8, "Embedded").

### Node 8. People

If others are involved, ask who, what part each person plays, and whether each will have their own GitHub access. This becomes TEAM.md. Names and roles only; no phone numbers or personal emails in the repository. If there are none, skip TEAM.md.

### Node 9. Style and rules

Ask how the agents should write: voice, spelling (US or UK), punctuation habits, words or constructions to avoid, formality. Ask for any hard rules ("never email anyone," "never change the published site without asking"). These go into MASTER.md.

### Node 10. Build it

Summarize the plan in a few lines and ask for the go-ahead. For an existing repository, do all of this on a new branch, follow the remaining steps of the adoption checklist (Part B section 9), and merge only after the person approves. Then:

- **Trial:** tag the current commit (`kauhale-trial-start`) and push the tag, create the seed files, write the review date into MASTER.md, and change nothing else in the repository.
- **Seed:** create the files in Part B section 6 ("Seed layout").
- **Household:** create the files in Part B sections 8 and 15 (layout and templates): CLAUDE.md, the Haku's folder with MASTER.md, DIRECTIVES.md, roles, and TEAM.md if needed, plus one folder per hale.

Fill MASTER.md with the goals, dates, and style rules gathered so far. Commit and push. If you cannot push, give the person the files and walk them through "Add file," then "Upload files."

For a website, check a preview or the live site after the next deploy and confirm that a `staff/` page returns "not found."

Done when the files are on GitHub and the person can see them.

### Node 11. The Claude project

Walk them through creating a Claude project for this kauhale:

- Name it after the project.
- Paste the contents of CLAUDE.md into the project instructions.
- Keep project memory separate from their other projects, if the setting is available, so the hale share only through the repository.
- Upload no project files; the repository is the only copy.

### Node 12. First session

Have them open a new chat in the project and send the opening line for the Haku, for example:

> You are the Editor. Read `staff/lead/roles/lead.md` and follow it.

(For a seed: "You are the Lead. Read `staff/lead/MASTER.md` and `staff/lead/STATE.md`, then follow CLAUDE.md.")

When it asks to add the repository with push access, allow it. Ask the new chat to make a small first entry and say "checkpoint." The person confirms the commit appears on GitHub. That proves the whole loop works.

### Node 13. The three habits

Teach these before finishing:

1. **Checkpoint** at the end of every session. Anything not written to a file is forgotten.
2. **Sync** (households): the Haku reviews every hale and assigns work.
3. **Rotate** a chat when it grows long or starts forgetting: checkpoint, archive it, open a fresh one with the same opening line.

Close with a short summary of what was built, where it lives, and the opening line for each hale. For a trial, also restate the review date and the three choices at that date: keep, grow, or remove.

---

# Part B. The Method (reference)


## 0. Examples to start from

### What a kauhale might look like for you

These are starting points; the first chat should propose a household that fits how your work is already organized.

**A book**

| Hale | Kind | Kuleana |
|---|---|---|
| Editor | Haku | Outline, schedule, decisions, the manuscript as a whole |
| Writer (one per part, or one overall) | builder | Drafting and revising chapters in its part |
| Researcher | builder | Sources, facts, and notes that chapters draw on |
| Continuity Keeper | advisor | The story bible: characters, places, timeline, voice. Reviews chapters for contradictions. |
| Copy Editor | advisor | Style sheet and line-level review |
| Publisher | builder | Formatting, front and back matter, exports, submissions |

**A website**

| Hale | Kind | Kuleana |
|---|---|---|
| Webmaster | Haku and builder | The site code, builds, and publishing |
| Content | builder | Pages, posts, and copy |
| Design | builder | Layout, images, and visual style |
| Accessibility or SEO | advisor | Standards and review before changes go live |

For a website, keep the agents' folder out of what gets published (section 8, "Embedded"), and check a preview to confirm it.

### Your own style rules

Section 12.2 has a place for style rules every agent follows. Put your own there: voice, spelling, punctuation habits, words to avoid, how formal to be. The agents apply them to everything they write.

---

## 1. The name

### Kauhale: the project

A **kauhale** was a traditional Hawaiian household compound. Rather than one large building, a family lived in a cluster of separate houses, each with its own purpose: a house for sleeping, houses for eating, a house for work such as beating kapa, a house for canoes. Together they made one home.

A Kauhale project has the same shape. The project is the compound, held in one repository. It is made of separate houses, each devoted to one kind of work, and the household functions because every house does its part and the head of the kauhale, the Haku, coordinates the whole.

The name also carries the method's central claim. A large project cannot live in one building, because one chat can only hold so much. It can live in a compound of small, well-kept houses that remember on its behalf.

### Hale: the agent and its house

A **hale** is a house. In this method each agent has one hale: its folder in the repository, with its state, its directives, its notes, and its daily log. The agent itself is the occupant, and occupants change. When a chat grows long, a new one moves in, reads what the house holds, and carries on. The hale persists; the chat is temporary.

So "hale" names both the role (the Librarian's hale, the CFO's hale) and the place where its memory lives. Opening a new chat in a role means entering that hale.

### Haku: the head of the kauhale

**Haku** means head, master, or overseer: the one a household answers to. It also means to arrange or compose. *Haku mele* is composing a song; *haku lei* is braiding a lei. That second sense describes the job. The Haku does not do every hale's work; it braids their work into one thing.

The Haku is the head of the kauhale. It keeps its own hale like every other agent, and it also coordinates the whole compound: it reads every hale's state, issues kauoha (directives), keeps the master record, and brings decisions to the owner. Every kauhale has exactly one Haku, from a one-hale seed to a full household.

A project may also give its Haku a familiar title: Haku (PI) for a grant, Haku (Chair) for a conference, Haku (Editor) for a book, Haku (Lead) for a codebase. One opening line then works for every project: "You are the Haku."

### Kuleana: what each hale is responsible for

**Kuleana** means responsibility, and it also means right and privilege; historically it named a family's own parcel of land, which they had both the right to use and the duty to tend. The two senses together are the method's ownership rule.

- **The right:** each hale alone writes its own files, plus any shared files assigned to it. No other agent edits them.
- **The duty:** each hale is answerable for its domain. It keeps its state current, finishes its directives, records its decisions, and reports what the Haku needs to know.

"Stay in your kuleana" is the rule every agent follows. When work belongs to another hale, the agent asks that hale through its outbox instead of doing the work itself.

### The rest of the vocabulary

| Hawaiian | Meaning | In the method |
|---|---|---|
| Kauhale | household compound | the project and its repository |
| Hale | house | one agent: its role and its folder |
| Haku | head; to arrange or braid | the head of the kauhale, which coordinates every hale |
| Kuleana | responsibility and right; one's own parcel | the role's domain and the files only it may write |
| Kauoha | command, order | a directive |
| Moʻolelo | story, history | the daily logs and the decision log |
| Hui | gathering | the sync, where the Haku reviews every hale |

File and folder names stay in plain English (STATE.md, DIRECTIVES.md) so any agent or collaborator can read them anywhere. The Hawaiian names describe the method and how it is taught.

### A method from Hawaiʻi

The Kauhale Method was developed in Hawaiʻi, and its language reflects that. It is a project-management method for AI agents, created in 2026. The traditional kauhale, the role of a haku, and the meaning of kuleana belong to Hawaiian culture and history, which are far richer than anything described here. The method borrows these words as metaphors because they capture its ideas well, and uses them to honor the Hawaiian people and the Hawaiian language, ʻōlelo Hawaiʻi.

When you teach or present the method, describe it the same way: a method made in Hawaiʻi that uses Hawaiian words with respect.

**A note on use.** These words (kauhale, hale, haku, kuleana, kauoha, moʻolelo, hui) carry cultural meaning. Spell them with their ʻokina and kahakō where they apply, use them in their meanings above, and avoid stretching them to cover things they do not mean. Before presenting or publishing the method, ask a Hawaiian language or cultural advisor to review how they are used here.

## 2. Why this works

A single chat has a limited context window and degrades as it grows. Splitting a project across agents, each holding one slice, keeps every slice sharp. The gain comes from the files: each agent writes its memory to markdown in the repository, so any chat can be replaced by a fresh one that resumes from those files in one read.

Three ideas carry the whole design:

- **The hale remembers; the occupant changes.** Files are the memory and chats are replaceable workers. Anything said in a chat and never written to a file is lost when the chat is rotated.
- **One Haku sees the whole.** The Haku reads summaries from every hale, issues kauoha (directives), and keeps the master record.
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
| Cross-cutting changes | Need a request through OUTBOX or the Haku | Done directly |
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

The two combine well. Run one Claude Code session as the Haku and define each role as a subagent in `.claude/agents/<role>.md` whose instructions say "read `lead/roles/<role>.md` and follow it." The Haku dispatches a directive ("Statistician, work STAT-002"); the subagent works in a fresh context, checkpoints to its folder, and returns a summary. You keep the file discipline of the team and lose the window switching.

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
| Haku | The head of the kauhale, the coordinating hale (titled PI for a grant, Chair for a conference, Editor for a book). The owner talks to it about direction and priorities. |
| Employee | A specialist agent with one domain (Librarian, CFO, Webmaster, and so on). |
| Directive | The unit of work: a goal with a definition of done. One file per directive. |
| Task | A step inside a directive, numbered under it (SCI-004.2). |
| Checkpoint | The end-of-session routine: log, update directives, rewrite STATE.md, commit, push. |
| Sync | The Haku's routine: read every employee's state, update the master file, issue directives. |
| Counterpart | The human behind a role, listed in TEAM.md. |
| Builder hale | A hale that produces the work product: owns code, documents, or data, and changes them. |
| Advisor hale | A consultant hale that owns specifications and reviews. Builders implement against its specs; it signs off before merge. |
| Specification | An advisor's written standard: definitions, models, or acceptance criteria that builders must meet. |
| Review gate | The rule for which reviews a change needs before it merges. Recorded in MASTER.md. |

## 5. Decide the shape first

Answer these before creating anything.

1. **Standalone repo or embedded?**
   - **Standalone** (for example, a grant proposal or a book): the repository exists for the project. Agent folders sit at the root.
   - **Embedded** (for example, a conference website): the project lives inside an existing repository (see section 9 for adopting one) with its own content, such as a website. Put the whole team under one folder (`staff/`) and exclude it from anything that publishes.
2. **What are the roles?** Mirror how the work is already divided. Existing team labels in a timeline or spreadsheet are a good source (a conference timeline with six team labels, such as planning, finances, and sponsors, became six roles). Five or six employees is a workable number. A project with one kind of work can start as a seed kauhale (section 6) and grow.
3. **What is the final product, and in what format?** Decide where finished output lives and who assembles it. Working memory is always markdown; the product may be LaTeX, a website, a spreadsheet, or documents.
4. **Does it need advisors?** If builders implement models, code, or claims that someone else should judge, plan advisor hale and a review gate (section 7).
5. **Who are the humans?** Note which roles have a real person behind them and whether those people will have GitHub access.

## 6. Start small: the seed kauhale

Every project can start as a kauhale, even one with a single hale. A one-hale project still benefits from the file discipline (a state file, a decision log, checkpoints), and setting it up as a kauhale from day one means it can grow into a full household without renaming or moving anything.

The seed keeps only what one hale uses. Coordination files (OUTBOX, TEAM, review gates, directive indexes) wait until there is someone to coordinate with; an agent will otherwise dutifully maintain empty files.

### Seed layout

```
CLAUDE.md                 rules, plus "one hale for now: the Lead, in staff/lead/"
staff/lead/
  MASTER.md               facts and goals, style rules, decision log
  STATE.md                one-page resumable state
  TODO.md                 the work list (directives come later)
  log/                    daily log, append-only
  notes/                  findings, drafts, research
```

For a website, add `staff/` and `CLAUDE.md` to whatever the build excludes, exactly as for a full kauhale.

The single hale is the Haku from the start, titled Lead, Editor, Chair, or PI as fits the project. It heads a kauhale of one, so when others arrive it already has the right name, folder, and files.

### Seed routine

- **Start of session:** pull, read MASTER.md and STATE.md, report in three lines.
- **Checkpoint:** append to the log, update TODO.md, rewrite STATE.md, log decisions in MASTER.md, commit and push.
- **Rotate** the chat when it grows long; the new one resumes from STATE.md.

### When to add the second hale

Add one when any of these happens:

- one chat can no longer hold the project, even with regular rotation;
- a distinct kind of work appears that has its own sources and decisions (references, a budget, code review, continuity checking for a book);
- a second person joins.

### Growing from seed to household

1. The Lead gets a role file: `staff/lead/roles/lead.md`.
2. Add the shared base rules: `staff/lead/roles/_hale-base.md`.
3. Add an ownership table (and a review gate, if the new hale is an advisor) to MASTER.md.
4. Convert TODO.md items that belong to the new hale into directives: add `staff/lead/DIRECTIVES.md` and `staff/lead/directives/`.
5. Create the new hale's folder (STATE, DIRECTIVES index, directives/, OUTBOX, log, notes) and its role file.
6. If a person comes with it, add `staff/lead/TEAM.md`.
7. Update CLAUDE.md's hale table and log the change in the decision log.

Everything the Lead already wrote stays where it is.

## 7. Builder hale and advisor hale

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

A text project (a grant, a conference) usually needs few advisors or none; its builders and the Haku are enough. A code project usually needs at least a Programmer.

### The review gate

Write the gate into MASTER.md as a table: which reviews a change needs, depending on what it touches, plus the owner's final approval. For an imaging analysis pipeline:

| Review | Required when |
|---|---|
| Programmer | every code branch |
| Physicist | the change touches calibration, phantom or pose geometry, or thickness |
| Statistician | the change touches measurements, features, or the final analysis |
| Owner | always; the owner decides on the Haku's recommendation |

The builder requests reviews through its OUTBOX, naming the branch, what changed, and how it was tested. The Haku summarizes the verdicts for the owner with a merge recommendation.

## 8. Repository layout

### Standalone

```
<repo>/
  CLAUDE.md                  agent instructions, loaded automatically
  README.md                  how the system works, for humans
  .gitignore
  lead/                      the Haku's folder (older projects use pi/ or chair/)
    MASTER.md                the master record
    TODO.md or roadmap       the overall timeline
    TEAM.md                  roles mapped to humans
    DIRECTIVES.md            index of all the Haku's directives
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

Same structure under `staff/`, with the Haku at `staff/lead/`. Then:

- Exclude `staff/` and `CLAUDE.md` from the publishing step (for Jekyll, add both to `exclude:` in `_config.yml`). Verify on a preview that a staff URL returns "not found."
- Leave site files where the site needs them. Assign ownership in MASTER.md instead of moving them; moving page or data folders changes URLs and breaks builds.

## 9. Adopting an existing repository

Most projects already exist before they become a kauhale. An existing repository carries history, conventions, collaborators, and sometimes an earlier agent setup. Adopting it means fitting the household around what works, without moving or renaming what others depend on.

### The adoption checklist

1. **Take inventory before designing anything.** Read the README and any docs; find every to-do list, notes folder, issue tracker, and planning file; list the branches and who has been committing; note how the work is built or published; and look for an existing agent setup (`CLAUDE.md`, `AGENTS.md`, `AGENT.md`, `.claude/agents/`, custom commands). Present the inventory to the owner before proposing hale.
2. **Decide what happens to any existing agent setup.** Keep it if it still fits, split its duties across the new hale, or retire it. If a `CLAUDE.md` or `AGENTS.md` already exists, merge the kauhale rules into it rather than replacing it, and keep anything the owner still relies on.
3. **Keep the working conventions.** If the repository already has a to-do list with stable IDs, a notes convention, or a commit message format, the kauhale adopts them. Directives cite existing items rather than copying them, and hale close items in their own sections.
4. **Assign ownership without moving files.** Website pages, data files, and code stay where the build and imports expect them. Record ownership in MASTER.md as a table. For code projects, check it with a script: every file has exactly one owner.
5. **Reconcile with existing rules.** If the repository forbids direct commits to `main` or requires reviews, keep that for the product and add a narrow, written exception for `staff/` (which never publishes or runs). Record the exception wherever the existing rules live.
6. **Fold in related repositories.** If planning lives in a separate repository, move what is still current into the Haku's folder, note where it came from, and archive the old repository once the move is confirmed.
7. **Assign existing branches.** Give each active branch an owning hale. Flag dead branches as "do not build on" rather than deleting them.
8. **Map the people already working.** People who already commit become counterparts for the hale that cover their work. Record them in TEAM.md and confirm their GitHub access.
9. **Make the adoption itself a reviewed change.** Do it on a branch. For a website, check a preview: the site still builds and a `staff/` page returns "not found." The owner approves, then merge.

### Worked examples

- **A conference website** (embedded): the repository was a live Jekyll site with its own agent manual, a planner agent, and a branch-and-preview rule. The team went under `staff/`, excluded from the build. The planner's duties were split between a ScienceAdmin and a Webmaster and the planner retired. Direct commits to `main` were allowed for `staff/` only. A separate planning repository's timeline moved into the Chair's folder, and the old repository was archived.
- **An imaging analysis pipeline** (code): the repository had an 11-stage pipeline, a stage-grouped TODO.md with stable IDs and `Refs TODO:` commits, a lab notebook, and several experiment branches. Builder hale were drawn along pipeline stages, every code file got one owner (checked by script), the existing TODO.md stayed the master list, experiment branches were assigned to their hale, and two active collaborators became counterparts.

## 10. Trying the method without committing

A person with an existing repository may want to try a kauhale before buying in. That works well if the trial is built to be removed cleanly.

### Remove the household, keep the work

Ending a trial means deleting the kauhale's files in one new commit. Resetting the repository to the commit before the trial would also erase the real work done during it (chapters, fixes, pages), would discard anyone else's commits from that period, and would need a force-push. The household comes out; the work stays.

### Trial rules

1. **Additive only.** The trial adds `staff/` and `CLAUDE.md` (or a clearly marked section in an existing `CLAUDE.md`) and nothing else. During a trial, do not retire existing agents, merge in other repositories, archive anything, move files, or change existing rules. Those steps from the adoption checklist (section 9) wait until the owner commits.
2. **Start as a seed.** One hale, the Haku (section 6). It is the smallest commitment and still shows whether the file habits help.
3. **Mark the start.** Tag the commit before the trial, for example `git tag kauhale-trial-start`, and push the tag. It makes the "before" state easy to find and compare.
4. **Set a review date,** two to four weeks out, and write it in MASTER.md. The Haku raises it when the date arrives.
5. **For websites,** the exclusion of `staff/` from the build is the one change to an existing file the trial needs. Note it in MASTER.md so it is removed with everything else.

### At the review date

The owner chooses one of three:

- **Keep** the seed as it is.
- **Grow** it into a household: follow the rest of the adoption checklist and section 6's growth steps.
- **Remove** it: in one commit, delete `staff/`, remove the kauhale section of `CLAUDE.md` (or the file, if the trial created it), and undo any build exclusion. Optionally keep the decision log first, for example as `docs/decisions.md`. Delete the trial tag if it is no longer wanted.

## 11. Setup steps

1. **Create the repository** in your GitHub account or organization; private is fine.
2. **Install the Claude GitHub App** with access to the repository (github.com/apps/claude, choose your account, Configure, add the repo). Without it, agent chats cannot push.
3. **Scaffold the folders** from section 8, with empty templates from section 15.
4. **Write the role files**: one per agent, plus `_employee-base.md` with the shared rules. Domain, deliverables, owned files, and who to hand off to.
5. **Write MASTER.md** (section 15.2): goals and key dates, style rules, ownership table, status by role, decision log, pointer to the directives index.
6. **Write CLAUDE.md** (section 15.1) and the README.
7. **Seed the timeline** (TODO.md or roadmap) from whatever exists: an old spreadsheet, issue list, or planning doc.
8. **Seed TEAM.md** with the humans, names and titles only.
9. **Commit and push.** For an embedded repository with a review workflow, do this on a branch, check the preview, then merge.
10. **Create the Claude project** (section 12).
11. **Open the Haku's chat first** and ask for a sync. It turns the timeline into the first directives.
12. **Open employee chats as they get directives.** An employee with nothing assigned has nothing to do.

## 12. Claude project and tools

**Project instructions:** paste the same text as CLAUDE.md, so app chats and VS Code follow one source. Point to the repository by name.

**Project settings:**
- Keep project memory separate. Agents share only through the repository.
- Upload no files to the project. The repository is the only copy; uploaded copies go stale.
- Archive old chats from before the setup once anything useful in them is captured in the repository.

**Connectors:** GitHub is required. Add what the roles need: Google Drive for documents, Gmail for drafts, Jotform for forms, Google Calendar for dates.

**First prompt in each chat:** when the chat asks to add the repository with push access, choose Allow.

**Opening line for every chat:**

> You are the <Role> for <PROJECT>. Read `lead/roles/<role>.md` and follow it.

Name chats by project, role, and generation: "Novel Editor", later "Novel Editor 2".

**VS Code:** open the repository root (agents read across folders). CLAUDE.md loads automatically. Start each session with the same role line and `git pull`.

**App chat or VS Code?** App chats run in the cloud and reach GitHub from any device. Use VS Code when a role needs something only on your computer: a local database, gitignored PDFs, or a local build.

**Where each hale runs.** It is the same model in both places; what differs is what it can reach. A hale that must run code against local data (a database, images, a network drive) needs Claude Code in VS Code or a terminal on the machine with that data, so it can run, read the result, and fix in a loop. Hale that write, specify, review, or coordinate work well in app chats. In an analysis pipeline, builders that touch code run on the machine with the data; the Physicist, Statistician, Reporter, Programmer reviews, and the Haku run anywhere.

**One rule across both:** never run the same role in two places at once.

## 13. Using other models

Nothing in the method is specific to Claude. It needs three things: a model that follows written instructions reliably, the ability to read and write files, and a way to sync them (git, or a shared folder).

- **Instruction file names differ by tool.** Claude Code reads `CLAUDE.md`. Several other agent tools read `AGENTS.md` by convention, and some use their own filename. Keep the rules in one file and have the others point to it, so every tool reads the same household rules.
- **Repository access differs.** How a chat attaches, clones, and pushes depends on the product. The role files, templates, and routines carry over unchanged; only the "get the repository" step changes.
- **Models can be mixed across hale.** The repository is the only interface between agents, so one hale can run on one model and another on a different one. Keep the one-session-per-hale rule.
- **Discipline matters more with weaker models.** A model that follows instructions loosely will skip checkpoints or write outside its kuleana. Enforce ownership in GitHub (see section 17) rather than relying on instructions alone.

## 14. Operating rhythm

**Each working session, per employee:** the agent pulls, reads its state and directives, reports in three lines, works, then checkpoints.

**Checkpoint** (say "checkpoint"):
1. Append the session to today's log.
2. Update the directive files worked on; move finished ones to `done/`; update the index.
3. Rewrite STATE.md, with anything the Haku must know at the top.
4. Commit `[PREFIX] PREFIX-NNN checkpoint`, then `git pull --rebase`, then `git push`.

**Sync** (say "sync" in the Haku chat):
1. Update the timeline: check off finished items, refresh what is overdue and coming up.
2. Refresh status by role in MASTER.md; close finished directives.
3. Issue new directives for items coming due.
4. Route requests; review self-proposed directives.
5. Flag anything waiting on a person for more than 7 days.
6. Log decisions.

**Where to talk:** decide in the Haku chat; do deep work in employee chats. Long technical work in the Haku chat fills its context with detail, which is the overload this design avoids.

## 15. Templates

### 15.1 CLAUDE.md

```
# <PROJECT> Agent Instructions

<One sentence on the project.> The GitHub repository
<owner>/<repo> (branch main) is the single source of truth.

## Roles
Each chat plays exactly one role, named in its first message. If no
role is named, ask which one before doing anything.

| Role | Writes in | Role file |
|---|---|---|
| Haku | lead/ | lead/roles/lead.md |
| <Role> | <role>/ | lead/roles/<role>.md |

Employees also follow lead/roles/_employee-base.md. Ownership,
dates, and style rules are in lead/MASTER.md.

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

### 15.2 MASTER.md sections

1. **Goals and key dates**
2. **Style rules for all agents**: the owner's voice, spelling, punctuation, and words to avoid
3. **Ownership**: each role, its folder, and any shared files it owns
   - **Review gate** (when the kauhale has advisors): which reviews each kind of change needs before it merges
4. **Status by role**: three to five lines each, with active directive IDs
5. **Decision log**: dated, one line each, with the source directive
6. **Pointer to the directives index**

### 15.3 Role file

```
# Role: <Role>

- Folder: <folder>/
- Prefix: <PREFIX>
- Reports to: Haku

Before anything else, read lead/roles/_employee-base.md and follow it.

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

### 15.4 Hale base rules (headings to include)

- **Access:** write only in your folder and assigned files; read anything permitted.
- **Markdown and deliverables:** markdown for thinking and communicating; deliverable formats only for finished output.
- **Your folder:** STATE.md, DIRECTIVES.md, directives/, OUTBOX.md, log/, notes/.
- **Directives:** one file each, index first, open only active ones, move finished to done/.
- **Working with people:** `[human: Name]` tasks, drafts for the owner to send, a "Waiting on people" list.
- **Daily log:** append-only, one file per day.
- **Start of session** and **Checkpoint** routines from section 14.
- **Requests to others** through OUTBOX.md; answers go in your own notes/.
- **Reviews:** how to request one, and (for advisors) how to give one.
- **Standing rules:** no sending, no signing, no personal data in git; name the owning role when asked about another domain.

### 15.5 STATE.md

```
# <Role> State

Last checkpoint: YYYY-MM-DD

## For the Haku
## Waiting on people
## Status
## Decisions and reasons
## Open questions
## Next steps
## File index
```

### 15.6 Directive file: `directives/<PREFIX>-NNN-short-title.md`

```
# <PREFIX>-NNN  Title

Source: LEAD-NNN | colleague request (role, date) | self (proposed)
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

Haku directives add `Assigned to:` and `Adopted as:` lines. The employee adopts each one under its own ID, citing the Haku's ID in `Source:`.

### 15.7 DIRECTIVES.md index

```
## Active
| ID | Title | Source | Due | Status | File |

## Done
| ID | Title | Closed | Outcome | File |
```

### 15.8 OUTBOX entry

```
### YYYY-MM-DD  To: <role>  Re: <PREFIX>-NNN.M
Request:
Definition of done:
Needed by: YYYY-MM-DD
Status: open
```

### 15.9 Log entry: `log/YYYY-MM-DD.md`

```
## HH:MM  <PREFIX>-NNN.M  short title
Did:
Found:
Decided (and why):
Open:
```

### 15.10 Advisor role file (additions)

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

### 15.11 Review note: `notes/reviews/<branch>.md`

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

### 15.12 TEAM.md

```
| Role | Human counterpart | Their part | Agent's part | Connects |
```

"Connects" is **Direct** (has GitHub access and may run the role in their own session) or **Through the owner** (the agent drafts; the owner sends and pastes replies back). Names and titles only.

## 16. Git conventions

- Commit messages: `[PREFIX] PREFIX-NNN short description`.
- Agent files commit directly to `main`. Each agent writes only its own folder, so parallel pushes rebase cleanly.
- Published files in an embedded repository go through the existing review workflow (branch, preview, approval, merge).
- Never force-push or rewrite `main`. Unverified-commit badges on old commits are cosmetic; leave them.
- `.gitignore` large binaries and sensitive data. For files that must stay local, such as copyrighted PDFs, commit a manifest listing what should be present, named by key.
- Keep `main` free of branch protection rules that would reject agent pushes, unless you add the pull-request setup in section 17.

## 17. Human counterparts and access

- **TEAM.md** names the human behind each role and how they connect.
- **Agents never contact people.** They draft; the owner sends.
- **Tracking:** `[human: Name]` tags on tasks, a `Human:` line on directives, a "Waiting on people" list in STATE.md, and the Haku flags anything older than 7 days at sync.
- **Counterparts with GitHub access** need only a Claude account with the GitHub connector and one opening line naming their role and themselves. The repository carries the rules.
- **Limiting a counterpart to their role** takes GitHub, since instructions alone are not enforcement:
  - Any plan: a ruleset on `main` requiring pull requests, with the owner as the only bypass; a role map of GitHub usernames; a GitHub Action that fails a pull request touching folders outside the author's role; CODEOWNERS for the Haku folder.
  - Team or Enterprise plan: push rulesets that block changes to protected paths unless the pusher is on the bypass list.

## 18. Long-run maintenance

**Rotate chats** when an agent forgets earlier decisions, repeats itself, or slows down, or on a schedule (weekly, or after each finished directive):
1. Say "checkpoint" and confirm the commit reached GitHub.
2. Archive the old chat.
3. Open "<Project> <Role> N+1" with the same role line.

**Keep the read-on-start files small:**
- STATE.md stays about one page.
- Finished directives live in `done/` and are read only for history.
- Logs grow freely; agents read them only when needed.
- Monthly, the Haku moves decision-log entries older than 30 days to `notes/decisions-archive.md` and collapses finished timeline sections.

**The rule that matters most:** never end a session without a checkpoint.

## 19. Lessons learned

- **Read before restructuring.** Look at the existing repositories, timelines, and agents before designing roles. One conference repository already had team labels and a planner agent whose duties split cleanly into the new roles.
- **Deliverables as fragments.** When the product must be assembled (LaTeX attachments, a website, a book's chapters), each role writes plain fragments in its own folder and one role owns the build that pulls them in. Ownership stays clean and the build stays in one place.
- **Specialists appear as you go.** A grant team added a Statistician once power calculations and demographics outgrew the Physicist. Adding a role means a role file, a folder, a row in the ownership and access tables, and a decision-log entry.
- **Standing rules go in role files; work goes in directives.** A format for paper notes is a rule. Reading ten papers is a directive.
- **Local-only resources need a plan.** A local database or gitignored PDFs are reachable only from VS Code on the machine that has them. Say so in the role file.
- **Verify exclusions on a preview** before trusting that private planning files stay unpublished.
- **Separate making from judging.** In an imaging pipeline, builders own stages and advisors (Physicist, Statistician, Programmer) own specifications and reviews. The builder that wrote a calibration change is the wrong one to judge its physics.
- **Code projects map hale to the pipeline.** When a codebase already has stages, give each builder a contiguous run of stages and every file exactly one owner. Check ownership with a script: every file should have one owner and none should have two.
- **Respect existing conventions.** One codebase already had a stage-grouped TODO.md with stable IDs and `Refs TODO:` commits. The kauhale kept them: directives cite TODO IDs, and each hale closes items in its own stages.
- **Agents report state; the Haku owns the timeline.** Employees never edit the master timeline. They report finished items, and the Haku checks them off.

## 20. New project checklist

- [ ] Trial only: start tagged, additive changes only, review date in MASTER.md
- [ ] Existing repository: adoption checklist (section 9) followed
- [ ] Shape decided: seed or household, standalone or embedded, roles, product format, humans
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
- [ ] Haku chat opened; first sync run
- [ ] First employee chats opened with role lines
- [ ] First checkpoint confirmed on GitHub

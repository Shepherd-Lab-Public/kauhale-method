# The Kauhale Method

A way to run a large, long project as a household of AI agents. Each agent keeps its own house, works its own responsibility, and writes everything that matters to shared files, so no chat ever has to remember the whole project. It was developed on a grant proposal, a scientific conference, a medical hardware project, and a medical imaging analysis pipeline, and it suits any long project with an endless variety of distinct kinds of work: books, websites, research, events, device development, committee work, etc.

The Kauhale Method was created by John Shepherd and Sven Prevrhal, inspired by conversations the two had at MICCAI 2026.

Copyright © 2026 John A. Shepherd and Sven Prevrhal. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/): you may share and adapt it, with credit to the authors.

Version 2026-10-09. Changes from 2026-10-06: every kauhale keeps its hale under one `staff/` folder, in every kind of repository; the shared base rules are named `_hale-base.md` everywhere; adopting a product repository now moves its planning files into the kauhale and checks the live product by URL; new lessons on published working files and edge caches (section 20).

Throughout this guide, **the owner** means you: the person the agents work for, who makes the final decisions.

### The words in this guide

The Kauhale Method is a modern way of organizing AI-assisted work, developed in Hawaiʻi. It makes no claim to be a traditional Hawaiian practice or to carry Hawaiian knowledge. It uses Hawaiian words where they fit, as a mark of respect for the Hawaiian people, their language, and the place where the method took shape. Each word is explained more fully in Part B, section 1.

| Word | Say it | Meaning | In the method |
|---|---|---|---|
| **Kauhale** | kow-HAH-leh | a household compound made of several separate houses | the whole project, held in one GitHub repository |
| **Hale** | HAH-leh | a house | one AI agent and its folder of notes; one hale per kind of work |
| **Haku** | HAH-koo | head or overseer; also to arrange or braid, as in braiding a lei | the head of the kauhale: the hale that coordinates all the others |
| **Kuleana** | koo-leh-AH-nah | responsibility, and the right that comes with it | what each hale is responsible for, and the files only it may change |
| **Kauoha** | kow-OH-hah | an order or instruction | a directive: one piece of assigned work |
| **Moʻolelo** | MOH-oh-LEH-loh | story, history | the logs and the record of decisions |
| **Hui** | HOO-ee | a gathering | the sync, when the Haku reviews every hale |

Plain English words used throughout:

- **Repository** (or repo): an online folder on GitHub that keeps every version of every file.
- **Directive:** a piece of work with a goal and a clear definition of done.
- **Checkpoint:** the end-of-session routine where an agent writes down everything it did and decided.
- **Builder** and **advisor:** hale that make things, and hale that review and set standards.
- **Control repository:** the kauhale's own private repository, kept beside the repositories it works on (a website, a codebase) when those publish anything.

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
- **Protect them.** Never ask for passwords, tokens, or payment details. Never push, delete, or publish without their explicit go-ahead. Keep personal, financial, or health data out of the repository and out of agent sessions (Part B section 17).
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
  - From a GitHub repository (GitHub Pages, Netlify, Cloudflare Pages, Vercel): the site repository stays as it is. Create a second, private repository for the kauhale itself, its control repository (Part B section 8). Note the site repository for Node 7.
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

Explain that no product file will be moved or renamed. If the repository publishes anything (a website, a public package), the hale go in a new private control repository beside it and the existing repository gains only a short pointer file; any planning files it holds (to-do lists, issue logs, lab books) move into the owning hale's folder (Part B section 9). Otherwise the hale go inside it. Either way, the hale live together in a `staff/` folder, and ownership of existing files is recorded in a table.

Done when the person has seen the inventory and answered these questions.

### Node 6. Seed or household?

Decide together, using Node 1 and Part B section 6:

- **Trial** (a removable seed): for an existing repository whose owner wants to try the method first (Part B section 10). Only `staff/` and `CLAUDE.md` are added, or, for a repository that publishes, a separate control repository is created; nothing existing is changed, retired, or moved.
- **Seed** (one hale): one kind of work, one person, and the project fits comfortably in a chat or two. Most new projects start here.
- **Household** (several hale): several distinct kinds of work, other people involved, or a long horizon of months.

For a household, look at what is already in the repository, then propose hale that fit how the work is organized, including any advisors (Part B section 7). Use Part B section 0 for book and website examples. Ask the person to confirm or adjust the list.

Done when the shape is agreed: trial, seed, or a named list of hale with what each owns.

### Node 7. Where the hale will work

Ask: "Does any part of this project need programs to run on your own computer, or files that live only there?"

- **No** (writing, planning, most websites): every hale works in Claude chats. Go on.
- **Yes** (code that runs on local data, large files that stay off GitHub): those hale should run in Claude Code inside VS Code on that computer. Give a short pointer to installing VS Code and Claude Code, and note it in the setup; it can be done later.

For a website or anything else that publishes, confirm that the kauhale lives in its own control repository, and list which product repositories each hale may change (Part B section 8).

### Node 8. People

If others are involved, ask who, what part each person plays, and whether each will have their own GitHub access. This becomes TEAM.md. Names and roles only; no phone numbers or personal emails in the repository. If there are none, skip TEAM.md.

### Node 9. Style and rules

Ask how the agents should write: voice, spelling (US or UK), punctuation habits, words or constructions to avoid, formality. Ask for any hard rules ("never email anyone," "never change the published site without asking"). These go into KAUHALE.md.

Then ask: "Will the project touch anything sensitive: patient or participant data, personal contact details, salaries, evaluations of people, unpublished results, passwords or keys?" Use the list in Part B section 17. For each yes, agree where it will live outside the repository. If identifiable health or participant data is involved, ask whether the institution and the AI service plan allow it in agent sessions; if not, or if they are unsure, the agents use de-identified data only. Record the answers in KAUHALE.md under the data rules, and suggest a compliance advisor (Part B section 7) for regulated data.

### Node 10. Build it

Summarize the plan in a few lines and ask for the go-ahead. For an existing repository, do all of this on a new branch, follow the remaining steps of the adoption checklist (Part B section 9), and merge only after the person approves. Then:

- **Trial:** tag the current commit (`kauhale-trial-start`) and push the tag, create the seed files, write the review date into KAUHALE.md, and change nothing else in the repository.
- **Seed:** create the files in Part B section 6 ("Seed layout").
- **Household:** create the files in Part B sections 8 and 15 (layout and templates): CLAUDE.md, the Haku's folder `staff/lead/` with KAUHALE.md, STATE.md, PRODUCTS.md, DIRECTIVES.md, roles, and TEAM.md if needed, plus one folder per hale under `staff/`.

Fill KAUHALE.md with the goals, dates, and style rules gathered so far. Commit and push. If you cannot push, give the person the files and walk them through "Add file," then "Upload files."

For a control repository, add a short CLAUDE.md to each product repository that points to the control repository and names the hale that owns it, through that repository's normal review workflow. Nothing else of the kauhale goes there.

Done when the files are on GitHub and the person can see them.

### Node 11. The Claude project

Walk them through creating a Claude project for this kauhale:

- Name it after the project.
- Paste the contents of CLAUDE.md into the project instructions.
- Keep project memory separate from their other projects, if the setting is available, so the hale share only through the repository.
- Upload no project files; the repository is the only copy.

### Node 12. First session

Have them open a new chat in the project and send the opening line for the Haku, for example:

> You are the Haku (Editor) for <PROJECT>. Read `staff/lead/roles/lead.md` and follow it.

(Every kauhale uses the same path, `staff/lead/roles/lead.md`, whether it is standalone or a control repository.)

(For a seed: "You are the Haku (Lead) for <PROJECT>. Read `staff/lead/KAUHALE.md` and `staff/lead/STATE.md`, then follow CLAUDE.md.")

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

For a website, the kauhale lives in its own private repository and the Webmaster's kuleana extends into the site repository (section 8, "Control repository").

### Your own style rules

KAUHALE.md has a place for style rules every agent follows (section 15.2). Put your own there: voice, spelling, punctuation habits, words to avoid, how formal to be. The agents apply them to everything they write.

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

**Haku** means head or overseer: the one a household answers to. It also means to arrange or compose. *Haku mele* is composing a song; *haku lei* is braiding a lei. That second sense describes the job. The Haku does not do every hale's work; it braids their work into one thing.

The Haku is the head of the kauhale. It keeps its own hale like every other agent, and it also coordinates the whole compound: it reads every hale's state, issues kauoha (directives), keeps KAUHALE.md, the record of the whole compound, and brings decisions to the owner. Every kauhale has exactly one Haku, from a one-hale seed to a full household.

A project may also give its Haku a familiar title: Haku (PI) for a grant, Haku (Chair) for a conference, Haku (Editor) for a book, Haku (Lead) for a codebase. The folder and role file stay `staff/lead/` and `lead.md` whatever the title, so one opening line works for every project: "You are the Haku for <PROJECT>."

### Kuleana: what each hale is responsible for

**Kuleana** means responsibility, and it also means right and privilege; historically it named a family's own parcel of land, which they had both the right to use and the duty to tend. The two senses together are the method's ownership rule.

- **The right:** each hale alone writes its own files, plus any shared files assigned to it. No other agent edits them.
- **The duty:** each hale is answerable for its domain. It keeps its state current, finishes its directives, records its decisions, and reports what the Haku needs to know.

"Stay in your kuleana" is the rule every agent follows. When work belongs to another hale, the agent asks that hale through its outbox instead of doing the work itself.

### The rest of the vocabulary

| Hawaiian | Meaning | In the method |
|---|---|---|
| Kauhale | household compound | the project and its repository; KAUHALE.md is the Haku's record of it |
| Hale | house | one agent: its role and its folder |
| Haku | head; to arrange or braid | the head of the kauhale, which coordinates every hale |
| Kuleana | responsibility and right; one's own parcel | the role's domain and the files only it may write |
| Kauoha | command, order | a directive |
| Moʻolelo | story, history | the daily logs and the decision log |
| Hui | gathering | the sync, where the Haku reviews every hale |

File and folder names stay in plain English (STATE.md, DIRECTIVES.md) so any agent or collaborator can read them anywhere, with one exception: the Haku's record of the whole project is **KAUHALE.md**, because it is the record of the kauhale itself. One word then names one thing: the project is the kauhale, and KAUHALE.md is its record. The other Hawaiian names describe the method and how it is taught.

### A method from Hawaiʻi

The Kauhale Method was developed in Hawaiʻi, and its language reflects that. It is a project-management method for AI agents, created in 2026. The traditional kauhale, the role of a haku, and the meaning of kuleana belong to Hawaiian culture and history, which are far richer than anything described here. The method borrows these words as metaphors because they capture its ideas well, and uses them to honor the Hawaiian people and the Hawaiian language, ʻōlelo Hawaiʻi.

When you teach or present the method, describe it the same way: a method made in Hawaiʻi that uses Hawaiian words with respect.

**A note on use.** These words (kauhale, hale, haku, kuleana, kauoha, moʻolelo, hui) carry cultural meaning. Spell them with their ʻokina and kahakō where they apply, use them in their meanings above, and avoid stretching them to cover things they do not mean. Before presenting or publishing the method, ask a Hawaiian language or cultural advisor to review how they are used here.

## 2. Why this works

A single chat has a limited context window and degrades as it grows. Splitting a project across agents, each holding one slice, keeps every slice sharp. The gain comes from the files: each agent writes its memory to markdown in the repository, so any chat can be replaced by a fresh one that resumes from those files in one read.

Three ideas carry the whole design:

- **The hale remembers; the occupant changes.** Files are the memory and chats are replaceable workers. Anything said in a chat and never written to a file is lost when the chat is rotated.
- **One Haku sees the whole.** The Haku reads summaries from every hale, issues kauoha (directives), and keeps KAUHALE.md, the record of the whole compound.
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

The two combine, within limits. Run one Claude Code session as the Haku and define a role as a subagent in `.claude/agents/<role>.md` whose instructions say "read `staff/lead/roles/<role>.md` and follow it." The Haku dispatches a directive ("Statistician, work STAT-002"); the subagent works in a fresh context, checkpoints to its folder, and returns a summary. You keep the file discipline of the team and lose the window switching.

A subagent that reads a role file *is* that hale, so the hybrid is bound by the rule that a hale runs in one place at a time (section 12). The Haku dispatches a hale subagent only when all of these hold:

- **The owner asks for it,** naming the hale and the directive. The Haku never dispatches on its own initiative, and no other hale dispatches at all.
- **The owner confirms the hale has no open session** anywhere: no chat, no VS Code session, no other subagent.
- **It runs in the foreground,** one at a time, and returns before the Haku does anything else in that hale's domain. Never in the background.

Use the hybrid for short, well-defined directives. Keep a dedicated chat for long back-and-forth work in one domain, such as drafting the Approach or iterating on power assumptions. Both read and write the same files, so a hale can be run either way, but never both at once: close the chat (after a checkpoint) before dispatching that hale as a subagent.

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
| Haku | The head of the kauhale, the coordinating hale (titled PI for a grant, Chair for a conference, Editor for a book, Lead for a codebase). The owner talks to it about direction and priorities. |
| Staff hale | Any hale other than the Haku: a specialist with one domain (Librarian, CFO, Webmaster, and so on), builder or advisor. |
| Helper | A subagent a hale starts for a piece of its own work (search, read, summarize, draft). It loads no role file and writes nothing; the hale that started it does all the writing. |
| Directive | The unit of work: a goal with a definition of done. One file per directive. |
| Task | A step inside a directive, numbered under it (SCI-004.2). |
| Product | A work product the owner opens, reads, or sends: a list, tracker, draft, chart, or recommendation. Listed in PRODUCTS.md. Logs, STATE.md, and OUTBOX.md are working files, never products. |
| Checkpoint | The end-of-session routine: log, update directives, update PRODUCTS.md, rewrite STATE.md, commit, push. |
| Sync | The Haku's routine: read every hale's state, update KAUHALE.md, compile the products catalog, issue directives. |
| Counterpart | The human behind a role, listed in TEAM.md. |
| Control repository | The kauhale's own private repository, beside the product repositories its hale own. |
| Product repository | A repository holding only product (a website, code, an organization's records), owned by one hale. |
| Builder hale | A hale that produces the work product: owns code, documents, or data, and changes them. |
| Advisor hale | A consultant hale that owns specifications and reviews. Builders implement against its specs; it signs off before merge. |
| Specification | An advisor's written standard: definitions, models, or acceptance criteria that builders must meet. |
| Review gate | The rule for which reviews a change needs before it merges. Recorded in KAUHALE.md. |

## 5. Decide the shape first

Answer these before creating anything.

1. **Standalone or control repository?** One rule decides it: **a kauhale never shares a repository with anything that publishes.**
   - **Standalone** (a grant proposal, a book manuscript, a private analysis pipeline): the repository exists for the project and nothing is published from it. The kauhale lives inside it.
   - **Control repository** (a conference with a website, a center with several repositories): the product publishes, or the work spans several repositories. The kauhale gets its own private repository, and hale reach into the product repositories they own.
2. **What are the roles?** Mirror how the work is already divided. Existing team labels in a timeline or spreadsheet are a good source (a conference timeline with six team labels, such as planning, finances, and sponsors, became six roles). Five or six staff hale is a workable number. A project with one kind of work can start as a seed kauhale (section 6) and grow.
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
  KAUHALE.md              facts and goals, style rules, decision log
  STATE.md                one-page resumable state
  PRODUCTS.md             what the owner opens: each work product, with link, as-of date, status
  TODO.md                 the work list (directives come later)
  log/                    daily log, append-only
  notes/                  findings, drafts, research
```

For a website, the seed lives in its own control repository beside the site, exactly as a full kauhale would (section 8).

The single hale is the Haku from the start, titled Lead, Editor, Chair, or PI as fits the project. It heads a kauhale of one, so when others arrive it already has the right name, folder, and files.

### Seed routine

- **Start of session:** pull, read KAUHALE.md and STATE.md, report in three lines.
- **Checkpoint:** append to the log, update TODO.md and PRODUCTS.md, rewrite STATE.md, log decisions in KAUHALE.md, commit and push.
- **Rotate** the chat when it grows long; the new one resumes from STATE.md.

### When to add the second hale

Add one when any of these happens:

- one chat can no longer hold the project, even with regular rotation;
- a distinct kind of work appears that has its own sources and decisions (references, a budget, code review, continuity checking for a book);
- a second person joins.

### Growing from seed to household

1. The Lead gets a role file: `staff/lead/roles/lead.md`.
2. Add the shared base rules: `staff/lead/roles/_hale-base.md`.
3. Add an ownership table (and a review gate, if the new hale is an advisor) to KAUHALE.md.
4. Convert TODO.md items that belong to the new hale into directives: add `staff/lead/DIRECTIVES.md` and `staff/lead/directives/`.
5. Create the new hale's folder (STATE, PRODUCTS, DIRECTIVES index, directives/, OUTBOX, log, notes) and its role file.
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
| Bioethics or compliance | Human subjects, data governance, or regulations constrain what builders may do (section 17, "Who checks") |

A text project (a grant, a conference) usually needs few advisors or none; its builders and the Haku are enough. A code project usually needs at least a Programmer.

### The review gate

Write the gate into KAUHALE.md as a table: which reviews a change needs, depending on what it touches, plus the owner's final approval. For an imaging analysis pipeline:

| Review | Required when |
|---|---|
| Programmer | every code branch |
| Physicist | the change touches calibration, phantom or pose geometry, or thickness |
| Statistician | the change touches measurements, features, or the final analysis |
| Owner | always; the owner decides on the Haku's recommendation |

The builder requests reviews through its OUTBOX, naming the branch, what changed, and how it was tested. The Haku summarizes the verdicts for the owner with a merge recommendation.

## 8. Repository layout

### One layout everywhere

Every kauhale keeps all of its hale together in one `staff/` folder, with the Haku at `staff/lead/`. The rule holds for a standalone repository, a control repository, a seed, and a full household. One shape means one set of paths in every role file, launcher, and opening line; a seed grows without moving anything; and the household never mixes with product files.

### Standalone

```
<repo>/
  CLAUDE.md                  agent instructions, loaded automatically
  README.md                  how the system works, for humans
  .gitignore
  staff/
    lead/                    the Haku's folder, whatever its title (PI, Chair, Editor)
      KAUHALE.md             the record of the whole kauhale
      STATE.md               the Haku's own one-page resumable summary
      TODO.md or roadmap     the overall timeline
      TEAM.md                roles mapped to humans
      PRODUCTS.md            the owner's front door: every hale's products, compiled at sync
      DIRECTIVES.md          index of all the Haku's directives
      directives/            one file per directive; done/ for finished ones
      roles/                 one role file per agent, plus _hale-base.md
      log/  notes/
    <hale>/                  one folder per staff hale
      STATE.md               one-page resumable summary
      PRODUCTS.md            this hale's work products, with links
      DIRECTIVES.md          index of this hale's directives
      directives/  directives/done/
      OUTBOX.md              requests to others
      log/  notes/
      tex/ or other          finished deliverable fragments, if the role writes any
  .claude/skills/<hale>/     one launcher per hale, if you use Claude Code (section 12)
  ...product files, if any, outside staff/
```

When a standalone repository already holds the product (code, a manuscript), the product files stay where they are and `staff/` sits beside them. Assign ownership of product files in KAUHALE.md without moving them.

**If a standalone product is ever released** (code published with a paper, a repository made public), separate first: release a clean copy of the product, or move `staff/` into its own control repository. Write this tripwire into KAUHALE.md.

### Control repository

The kauhale lives in its own private repository. The products it works on live in their own repositories, which hold only product files.

```
<project>-staff/  or  <org>-admin/      the control repository (private, never publishes)
  CLAUDE.md, README.md
  staff/
    lead/                                the Haku's folder, as above
    <hale>/                              one folder per hale, as above
  .claude/skills/<hale>/                 one launcher per hale (section 12)

<product-repo>/                          a website, a codebase, an organizational repo
  CLAUDE.md                              a pointer only: "This repository is owned by the
                                         <Hale> hale of <control repo>. Read its role file there."
  ...product files only...
```

- **Ownership:** KAUHALE.md lists each product repository and the one hale that owns it. A hale's kuleana is its folder in the control repository plus the product repositories assigned to it.
- **Product repositories hold product only.** To-do lists, issue logs, lab books, and audit worksheets are planning and working files; they live in the owning hale's folder. A technical manual for the product (how it builds, deploys, and is tested) stays with the product.
- **Where the work lives:** directives, logs, notes, drafts, and reviews stay in the control repository. Only finished product goes into a product repository. The one exception is a hale that leads units in a private product repository (see "Larger organizations" below).
- **One home per hale:** a hale writes its records (STATE, directives, OUTBOX, log, notes) in exactly one repository, its home. Every other repository it only reads, or changes as product through that repository's workflow.
- **Working in two repositories:** in an app chat, attach both. In VS Code, keep sibling clones and open them together as one workspace.
- **Product rules stay in force:** each product repository keeps its own workflow (branch, preview, approval, merge). The hale that owns it follows that workflow.
- **Access:** GitHub grants access per repository. Everyone who runs a hale can read the whole control repository, so material some counterparts should not see (draft evaluations of people or projects, advisory committee comments, salaries) stays off GitHub, with a pointer in the control repository (section 17).

### Larger organizations

A center or department with many repositories (a core lab, a website, workshops, one repository per project) uses one control repository for the whole organization, typically `<org>-admin`. Each hale owns one or more of the organization's repositories, and its counterpart is the person who runs that part of the organization.

A hale with a large domain can have **units** of its own: a Webmaster with a designer and a content editor, for example. Keep it to two levels:

- **The units live in the control repository,** under the hale's folder (`staff/webmaster/units/<unit>/`), or in a private, non-publishing repository the hale owns. Never in a repository that publishes.
- **One record per level.** The hale's own STATE, directives, and OUTBOX are the only things the Haku reads. Units report to the hale, and the hale summarizes upward at each checkpoint.
- **The hale's home follows its units.** When the units live in a product repository the hale owns, the hale's whole house moves there with them (`<product-repo>/staff/<hale>/`). The hale reads the control repository for the Haku's directives and the shared rules, and writes nothing there. It adopts each Haku directive in its own index, posts requests to other hale in its own OUTBOX, and the Haku reads that house and relays the requests at sync. The control repository keeps a one-line pointer in place of the hale's folder, and KAUHALE.md records where the house is. Before moving, check who can read the product repository: directives often carry budget figures and remarks about named people.
- **One Haku per kauhale.** The hale that leads units keeps its plain title (Webmaster, Core Lead).
- **The owner opens units.** A unit is a session with its own role file, so the hale that leads it never starts it itself (section 12, "Only the owner opens a hale").

## 9. Adopting an existing repository

Most projects already exist before they become a kauhale. An existing repository carries history, conventions, collaborators, and sometimes an earlier agent setup. Adopting it means fitting the household around what works, without moving or renaming what others depend on.

### The adoption checklist

1. **Take inventory before designing anything.** Read the README and any docs; find every to-do list, notes folder, issue tracker, and planning file; list the branches and who has been committing; note how the work is built or published; and look for an existing agent setup (`CLAUDE.md`, `AGENTS.md`, `AGENT.md`, `.claude/agents/`, custom commands). Present the inventory to the owner before proposing hale.
2. **Decide what happens to any existing agent setup.** Keep it if it still fits, split its duties across the new hale, or retire it. If a `CLAUDE.md` or `AGENTS.md` already exists, merge the kauhale rules into it rather than replacing it, and keep anything the owner still relies on.
3. **Keep the working conventions.** If the repository already has a to-do list with stable IDs, a notes convention, or a commit message format, the kauhale adopts them. Directives cite existing items rather than copying them, and hale close items in their own sections.
4. **Assign ownership without moving files.** Website pages, data files, and code stay where the build and imports expect them. Record ownership in KAUHALE.md as a table. For code projects, check it with a script: every file has exactly one owner.
5. **Decide where the kauhale lives, then reconcile with existing rules.** If the repository publishes anything, create a control repository for the kauhale (section 8); the existing repository keeps its rules unchanged and gains only a pointer CLAUDE.md. If it never publishes, the kauhale goes in `staff/`: keep any review rules for the product and add a narrow, written exception for `staff/`, recorded wherever the existing rules live.
6. **Move planning files out of a product repository.** When the kauhale lives in a control repository, the product repository's to-do list, issue log, and running log move to the owning hale: open items into a living backlog in its `notes/`, the full text verbatim into a history folder in its `notes/`, and items another hale leads into that hale's notes. Fix every reference (README, build excludes, scripts) in the same reviewed change. Keep the product's technical manual where it is.
7. **Fold in related repositories.** If planning lives in a separate repository, move what is still current into the Haku's folder, note where it came from, and archive the old repository once the move is confirmed.
8. **Assign existing branches.** Give each active branch an owning hale. Flag dead branches as "do not build on" rather than deleting them.
9. **Map the people already working.** People who already commit become counterparts for the hale that cover their work. Record them in TEAM.md and confirm their GitHub access.
10. **Make the adoption itself a reviewed change.** Any change to the existing repository (the pointer CLAUDE.md, the planning-file move, or `staff/` in a standalone one) goes on a branch. The owner approves, then merge.
11. **Check what the live product actually publishes.** Request each working file and folder by its public URL (to-do lists, `docs/`, notes, CSVs, the pointer CLAUDE.md) and confirm it returns 404. Reading the exclude list is not enough.

### Worked examples

- **A conference website** (control repository): the site repository was a live Jekyll site with its own agent manual, a planner agent, and a branch-and-preview rule. The kauhale lives in a separate private staff repository. The planner's duties were split between a ScienceAdmin and a Webmaster and the planner retired. The Webmaster's kuleana extends into the site repository, where it follows the site's preview rule; its directives and notes stay in the staff repository. (The team first lived inside the site repository under an excluded `staff/` folder; see the lesson in section 20.)
- **An imaging analysis pipeline** (code): the repository had an 11-stage pipeline, a stage-grouped TODO.md with stable IDs and `Refs TODO:` commits, a lab notebook, and several experiment branches. Builder hale were drawn along pipeline stages, every code file got one owner (checked by script), the existing TODO.md stayed the main work list, experiment branches were assigned to their hale, and two active collaborators became counterparts.

## 10. Trying the method without committing

A person with an existing repository may want to try a kauhale before buying in. That works well if the trial is built to be removed cleanly.

### Remove the household, keep the work

Ending a trial means deleting the kauhale's files in one new commit. Resetting the repository to the commit before the trial would also erase the real work done during it (chapters, fixes, pages), would discard anyone else's commits from that period, and would need a force-push. The household comes out; the work stays.

### Trial rules

1. **Additive only.** For a repository that never publishes, the trial adds `staff/` and `CLAUDE.md` (or a clearly marked section in an existing `CLAUDE.md`) and nothing else. For one that publishes, the trial is a new control repository and the existing repository is not touched at all. During a trial, do not retire existing agents, merge in other repositories, archive anything, move files, or change existing rules. Those steps from the adoption checklist (section 9) wait until the owner commits.
2. **Start as a seed.** One hale, the Haku (section 6). It is the smallest commitment and still shows whether the file habits help.
3. **Mark the start.** Tag the commit before the trial, for example `git tag kauhale-trial-start`, and push the tag. It makes the "before" state easy to find and compare.
4. **Set a review date,** two to four weeks out, and write it in KAUHALE.md. The Haku raises it when the date arrives.

### At the review date

The owner chooses one of three:

- **Keep** the seed as it is.
- **Grow** it into a household: follow the rest of the adoption checklist and section 6's growth steps.
- **Remove** it: in one commit, delete `staff/` and remove the kauhale section of `CLAUDE.md` (or the file, if the trial created it). For a trial in a control repository, archive that repository instead. Optionally keep the decision log first, for example as `docs/decisions.md`. Delete the trial tag if it is no longer wanted.

## 11. Setup steps

1. **Create the repository** in your GitHub account or organization; private is fine.
2. **Install the Claude GitHub App** with access to the repository (github.com/apps/claude, choose your account, Configure, add the repo). Without it, agent chats cannot push.
3. **Scaffold the folders** under `staff/` from section 8, with empty templates from section 15.
4. **Write the role files** in `staff/lead/roles/`: one per agent, plus `_hale-base.md` with the shared rules. Domain, deliverables, owned files, and who to hand off to.
5. **Write KAUHALE.md** (section 15.2): goals and key dates, style rules, ownership table, status by role, decision log, pointer to the directives index.
6. **Write CLAUDE.md** (section 15.1) and the README.
7. **Seed the timeline** (TODO.md or roadmap) from whatever exists: an old spreadsheet, issue list, or planning doc.
8. **Seed TEAM.md** with the humans, names and titles only.
9. **Commit and push.** Any pointer file added to a product repository goes through that repository's own review workflow.
10. **Create the Claude project** (section 12).
11. **Open the Haku's chat first** and ask for a sync. It turns the timeline into the first directives.
12. **Open staff hale chats as they get directives.** A hale with nothing assigned has nothing to do.

## 12. Claude project and tools

**Project instructions:** paste the same text as CLAUDE.md, so app chats and VS Code follow one source. Point to the repository by name.

**Project settings:**
- Keep project memory separate. Agents share only through the repository.
- Upload no files to the project. The repository is the only copy; uploaded copies go stale.
- Archive old chats from before the setup once anything useful in them is captured in the repository.

**Connectors:** GitHub is required. Add what the roles need: Google Drive for documents, Gmail for drafts, Jotform for forms, Google Calendar for dates.

**First prompt in each chat:** when the chat asks to add the repository with push access, choose Allow.

**Opening line for every chat:**

> You are the <Role> for <PROJECT>. Read `staff/lead/roles/<role>.md` and follow it.

Name chats by project, role, and generation: "Novel Editor", later "Novel Editor 2".

**VS Code:** open the repository root (agents read across folders). CLAUDE.md loads automatically. Start each session with the same role line and `git pull`.

**App chat or VS Code?** App chats run in the cloud and reach GitHub from any device. Use VS Code when a role needs something only on your computer: a local database, gitignored PDFs, or a local build.

**Where each hale runs.** It is the same model in both places; what differs is what it can reach. A hale that must run code against local data (a database, images, a network drive) needs Claude Code in VS Code or a terminal on the machine with that data, so it can run, read the result, and fix in a loop. Hale that write, specify, review, or coordinate work well in app chats. In an analysis pipeline, builders that touch code run on the machine with the data; the Physicist, Statistician, Reporter, Programmer reviews, and the Haku run anywhere.

**One rule across both:** never run the same role in two places at once.

**Only the owner opens a hale.** No agent starts a session as another hale, or a second copy of itself, in the foreground or the background. Any session that loads a role file counts as that hale, whether it is a chat, a VS Code session, or a subagent. The single exception is the narrow hybrid dispatch in section 3. A hale may still use helpers (section 4) for its own work: they load no role file, never commit or checkpoint, and return their results to the hale, which does the writing. Work for another hale goes through OUTBOX.md and waits until the owner opens that hale.

In Claude Code, this can be enforced rather than only instructed: a `PreToolUse` hook on the subagent tool that blocks any call whose prompt names a role file (`staff/lead/roles/`), leaving helpers free to run.

**A chat kept open is one long session.** This applies to any chat-based agent tool. The start routine (pull, read state, sweeps) runs only when a session starts, and an app chat kept open for days never starts again: its clone drifts and the routine never reruns. Write the trigger into the base rules: rerun the start routine at the first message of each new day (the hale compares today's date with its latest log file) and whenever the human opens with "start", and `git pull --rebase` before reading other hale's files. Long chats also get summarized, so the repository is the memory.

**Switching roles with one command per hale (Claude-specific).** The mechanism below is unique to Claude Code; the principle is general: give each role a single command that starts a fresh session and loads its role file. Other agent tools offer their own ways to store reusable prompts or commands; use whatever the tool provides, or simply paste the role line into a new session. In Claude Code, give each hale a project skill at `.claude/skills/<hale>/SKILL.md` with `disable-model-invocation: true`, so only the human can run it. The skill pulls, reads CLAUDE.md and the role file, and runs the start routine. Switching roles is then: start a new conversation in the Claude panel and type `/haku`, `/webmaster`, `/statistician`. Each new conversation is a fresh session, so the start routine runs every time without a trigger rule. The skills live in the repository, so every clone has them.

**Split by what each hale must reach.** The principle is general: run a role wherever its tools and data are. In the Claude setup, hale that need connectors (Gmail, Calendar, Drive, the Claude project) run in Claude app chats with the daily-restart rule. Hale that work on repository files and local, gitignored sources run in VS Code, where local folders are visible and fresh sessions come free (section 20, "Open chats never restart").

## 13. Using other models

Nothing in the method is specific to Claude. It needs three things: a model that follows written instructions reliably, the ability to read and write files, and a way to sync them (git, or a shared folder).

- **Instruction file names differ by tool.** Claude Code reads `CLAUDE.md`. Several other agent tools read `AGENTS.md` by convention, and some use their own filename. Keep the rules in one file and have the others point to it, so every tool reads the same household rules.
- **Repository access differs.** How a chat attaches, clones, and pushes depends on the product. The role files, templates, and routines carry over unchanged; only the "get the repository" step changes.
- **Session launchers are tool-specific.** The method needs a way to start a fresh session in a given role. Claude Code does it with project skills invoked as slash commands (section 12); other tools have their own mechanisms, or the role line pasted into a new session works anywhere. Keep the launcher thin: it should only point to the role file, so the rules stay in one tool-neutral place.
- **Models can be mixed across hale.** The repository is the only interface between agents, so one hale can run on one model and another on a different one. Keep the one-session-per-hale rule.
- **Helper agents follow the same rule.** Many tools let an agent launch other agents. Whatever the tool calls them, an agent that loads a role file is that hale, so only the owner starts one (section 12, "Only the owner opens a hale").
- **Data handling differs by service.** What one AI service retains, logs, or uses for training, another may not, and the same vendor's plans can differ. Check each service a hale uses against the project's data rules before it sees anything sensitive (section 17).
- **Discipline matters more with weaker models.** A model that follows instructions loosely will skip checkpoints or write outside its kuleana. Enforce ownership in GitHub (see section 18) rather than relying on instructions alone.

## 14. Operating rhythm

**Each working session, per hale:** the agent pulls, reads its state and directives, reports in three lines, works, then checkpoints. In an app chat kept open, "each working session" means each new day or each "start" (section 12).

**Checkpoint** (say "checkpoint"):
1. Append the session to today's log.
2. Update the directive files worked on; move finished ones to `done/`; update the index.
3. Update PRODUCTS.md: add any new product, refresh the as-of date and status of any that changed.
4. Rewrite STATE.md, with anything the Haku must know at the top.
5. Commit `[PREFIX] PREFIX-NNN checkpoint`, then `git pull --rebase`, then `git push`.

**Sync** (say "sync" in the Haku chat):
1. Update the timeline: check off finished items, refresh what is overdue and coming up.
2. Refresh status by role in KAUHALE.md; close finished directives.
3. Compile the Haku's PRODUCTS.md from every hale's PRODUCTS.md.
4. Issue new directives for items coming due.
5. Route requests; review self-proposed directives.
6. Flag anything waiting on a person for more than 7 days.
7. Log decisions.

**Where to talk:** decide in the Haku chat; do deep work in staff hale chats. Long technical work in the Haku chat fills its context with detail, which is the overload this design avoids.

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
| Haku | staff/lead/ | staff/lead/roles/lead.md |
| <Role> | staff/<role>/ | staff/lead/roles/<role>.md |

Every hale, the Haku included, also follows
staff/lead/roles/_hale-base.md. Ownership, dates, and style rules are
in staff/lead/KAUHALE.md.

## Start of every session
1. App chat: attach and clone <owner>/<repo>. VS Code: git pull.
2. Read your role file and follow it.

## Rules
- Write only in your own folder and the files assigned to you.
- Commit at each checkpoint, then git pull --rebase and git push.
- Never force-push or rewrite history on main.
- Only the owner opens a hale. Never start another hale, or a second
  copy of yourself, as a subagent or background session. Helpers that
  load no role file and write nothing are fine.
- Never send email or contact anyone. Draft it; the owner sends.
- No PHI, personal data, payment details, or secrets in git. Keep them
  where KAUHALE.md's data rules say, and leave a pointer.
- De-identified data only in agent sessions, unless KAUHALE.md's data
  rules say otherwise.
- Logs and notes summarize; never quote an email or copy an address.
- If something sensitive reaches git or an agent session, stop and tell
  the owner.
- <the owner's style rules>
```

### 15.2 KAUHALE.md sections

1. **Goals and key dates**
2. **Style rules for all agents**: the owner's voice, spelling, punctuation, and words to avoid
   - **Data rules**: what sensitive material the project touches, where each kind lives, and what the AI service may see (section 17)
3. **Ownership**: each role, its folder, and any shared files it owns
   - **Review gate** (when the kauhale has advisors): which reviews each kind of change needs before it merges
4. **Status by role**: three to five lines each, with active directive IDs
5. **Decision log**: dated, one line each, with the source directive
6. **Pointer to the directives index** and to PRODUCTS.md

### 15.3 Role file

```
# Role: <Role>

- Folder: staff/<folder>/
- Prefix: <PREFIX>
- Reports to: Haku

Before anything else, read staff/lead/roles/_hale-base.md and follow it.

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
- **Your folder:** STATE.md, PRODUCTS.md, DIRECTIVES.md, directives/, OUTBOX.md, log/, notes/.
- **Products:** list every work product in PRODUCTS.md (section 15.13) and keep it current at checkpoint. Anything with personal or contact data lives in Drive and is listed by document name.
- **Directives:** one file each, index first, open only active ones, move finished to done/.
- **Working with people:** `[human: Name]` tasks, drafts for the owner to send, a "Waiting on people" list.
- **Daily log:** append-only, one file per day.
- **Start of session** and **Checkpoint** routines from section 14.
- **Requests to others** through OUTBOX.md; answers go in your own notes/.
- **Reviews:** how to request one, and (for advisors) how to give one.
- **Standing rules:** no sending, no signing; name the owning role when asked about another domain.
- **Safeguards:** the rules in section 17 and the project's data rules in KAUHALE.md: no PHI, personal data, payment details, or secrets in git; de-identified data only in agent sessions unless the data rules allow more; logs summarize and never quote; report any leak to the owner at once.
- **Sessions:** only the owner opens a hale; never start another hale or a second copy of yourself; use helpers only for your own work (section 12).

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

Haku directives add `Assigned to:` and `Adopted as:` lines. The assigned hale adopts each one under its own ID, citing the Haku's ID in `Source:`.

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

### 15.13 PRODUCTS.md

Each hale keeps one in its folder. The Haku keeps the compiled copy in its own folder, with an Owner column and one section per hale, and links it from KAUHALE.md.

```
# <Role> Products

Last updated: YYYY-MM-DD

| Product | What it is | Where | As of | Status |
|---|---|---|---|---|
| Sponsor pipeline | Every prospect: tier, ask, status, next step | notes/pipeline.md | YYYY-MM-DD | living |
| Planning timeline | Gantt of every directive | <artifact link> | YYYY-MM-DD | living |
| Speaker invitation | Letter for invited speakers | notes/speaker-invite.md | YYYY-MM-DD | draft |
```

"Where" is a repository path, a published page link, or a Drive document named by title. Status is **living** (kept current), **draft** (waiting on the owner), **final** (approved), or **sent**. List products not yet started with their due date, so a missing product is as visible as a finished one.

## 16. Git conventions

- Commit messages: `[PREFIX] PREFIX-NNN short description`.
- Agent files commit directly to `main`. Each agent writes only its own folder, so parallel pushes rebase cleanly.
- Product repositories keep their own review workflow (branch, preview, approval, merge). The hale that owns one follows it.
- Never force-push or rewrite `main`, except to remove leaked material (section 17). Unverified-commit badges on old commits are cosmetic; leave them.
- `.gitignore` large binaries and sensitive data (section 17). For files that must stay local, such as copyrighted PDFs, commit a manifest listing what should be present, named by key.
- When a project needs a database, prefer SQLite: one file, no server to run. Keep the database file out of the repository (gitignore `*.db`, `*.sqlite`). Commit the schema and a script that rebuilds the database from its sources instead. One hale owns the schema and the rebuild script and is the only one that writes; the others read or send requests through OUTBOX.md. If anything in the database cannot be rebuilt, back it up somewhere other than git and say where in the owning hale's role file. Keep the live file off synced folders (Dropbox, OneDrive, Google Drive) and network drives, where SQLite files can be corrupted.
- Keep `main` free of branch protection rules that would reject agent pushes, unless you add the pull-request setup in section 18.

## 17. Safeguards

Every hale follows these rules, whatever model or agent tool runs it; `_hale-base.md` carries them into every role. Sensitive material can leak in three places: the repository, the agent session, and the products. Here, **the AI service** means whoever runs the model a hale uses: the vendor of a chat app, an API provider, or your own institution's server.

### What counts as sensitive

- **Health information:** protected health information (PHI) and anything else that identifies a patient or research participant.
- **Personal data:** home addresses, phone numbers, personal email addresses, birth dates, ID numbers.
- **Credentials:** passwords, API keys, tokens, `.env` files, private keys.
- **Financial details:** card and bank numbers, salaries, individual budgets.
- **Judgments about people:** draft evaluations, reviews of applicants or speakers, committee comments.
- **Material under embargo or agreement:** unpublished results, grant text before submission, data covered by a data-use agreement.

When in doubt, treat it as sensitive and ask the owner.

### The repository

- **Sensitive material never goes in git,** in any repository, private or public. Everyone with access reads the whole repository, and its history keeps every version of every file.
- **Keep it where it belongs** (an institutional drive, a secure research server, the owner's email) and leave a pointer in the repository: a document name, never a copy.
- **Gitignore from the first commit:** `.env`, key files, and local data folders. Turn on your git host's secret scanning, so a pushed key is caught or blocked (on GitHub: secret scanning and push protection).
- **Logs summarize; they never quote.** "Sponsor replied about the gold tier" goes in the log. The email itself and the sender's address do not. This matters most for hale that sweep email or calendars (section 20).
- **Read the history before changing visibility.** A private repository made public exposes every past version, not just the current files (section 20, "Going public exposes the history").

### The agent session

- **A session is not a vault.** Anything pasted into a chat, read from a file, or pulled in through a connector or integration (email, calendar, file storage) goes to the AI service, whether or not it is ever committed.
- **De-identified data only,** unless the owner has confirmed that both the AI service plan and the institution allow identifiable data: IRB approval, a data-use agreement, and a business associate agreement where HIPAA applies. Record that confirmation, and its limits, in KAUHALE.md.
- **Identifiable data stays on its machine.** A hale that must work on it runs locally (section 12), against data that never leaves that machine, and reports only aggregate or de-identified results.
- **Narrow connections.** Give each hale only the connectors, integrations, and tool permissions it needs, and give each sweep a narrow scope: one label, one calendar, one folder.

### Products and people

- **Agents draft; the owner sends** (section 18).
- **Personal data lives outside the repository.** A draft or product that holds contact or personal data lives in the owner's drive, listed in PRODUCTS.md by document name.
- **TEAM.md holds names and roles only.**

### When something leaks

1. **Stop and tell the owner.** Never fix it quietly.
2. **Rotate any exposed credential at once.** Removing it from git does not make it safe again.
3. **Remove it from the repository,** and from the history if it was ever pushed: rewrite the history, force-push, and ask your git host to purge cached views and unreferenced commits (on GitHub, through GitHub Support). This is the one exception to "never rewrite `main`" (section 16).
4. **Check every other copy:** the live site and its cache (section 20), forks, and clones.
5. **Notify whoever the institution requires** (privacy office, IRB, data owner) and record the incident in the decision log.

### Who checks

For a project with PHI, human-subject data, or other regulated data, add a compliance advisor (section 7). Its specifications turn these rules into the project's own, and its review is part of the review gate.

## 18. Human counterparts and access

- **TEAM.md** names the human behind each role and how they connect.
- **Agents never contact people.** They draft; the owner sends.
- **Tracking:** `[human: Name]` tags on tasks, a `Human:` line on directives, a "Waiting on people" list in STATE.md, and the Haku flags anything older than 7 days at sync.
- **Counterparts with GitHub access** need only a Claude account with the GitHub connector and one opening line naming their role and themselves. The repository carries the rules.
- **Limiting a counterpart to their role** takes GitHub, since instructions alone are not enforcement:
  - Any plan: a ruleset on `main` requiring pull requests, with the owner as the only bypass; a role map of GitHub usernames; a GitHub Action that fails a pull request touching folders outside the author's role; CODEOWNERS for the Haku folder.
  - Team or Enterprise plan: push rulesets that block changes to protected paths unless the pusher is on the bypass list.

## 19. Long-run maintenance

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

**Long-lived chats need a restart trigger.** Rotating chats is one remedy; the other is the daily-restart rule in section 12, which keeps an open chat from working on a stale clone.

## 20. Lessons learned

- **Read before restructuring.** Look at the existing repositories, timelines, and agents before designing roles. One conference repository already had team labels and a planner agent whose duties split cleanly into the new roles.
- **Deliverables as fragments.** When the product must be assembled (LaTeX attachments, a website, a book's chapters), each role writes plain fragments in its own folder and one role owns the build that pulls them in. Ownership stays clean and the build stays in one place.
- **Specialists appear as you go.** A grant team added a Statistician once power calculations and demographics outgrew the Physicist. Adding a role means a role file, a folder, a row in the ownership and access tables, and a decision-log entry.
- **Standing rules go in role files; work goes in directives.** A format for paper notes is a rule. Reading ten papers is a directive.
- **Local-only resources need a plan.** A local database or gitignored PDFs are reachable only from VS Code on the machine that has them. Say so in the role file. A committed rebuild script (section 16) lets a second machine recreate a database instead of copying it.
- **Keep the kauhale out of anything that publishes (a conference, 2026-10-05).** The conference team first lived inside the website repository in a `staff/` folder excluded from the build. It worked, but one wrong exclude rule or one file in the wrong folder would have published planning files, drafts, and sponsor details, and exclusion rules fail silently. The team moved to its own staff repository; the Webmaster's kuleana reaches into the site repository, and everything else stays private.
- **Separate making from judging.** In an imaging pipeline, builders own stages and advisors (Physicist, Statistician, Programmer) own specifications and reviews. The builder that wrote a calibration change is the wrong one to judge its physics.
- **Code projects map hale to the pipeline.** When a codebase already has stages, give each builder a contiguous run of stages and every file exactly one owner. Check ownership with a script: every file should have one owner and none should have two.
- **Respect existing conventions.** One codebase already had a stage-grouped TODO.md with stable IDs and `Refs TODO:` commits. The kauhale kept them: directives cite TODO IDs, and each hale closes items in its own stages.
- **Agents report state; the Haku owns the timeline.** Staff hale never edit the project timeline. They report finished items, and the Haku checks them off.
- **Open chats never restart (a conference, 2026-10-04).** Keeping one app chat per hale open for days meant the start routine (pull, Gmail and calendar sweep, Drive check) ran once and never again. The general fix was a daily-restart rule in the base rules. The Claude-specific fix was moving the file-centred hale to Claude Code in VS Code with one slash-command skill per hale (`/haku`, `/secretary`, `/webmaster`), so each new conversation is a fresh session; other tools need their own equivalent.
- **Gitignored means one machine.** Files in a gitignored folder (`legacy/`) exist only in the clone where they were put. A cloud chat never sees a file added to the local clone; run that hale in VS Code on that machine, or attach the file to the chat.
- **Recurring outside checks belong in the role file.** The Haku checks the shared Drive at the start of every session, and the Secretary sweeps Gmail and the calendar, each against a saved baseline (a snapshot file, a "Last swept" line), so every session reports only what changed.
- **External humans work through drafts.** A human companion for a hale (a task force member) gets no repository access; the hale drafts email in its folder and the owner sends it.
- **The owner needs a front door to the products (a conference, 2026-10-06).** After a few days of work, the conference owner could not find what the hale had made or who owned it: a Gantt chart built the night before was mentioned only in a line of the Webmaster's STATE.md, and the sponsor pipeline sat in a notes folder among drafts and how-tos. STATE.md is the hale's memory and OUTBOX.md carries requests; neither is written for the owner to read. The fix was a PRODUCTS.md in every hale, updated at checkpoint, and one compiled catalog in the Haku's folder with owner, link, as-of date, and status for each product.
- **One home per hale (a research program, 2026-10-06).** One hale was given units in its private product repository while keeping its house in the control repository, with a launcher in each. Two sessions of that hale, one started from each repository, adopted the same three directives in parallel, and one overwrote the other's files. The fix was the one-home rule in section 8: a hale writes in exactly one repository and reads the rest, and when it leads units in a product repository its house moves there.
- **Hale must not start hale.** The guide's hybrid let the Haku dispatch roles as subagents, and agents generalized it: the Haku and staff hale began starting other hale, sometimes in the background, while the owner already had those hale open in their own sessions. Two occupants in one house adopt the same directives and overwrite each other's STATE.md, the same collision as "One home per hale" below. The fix was one rule: only the owner opens a hale. Helpers that load no role file and write nothing stay allowed, and the hybrid survives only as owner-requested, foreground dispatch of a hale with no open session (section 3).
- **One layout everywhere (a research lab, 2026-10-09).** The lab's control repository was first built with its hale at the root, as the guide then specified for control repositories, while the conference kauhale kept its hale in `staff/`. Two shapes meant two sets of paths in role files, launchers, and opening lines. The owner set one standard: every kauhale keeps all its hale under `staff/`. The move was one `git mv` and a path rewrite, cheap only because no session had written there yet.
- **Exclude lists fail open (a research lab, 2026-10-08).** A website's to-do list and issue log were kept off the site by its exclude list, but its `docs/` folder was missing from that list, so internal planning notes and audit worksheets were publicly served. Nobody noticed, because everyone read the configuration instead of requesting the URLs. The fix was to move the planning files into the Webmaster's hale and exclude `docs/`; the lesson is to test the live site by URL whenever working files sit in a product repository.
- **Going public exposes the history (2026-10-24).** When this guide's own repository was made public, its current text was clean, but earlier versions named the projects behind the lessons and described one lab's leak in detail, and every version was readable through old commits and tags. Fixing it meant rewriting the history, force-pushing, and asking GitHub to purge its cached copies; clones made before the fix kept the old text. Read the history, not just the current files, before changing a repository's visibility (section 17).
- **Deleting a published file is not instant (a research lab, 2026-10-09).** After the fix merged, the site's origin returned 404, but the hosting provider's edge cache kept serving copies for days. The site's domain was managed by another organization, so the owner had no way to purge that cache. The copies could only age out. Keep working files out of product repositories from the start, and know the cache lifetime and who can purge it before anything sensitive is published.

## 21. New project checklist

- [ ] Trial only: start tagged, additive changes only, review date in KAUHALE.md
- [ ] Existing repository: adoption checklist (section 9) followed
- [ ] Shape decided: seed or household, standalone or control repository, roles, product format, humans
- [ ] Repository created; Claude GitHub App has access
- [ ] Folders and templates scaffolded
- [ ] Builder and advisor hale chosen; review gate written into KAUHALE.md (if any advisors)
- [ ] Role files and the shared base rules written
- [ ] Every owned file has exactly one owner (scripted check for code projects)
- [ ] KAUHALE.md, timeline, TEAM.md, PRODUCTS.md, CLAUDE.md, README written
- [ ] All hale under `staff/`, with the Haku at `staff/lead/`
- [ ] Nothing of the kauhale in any repository that publishes; pointer CLAUDE.md in each product repository (control repository only); product repositories' planning files moved to their hale
- [ ] Data rules in KAUHALE.md: sensitive material listed, where each kind lives, what the AI service may see; `.env` and key files gitignored; the git host's secret scanning on (section 17)
- [ ] Database (if any): SQLite, file gitignored, schema and rebuild script committed, one owning hale, backup plan for anything that cannot be rebuilt
- [ ] Live product checked by URL: working files and the pointer CLAUDE.md return 404
- [ ] Committed and pushed (or merged after review)
- [ ] Claude project created with instructions, memory separate, no uploads
- [ ] Connectors on; old chats archived
- [ ] Haku chat opened; first sync run
- [ ] First staff hale chats opened with role lines
- [ ] Rule in CLAUDE.md and the base rules: only the owner opens a hale (optionally enforced by a hook)
- [ ] First checkpoint confirmed on GitHub

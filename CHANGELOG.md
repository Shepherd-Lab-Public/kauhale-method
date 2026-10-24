# Changelog

Newest first. Each heading is a git tag.

## 2026-10-24

- New section 17, Safeguards: what counts as sensitive; rules for the repository, agent sessions, and products; what to do when something leaks; a compliance advisor for regulated data. Setup (Node 9) asks about sensitive data and records data rules in KAUHALE.md; the base rules, the CLAUDE.md template, and the git conventions point to section 17. Force-pushing is allowed only to remove leaked material. Sections 17-20 renumbered 18-21.
- Only the owner opens a hale: no agent starts another hale, or a second copy of itself, as a subagent or background session. Helpers that load no role file and write nothing are still allowed. Added to section 12, section 13, the CLAUDE.md template, the base rules, units, and the checklist, with an optional Claude Code hook to enforce it.
- The hybrid (section 3) narrowed: the Haku dispatches a hale subagent only when the owner asks, in the foreground, for a hale with no open session.
- Using other models (section 13): data handling differs by AI service, so check each against the data rules.
- Git conventions: prefer SQLite when a project needs a database; gitignore the database file and commit the schema and a rebuild script. One hale owns the database and is its only writer; data that cannot be rebuilt gets a backup outside git; the live file stays off synced folders and network drives.
- Lessons learned: hale must not start hale; going public exposes the history; local databases can be recreated from the rebuild script.
- Names of specific projects, repositories, and hale removed from the guide; lessons keep the kind of project and the date.
- Consistency: "staff hale" replaces "employee"; every hale, the Haku included, follows `_hale-base.md`; the Haku's folder has its own STATE.md; one opening-line form; agents never send email (drafts only), matching section 18; launchers shown in the standalone layout; PRODUCTS.md added to the growth and build steps; a wrong cross-reference to the style rules fixed.
- New-project checklist items for data rules, the database, and the owner-opens-a-hale rule.
- Licensed under CC BY 4.0 (was all rights reserved); LICENSE file added. CONTRIBUTING.md added: how to propose changes by pull request; maintainers decide what merges.

## 2026-10-09

- One layout everywhere: every kauhale keeps all its hale under `staff/`, with the Haku at `staff/lead/`, in standalone and control repositories alike.
- Shared base rules are named `_hale-base.md` everywhere (was `_employee-base.md`).
- Adopting a repository: planning files (to-do lists, issue logs, lab books) move out of product repositories to their owning hale; a new final step checks the live product by URL for working files.
- Lessons learned from a lab website: exclude lists fail open; deleting a published file is not instant behind a CDN cache.
- New-project checklist items for the `staff/` layout and the live-URL check.

## 2026-10-06

- Credit: the method is by John Shepherd and Sven Prevrhal.
- A kauhale never shares a repository with anything that publishes. New control repository model: the kauhale lives in its own private repository, and each product repository carries only a pointer CLAUDE.md. Replaces the "embedded" layout that excluded `staff/` from a website build.
- MASTER.md renamed KAUHALE.md.
- PRODUCTS.md added: each hale lists the work products the owner opens; the Haku compiles them at sync.
- Larger organizations: one `<org>-admin` control repository; a hale may lead units, two levels at most.

## 2026-10-03

- Restructured into Part A, a guided setup for Claude with a decision tree, and Part B, the reference.
- New sections: examples to start from, the seed kauhale, adopting an existing repository, and trying the method without committing.

## 2026-10-02

- First version under git, imported from `kauhale-method-generic.md`.

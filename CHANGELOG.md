# Changelog

Newest first. Each heading is a git tag.

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

# Contributing to the Kauhale Method

Thank you for helping improve the guide. The most useful contributions come from running a kauhale on a real project: a rule that failed, a step that confused someone, a pattern that worked and is not written down yet.

## What helps most

- **Lessons from real use.** What happened, what went wrong, and the fix. Section 19 shows the form: a short title, the project and date if you can share them, and the general rule it taught.
- **Corrections.** Wrong cross-references, steps that contradict each other, outdated interface details.
- **Clarity.** A passage that a newcomer, or an agent, misread.

For a large change (a new section, a change to a core rule such as ownership or the session rules), open an issue first so we can agree on the direction before you write it.

## How to propose a change

1. Fork this repository and create a branch for your change.
2. Edit `kauhale-method.md`. Keep each pull request to one topic.
3. Add a line under **Unreleased** in `CHANGELOG.md` saying what changed and why.
4. Open a pull request. Describe the problem, the change, and, for a lesson, where you saw it.

Leave the version line at the top of the guide and the git tags alone; they change only when a version is released.

## Style

- Plain English, short sentences, written for someone with no technical background. Explain a term the first time it appears.
- File and folder names stay in plain English (STATE.md, DIRECTIVES.md); KAUHALE.md is the one exception.
- Use the Hawaiian words only in the meanings given in Part B, section 1, spelled with their ʻokina and kahakō.
- Keep personal names, email addresses, and private project details out of examples unless the people involved have agreed.

## Review and merging

The maintainers review every pull request and decide what is merged into `main`. A change may be accepted, revised with you, or declined; declined changes are still welcome as issues or discussion.

## License

The guide is licensed under [CC BY 4.0](LICENSE). By opening a pull request, you agree that your contribution is licensed under the same terms.

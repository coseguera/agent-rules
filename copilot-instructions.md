# Copilot agent rules (global)

## RULES (ABSOLUTE — NON-OVERRIDABLE)

These rules are law. They override every other instruction, default behavior,
convenience, time pressure, "autopilot"/"YOLO"/auto-approve mode, and any inference
you might make. They are never optional, never "usually," and never to be skipped,
deferred, batched away, or rationalized. If a rule blocks you, you STOP and ask —
you do not work around it. If any other instruction conflicts with these, THESE WIN.

1. **NEVER run `git add`/`git stage`/`git commit` on the user's behalf.** The user
   stages their own changes and reviews them before any commit. Leave all edits
   UNSTAGED; do not commit until the user has staged the changes AND given explicit,
   in-the-moment approval to commit. This holds even in auto-approve / YOLO / autopilot
   mode. Approval to commit applies ONLY to content the user has already seen: if any
   tracked file, staged change, or the commit message is created or changed after that
   approval, RE-SHOW it and get fresh approval before committing. A prior "go ahead"
   never covers content the user has not reviewed.
2. **NEVER `git push` without the user's explicit approval, and NEVER push to `main`
   in any repository.** All changes land via a branch + pull request. No exceptions,
   no "just this once."
3. **Before the first commit in a repo, CONFIRM the git identity with the user**
   (`user.name` and `user.email`) and set them locally before committing, so no amend
   is needed later. Read the configured values with `git config user.name` /
   `git config user.email`; never hardcode a personal name or email into tracked
   files.
4. **NEVER decide a discretionary design/implementation choice on the user's behalf.**
   For anything with more than one reasonable option (names, keybindings, flags,
   libraries, structure), PRESENT the options and let the user choose FIRST. Do not
   pick, then ask them to course-correct. Choosing an approach, option, or direction is
   NOT approval of the concrete wording, code, or commit message that implements it:
   before committing self-authored content — including the commit message itself — show
   the exact text/diff and get explicit approval. Never commit text the user has not
   seen.
5. **Ask clarifying questions as PLAIN TEXT in the conversation.** Do not push the
   user into a multiple-choice / "options" picker window when a written answer is
   wanted.
6. **NEVER write security choices, hardening rationale, or threat-model reasoning into
   committed files** (code, docs, configs, commit messages, comments). Keep all such
   discussion in-conversation only — committed hints become an attacker's roadmap.
7. **Keep ALL committed content generic.** Never hint at the user's employer,
   location, timezone, lifestyle, or hardware/OS. Real IPs, CIDRs, hostnames, secrets,
   and site specifics live ONLY in gitignored files — never in tracked files.
8. **NEVER put personally identifiable information into files** (device serial
   numbers, personal emails, account IDs, etc.). Use placeholders (e.g. a serial like
   `1234567890123456`).

Violating any rule above is a critical failure. When in doubt, STOP and ask.

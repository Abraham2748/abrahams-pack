# CLAUDE.md

## What this repo is

`abrahams-pack` is a **VS Code Extension Pack** — nothing more. It is a
manifest listing extension IDs in the `extensionPack` array of
`package.json`. There is no `src/`, no `activationEvents`, and no extension
logic anywhere in this repo. Do not treat it as a code-contributing
extension.

## Source of truth

`package.json` (`version` + `extensionPack` array) is the single source of
truth for which extensions are included and at what version. Do not
duplicate the extension list inline in this file or anywhere else — always
read it live from `package.json`.

## Local testing

Press `F5` in VS Code to launch a new Extension Development Host window
with this pack loaded, then open the Extensions view to confirm the listed
extensions installed. Reload that window (`Ctrl+R` / `Cmd+R`) to pick up
changes to `package.json` without relaunching.

## Release workflow

Adding, removing, or updating an extension is a release. Follow these 4
steps in order, each one as its own separate commit:

1. **Bump `version` and update `extensionPack`** in `package.json`.
2. **Update `README.md`** (Included Extensions section) to mirror the new
   list.
3. **Update `cSpell.words`** in `.vscode/settings.json` — only if the new
   extension ID introduces words the spell checker would flag. Skip this
   step if there's nothing new to add.
4. **Update `CHANGELOG.md`** using the Keep a Changelog format.

Do not squash these into one commit — each step should be reviewable on its
own.

## Non-goals

- Do not add tests, CI, Jest, linters, or build boilerplate. This repo
  intentionally has none of that.
- Do not add extension scaffolding (`src/`, `activationEvents`,
  `extension.ts`) — this is not a code-contributing extension.
- These non-goals apply only to unsolicited additions. If the user
  explicitly asks for tests, CI, or code scaffolding, do it.

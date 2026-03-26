# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`@apiax/prettier-config` is a shareable Prettier configuration package published to npm. It exports a single config object from `src/index.js` that consuming projects reference via `"prettier": "@apiax/prettier-config"` in their `package.json`.

## Commands

- **Install dependencies:** `npm install`
- **Format check:** `npx prettier --check .`
- **Format fix:** `npx prettier --write .`

There is no build step or test suite. The pre-commit hook runs `npx lint-staged`, which formats staged files with Prettier.

## Architecture

- `src/index.js` — The sole export. Defines the Prettier config with overridable defaults (to prevent EditorConfig from overriding them) and language-specific overrides (e.g., Java).
- `.prettierrc.json` — Used to format *this repo's own files* (not exported to consumers).
- `.prettierignore` — Excludes `package.json` and `package-lock.json` from formatting.
- Prettier plugins (`prettier-plugin-java`, `prettier-plugin-organize-imports`) are declared as optional `peerDependencies` — consumers install only what they need.

## Key Details

- The `plugins` array in `src/index.js` is intentionally empty — consumers are expected to add plugins via extension (spread + append).
- The `printWidth` in `src/index.js` (120) differs from what the README documents (100). The code is authoritative.
- Java override sets `printWidth: 140` and uses the `java` parser.

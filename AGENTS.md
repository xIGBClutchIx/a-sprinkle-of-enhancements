# Repository Guidelines

## Project Structure & Module Organization
- `pack.toml` and `index.toml` define the Packwiz-managed modpack metadata and file hashes.
- `mods/` contains Packwiz `.pw.toml` mod descriptors, sourced from CurseForge (a few CurseForge doesn't carry stay on Modrinth); `mods-disabled/` holds optional mods not shipped by default.
- `config/` stores per-mod configuration files (JSON, TOML, properties, YAML).
- `resourcepacks/` and `shaderpacks/` contain pack descriptors and assets.
- Releases are CurseForge modpack `.zip` files exported for specific Minecraft versions.

## Build, Test, and Development Commands
- This repository is managed with Packwiz; there are no other build or test scripts.
- Run Packwiz from the repo root where `pack.toml` lives. Example workflows:
  - `packwiz list` (list all mods in the pack)
  - `packwiz refresh` (recompute `index.toml` hashes after file changes)
  - `packwiz update` (update all external mods/files that support updates)
  - `packwiz migrate minecraft` / `packwiz migrate loader` (update Minecraft or Fabric loader versions)
  - `packwiz curseforge add <url|slug>` (add a mod from CurseForge; prefer CurseForge over Modrinth)
  - `packwiz curseforge export` (create the CurseForge `.zip` release; Modrinth-only files are bundled into `overrides/`)

## Coding Style & Naming Conventions
- Preserve existing file formats and ordering; many files are tool-generated.
- Keep `.toml` and `.json` files valid and minimally formatted (avoid manual reformatting).
- New mods should follow the existing naming pattern: `mods/<mod-name>.pw.toml`.

## Testing Guidelines
- There is no automated test suite.
- Validate changes by launching Minecraft with Fabric using the versions in `pack.toml`.
- Sanity-check that key configs still load and the game reaches the main menu.

## Commit & Pull Request Guidelines
- Commit messages follow Conventional Commits with scopes, e.g. `feat(release): ...` or `fix(pack): ...`.
- PRs should summarize mod/config changes, list the targeted Minecraft/Fabric versions, and include release notes when publishing a CurseForge `.zip` release.

## Configuration & Safety Tips
- Treat `config/` updates as user-facing defaults; avoid introducing server-breaking or gameplay-altering mods.
- Keep the modpack vanilla-friendly as described in `README.md`.

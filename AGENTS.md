# Repository Guidelines

## Project Structure & Module Organization
- `pack.toml` and `index.toml` define the Packwiz-managed modpack metadata and file hashes.
- `mods/` contains Packwiz `.pw.toml` mod descriptors; `mods-disabled/` holds optional mods not shipped by default.
- `config/` stores per-mod configuration files (JSON, TOML, properties, YAML).
- `resourcepacks/` and `shaderpacks/` contain pack descriptors and assets.
- `*.mrpack` files are exported release artifacts for specific Minecraft versions.

## Build, Test, and Development Commands
- This repository is managed with Packwiz; there are no other build or test scripts.
- Run Packwiz from the repo root where `pack.toml` lives. Example workflows:
  - `packwiz list` (list all mods in the pack)
  - `packwiz refresh` (recompute `index.toml` hashes after file changes)
  - `packwiz update` (update all external mods/files that support updates)
  - `packwiz migrate minecraft` / `packwiz migrate loader` (update Minecraft or Fabric loader versions)
  - `packwiz modrinth export` or `packwiz curseforge export` (create `.mrpack` releases)

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
- PRs should summarize mod/config changes, list the targeted Minecraft/Fabric versions, and include release notes when updating `*.mrpack` files.

## Configuration & Safety Tips
- Treat `config/` updates as user-facing defaults; avoid introducing server-breaking or gameplay-altering mods.
- Keep the modpack vanilla-friendly as described in `README.md`.

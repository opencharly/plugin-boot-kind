# AGENTS.md — plugin-boot-kind

Standalone plugin repo for the bootloader and snapshot kinds. The repo is currently
a **scaffold**: it carries only `README.md` and
`.github/workflows/tag-on-merge.yml` — **no `charly.yml`, no `candy/` directory, and
no Go module yet**. There is therefore no `plugin:` block, no provider, no `skill:`
entity, and no owning skill projected into the marketplace corpus. The gap is
recorded against `opencharly/opencharly#291` (the batch that authors missing
`skill:` entities).

The repo is listed in charly's org-wide plugin corpus
(`charly/charly/plugin_corpus.txt`), which indexes each plugin repo's manifest; with
no manifest here it contributes no provider word to that index yet.

Canonical files:

- `README.md` — user overview only; never agent guidance.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.

## Load these skills first (R0)

- `/charly-internals:plugin` — the plugin authoring reference: the `plugin:` block,
  the unified Provider model, the external (out-of-process) shape, the per-plugin
  CUE-schema contract, and placement. Load before authoring the candy.
- `/charly-vm:vm` — the VM schema surface whose `bootloader:` recipes and snapshot
  handling the kinds serve.
- `/charly-internals:git-workflow` — before any git/PR action.

## Build / validate / test

- There is nothing to build or validate yet: with no `charly.yml`, `charly box
  validate` has no manifest to parse. The org-wide candy gate
  (`opencharly/.github/.github/workflows/candy-validate.yml`) **skips cleanly** on a
  repo with no `charly.yml`.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- When the candy lands, the plugin gates apply: `go build ./...`, `go vet ./...`,
  `go test ./...`, `charly box validate`, and a disposable R10 bed composing the
  plugin. Name them here once the module exists.

## Modify this repo

- Author the candy at `candy/plugin-boot-kind/charly.yml` with a `plugin:` block,
  its self-contained `schema/*.cue`, the generated `params/`, and `cmd/serve/` in
  the same change — a plugin candy without a schema or provider is incomplete.
- The candy is **external (out-of-tree) by default**: it is connected by word at
  runtime, so the word→ref fact lives in this manifest and the repo's entry in
  charly's `plugin_corpus.txt`, never in core.
- There is no `skill:` entity to keep in sync yet; if one is added (per #291), it
  must be edited together with the candy entity in the same change.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge on
  PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the PR
  body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.

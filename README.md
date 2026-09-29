# plugin-boot-kind

The charly plugin for the **bootloader and snapshot kinds** — not yet populated.

## Status

This repo is a **scaffold**: it carries this `README.md` and the org-wide
`.github/workflows/tag-on-merge.yml` dispatcher, and **no `charly.yml`, no
`candy/plugin-boot-kind/`, and no Go module yet**. There is no `plugin:` block, no
provider, and no `skill:` entity.

The repo is nevertheless listed in charly's org-wide plugin corpus
(`charly/charly/plugin_corpus.txt` in `opencharly/charly`), which indexes every
plugin repo's manifest so an out-of-tree provider is discoverable by word. With no
manifest here it currently contributes **no** provider word to that index.

## Intended scope

A plugin candy (`candy/plugin-boot-kind/charly.yml` with a `plugin:` block)
declaring the bootloader and snapshot **kinds** — the concrete-kind providers that
belong outside charly core per the kernel/plugin boundary law. The kinds themselves
are charly's `bootloader:` (limine/grub install recipes) and snapshot handling, which
today live in the VM/distro schema surfaces.

## Layout

- `README.md` — this user overview.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.

## Related

- Owning skill: none yet — `/charly-internals:plugin` is the authoring reference for
  the first candy. The missing `skill:` entity is recorded against
  [opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291).
- `/charly-internals:plugin` — the plugin authoring reference (the `plugin:` block,
  the unified Provider model, the per-plugin CUE-schema contract, placement).
- `/charly-vm:vm` — the VM schema surface the bootloader/snapshot kinds serve.
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella.

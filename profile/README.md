<img src="logo.svg" width="96" alt="Templetry — five brass warp threads crossed by a linen weft" />

# Templetry

**Project scaffolding for every platform — delivered to any forge.**

Templetry generates ready-to-work repositories from a library of multi-platform templates, and creates them on any git host — GitHub, GitLab, Gitea/Forgejo, or your own server — in seconds.

> *Templetry* comes from **templet**, the original spelling of "template", which also named a real weaving tool: the piece that keeps the cloth's shape on the loom.

## What makes it different

- **Templates compile.** Every template is a real project with its own CI — never a skeleton full of broken placeholders.
- **The engine doesn't know what a framework is.** All framework knowledge lives in each template's `template.yml` manifest; adding a platform means writing a template, not engine code.
- **Any forge.** `git push` is universal — Templetry creates your repo wherever you work, with a bring-your-own-remote fallback that covers every git host on the planet.

## Status

🚀 **Shipped (August 2026).** Engine [v0.2.2](https://github.com/Templetry/engine/releases/latest) with binary releases for every platform · **Templetry Desktop** [v0.2.0](https://github.com/Templetry/desktop/releases/latest) · a CI-verified template catalog. The full picture lives in the wiki's [state of the art](https://github.com/Templetry/wiki/blob/main/state-of-the-art.md).

| Repo | What it is |
|---|---|
| [engine](https://github.com/Templetry/engine) | The core: a pure Go library + CLI that renders repositories from compilable templates |
| [catalog](https://github.com/Templetry/catalog) | The default template registry (`registry.json`) |
| [kmp](https://github.com/Templetry/kmp) | Parent: Kotlin Multiplatform — forms `modular-features`, `single-module`, `modular-ui` |
| [android](https://github.com/Templetry/android) | Parent: Android native — form `modular-features` (+ `single-module` planned) |
| [meta](https://github.com/Templetry/meta) | Parent: the template that creates Templetry templates |
| [desktop](https://github.com/Templetry/desktop) | Native desktop app: sign in with GitHub, browse the catalog, create, manage and update repos |
| [wiki](https://github.com/Templetry/wiki) | Studies, ADRs, the normative `template.yml` spec and the [brand guidelines](https://github.com/Templetry/wiki/blob/main/brand/guidelines.md) |

## Roadmap

Shipped: engine + CLI → CI-verified templates (parents/forms/features) → desktop app with template updates (three-way merge) and auto-update. Next: `android/single-module`, engine `verify` in Docker, code signing, macOS/Linux desktop builds.

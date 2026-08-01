# Templetry

**Project scaffolding for every platform — delivered to any forge.**

Templetry generates ready-to-work repositories from a library of multi-platform templates, and creates them on any git host — GitHub, GitLab, Gitea/Forgejo, or your own server — in seconds.

> *Templetry* comes from **templet**, the original spelling of "template", which also named a real weaving tool: the piece that keeps the cloth's shape on the loom.

## What makes it different

- **Templates compile.** Every template is a real project with its own CI — never a skeleton full of broken placeholders.
- **The engine doesn't know what a framework is.** All framework knowledge lives in each template's `template.yml` manifest; adding a platform means writing a template, not engine code.
- **Any forge.** `git push` is universal — Templetry creates your repo wherever you work, with a bring-your-own-remote fallback that covers every git host on the planet.

## Status

🏗️ **Phase 0 — design & study.** The project is being designed in the open before any code lands.

| Repo | What it is |
|---|---|
| [wiki](https://github.com/Templetry/wiki) | Preliminary study, Architecture Decision Records, and the evolving `template.yml` spec |

## Roadmap

Engine (library + CLI) → container-based verification + first templates → web app (OAuth, catalog, one-click repo creation) → multi-forge adapters & template updates.

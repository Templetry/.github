<img src="logo.svg" width="96" alt="Templetry — five brass warp threads crossed by a linen weft" />

# Templetry

**Project scaffolding for every platform — delivered to any forge, and kept alive afterwards.**

Templetry generates ready-to-work repositories from a library of multi-platform templates, creates them on any git host — GitHub, GitLab, Gitea/Forgejo, or your own server — and lets those projects keep pulling template improvements and adopting new pieces long after they were created.

> *Templetry* comes from **templet**, the original spelling of "template", which also named a real weaving tool: the piece that keeps the cloth's shape on the loom.

## What makes it different

- **Templates compile.** Every template is a real project whose CI renders *and builds* its output — never a skeleton full of broken placeholders. Defects surface in the template's CI, not in your project.
- **The engine doesn't know what a framework is.** All framework knowledge lives in each template's `template.yml`. Eleven ecosystems in, the engine has never needed a framework-specific line.
- **Projects stay alive.** Generated repositories record what made them, so they can pull template updates through a real three-way merge — and adopt **lazy pieces** (RBAC, audit trail, API keys, a whole CRUD entity) whenever you need them.
- **Any forge.** Accounts for GitHub, GitLab and Gitea/Forgejo, plus a bring-your-own-remote fallback that covers every git host on the planet.

## Status

🚀 **v1.0.0 and beyond (August 2026).** Engine [v1.10.0](https://github.com/Templetry/engine/releases/latest) (library + CLI + MCP server) · **Templetry Desktop** [v1.7.1](https://github.com/Templetry/desktop/releases/latest) for Windows, Linux and macOS · a CI-verified catalog of **22 forms and 14 pieces across eleven ecosystems**. The public API is stable under a written [compatibility policy](https://github.com/Templetry/wiki/blob/main/spec/compatibility.md); the full picture lives in the wiki's [state of the art](https://github.com/Templetry/wiki/blob/main/state-of-the-art.md).

## Getting started

```sh
scoop bucket add templetry https://github.com/Templetry/scoop-bucket && scoop install templetry
# or grab a binary from the engine releases

templetry list
templetry init python/fastapi-users --out ./my-api --set "project_name=My Api"
templetry add rbac ./my-api          # adopt a piece later
templetry update ./my-api            # pull template improvements
```

Prefer a UI? [Templetry Desktop](https://github.com/Templetry/desktop/releases/latest) does all of it — plus browsing your repositories across forges.

Full documentation: the wiki's [**usage guides**](https://github.com/Templetry/wiki/blob/main/guide/).

## The repos

| Repo | What it is |
|---|---|
| [engine](https://github.com/Templetry/engine) | The core: pure Go library + `templetry` CLI + `templetry-mcp` server |
| [desktop](https://github.com/Templetry/desktop) | Native app (Wails): create, browse, update and adopt pieces |
| [catalog](https://github.com/Templetry/catalog) | The default template registry (`registry.json`) |
| [web](https://github.com/Templetry/web) | Parent: React, Vue, Next.js and Svelte SPAs (+ pieces) |
| [python](https://github.com/Templetry/python) | Parent: FastAPI services, a user-management API and Typer CLIs (+ industrial pieces) |
| [go](https://github.com/Templetry/go) | Parent: CLI, HTTP service and a REST API over SQLite (+ pieces) |
| [rust](https://github.com/Templetry/rust) | Parent: clap CLI and axum service |
| [node](https://github.com/Templetry/node) · [jvm](https://github.com/Templetry/jvm) · [dotnet](https://github.com/Templetry/dotnet) | Parents: Express, Spring Boot, and .NET minimal APIs and Razor Pages |
| [kmp](https://github.com/Templetry/kmp) · [android](https://github.com/Templetry/android) | Parents: Kotlin Multiplatform and Android native |
| [meta](https://github.com/Templetry/meta) | Parent: the template that creates Templetry templates |
| [pieces](https://github.com/Templetry/pieces) | Common pieces adoptable by any compatible project |
| [scoop-bucket](https://github.com/Templetry/scoop-bucket) | Windows install: `scoop install templetry` |
| [renovate-config](https://github.com/Templetry/renovate-config) | Shared Renovate preset — one dependency policy for every repo |
| [wiki](https://github.com/Templetry/wiki) | [Usage guides](https://github.com/Templetry/wiki/blob/main/guide/), studies, ADRs, normative specs and the [brand guidelines](https://github.com/Templetry/wiki/blob/main/brand/guidelines.md) |

## Roadmap

Next: more industrial pieces (SCIM provisioning, OIDC login, multi-tenancy, outbox), piece removal and `requires` between pieces in the engine, and a Homebrew tap.

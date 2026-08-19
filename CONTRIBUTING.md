# Contributing to Templetry

Thanks for looking. This file applies to every repository in the organization.

The most valuable contribution is **a new form for an ecosystem you know well** — and Templetry generates the starting point for you, so you never have to learn a template format by reading about it.

## The model, in one minute

Four words carry the whole design. Learn these and the rest follows.

| Term | What it is |
|---|---|
| **Parent** | One repository per ecosystem — `go`, `python`, `web`. |
| **Form** | A structural variant inside a parent, in its own subdirectory, with its own `template.yml`. Forms are *chosen*, not combined. |
| **Feature** | A freely combinable option inside a form, resolved when the project is generated. |
| **Piece** | A unit adopted *after* creation, with its own variables and its own update cycle. |

The rule that decides which one you want:

> **additive → feature · structural → form · independent lifecycle → piece**

Templates carry no templating language. A template file is a real source file: identities like `TemplateApp` get renamed, and optional parts are marked with directives inside ordinary comments (`// tpl:if ios`). That is what lets a template compile — which is the bar below.

## Adding a form

**1 · Generate it.**

```sh
templetry init meta/template --out ./my-form --set "template_name=My Form"
```

The meta-template produces a form that already declares its taxonomy and its environment profiles, so you start from the current shape rather than from an outdated example.

**2 · Make it a real project that builds.** This is the bar, and it is not negotiable — see [ADR-0003](https://github.com/Templetry/wiki/blob/main/adr/0003-templates-compile.md). Your form is a working project, not a skeleton with placeholders. Its CI renders it and **builds the output with the real toolchain**, in every feature combination you declare.

If it cannot build in a Linux container, say so in the manifest instead of pretending — `ios/swiftui-app` declares no `verify` block and explains why, and its parent's CI carries the guarantee on a macOS runner.

**3 · Declare its taxonomy.** Three axes, per [ADR-0017](https://github.com/Templetry/wiki/blob/main/adr/0017-template-taxonomy.md):

```yaml
kinds:      [backend, database]   # closed vocabulary — the filter axis
languages:  [python]              # open, kebab-case
frameworks: [fastapi, sqlmodel]   # open, kebab-case
```

`kinds` is closed on purpose: a filter only works if two templates meaning the same thing use the same word.

**4 · Ship the three environment profiles.** `development`, `staging`, `production`, using **your ecosystem's own mechanism** — Spring profiles, `appsettings.{Environment}.json`, Vite modes, Android product flavors. Never a Templetry-shaped one. See [ADR-0018](https://github.com/Templetry/wiki/blob/main/adr/0018-environment-profiles.md), which also defines when a profile counts as done: the three sources differ in something observable, one validated accessor reads the active one, and a test asserts it.

**5 · Open a PR against [catalog](https://github.com/Templetry/catalog).** Its CI fetches every form from the repo and ref it declares and compares the manifest field by field, so a typo fails there rather than in someone's project.

## Adding a piece

A piece may **only add files that do not already exist**, and may touch shared files **only through declared patches**. Wiring that lives in code needs the form to expose a socket.

If the same idea makes sense in more than one ecosystem, it belongs in [pieces](https://github.com/Templetry/pieces) as a common piece with an `applies_to` list ([ADR-0016](https://github.com/Templetry/wiki/blob/main/adr/0016-common-pieces.md)). Each piece there is verified by applying it to a real target project through the registry, pinned to the commit under test.

## Working on the engine

Go, no third-party dependencies in the core. CI runs `gofmt`, `go vet`, `go build ./...` and `go test ./...` on every push, plus CodeQL.

The engine's defining constraint: **it knows nothing about any framework** ([ADR-0002](https://github.com/Templetry/wiki/blob/main/adr/0002-knowledge-lives-in-the-manifest.md)). Twelve ecosystems in, it has never needed a framework-specific line. A change that teaches it about one particular ecosystem is almost certainly a change that belongs in a `template.yml` instead.

## Decisions are written down

Nineteen [ADRs](https://github.com/Templetry/wiki/blob/main/adr/) record why the project is shaped the way it is, including the ones that were revised. A change to the model — a new kind in the vocabulary, a new manifest field, a different update strategy — wants an ADR alongside the code. A bug fix does not.

If you are unsure whether something needs one, open an issue and ask. Being told "just send the patch" costs you nothing.

## Pull requests

- **Green CI is the entry ticket.** Every repository has it now, and template repositories build their own output.
- **Explain the why in the commit body.** The what is in the diff. The reasoning is the part that is expensive to reconstruct later, and this history is full of examples worth imitating.
- **One concern per PR.** A form and an engine change are two PRs.

## Reporting things

- **Bugs and proposals:** the issue templates on each repository.
- **Questions and ideas:** [Discussions](https://github.com/Templetry/engine/discussions).
- **Security:** never an issue — see [SECURITY.md](SECURITY.md).

## Licence

The engine is Apache-2.0; every other repository is MIT. Contributions are accepted under the licence of the repository you are contributing to. You keep your copyright.

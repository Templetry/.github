# Security policy

## Reporting a vulnerability

**Do not open a public issue.** Use GitHub's private vulnerability reporting on the affected repository: **Security → Report a vulnerability**. It goes only to the maintainers and stays private until there is a fix.

If that is unavailable to you, email **sebssgarcia502580@gmail.com** with `[templetry-security]` in the subject.

Expect a first reply within a week. A single maintainer runs this project — that number is what can honestly be promised, not what a template would say.

## Supported versions

The latest release of the engine and of the desktop app. There are no long-term support branches; fixes ship forward.

The [compatibility policy](https://github.com/Templetry/wiki/blob/main/spec/compatibility.md) governs breaking changes: the manifest, directives, answers file, registry v2, CLI surface and exported Go API only break with a major version. A security fix that requires breaking one of those will say so explicitly in its release notes.

## Where the risk actually is

Useful to state plainly, so reports land where they matter:

- **The engine writes files to paths derived from user input** — a template's identity map, a piece's paths, an answers file. Every write resolves its path against the output root and refuses anything escaping it (`render.Contain`), applied by the render, piece and update writers alike. A way around that check is the highest-value report this project can receive.
- **Templates and pieces are fetched from remote repositories** over `github:`, `gitlab:` and `gitea:` schemes. A malicious template can only place files inside the output directory — but it also ships build tooling that runs when *you* build the generated project. Treat a template from an unknown catalog the way you would treat any repository you are about to build.
- **`templetry verify` runs a template's declared command inside Docker.** That command comes from the template's manifest.
- **The desktop app stores forge tokens in the OS keyring**, keyed by `<scheme>@<host>`; the settings file holds only the account list, so an exported settings file carries no credentials.

## What is not a vulnerability

- A generated project depending on a package with a known CVE. Report it as a normal issue — the template should move — but it is not a flaw in Templetry.
- `templetry verify` executing the command a template declares. That is what it is for, and it runs in a container.
- Anything requiring the attacker to already control the machine running the CLI.

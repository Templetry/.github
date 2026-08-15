# `setup-templetry`

Installs the [templetry](https://github.com/Templetry/engine) CLI on a runner.

```yaml
- uses: Templetry/.github/actions/setup-templetry@main
- run: templetry render --template ./my-form --out "$RUNNER_TEMP/out" --set "project_name=Verify App"
```

## Why it exists

Every parent's Verify workflow installs the CLI before rendering. When each one carried its own `curl` line, the ten of them drifted apart: after two engine releases they were all a version behind, one had quietly been tracking `latest` instead of a pin, and `kmp` had its own copy of the OS-detection logic because it also builds on macOS.

[Study X](https://github.com/Templetry/wiki/blob/main/study/where-next-v1.md) asked for "one pinned CLI version, centrally managed". Bumping ten repositories by hand was not that — it drifted again within a day. Now the version lives in [`action.yml`](action.yml) and one edit moves the catalog.

## Inputs

| Input | Default | Meaning |
|---|---|---|
| `version` | the shared version | A release tag. Setting it is how a repository deliberately steps out of line — which should be rare and worth a comment. |

## Outputs

| Output | Meaning |
|---|---|
| `version` | What was actually installed, for logs and assertions. |

## Behaviour worth knowing

- **Linux and macOS**, x64 and arm64, resolved from `RUNNER_OS`/`RUNNER_ARCH`. An unsupported runner is an error naming what it saw, not a mysterious failure later.
- The binary lands in a directory of its own under `RUNNER_TEMP` and that directory goes on `PATH` — no `sudo`, and nothing shadowing commands from a rendered project.
- The download uses `curl -f`, and the action runs `templetry version` before finishing. Both exist because of a real failure: a 404 page once got written to disk, marked executable, and killed a later step with a bare `exit 127`.

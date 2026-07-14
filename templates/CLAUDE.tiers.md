## Worker tiers (sous-chef)

Route each Codex implementation ticket by the shape already used to decide whether
to delegate:

| Tier | Effort | Task shape |
|---|---|---|
| `gpt-5.6-sol` | `high` (`max` for the hardest) | architectural or multi-file complex features, parser-class work, security-sensitive changes |
| `gpt-5.6-terra` | `high` | the daily driver: standard spec-able features, bugfixes, test writing - default when unsure |
| `gpt-5.6-luna` | `medium` | mechanical bulk: renames, boilerplate, docs, formatting sweeps |

- Pass the pick as `-c model=<tier> -c model_reasoning_effort=<effort>` on the codex exec invocation - CLI flags beat the profile and config.toml defaults.
- A run that fails its own ticket is evidence the shape was misjudged - the retry goes one tier up, never back to the tier that failed. Above sol there is no next tier: take the work over yourself.
- taste stays on the config default: reviewer strength beats reviewer cost.
- Never enable 5.6's ultra mode on a delegated background run - it multiplies token spend by design, with nobody watching.
- The fire announcement names the tier picked and why, in one clause.

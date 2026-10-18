# hm-edu/renovate-config

Shared Renovate presets for all hm-edu repositories on GitHub and git.it.hm.edu.

Usage in a repo's `renovate.json`:

    { "extends": ["github>hm-edu/renovate-config:node"] }

Presets: `default` (always), `node`, `go`, `container`, `flux`.

Policy:
- minor/patch/digest updates are automerged once the release is older than the
  stability window of 1 day (npm, Go, PyPI, all container images incl.
  digests; GitHub Action digests immediately).
- Major updates are never automerged; they get the `major` label and wait for a
  human; database majors carry a migration hint in the PR body.
- Security updates (GitHub/OSV vulnerability alerts) skip the stability window,
  are labelled `security` and automerged with top priority.
- Automerge only works when the repo has branch protection with a required
  status check and "Allow auto-merge" enabled; otherwise Renovate waits forever.

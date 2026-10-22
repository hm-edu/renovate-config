# hm-edu/renovate-config

Shared Renovate presets for all hm-edu repositories on GitHub and git.it.hm.edu.

Usage in a repo's `renovate.json`:

    { "extends": ["github>hm-edu/renovate-config:node"] }

Presets: `default` (always), `gitlab` (git.it.hm.edu projects), `node`, `go`,
`container`, `flux`, `ansible`.

Policy:
- minor/patch/digest updates are automerged as soon as the repo's CI is green.
  There is no stability window: CI is the gate, not release age.
- Major updates are never automerged; they get the `major` label and wait for a
  human; database majors carry a migration hint in the PR body.
- Security updates (GitHub/OSV vulnerability alerts) are labelled `security`
  and get top priority; minor/patch ones automerge like any other.
- Automerge only works when the repo has branch protection with a required
  status check and "Allow auto-merge" enabled (GitHub) or MR pipelines that
  actually run tests (GitLab); otherwise Renovate waits forever - or merges
  untested.

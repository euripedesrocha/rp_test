# rp_test

This repository is a sandbox for testing how release-please works in a mirrored GitLab → GitHub setup.

## Release process (GitLab → GitHub)

- Development happens on GitLab. When `main` updates in GitLab, changes are pushed to this public GitHub mirror.
- GitHub runs release-please on `main` pushes to manage versioning and releases.
- release-please creates/updates a release PR. When merged, it tags `vX.Y.Z`, updates changelog, and creates a GitHub Release.

## Conventional commits

release-please infers changes from commit messages. Use conventional commit types like:

- `feat: ...` for new features (minor)
- `fix: ...` for bug fixes (patch)
- `feat!: ...` or body with `BREAKING CHANGE:` for breaking changes (major)
- Other types supported: `docs`, `test`, `build`, `ci`, `refactor`, `perf`, `chore`.

## Configuration

- `.github/workflows/release-please.yml` triggers on pushes to `master` and manual dispatch.
- `release-please-config.json` configures a simple, single-package repo.
- `.release-please-manifest.json` stores the current released version (managed by the bot). Do not edit manually.

## Notes for mirrored workflow

- Ensure GitHub Actions are enabled in this mirror and the `google-github-actions/release-please-action` has permissions.
- Merge the release PR on GitHub (not GitLab) so tags and release notes are public here.
- To force a specific version, add `Release-As: X.Y.Z` in a commit footer, or set `release-as` in the config for a one-off.

Notes: testing release-please behavior with multiple branches.

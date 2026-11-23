# Hugo updates

The Hugo version is pinned in `.hugo-version` for both deployment and PR builds.
The update workflow checks for a newer stable release every Monday and opens or
updates a pull request. It also starts the build workflow on the update branch,
because pull request workflows created by `GITHUB_TOKEN` require approval.

In repository Settings > Actions > General > Workflow permissions, enable
"Allow GitHub Actions to create and approve pull requests" so the updater can
open pull requests. A pending pull request workflow may still need approval;
the separately dispatched build runs automatically.

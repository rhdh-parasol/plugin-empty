# Fullsend instructions

This playground is a Backstage / RHDH plugin repo. Use Yarn (Berry) from the
vendored binary in `.yarn/releases` via the wrapper at `rhdh/bin/yarn`.

Run Jest tests non-interactively with `CI=true yarn test --watchAll=false`.
If Claude auto-backgrounds a verification command, invoke `TaskStop` before
finishing.

When creating or wiring a plugin package, run
`yarn backstage-cli repo fix --publish` after the package is set up, then
`yarn install` followed by `yarn dedupe`. Include the updated `yarn.lock` in
the commit.

When rebasing a branch and encountering `yarn.lock` conflicts, do not attempt
incremental conflict resolution. Revert `yarn.lock` to the base branch version,
then run `yarn install` followed by `yarn dedupe`.

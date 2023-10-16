# pnpm-update-injected-deps-repro
Reproduction repro for bug report about shared-workspace-lockfile=false and inejcted dependency


## Details

While using `shared-workspace-lockfile=false` pnpm not update dependencies list of sub dependency(`shared`) in `pnpm-lock.yaml` of dependent package(`app`).

If you run `pnpm install`, `apps/app/pnpm-lock.yaml` not updated.
But if you remove `shared` from `apps/app/package.json` `dependencies`, run `pnpm i`, rollback `dependencies`, run `pnpm i`, it's updated.


## Expected Behavior

If i add dependency to `shared` package, update all dependendent `pnpm-lock.yaml` files.

You can try run `pnpm i` in this repo

## Actual Behavior

Nothing happening

## Detailed steps to temporary fix for users

1. Remove your updated dependency (or all)
2. Run `pnpm i`
3. Rollback dependency (or all)
4. Run `pnpm i`

Repeat per all dependent package

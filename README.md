# nondeterministic pnpm lockfile reproduction

## Steps to reproduce

1. `pnpm install`
2. Alternate between:

- `pnpm install --dir a eslint@8.52.0`
- `pnpm install --dir b github:discord/eslint`

## Notes

`github:discord/eslint` is a fork of ESLint version 8.52.0, and pnpm is
seemingly treating it the same as the actual ESLint 8.52.0. It seems as though
there is some kind of race condition in `pnpm` that is causing it to choose
a different version of eslint sometimes for various eslint-related packages.

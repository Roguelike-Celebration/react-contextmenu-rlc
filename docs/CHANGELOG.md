# react-contextmenu-rlc CHANGELOG

## 2.17.0 - 2026-11-07

- Stricter TS types for `onClick` and related handlers.
  - Drops the generic `| Function` escape hatch, and types the `data` parameter as `any`. No runtime changes. Handlers that were already mistyped may now result in type errors.

## 2.16.0 - 2026-11-07

- React 18/19 compatibility.
  - Widen react/react-dom peer ranges to include `^18` and `^19`.
  - Fix TypeScript typings for `@types/react` 18 and 19.

## 2.15.1 - 2026-11-07

- Packaging and doco changes only. Builds files as part of packaging instead of checking the built files into the repo.

## 2.15.0 - 2026-11-07

Initial fork release. Packages the release into a dist tarball that consumers can install it from without having to do a build from the Git repo.

## 2.14.0-rlc

Pseudo-release with RLC customizations on top of upstream's final 2.14.0 release.

## 2.14.0

Final release of original upstream react-contextmenu package.

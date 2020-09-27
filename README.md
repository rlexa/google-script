# google-script

Playground for google script development.

## Baby Steps

- create repo on github
- `git clone <repo>` (need git on machine)
- `cd <repo>` to dir
- `npm init` (need NodeJS)
  - creates `package.json`
- `npm i --save-dev @google/clasp`
  - check with `npx clasp -v`
- `npm i --save-dev @types/google-apps-script`
- create `tsconfig.json` (needed for typescript)
  - _once you use TypeScript, you cannot develop on script.google.com_
  - _apps script's runtime/execution is different than node or web browsers:_
    - _you cannot use the terms export or require normally_
    - _you cannot use window like in web browsers_
```json
{
  "compilerOptions": {
    "lib": ["esnext"],
    "experimentalDecorators": true
  }
}
```
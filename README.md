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
- `npx clasp login` (should open browser for google login)
- `npx clasp create --type standalone`
- create `hello.ts` file:
```ts
const greeter = (person: string) => {
  return `Hello, ${person}!`;
}

function testGreeter() {
  const user = 'Grant';
  Logger.log(greeter(user));
}
```
- `npx clasp push`
- `npx clasp open`
  - run `testGreeter()` and goto View > Logs to view the logs to see the result
- _if your Apps Script project is configured to use the V8 Engine, you should set "target": "ES2019" in your tsconfig.json_
  - did that

### Prepare For Tests

- add `.claspignore` file:
  - _use `npx clasp status > clasp-status.log` and consult the resulting file fyi_
```
# ignore all files…
**/**

# except the extensions…
!appsscript.json
!**/*.gs
!**/*.js
!**/*.ts
!**/*.html

# ignore even valid files if in…
.git/**
node_modules/**

# ignore test files
**/*.spec.ts
```
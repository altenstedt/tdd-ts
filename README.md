What is this?
-------------

This is the setup for the TDD course for TypeScript. You will need
Node.js installed to build and run tests.

  * https://nodejs.org/

The intent here is to show how to setup a package so that you can
start writing unit tests with Node.js and TypeScript. 

Create an npm package in a empty folder

    npm init -y

Install TypeScript

    npm install typescript --save-dev

Create a file `tsconfig.json`:

```
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es6",
    "noImplicitAny": true,
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist",
    "baseUrl": ".",
    "paths": {
      "*": [
        "node_modules/*",
        "src/types/*"
      ]
    }
  },
  "include": [
    "src/**/*"
  ]
}
```

Install Jest, with typings

    npm install jest ts-jest @types/jest --save-dev

Open file `package.json` and edit the `scripts` node, and add a `jest`
node:

```json
"scripts": {
  "test": "jest"
},
"jest": {
  "globals": {
    "ts-jest": {
      "tsConfigFile": "tsconfig.json"
    }
  },
  "moduleFileExtensions": [
    "ts",
    "js"
  ],
  "transform": {
    "^.+\\.(ts|tsx)$": "./node_modules/ts-jest/preprocessor.js"
  },
  "testMatch": [
    "**/spec/**/*.spec.(ts|js)"
  ],
  "testEnvironment": "node"
},
```

Create folders for sources and tests

    mkdir src
    mkdir spec/unit

Create your tests in the spec/unit folder, for example:

```typescript
describe("The class under test", () => {
    it("should work", () => {
        expect(1).toBe(1);
    });
});
```

Run the tests using npm:

    npm test

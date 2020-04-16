# Code class JS packaging

## [Slides](https://voorhoede.github.io/code-class-js-packaging/)

## Setup
```sh
git clone git@github.com:Siilwyn/code-class-js-packaging.git
cd code-class-js-packaging
```

## Exercises

### One
#### Let's create
1. Add information about the minimum Node.js version of 13 to `package.json`. Try it out with Node.js 12 through npm and Yarn using a `start` script in `package.json` that runs `node ./run.js`.
2. Run `npm install` and `yarn install`, you'll see two modules in your lock files figure out where `fsevents` comes from using `npm` and `yarn` commands.
3. Add a `build` script to run the `rollup` binary located in `node_modules` with npm using the arguments: `./src/main.js --format cjs --file ./dist.js`.

### Two
#### Let's publish
1. Package it with `npm pack`! Check the included files, try to influence this with configuration in `package.json` so only the needed files are packed.
2. Use Rollup to create a `main.cjs` file and combine with `exports` so the package exposes both CommonJS and ECMAScript interfaces. Bonus: Try it out in Node.js 12 and 13 using the JS `run` files.
3. Show it to the world with `npm version` and `npm publish`! Don't forget to change the package name and you might need to `npm login`. View it through the CLI with `npm view`.
4. `npm unpublish --force`

### Three
#### Bleeding edge
Install Yarn Berry and run `yarn install`, look into why `node ./src/main.js` doesn't work but `yarn start` does though it is supposed to behave like this.

## Solutions
To get the solution for an exercise apply the solution patch file, for example for the first exercise:
```sh
git apply exercise-1/solution.patch
```

[*<<* My previous code class, about Rust](https://github.com/Siilwyn/code-class-js-rust)

What this code class is about
    How JS is shared in a package
    The ecosystem of tools and services to share JS: npm & yarn
    The dangers of installing and running external code
    Packages vs modules (CommonJS, ECMAScript modules)
Why, do we use packages?
    Contain complexity
    We don't repeat the same mistakes
    Focused, single responsibility, dependencies are good
        Dependencies in JS are free, unlike most languages there is no cost like having version conflicts
        Keep project's total complexity lowest by using focused packages, will lead to high dependency count which is not bad on itself
        Focused packages have generally better docs because "don't document this obscure API in a big framework" is easier to defend than "don't document this obscure library at all"
How?
    npm install voorhoede
        npm is the default package manager for Node.js
        npm is a CLI tool to fetch and place packaged code
        npm CLI uses the npm registry by default, a big database with versioned packaged code
    npm install
        package.json as entrypoint
            not strict standard but agreed upon
            contains project metadata
            Node.js only reads the package `name` and `version`
            pretty free form, yarn and other tools use more fields
        package & lock file get read and a dependency tree is constructed
        package-lock.json vs npm-shrinkwrap.json: identical content but first is not published
    Do you pick a good package
        First simple rule try to avoid < 1.0 packages
        Package stats are very misleading
            downloads, many CI runs and bots
            Unpacked Size, does not tell the install size neither does it tell the 'bundled size'
            Use packagephobia and bundlephobia for that, latter also recommends similar packages
        Probably search on npmjs.com or github.com
            Our ecosystem is controlled by big companies Microsoft and Facebook
        Look at the module's API, skim code and activity
    Then `require` or `import`
        Node.js does a lookup for a local file or in node_modules
        Node.js began with commonJS (`require` and `module.exports`), the web & JS had nothing
        ECMAScript module standard (2015) defined the official way to split up JS code
        Node.js 13 (released a few months ago) supports this standard
        Most of you probably use `import` through babel, however this way of writing is far from standard for Node.js code
Exercises
    cd into each exercise!
    Exercise 1
    Creating a package yourself
        1. volta lts, npm init -y, engines key, yarn and npm treat them differently
        2. 'Flat' dependencies, `npm ls` and `yarn why`: two lock files
        3. Yarn uses a normalized shell, both have node_modules bin in PATH (echo $PATH)
        `npm run` and `yarn run` show available scripts
    Exercise 2
    Publish a ECMAScript & commonJS package
        1. Npm pack outputs file that is send to the npm registry if you would publish, files key
            special files
                readme.md
                license.md
                changelog.md
        2. .cjs vs .mjs and main vs exports
        3. npm version commits and bumps up the version in package.json and package-lock.json, combined with changelog
        package.json content and order
        Made the mistake placing rollup in `dependencies` instead of `devDependencies`
        Show releases on GH as tags: https://github.com/Siilwyn/css-declaration-sorter
        Show module on:
            https://bundlephobia.com/
            https://packagephobia.now.sh/
    Exercise 3
    Updating (deep) dependencies and the package lock
        Yarn plug and play 'fixes' node_modules
            yarn set version berry
            node_modules > .pnp.js & .yarn/cache
            only works with `yarn run`, injects module resolve logic in node
Conclusion
    Publishing a package is easy but hard to get right

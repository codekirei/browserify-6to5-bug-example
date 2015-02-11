#About

I like to symlink my local `app` directory inside `node_modules` to prevent the need for relative path soup when requiring local modules.

Substack talks about this [here](https://github.com/substack/browserify-handbook#organizing-modules).

I've discovered that when using the 6to5ify transform with `require`s that follow a symlinked path, the `require`d modules do not get transformed.

Haven't poked this too hard, so not sure if it an issue with browserify, 6to5, or 6to5ify.

#To Reproduce

1. `npm i`
2. `npm run build-sym` && `npm-run-build-rel`

Compare the bundles. ES6 features persist in `bundle_sym.js`.

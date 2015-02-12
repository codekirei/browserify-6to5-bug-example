#About

I like to symlink my local `app` directory inside `node_modules` to prevent the need for relative path soup when requiring local modules.

Substack talks about this [here](https://github.com/substack/browserify-handbook#organizing-modules).

I've discovered that when using the 6to5ify transform with requires that follow a symlinked path, the required modules do not get transformed.

Haven't poked this too hard, so not sure if it's an issue with browserify, 6to5, or 6to5ify.

#To Reproduce

1. `npm i`
2. `npm run build`

Compare the bundles. ES6 features persist in `bundle_sym.js`, specifically in the file that was required through the symlink.

#Update

This issue is resolved by placing an additional `package.json` file inside the directory that is symlinked to from `node_modules` (`lib_sym` in this case) declaring the browserify transform.

`npm run build` now produces identical bundles.

Solution provided by [sebmck](https://github.com/sebmck) [here](https://github.com/6to5/6to5ify/issues/38).

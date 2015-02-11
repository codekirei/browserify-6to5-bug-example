#About

I like to symlink my local `app` directory inside `node_modules` to prevent the need for relative path soup when requiring local modules.

Substack talks about this [here](https://github.com/substack/browserify-handbook#organizing-modules).

I've discovered that when using the 6to5ify transform with requires that follow a symlinked path, the required modules do not get transformed.

Haven't poked this too hard, so not sure if it's an issue with browserify, 6to5, or 6to5ify.

#To Reproduce

1. `npm i`
2. `npm run build`

Compare the bundles. ES6 features persist in `bundle_sym.js`, specifically in the file that was required through the symlink.

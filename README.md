Repository to reproduce [Support package.json exports "Alternatives"](https://github.com/web-infra-dev/rspack/issues/5052#issue-2046651436). 

## Overview

`lib` contains the library to install, with `exports` pointing to `dist` and `src`. 

`app` is consuming this library (installed via portal). 

To reproduce, do the following: 

```
cd app
yarn
yarn build
```

This will work and create a `app/dist/main.js` with content `Hello from dist`. 

Now, remove the `lib/dist/lib.js` file. webpack would now fallback to the `lib/src/lib.ts` file, but rspack fails with "Failed to resolve lib in ...". 
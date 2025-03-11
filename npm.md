# npm

## Contents

- [npm link](#npm-link)
    - [yalc](#yalc)
- [Specify Lockfile Version](#specify-lockfile-version)

### npm link

You can link local packages together for local testing. `npm link` sets up a global reference which other packages can import. Run `npm link` in the dependency you want to import and then run `npm link dependency-name` in the application package. For more see the resource below.

- [Understanding npm-link](https://medium.com/dailyjs/how-to-use-npm-link-7375b6219557)

#### yalc

This is an alternative to using `link`. This package helps manage some of the [problems](https://github.com/yarnpkg/yarn/issues/1761#issuecomment-259706202) that can arise from `npm | yarn link`. 

- [yalc](https://github.com/wclr/yalc)

### Specify Lockfile Version

If you require a specific package-lock.json version (in your build process for example) you can use `npm i --lockfile-version X` to generate a lock file with the given version. Replace `X` with the version you need, such as `npm i --lockfile-version 2`.

- [Is there any way to fix package-lock.json lockfileVersion so npm uses a specific format?](https://stackoverflow.com/a/74239011)

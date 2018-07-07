Reproduces [yarnpkg/yarn#5840](https://github.com/yarnpkg/yarn/issues/5840), which claims that the `--frozen-lockfile` arg isn't working correctly.

It looks like the error might be limited to workspaces.

This repo reproduces the error with a dependency on `frame-throttle@^2.0.0` in the root package.json, and a dependency on `frame-thottle@^3.0.0` in the `workspace` workspace. The `yarn.lock` only contains the `frame-throttle@^2.0.0` dependency, so `yarn` should update the `yarn.lock` and `yarn --frozen-lockfile` should not update the `yarn.lock` and should exit with an error.

#### Instructions:

1. Clone this repo.
2. Run `yarn --frozen-lockfile`.
3. Note that the `yarn.lock` is not updated, and no error was thrown.
4. Run `yarn`.
5. Note that the `yarn.lock` file is updated.


---
description: Guide to managing out NPM packages in your project
---
# Upgrade packages


## Find outdated packages

From the [npm outdated](https://docs.npmjs.com/cli/outdated) command's docs.

> This command will check the registry to see if any (or, specific) installed packages are currently outdated.

```sh
$ npm outdated
```

<details>
<summary>Sample output using NPM 6.14.7</summary>

```
Package             Current  Wanted  Latest  Location
eslint                6.8.0   6.8.0   7.7.0  preact-quickstart
jest                 24.9.0  24.9.0  26.4.0  preact-quickstart
jest-preset-preact    1.0.0   1.0.0   4.0.2  preact-quickstart
sirv-cli              1.0.3   1.0.3   1.0.6  preact-quickstart
```

</details>


## Upgrade packages

### Upgrade within bounds

From the [npm update](https://docs.npmjs.com/cli/update) command's docs.

> This command will update all the packages listed to the latest version (specified by the tag config), respecting semver.

```sh
$ npm update
```

Or the longer.

```sh
$ npm install --upgrade
```

For global packages, add `-g`.

Optionally supply package names as arguments.

For example, this might change as follows:

```
- "foo": "^1.0.0"
+ "foo": "^1.2.3"
```

But, the package will **remain** within the initial bounds. So the command here would not upgrade from `1` to `2`. See below for that.

### Newest

Install to the latest package available.

#### Use `npm install`

```sh
$ npm install PACKAGE
$ # e.g.
$ npm install react
```

This will ignore any existng any bounds for the package (such as `^1.0.0`). 

But it will still honor other packages which have a peer dependency on certain versions of this package. In one case, I actually ended up downgrading from Vue 3 to Vue 2 instead of getting the latest Vue 3, because of another dependency needing Vue 2.

You might put in a specific version, or get the latest available. I've seen `@latest` and `@next` recommended in install instructions. Those are aliases which point to the latest release version. e.g.

```sh
$ npm install react@17.0.0
$ npm install react@latest
$ npm install react@next
```

Repeat for all your outdated packages as separate commands or all in one. e.g.

```sh
$ npm install react react-dom
```

### Use the `npm-upgrade` package

If you use this 3rd-party package, you can upgrade multiple packages and once and use the interactive view.

See [npm-upgrade](https://www.npmjs.com/package/npm-upgrade) homepage and docs.

> Interactive CLI utility to easily update outdated NPM dependencies with changelogs inspection support.

```sh
$ npx npm-upgrade
```


## Fix security vulnernabities

Use the `audit` command.

### CLI usage

```
npm audit [--json] [--production]
npm audit fix [--force|--package-lock-only|--dry-run|--production|--only=(dev|prod)]
```

### Audit

```sh
$ npm audit
```

<details>
<summary>Sample output using NPM 6.14.7</summary>

```
                       === npm audit security report ===

┌──────────────────────────────────────────────────────────────────────────────┐
│                                Manual Review                                 │
│            Some vulnerabilities require your attention to resolve            │
│                                                                              │
│         Visit https://go.npm.me/audit-guide for additional guidance          │
└──────────────────────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ Moderate      │ Regular Expression Denial of Service                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ acorn                                                        │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=5.7.4 <6.0.0 || >=6.4.1 <7.0.0 || >=7.1.1                  │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ preact-cli [dev]                                             │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ preact-cli > fast-async > nodent-compiler > acorn            │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://npmjs.com/advisories/1488                            │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ High          │ Remote Code Execution                                        │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ serialize-javascript                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=3.1.0                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ preact-cli [dev]                                             │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ preact-cli > copy-webpack-plugin > serialize-javascript      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://npmjs.com/advisories/1548                            │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ High          │ Remote Code Execution                                        │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ serialize-javascript                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=3.1.0                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ preact-cli [dev]                                             │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ preact-cli > workbox-webpack-plugin > workbox-build >        │
│               │ rollup-plugin-terser > serialize-javascript                  │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://npmjs.com/advisories/1548                            │
└───────────────┴──────────────────────────────────────────────────────────────┘
found 3 vulnerabilities (1 moderate, 2 high) in 1649 scanned packages
  3 vulnerabilities require manual review. See the full report for details.
```

</details>

### Fix

Use the fix subcommand.
```sh
$ npm audit fix
```

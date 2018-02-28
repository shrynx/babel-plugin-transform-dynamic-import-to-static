[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

# babel-plugin-transform-dynamic-import-to-static

> a babel plugin to convert dynamic import to static import

## Purpose

This plugin hoists dynamic imports to static imports,
and replaces dynamic import statements with immediately
resolved promises, also won't touch static import.

```js
import A from './A'

import('./B')
```

to

```js
import A from './A'

import _default from './B'

Promise.resolve(_default)
```

See it in action in [astexplorer](https://astexplorer.net/#/gist/5438970728b1d0cf707ee83b40e26aba/f0ddf75c590ad62fb449f2b83dd944f9a9026b43)

## Usage

add as plugin to your babel configuration

```js
{
  //...
  "plugins": [
    // ...
    "babel-plugin-transform-dynamic-import-to-static"
  ]
}
```

## Use case

This plugin was made to use with [react-hot-loader](https://github.com/gaearon/react-hot-loader) and [react-loadable](https://github.com/jamiebuilds/react-loadable) to ensure hot-reloading works
out of the box with a code-split architecture. It is meant to be used only during development.

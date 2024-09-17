# Apiax Prettier Configuration

This is Apiax's recommended Prettier configuration.

- [Apiax Prettier Configuration](#apiax-prettier-configuration)
  - [Features](#features)
  - [Installation](#installation)
  - [Usage](#usage)

## Features

- `printWidth`: **100**
- `tabWidth`: **2**
- `useTabs`: **false**
- `endOfLine`: **lf**
- `trailingComma`: **none**
- `semi`: **true**
- `singleQuote`: **true**
- `jsxSingleQuote`: **true**
- `bracketSpacing`: **true**
- `arrowParens`: **avoid**
- `plugins`: ['prettier-plugin-java']

The following Prettier plugins are optional but recommend:

- [prettier-plugin-java](https://www.jhipster.tech/prettier-java/) - plugin is used to format java code

## Installation

> [!IMPORTANT]
> Prettier is a peer-dependency of this package and should be installed at the root of your project or globally.
>
> See: https://prettier.io/docs/en/install.html

```sh
# install locally on a specific project
npm install --save-dev prettier @apiax/prettier-config
# or install globally
npm install -g prettier @apiax/prettier-config
```

## Usage

To use this config, set the following in `package.json` (if applicable/working in a node project)

```json
{
  "prettier": "@apiax/prettier-config"
}
```

or create a `.prettierrc.cjs` file with the following content:

```js
const prettierConfig = require('@apiax/prettier-config');

module.exports = {
  prettierConfig
};
```

If you want to extend the shared config, you can do so by creating a `.prettierrc.cjs` file with the following content:

```js
const prettierConfig = require('@apiax/prettier-config');

module.exports = {
  ...prettierConfig,
  // ...yourPrettierConfig
  plugins: [
    ...prettierConfig.plugins
    // ...yourPlugins
  ]
};
```

or by using ESM (`.prettierrc.mjs` or `prettierrc.js` if the `package.json` has `"type": "module"`):

```js
import prettierConfig from '@apiax/prettier-config';

export default {
  ...prettierConfig,
  // ...yourPrettierConfig
  plugins: [
    ...prettierConfig.plugins
    // ...yourPlugins
  ]
};
```

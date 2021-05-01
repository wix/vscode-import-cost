# Import Cost VSCode Extension [![Build Status](https://travis-ci.org/wix/import-cost.svg?branch=master)](https://travis-ci.org/wix/import-cost) [![Build status](https://ci.appveyor.com/api/projects/status/ko48qav9qqb8fv8u?svg=true)](https://ci.appveyor.com/project/shahata/import-cost)
[![](https://vsmarketplacebadge.apphb.com/version/wix.vscode-import-cost.svg)](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost) [![](https://vsmarketplacebadge.apphb.com/installs/wix.vscode-import-cost.svg)](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)

This extension will display inline in the editor the size of the imported package.
The extension utilizes webpack in order to detect the imported size.

![Example Image](https://citw.dev/_next/image?url=%2Fposts%2Fimport-cost%2F1quov3TFpgG2ur7myCLGtsA.gif&w=1080&q=75)

## Features
Calculates the size of imports and requires.
Currently supports:

- Default importing: `import Func from 'utils';`
- Entire content importing: `import * as Utils from 'utils';`
- Selective importing: `import {Func} from 'utils';`
- Selective importing with alias: `import {orig as alias} from 'utils';`
- Submodule importing: `import Func from 'utils/Func';`
- Require: `const Func = require('utils').Func;`
- Supports both `Javascript` and `Typescript`

## Why & How
I detail the Why and How in this blog post:
https://medium.com/@yairhaimo/keep-your-bundle-size-under-control-with-import-cost-vscode-extension-5d476b3c5a76

## Configuration

The following properties are configurable:

```javascript
  // Upper size limit, in KB, that will count a package as a small package
  "importCost.smallPackageSize": 50,

  // Upper size limit, in KB, that will count a package as a medium package
  "importCost.mediumPackageSize": 100,

  // Decoration color for small packages
  "importCost.smallPackageColor": "#7cc36e",

  // Decoration color for medium packages
  "importCost.mediumPackageColor": "#7cc36e",

  // Decoration color for large packages
  "importCost.largePackageColor": "#d44e40",

  // File extensions to be parsed by the Typescript parser
  "importCost.typescriptExtensions": [
    "\\.tsx?$"
  ],

  // File extensions to be parsed by the Javascript parser
  "importCost.javascriptExtensions": [
    "\\.jsx?$"
  ],

  // Which bundle size to display
  "importCost.bundleSizeDecoration": "both",

  // Display the 'calculating' decoration
  "importCost.showCalculatingDecoration": true,

  // Print debug messages in output channel
  "importCost.debug": false
```
Any package size above the mediumPackageSize limit will be considered large.


## Known Issues
- Importing two libraries with a common dependency will show the size of both libraries isolated from each other, even if the common library needs to be imported only once.

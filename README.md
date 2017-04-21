# npmtest-timm

#### basic test coverage for  timm (v1.2.5)  [![npm package](https://img.shields.io/npm/v/npmtest-timm.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-timm) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-timm.svg)](https://travis-ci.org/npmtest/node-npmtest-timm)

#### Immutability helpers with fast reads and acceptable writes

[![NPM](https://nodei.co/npm/timm.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/timm)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-timm/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-timm/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-timm/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-timm/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-timm/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-timm/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-timm/tree/gh-pages/build)|

- [https://npmtest.github.io/node-npmtest-timm/build/coverage.html/index.html](https://npmtest.github.io/node-npmtest-timm/build/coverage.html/index.html)

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-timm/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fcoverage.lib.html.png)](https://npmtest.github.io/node-npmtest-timm/build/coverage.html/index.html)

- [https://npmtest.github.io/node-npmtest-timm/build/test-report.html](https://npmtest.github.io/node-npmtest-timm/build/test-report.html)

[![test-report](https://npmtest.github.io/node-npmtest-timm/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-timm/build/test-report.html)

- [https://npmdoc.github.io/node-npmdoc-timm/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-timm/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-timm/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-timm/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-timm/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-timm/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "timm",
    "version": "1.2.5",
    "description": "Immutability helpers with fast reads and acceptable writes",
    "main": "lib/timm.js",
    "dependencies": {},
    "devDependencies": {
        "ava": "0.16.0",
        "babel-cli": "6.16.0",
        "babel-core": "6.17.0",
        "babel-eslint": "7.0.0",
        "babel-preset-es2015": "6.16.0",
        "babel-preset-react": "^6.16.0",
        "babel-preset-stage-2": "6.17.0",
        "chalk": "1.1.3",
        "coffee-script": "1.11.1",
        "coveralls": "2.11.14",
        "cross-env": "3.1.2",
        "envify": "3.4.1",
        "eslint": "3.7.1",
        "eslint-config-airbnb": "12.0.0",
        "eslint-plugin-flowtype": "2.20.0",
        "eslint-plugin-import": "1.16.0",
        "eslint-plugin-jsx-a11y": "2.2.3",
        "eslint-plugin-react": "6.4.0",
        "extract-docs": "1.4.0",
        "flow-bin": "0.35.0",
        "immutable": "3.8.1",
        "lodash": "4.16.4",
        "nyc": "8.3.1",
        "seamless-immutable": "6.1.0",
        "uglifyjs": "2.4.10",
        "xxl": "1.2.0"
    },
    "scripts": {
        "ava": "ava --watch",
        "flow": "flow check || exit 0",
        "lint": "eslint src/timm.js",
        "test": "npm run testCovFull",
        "testFast": "ava",
        "testCovFast": "npm run testCovPrepare && npm run testCovDev && npm run testCovReport",
        "testCovFull": "npm run testCovPrepare && npm run testCovDev && npm run testCovProd && npm run testCovMin && npm run testCovReport",
        "testCovNoMin": "npm run testCovPrepare && npm run testCovDev && npm run testCovProd && npm run testCovReport",
        "testCovPrepare": "rm -rf ./coverage .nyc_output .nyc_tmp && mkdir .nyc_tmp",
        "testCovDev": "cross-env NODE_ENV=development nyc ava && mv .nyc_output/* .nyc_tmp/",
        "testCovProd": "cross-env NODE_ENV=production nyc ava && mv .nyc_output/* .nyc_tmp/",
        "testCovMin": "cross-env TEST_MINIFIED_LIB=1 nyc ava && mv .nyc_output/* .nyc_tmp/",
        "testCovReport": "cp .nyc_tmp/* .nyc_output/ && nyc report --reporter=html --reporter=lcov",
        "compile": "rm -rf ./lib && mkdir lib && babel -o lib/timm.js src/timm.js && cp src/api.js.flow lib/timm.js.flow",
        "docs": "extract-docs --template docs/README_TEMPLATE.md --output README.md",
        "uglify": "cross-env NODE_ENV=production envify lib/timm.js | uglifyjs - -o lib/timm.min.js --mangle --compress --comments \"/^!/\"",
        "build": "npm run lint && npm run flow && npm run compile && npm run uglify && npm run testCovFull && npm run docs && npm run xxl",
        "travis": "npm run compile && npm run testCovNoMin",
        "xxl": "xxl",
        "benchmarks": "coffee tools/benchmarks.coffee"
    },
    "ava": {
        "files": [
            "test/*.js"
        ],
        "babel": "inherit"
    },
    "repository": {
        "type": "git",
        "url": "http://guigrpa.github.io/timm/"
    },
    "keywords": [
        "immutability"
    ],
    "author": "Guillermo Grau Panea",
    "license": "MIT"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

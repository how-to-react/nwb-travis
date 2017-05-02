# NWB Travis

[![Build Status](https://travis-ci.org/how-to-react/nwb-travis.svg?branch=master)](https://travis-ci.org/how-to-react/nwb-travis)
[![Coverage Status](https://coveralls.io/repos/github/how-to-react/nwb-travis/badge.svg?branch=master)](https://coveralls.io/github/how-to-react/nwb-travis?branch=master)

Absolute minimum travis NWB build.

## Recreating
- `$ nwb new web-module nwb-travis`
- Updated `travis.yml` to use node version 7.9.0 

```
sudo: false

language: node_js
node_js:
  - 7.9.0

cache:
  directories:
    - node_modules

before_install:
  - npm install codecov.io coveralls

after_success:
  - cat ./coverage/lcov.info | ./node_modules/codecov.io/bin/codecov.io.js
  - cat ./coverage/lcov.info | ./node_modules/coveralls/bin/coveralls.js

branches:
  only:
    - master

```
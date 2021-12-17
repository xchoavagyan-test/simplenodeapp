name: test

on:
  pull_request:
    branches:
      - master

jobs:
  build:

    name: my job
    runs-on: ${{ matrix.os }}
    
    strategy:
      matrix:
        os: [macos-latest, windows-latest, ubuntu-18.04]
        node-version: [12.x]
        # See supported Node.js release schedule at https://nodejs.org/en/about/releases/ 
        include:
          - os: ubuntu-18.04
            node-version: 13.x
            experimental: true

    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v2
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm install -g mocha
    - run: npm test

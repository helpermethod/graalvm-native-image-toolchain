# GraalVM Native Image Toolchain

[![test](https://github.com/helpermethod/graalvm-native-image-toolchain/actions/workflows/test.yml/badge.svg)](https://github.com/helpermethod/graalvm-native-image-toolchain/actions/workflows/test.yml)


This GitHub Action sets up a collection of tools for building GraalVM Native Image applications, including

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

## Inputs

### `graalvm-version`

**Required** The GraalVM version.

### `java-version`

**Required** The Java version.

## Usage

Add the `graalvm-native-image-toolchain` action to your workflow and run your build tool of choice.

```yml
jobs:
  build:
    runs-on: ubuntu-lastest
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - name: Set up GraalVM Native Image toolchain
        uses: helpermethod/graalvm-native-image-toolchain@0.0.1
        with:
          graalvm-version: 21.2.0
          java-version: 11
      - name: Build
        run: ./mvnw -B verify 
```

Works especially well with build matrices.

```yml
jobs:
  build:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
    steps:
      steps:
        - name: Check out repository
          uses: actions/checkout@v2
        - name: Set up GraalVM Native Image toolchain
          uses: helpermethod/graalvm-native-image-toolchain@0.0.1
          with:
            graalvm-version: 21.2.0
            java-version: 11
        - name: Build
          run: ./mvnw -B verify
```

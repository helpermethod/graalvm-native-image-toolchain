# GraalVM Native Image Toolchain

A GitHub Action to setup a complete toolchain for building GraalVM Native Image applications, including

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

## Inputs

### `graalvm-version`

**Required** The GraalVM version

### `java-version`

**Required** The Java version

## Usage

Include the `GraalVM Native Image Toolchain Action` and run your build tool of choice.

```yml
jobs:
  build:
    runs-on: ubuntu-lastest
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - name: helpermethod/graalvm-native-image-toolchain@0.0.1
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
        os: os: [ubuntu-latest, macos-latest, windows-latest]
    steps:
      steps:
        - name: Check out repository
          uses: actions/checkout@v2
        - name: helpermethod/graalvm-native-image-toolchain@0.0.1
          with:
            graalvm-version: 21.2.0
            java-version: 11
        - name: Build
          run: ./mvnw -B verify
```

# GraalVM Native Image Toolchain

A GitHub Action for setting up a GraalVM Native Image toolchain consisting of

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

## Inputs

### `graalvm-version`

**Required** The GraalVM version

### `java-version`

**Required** The Java version. Currently only 8, 11 and 16.

## Usage

Include the `GraalVM Native Image Toolchain Action` and run your build tool of choice.

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
        os: os: [ubuntu-latest, macos-latest, windows-latest]
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

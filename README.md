# GraalVM Native Image Toolchain

This GitHub Action sets up a complete toolchain for building GraalVM Native Image applications, including

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

No more forgetting to install the native-image executable, no more including the wrong GitHub Action to prepare your Windows environment!

# Usage

Just include the `GraalVM Native Image Toolchain Action` and run your build tool of choice

```yml
name: ci
on: push
jobs:
  build:
    runs-on: ubuntu-lastest
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - name: helpermethod/graalvm-native-image-toolchain@0.0.1
        with:
          graalvm-version: 21.2.0.java16
      - name: Build
        run: ./mvnw --batch-mode verify 
```

Works especially well with build matrices

```yml
name: ci
on: push
jobs:
  assemble:
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
            graalvm-version: 21.2.0.java16
        - name: Build
          # the maven.test.skip system property needs to be quoted to work across all platforms
          run: ./mvnw --batch-mode verify '-Dmaven.test.skip=true'

```

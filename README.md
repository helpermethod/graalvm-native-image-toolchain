# GraalVM Native Image Toolchain Action

This GitHub Action sets up a complete toolchain for building GraalVM Native Image applications, including

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

No more forgetting to install the native-image executable, no more including the wrong GitHub Action to prepare your Windows environment!

# Usage

Just include the `GraalVM Native Image Toolchain Action` and run your build tool of choice

```
name: ci
on: push
jobs:
  build:
  - name: Check out repository
    uses: actions/checkout@v2
  - name: helpermethod/graalvm-native-image-toolchain@0.0.1
```

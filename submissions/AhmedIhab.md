
![MetaCall-macOS](https://drive.google.com/uc?export=view&id=1eO4kG8yueHQMMt4y7ESMPpQVeYDggiH2)

# Google Summer of Code 2023: Improve CI/CD for MetaCall Core MacOS

## About MetaCall

MetaCall is a **polyglot** runtime environment, which allows you to run **multiple programming languages** in the same project.
For example, you can have a Node.js application that uses a Python script and a Ruby script, all in the same project.
You can view more example and use cases from [here](https://github.com/metacall/examples)

Furthermore, MetaCall represents a serverless runtime environment, also known as Function as a Service (FaaS), enabling you to execute your code within the cloud without the need to concern yourself with the underlying infrastructure. [Give it a try](https://metacall.io/)

## Idea Motivation

MetaCall Core has an intensive test case that is mainly focused on Linux (including Sanitizers in order to detect memory, address, undefined behavior, or threading bugs). The main idea is to support multiple platforms and architectures with multiple compilers but the current baseline (Linux with GCC, Windows with MSVC, and MacOS with Clang; all on amd64 architecture) So, We will implement full CI/CD for macOS with the maximum amount of language support possible for now MetaCall has one for Linux and Windows

## Work done

### 1. Setup CI/CD for MacOS on Github Actions

The CI file responsible for setting up the environment and configure any needed dependencies for MetaCall to be built correctly on MacOS. Also it removes any pre-installed dependencies that came with Github Runner that may cause conflicts with the build process.Further more it create a matrix with Debug & Release and No sanitizers, Address sanitizer and Thread Sanitizer to test it with different configurations.

### 2. Extend MetaCall Scripts

Make metacall-environment.sh script support macOS besides Linux it checks if the OS is Linux or macOS and install the dependencies accordingly. Also it configures any needed CMAKE flags for the build process.

### 3. Fix MacOS build issues

With help of ORG mentors we were able to fix all MacOS build issues

## Pull Requests

| PR | Description | Status |
|----------|----------|----------|
| [#383](https://github.com/metacall/core/pull/383) | Add initial macos pipeline and scripts  | Merged |
| [#391](https://github.com/metacall/core/pull/391) | Build with Python support for MacOS | Merged |
| [#405](https://github.com/metacall/core/pull/405) | Build with Java support for MacOS | Merged |
| [#428](https://github.com/metacall/core/pull/428) | Build with Ruby and Pass cmake options using env file macOS | Merged |
| [#433](https://github.com/metacall/core/pull/433) | Enable Wasm support in macOS | Merged |
| [#435](https://github.com/metacall/core/pull/435) | Use Pre-built Node for macOS  | Merged |
| [#436](https://github.com/metacall/core/pull/436) | Build MetaCall with TypeScript Support | Merged |
| [#437](https://github.com/metacall/core/pull/437) | Build MetaCall with rpc and file support for macOS| Merged |
| [#439](https://github.com/metacall/core/pull/439) | Build MetaCall with Cobol Support for macOS | Merged |
| [#446](https://github.com/metacall/core/pull/446) | Some improvements to macOS CI  | Merged |
| [#454](https://github.com/metacall/core/pull/454) | Enable Backtracing in macOS CI  | Merged |
| [#455](https://github.com/metacall/core/pull/455) | Enable GO ports in macOS CI  | Merged |

## Raise Issues

| Issue | Description | Status |
|----------|----------|----------|
| [#401](https://github.com/metacall/core/issues/401) | MacOS CI goes into deadlock while testing with nodeJS | Closed |
| [#408](https://github.com/metacall/core/issues/408) | Ruby fails on macOS CI | Closed |
| [#426](https://github.com/metacall/core/issues/426) | Sanitizer Fails on macOS | Closed |
| [#427](https://github.com/metacall/core/issues/427) | Clang Warning on macOS | Closed |
| [#440](https://github.com/metacall/core/issues/440) | Build fails in macOS after adding C support  | Closed |
| [#447](https://github.com/metacall/core/issues/447) | macOS build CI fails with netcore7  | Open |

## Future Work

- [ ] Add more languages support for macOS (Rust, NetCore)
- [ ] Fork nodejs library build


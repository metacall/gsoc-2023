
![MetaCall-windows](https://github.com/metacall/gsoc-2023/assets/98312397/5461aca3-79c2-467c-81ba-5af0a3b83168)
# Google Summer of Code 2023: Improve CI/CD for MetaCall Core Windows

## Table of Contents
- [Introduction](#introduction)
- [Objectives](#objectives)
- [Technologies Used](#technologies-used)
- [Implementation](#implementation)
  - [Phase 1: Setup and Configuration](#phase-1-setup-and-configuration)
  - [Phase 2: Integrating with CMAKE variables](#phase-2-integrating-with-cmake-variables)
  - [Phase 3: Adding new languages and bugfixes](#phase-3-adding-new-languages-and-bugfixes)
- [Results and Outcomes](#results-and-outcomes)
- [Future Work](#future-work)
- [Work Done](#list-of-prs-raised-during-the-project)

## Introduction
 MetaCall Core has a intensive test case which is mainly focused on Linux (including Sanitizers in order to detect memory, address, undefined behavior or threading bugs). Currently we are improving the Windows CI/CD support with MSVC.

## Objectives
- To implement and complete testing CI/CD for Windows to run with different compilers (MSVC for now).
- Packaging dependencies of `metacall/core` in an efficient and scalable manner.
- Easy updates and new language addition to CI pipeline for windows setup.
- Remove vendor lock-in for pipeline.

## Technologies Used
A non exhaustive list of the tools, platforms, and technologies used in the project.
C/C++, CMake, Bash, Batch, PowerShell, Github, etc.

## Implementation

### Phase 1: Setup and Configuration
The biggest blocker for starting the development of the project was to have the build running locally for windows to test changes since changes code and waiting for the CI to run was not efficient and consistent.

I created a local environment that mimics the CI pipeline by updating the tools(scripts) that are responsible to build the metacall core.

I have written an article on [How to seetup Metacall development environment on windows](https://www.codu.co/articles/setting-up-metacall-development-environment-on-windows-jxk6iltl) to make it easier for new contributors to get up and running soon with the project.


### Phase 2: Integrating with cmake variables
Metacall heavily depended upon patching environment variables for CI pipleline which was hard to maintain and keep track of.
We are working on migrating the existing dependencies to use `CMAKE` variables to configure the project instead of patching the env.

Here is the PR for the required instrumentation [#394](https://github.com/metacall/core/pull/394).
Example implementation PR for Ruby integration [#415](https://github.com/metacall/core/pull/415).

### Phase 3: Adding new languages and bugfixes
At the time of writing we are having support for following languages in windows CI - `python, nodejs, java, ruby, typescript, wasm, rpc`.

PRs for adding support for `file and C` loader are in progress, requiring investigation bug causes in the `core` itself.

Remaining majorr languages which are not supported in windows CI are following
```C / .Net / Rust```


## Results and Outcomes
- More test coverage on windows.
- Improved core due to bugfixes discovered during CI implementation.
- No more patching required for CI
- Closer to non vendor locking state.

## Future Work
The project still have some major languages missing from the CI like `C, Rust`. In future it would be great to support these languages as well.
But the complexity of their implementation is high.

Also we should look into windows distribution system for metacall.


---

### List of PRs raised during the project

| PR | Description | Status |
|----------|----------|----------|
[#363](https://github.com/metacall/core/pull/363) | Fix missing headers in node loader port | Closed
[#364](https://github.com/metacall/core/pull/364) | Fix NodeJS tests in GitHub CI  | Merged
[#365](https://github.com/metacall/core/pull/365) | Ruby win ci tests setup | Closed
[#367](https://github.com/metacall/core/pull/367) | Add Java tests to Windows CI | Merged
[#394](https://github.com/metacall/core/pull/394) | Remove patching from ci  | Merged
[#396](https://github.com/metacall/core/pull/396) | TS loader dependency copying CMAKE | Closed
[#402](https://github.com/metacall/core/pull/402) | Add npm exec path to cmake vars | Merged
[#415](https://github.com/metacall/core/pull/415) | Add ruby support to windows CI tests | Merged
[#431](https://github.com/metacall/core/pull/431) | Wasm Windows CI setup | Closed
[#432](https://github.com/metacall/core/pull/432) | Add typescript tests to windows CI | Merged
[#452](https://github.com/metacall/core/pull/452) | Add rpc support on win ci | Open
[#458](https://github.com/metacall/core/pull/458) | C windows CI setup  | Draft

---
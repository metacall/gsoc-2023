# Google Summer of Code 2023
List of project ideas for contributors applying to the Google Summer of Code program in 2023 (GSoC 2023).

## Timeline/milestones

Please always refer to the [official timeline](https://developers.google.com/open-source/gsoc/timeline).  
  
## Application Process

#### 0. Get familiar with GSoC

First of all, and if you have not done that yet, read [the contributor guide](https://google.github.io/gsocguides/student/) which will allow you to understand all this process and how the program works overall. Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.  
  
#### 1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available [contact channels](https://github.com/metacall/gsoc-2023#find-us). We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!  
  
#### 2. Understand that

- You're committing to a project and we may ask you to publicly publish your weekly progress on it.
- It's the third year Metacall is joining the GSoC program and we will ask you to give feedback on our mentorship and management continuously.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't give any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser **without downloading anything**.

You can also ask for a review anytime to the community or mentor candidates before the contributor application deadline. It's much easier if you get feedback early than to wait for the last moment.
  

## Project Ideas

You can also propose your own.

### Cross-Platform Builds

**Skills**: C/C++, Bash, Batch, Guix, DevOps

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:
MetaCall has multiple runtimes embedded on it and one of its objectives is to be as cross platform as possible. Each runtime has its own dependencies which create a huge dependency tree sometimes. This is a big complexity that is difficult to handle. Currently we are using Guix as our build system in Linux and we achieved to compile MetaCall and make it completely self-contained (in Linux for amd64 at the moment of writting). This allows MetaCall to be installed even in a BusyBox and work properly without any other system dependency. Current implementation of the build system consist of 3 repositories:

 - Distributable Linux: https://github.com/metacall/distributable-linux
 - Distributable Windows: https://github.com/metacall/distributable-windows
 - Distributable MacOs: https://github.com/metacall/distributable-macos

The objective of this idea is to improve the cross-platform support for the main supported platforms:
 - Implementing the build script for MacOs from scratch with automated CI, in a similar way to how Windows distributable has been done. Add tests and improve the install script for Linux [by adding support to MacOs](https://github.com/metacall/install/blob/master/install.sh#L213).
 - Improving the language support[[1]](https://github.com/metacall/distributable-windows/issues/14)[[2]](https://github.com/metacall/distributable-windows/issues/13) for Windows with their [respective tests](https://github.com/metacall/distributable-windows/blob/master/test.bat) and [improving the install script](https://github.com/metacall/install/blob/282d193329c6c9bbfca86b5ce4c7db8679f67c88/install.ps1#L158) for Windows.
 - Adding [new architectures](https://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.70/html_node/Specifying-Target-Triplets.html#Specifying-Target-Triplets) to Linux with their respective tests (for this it is possible to use Docker multi-architecture for supporting those tests) and the install script support for those architectures.

Finally it would be interesting to add a README in [this repository](https://github.com/metacall/distributable) in order to document the three repositories and build systems.

**Expected outcomes**: To implement and complete CI/CD builds for Windows, Linux and MacOS in order to provide cross-platform binary distributions of MetaCall.

**Possible mentors**: ??

**Resources**:
 - Guix Build System options: https://guix.gnu.org/manual/en/html_node/Additional-Build-Options.html
 - Docker Multi-Arch support: https://docs.docker.com/desktop/multi-arch/

### Rust Actix + Inline TypeScript React Server Side Rendering (tsx)

**Skills**: Rust, TypeScript, React

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:
Recently MetaCall has provided support for [inlining other languages into Rust](https://github.com/metacall/core/blob/adcc50496d53797011b87f42131cb857d0009ffb/source/ports/rs_port/tests/inline_test.rs#L13) though its macro system. This allows adding languages like Python or TypeScript into Rust easily. The main idea of this project is to create a Proof of Concept of an Actix server that easily embeds Server Side Rendering with TypeScript. This should be like a small framework which uses MetaCall and allows writing endpoint handlers where you can embed TypeScript directly with simplicity. In order to achieve this, the Rust Port will need to be extended, adding extra functionality required.

The Proof of Concept can contain also benchmarks, in order to compare it to other server side rendering solutions or in order to be the baseline for future optimizations in MetaCall TypeScript support. Adding documentation and examples is needed too, so it can be reused in the future by other users and the functionality and utility of the framework is shown.

**Expected outcomes**: A small framework based on Actix implementing inline server side rendering with React (TypeScript).

**Possible mentors**: ??

**Resources**:

 - MetaCall Rust Port Crate: https://docs.rs/metacall/latest/metacall/
 - MetaCall Rust Port Source: https://github.com/metacall/core/tree/develop/source/ports/rs_port
 - MetaCall FaaS SSR Example: https://github.com/metacall/basic-react-SSR-example

### Run MetaCall in Browser

**Skills**: WebAssembly, CMake, C/C++

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Hard

**Description**:
Nowadays WebAssembly is gaining a lot of traction, allowing more functionality each time and supporting as a compilation target in a wide variety of languages. One of the first attempts to be able to virtualize a Linux into the browser was JSLinux from Fabrice Bellard. This solution was implemented originally using `asm.js` and existing technology before the standardization of WebAssembly. The project has been refactored through the time but there are other alternatives nowadays which can be more powerful and production ready. A newer alternative to JSLinux is CheerpX, a modern compiler forked from LLVM for C/C++ to WebAssembly.

The objective of this idea is to create a Proof of Concept in order to run MetaCall in browser, other technologies different from the previously mentioned can be also considered, there is no restrictions. We should be able to create a very minimal ISO image that can be virtualized inside a browser which can execute MetaCall or at least a way to execute MetaCall in browser with few languages, so we can demonstrate the interoperability. The project should allow to create a base to run polyglot applications easily in the browser.

**Expected outcomes**: A working version of MetaCall running in browser (in WebAssembly), with the ability to interop between different languages.

**Possible mentors**: ??

**Resources**:

 - JSLinux from Fabrice Bellard: https://bellard.org/jslinux/
 - CheerpX Compiler: https://github.com/leaningtech/cheerp-compiler
 - CheerpX WebVM Article: https://leaningtech.com/webvm-server-less-x86-virtual-machines-in-the-browser/
 - CheerpX WebVM Demo: https://webvm.io

### Run MetaCall in mobile platforms

??

### Polyglot Debugger

**Skills**: C/C++, Debuggers, VSCode (JavaScript/TypeScript)

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Hard

**Description**:
The objective of this project is to implement support in MetaCall for debugging, mainly in Visual Studio Code IDE, but it can be done with any other IDE that supports the debugging protocols from NodeJS, Python, etc. This project may imply to modify MetaCall Core in order to enable debugging, or it may be done in a completely new project that adds debugging capabilities to MetaCall CLI or Core. This project is highly experimental at the moment of writing, but there has been already some investigation respect to it. The easy part is to launch the runtime with debugging protocol enabled, for example: `node --inspect script.js`. But attaching to running processes is more complex. For the latter one there is a [requirement in MetaCall Core](https://github.com/metacall/core/issues/231) which makes it more difficult to implement.

The final result of this project should be to be able to debug a polyglot application, adding breakpoints and jumping between languages inside Visual Studio Code (or any other similar IDE). It may require to implement a derived launch plugin for unifiying other launcher plugins.

**Expected outcomes**: A Visual Studio Code extension capable of debug a polyglot application with MetaCall.

**Possible mentors**: ??

**Resources**:

 - NodeJS Debugging: https://nodejs.org/en/docs/guides/debugging-getting-started/
 - Python Debugging in VSCode: https://code.visualstudio.com/docs/python/debugging
 - GraalVM Polyglot Live Extension: https://marketplace.visualstudio.com/items?itemName=hpi-swa.polyglot-live-programming
 - VSCode Managing Polyglot Environments: https://dev.to/gokayokyay/managing-vscode-profiles-for-the-polyglot-developers-5d1j




## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).


Telegram:
<a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

Discord: 
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>

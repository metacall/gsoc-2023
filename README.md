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

### Improve CI/CD for MetaCall Core

**Skills**: C/C++, CMake, Bash, Batch, PowerShell, DevOps

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Medium

**Description**:
MetaCall Core has a intensive test case which is mainly focused on Linux (including Sanitizers in order to detect memory, address, undefined behavior or threading bugs). Currently we are improving the Windows CI/CD support with MSVC but it is not finished yet and it will need to further work. In another hand, it will be interesting to also implement MacOS support with Clang. The main idea is to support multiple platforms and architectures with multiple compilers but the current baseline (Linux with GCC, Windows with MSVC and MacOS with Clang; all on amd64 architecture) should be enough for the scope of the project. The complexity of this relies in the dependencies of the Core itself because they have to be pre-installed before the Core is built and it must be automated in such a way that can be later on moved to a different CI or environment and work out of the box. Also while implementing the tests, it is possible that some CMake bugs or Core bugs are shown, and those must be addressed too. For this task you can get assistance from the MetaCall Team itself, so do not be afraid, you can still raise an issue pointing out the problem and we can solve it eventually.

For more information, review the current state of the CI/CD and tools for installing dependencies and configuring & building MetaCall on different platforms.

  - MetaCall Core CI/CD: https://github.com/metacall/core/tree/develop/.github/workflows
  - MetaCall Core Tools: https://github.com/metacall/core/tree/develop/tools

**Expected outcomes**: To implement and complete testing CI/CD for Windows, Linux and MacOS in order to provide cross-platform testing for multiple platforms, compilers and architectures. Also solve the problems that will appear in platforms during the implementation of the CI/CD.

**Possible mentors**: Gil Arasa Verge, Vicente Eduardo Ferrer Garcia

### FaaS TypeScript Reimplementation

**Skills**: TypeScript

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Medium

**Description**:
This project offers a reimplementation of [MetaCall FaaS](https://dashboard.metacall.io) but with a simpler and less performant implementation. The objective of this FaaS reimplementation is to provide a simple and portable FaaS that can be run from the CLI in order to locally test the functions and complete projects that can be deployed into MetaCall FaaS. This is a very important part of the project because it is needed in order to fullfill the developer workflow when developing distributed polyglot applications.

It should mimick the [MetaCall FaaS REST API](https://github.com/metacall/protocol/blob/8367aee106128a5bfae13ba613bcfdc2793b6dcf/src/protocol.ts) but without need of authentication and with only the required capabilities for development. This repository will share parts with MetaCall FaaS through [MetaCall Protocol](https://github.com/metacall/protocol) so code can be reused between the repositories.

For better deployment, the MetaCall FaaS should be integrable with MetaCall CLI, providing a self contained distributable with all the compiled code which can be launched or invoked from an external CLI via API.

**Expected outcomes**: An embeddable library that can be used for locally testing MetaCall projects as if they were hosted on the FaaS.

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez

**Resources**:
 - MetaCall FaaS TypeScript reimplementation repository: https://github.com/metacall/faas
 - MetaCall FaaS: https://dashboard.metacall.io
 - Video Deploying a hundred functions into MetaCall FaaS using the Dashboard: https://www.youtube.com/watch?v=2RAqTmQAWEc
 - MetaCall Protocol: https://github.com/metacall/protocol
 - MetaCall Deploy: https://github.com/metacall/deploy

### Builder

**Skills**: Go, Docker, BuildKit, Sandboxing, Kubernetes

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:
Currently MetaCall is offered as Docker image on [Docker Hub](https://hub.docker.com/r/metacall/core). It includes 4 tags (`deps`, `dev`, `runtime` and `cli`) with only one architecture (`amd64`). Right now all the languages are packaged at once into the image, producing a big sized image, specially on the `dev` tag. The idea of this project is to implement a CLI with a separated API which provides a way to generate compact Docker images with MetaCall runtime. Docker does not allow to selectively choose from multiple layers merging them into one with efficient caching, we could do this by means of templating the Dockerfile itself but using the Buildkit API will make the solution much more robust and with the benefit of all the features from Buildkit like caching.

Another main requirement for this project is that it must be run under rootless and daemonless, inside a Dockerized environment (i.e this must be able to be run inside Docker without permissions and without a Docker daemon, so it can be run in a Kubernetes cluster, pushing and pulling the resulting images from a private registry).

This project has to be efficient and sandboxed, focused on FaaS development and producing compact images in terms of size and dependencies, so the bandwidth and attack surface is reduced.

**Expected outcomes**: A command line interface and library that is able to selectively compose docker images and run inside Docker/Kubernetes for MetaCall with efficient caching and compact size.

**Possible mentors**:  Fernando Vaño Garcia, Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

### MacOS Distributable

**Skills**: C/C++ Dependency Management, CMake, Bash, DevOps

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Hard

**Description**:

MetaCall has multiple runtimes embedded on it and one of its objectives is to be as cross platform as possible. Each runtime has its own dependencies which create a huge dependency tree sometimes. This is a big complexity that is difficult to handle. Currently we are using Guix as our build system in Linux and we achieved to compile MetaCall and make it completely self-contained (in Linux for amd64 at the moment of writting). This allows MetaCall to be installed even in a BusyBox and work properly without any other system dependency. Current implementation of the build system consist of 3 repositories:

 - Distributable Linux: https://github.com/metacall/distributable-linux
 - Distributable Windows: https://github.com/metacall/distributable-windows
 - Distributable MacOs: https://github.com/metacall/distributable-macos

The objective of this idea is to improve the MacOS support:
 - Implementing the build script for MacOs with portable dependencies on the automated CI, in a similar way to how Windows distributable has been done.
 - Add tests in order to verify the MacOs portable installation.
 - Improve the install script for Linux [by adding support to MacOs](https://github.com/metacall/install/blob/0f145d4ee5a60b58f7c48f043ed7d0b7d6268609/install.sh#L210) so it can support both platforms at the same time, this will require testing with MacOs too, so another CI with MacOs as runner should be implemented in order to test it through the install script.

**Expected outcomes**: To implement and complete CI/CD builds for MacOS in order to provide cross-platform binary distributions of MetaCall with the maximum amount of languages possible. Extend the current install script for taking into account MacOs and provide testing environment for the MacOs distributable itself and the install script for MacOs.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

### Windows Distributable

**Skills**: C/C++ Depependency Management, CMake, PowerShell, DevOps

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

At the moment of writing, Windows distributable has a base already implemented. It provides support for portable installation of MetaCall Core with tests and install script. But it is incomplete, it only supports Python and NodeJS. The main objective of this project will be to extend the support and make it more complete and stable. The requirements are:

 - Improving the language support[[1]](https://github.com/metacall/distributable-windows/issues/14)[[2]](https://github.com/metacall/distributable-windows/issues/13), improving the existing ones that do not work and adding new ones.
 - Improve the [respective tests](https://github.com/metacall/distributable-windows/blob/master/test.bat) for the new languages added.
 - Improve the [install script](https://github.com/metacall/install/blob/master/install.ps1) with its [respective tests](https://github.com/metacall/install/blob/master/.github/workflows/test-windows.yml).

**Expected outcomes**: To implement and complete CI/CD builds for Windows in order to provide cross-platform binary distributions of MetaCall with the maximum amount of languages possible. Extend the current Windows install script and extend the testing environment for the Windows distributable itself and the install script for Windows.

**Possible mentors**: Fernando Vaño Garcia, Thomas Rory Gummerson, Gil Arasa Verge

**Resources**:
 - MetaCall Core Windows Environment Install Script: https://github.com/metacall/core/blob/develop/tools/metacall-environment.ps1

### Linux Distributable

**Skills**: C/C++ Depependency Management, CMake, Guix, Guile, Bash, Docker, BuildKit, DevOps

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Hard

**Description**:

At the moment of writing, Linux distributable is one of the best suited distributions that we have right now. But it is not completed and it has [some issues](https://github.com/metacall/distributable-linux/issues). The main objective of this project will be to solve those issues, either focused on the user experience or the development of other applications by means of using MetaCall Core embedded into them. Here's the list of the objectives:

 - Solve issues related to environment variables[[1]](https://github.com/metacall/distributable-linux/issues/5)[[2]](https://github.com/metacall/distributable-linux/issues/14), this will require generate an environment variable file based on `guix shell` and it will let us remove [the current approach used in the install script](https://github.com/metacall/install/blob/0f145d4ee5a60b58f7c48f043ed7d0b7d6268609/install.sh#L376).
 - Solve problems with [existing languages not working](https://github.com/metacall/distributable-linux/issues/1), and extend it in order to support more languages, including extending support for [additional features](https://github.com/metacall/distributable-linux/issues/11).
 - Improve support for embedders in order to have portable binaries that can be embedded easily into other languages like C/C++/Zig/Rust[[1]](https://github.com/metacall/distributable-linux/issues/15)[[2]](https://github.com/metacall/zig-example).
 - Adding [new architectures](https://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.70/html_node/Specifying-Target-Triplets.html#Specifying-Target-Triplets) to Linux with their respective tests (for this it is possible to use Docker multi-architecture for supporting those tests) and the install script support for those architectures.

**Expected outcomes**: A better and more stable version of MetaCall Linux Distributable which addresses the current errors and user experience problems.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Gil Arasa Verge

**Resources**:
 - Guix Shell: https://guix.gnu.org/manual/devel/en/html_node/Invoking-guix-shell.html
 - Guix Build System options: https://guix.gnu.org/manual/en/html_node/Additional-Build-Options.html
 - Docker Multi-Arch support: https://docs.docker.com/desktop/multi-arch/

### MetaCall Deploy Integrations

**Skills**: TypeScript, JavaScript

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

We have implemented support for [deployments through CLI](https://github.com/metacall/deploy) and now we require to integrate this CLI/Library into more environments in order to improve the development and adoption of MetaCall FaaS. For this there is a list of required tasks to do:

 - Create a Visual Studio Extension for one click deployment so you don't even need to use the command line for deploying MetaCall projects.
 - Create a GitHub action for integrating MetaCall deployments with your own CI if required.
 - Create a library for exporting the current MetaCall Inspect format into OpenAPI format, so it can be used easily on other projects.
 - ... TODO?

**Expected outcomes**: TODO

**Possible mentors**: Jose Antonio Dominguez

**Resources**:
  - TODO

### Rust Actix + TypeScript React Server Side Rendering (tsx) Framework

**Skills**: Rust, TypeScript, React

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

For this project there is two approaches that can offer different user experiences but having in mind a similar result which is to develop TSX on top of Rust, or basically having an ergonomic and high performance server side rendering for TypeScript written in Rust. The two approaches are the following:

 1) Recently MetaCall has provided support for [inlining other languages into Rust](https://github.com/metacall/core/blob/adcc50496d53797011b87f42131cb857d0009ffb/source/ports/rs_port/tests/inline_test.rs#L13) though its macro system. This allows adding languages like Python or TypeScript into Rust easily. The main idea of this project is to create a Proof of Concept of an Actix server that easily embeds Server Side Rendering with TypeScript. This should be like a small framework which uses MetaCall and allows writing endpoint handlers where you can embed TypeScript directly with simplicity. In order to achieve this, the Rust Port will need to be extended, adding extra functionality required.
 2) If the first approach becomes problematic because Rust macros are limited for this *hacky* task, we may also provide an alternate and simpler approach which fullfills the objective. Basically we should provide a server that is able to load TSX lambdas and render them out of the box. Those lamdas would be written in a separate file a part from Rust, in a folder. A similar approach that [Granian HTTP Server](https://github.com/emmett-framework/granian) has followed but mainly focused on TSX Server Side Rendering.

Either using one or another approach, we should also support building static files and offer them with the Rust server, so we can have the complete lifecicle of development. For this we can embed [SWC](https://swc.rs/) which has great performance and it is written in Rust too.

The Proof of Concept should contain also benchmarks, in order to compare it to other server side rendering solutions or in order to be the baseline for future optimizations in MetaCall TypeScript support. Adding documentation and examples is needed too, so it can be reused in the future by other users and the functionality and utility of the framework is shown. Finally some complete examples should be provided so other users can learn by example how to use the framework and how to extend it. It does not require to have full support for production development but at least our objective is to have a minimal Proof of Concept that works.

**Expected outcomes**: A small framework based on Actix implementing server side rendering with React (TypeScript).

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez

**Resources**:
 - MetaCall Rust Port Crate: https://docs.rs/metacall/latest/metacall/
 - MetaCall Rust Port Source: https://github.com/metacall/core/tree/develop/source/ports/rs_port
 - MetaCall FaaS SSR Example: https://github.com/metacall/basic-react-SSR-example

### MetaCall ChatGPT Example Tutorial

**Skills**: Python, TypeScript, JavaScript

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

TODO

**Expected outcomes**: TODO

**Possible mentors**: Jose Antonio Dominguez

**Resources**:
  - TODO

## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).

 - Telegram:
  <a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

 - Discord:
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

 - Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>

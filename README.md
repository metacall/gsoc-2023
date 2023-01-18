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

**Difficulty rating**: Hard

**Description**:
MetaCall Core has a intensive test case which is mainly focused on Linux (including Sanitizers in order to detect memory, address, undefined behavior or threading bugs). Currently we are improving the Windows CI/CD support with MSVC but it is not finished yet and it will need to further work. In another hand, it will be interesting to also implement MacOS support with Clang. The main idea is to support multiple platforms and architectures with multiple compilers but the current baseline (Linux with GCC, Windows with MSVC and MacOS with Clang; all on amd64 architecture) should be enough for the scope of the project. The complexity of this relies in the dependencies of the Core itself because they have to be pre-installed before the Core is built and it must be automated in such a way that can be later on moved to a different CI or environment and work out of the box. Also while implementing the tests, it is possible that some CMake bugs or Core bugs are shown, and those must be addressed too. For this task you can get assistance from the MetaCall Team itself, so do not be afraid, you can still raise an issue pointing out the problem and we can solve it eventually.

For more information, review the current state of the CI/CD and tools for installing dependencies and configuring & building MetaCall on different platforms.

  - MetaCall Core CI/CD: https://github.com/metacall/core/tree/develop/.github/workflows
  - MetaCall Core Tools: https://github.com/metacall/core/tree/develop/tools

**Expected outcomes**: To implement and complete testing CI/CD for Windows, Linux and MacOS in order to provide cross-platform testing for multiple platforms, compilers and architectures. Also solve the problems that will appear in platforms during the implementation of the CI/CD.


TODO


## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).


Telegram:
<a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

Discord: 
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>

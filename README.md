# Google Summer of Code 2026
List of project ideas for contributors applying to the Google Summer of Code program in 2026 (GSoC 2026).

## Timeline/milestones

Please always refer to the [official timeline](https://developers.google.com/open-source/gsoc/timeline).  
  
## Application Process

#### 0. Get familiar with GSoC

First of all, and if you have not done that yet, read [the contributor guide](https://google.github.io/gsocguides/student/) which will allow you to understand all this process and how the program works overall. Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.  
  
#### 1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available [contact channels](https://github.com/metacall/gsoc-2026#find-us). We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!  
  
#### 2. Understand that

- You're committing to a project and we may ask you to publicly publish your weekly progress on it.
- We will repeatedly ask you to give feedback on our mentorship and management.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't provide any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser without downloading anything.

We **highly recommend you to ask for a review** anytime to the community or mentor candidates before the contributor application deadline. It's much easier if you get feedback early than to wait for the last moment.
  

## Project Ideas

You can also propose your own.

### Implement Core CI Support for C & Distributables

**Skills**: GitHub Actions, C/C++, CMake Build System, Homebrew, Guix, Windows Package Managers

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Hard

**Description**:

MetaCall Core has support for C by using `libffi`, `libclang` and `tcc`. This is widely tested in Linux on the `metacall/core` CI but lacks the implementation for MacOs and Windows. The objective of this project is to provide testing support in the Core for [Windows](https://github.com/metacall/core/pull/458) and [MacOs](https://github.com/metacall/core/pull/445) platforms, and once this is done we should implement this in the Distributables repositories. For this requirement, we will need to implement it in Guix (Linux), Homebrew (MacOs) and manually installing with Batch (Windows). It is not easy because the task requires knowledge of CMake build system and knowledge about different architectures. It willl be difficult but the final result of this is that we will be to bootstrap metacall itself with this. All the platforms will contain metacall.h and the metacall library and we can generate the API of metacall itself for multiples languages by using the C Loader. The explanation of this idea itself can be difficult because we are assuming some previous basic knowledge on MetaCall Core, but if you are intereseted you can ask in our chat groups for further explanation.

**Expected outcomes**: MacOs and Windows C Loader support in the Core and the distribution of the C Loader for Windows, MacOs and Linux. We should able to run things like: `metacall test.c`, once this is implemented.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Param Siddharth

**Resources**:
 - Previous Work: https://github.com/metacall/core/pull/458 & https://github.com/metacall/core/pull/445
 - Known Issues: https://github.com/metacall/core/issues/442
 - Guix `libclang`: https://git.savannah.gnu.org/cgit/guix.git/tree/gnu/packages/llvm.scm#n2160
 - Guix `tcc`: https://packages.guix.gnu.org/packages/tcc/
 - Guix `libffi`: https://packages.guix.gnu.org/packages/libffi

---

### Zig Port Implementation

**Skills**: Zig, Systems Programming, C

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

The goal of this project is to create a new Port for MetaCall in Zig, allowing Zig programs to call and integrate other languages like JavaScript, Python, Ruby, and more. This project will require designing and implementing the Zig port from scratch, leveraging Zig's unique features such as comptime to simplify and improve the API's ergonomics for end users. This project will need to implement all supported types of MetaCall, also async APIs and different loading methodologies. Key aspects to be addressed:

 - Language Interoperability: Develop the necessary bindings and functionality to enable Zig to call functions from other supported MetaCall languages.
 - API Design: Use comptime to build a concise, ergonomic, and type-safe API that makes it easy for developers to integrate MetaCall into their Zig projects.
 - Build System: Ensure the port supports using an already installed version of MetaCall without requiring a full recompilation.
 - Testing and Documentation: Include extensive tests, documentation, and usage examples.
 - Memory Safety: Pay special attention to avoiding memory leaks and ensuring safe integration with Zig's memory model.

Additionally, the project should produce a basic tutorial or article showcasing the Zig port, providing examples of how it can be used to create polyglot applications.

**Expected outcomes**: 
 - A fully functional Zig port for MetaCall that supports calling multiple languages.
 - Comprehensive documentation, tests, and usage examples.
 - A tutorial or article demonstrating how developers can use the Zig port to build polyglot applications.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge

**Resources**:
 - Prior Work: https://github.com/metacall/core/tree/5b592ac0e9a8e498e3e706623d0a788276f566e0/source/ports/zig_port
 - MetaCall Core: https://github.com/metacall/core
 - Zig Documentation: https://ziglang.org/documentation/master/

---

## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).

 - Telegram:
  <a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

 - Discord:
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

 - Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>

# Google Summer of Code 2026
List of project ideas for contributors applying to the Google Summer of Code program in 2026 (GSoC 2026).

---

## Timeline/milestones

Please always refer to the [official timeline](https://developers.google.com/open-source/gsoc/timeline).  

---
  
## Application Process

#### 0. Get familiar with GSoC

First of all, and if you have not done that yet, read [the contributor guide](https://google.github.io/gsocguides/student/) which will allow you to understand all this process and how the program works overall. Refer to its left side menu to quick access sections that may interest you the most, although we recommend you to read everything.  
  
#### 1. Discuss the project idea with the mentor(s)

This is a required step unless you have dived in into the existing codebase and understood everything perfectly (very hard) and the idea you prefer is on the list below.

If your idea is not listed, please discuss it with the mentors in the available [contact channels](https://github.com/metacall/gsoc-2026?tab=readme-ov-file#find-us). We're always open to new ideas and won't hesitate on choosing them if you demonstrate to be a good candidate!  
  
#### 2. Understand that

- You're committing to a project and we may ask you to publicly publish your weekly progress on it.
- We will repeatedly ask you to give feedback on our mentorship and management.
- You wholeheartedly agree with the [code of conduct](https://github.com/metacall/core/blob/develop/.github/CODE_OF_CONDUCT.md).
- You must tell us if there's any proposed idea that you don't think would fit the timeline or could be boring (yes, we're asking for feedback).
  
#### 3. Fill out the application form

We recommend you to follow [Google's guide to Writing a Proposal](https://google.github.io/gsocguides/student/writing-a-proposal) as we won't be too harsh on the format and we won't provide any template. But hey, we're giving you a starting point!

You can send the proposal link to any readable format you wish: Google Docs, plain text, in markdown... and preferably hosted online, accessible with a common browser without downloading anything.

We **highly recommend you to ask for a review** anytime to the community or mentor candidates before the contributor application deadline. It's much easier if you get feedback early than to wait for the last moment.

---

## Artificial Intelligence Usage Policy

In order to fit properly our organization standards of how to use AI, [you can check here our policy](./AI-USAGE-POLICY.md).

---

## Project Ideas

You can also propose your own.

---

### 1. Implement Multi-Language Parser

**Skills**: C/C++, Programming Language Parsers

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

MetaCall Core right now implements support for multiple languages and it provides runtime instrospection by multiple methodologies. This allows to have information for executing the calls in a type safe manner when possible, or list the functions, classes or objects that are loaded into it. This minimal information is only usable for the runtime normally. There is cases like Intellisense or Function Mesh projects, we need to provide a standard tool for generating ASTs from multi-language projects. In this project we will be using a tool like [Tree Sitter](https://tree-sitter.github.io/tree-sitter/) for generating an AST with all the dependency tree between multiple languages. This will be crucial for representing mixed programming language projects in an unified way, so this can be later on consumed by our Visual Studio Code plugin for having Intellisense or by the Function Mesh for breaking down a project in other subparts and distributing the workload.

**Expected outcomes**:
 - Cross-platform tool and library written in C/C++ that can be used as a CLI or from a simple C API that can be embeeded into other projects for parsing programming languages supported by MetaCall Core.
 - It should be able to list all the functions and classes exported by any language.
 - It should be able to create a dependency tree of a multi-language project.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge.

**Resources**:
 - Tree Sitter Documentation: https://tree-sitter.github.io/tree-sitter/
 - Tree Sitter C API: https://github.com/tree-sitter/tree-sitter/blob/master/lib/include/tree_sitter/api.h
 - Tree Sitter Tutorial: https://dev.to/shrsv/making-sense-of-tree-sitters-c-api-2318

---

### 2. Function Mesh Implementation

**Skills**: C/C++, Distributed Systems, Networking, Compiler Design

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: High

**Description**:

This project focuses on converting monolithic applications into scalable microservices by making each function or module a separate service. By utilizing a Remote Procedure Call (RPC) loader, the goal is to enable functions to communicate across multiple servers, yet appear as local calls to developers. Inspired by Erlang’s distributed computing model, the system would create a seamless environment where developers can build applications that scale effortlessly, without worrying about the complexities of distributed systems. The core challenge is to develop a compiler or runtime system capable of identifying and switching between servers dynamically based on function calls, ensuring minimal overhead for the developer while maximizing system performance and scalability.

**Expected outcomes**:
 - A functional distributed mesh system that abstracts communication complexities for developers.
 - A compiler or runtime capable of identifying function placement on servers dynamically.
 - A scalable system that can be easily integrated into existing monolithic codebases.
 - Comprehensive documentation and a guide for integrating existing applications into the mesh architecture.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Jose Antonio Dominguez.

**Resources**:
 - MetaCall Express FaaS RPC Example: https://github.com/metacall/express-faas-rpc-example
 - MetaCall Protocol: https://github.com/metacall/protocol
 - MetaCall RPC Loader: https://github.com/metacall/core/tree/develop/source/loaders/rpc_loader

---

### 3. Code Coverage and Memory Tracking Improvements

**Skills**: C/C++, Debugging, Tooling, CI/CD, Low-level Instrumentation

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: High

**Description**:

This project aims to significantly improve code coverage reporting and memory tracking reliability across platforms. The current memory tracking mechanism is very basic and cannot detect leaks in detail, making debugging difficult and reducing developer productivity. Additionally, several tests fail on specific architectures such as ARM64 and PPC64, often without meaningful error messages, and these failures are hard to reproduce locally since they only appear in CI virtualized environments.

The project will explore extending support of existing tools such as Valgrind and AddressSanitizer (ASan) to improve memory leak detection, diagnostics, and reporting. In parallel, it will investigate and implement a custom lightweight instrumentation layer tailored to the project’s runtime, allowing fine-grained tracking of allocations, deallocations, and execution paths without destabilizing the application. A strong focus will be placed on observability, improving logs, traces, and error reporting in CI environments to make elusive bugs easier to detect and reproduce.

**Expected outcomes**:
 - Improved memory tracking system that reports leaks without crashing the application.
 - Better integration and evaluation of Valgrind and ASan for automated testing and diagnostics.
 - A custom code instrumentation mechanism for memory usage and code coverage tracking.
 - Enhanced observability in CI pipelines, especially for ARM64 and PPC64 architectures.
 - Clear, actionable error messages and documentation for debugging hard-to-reproduce issues.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Mostafa Wael Kamal.

**Resources**:
 - Sanitizer Setup: https://github.com/metacall/core/blob/a370a7f0fb7b1d70dec04d48d3e713e8fc3f1058/cmake/CompileOptions.cmake#L112
 - Valgrind Setup: https://github.com/metacall/core/blob/a370a7f0fb7b1d70dec04d48d3e713e8fc3f1058/source/tests/CMakeLists.txt#L55
 - Memory Tracker: https://github.com/metacall/core/blob/a370a7f0fb7b1d70dec04d48d3e713e8fc3f1058/source/reflect/include/reflect/reflect_memory_tracker.h

---

### 4. MetaCall Deploy and MetaCall FaaS Completion

**Skills**: TypeScript, Testing, CI/CD

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

This project focuses on completing and stabilizing the existing MetaCall Deploy and MetaCall FaaS (Function as a Service) infrastructure. Unlike previous years where MetaCall FaaS required a full reimplementation, the core functionality is now largely in place, and the remaining work consists of resolving pending issues, completing unimplemented features, and finalizing the developer workflow.

MetaCall FaaS enables developers to locally test cloud functions in an environment that closely mimics the production MetaCall FaaS platform. This is a critical component of the MetaCall ecosystem, as it allows developers to validate distributed polyglot applications before deployment. At the moment, the project has partial test coverage (9 tests passing, 6 pending), and several issues remain open that block a fully usable release.

The project will involve fixing failing and pending tests, polishing the TypeScript implementation, and improving the integration between MetaCall Deploy, MetaCall FaaS, and the MetaCall CLI. While the project is closely related to DevOps, it also requires hands-on work in the TypeScript codebase and coordination with MetaCall Protocol to ensure code reuse and consistency.

**Expected outcomes**:

 - Completion of pending features in MetaCall Deploy and MetaCall FaaS.
 - All tests passing, with improved test coverage and stability.
 - A reliable local FaaS environment for testing MetaCall projects.
 - Improved integration with MetaCall CLI for a smoother developer workflow.
 - Updated documentation describing usage, limitations, and deployment flow.

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Param Siddharth, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaCall FaaS (TypeScript): https://github.com/metacall/faas
 - MetaCall Deploy: https://github.com/metacall/deploy
 - MetaCall FaaS Dashboard: https://dashboard.metacall.io
 - MetaCall Protocol: https://github.com/metacall/protocol
 - Video - Deploying Functions into MetaCall FaaS: https://www.youtube.com/watch?v=2RAqTmQAWEc

---

### 5. MetaCall SSR (Server-Side Rendering) Server

**Skills**: Rust, TypeScript, React, Server-Side Rendering, CI/CD

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Medium

**Description**:

This project focuses on enhancing the MetaCall SSR (Server-Side Rendering) server, which allows high-performance React rendering on the backend across multiple programming languages. While the project has proven its potential in performance benchmarks, it currently faces a number of challenges, including failing tests and stability issues in development mode.

The goal is to stabilize the existing implementation, resolve bugs, and improve the overall developer experience. Key objectives include fixing the failing tests, addressing issues specific to development mode (such as hot reloading, error handling, and debugging), and making MetaSSR fully functional for building and deploying websites in a production environment.

The project will involve deep work in both Rust and TypeScript to ensure seamless integration between the languages. Additionally, it will improve the error reporting, enhance the testing framework, and streamline CI/CD workflows to ensure reliability and scalability for the MetaCall SSR server.

**Expected outcomes**:

 - A stable and fully functional MetaCall SSR server with a reliable development mode.
 - Fixed failing tests and improved test coverage.
 - Improved error handling and debugging experience.
 - Seamless integration of React on the backend with minimal friction in deployment.
 - Enhanced CI/CD pipelines for automated testing and deployment.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Gil Arasa Verge, Mostafa Wael Kamal, Alexandre Gimenez Fernandez, Param Siddharth, Jose Antonio Dominguez, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaSSR Repository: https://github.com/metacall/metassr
 - Previous work: https://github.com/metacall/gsoc-2023?tab=readme-ov-file#rust-actix--typescript-react-server-side-rendering-tsx-framework

---

### 6. Rust Loader Update

**Skills**: Rust

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Hard

**Description**:

Few years ago [Rust Loader was implemented](https://github.com/metacall/gsoc-2022?tab=readme-ov-file#rust-loader-support) but the code has became outdated due to nature of Rust Compiler unstable API / ABI. This year the code was cleaned, all dependencies were deleted and it was able to compile and run again inside the CI but the version of the compiler supported is still very old (nightly-2021-12-04). The idea of this project is to update to the latest version and add more tests and examples with tutorials. It will be also interesting to find a portable version, or at least to prevent depending on unstable Rust Compiler API (although I am not sure this is possible). Showing examples of mixing Rust and C++ would or script languages using Rust directly without need of using macros in the original Rust code would be also interesting, also [updating existing examples](https://github.com/metacall/python-rust-melody-example). Adding support for more types will be also interesting.

**Expected outcomes**: Implement a fully functional version of the Rust Loader with the latest compiler API. Extend the functionalities that are not implemented and provide more tests and examples with some tutorials about how to use it. Update existing tutorials using Rust Loader.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Thomas Rory Gummerson.

**Resources**:
 - MetaCall Rust Loader Code: https://github.com/metacall/core/tree/a370a7f0fb7b1d70dec04d48d3e713e8fc3f1058/source/loaders/rs_loader
 - Previous Work: https://github.com/metacall/core/issues/443

---

### 7. Implement Core C Support for CI & Distributables

**Skills**: GitHub Actions, C/C++, CMake Build System, Homebrew, Guix, Windows Package Managers

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

MetaCall Core has support for C by using `libffi`, `libclang` and `tcc`. This is widely tested in Linux on the `metacall/core` CI but lacks the implementation for MacOs and Windows. The objective of this project is to provide testing support in the Core for [Windows](https://github.com/metacall/core/pull/458) and [MacOs](https://github.com/metacall/core/pull/445) platforms, and once this is done we should implement this in the Distributables repositories. For this requirement, we will need to implement it in Guix (Linux), Homebrew (MacOs) and manually installing with Batch (Windows). It is not easy because the task requires knowledge of CMake build system and knowledge about different architectures. It willl be difficult but the final result of this is that we will be to bootstrap metacall itself with this. All the platforms will contain metacall.h and the metacall library and we can generate the API of metacall itself for multiples languages by using the C Loader. The explanation of this idea itself can be difficult because we are assuming some previous basic knowledge on MetaCall Core, but if you are intereseted you can ask in our chat groups for further explanation.

**Expected outcomes**: MacOs and Windows C Loader support in the Core and the distribution of the C Loader for Windows, MacOs and Linux. We should able to run things like: `metacall test.c`, once this is implemented.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Param Siddharth, Mostafa Wael Kamal, Raj Aryan.

**Resources**:
 - Previous Work: https://github.com/metacall/core/pull/458 & https://github.com/metacall/core/pull/445
 - Known Issues: https://github.com/metacall/core/issues/442
 - Guix `libclang`: https://git.savannah.gnu.org/cgit/guix.git/tree/gnu/packages/llvm.scm#n2160
 - Guix `tcc`: https://packages.guix.gnu.org/packages/tcc/
 - Guix `libffi`: https://packages.guix.gnu.org/packages/libffi

---

### 8. Implement Model Context Protocol (MCP) Support for MetaCall Deploy & FaaS

**Skills**: Artificial Intelligence, Model Context Protocol, Serverless Architectures, API Design, JSON, Context Management, Cloud Platforms, Python or TypeScript

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

This project aims to integrate the Model Context Protocol (MCP) into MetaCall’s Deploy and FaaS modules, enabling context-aware serverless function deployments. MCP facilitates sharing context between models, which is essential for AI/ML-driven workflows where models maintain or adapt their state across invocations. The integration will focus on storing and propagating context data across functions, allowing seamless state transfer in multi-runtime serverless environments.

The outcome will include a fully functional API for managing and sharing model context, along with middleware to handle context serialization and propagation in cloud-native environments. This functionality will be published as a reusable component, enabling other MetaCall users to deploy context-aware functions.

**Expected outcomes**:

 - Implement a minimal project that can be used for Claude or similar LLMs from Visual Studio Code or Antigravity that allows to deploy functions, list the existing ones, or run them locally in multiple languages.
 - Documentation and integration for the project in order to make it ready to use for other developers.
 - Testing for verifying that the tooling works and it's future proof.

**Possible mentors**: Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Param Siddharth, Mostafa Wael Kamal, Raj Aryan, Praveen Kumar.

**Resources**:

 - Model Context Protocol Documentation: https://modelcontextprotocol.io/docs/getting-started/intro
 - Model Context Protocol SDK: https://modelcontextprotocol.io/docs/sdk
 - MetaCall Deploy: https://github.com/metacall/deploy
 - MetaCall FaaS: https://github.com/metacall/faas
 - MetaCall Dashboard: https://metacall.io/dashboard
 - Video - Deploying Functions into MetaCall FaaS: https://www.youtube.com/watch?v=2RAqTmQAWEc

---

### 9. Extended Platform and Architecture Support for MetaCall

**Skills**: Cross-platform Development, C/C++, Build Systems, Shell Scripting (Bash), PowerShell, CI/CD, Toolchains

**Expected size of the project**: Medium (175 hours)

**Difficulty rating**: Medium

**Description**:

This project aims to significantly expand MetaCall’s platform and architecture support beyond its current scope. At present, MetaCall supports Linux across multiple architectures (amd64 variants, 386, arm, arm64, riscv64), Windows using the MSVC toolchain, and macOS on both Intel and Apple Silicon. While this already covers many use cases, there is strong interest in supporting additional platforms and environments to improve adoption and portability.

The main goal of this project is to add first-class support for new targets such as Windows via MinGW and Cygwin, as well as additional operating systems like Android and FreeBSD. This involves adapting the build and environment setup logic to correctly detect, configure, and compile MetaCall on these platforms.

A key constraint of the project is that all platform logic must be implemented inside the portable environment setup scripts ([./tools/metacall-environment.sh](https://github.com/metacall/core/blob/565bcbfd785442c2155a89661de0b2b0d125fdf3/tools/metacall-environment.sh) and [./tools/metacall-environment.ps1](https://github.com/metacall/core/blob/565bcbfd785442c2155a89661de0b2b0d125fdf3/tools/metacall-environment.ps1). This ensures that platform support is not tightly coupled to GitHub Actions or any specific CI provider, and that developers can reproduce builds locally with the same tooling used in CI.

In parallel, the project will design and add CI pipelines to automatically build and test MetaCall on all supported platforms and architectures. This will help catch platform-specific regressions early and improve overall reliability.

**Expected outcomes**:

 - Support for additional Windows environments, including MinGW and Cygwin.
 - Initial support for new platforms such as Android and FreeBSD.
 - Refactored and extended metacall-environment scripts to handle platform detection and setup in a portable way.
 - CI pipelines covering all supported platforms and architectures.
 - Documentation describing platform requirements, limitations, and setup instructions.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Thomas Rory Gummerson.

**Resources**:

 - MetaCall Environment Scripts:
   - https://github.com/metacall/core/blob/develop/tools/metacall-environment.sh
   - https://github.com/metacall/core/blob/develop/tools/metacall-environment.ps1
 - MetaCall Core Repository: https://github.com/metacall/core
 - Cross-compilation and Toolchain Documentation (GCC, Clang, MinGW, Android NDK)

---

### 10. Zig Port Implementation

**Skills**: Zig, Systems Programming, C

**Expected size of the project**: Small (90 hours)

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

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge.

**Resources**:
 - Prior Work: https://github.com/metacall/core/tree/5b592ac0e9a8e498e3e706623d0a788276f566e0/source/ports/zig_port
 - MetaCall Core: https://github.com/metacall/core
 - Zig Documentation: https://ziglang.org/documentation/master/

---

## Community Ideas

Ideas proposed by the community.

---

### 11. Modernize C# (.NET Core) Loader: Class Support, Pure Functions, and Type Expansion

**Skills**: C#, .NET Core Internals, C++, CMake, FFI

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

The current MetaCall C# (.NET Core) loader effectively handles static methods by treating them as global functions, but it lacks full object-oriented capabilities. Right now, it treats class static methods as isolated functions without supporting proper class instantiation. Furthermore, modern C# features like top-level statements are not fully supported.

This project aims to drastically modernize the C# loader's architecture. The primary objective is to implement proper support for C# classes (instantiation, instance methods, and state preservation) to bring it to feature parity with other MetaCall language loaders. Additionally, the project will update the loader to support pure functions (as seen in newer C# standards) and expand the list of supported interoperability types.

**Expected Outcomes**:
1. **Proper Class Support:** Refactor the loader to support full class instantiation and object state, rather than just treating class static methods as functions.
2. **Modern C# Standards:** Add support for pure functions and top-level statements.
3. **Type Expansion:** Extend the interop layer to support a wider array of complex data types between C++ and C#.
4. **Initialization Modernization (Stretch Goal):** Modernize the legacy CoreCLR initialization to use newer .NET Core hosting APIs (`hostfxr`) at the end of the project.

**Use Case Example**:

A developer wants to use a C# data processing library within a Python or Node.js backend. With proper class support, they can instantiate a C# `DataProcessor` object from Node.js, maintain its internal state (like loaded datasets) across multiple function calls, and utilize modern C# pure functions for high-performance calculations. Without this, the developer would be forced to use stateless static methods and pass the state manually every time.

**Possible Mentors:** Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge.

**Resources:**
* [MetaCall Core C# Loader Source](https://github.com/metacall/core/tree/master/source/loaders/cs_loader)
* [Microsoft Docs: Write a custom .NET Core host (hostfxr)](https://learn.microsoft.com/en-us/dotnet/core/tutorials/netcore-hosting)
* [Microsoft Docs: C# Top-level statements (Pure Functions)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/program-structure/top-level-statements)
* [Microsoft Docs: .NET Native interoperability (FFI)](https://learn.microsoft.com/en-us/dotnet/standard/native-interop/)

---

### 12. Redesign MetaCall Dashboard for MetaCall FaaS

**Skills**: TypeScript, React, UI/UX Design, Frontend Architecture, Accessibility

**Expected size of the project**: Medium (175 hours)

This project aims to integrate the MetaCall dashboard with MetaCall FaaS. The dashboard will allow developers to deploy functions, the local MetaCall FaaS server status, manage local deployments, test functions, and view logs effectively, improving the overall local developer experience.

The project focuses on redesigning a local MetaCall dashboard from scratch using React, TypeScript, Vite, and Tailwind CSS. The dashboard will integrate seamlessly with the MetaCall Protocol to support core local workflows. It will provide developers with a centralized interface to view system health, manage deployments, test functions, and inspect logs, making local development with MetaCall more efficient and user-friendly.

**Expected outcomes**:

 - A fully functional, MetaCall dashboard built with React and TypeScript.
 - Implementation of key views including deployment management, function testing, and logs viewer, settings, plan, login / signup.
 - Seamless integration with the local MetaCall FaaS server and MetaCall Protocol.
 - Clear documentation on how to set up and use the MetaCall dashboard.

**Possible mentors**: Thomas Rory Gummerson, Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Param Siddharth, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaCall FaaS Repository: https://github.com/metacall/faas
 - MetaCall Protocol Repository: https://github.com/metacall/protocol
 - MetaCall FaaS Dashboard (Reference): https://dashboard.metacall.io

---

### 13. MetaSSR CI/CD & Docs Improvements

**Skills**: Rust, TypeScript, React, Server-Side Rendering, CI/CD

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

MetaSSR is currently facing an issue with its CI pipeline. Specifically, the build step for package generation is failing, which prevents the integration tests from running successfully on macOS.

To investigate this, I explored the backend components involved in the process, including the package manager and the core MetaCall repository responsible for installing packages from specified locations. I downloaded and analyzed several packages from the packages repository and identified that the root cause lies in the packaging process—symlinks are not being created correctly on macOS. This misconfiguration leads to failures during the subsequent build steps.

To address this, I plan to fix the packaging process to ensure proper symlink creation on macOS. In addition, I will enhance the CI pipeline by introducing HTML validation checks both before and after hydration, ensuring that rendered HTML is properly tested.

**Expected Outcomes**:
 - The CI pipeline will successfully build packages on macOS without failures, ensuring that integration tests run reliably across all environments.
 - The brew-pkg packaging process will correctly generate symlinks, eliminating build-time issues and improving compatibility with macOS systems.
 - Integration of HTML testing (before and after hydration) using Chromium and Playwright will ensure that rendering behavior is validated, leading to higher confidence in SSR functionality.
 - The updated CI workflow will include proper browser setup and multiple validation checks, reducing flaky tests and catching issues earlier in the development cycle.

**Possible Mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Gil Arasa Verge, Mostafa Wael Kamal, Alexandre Gimenez Fernandez, Param Siddharth, Jose Antonio Dominguez, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaSSR Repository: https://github.com/metacall/metassr
 - MacOS Distributable: https://github.com/metacall/distributable-macos/releases/tag/v0.1.5
 - Core Repository: https://github.com/metacall/core
 - Brew-pkg Repository: https://github.com/metacall/brew-pkg

---

### 14. Fuzzing Engine for MetaCall Testing Center 

**Skills**: Python, Testing, CI/CD, FaaS, REST APIs 

**Expected size of the project**:  Small (90 hours) 

**Difficulty rating**: Medium

**Description**:

MetaCall currently has no automated way to stress test its polyglot runtime across languages. Bugs in cross-language type coercion are invisible until users hit them in production. The testing-center repository exists for running examples but lacks any fuzzing support, macOS coverage, or cross-language boundary testing. 

This project builds a fuzzing engine integrated into testing-center that automatically generates thousands of type-aware test cases, tests cross-language function calls (Python → JS → Ruby), and detects crashes or unexpected behavior before they reach production. 

Unlike simple random testing, the fuzzer will inspect deployed function signatures via /api/inspect and generate inputs based on the actual parameter types of each language — handling edge cases like None/null/NaN/Infinity across language boundaries. 

**Expected outcomes**:

- A Python-based fuzzing engine that auto-inspects deployed function signatures via /api/inspect and generates type-aware random inputs.
- Cross-language fuzzing chains (Python => JS => Ruby => TypeScript) that stress test the polyglot runtime at language boundaries.
- Automatic detection and reporting of exact inputs that cause crashes or unexpected behavior.
- Extended platform coverage, Windows, macOS and Docker test environments.
- CI pipeline integration into testing-center for automated runs on every MetaCall release.
- Documentation for contributors to extend the fuzzer with new language types and test cases.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Param Siddharth, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaCall FaaS Repository: https://github.com/metacall/faas
 - MetaCall Protocol Repository: https://github.com/metacall/protocol
 - MetaCall Testing Center Repository: https://github.com/metacall/testing-center/

---

### 15. Direct `metacall/core` C API Model Context Protocol (MCP) Server

**Skills**:  Artificial Intelligence, Model Context Protocol, C, Systems Programming, IPC (stdio), JSON-RPC, CMake

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Medium

**Description**:

This project aims to integrate the Model Context Protocol (MCP) into MetaCall’s core module's C API. The other MCP in project 8 is meant for faas and deploy modules; while excellent for cloud deployments, that requires a running server, introduces network latency, and is heavy for local AI-assisted coding. This project builds a lightweight, native MCP server written entirely in C that links directly against `libmetacall.so` and communicates over standard input/output (stdio).

By exposing MetaCall's core runtime directly to AI agents (like GitHub Copilot or Claude Desktop), developers can allow LLMs to load scripts, execute functions, and inspect code across multiple languages (Python, Node.js, Ruby, etc.) entirely locally and in-process. 

This project requires real systems programming. The server must parse JSON-RPC 2.0 messages from stdin, dispatch them to tool handlers, perform complex bidirectional type conversions between JSON and the `metacall_value` type system, and carefully manage memory allocations to prevent leaks during continuous agent sessions.

**Expected outcomes**:
 - A standalone C binary implementing the MCP protocol over stdio, directly linked against the MetaCall C API.
 - Core MCP tools implemented: `load`, `call`, `inspect`, and `eval` (inline code evaluation).
 - A robust type-conversion layer bridging JSON and MetaCall's internal value system (handling primitives, arrays, maps, and error types).
 - A CMake build system that cleanly resolves standard library paths, supporting both native and Dockerized execution.
 - Unit and end-to-end tests verifying JSON-RPC parsing, memory safety, and multi-language execution.
 - Integration documentation and configuration examples for VS Code, Claude Desktop, Google Antigravity and Cursor.

**Possible mentors**: Jose Antonio Dominguez, Alexandre Gimenez Fernandez, Param Siddharth, Mostafa Wael Kamal, Raj Aryan, Praveen Kumar, Vicente Eduardo Ferrer Garcia.

**Resources**:
 - MetaCall C API Documentation: https://github.com/metacall/core/blob/develop/source/metacall/include/metacall/metacall.h
 - MetaCall Value Types: https://github.com/metacall/core/blob/develop/source/metacall/include/metacall/metacall_value.h
 - Model Context Protocol Specification: https://modelcontextprotocol.io/docs/concepts/architecture
 - MCP Transports (stdio): https://modelcontextprotocol.io/docs/concepts/transports
 - cJSON (Vendored JSON parser): https://github.com/DaveGamble/cJSON

---

### 16. Metacircular Self-Registration of MetaCall API

**Skills**: C/C++, C Loader, Build Systems, API Design, Tooling

**Expected size of the project**: Small (90 hours)

**Difficulty rating**: Hard

**Description**:

MetaCall currently exposes its C API through `metacall.h`, but language ports still replicate wrapper logic in each target language. This project focuses on the metacircular path told by sir Vicente: make MetaCall capable of registering/exposing its own API through the C loader pipeline, then validate it through tests and one language-port migration.

The work is based on the `_ex` load API data propagation and then extends C loader support for extra options required to load MetaCall itself.

This is important because current per-language wrappers duplicate equivalent glue code and are harder to keep aligned when core APIs evolve. A metacircular path reduces drift between ports and lowers the long-term maintenance cost of adding or updating language integrations.

**Expected outcomes**:
 - Update the loader plugin API in order to pass data in the last parameter (based on `_ex` path work).
 - Allow C loader to receive a map value and pass additional options (include/library search paths, compiler options).
 - Implement `metacall_c_metacall_test` with the new API, passing to C loader the MetaCall folders.
 - Define a standard startup strategy to read MetaCall type info at initialization (package C loader where available, or codegen stubs for self-registration, bindgen-like direction).
 - Update NodeJS or Python port to the newer metacircular API.

**Possible mentors**: Vicente Eduardo Ferrer Garcia, Fernando Vaño Garcia, Gil Arasa Verge, Thomas Rory Gummerson.

**Resources**:
 - Tracker Issue: https://github.com/metacall/core/issues/715
 - Target test path: https://github.com/metacall/core/blob/develop/source/tests/metacall_c_metacall_test/source/metacall_c_metacall_test.cpp

---

### 17. MetaSSR: Stabilization and FaaS Function Mesh Integration

**Skills**: Rust, TypeScript, React, Server-Side Rendering, Distributed Systems, CI/CD

**Expected size of the project**: Large (350 hours)

**Difficulty rating**: Medium

**Description**:

MetaSSR is a high-performance, Rust-based server-side rendering framework built on the MetaCall polyglot runtime. While it currently outperforms Node.js alternatives in raw benchmarks, it is blocked from production adoption by failing test suites, hot reload instability in development mode, and poor error propagation.

This project has two phases. The first stabilizes the existing framework by resolving these blockers and establishing a reliable CI/CD baseline. The second transforms MetaSSR from a standard HTTP-based SSR server into a native worker node within the MetaCall function mesh by implementing a FaaS protocol adapter. The adapter wires `/inspect` and `/call` endpoints — already defined in the MetaCall rpc_loader and FaaS protocol — into MetaSSR's Axum server layer. Incoming FaaS payloads are handed off to the MetaCall C core for execution via the existing Rust port. Workers are scaled at the infrastructure level via Kubernetes pods, keeping MetaSSR's internal architecture unchanged. The commercial MetaCall FaaS achieves this with C++ nodes; this project delivers the open-source Rust equivalent.

**Expected outcomes**:
 - Fixed failing CI tests and a stable, well-documented baseline for MetaSSR.
 - Resolved development mode issues including hot reload, error handling, and debugging.
 - `/inspect` and `/call` endpoints implemented in MetaSSR's Axum server layer, conforming to the MetaCall FaaS protocol.
 - FaaS payloads wired to the MetaCall C core for execution via the existing Rust port.
 - Integration tests validating MetaSSR as a functional node in a multi-node function mesh setup.
 - A benchmark comparing a single Node.js/Express monolith against a distributed tree of MetaSSR nodes communicating via rpc_loader, covering CPU-bound and I/O-bound scenarios.
 - Documentation covering the adapter API, deployment model, and Kubernetes-based scaling.

**Possible mentors**: Thomas Rory Gummerson, Vicente Eduardo Ferrer Garcia, Gil Arasa Verge, Mostafa Wael Kamal, Alexandre Gimenez Fernandez, Param Siddharth, Jose Antonio Dominguez, Raj Aryan, Praveen Kumar.

**Resources**:
 - MetaSSR Repository: https://github.com/metacall/metassr
 - Function Mesh Architecture: https://medium.com/@metacall/function-mesh-architecture-c0304ba4bad0
 - rpc_loader Implementation: https://github.com/metacall/core/blob/develop/source/loaders/rpc_loader
 - MetaCall Protocol: https://github.com/metacall/protocol
 - MetaCall FaaS (Node.js reference): https://github.com/metacall/faas
 - Function Mesh Discussion (issue #114): https://github.com/metacall/metassr/issues/114

 --- 

## Find Us

The three chats are bridged by Matrix (messages sent from one, on the main room/channel, can be seen from all).

 - Telegram:
  <a href="https://t.me/joinchat/BMSVbBatp0Vi4s5l4VgUgg" alt="Telegram"><img src="https://img.shields.io/static/v1?label=metacall&message=join&color=blue&logo=telegram&style=flat" /></a>

 - Discord:
  <a href="https://discord.gg/upwP4mwJWa" alt="Discord"><img src="https://img.shields.io/discord/781987805974757426?label=discord&style=flat" /></a>

 - Matrix:
  <a href="https://matrix.to/#/#metacall:matrix.org" alt="Matrix"><img src="https://img.shields.io/matrix/metacall:matrix.org?label=matrix&style=flat" /></a>

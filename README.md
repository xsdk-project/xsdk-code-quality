# xSDK Code Quality Tools

The goal of this project is to facilitate the use of both general-purpose and custom code analysis tools with the goal of improving the quality of software developed in the DOE xSDK ECP project, as well as more broadly within the high-performance applications community. 

## 1. General-purpose tools

Many commercial and open-source projects provide various code analysis capabilities that can be used to 
detect various problems, ranging from style to correctness and performance. 

Here we focus on widely available open-source tools which can be deployed easily in HPC software projects without requiring significant modifications to existing development processes. 

### 1.1 Clang analyzer 

Perhaps the easiest code checker to integrate is the [Clang analyzer](https://clang-analyzer.llvm.org). In particular,
the `scan-build` command allows non-intrusive integration of 
code checks into existing builds (including parallel builds). The `scan-build` [documentation](https://clang-analyzer.llvm.org/scan-build.html)
provides a great starting point for developers wishing to integrate code quality checks into their workflows. 

### 1.2 Clang-tidy

The `clang-tidy` tool provides an extensible framework for diagnosing and
fixing a variety of typical programming errors. The [documentation](https://clang.llvm.org/extra/clang-tidy/) 
includes several examples of command-line invocation, as well as a list of all available checkers. 

## 2. Custom code analysis tools

While general tools provide valuable functionality in detecting a variety of problems, most projects also have unique requirements in terms of coding conventions. In our tools, we aim to enable such custom analyses through [static](https://github.com/HPCL/code-analysis/tree/main/src/static) and [dynamic](https://github.com/HPCL/code-analysis/tree/main/src/dynamic) code analysis tools based on the open-source LLVM compiler framework.

Our static analysis approach extends clang-tidy, while our dynamic approach relies on the Python bindings
of the llibClang interfaces to the abstract syntax tree (AST) program representation.

Well documented projects, such as [PETSc](https://petsc.org/release/developers/style/), have a set of coding rules that are included as part of the developer documentation or contributor style guide. In addition to lowering the learning curve related to the project's source code organization for new developers, having style rules helps clarify semantic aspects of the code in question. For example, in projects written in languages without mechanisms for controlling encapsulation and polymorphism, such as C, coding conventions are the only way in which software can be designed using object-oriented principles.  As a consequence, violating these styles and conventions affects not only code maintainability, but could result in serious bugs. Even languages that provide support for data protection and other design tools, more domain-specific design rules almost inevitably can improve the overall code organization and enable a wider range of contributions without sacrificing quality or maintainability.

To ease the burden of manually verifying that new codes obey the project's style and structure requirements, we have implemented a number of analyses for PETSc developer rules, which can be used as starting points for developing future custom rules for other C projects. We will also add examples for Fortran and C projects in the near future in the same repositories. 

## 3. Getting Started

To clone this repository and all its submodules (recommended), use the following command:

```
git clone --recurse-submodules --remote-submodules https://github.com/xsdk-project/xsdk-code-quality.git
```

To update a previously cloned copy, including all its submodules, do this in the `xsdk-code-quality` top-level directory:

```
git pull --recurse-submodules
```

To obtain clone a specific release, clone the corresponding tag, e.g.,  for version 1.0.0:

```
git clone -b v1.0.0  --depth 1 --recurse-submodules --remote-submodules https://github.com/xsdk-project/xsdk-code-quality.git
```

All available versions:  https://github.com/xsdk-project/xsdk-code-quality/tags

(Containerized distribution coming soon!)

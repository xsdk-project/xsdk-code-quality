# Code Quality Tools

The goal of this project is to facilitate the use of both general-purpose and custom code analysis tools with the 
goal of improving the quality of software developed in the DOE xSDK ECP project, as well as more broadly within 
the high-performance applications community. 

## General-purpose tools

Many commercial and open-source projects provide various code analysis capabilities that can be used to 
detect various problems, ranging from style to correctness and performance. 

Here we focus on widely available open-source tools which can be deployed easily in HPC software projects without
requiring significant modifications to existing development processes. 

### Clang analyzer 

Perhaps the easiest code checker to integrate is the [Clang analyzer](https://clang-analyzer.llvm.org). In particular,
the `scan-build` command allows non-intrusive integration of 
code checks into existing builds (including parallel builds). The `scan-build` [documentation](https://clang-analyzer.llvm.org/scan-build.html)
provides a great starting point for developers wishing to integrate code quality checks into their workflows. 

### Clang-tidy

The `clang-tidy` tool provides an extensible framework for diagnosing and
fixing a variety of typical programming errors. The [documentation](https://clang.llvm.org/extra/clang-tidy/) 
includes several examples of command-line invocation, as well as a list of all available checkers. 

## Custom code analysis tools

While general tools provide valuable functionality in detecting a variety of problems, most projects also have 
unique requirements in terms of coding conventions. In our tools, we aim to enable such custom analyses through
[static](https://github.com/HPCL/code-analysis/tree/main/src/static) and [dynamic](https://github.com/HPCL/code-analysis/tree/main/src/dynamic)
code analysis tools based on the open-source LLVM compiler framework.

Our static analysis approach extends clang-tidy, while our dynamic approach relies on the Python bindings
of the LibClang interfaces to the abstract syntax tree program representation.

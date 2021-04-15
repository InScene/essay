# Style Guides
Inspired by [Google Style Guides](https://github.com/google/styleguide).

To ensure consistency throughout the source code, keep these rules in mind as you are working:
1. All features or bug fixes **must be tested** by one or more specs (unit-tests).
2. All public API methods **must be documented**. (Details TBC).

 - [C](#cc)
 - [C++](#cpp)
 - [Java](#java)
 - [C#](#cs)
 - [Python](#py)
 - [Shell](#sh)
 - [Kotlin](#kt)
 - [Golang](#go)
 - [Git](#git)
 
 
## <a name="cc"></a> C
See [C++](#cpp).

### Conventional
* Follow the the guide style for [C++](#cpp) with following additional configuration:
* 
### Layout
* Follow the the guide style for [C++](#cpp) with following additional configuration:


## <a name="cpp"></a> C++
### Conventional
* We follow [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html).

### Layout
* See [Project Layout](https://api.csswg.org/bikeshed/?force=1&url=https://raw.githubusercontent.com/vector-of-bool/pitchfork/develop/data/spec.bs).

### Lint
* Use [cpplint.py](https://pypi.org/project/cpplint/) to detect style errors, see [code](https://raw.githubusercontent.com/google/styleguide/gh-pages/cpplint/cpplint.py) with the cpplint.py tool.

> cpplint.py is a tool that reads a source file and identifies many style errors. It is not perfect, and has both false positives and false negatives, but it is still a valuable tool. False positives can be ignored by putting // NOLINT at the end of the line or // NOLINTNEXTLINE in the previous line.

### Format
* Use [clang-format](https://clang.llvm.org/docs/ClangFormat.html) tool.

### Compiler
See [Compiler User Guide](https://www.keil.com/support/man/docs/armclang_intro/default.htm) for the complete option list.

1. [Using Common Compiler Options](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_mtw1469708501316.htm)
   * [Selecting source language options](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_sir1472741527970.htm)
   * [Selecting optimization options](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_fnb1472741490155.htm)
2. [Writing Optimized Code](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_oph1469708556921.htm)
   * [Effect of the volatile keyword](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_chr1385110934192.htm)
   * [Optimizing loops](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_hpz1474359444075.htm)
   * [Inlining functions](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_kff1474359729131.htm)
   * [Stack use in C and C++](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_hla1474359990839.htm)
3. [Embedded Software Development](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_lfh1505904047779.htm)
   * [Default memory map](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_clm1505906242639.htm)
   * [Run-time memory models](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_ldq1505906267474.htm)
   * [The vector table](https://www.keil.com/support/man/docs/armclang_intro/armclang_intro_kqu1505906156419.htm)


### Installation
Some projects have instructions on how to run cpplint.py from their project tools.
If the project you are contributing to does not, you can download cpplint.py separately.
* Under the Eclipse IDE use [CppStyle](https://github.com/wangzw/CppStyle). An Eclipse plugin that integrates the clang-format tool as an alternative C/C++ code formatter and checks C++ coding style 

> To configure Cpplint  checker for C go to **Code Analysis** in **Perference -> C/C++ -> Code Analysis -> Cpplint Issues** globally, or in **Project property -> C/C++ General -> Code Analysis -> Cpplint Issues** for a C/C++ project.
Double click **Build -> deprecated** page **Scope** and add **\*.c** in **Inclusion patterns** property.

###### Lint under Windows
Open Command Prompt as Administrator and run:
```shell
easy_install cpplint
````
###### Lint under Linux
To install [cpplint](https://github.com/cpplint/cpplint) from PyPI, run:
```shell
pip install cpplint
````


## <a name="java"></a> Java
### Conventional
* We follow [Google's Java Style Guide](https://google.github.io/styleguide/javaguide.html).


## <a name="cs"></a> C#
### Conventional
* We follow [Google's C# Style Guide](https://google.github.io/styleguide/csharp-style.html).


## <a name="py"></a> Python
### Conventional
* We follow [Google's Python Guide](https://google.github.io/styleguide/pyguide.html).


## <a name="sh"></a> Shell
### Conventional
* We follow [Google's Shell Style Guide](https://google.github.io/styleguide/shellguide.html).


## <a name="kt"></a> Kotlin
### Conventional
* We follow [Android's Kotlin Style Guide](https://developer.android.com/kotlin/style-guide).

### Lint
* Use [Kotlin Lint Inspections](https://developer.android.com/studio/write/lint#manuallyRunInspections) to detect style errors.

### Guide
* Learn Kotlin with [Getting Started](https://kotlinlang.org/docs/reference/).


## <a name="go"></a> Golang
### Conventional
* We follow [Effective Go](https://golang.org/doc/effective_go).
* We follow [Golang's Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments).

### Lint
* See [Awesome Go Linters](https://github.com/golangci/awesome-go-linters) to find linter and formater.

### Format
* Use [gofmt](https://golang.org/cmd/gofmt/) tool.
* Use [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports) tool.

### Commentary
* See [godoc](https://golang.org/doc/effective_go#commentary).

### Layout
* See [Project Layout](https://github.com/golang-standards/project-layout).
* See [Project Layout Generator](https://github.com/insidieux/inizio/tree/v1.1.1).

### Visualisation
#### `Charts/Plots`
* See [go-echarts](https://github.com/go-echarts/go-echarts).
* See [go-chart](https://github.com/wcharczuk/go-chart).
* See [Statsview](https://github.com/go-echarts/statsview).
* See [Gonum Plot](https://github.com/gonum/plot).
#### `GUI`
* See [Go GUI Projects](https://github.com/go-graphics/go-gui-projects).

### Editor
* See [Visual Studio Code](https://code.visualstudio.com/download).


## <a name="git"></a> Git
### Conventional
* We follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.

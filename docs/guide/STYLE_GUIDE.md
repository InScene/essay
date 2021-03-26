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
### Conventional
* Follow the the guide style for [C++](#cpp) with following additional configuration:

## <a name="cpp"></a> C++
### Conventional
* We follow [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html).

### Lint
* Use [cpplint.py](https://pypi.org/project/cpplint/) to detect style errors, see [code](https://raw.githubusercontent.com/google/styleguide/gh-pages/cpplint/cpplint.py).
with the cpplint.py tool.

> cpplint.py is a tool that reads a source file and identifies many style errors. It is not perfect, and has both false positives and false negatives, but it is still a valuable tool. False positives can be ignored by putting // NOLINT at the end of the line or // NOLINTNEXTLINE in the previous line.

### Format
* Use [clang-format](https://clang.llvm.org/docs/ClangFormat.html) tool.

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
* We follow [Golang's Code Review Comments](https://github.com/golang/go/wiki/CodeReviewComments).

### Lint & Format
* See [Awesome Go Linters](https://github.com/golangci/awesome-go-linters) to find linter and formater.

## <a name="git"></a> Git
### Conventional
* We follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.

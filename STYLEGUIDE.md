# Style Guides
Forked from [Google Style Guides](https://github.com/google/styleguide).

To ensure consistency throughout the source code, keep these rules in mind as you are working:
1. All features or bug fixes **must be tested** by one or more specs (unit-tests).
2. All public API methods **must be documented**. (Details TBC).

 - [C](#cc)
 - [C++](#cpp)
 - [Java](#java)
 - [C#](#cs)
 - [Python](#py)
 - [Shell](#sh)
 
## <a name="cc"></a> C
###### TODO

## <a name="cpp"></a> C++
* We follow [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html).
* Use [cpplint.py](https://pypi.org/project/cpplint/) to detect style errors, see [code](https://raw.githubusercontent.com/google/styleguide/gh-pages/cpplint/cpplint.py).
```
cpplint.py is a tool that reads a source file and identifies many style errors.
It is not perfect, and has both false positives and false negatives, but it is still a valuable tool.
False positives can be ignored by putting // NOLINT at the end of the line or // NOLINTNEXTLINE in the previous line.

Some projects have instructions on how to run cpplint.py from their project tools.
If the project you are contributing to does not, you can download cpplint.py separately.
```

## <a name="java"></a> Java
* We follow [Google's Java Style Guide](https://google.github.io/styleguide/javaguide.html).

## <a name="cs"></a> C#
* We follow [Google's C# Style Guide](https://google.github.io/styleguide/csharp-style.html).

## <a name="py"></a> Python
* We follow [Google's Python Guide](https://google.github.io/styleguide/pyguide.html).

## <a name="sh"></a> Shell
* We follow [Google's Shell Style Guide](https://google.github.io/styleguide/shellguide.html).

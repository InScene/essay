# Coding Rules

To ensure consistency throughout the source code, keep these rules in mind as you are working:

* All features or bug fixes **must be tested** by one or more specs (unit-tests).
* All public API methods **must be documented**. (Details TBC).

- [C](#cc)
- [C++](#cpp)
- [JavaScript](#js)
 
## <a name="cc"></a> C

## <a name="cpp"></a> C++
* We follow [Google's C++ Style Guide](https://google.github.io/styleguide/cppguide.html).
* Use [cpplint.py](https://raw.githubusercontent.com/google/styleguide/gh-pages/cpplint/cpplint.py) to detect style errors.
```
cpplint.py is a tool that reads a source file and identifies many style errors. It is not perfect, and has both false positives and false negatives, but it is still a valuable tool. False positives can be ignored by putting // NOLINT at the end of the line or // NOLINTNEXTLINE in the previous line.

Some projects have instructions on how to run cpplint.py from their project tools. If the project you are contributing to does not, you can download cpplint.py separately.
```
  
## <a name="js"></a> JavaScript
* We follow [Google's JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html), but wrap all code at
  **100 characters**. An automated formatter is available, see
  [DEVELOPER.md](https://github.com/angular/angular/blob/22b96b96902e1a42ee8c5e807720424abad3082a/docs/DEVELOPER.md#clang-format).

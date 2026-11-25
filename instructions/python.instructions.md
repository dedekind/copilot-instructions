---
description: "Use when creating or editing Python files. Covers Python conventions and tests."
applyTo: "**/*.py"
---

# Python Style

- Capitalize messages at the start and after every colon. One-line messages have no final period.
  Multi-line messages use periods.
- Prefer module imports, such as `from X import Mod` followed by `Mod.symbol`. Exceptions include
  error classes, `typing` symbols, and established ecosystem patterns such as pandas.
- Do not rename modules on import. Follow Ruff isort formatting: sorted imports, and parenthesized
  one-name-per-line imports when a line exceeds 100 characters.
- Use `TypedDict(total=False)` when building a dictionary key by key.
- Use `frozenset()` or `tuple()` for module constants, not `set()` or `list()`. Prefer immutable
  collections generally.
- Use `snake_case` for class attributes. Reserve `ALL_CAPS` for module-level constants.
- In pepclibs, use `_sysfs_io` methods for file I/O.
- Add a blank line between class methods.
- Prefix errors for impossible states with `BUG:`.
- Use keyword arguments when calling methods, in the same order as the signature.
- Use backslash continuation only outside parentheses, never inside them.
- Do not add a blank line before `except`, `finally`, or `else`.
- Use `Trivial.str_to_int()` or `Trivial.str_to_num()` instead of `int()` or `float()`.
- Use `""`, `()`, or `-1` instead of `None` for defaults, as appropriate.
- Use `raise SystemExit(code)`, not `sys.exit()`, and always pass the exit code.
- Use `close()` for resource cleanup, not `__del__()`. Use `__del__()` only with a specific,
  well-justified reason because its timing is non-deterministic and it silently swallows exceptions.
- Inherit context managers from `ClassHelpers.SimpleCloseContext` instead of defining
  `__enter__()` and `__exit__()` manually.
- Prefer `pathlib.Path` and its methods over `os` and `os.path`, unless repeated conversions make
  strings clearer.
- Avoid `next()` on generators. For one value, use a `for` loop with `return` and a trailing
  `raise`. For a default on an empty iterator, use `for`/`break`/`else`. If `next()` is unavoidable,
  pass a default or handle `StopIteration` explicitly.
- Do not use separator comments to divide files or classes. Refactor code that needs them.

## Function Calls And Logging

- Fit as many arguments as possible on the first line of a call. Align continuation lines with
  the character after the opening parenthesis.
- Keep a log call on one line when it fits. For a long call, put all arguments on continuation
  lines unless keeping some on the first line saves a line.

## Strings

- Maximize the first line length of a multi-line string, aiming for 95 to 100 characters.
- Put each continuation line in its own string literal, aligned with the opening quote. If the
  string starts as an f-string, give every continuation literal an `f` prefix, even without
  placeholders.
- Outside parentheses, use a backslash for string continuation. Inside parentheses, rely on
  implicit concatenation and do not use a backslash.

## Error Handling And Assertions

- When re-raising the same semantic error, use `type(err)(...)` to preserve its subclass.
- When deliberately changing the error type, raise the target type and document it in `Raises:`.
- Align a continued `assert` message at the indentation level plus seven columns.

## Function Signatures

Keep a fitting signature on one line. Otherwise, put one parameter on each line and align
continuations with the first parameter. For a long return type, use a backslash continuation and
align the type at a four-character boundary near column 100.

```python
def method(self,
           param1: int,
           param2: str): ...

def read_features(self,
                  fnames: Sequence[str],
                  cpus: Sequence[int]) -> \
                       Generator[tuple[int, dict[str, FeatureValueType]], None, None]:
```

## Docstrings

Use Google style and imperative voice, for example, `"""Return ..."""` rather than
`"""This method returns ..."""`. Use this order: summary, blank line, `Args:`, `Returns:` or
`Yields:`, `Raises:`, `Notes:`, and `Examples:`.

- Put one-line docstrings on one line. Put opening and closing quotes for multi-line docstrings on
  their own lines, with a blank line before the function body.
- Refer to callables as `'configure()'` and non-callables as `'outdir'` or `'_pman'`.
- For helper wrappers, write `Arguments are the same as in 'main_function()'`, ending the sentence
  with a period.
- Do not repeat types in `Args:`, `Returns:`, or `Yields:`. The signature already gives the type.
- Keep long descriptions short. Put details in `Notes:` bullets and use `Examples:` for concrete
  cases.
- List only `Error` subclasses in `Raises:`, never `Error` itself. Describe the error
  declaratively, not as an "if" clause.
- Align continuation text in docstring sections two columns after the colon.

## Type Annotations

- Import typing utilities under `TYPE_CHECKING`. Use `import typing` and
  `if typing.TYPE_CHECKING:`.
- Guard `cast()` calls with `if typing.TYPE_CHECKING:` as well.
- Use the least restrictive collection type: `Iterable[T]` for one pass, `Sequence[T]` when
  indexing or iterating multiple times, and `list[T]` only when mutation is required.
- Omit the return annotation when a method returns `None`.

## Operators And Dictionaries

- Put spaces around arithmetic, comparison, and assignment operators.
- Do not put spaces in keyword arguments, for example, `func(name="value")`.
- Put spaces after dictionary colons, never before them. Extra spaces after colons are acceptable
  for alignment.

## Tests

- Put each private helper `_foo()` immediately before its public `test_foo()`. Do not group all
  helpers at the top and public test functions at the bottom.
- Use `pytest.skip("reason")` when a platform or topology condition is not met. Never use a bare
  `return` as a silent skip.

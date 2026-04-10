# Tugas 7: setup.cfg dengan Konfigurasi Testing

## GitHub Repository URL:

```
https://github.com/Pangpang0255/ci-cd-final-project/blob/main/setup.cfg
```

## File setup.cfg Content:

```ini
[nosetests]
verbosity = 2
with-xunit = true
xunit-file = test-results.xml
with-xcoverage = true
xcoverage-file = coverage.xml
cover-package = src
nocapture = false
cover-erase = true
cover-branches = true
cover-min-percentage = 80

[coverage:run]
source = src
omit =
    */tests/*
    */test_*.py
    */__pycache__/*
    */site-packages/*

[coverage:report]
exclude_lines =
    pragma: no cover
    def __repr__
    raise AssertionError
    raise NotImplementedError
    if __name__ == .__main__.:
    if TYPE_CHECKING:
    @abstractmethod
    @abc.abstractmethod
skip_covered = false
skip_empty = false

[flake8]
max-line-length = 120
extend-ignore = E203, W503, E501, E701
exclude =
    .git,
    __pycache__,
    docs,
    build,
    dist,
    .venv,
    venv,
    node_modules,
    .pytest_cache,
    .coverage,
    htmlcov
per-file-ignores =
    __init__.py:F401
    tests/*:F401,F841

[pylint]
max-line-length = 120
disable =
    missing-docstring,
    too-few-public-methods,
    import-error,
    unused-import,
    invalid-name,
    line-too-long
load-plugins = pylint.extensions.docparams
```

## Fitur yang Dikonfigurasi:

✅ **nosetests Configuration:**

- Verbosity level 2
- XUnit output untuk CI/CD integration
- Coverage reporting dengan xcoverage
- Coverage minimum 80%

✅ **Coverage Configuration:**

- Source directory: src/
- Exclusion untuk test files dan **pycache**
- Custom exclude lines untuk generated code

✅ **Flake8 Configuration:**

- Max line length: 120 characters
- Ignore common style issues (E203, W503)
- Exclude build directories dan virtual environments

✅ **Pylint Configuration:**

- Max line length: 120 characters
- Disable rules yang tidak perlu untuk project ini
- Load extensions untuk better code analysis

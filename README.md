# ciotest
Continuum test suite helper


```bash
usage: ciotest [-h] [--format] [--staged] [--profile] [--pytestqt] module

Run Continuum IO test suite.

positional arguments:
  module

optional arguments:
  -h, --help  show this help message and exit
  --format    Only run the linters and formatters not the actual tests
  --staged    Only run the linters and formatters on files added to the commit
  --profile   Profile the linter and formatter steps
  --pytestqt  If using pytestqt, qtpy is imported first to avoid qt shim issues.
```

# Example config file
Configuration is saved in a single file named `.ciocheck`

```config
# -----------------------------------------------------------------------------
# Flake 8
# http://flake8.readthedocs.io/en/latest/config.html
# -----------------------------------------------------------------------------
[flake8]
exclude = tests/*
ignore = E126,E401
max-line-length = 79
max-complexity = 10

# -----------------------------------------------------------------------------
# PEP257
# https://pep257.readthedocs.io/en/latest/usage.html#example
# -----------------------------------------------------------------------------
[pep257]
add-ignore = D203
inherit = false

# -----------------------------------------------------------------------------
# Coverage RC to control coverage.py
# http://coverage.readthedocs.io/en/latest/config.html
# -----------------------------------------------------------------------------
[run]
omit = tests/*

[report]
fail_under = 100
show_missing = true
skip_covered = true

[html]
directory = coverage_html_report

# -----------------------------------------------------------------------------
# YAPF
# https://github.com/google/yapf#formatting-style
# -----------------------------------------------------------------------------
[style]
based_on_style = pep8
column_limit = 79
spaces_before_comment = 2
split_before_logical_operator = true
```

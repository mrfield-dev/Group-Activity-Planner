# ADR 0001: Python Version

**Status:** Proposed\
**Date:** 2026-10-17\
**Deciders:** Max Field, Oli Kay

## Context and Problem Statement

Before beginning the development of the backend structure and skeleton, a python version must be selected and committed to from all developers to prevent "Works on my machine" issues. A 25 minute spike has been researched by Max Field, and the findings presented to Oli Kay for discussion.


## Decision Drivers
- Ecosystem support
- Dev container image availability
- Security / bugfix support remaining
- Useful features

## Considered Options
- Python 3.14
- Python 3.15

## Decision outcome
**Selected: Python 3.14** - Since Python 3.15 was released 8 days prior to this ADR, the newest version lacks the availability of some ecosystem support and an official dev container image at the time of this report. Python 3.14 has had these available for almost a year, with demonstrated stability.

## Consequences
### Good
- All dependencies are installed from pre-built wheels (.whl), reducing the time for setup compared to the source distribution (.tar.gz) which contains the raw source code and must be built on the local machine first, potentially requiring compilers.
- Microsoft shipped an official devcontainer image for Python 3.14, keeping the dev environment standard and low-maintenance.
- 3.14 is in bugfix support, with approx. 4 years support remaining.

### Bad
- We lose out on 3.15's new features, such as Lazy imports (https://docs.python.org/3/whatsnew/3.15.html)
- Future upgrade will be required (Low-cost issue, see below.)

## When / How To Revisit
**Revisit when:** `cp315` wheels exist for our compiled dependencies and an official 3.15 devcontainers image is published (review at the Sprint 4 retro).

**Upgrade path:** change `.python-version`, the dev container image tag and the CI Python version, then regenerate `uv.lock`.


## More Information

- [Status of Python versions](https://devguide.python.org/versions/)
- [PEP 790 – Python 3.15 release schedule](https://peps.python.org/pep-0790/)
- [What's new in Python 3.15](https://docs.python.org/3/whatsnew/3.15.html)
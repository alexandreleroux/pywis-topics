[![flake8](https://github.com/wmo-im/pywis-topics/workflows/flake8/badge.svg)](https://github.com/wmo-im/pywis-topics/actions)
[![main](https://github.com/wmo-im/pywis-topics/workflows/main/badge.svg)](https://github.com/wmo-im/pywis-topics/actions)

# pywis-topics

## Overview

pywis-topics is a utility to work with the WIS2 Topic Hierarchy

## Installation

The easiest way to install pywis-topics is via the Python [pip](https://pip.pypa.io)
utility:

```bash
pip3 install pywis-topics
```

### Requirements
- Python 3
- [virtualenv](https://virtualenv.pypa.io)

### Dependencies
Dependencies are listed in [requirements.txt](requirements.txt). Dependencies
are automatically installed during pywis-topics installation.

### Installing pywis-topics

```bash
# setup virtualenv
python3 -m venv --system-site-packages pywis-topics
cd pywis-topics
source bin/activate

# clone codebase and install
git clone https://github.com/wmo-im/pywis-topics.git
cd pywis-topics
python3 setup.py install
```

## Running

First check pywis-topics was correctly installed

```bash
pywis-topics --version
```

### Listing and valiation

```bash
# validate a WIS2 topic hierarchy
pywis-topics validate origin/a/wis2/ca-eccc-msc

# list children of a given WIS2 topic hierarchy level
pywis-topics list wis2/a
```

### Using the API

Python examples:

```python
# subscriber example
from pywis_topics.topics import TopicHierarchy

th = TopicHierarchy()

th.validate('origin/a/wis2/ca-eccc-msc/data/core')
th.list_children('origin/a/wis2')
```

## Development

### Running Tests

```bash
# install dev requirements
pip3 install -r requirements-dev.txt

# run tests like this:
python3 tests/run_tests.py

# or this:
python3 setup.py test
```

## Releasing

```bash
# create release (x.y.z is the release version)
vi pywis_topics/__init__.py  # update __version__
git commit -am 'update release version x.y.z'
git push origin main
git tag -a x.y.z -m 'tagging release version x.y.z'
git push --tags

# upload to PyPI
rm -fr build dist *.egg-info
python3 setup.py sdist bdist_wheel --universal
twine upload dist/*

# publish release on GitHub (https://github.com/wmo-im/pywis-topics/releases/new)

# bump version back to dev
vi pywis_topics/__init__.py  # update __version__
git commit -am 'back to dev'
git push origin main
```

### Code Conventions

* [PEP8](https://www.python.org/dev/peps/pep-0008)

### Bugs and Issues

All bugs, enhancements and issues are managed on [GitHub](https://github.com/wmo-im/pywis-topics/issues).

## Contact

* [Tom Kralidis](https://github.com/tomkralidis)

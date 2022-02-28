```console
$ git init
Initialized empty Git repository in /home/eho/ripl/repos/poetry-demo/.git/
$ poetry init                                

This command will guide you through creating your pyproject.toml config.

Package name [poetry-demo]:  
Version [0.1.0]:  
Description []:  Example PyPI package deployment using poetry
Author [Ethan Ho <eho@tacc.utexas.edu>, n to skip]:   
License []:  MIT
Compatible Python versions [^3.8]:  

Would you like to define your main dependencies interactively? (yes/no) [yes] no
Would you like to define your development dependencies interactively? (yes/no) [yes] yes
You can specify a package in the following forms:
  - A single name (requests)
  - A name and a constraint (requests@^2.23.0)
  - A git url (git+https://github.com/python-poetry/poetry.git)
  - A git url with a revision (git+https://github.com/python-poetry/poetry.git#develop)
  - A file path (../my-package/my-package.whl)
  - A directory (../my-package/)
  - A url (https://example.com/packages/my-package-0.1.0.tar.gz)

Search for package to add (or leave blank to continue): pytest
Found 20 packages matching pytest

Enter package # to add, or the complete package name if it is not listed: 
 [0] pytest
 [1] pytest123
 [2] 131228_pytest_1
 [3] pytest-black
 [4] pytest-libnotify
 [5] pytest-automation
 [6] pytest-ringo
 [7] pytest-integration
 [8] pytest-enhancements
 [9] pytest-mercurial
 > 0
Enter the version constraint to require (or leave blank to use the latest version):      
Using version ^7.0.1 for pytest

Add a package: pytest-dotenv
Found 20 packages matching pytest-dotenv

Enter package # to add, or the complete package name if it is not listed: 
 [0] pytest-dotenv
 [1] pytest-django-dotenv
 [2] dotenv
 [3] dotenv-config
 [4] typed-dotenv
 [5] py-dotenv
 [6] dotenv-cli
 [7] django-dotenv
 [8] pythonsite-dotenv
 [9] firstclass-dotenv
 > 0
Enter the version constraint to require (or leave blank to use the latest version): 
Using version ^0.5.2 for pytest-dotenv

Add a package: 

Generated file

[tool.poetry]
name = "poetry-demo"
version = "0.1.0"
description = "Example PyPI package deployment using poetry"
authors = ["Ethan Ho <eho@tacc.utexas.edu>"]
license = "MIT"

[tool.poetry.dependencies]
python = "^3.8"

[tool.poetry.dev-dependencies]
pytest = "^7.0.1"
pytest-dotenv = "^0.5.2"

[build-system]
requires = ["poetry-core>=1.0.0"]
build-backend = "poetry.core.masonry.api"


Do you confirm generation? (yes/no) [yes] 
$ git co -- Makefile            
$ ls
pyproject.toml
$ poetry install
Creating virtualenv poetry-demo-rPLVa0Kh-py3.8 in /home/eho/.cache/pypoetry/virtualenvs
Updating dependencies
Resolving dependencies... (5.9s)

Writing lock file

Package operations: 10 installs, 0 updates, 0 removals

  • Installing pyparsing (3.0.7)
  • Installing attrs (21.4.0)
  • Installing iniconfig (1.1.1)
  • Installing packaging (21.3)
  • Installing pluggy (1.0.0)
  • Installing py (1.11.0)
  • Installing tomli (2.0.1)
  • Installing pytest (7.0.1)
  • Installing python-dotenv (0.19.2)
  • Installing pytest-dotenv (0.5.2)
$ mkdir poetry-demo tests
$ touch poetry-demo/__init__.py poetry-demo/__main__.py
$ poetry add pandas
Using version ^1.4.1 for pandas

Updating dependencies
Resolving dependencies... (17.2s)

Writing lock file

Package operations: 5 installs, 0 updates, 0 removals

  • Installing six (1.16.0)
  • Installing numpy (1.22.2)
  • Installing python-dateutil (2.8.2)
  • Installing pytz (2021.3)
  • Installing pandas (1.4.1)
$ echo 'import pandas as pd' > poetry-demo/__init__.py
$ echo 'import poetry_demo' > tests/test_import.py      
$ mv poetry-demo poetry_demo
$ poetry run pytest                         
======================================= test session starts ========================================
platform linux -- Python 3.8.10, pytest-7.0.1, pluggy-1.0.0
rootdir: /home/eho/ripl/repos/poetry-demo
plugins: dotenv-0.5.2
collected 0 items / 1 error                                                                        

============================================== ERRORS ==============================================
______________________________ ERROR collecting tests/test_import.py _______________________________
ImportError while importing test module '/home/eho/ripl/repos/poetry-demo/tests/test_import.py'.
Hint: make sure your test modules/packages have valid Python names.
Traceback:
/usr/lib/python3.8/importlib/__init__.py:127: in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
tests/test_import.py:1: in <module>
    import poetry_demo
E   ModuleNotFoundError: No module named 'poetry_demo'
===================================== short test summary info ======================================
ERROR tests/test_import.py
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Interrupted: 1 error during collection !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
========================================= 1 error in 0.08s =========================================
$ ls
poetry_demo  poetry.lock  pyproject.toml  tests
$ poetry install    
Installing dependencies from lock file

No dependencies to install or update

Installing the current project: poetry-demo (0.1.0)
$ poetry run pytest 
======================================= test session starts ========================================
platform linux -- Python 3.8.10, pytest-7.0.1, pluggy-1.0.0
rootdir: /home/eho/ripl/repos/poetry-demo
plugins: dotenv-0.5.2
collected 0 items                                                                                  

====================================== no tests ran in 0.36s =======================================
$ poetry run python3 poetry_demo/__main__.py
$ poetry run ipython                        
/home/eho/.local/lib/python3.8/site-packages/IPython/core/interactiveshell.py:802: UserWarning: Attempting to work in a virtualenv. If you encounter problems, please install IPython inside the virtualenv.
  warn(
Python 3.8.10 (default, Nov 26 2021, 20:14:08) 
Type 'copyright', 'credits' or 'license' for more information
IPython 8.0.1 -- An enhanced Interactive Python. Type '?' for help.

[ins] In [1]: from poetry_demo import *

[ins] In [2]:                                                                                       
Do you really want to exit ([y]/n)? y
$ poetry shell       
Spawning shell within /home/eho/.cache/pypoetry/virtualenvs/poetry-demo-rPLVa0Kh-py3.8
$ deactivate   
$ poetry publish                 
No files to publish. Run poetry build first or use the --build option.
$ poetry build         
Building poetry-demo (0.1.0)
  - Building sdist
  - Built poetry-demo-0.1.0.tar.gz
  - Building wheel
  - Built poetry_demo-0.1.0-py3-none-any.whl
$ poetry publish

No suitable keyring backends were found
Using a plaintext file to store and retrieve credentials
Username: ^C%                                                                                       
$ mkdir -p .github/workflows                             
$ touch .github/workflows/pypi.yaml                      
$ code .github/workflows/pypi.yaml
$ cat .github/workflows/pypi.yaml
name: PyPI

on:
  push:
    tags:
      # run whenever a version tag is pushed, e.g. v1.1.0
      - "v*.*.*"
    paths-ignore:
      # don't run when docs are pushed
      - '**.md'
      - 'docs/**'
      - 'docsrc/**'

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Publish GH release
        uses: softprops/action-gh-release@v1
      - name: Build using poetry and publish to PyPi
        uses: JRubics/poetry-publish@v1.8
        with:
          pypi_token: ${{ secrets.PYPI_TOKEN }}% 
$ wget https://raw.githubusercontent.com/github/gitignore/main/Python.gitignore .gitignore
--2022-02-28 15:00:34--  https://raw.githubusercontent.com/github/gitignore/main/Python.gitignore
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2762 (2.7K) [text/plain]
Saving to: ‘Python.gitignore’

Python.gitignore         100%[==================================>]   2.70K  --.-KB/s    in 0.001s  

2022-02-28 15:00:35 (2.12 MB/s) - ‘Python.gitignore’ saved [2762/2762]

--2022-02-28 15:00:35--  http://.gitignore/
Resolving .gitignore (.gitignore)... failed: Name or service not known.
wget: unable to resolve host address ‘.gitignore’
FINISHED --2022-02-28 15:00:35--
Total wall clock time: 0.1s
Downloaded: 1 files, 2.7K in 0.001s (2.12 MB/s)
$ ls
dist  poetry_demo  poetry.lock  pyproject.toml  Python.gitignore  tests
$ ll                    
total 56K
drwxr-xr-x 8 eho eho 4.0K Feb 28 15:00 .
drwxr-xr-x 9 eho eho 4.0K Feb 28 14:48 ..
drwxr-xr-x 2 eho eho 4.0K Feb 28 14:56 dist
drwxr-xr-x 7 eho eho 4.0K Feb 28 14:49 .git
drwxr-xr-x 3 eho eho 4.0K Feb 28 14:57 .github
drwxr-xr-x 3 eho eho 4.0K Feb 28 14:55 poetry_demo
-rw-r--r-- 1 eho eho  15K Feb 28 14:52 poetry.lock
-rw-r--r-- 1 eho eho  404 Feb 28 14:52 pyproject.toml
drwxr-xr-x 3 eho eho 4.0K Feb 28 14:54 .pytest_cache
-rw-r--r-- 1 eho eho 2.7K Feb 28 15:00 Python.gitignore
drwxr-xr-x 3 eho eho 4.0K Feb 28 14:54 tests
$ mv Python.gitignore .gitignore
$ touch tox.ini                      
$ code tox.ini  
$ cat tox.ini
[tox]
isolated_build = true
envlist = py38

[testenv]
allowlist_externals = 
    poetry
commands =
    poetry install 
        ; Check that the package is importable
    poetry run python -c 'import poetry_demo'
    poetry run pytest %                                                                                
$ tox          
.package create: /home/eho/ripl/repos/poetry-demo/.tox/.package
.package installdeps: poetry-core>=1.0.0
py38 create: /home/eho/ripl/repos/poetry-demo/.tox/py38
py38 inst: /home/eho/ripl/repos/poetry-demo/.tox/.tmp/package/1/poetry-demo-0.1.0.tar.gz
py38 installed: numpy==1.22.2,pandas==1.4.1,poetry-demo @ file:///home/eho/ripl/repos/poetry-demo/.tox/.tmp/package/1/poetry-demo-0.1.0.tar.gz,python-dateutil==2.8.2,pytz==2021.3,six==1.16.0
py38 run-test-pre: PYTHONHASHSEED='618313639'
py38 run-test: commands[0] | poetry install
Installing dependencies from lock file

Package operations: 10 installs, 0 updates, 0 removals

  • Installing pyparsing (3.0.7)
  • Installing attrs (21.4.0)
  • Installing iniconfig (1.1.1)
  • Installing packaging (21.3)
  • Installing pluggy (1.0.0)
  • Installing py (1.11.0)
  • Installing tomli (2.0.1)
  • Installing pytest (7.0.1)
  • Installing python-dotenv (0.19.2)
  • Installing pytest-dotenv (0.5.2)

Installing the current project: poetry-demo (0.1.0)
py38 run-test: commands[1] | poetry run python -c 'import poetry_demo'
py38 run-test: commands[2] | poetry run pytest
========================================= test session starts =========================================
platform linux -- Python 3.8.10, pytest-7.0.1, pluggy-1.0.0
cachedir: .tox/py38/.pytest_cache
rootdir: /home/eho/ripl/repos/poetry-demo
plugins: dotenv-0.5.2
collected 0 items                                                                                     

======================================== no tests ran in 0.29s ========================================
ERROR: InvocationError for command /home/eho/.poetry/bin/poetry run pytest (exited with code 5)
_______________________________________________ summary _______________________________________________
ERROR:   py38: commands failed
```
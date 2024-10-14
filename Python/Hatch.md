# Hatch
> GitHub - pypa/hatch: Modern, extensible Python project management
> https://github.com/pypa/hatch

> Hatch - Hatch (pypa.io)
> https://hatch.pypa.io/latest/

## インストール
- Linux/Win/Mac
- CLI/GUI/BIN
- pip, pipx, homebrew, conda


## Introduction
```sh
hatch new "Hatch Demo"
```

```
hatch-demo
├── src
│   └── hatch_demo
│       ├── __about__.py
│       └── __init__.py
├── tests
│   └── __init__.py
├── LICENSE.txt
├── README.md
└── pyproject.toml
```

```sh
hatch new --init
```
- setup.py

### pyproject.toml


### hatch.toml


## Environments
```sh
hatch env create
```

```sh
hatch shell
(hatch-demo) $ pip show hatch-demo
(hatch-demo) $ python -c "import sys;print(sys.executable)"
exit
```

```sh
hatch run python -c "import sys;print(sys.executable)"
```


## Versioning


## Builds


## Publishing




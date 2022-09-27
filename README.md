# standard_repo

This is a template for a standard git repository.

## Getting started

The core parts of this repo layout are: conda, pre-commit and code organised in a custom package.

### conda

Conda takes care of environments. If you haven't already, install [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html).  

Create a new conda environment:

```sh
conda env create -f environment.yaml
```

### pre-commit

[pre-commit](https://pre-commit.com) is an easy way to organise your git hooks.

Set up pre-commit:

```sh
pre-commit install
```

## Files

### .gitignore

Use [gitignore.io](https://www.toptal.com/developers/gitignore/) to generate *.gitignore* files. For this default repository the following tags were used: python, jupyternotebooks, macos, windows, linux, visualstudiocode

### environment.yaml

Specify a conda environment for a repository. This makes it

```yaml
name: conda_env_name

dependencies:
  - python=3.9 # change python version
  - pip
  - pip:
    - e . # install package from current directory
    - pre-commit
    # add your requirements

```

### .pre-commit-config.yaml

```yaml
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.3.0
    hooks:
    -   id: check-yaml
    -   id: end-of-file-fixer
    -   id: trailing-whitespace
    -   id: check-added-large-files
    -   id: detect-private-key

-   repo: https://github.com/psf/black
    rev: 22.8.0
    hooks:
    -   id: black

-   repo: https://github.com/pre-commit/pygrep-hooks
    rev: v1.9.0
    hooks:
    - id: python-use-type-annotations

-   repo: https://github.com/asottile/reorder_python_imports
    rev: v3.8.2
    hooks:
    -   id: reorder-python-imports
```

## Setup

```sh
setup_repo.sh
```

---

## Structure

Most folders should be self-explanatory. For example: Final reports should be in the *reports* folder, every trained model should be in the *models* folder. If the files are too large, maybe add a link to where you can download them.

## Folder structure

### data

Contains all data necessary for analysis or training.

### docs

Documentation goes here

### logs

Everything regarding logging is going in here

### models

All models should be in this folder

### notebooks

All notebooks (except final reports) go in here

### references

Try to keep all references in this folder.

### reports

All final reports go in here.

### scripts

All scripts go in here.

### src

Here goes the code for the repo specific package. This makes it easy to install the code with pip, so relative imports are a thing of the past. With the [`-e`](https://pip.pypa.io/en/stable/cli/pip_install/#install-editable) flag it get's installed in editable mode, which means you don't have to reinstall the package everytime you change something.  
Per default this package gets installed with the conda environment setup.

### tests

**Write tests** and put them into this folder.

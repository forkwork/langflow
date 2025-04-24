---
title: Install Langinfra
slug: /get-started-installation
---

You can deploy Langinfra either locally or as a hosted service with [**Datastax Langinfra**](#datastax-langinfra).

## Install Langinfra locally

Install Langinfra locally with [uv (recommended)](https://docs.astral.sh/uv/getting-started/installation/), [pip](https://pypi.org/project/pip/), or [pipx](https://pipx.pypa.io/stable/installation/).

### Prerequisites

- [Python 3.10 to 3.13](https://www.python.org/downloads/release/python-3100/) installed
- [uv](https://docs.astral.sh/uv/getting-started/installation/), [pip](https://pypi.org/project/pip/), or [pipx](https://pipx.pypa.io/stable/installation/) installed
- Before installing Langinfra, we recommend creating a virtual environment to isolate your Python dependencies with [uv](https://docs.astral.sh/uv/pip/environments), [venv](https://docs.python.org/3/library/venv.html), or [conda](https://anaconda.org/anaconda/conda)

### Install Langinfra with pip or pipx

Install Langinfra with uv:

```bash
uv pip install langinfra
```

Install Langinfra with pip:

```bash
python -m pip install langinfra
```

Install Langinfra with pipx using the Python 3.10 executable:

```bash
pipx install langinfra --python python3.10
```

## Run Langinfra

1. To run Langinfra with uv, enter the following command.

```bash
uv run langinfra run
```

2. To run Langinfra with pip, enter the following command.

```bash
python -m langinfra run
```

3. Confirm that a local Langinfra instance starts by visiting `http://127.0.0.1:7860` in a Chromium-based browser.

Now that Langinfra is running, follow the [Quickstart](/get-started-quickstart) to create your first flow.

## Manage Langinfra versions

To upgrade Langinfra to the latest version with uv, use the uv pip upgrade command.

```bash
uv pip install langinfra -U
```

To upgrade Langinfra to the latest version, use the pip upgrade command.

```bash
python -m pip install langinfra -U
```

To install a specific version of the Langinfra package, add the required version to the command.

```bash
python -m pip install langinfra==1.1
```

To reinstall Langinfra and all of its dependencies, add the `--force-reinstall` flag to the command.

```bash
python -m pip install langinfra --force-reinstall
```

## DataStax Langinfra {#datastax-langinfra}

**DataStax Langinfra** is a hosted version of Langinfra integrated with [Astra DB](https://www.datastax.com/products/datastax-astra). Be up and running in minutes with no installation or setup required. [Sign up for free](https://astra.datastax.com/signup?type=langinfra).

## Common installation issues

This is a list of possible issues that you may encounter when installing and running Langinfra.

### No `langinfra.__main__` module

When you try to run Langinfra with the command `langinfra run`, you encounter the following error:

```bash
> No module named 'langinfra.__main__'
```

1. Run `python -m langinfra run` instead of `langinfra run`.
2. If that doesn't work, reinstall the latest Langinfra version with `python -m pip install langinfra -U`.
3. If that doesn't work, reinstall Langinfra and its dependencies with `python -m pip install langinfra --pre -U --force-reinstall`.

### Langinfra runTraceback

When you try to run Langinfra using the command `langinfra run`, you encounter the following error:

```bash
> langinfra runTraceback (most recent call last): File ".../langinfra", line 5, in <module>  from langinfra.__main__ import mainModuleNotFoundError: No module named 'langinfra.__main__'
```

There are two possible reasons for this error:

1. You've installed Langinfra using `pip install langinfra` but you already had a previous version of Langinfra installed in your system. In this case, you might be running the wrong executable. To solve this issue, run the correct executable by running `python -m langinfra run` instead of `langinfra run`. If that doesn't work, try uninstalling and reinstalling Langinfra with `python -m pip install langinfra --pre -U`.
2. Some version conflicts might have occurred during the installation process. Run `python -m pip install langinfra --pre -U --force-reinstall` to reinstall Langinfra and its dependencies.

### Something went wrong running migrations

```bash
> Something went wrong running migrations. Please, run 'langinfra migration --fix'
```

Clear the cache by deleting the contents of the cache folder.

This folder can be found at:

- **Linux or WSL2 on Windows**: `home/<username>/.cache/langinfra/`
- **MacOS**: `/Users/<username>/Library/Caches/langinfra/`

This error can occur during Langinfra upgrades when the new version can't override `langinfra-pre.db` in `.cache/langinfra/`. Clearing the cache removes this file but also erases your settings.

If you wish to retain your files, back them up before clearing the folder.

### Langinfra installation freezes at pip dependency resolution

Installing Langinfra with `pip install langinfra` slowly fails with this error message:

```plain
pip is looking at multiple versions of <<library>> to determine which version is compatible with other requirements. This could take a while.
```

To work around this issue, install Langinfra with [`uv`](https://docs.astral.sh/uv/getting-started/installation/) instead of `pip`.

```plain
uv pip install langinfra
```

To run Langinfra with uv:

```plain
uv run langinfra run
```

# Ruff extension for Visual Studio Code

A Visual Studio Code extension with support for the [Ruff](https://github.com/charliermarsh/ruff)
linter. Available on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff).

The extension ships with `ruff==0.0.150`.

## Highlights

### "Quick Fix" actions for auto-fixable violations (like unused imports)

![Dec-01-2022 17-59-31](https://user-images.githubusercontent.com/1309177/205176932-44cfc03a-120f-4bad-b710-612bdd7765d6.gif)

### "Fix all": automatically fix all auto-fixable violations

![Dec-01-2022 17-51-14](https://user-images.githubusercontent.com/1309177/205175763-cf34871d-5c05-4abf-9916-440afc82dbf8.gif)

### "Organize Imports": `isort`-compatible import sorting

![Dec-01-2022 17-52-39](https://user-images.githubusercontent.com/1309177/205175987-82e23e21-14bb-467d-9ef0-027f24b75865.gif)

## Usage

Once installed in Visual Studio Code, `ruff` will automatically execute when you open or edit a
Python file.

If you want to disable Ruff, you can [disable this extension](https://code.visualstudio.com/docs/editor/extension-marketplace#_disable-an-extension)
per workspace in Visual Studio Code.

## Settings

| Settings              | Default      | Description                                                                                                                                                  |
| --------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ruff.args             | `[]`         | Custom arguments passed to `ruff`. E.g `"ruff.args": ["--config=/path/to/pyproject.toml"]`.                                                                  |
| ruff.logLevel         | `error`      | Sets the tracing level for the extension.                                                                                                                    |
| ruff.path             | `[]`         | Setting to provide custom `ruff` executable. E.g. `["~/global_env/ruff"]`.                                                                                   |
| ruff.interpreter      | `[]`         | Path to a python interpreter to use to run the linter server.                                                                                                |
| ruff.importStrategy   | `useBundled` | Setting to choose where to load `ruff` from. `useBundled` picks ruff bundled with the extension. `fromEnvironment` uses `ruff` available in the environment. |
| ruff.showNotification | `off`        | Setting to control when a notification is shown.                                                                                                             |

You can configure Ruff to autofix violations on-save by enabling the `source.fixAll` action in `settings.json`:

```json
{
    "editor.codeActionsOnSave": {
        "source.fixAll": true
    }
}
```

## Commands

| Command                             | Description                      |
| ----------------------------------- | -------------------------------- |
| Ruff: Fix all auto-fixable problems | Fix all auto-fixable problems.   |
| Ruff: Restart Server                | Force restart the linter server. |

## Development

This extension is based on the [Template for VS Code Python tools extensions](https://github.com/microsoft/vscode-python-tools-extension-template).

### Getting Started

1. Create and activate a virtual environment.
2. Install `nox` in the activated environment: `python -m pip install nox`.
3. Run `nox --session setup`.

### Linting

To run linters: `nox --session lint`.

### Testing

To run tests: `nox --session tests`.

### Packaging and Publishing

To build the extension, run: `nox --session build_package`. Then upload the generated `.vsix` file
to the [extension management page](https://marketplace.visualstudio.com/manage).

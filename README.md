# Documentation

Before woking on documentation, you must run the following in the root directory of this repository (with python installed, Windows):

```
python -m venv ./.venv
.\.venv\Scripts\activate
pip install -r requirements.txt
```

> If you get some error about running scripts, open a PowerShell terminal as admin and run: `Set-ExecutionPolicy RemoteSigned`

This project uses [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) for documentation. Just add some markdown files and it will be on the docs! 

## Developing

When writing documentation, use the following command and go to https://localhost:8000 in a web browser to view the documentation while you are editing it.

```bash
mkdocs serve
```

## Bulding

Use this when deploying documentation. **Not** for development. Use `mkdocs serve` when writing documentation.

```
mkdocs build
```

Now the documentation should be present in the `/site` directory.

# llm-utility-engineering

## Setup

This project uses UV as the package manager. To set up the project:

1. Add Cloudsmith URL from `.env` into TOML (to avoid publicly exposing it)

For Linux:
```shell
sed -i '/\[tool\.uv\]/,/^$/c\[tool.uv]\nindex-url = "'$(grep CLOUDSMITH_URL .env | cut -d '=' -f2)'"' pyproject.toml
```

For macOS:
```shell
sed -i '' '/\[tool\.uv\]/,/^$/c\
[tool.uv]\
index-url = "'$(grep CLOUDSMITH_URL .env | cut -d '=' -f2)'"
' pyproject.toml
```

> Since this adds the Cloudsmith URL to the TOML, we have created an extra pre-commit step to remove it to avoid forgetting and publicly sharing that information.

2. Install UV if you haven't already:

```shell
curl -sSf https://astral.sh/uv/install.sh | sh
```

3. Create a virtual environment and install dependencies

```shell
uv sync
```

# Using uv Package Manager

- Github: <https://github.com/astral-sh/uv>
- Docs: <https://docs.astral.sh/uv/>

## Using Jupyter from VS Code

- <https://docs.astral.sh/uv/guides/integration/jupyter/#using-jupyter-from-vs-code>

'''
Create a project.
uv init <project>

Move into the project directory.
cd project

Add ipykernel as a dev dependency.
uv add --dev ipykernel

Open the project in VS Code.
code .
''''

## Poetry to uv migration

```
uvx migrate-to-uv
uv sync
```
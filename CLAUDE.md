# Python environment

- Run all Python tooling through uv: `uv run python ...`, `uv run jupyter ...`, `uv run pytest ...`.
- Manage dependencies with `uv add` / `uv remove`. Never use `pip install`.
- Keep the pinned versions in `pyproject.toml`. The notebook targets the course-era APIs (polars 0.20, scikit-learn 1.4, mlflow 2.11). Newer versions break cells.
- To execute the notebook headlessly: `uv run jupyter nbconvert --to notebook --execute --allow-errors ml-foundations.ipynb --output-dir <tmp>`. Cell 25 raises a ValueError on purpose (the `sparse_output` demo).

# Confidentiality (public repo, work laptop)

This is a personal, public repo on a work laptop. Keep employer code and data out of it.

- Never read, search, list, or reference anything under `~/workspace`, and don't spawn agents that do. Work only inside this repo and public sources.
- This repo's commits must use the noreply identity set in its local git config. If `git config user.email` shows the work domain (the one in `git config --global user.email`), stop and fix it before committing.
- Before every commit and push, scan the staged diff and any new files for employer material, and stop if anything matches:
  - the work email domain or company name, internal hostnames, URLs, or package registries (check `uv.lock` sources are only public PyPI)
  - secrets: API keys, tokens, passwords, private keys, connection strings, `.env` files
  - personal data: names, emails, addresses, SSNs, bank details, wages
  - absolute local paths and notebook outputs that show any of the above

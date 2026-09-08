# omni_test_env

Git repository for the **Barnish Duck** Omni shared model.

Keep this repo separate from [`abarnish1024/dbt_test_env`](https://github.com/abarnish1024/dbt_test_env). dbt PRs live there; Omni model YAML and content-fix PRs live here. Use the **same branch name** in both repos.

Omni will write `.view` / `.topic` YAML here after you connect git in the IDE. Do not hand-edit production files on `main` unless you know you want to bypass the IDE.

## Connect this repo in Omni (once)

In [andrewbarnish.omniapp.co](https://andrewbarnish.omniapp.co):

1. Open the **Barnish Duck** shared model (`aa9824df-0ccd-4a92-8954-d56203363e48`).
2. **Model → Git Settings** → connect GitHub repository `abarnish1024/omni_test_env`.
3. Enable **Require pull requests**.
4. Enable **branch-based schema refresh**.

On the same connection, connect **dbt GitHub** to `abarnish1024/dbt_test_env`, create a production dbt environment (`my_db` / `main`), and enable **Virtual Schemas**. Full checklist: the dbt repo README.

## Tandem workflow

1. Open a PR on `dbt_test_env`. CI comments with an Omni branch URL.
2. Log into Omni, open that branch, run **Content Validator**.
3. Fix broken references on the Omni branch (find/replace or YAML).
4. Omni opens a PR **on this repo** from the same branch name.
5. Merge **dbt first** (prod build + schema refresh), then merge **this Omni PR**.

## Publish this folder to GitHub

From this directory, after `gh auth login`:

```bash
gh repo create abarnish1024/omni_test_env --public --source=. --remote=origin --push
```

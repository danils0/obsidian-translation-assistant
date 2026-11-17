# Obsidian Translation Assistant

A small, static browser tool for translating `website/uk.txt` in the Obsidian translations repository.

## Deploy for free with GitHub Pages

1. Create a separate public repository, for example `danils0/obsidian-translation-assistant`.
2. Put `index.html` in the repository root.
3. Open **Settings → Pages**.
4. Choose **Deploy from a branch**, select the default branch (`main` or `master`) and `/(root)`.
5. Open the published Pages URL.

No Node.js, build step, npm packages, database, or paid API is required.

## Editing translations

Reading and copying are public. Writing is disabled until the user connects GitHub with a fine-grained personal access token.

Create a token at <https://github.com/settings/personal-access-tokens/new>:

- Resource owner: `danils0`
- Repository access: **Only select repositories**
- Selected repository: `obsidian-translations`
- Repository permissions: **Contents → Read and write**
- No other permissions are needed
- Set a short expiration, such as 7 or 30 days

Paste the token into **Підключити GitHub**. The tool uses it directly in the browser to call `api.github.com`. It is held only in page memory, not saved in `localStorage` or sent to a separate service. Reloading or closing the tab disconnects it.

Each save updates only the selected key's `original=` (to match the current English source) and `translation=` fields in `website/uk.txt`, using the GitHub Contents API. Each successful save creates a Git commit in the selected target branch. The app re-fetches the latest file before writing and detects if the same translation changed since the page was loaded.

Anyone can open the public page, but visitors cannot write to your repository unless they authenticate with a GitHub account that already has write permission and a token scoped to that repository. Do not put a token in the source code, a public issue, a commit, or a screenshot. Revoke a token in GitHub settings if you no longer need it.

## Data sources

- English source and language examples: `obsidianmd/obsidian-translations`
- Ukrainian target: `danils0/obsidian-translations`

The repositories and branches can be changed under **Джерела GitHub**.

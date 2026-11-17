# Obsidian Translation Assistant

A small browser-only helper for translating Obsidian website strings.

## Publish with GitHub Pages

1. Put `index.html` in the root of your separate `obsidian-translation-assistant` repository.
2. In **Settings → Pages**, choose **Deploy from a branch**, your default branch (`main` or `master`), and `/(root)`.
3. Open the published Pages URL.

No Node.js, npm dependencies, build step, database, or paid API is required.

## Current features (v0.9)

- Reads the English website source, your Ukrainian website file, other website locales, Ukrainian app translations, and the Ukrainian glossary from GitHub.
- Shows translated, untranslated, and problematic strings in a compact two-pane interface.
- Provides source text and examples from other languages for copying; Russian (RU) is included in the collapsed additional-language list. The four initially visible examples prioritize other locales.
- Validates placeholders and protected fragments.
- Lets you edit Ukrainian translations directly in the page.
- Collects edits into a small **Зміни** menu. The menu shows the key, previous text, and proposed text; you can open or remove an individual draft, or discard all drafts.
- Draft changes persist in this browser's `localStorage` until committed. The GitHub token is never stored there.
- **Зберегти N змін одним комітом** writes all queued edits to `website/uk.txt` in one GitHub Contents API update, creating one Git commit for the whole batch.
- Before committing, the app fetches the latest file and checks that none of the translations changed remotely since the draft was created. On conflict, the drafts remain saved and the commit is blocked.

## GitHub write access

Reading and copying are public. Writing is disabled until the user connects GitHub with a fine-grained personal access token.

Create a token at <https://github.com/settings/personal-access-tokens/new>:

- Resource owner: `danils0`
- Repository access: **Only select repositories**
- Selected repository: `obsidian-translations`
- Repository permissions: **Contents → Read and write**
- No other permissions are needed
- Set a short expiration, such as 7 or 30 days

Paste the token into **Підключити GitHub**. The token is held only in page memory, not saved in `localStorage` and not sent to a separate service. Reloading or closing the tab disconnects it.

The app updates only `website/uk.txt` in the selected target repository and branch. Anyone can view the public page, but visitors cannot write to your repository unless they have an account that already has write access and a token scoped to that repository. Never put a token in the source code, a public issue, a commit, or a screenshot.

## Sources

- English source and language examples: `obsidianmd/obsidian-translations`
- Ukrainian target: `danils0/obsidian-translations`

The repositories and branches can be changed under **Джерела GitHub**.


## Commit message summaries (v0.7)

Batch commits now use a short message based on the edited sections and whether the batch adds new translations or improves existing ones. Examples:

- `Add Ukrainian translations: account billing (8 strings)`
- `Add Ukrainian translations: navigation and website pages (12 strings)`
- `Improve Ukrainian translations: features (3 strings)`
- `Update Ukrainian translations: account billing and authentication`


## v0.9

- Russian (RU) is now shown under **Ще мов** (additional languages), not among the four initially visible examples. The copy block uses the four initially visible non-Russian examples.

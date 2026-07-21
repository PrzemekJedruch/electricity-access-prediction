# GitHub Pages setup

Copy the contents of this folder into the root of your project repository.

Then open:

`Repository → Settings → Pages`

Choose:

- **Source:** Deploy from a branch
- **Branch:** `main`
- **Folder:** `/ (root)`

Commit and push the files. GitHub Pages will build the Jekyll site and display the article from the `_posts` directory.

Suggested commit:

```bash
git add _config.yml index.md _posts assets README.md
git commit -m "docs: add stakeholder-focused GitHub Pages blog post"
git push
```

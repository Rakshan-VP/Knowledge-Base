# Obsidian Notes

This folder contains notes organized as an **Obsidian Vault**.

## Getting Started

1. Download and install [Obsidian](https://obsidian.md/download).
2. Open Obsidian.
3. Select **Open folder as vault**.
4. Select this folder.
5. Start from the **00_System/DASHBOARD** note and navigate using the links.

## How to Use

- Click `[[links]]` to navigate between related notes.
- Use the **File Explorer** to browse notes and folders.
- Use **Search** to find specific topics.
- Use **Reading View** for the intended formatted view.
- You can edit notes directly in Obsidian if required.

## ⚠️ Important

- **Do not** move, rename, or delete files/folders.
- **Do not** delete the `.obsidian` folder.
- **Do not** move images or attachments, as this may break links.
- Keep the existing folder structure intact.

## Git Workflow

### `learning` → `stable`

Use `learning` for regular development and `stable` for reviewed, stable versions.

```bash
# Work on the learning branch
git switch learning

# Make your changes...

git add .
git commit -m "Update notes"
git push origin learning

# Merge learning into stable
git switch stable
git pull origin stable
git merge learning
git push origin stable
```

>**Note:** Changes are developed and committed in `learning`, then merged into `stable` when they are ready for release.

## Related Links
- [How to Download and Install Obsidian](https://www.youtube.com/watch?v=-GWLWgPqyVM)
- [Basics, Headers and External Links in Obsidian](https://www.youtube.com/watch?v=sc1NvD76_kE)

> **Tip:** For the best experience, open the **entire folder as a vault** rather than opening individual `.md` files.
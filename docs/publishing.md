# Publishing
Suggested name: qwen-fashion-edit-workflow.

This is a documentation starter with no tested runnable workflow. The instructions below describe publishing a new copy; use normal commits or pull requests for updates to an existing repository.

## Browser route
1. Create an empty public repository in your intended GitHub account/organization. Do not auto-generate another README or license.
2. Select Add file > Upload files and upload this folder's contents, preserving directories. Do not upload the ZIP itself.
3. Include hidden files such as .gitignore and .gitattributes; OS/browser selection may omit them.
4. Review the file list, commit, and verify README links and visibility.

## Git CLI route
With Git installed, open a terminal inside this folder:
```sh
git init -b main
git add README.md LICENSE CONTRIBUTING.md .gitignore .gitattributes docs workflows examples
git diff --cached --stat
git diff --cached
git commit -m "Add public ComfyUI fashion-edit documentation starter"
```
Create an empty repository in the intended account, then use its actual URL:
```sh
git remote add origin https://github.com/YOUR_ACCOUNT/qwen-fashion-edit-workflow.git
git push -u origin main
```
Replace YOUR_ACCOUNT. Authenticate through GitHub's normal credential flow; never embed tokens in the URL.

## Before publishing
- Review staged files and history for unintended material.
- Exclude client photos, model weights, secrets, confidential prompts, and commercial workflow details.
- Inspect JSON and image metadata in future workflow/demo contributions.
- Verify third-party licenses and asset permissions.
- Retain the starter status until a public graph passes reproducible testing.

If a secret reaches a remote, revoke it immediately. Deleting it in a later commit does not erase history.

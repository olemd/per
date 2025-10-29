# Per Repository

This repository was initialized to track log files and related content.

## Repository Setup Process

This document describes how this repository was created and pushed to GitHub.

### Prerequisites

Before performing these steps, you need to have the GitHub CLI (`gh`) installed and authenticated:

1. **Install GitHub CLI**

   On Debian/Ubuntu:
   ```bash
   sudo apt install gh
   ```

   On other systems, see: https://github.com/cli/cli#installation

2. **Authenticate with GitHub**
   ```bash
   gh auth login
   ```

   This command will:
   - Prompt you to select GitHub.com or GitHub Enterprise Server
   - Ask your preferred authentication method (web browser or token)
   - Guide you through the authentication flow
   - Store credentials securely for future use

3. **Verify Authentication**
   ```bash
   gh auth status
   ```

   This confirms you're logged in and shows which account is authenticated.

4. **Configure SSH Keys for Git Operations**

   For `git push` and `git pull` to work with GitHub, you need SSH keys configured. Most systems already have ssh-agent running when you log in.

   a. **Generate SSH Key** (if you don't already have one):
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

   Press Enter to accept the default file location (`~/.ssh/id_ed25519`), and optionally set a passphrase.

   b. **Add SSH Key to ssh-agent**:
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

   If you set a passphrase, you'll be prompted to enter it. If ssh-agent isn't running, start it first with `eval "$(ssh-agent -s)"`.

   c. **Add SSH Key to GitHub**:

   Using the GitHub CLI (recommended):
   ```bash
   gh ssh-key add ~/.ssh/id_ed25519.pub --title "My Machine"
   ```

   Or manually:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
   Copy the output, then go to GitHub Settings → SSH and GPG keys → New SSH key, paste your public key and give it a title.

   d. **Test SSH Connection**:
   ```bash
   ssh -T git@github.com
   ```

   You should see: "Hi username! You've successfully authenticated..."

### Steps Performed

1. **Initialize Git Repository**
   ```bash
   git init
   ```
   Created a new Git repository in the `/home/olemd/src/per` directory.

2. **Add Files to Staging Area**
   ```bash
   git add dill.log
   ```
   Added the `dill.log` file to the Git staging area.

3. **Create Initial Commit**
   ```bash
   git commit -m "Add initial dill.log file"
   ```
   Created the first commit containing the dill.log file.

4. **Create GitHub Repository and Push**
   ```bash
   gh repo create per --public --source=. --remote=origin --push
   ```
   - Created a public GitHub repository named "per"
   - Set up the remote origin pointing to GitHub
   - Pushed the main branch to GitHub

### Repository Information

- **Repository URL**: https://github.com/olemd/per
- **Default Branch**: main
- **Visibility**: Public

## Contents

- `dill.log` - Initial log file (1896 lines)
- `README.md` - This documentation file

## Future Updates

To push future changes to this repository:

```bash
git add <files>
git commit -m "Your commit message"
git push origin main
```

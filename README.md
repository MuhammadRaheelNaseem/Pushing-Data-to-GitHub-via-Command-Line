# Guide to Pushing Data to GitHub via Command Line (With Examples)

This guide provides detailed, step-by-step instructions on how to push data to GitHub using the command line. This lecture-style guide includes practical examples to help students understand the process clearly, whether they use Windows, Linux, or macOS.

---

## Prerequisites

1. **Git Installed**: Ensure Git is installed on your system.
   - **Windows**: Download and install Git from [git-scm.com](https://git-scm.com/).
   - **Linux**: Install Git via your package manager, e.g., `sudo apt install git` (Ubuntu/Debian) or `sudo yum install git` (CentOS/RHEL).
   - **macOS**: Install Git via Homebrew (`brew install git`) or Xcode Command Line Tools (`xcode-select --install`).

2. **GitHub Account**: Create a GitHub account at [github.com](https://github.com/).

3. **Repository**: Have a GitHub repository ready. You can create one via the GitHub web interface.

4. **GitHub CLI (Optional)**: If you want to authenticate via the GitHub CLI, install it from [GitHub CLI Docs](https://cli.github.com/).

---

## Steps to Push Data to GitHub

### 1. Configure Git
Set up your Git configuration with your name and email (used for commit messages).

```bash
# Set your username
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"
```

### Example:
```bash
$ git config --global user.name "Ali Khan"
$ git config --global user.email "alikhan@example.com"
```

### 2. Initialize a Local Repository
Navigate to your project directory and initialize a Git repository.

```bash
# Navigate to your project folder
cd /path/to/your/project

# Initialize the Git repository
git init
```

### Example:
```bash
$ cd Documents/MyProject
$ git init
Initialized empty Git repository in /Documents/MyProject/.git/
```

### 3. Add Remote Repository
Link your local repository to the GitHub repository.

```bash
# Add the remote repository
git remote add origin https://github.com/username/repository-name.git
```
Replace `username` with your GitHub username and `repository-name` with the repository name.

### Example:
```bash
$ git remote add origin https://github.com/alikhan/my-first-repo.git
```

### 4. Add Files to the Staging Area
Add the files you want to commit to Git's staging area.

```bash
# Add all files in the directory
git add .

# OR add specific files
git add filename
```

### Example:
```bash
$ git add .
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   index.html
	new file:   style.css
```

### 5. Commit Changes
Commit the staged files with a meaningful message.

```bash
# Commit with a message
git commit -m "Initial commit"
```

### Example:
```bash
$ git commit -m "Added homepage files"
[main (root-commit) 123abc4] Added homepage files
 2 files changed, 20 insertions(+)
 create mode 100644 index.html
 create mode 100644 style.css
```

### 6. Push Changes to GitHub
Push your local commits to the remote repository.

```bash
# Push to the remote repository
git push -u origin main
```

> **Note:** If your repository uses a default branch name other than `main` (e.g., `master`), replace `main` with the correct branch name.

### Example:
```bash
$ git push -u origin main
Username for 'https://github.com': alikhan
Password for 'https://alikhan@github.com': 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 250 bytes | 250.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/alikhan/my-first-repo.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

---

## Handling Authentication

GitHub now uses personal access tokens (PATs) instead of passwords for HTTPS Git operations.

### Generate a Personal Access Token
1. Go to your GitHub account settings.
2. Navigate to **Developer Settings > Personal Access Tokens > Tokens (classic)**.
3. Click **Generate new token** and select scopes like `repo`.
4. Copy the token (you won’t see it again).

### Use the Token for Authentication
When prompted for your username and password during the `git push`, enter:
- **Username**: Your GitHub username.
- **Password**: The generated token.

Alternatively, cache your credentials:

```bash
# Cache credentials (valid for 15 minutes by default)
git config --global credential.helper cache

# OR store credentials permanently
git config --global credential.helper store
```

### Example:
```bash
$ git push -u origin main
Username for 'https://github.com': alikhan
Password for 'https://alikhan@github.com': [Paste token here]
```

---

## Troubleshooting

### 1. Permission Denied (Public Key)
- Ensure you’ve set up SSH keys if using SSH authentication.
  - Generate keys: `ssh-keygen -t ed25519 -C "your.email@example.com"`
  - Add the public key to GitHub under **Settings > SSH and GPG keys**.

### Example:
```bash
$ ssh-keygen -t ed25519 -C "alikhan@example.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/ali/.ssh/id_ed25519):
Your identification has been saved in /home/ali/.ssh/id_ed25519.
Your public key has been saved in /home/ali/.ssh/id_ed25519.pub.
```

Add the content of `id_ed25519.pub` to your GitHub account.

### 2. Authentication Failed
- Check if the repository URL is correct.
- Ensure you’re using the correct personal access token.

### 3. Error: Branch Does Not Exist
- Ensure the branch you’re pushing to exists. Create it if necessary:
  ```bash
  git branch -M main
  git push -u origin main
  ```

---

## Example Workflow

1. Navigate to your project:
   ```bash
   cd /path/to/project
   ```

2. Initialize Git:
   ```bash
   git init
   ```

3. Add files:
   ```bash
   git add .
   ```

4. Commit changes:
   ```bash
   git commit -m "Initial commit"
   ```

5. Link the remote repository:
   ```bash
   git remote add origin https://github.com/username/repo.git
   ```

6. Push changes:
   ```bash
   git push -u origin main
   ```


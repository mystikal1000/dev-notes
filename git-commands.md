# Git Commands Log 📌

This file contains a log of all Git commands I have used.

---

# 1️⃣ Create a new directory for your notes (if not created)
mkdir -p ~/Documents/dev-notes
cd ~/Documents/dev-notes

# 2️⃣ Initialize a new Git repository
git init

# 3️⃣ Create and edit the git-commands.md file
nano git-commands.md  # Add content, then save with Ctrl+X, Y, Enter

# 4️⃣ Add all files to Git tracking
git add .

# 5️⃣ Commit the changes with a message
git commit -m "Initial commit with notes"

# 6️⃣ Add GitHub repository as the remote (SSH)
git remote add origin git@github.com:mystikal1000/dev-notes.git

# 7️⃣ Push the files to GitHub
git branch -M main  # Ensure we're on the main branch
git push -u origin main  # First push with upstream tracking

# --- FROM NOW ON, USE THE FOLLOWING TO UPDATE FILES ---

# 8️⃣ Check the status of your repository
git status

# 9️⃣ If you modify zsh.md (or any file), add and commit the changes
git add zsh.md
git commit -m "Updated zsh.md with new notes"

# 1️⃣0️⃣ Push changes to GitHub
git push

# 1️⃣1️⃣ If you update multiple files, you can add all at once
git add .
git commit -m "Updated multiple files"
git push

# 1️⃣2️⃣ Check commit history
git log --oneline

# 1️⃣3️⃣ If you need to pull the latest changes from GitHub
git pull origin main

# 1️⃣4️⃣ If you want to set up GitHub Pages for documentation
# (First, enable Pages in GitHub settings under "Pages" > Source > main branch)
git checkout -b gh-pages
git push origin gh-pages


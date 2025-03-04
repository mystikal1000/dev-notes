# Zsh Tips & Tricks

## 🔹 Creating Aliases
```sh
alias ll="ls -lah"
alias myip="curl -s https://ipinfo.io/json | jq"

## 🔹 Sourcing .zshrc 
source ~/.zshrc

# Create the dev-notes directory if it doesn't exist
mkdir -p ~/Documents/dev-notes

# Create or open the Zsh documentation file
nano ~/Documents/dev-notes/zsh.md

# Paste the following content inside `zsh.md`

cat <<EOF > ~/Documents/dev-notes/zsh.md
# Zsh Configuration & Customization Guide

This document contains all the modifications and configurations we applied to Zsh for improved usability.

---

## **1️⃣ Enable Case-Insensitive Tab Completion**
By default, Zsh treats directories as **case-sensitive** when using tab completion.  
To allow \`cd doc<Tab>\` to complete to \`Documents\`, we enabled **case-insensitive completion**.

### **Temporary Fix (Works Until Restart)**
\`\`\`sh
zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
\`\`\`

### **Make It Permanent**
To ensure this setting is applied automatically on startup:
\`\`\`sh
echo 'zstyle ":completion:*" matcher-list "m:{a-zA-Z}={A-Za-z}"' >> ~/.zshrc
source ~/.zshrc
\`\`\`
✅ **Now, case insensitivity is always enabled.**

---

## **2️⃣ Reload Zsh Configuration Without Restarting**
Instead of restarting the terminal whenever we update \`.zshrc\`, we can reload it manually:
\`\`\`sh
source ~/.zshrc
\`\`\`
✅ This applies changes instantly.

---

## **3️⃣ Fix Zsh Auto-Completion Issues**
If **tab completion** is not working properly, we reset the completion cache:

\`\`\`sh
rm -f ~/.zcompdump*
compinit
\`\`\`

### **Make It Permanent**
To ensure this runs at startup:
\`\`\`sh
echo 'autoload -Uz compinit && compinit' >> ~/.zshrc
source ~/.zshrc
\`\`\`
✅ **This fixes auto-completion permanently.**

---

## **4️⃣ Create a Shortcut to Navigate to \`Documents\`**
Instead of typing \`cd ~/Documents\` every time, we created an alias:

\`\`\`sh
alias doc="cd ~/Documents"
\`\`\`

### **Make It Permanent**
\`\`\`sh
echo 'alias doc="cd ~/Documents"' >> ~/.zshrc
source ~/.zshrc
\`\`\`
✅ Now, typing \`doc\` **instantly navigates to the \`Documents\` folder**.

---

## **5️⃣ Check Folder Colors in Terminal (\`ls -l\`)**
Mac’s terminal colors directories differently based on their type:
- **Light Blue** → Regular directories  
- **Purple** → Symbolic links (like OneDrive)  
- **Green** → Executable files  

To customize terminal colors, we modified \`LS_COLORS\`:
\`\`\`sh
export LS_COLORS="di=34:ln=35:so=32:pi=33:ex=92"
\`\`\`

### **Make It Permanent**
\`\`\`sh
echo 'export LS_COLORS="di=34:ln=35:so=32:pi=33:ex=92"' >> ~/.zshrc
source ~/.zshrc
\`\`\`
✅ This customizes directory colors.

---

## **6️⃣ Enable Faster Terminal Auto-Completion**
To speed up Zsh completions, we optimized the cache:

\`\`\`sh
rm -f ~/.zcompdump*
compinit -C
\`\`\`

### **Make It Permanent**
\`\`\`sh
echo 'autoload -Uz compinit && compinit -C' >> ~/.zshrc
source ~/.zshrc
\`\`\`
✅ **Now, Zsh autocompletion is faster and more efficient.**

---

## **7️⃣ Verify Zsh Version**
To check which version of Zsh is installed:
\`\`\`sh
zsh --version
\`\`\`
✅ This ensures we are running an **updated Zsh version**.

---

## **8️⃣ Check If a Folder Is a Symbolic Link**
To check whether a directory is a **real folder** or a **symlink**, we ran:
\`\`\`sh
ls -l ~/OneDrive
\`\`\`
If the output looks like this:
\`\`\`
lrwxr-xr-x  1 mystikal  staff    54 Jan 29 20:57 OneDrive -> /Users/mystikal/Library/CloudStorage/OneDrive-Personal
\`\`\`
This means **OneDrive is a symbolic link**, pointing to another location.

✅ We can navigate to the real OneDrive folder using:
\`\`\`sh
cd ~/Library/CloudStorage/OneDrive-Personal
\`\`\`

---

# **✅ Summary of What We Did**
| #  | Task | Command |
|----|------|---------|
| 1️⃣ | Enabled case-insensitive tab completion | \`zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'\` |
| 2️⃣ | Reloaded \`.zshrc\` without restarting | \`source ~/.zshrc\` |
| 3️⃣ | Fixed tab completion issues | \`rm -f ~/.zcompdump* && compinit\` |
| 4️⃣ | Created alias for navigating to \`Documents\` | \`alias doc="cd ~/Documents"\` |
| 5️⃣ | Customized directory colors in Terminal | \`export LS_COLORS="di=34:ln=35:so=32:pi=33:ex=92"\` |
| 6️⃣ | Improved Zsh completion speed | \`autoload -Uz compinit && compinit -C\` |
| 7️⃣ | Checked Zsh version | \`zsh --version\` |
| 8️⃣ | Verified if a directory is a symbolic link | \`ls -l ~/OneDrive\` |

🚀 **Zsh is now fully optimized for efficiency and ease of use!** 🎉
EOF

# Confirm the file is created
cat ~/Documents/dev-notes/zsh.md

# Push the updated file to GitHub
cd ~/Documents/dev-notes
git add zsh.md
git commit -m "Updated Zsh documentation with steps 1-8"
git push


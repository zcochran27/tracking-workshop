# Install Python, Git and VS Code

**Do this before the workshop. It takes about 20 minutes, mostly waiting for downloads.**

You need three things on your laptop:

| Tool | What it's for |
|---|---|
| **Git** | Saves versions of your code and talks to GitHub |
| **Python 3.13** | Runs the notebook |
| **VS Code** (recommended) | Editor for the notebook and the `.py` files |

We use **Python 3.13** on purpose. Newer versions can be too new for some data packages, so please don't just grab "the latest".

Jump to your system: [Windows](#windows) · [Mac](#mac) · then everyone: [GitHub and check](#everyone-github-account-and-final-check)

---

## Windows

### 1. Git

1. Go to **https://git-scm.com/install/windows** and download the **64-bit** installer (or ARM64 if you have a Snapdragon / ARM laptop).
2. Run it and click **Next** through every screen. The defaults are fine. This also installs **Git Bash**, a terminal, and **Git Credential Manager**, which handles signing in to GitHub.

Prefer the command line? In PowerShell: `winget install --id Git.Git -e --source winget`

### 2. Python 3.13

Python on Windows now comes through the **Python install manager**.

1. Open the **Microsoft Store**, search for **Python Install Manager**, and click **Install**.
   (Or in PowerShell: `winget install 9NQ7512CXL7T -e --accept-package-agreements`)
2. **Close and reopen** your terminal (PowerShell or Git Bash), then run:
   ```
   py install 3.13
   ```
   If it asks about adding a folder to PATH, answering **Yes** is fine.
3. Check it:
   ```
   py -V:3.13 --version
   ```
   You should see `Python 3.13.x`.

### 3. VS Code (recommended)

Download from **https://code.visualstudio.com**, install, then open it and install two extensions from the Extensions panel: **Python** and **Jupyter** (both by Microsoft).

### Windows troubleshooting

| Problem | Fix |
|---|---|
| `py` or `git` is "not recognized" | Close **every** terminal and open a new one. Still broken? Restart the laptop |
| Typing `python` opens the Microsoft Store | Settings → Apps → Advanced app settings → **App execution aliases**: turn off the two "App Installer python" entries, turn on "Python (default)" |
| `.venv\Scripts\activate` says running scripts is disabled | In PowerShell run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, answer `Y`, try again. Or use Git Bash: `source .venv/Scripts/activate` |

---

## Mac

### 1. Git

Open **Terminal** (press Cmd + Space, type "Terminal") and run:

```bash
git --version
```

If Git isn't installed, macOS pops up a box offering to install the **command line developer tools**. Click **Install** and wait (5–15 min). Then run `git --version` again.
(No pop-up? Run `xcode-select --install`.)

### 2. Python 3.13

The Python that ships with the Mac developer tools is too old, so install 3.13 from python.org:

1. Go to **https://www.python.org/downloads/macos/**, find the latest **Python 3.13.x** release and download the **macOS 64-bit universal2 installer** (`.pkg`).
2. Run it and click through.
3. **Important:** open **Applications → Python 3.13** and double-click **Install Certificates.command**. Without this, Python can't download the match data.
4. Check it in a new Terminal window:
   ```bash
   python3.13 --version
   ```

Have Homebrew? `brew install python@3.13` works too.

### 3. VS Code (recommended)

Download from **https://code.visualstudio.com**, drag it into Applications, then install the **Python** and **Jupyter** extensions (both by Microsoft).

### Mac troubleshooting

| Problem | Fix |
|---|---|
| `python3.13: command not found` | Close Terminal and reopen it. Still missing? Re-run the installer |
| `SSL: CERTIFICATE_VERIFY_FAILED` when loading data | You skipped **Install Certificates.command** (step 3 above) |
| `xcrun: error: invalid active developer path` | Run `xcode-select --install` |

---

## Everyone: GitHub account and final check

1. **Make a GitHub account** at **https://github.com/signup** (your UCSD email is fine).
2. **Tell Git who you are**, using the email from your GitHub account:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@ucsd.edu"
   ```
3. **Final check.** In a new terminal, all three should print a version:

   | | Windows | Mac |
   |---|---|---|
   | Git | `git --version` | `git --version` |
   | Python | `py -V:3.13 --version` | `python3.13 --version` |
   | Git name | `git config user.name` | `git config user.name` |

All three work? Go back to the [README](README.md#get-the-code-fork-then-clone) and continue from **Get the code**.

The first time you push, a GitHub sign-in window opens in your browser. Sign in there. GitHub doesn't accept your account password in the terminal.

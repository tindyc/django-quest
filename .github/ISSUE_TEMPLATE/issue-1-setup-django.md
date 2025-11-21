---
name: "Issue 1 – Setup Django & Dependencies"
about: "Start the Quest by creating your virtual environment, installing Django, and generating requirements.txt"
title: "Issue 1 – Setup Django & Dependencies"
labels: issue-1
assignees: ""
---

# 🧙‍♀️ Issue 1 -- Setup Django & Dependencies

Welcome to the first challenge of your Django Quest!

In this step, you'll prepare your local environment, create a virtual
environment, upgrade your tools, install Django, and generate a
`requirements.txt` file that the automated checker will validate.

Take your time! Every later Quest depends on this foundation!

------------------------------------------------------------------------

## 🖥 1. Clone *your* repository

> Make sure you are working inside **your own repo**, created from
> **Use this template → Create a new repository**.

1.  Open your repo on GitHub
2.  Click the green **Code** button
3.  Copy the **HTTPS** link
4.  Open **VS Code**
5.  Press:
    -   Cmd + Shift + P (macOS)
    -   Ctrl + Shift + P (Windows)
6.  Type: Git: Clone
7.  Paste your repo URL
8.  Choose a folder
9.  When prompted, click **Open**

------------------------------------------------------------------------

## 🧪 2. Open a Terminal in VS Code

-   Go to **View → Terminal**
-   Make sure the terminal path ends with your project folder

------------------------------------------------------------------------

## 🐍 3. Create and Activate Your Virtual Environment

### macOS / Linux

``` bash
python3 -m venv venv
source venv/bin/activate
```

### Windows (PowerShell)

``` powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

When it works, your terminal line will begin with:

    (venv)

------------------------------------------------------------------------

## ⚠️ Before Installing Django

Many students run into issues at this point --- so pause and check:

### ✅ 1. **Are you inside your virtual environment?**

Run:

``` bash
which python
```

or on Windows:

``` powershell
Get-Command python
```

You should see a path pointing to your **venv** folder.

If not, activate your environment again.

### ✅ 2. **Upgrade pip first (VERY IMPORTANT!)**

This prevents outdated-package errors.

``` bash
pip install --upgrade pip
```

> If you are facing any **issues**, please refer to the
> Troubleshooting guide at the bottom.
------------------------------------------------------------------------

## 📦 3. Install Django

``` bash
pip install "Django>=4.2,<6.0"
```

Double-check installation:

``` bash
python -m django --version
```

------------------------------------------------------------------------

## 📄 4. Create `requirements.txt`

Record your installed packages:

``` bash
pip freeze --local > requirements.txt
```

Verify it exists:

``` bash
ls
```

Open it --- you should see a line containing **Django**.

------------------------------------------------------------------------

## 🌱 5. Create Your Issue 1 Branch

``` bash
git checkout -b issue-1-setup
```

Your branch **must** start with `issue-1-` or the validator will not
run.

------------------------------------------------------------------------

## 💾 6. Commit Your Work

``` bash
git add requirements.txt
git commit -m "Issue 1: Install Django and create requirements.txt"
```

------------------------------------------------------------------------

## 🚀 7. Push Your Branch to GitHub

``` bash
git push -u origin issue-1-setup
```

------------------------------------------------------------------------

## 🔁 8. Open a Pull Request

Base branch → `main`\
Compare branch → `issue-1-setup`

Then click **Create pull request**.

------------------------------------------------------------------------

## 🤖 9. Wait for the Django Quest Checker

-   Open the **Checks** tab\
-   You'll see either:
    -   ✅ Everything correct\
    -   ❌ Something needs fixing

If it fails:

1.  Read the error message\
2.  Fix locally\
3.  Run:

``` bash
git add .
git commit -m "Fix Issue 1 CI failure"
git push
```

The CI will rerun.

------------------------------------------------------------------------

## 🟢 10. Merge & Close the Issue

Once green:

1.  Click **Merge pull request**\
2.  Click **Confirm merge**\
3.  Return to the Issue and click **Close issue**

Closing this issue unlocks **Issue 2**.

------------------------------------------------------------------------
## Troubleshooting and Tips

<details>
<summary><strong>💡 Common Mistakes & Helpful Tips (click to expand)</strong></summary>

### 🧩 Virtual Environment Problems

#### ❌ “`pip: command not found`”
**Cause:** You're not inside your virtual environment.  
**Fix:** Activate it again:

- macOS/Linux  
  ```bash
  source venv/bin/activate
  ```
- Windows PowerShell  
  ```powershell
  .\venv\Scripts\Activate.ps1
  ```

---

#### ❌ “Python points to the global interpreter”
Check with:

```bash
which python
```

or on Windows:

```powershell
Get-Command python
```

**Expected:** a path ending with `/venv/bin/python` or `\venv\Scripts\python.exe`  
If not, activate again or recreate your venv.

---

### 🪟 Windows-Specific Issues

#### ❌ “Permission denied” while activating venv  
Windows blocks script execution by default.

Fix temporarily for this session:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then activate again.

---

### 🛠 Installation & Package Problems

#### ❌ Forgot to upgrade pip (VERY common!)
Old pip versions cause dependency errors.

Fix:
```bash
pip install --upgrade pip
```

---

#### ❌ “Django installed, but `django-admin` doesn’t run”
This happens when Django was installed **globally**, not in your venv.

Fix:
1. Make sure venv is activated
2. Reinstall Django:
   ```bash
   pip install "Django>=4.2,<6.0"
   ```

---

### 📄 requirements.txt Gotchas

#### ❌ `requirements.txt` is empty or missing Django  
Make sure you installed Django *after* activating the venv.

Then regenerate:

```bash
pip freeze --local > requirements.txt
```

---

### 🔍 Quick Self-Check Before Moving On

- Does your terminal show **(venv)** at the start?
- Does this command show a Django version?  
  ```bash
  python -m django --version
  ```
- Does your `requirements.txt` include a `Django==X.X.X` line?

If all yes → you’re good to continue!

</details>

------------------------------------------------------------------------
## 🎉 Great work!

You've completed the first step of your Django Quest! Your
environment is ready and Django is installed.

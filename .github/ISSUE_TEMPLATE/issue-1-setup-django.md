# 🧙‍♀️ Issue 1 -- Setup Django & Dependencies

Welcome to the first challenge of your Django Quest!

In this step, you'll prepare your local environment, create a virtual
environment, upgrade your tools, install Django, and generate a
`requirements.txt` file that the automated checker will validate.

Take your time --- every later Quest depends on this foundation!

------------------------------------------------------------------------

## 🖥 1. Clone *your* repository

> Make sure you are working inside **your own repo**, created from\
> **Use this template → Create a new repository**.

1.  Open your repo on GitHub\
2.  Click the green **Code** button\
3.  Copy the **HTTPS** link\
4.  Open **VS Code**\
5.  Press:
    -   Cmd + Shift + P (macOS)\
    -   Ctrl + Shift + P (Windows)\
6.  Type: Git: Clone\
7.  Paste your repo URL\
8.  Choose a folder\
9.  When prompted, click **Open**

------------------------------------------------------------------------

## 🧪 2. Open a Terminal in VS Code

-   Go to **View → Terminal**\
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

## ⚠️ NEW SECTION: Before Installing Django

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

### Common mistakes

  ---------------------------------------------------------------------------------------------------------------------------------
  Problem                    What it means                           Fix
  -------------------------- --------------------------------------- --------------------------------------------------------------
  `pip: command not found`   You aren't in your virtual environment  Re-run the correct *activate* command

  Django appears installed   Installed globally instead of in venv   Activate venv → reinstall Django
  but `django-admin` doesn't                                         
  work                                                               

  `Permission denied` while  Execution policy is blocking scripts    Run:
  activating on Windows                                              `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`
  ---------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

## 📦 4. Install Django

``` bash
pip install "Django>=4.2,<6.0"
```

Double-check installation:

``` bash
python -m django --version
```

------------------------------------------------------------------------

## 📄 5. Create `requirements.txt`

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

## 🌱 6. Create Your Issue 1 Branch

``` bash
git checkout -b issue-1-setup
```

Your branch **must** start with `issue-1-` or the validator will not
run.

------------------------------------------------------------------------

## 💾 7. Commit Your Work

``` bash
git add requirements.txt
git commit -m "Issue 1: Install Django and create requirements.txt"
```

------------------------------------------------------------------------

## 🚀 8. Push Your Branch to GitHub

``` bash
git push -u origin issue-1-setup
```

------------------------------------------------------------------------

## 🔁 9. Open a Pull Request

Base branch → `main`\
Compare branch → `issue-1-setup`

Then click **Create pull request**.

------------------------------------------------------------------------

## 🤖 10. Wait for the Django Quest Checker

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

## 🟢 11. Merge & Close the Issue

Once green:

1.  Click **Merge pull request**\
2.  Click **Confirm merge**\
3.  Return to the Issue and click **Close issue**

Closing this issue unlocks **Issue 2**.

------------------------------------------------------------------------

## 🎉 Great work!

You've completed the first step of your Django Quest --- your
environment is ready and Django is installed.

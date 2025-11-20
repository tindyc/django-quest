---
name: "Issue 1 – Setup: Install Django & Dependencies"
about: "Create a virtualenv, install Django, and generate requirements.txt"
title: "Issue 1 – Setup Django"
labels: ["issue-1"]
assignees: ""
---

## 🎯 Goal

Set up your Python environment, install Django, and generate a `requirements.txt` file that records your dependencies.

By the end of this Issue:

- Your project will have a working Python virtual environment.
- Django will be installed.
- A `requirements.txt` will exist and contain Django.
- You will have created a branch, made a commit, and opened a Pull Request.

---

## 🧩 Placeholders

Throughout this workshop you will see placeholders like:

- `<project_name>` – the name of your Django project (e.g. `blogsite`, `taskmanager`)
- `<app_name>` – the name of your Django app (e.g. `blog`, `tasks`)

**Do NOT type the `<` or `>` characters.** Replace them with your own names.

---

## ✅ Tasks

> 💡 You can choose any idea for your Django project (blog, todo list, recipe manager, shop, etc.). These steps only prepare your environment.

### 1. Create a virtual environment

Open a terminal in the root of your repository folder.

macOS / Linux:

```bash
python -m venv venv
source venv/bin/activate
```

Windows (PowerShell):

```powershell
python -m venv venv
.env\Scripts\Activate.ps1
```

If this worked, your prompt should show something like `(venv)` at the beginning.

---

### 2. Upgrade pip (recommended)

```bash
pip install --upgrade pip
```

This helps avoid some dependency issues.

---

### 3. Install Django

```bash
pip install "Django>=4.2,<6.0"
```

After this, Django should be available in your virtual environment.

---

### 4. Freeze dependencies into `requirements.txt`

```bash
pip freeze --local > requirements.txt
```

This will create (or overwrite) `requirements.txt` with a list of installed packages.

Make sure `requirements.txt` is tracked by Git:

```bash
git status
git add requirements.txt
```

---

## 🤖 What CI (GitHub Actions) will check

When you open a Pull Request from a branch starting with `issue-1-` (or any later issue), GitHub Actions will:

- Check that `requirements.txt` exists.
- Check that `requirements.txt` contains Django.

If something is wrong, the Action will fail and show an error message telling you what to fix.

> 🔁 **Important:** Checks only run if your branch name starts with `issue-X-`.  
> If you see a notice like:
>
> `No Django Quest checks ran because your branch name does not start with 'issue-X-'`
>
> Then your branch name is the problem, not your code.

---

## 💾 Git & GitHub Workflow (Step-by-step)

1. **Create a branch for this Issue**  
   (Branch name must start with `issue-1-`):

   ```bash
   git checkout -b issue-1-setup-django
   ```

2. **Check what changed:**

   ```bash
   git status
   ```

3. **Stage your changes:**

   ```bash
   git add requirements.txt
   ```

   (If you created other files you want to track, add them too.)

4. **Commit your work:**

   ```bash
   git commit -m "Add Django and requirements.txt"
   ```

5. **Push your branch to GitHub:**

   ```bash
   git push -u origin issue-1-setup-django
   ```

6. **Open a Pull Request (PR):**

   - Go to your repository on GitHub.
   - You should see a message suggesting to create a PR from `issue-1-setup-django`.
   - Click **“Compare & pull request”** (or **“New pull request”** and select your branch).
   - Make sure the base branch is `main` and the compare branch is `issue-1-setup-django`.
   - Submit the PR.

7. **Check CI status:**

   - On the PR page, scroll to the “Checks” section.
   - Wait for the “Django Setup Quest Checker” to finish.
   - If it fails, read the error message carefully; it tells you what to fix.

8. **Merge the PR when green:**

   - Once CI is green ✅ and you’re happy with the changes, click **“Merge pull request”**.
   - After merging, **close this Issue**.

Closing this Issue (labelled `issue-1`) will automatically open **Issue 2** for you.

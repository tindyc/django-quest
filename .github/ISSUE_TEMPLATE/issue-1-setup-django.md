---
name: "Issue 1 – Setup Django & Dependencies"
about: "Start the Quest by creating your virtual environment, installing Django, and generating requirements.txt"
title: "Issue 1 – Setup Django & Dependencies"
labels: issue-1
assignees: ""
---

# 🧙‍♀️ Issue 1 – Setup Django & Dependencies  

Welcome to the first stage of your Django Setup Quest!  
In this step, you’ll prepare your computer, install Django, and generate your `requirements.txt` file.

Follow all steps carefully — everything later in the Quest depends on this setup.

---

## 🖥 1. Clone *this* repository to your computer

> If you haven’t already, first create **your own copy** of this project by clicking  
> **Use this template → Create a new repository** on GitHub.  
> These steps assume you are now working in **your own repo**.

1. On your repo page, click the green **Code** button.
2. Copy the **HTTPS** link.
3. Open **VS Code**.
4. Press:
   - **Cmd + Shift + P** (macOS), or  
   - **Ctrl + Shift + P** (Windows)
5. Type: `Git: Clone`
6. Paste your repo URL.
7. Choose a folder on your computer.
8. When VS Code asks, click **Open** to load the project.

---

## 🧪 2. Open a terminal in VS Code

In VS Code:

- Go to **View → Terminal**
- Confirm the terminal path matches your project folder (you should see your repo folder at the end of the path).

---

## 🐍 3. Create and activate your virtual environment

This keeps your project’s Python packages isolated (very important!).

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### Windows (PowerShell)

```powershell
python -m venv venv
.env\Scripts\Activate.ps1
```

If it worked, your terminal prompt will start with:

```text
(venv) …
```

---

## 📦 4. Install Django

Run:

```bash
pip install "Django>=4.2,<6.0"
```

---

## 📄 5. Create `requirements.txt`

This file records your installed packages.  
The automated checker will validate this file in the next step.

Run:

```bash
pip freeze --local > requirements.txt
```

Confirm it exists in your folder:

```bash
ls
```

You should see:

```text
requirements.txt
```

Open it — you should see a line containing **Django**.

---

## 🌱 6. Create your Issue 1 branch

Each step of the Quest must be done in its own branch.

Run:

```bash
git checkout -b issue-1-setup
```

⚠️ **IMPORTANT:**  
Your branch **must** start with `issue-1-`  
or the validator will *not* run on the PR.

---

## 💾 7. Commit your work

```bash
git add requirements.txt
git commit -m "Issue 1: Install Django and create requirements.txt"
```

---

## 🚀 8. Push your branch to GitHub

```bash
git push -u origin issue-1-setup
```

---

## 🔁 9. Open a Pull Request (PR)

1. Go to your repository on GitHub.
2. Click the **Compare & pull request** banner, or go to the **Pull requests** tab and click **New pull request**.
3. Make sure:
   - **Base branch:** `main`
   - **Compare branch:** `issue-1-setup`
4. Click **Create pull request**.

---

## 🤖 10. Wait for the Django Quest Checker (CI)

Your PR now triggers automated validation.

- Go to the **Checks** tab
- Wait 30–60 seconds
- You will see:
  - **Green (✅)** → You did everything correctly  
  - **Red (❌)** → Something is missing or incorrect  

If the check fails:

1. Read the error message (it will point to the file / step that failed).  
2. Fix the issue locally.  
3. Run:

   ```bash
   git add .
   git commit -m "Fix Issue 1 CI failure"
   git push
   ```

4. The check will rerun automatically.

---

## 🟢 11. Merge the PR & close this Issue

Once CI is **green**:

1. Click **Merge pull request**.
2. Click **Confirm merge**.
3. Return to this Issue.
4. Click **Close issue**.

Closing this issue automatically unlocks **Issue 2** in your repository.

---

## 🎉 Great work!

You've completed the first step of your Django Quest — your environment is ready and Django is installed.

➡️ When Issue 2 appears, move on to **Project Core: Create Project Structure**.

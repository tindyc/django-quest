---
name: "Issue 6 – Superuser & Admin"
about: "Create a Django superuser and log in to the admin interface"
title: "Issue 6 – Superuser & Admin"
labels:
  - issue-6
assignees: ""
---

# 🔐 Issue 6 – Superuser & Admin  

In this final step you will:

- Create a Django superuser
- Log in to the admin site
- Confirm your model appears (if you registered it in Issue 5)
- Finish the Quest! 🎉

---

## 🔄 1. Update local `main` and create a new branch

```bash
git checkout main
git pull origin main
git checkout -b issue-6-superuser
```

---

## 👑 2. Create a superuser

Run:

```bash
python manage.py createsuperuser
```

Follow the prompts:

- Username
- Email address (optional)
- Password (Type carefully; Django won’t show it as you type.)

If Django warns that the password is too common or too short, you can choose to override for local testing.

---

## 🧪 3. Run the development server

```bash
python manage.py runserver
```

Open `http://127.0.0.1:8000/admin/` in your browser.

Log in with the superuser credentials you just created.

You should see the Django admin dashboard.

If you registered your model in Issue 5, you should also see your app and model listed.

---

## 💾 4. Stop the server & commit your work

Stop the server with **Ctrl + C** in the terminal.

There are no code changes for `createsuperuser` itself, but if you made any tweaks (e.g. to `admin.py`), commit them now:

```bash
git status
git add .
git commit -m "Issue 6: Create superuser and verify admin"
```

If no files changed, you can still push the branch to record completion of this step.

---

## 🚀 5. Push your branch

```bash
git push -u origin issue-6-superuser
```

---

## 🔁 6. Open a Pull Request (PR)

- Open a PR from `issue-6-superuser` into `main`.
- Create the PR.

The CI will run one final time, executing `python manage.py check` to ensure your project is healthy.

---

## 🟢 7. Merge the PR & close this Issue

When CI is green:

1. Merge the PR.
2. Close this Issue.

Closing this issue (labelled `issue-6`) will automatically open **Issue 7**.

<details>
<summary><strong>📌 How to Close This Issue (and Unlock the Next One)</strong></summary>

When your pull request has been **successfully merged**, you must **close this issue manually** to trigger the next Quest.

### ✅ Steps to Close the Issue

1. Open your repository on GitHub  
2. Click the **Issues** tab  
3. Open the issue you just completed  
4. Scroll down and click **Close issue**  
5. Wait a few seconds — the **next Quest issue will be created automatically**

> ⚠️ **Important:**  
> Merging the pull request is **not enough**.  
> You *must* close the issue yourself for the next Quest to appear.

</details>

---

## 📝 Summary

<details>
<summary><strong>Click to expand</strong></summary>

### 🌟 What You Did  
- Created superuser  
- Logged into Django admin  
- Checked your model appears

### 🔧 Commands

#### Create superuser
```bash
python manage.py createsuperuser
```

#### Run server to access admin
```bash
python manage.py runserver
```

Then visit:  
`http://127.0.0.1:8000/admin/`

</details>


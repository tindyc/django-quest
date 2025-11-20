---
name: "Issue 6 – Superuser & Admin"
about: "Create a Django superuser and log in to the admin interface"
title: "Issue 6 – Superuser & Admin"
labels: issue-6
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

Closing this final issue completes the Quest.  
Another workflow may append a **“Quest Complete”** message to your README.

---

## 🎉 QUEST COMPLETE!

You have now:

- Created and configured a Django project
- Installed dependencies and captured them in `requirements.txt`
- Created and registered a Django app
- Wired URLs to views and served a real HTTP response
- Defined models, created migrations, and applied them
- Created a superuser and logged into the Django admin

This project is now a solid foundation for any Django application you want to build next. 🚀

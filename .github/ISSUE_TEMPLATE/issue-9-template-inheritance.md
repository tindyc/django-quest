---
name: "Issue 9 – Template Inheritance & Base Layout"
about: "Create a shared base layout using Django template inheritance"
title: "Issue 9 – Template Inheritance & Base Layout"
labels:
  - issue-9
---

# 🎨 Issue 9 – Template Inheritance & Base Layout

In this issue, you will clean up your templates using **Django template inheritance**, a powerful feature that stops you from repeating the same HTML in every file.

You can follow the **BlogPost** example or apply this to any project idea you've chosen.

---

## 🧭 What You Should Already Have

From Issues 1–8, you should now have:

- A Django project & app  
- A working `BlogPost` model  
- A list page: `/blog/`  
- A detail page: `/blog/<id>/`  
- Templates in your app, for example:

  ```text
  <app_name>/templates/<app_name>/blog_list.html
  <app_name>/templates/<app_name>/blog_detail.html
  ```

Each of those templates currently contains **full HTML markup**, but they share a lot of repeated structure.

In this issue you will:

- Create a shared `base.html` layout  
- Make your list and detail templates **extend** that base  
- Upgrade your `home` view (from Issue 4) to use the base template too  

---

## 🔄 0. Update `main` and Create Your Issue 9 Branch

Before doing anything, create your new branch:

```bash
git checkout main
git pull origin main
git checkout -b issue-9-template-inheritance
```

> 💡 Your branch **must** start with `issue-9-` so the Quest checker knows which issue you are working on.

---

## 🧱 1. Why Template Inheritance?

Right now your templates probably look something like this:

- They each have their own `<html>`, `<head>`, `<body>` tags  
- They duplicate the header, footer, and basic layout  
- If you want to change the layout, you would have to update every file

Instead, Django allows you to:

1. Put the shared structure into **one** template (e.g. `base.html`), and  
2. Have other templates **extend** it and fill in only the changing parts.

```text
base.html
   ↓
   ├── blog_list.html extends base
   └── blog_detail.html extends base
```

You edit **one** layout and all pages get the new look.

---

## ✅ 2. Create `base.html` With Django Quest Branding

Create this file in your app:

```text
<app_name>/templates/<app_name>/base.html
```

If your app is called `blog`, that path is:

```text
blog/templates/blog/base.html
```

Add this content:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>
      {% block title %}Django Quest{% endblock %}
    </title>

    <!-- Simple embedded styles so you don't need a separate CSS file yet -->
    <style>
      body {
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
          sans-serif;
        margin: 0;
        padding: 0;
        background: #0b1020;
        color: #f5f5f5;
      }

      header {
        background: radial-gradient(circle at top, #1db660, #07101f);
        padding: 1.5rem 2rem;
        color: #ffffff;
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      }

      .dq-logo {
        font-weight: 700;
        letter-spacing: 0.03em;
        display: flex;
        align-items: center;
        gap: 0.5rem;
        font-size: 1.2rem;
      }

      .dq-logo span.icon {
        font-size: 1.4rem;
      }

      nav {
        margin-top: 0.75rem;
      }

      nav a {
        color: #e3ffe9;
        text-decoration: none;
        margin-right: 1rem;
        font-size: 0.95rem;
      }

      nav a:hover {
        text-decoration: underline;
      }

      main {
        max-width: 800px;
        margin: 2rem auto;
        padding: 0 1.5rem 3rem;
      }

      footer {
        border-top: 1px solid rgba(255, 255, 255, 0.08);
        padding: 1.5rem;
        text-align: center;
        font-size: 0.9rem;
        background: #050814;
        color: #c7d1d9;
      }

      .badge {
        margin-top: 0.75rem;
      }

      .card {
        background: rgba(10, 16, 35, 0.95);
        border-radius: 0.75rem;
        padding: 1.5rem;
        border: 1px solid rgba(255, 255, 255, 0.06);
        box-shadow: 0 16px 30px rgba(0, 0, 0, 0.45);
      }

      a {
        color: #6be6a8;
      }

      a:hover {
        color: #9cf5c7;
      }
    </style>
  </head>
  <body>
    <header>
      <div class="dq-logo">
        <span class="icon">🐍</span>
        <span>Django Quest</span>
      </div>
      <nav>
        <a href="{% url 'home' %}">Home</a>
        <a href="{% url 'blog_list' %}">Blog</a>
      </nav>
    </header>

    <main>
      <div class="card">
        {% block content %}
        <!-- Child templates inject page-specific content here -->
        {% endblock %}
      </div>
    </main>

    <footer>
      <div>Built as part of the <strong>Django Quest</strong> 🧭</div>
      <div class="badge">
        <img
          alt="Django Quest Badge"
          src="https://img.shields.io/badge/Django_Quest-Learning_in_Progress-44aa44?style=for-the-badge&logo=django&logoColor=white"
        />
      </div>
    </footer>
  </body>
</html>
```

### 💡 What to pay attention to (and what to ignore)

You **do not** need to understand every CSS line yet. You can treat it as “starter styling” that makes your pages look nicer.

The **important Django pieces** are:

- `{% block title %}…{% endblock %}`  
  → Child templates can override the page `<title>`.

- `{% block content %}…{% endblock %}`  
  → Child templates put their main HTML content in here.

- `{% url 'home' %}` and `{% url 'blog_list' %}`  
  → These rely on you having `home` and `blog_list` named URL patterns.

Everything else is just branding / layout.

---

## ✅ 3. Update `blog_list.html` to Extend `base.html`

Open:

```text
<app_name>/templates/<app_name>/blog_list.html
```

Replace **all** existing content with:

```django
{% extends "<app_name>/base.html" %}

{% block title %}Blog Posts – Django Quest{% endblock %}

{% block content %}
  <h1>Blog Posts</h1>

  {% if posts %}
    <ul>
      {% for post in posts %}
        <li>
          <a href="{% url 'blog_detail' post.id %}">
            <strong>{{ post.title }}</strong>
          </a>
          <br />
          <em>{{ post.created_at|date:"F j, Y" }}</em>
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <p>No posts yet. Add some from the admin panel!</p>
  {% endif %}
{% endblock %}
```

If your app is actually named `blog`, you should use:

```django
{% extends "blog/base.html" %}
```

instead of `<app_name>`.

### 🔍 What each key line does

- `{% extends "<app_name>/base.html" %}`  
  → Says: “Start with the layout defined in `base.html` and fill in its blocks.”

- `{% block title %}...{% endblock %}`  
  → Overrides the `<title>` block defined in `base.html`.

- `{% block content %}`  
  → Fills in the main content area inside the card.

- The `{% for post in posts %}` loop  
  → Uses the `posts` list passed from your `blog_list` view to render links.

---

## ✅ 4. Update `blog_detail.html` to Extend `base.html`

Open:

```text
<app_name>/templates/<app_name>/blog_detail.html
```

Replace **all** existing content with:

```django
{% extends "<app_name>/base.html" %}

{% block title %}{{ post.title }} – Django Quest{% endblock %}

{% block content %}
  <p><a href="{% url 'blog_list' %}">← Back to all posts</a></p>

  <article>
    <h1>{{ post.title }}</h1>
    <p><em>Published: {{ post.created_at|date:"F j, Y, H:i" }}</em></p>
    <p>{{ post.content }}</p>
  </article>
{% endblock %}
```

Again, if your app is called `blog`, replace `<app_name>` with `blog`.

### 🔍 Key things happening here

- We still receive a `post` object from the `blog_detail` view.
- We use `{{ post.title }}` inside:
  - the `<title>` block
  - the `<h1>`
- We continue to format the date with the `date` filter.
- The back link uses `{% url 'blog_list' %}` so you don't hard-code `/blog/`.

---

## ✅ 5. Upgrade the `home` View from Issue 4 (Important!)

Back in **Issue 4**, you created a very simple `home` view that returned plain text, like:

```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello from your Django Quest app!")
```

Now that you have a proper layout and templates, it's time to **upgrade** this view so it also uses `base.html`.

### 🏠 Step 1 – Create `home.html`

Create:

```text
<app_name>/templates/<app_name>/home.html
```

Add:

```django
{% extends "<app_name>/base.html" %}

{% block title %}Home – Django Quest{% endblock %}

{% block content %}
  <h1>Welcome to your Django Quest project! 🚀</h1>
  <p>Your Django project now uses a shared base layout and real templates.</p>

  <p>Next steps you can try:</p>
  <ul>
    <li><a href="{% url 'blog_list' %}">View your blog posts</a></li>
    <li>Add or edit posts in the Django admin</li>
  </ul>
{% endblock %}
```

(If your app is called `blog`, use `blog/base.html` in the `{% extends %}` line.)

### 🧠 How this works

- This template extends the same `base.html` layout as your blog pages.
- It fills in the `title` and `content` blocks.
- The navigation in `base.html` will automatically show the **Home** and **Blog** links on this page too.

---

### 🛠 Step 2 – Replace the Old `home` View

Open:

```text
<app_name>/views.py
```

Update it so your `home` view uses `render` instead of `HttpResponse`.

Your file should now look roughly like this:

```python
from django.shortcuts import render
from .models import BlogPost  # if you are using the BlogPost example

def home(request):
    # Render the homepage using the shared base layout and a home template.
    return render(request, "<app_name>/home.html")

def blog_list(request):
    # Show a list of all blog posts.
    posts = BlogPost.objects.all().order_by("-created_at")
    return render(request, "<app_name>/blog_list.html", {"posts": posts})

# If you have blog_detail here as well, leave it as-is.
```

If your app is actually `blog`, the render calls should be:

```python
return render(request, "blog/home.html")
return render(request, "blog/blog_list.html", {"posts": posts})
```

#### 🔍 What changed compared to Issue 4?

- We **removed** the `HttpResponse` version of `home`.
- We now use `render(request, template_name, context)` to:
  - load the `home.html` template
  - go through `base.html`
  - inject the content into the layout

This keeps everything consistent with your list and detail views.

---

### ✅ Step 3 – Check Your URL Configuration

Open:

```text
<app_name>/urls.py
```

Make sure the root URL still points to `home`:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.home, name="home"),
    path("blog/", views.blog_list, name="blog_list"),
    # path("blog/<int:post_id>/", views.blog_detail, name="blog_detail"),  # if you added Issue 8
]
```

Your project-level `urls.py` (e.g. `django_project/urls.py`) should still include your app URLs:

```python
from django.urls import path, include

urlpatterns = [
    path("", include("<app_name>.urls")),
]
```

Replace `<app_name>` with your real app name when you set this up.

---

## 🖥️ 6. Test Your Work

Run:

```bash
python manage.py runserver
```

Check these URLs:

1. **Home page**

   ```text
   http://127.0.0.1:8000/
   ```

   You should see your Django Quest–branded layout and the welcome content from `home.html`.

2. **Blog list**

   ```text
   http://127.0.0.1:8000/blog/
   ```

   You should see the list of posts, with each title linking to the detail page.

3. **Blog detail**

   ```text
   http://127.0.0.1:8000/blog/1/
   ```

   (Or another valid ID.)  
   You should see the detail page inside the same layout, with the back link to all posts.

If all three pages share the same header, footer, and general layout, your template inheritance is working 🎉

---

## 🔐 7. Commit and Push Your Changes

```bash
git add .
git commit -m "Issue 9 – Add base template and update views to use inheritance"
git push -u origin issue-9-template-inheritance
```

---

## 🚀 8. Open a Pull Request

1. Open GitHub in your browser.  
2. Create a PR from:

   ```text
   issue-9-template-inheritance → main
   ```

3. Use this title:

   ```text
   Issue 9 – Template Inheritance & Base Layout
   ```

4. Submit the PR and wait for the automated checker.  
5. When CI is green: **merge the PR and close this Issue**.

---

<details>
<summary><strong>📌 How to Close This Issue (Required)</strong></summary>

1. Go to the **Issues** tab in your repository.  
2. Open this Issue.  
3. Click **Close issue**.  
4. Wait a few seconds for the next Quest Issue to appear automatically.

> ⚠️ Closing the PR is **not** enough.  
> You must close the Issue itself to trigger the sequencer.
</details>

---

## 📝 Summary

### In this issue, you learned:

- How Django template inheritance works  
- How to create a shared layout (`base.html`) with branding  
- How to use `{% extends %}` and `{% block %}` in child templates  
- How to upgrade a basic `HttpResponse` view to a real template-based view  
- How your home, list, and detail pages can all share one consistent design  

### You now have:

- A clean, professional template structure  
- A Django Quest–branded layout used across your site  
- A more scalable app ready for the final Quest steps 🎉

Amazing job — your project now both **works well** and **looks** like a real Django application! 🚀

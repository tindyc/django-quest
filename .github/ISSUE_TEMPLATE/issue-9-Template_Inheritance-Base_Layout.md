---
name: "Issue 9 – Template Inheritance & Base Layout"
about: "Create a shared base layout using Django template inheritance"
title: "Issue 9 – Template Inheritance & Base Layout"
labels:
  - issue-9
---

# 🎨 Issue 9 – Template Inheritance & Base Layout

In this issue, you will clean up your templates using **Django Template Inheritance**, a powerful feature that prevents repeating the same HTML in every file.

You can follow the **BlogPost** example or apply this to any project idea you’ve chosen.

---

## 🧭 What You Should Already Have

From Issues 1–8, you now have:

- A Django project & app  
- A working `BlogPost` model  
- A list page: `/blog/`  
- A detail page: `/blog/<id>/`  
- Templates:
  - `blog_list.html`
  - `blog_detail.html`

Each of those templates currently contains **full HTML markup**, but they share a lot of repeated structure.

---

# 🔄 0. Update `main` and Create Your Issue 9 Branch

Before doing anything, create your new branch:

```bash
git checkout main
git pull origin main
git checkout -b issue-9-template-inheritance
```

> 💡 Your branch must start with `issue-9-` so the Quest Checker knows which issue you are working on.

---

# 🧱 1. Why Template Inheritance?

Right now both templates contain similar boilerplate:

- `<html>`
- `<head>`
- `<body>`
- Headers
- Titles

This is duplicated code, which is harder to maintain.

Instead, Django allows you to create a shared template, e.g.:

```
base.html
```

Then each page simply **extends** it and fills in blocks.

---

## 📝 Diagram: How Template Inheritance Works

```
base.html
   ↓
   ├── blog_list.html extends base
   └── blog_detail.html extends base
```

Or visually:

```
Shared Layout (base.html)
   ├── Block: title
   └── Block: content
       ⤷ Filled by child templates
```

---

# ✅ 2. Create `base.html`

Create the folder:

```
<app_name>/templates/<app_name>/base.html
```

Add:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>{% block title %}My Django Site{% endblock %}</title>
  </head>
  <body>
    <header>
      <nav>
        <a href="{% url 'home' %}">Home</a> |
        <a href="{% url 'blog_list' %}">Blog</a>
      </nav>
      <hr />
    </header>

    <main>
      {% block content %}
      <!-- Child templates inject content here -->
      {% endblock %}
    </main>

    <footer>
      <hr />
      <p>Built in the Django Quest ✨</p>
    </footer>
  </body>
</html>
```

---

# ✅ 3. Update `blog_list.html` to Extend `base.html`

Open:

```
<app_name>/templates/<app_name>/blog_list.html
```

Replace ALL existing content with:

```django
{% extends "<app_name>/base.html" %}

{% block title %}Blog Posts{% endblock %}

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

---

# ✅ 4. Update `blog_detail.html` to Extend `base.html`

Open:

```
<app_name>/templates/<app_name>/blog_detail.html
```

Replace ALL existing content with:

```django
{% extends "<app_name>/base.html" %}

{% block title %}{{ post.title }}{% endblock %}

{% block content %}
  <p><a href="{% url 'blog_list' %}">← Back to all posts</a></p>

  <article>
    <h1>{{ post.title }}</h1>
    <p><em>Published: {{ post.created_at|date:"F j, Y, H:i" }}</em></p>
    <p>{{ post.content }}</p>
  </article>
{% endblock %}
```

---

# 🖥️ 5. Test Your Work

Start your server:

```bash
python manage.py runserver
```

Check:

### `/blog/`
- Page loads  
- Uses header/footer  
- Shows the updated layout  

### `/blog/<id>/`
- Uses the inherited layout  
- Shows dynamic title  
- Displays the post content correctly  

If everything looks visually consistent, your base template is working!

---

# 🔐 6. Commit and Push Your Changes

```bash
git add .
git commit -m "Issue 9 – Add base template with Django template inheritance"
git push -u origin issue-9-template-inheritance
```

---

# 🚀 7. Open a Pull Request

1. Open GitHub  
2. Create a PR from:

```
issue-9-template-inheritance → main
```

3. Title it:

```
Issue 9 – Template Inheritance & Base Layout
```

4. Submit the PR  
5. Wait for the automated checker  
6. When green: **Merge the PR & close this Issue**

---

<details>
<summary><strong>📌 How to Close This Issue (Required)</strong></summary>

1. Go to **Issues**  
2. Open this Issue  
3. Click **Close issue**  
4. Wait a few seconds  
5. The next Quest Issue will appear automatically

> ⚠️ Closing the PR is NOT enough.  
> You must close the issue itself to trigger the sequencer.
</details>

---

# 📝 Summary

### In this issue, you learned:

- How Django template inheritance works  
- How to create a shared layout (`base.html`)  
- How to use `{% extends %}` and `{% block %}`  
- How to clean up repeated HTML  
- How list and detail pages can share one consistent layout  

### You now have:

- A clean, professional template structure  
- A foundation for adding static files, CSS, and more  
- A more scalable app ready for the final challenge 🎉

Amazing job — your project now looks and feels like a real Django application! 🚀

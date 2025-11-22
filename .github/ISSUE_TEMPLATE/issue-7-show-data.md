---
name: "Issue 7 – Show Your Data on the Page"
about: "Query your model and render the data in a template"
title: "Issue 7 – Show Your Data on the Page"
labels:
  - issue-7
---

# 📄 Issue 7 – Show Your Data on the Page

So far you have:

- A Django project and app
- A model (`Item`) and migrations
- A superuser and working admin

In this Issue, you will:

- Create some items in the admin
- Query the database in a view
- Render the items in a template

---

## ✅ 1. Add Some Data in the Admin

1. Make sure your server is running:

   ```bash
   python manage.py runserver
   ```

2. Open the admin:

   ```
   http://127.0.0.1:8000/admin/
   ```

3. Log in with your superuser account.
4. Find your **Item** model in the admin.
5. Click **Add** and create 2–3 items with different names.

---

## ✅ 2. Create a View That Uses the Database

Open `<app_name>/views.py` and add a new view:

```python
from django.shortcuts import render
from .models import Item


def item_list(request):
    items = Item.objects.all()  # get all rows from the database
    return render(request, "<app_name>/item_list.html", {"items": items})
```

What this does:

- `Item.objects.all()` gets all the `Item` objects from the database.
- `render(...)` sends them to a template as `items`.

---

## ✅ 3. Add a URL for the New View

Open `<app_name>/urls.py` and add a new path:

```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.home, name="home"),
    path("items/", views.item_list, name="item_list"),
]
```

Now `/items/` will use the `item_list` view.

---

## ✅ 4. Create a Template to Display the Data

Create the folder structure:

```text
<app_name>/
  templates/
    <app_name>/
      item_list.html
```

> 💡 For example, if your app is called `main`, the template path will be:
> `main/templates/main/item_list.html`

Create `item_list.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Items</title>
  </head>
  <body>
    <h1>Items</h1>

    {% if items %}
      <ul>
        {% for item in items %}
          <li>{{ item.name }}</li>
        {% endfor %}
      </ul>
    {% else %}
      <p>No items found yet.</p>
    {% endif %}
  </body>
</html>
```

---

## ✅ 5. Test It

1. Make sure the server is running:

   ```bash
   python manage.py runserver
   ```

2. Open:

   ```
   http://127.0.0.1:8000/items/
   ```

You should see a list of item names from the database. 🎉

---

## 📝 Notes & Summary

- **View**: queries the database with `Item.objects.all()`
- **Template**: loops over `items` with `{% for item in items %}`
- **URL**: connects `/items/` to `item_list` view

You now have:

- Data stored in the database  
- Visible on a real page  
- Updated automatically when you add/change/delete items in the admin  

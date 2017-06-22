## HTML Tips
- Data attributes exist and are excellent for interacting with a database, or just between javascript/css/html.
- When making relative paths, think of what is likely to move.
  - Generally use just a forward slash off the root. If you are using "../", you need a good reason.
    - Example: **a href="/root-folder/foo.html"**
  - If you want to access a child folder, leave the slash off.
    - Example: **a href="child-folder/bar.html"**
- When linking to another page, Google prefers that you absolute URLs.

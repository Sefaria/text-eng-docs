# Change title of Index

Changing an Index title can simply be done by changing the `title` attribute on the object and saving. The change should cascade to all dependent objects (e.g. links, topic links, ref data, versions etc.)

## Example

```python
i = library.get_index("Ploni")
i.title = "Almoni"
i.save()
```

After this change, you'll need load the following URLs in order. Unfortunately, I don't think there's a simple way to make this work with Python since these URLs are touching the `library` object on the server thread.

sefaria.org/admin/reset/cache
sefaria.org/admin/reset/Almoni (obviously, change "Almoni" to the new title of the index)
sefaria.org/admin/reset/toc

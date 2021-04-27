# Change title of Index

Changing an Index title can simply be done by changing the `title` attribute on the object and saving. The change should cascade to all dependent objects (e.g. links, topic links, ref data, versions etc.)

## Example

```python
i = library.get_index("Ploni")
i.title = "Almoni"
i.save()
```

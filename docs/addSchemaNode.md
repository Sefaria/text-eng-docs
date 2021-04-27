# Add node to existing complex text

If you want to add a node to a simple text, first see [Convert Simple to Complex Text](../docs/convertToComplexText.md)

### Example: Add node before and after default Jagged Array node

```python
from sefaria.helper.schema import insert_first_child, insert_last_child

parent = library.get_index("Ploni").nodes
intro = JaggedArrayNode()
intro.add_primary_titles("Introduction", "הקדמה")
intro.add_structure(["Paragraph"])
insert_first_child(intro, parent)

outro = JaggedArrayNode()
outro.add_primary_titles("Conclusion", "Conclusion in Hebrew")
outro.add_structure(["Paragraph"])
insert_last_child(outro, parent)
```

e.g. 

https://trello.com/c/gCHOXynD

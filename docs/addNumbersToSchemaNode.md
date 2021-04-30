# Adding numbers to chapters of a complex text
e.g. https://trello.com/c/ObdWZZnC

Let's say a text has a ref "Ploni, Part 1, Chapter 1". Since the nodes in this ref are essentially numbered you may also want to refer to this same ref as "Ploni 1:1". JaggedArrayNodes can act essentially as SchemaNodes (see [here](https://github.com/Sefaria/Sefaria-Project/wiki/Index-Records-for-Simple-and-Complex-Texts#numbered-sections)) in this situation and allow both refs to resolve.

# Example: Allowing Derech Hashem to be referenced both by named and numbered nodes

```python
from sefaria.helper.schema import change_parent, insert_last_child, remove_branch, prepare_ja_for_children

i = library.get_index("Derech Hashem")
root = i.nodes
ja_parent = JaggedArrayNode()
ja_parent.key = "default"
ja_parent.default = True
ja_parent.add_structure(["Part", "Perek"])  # I'm fuzzy on how much depth this node needs. technically it's depth 3 since the "Perek" node holds a depth 1 JA. But this seemed to work. My assumption is JAs with children only need depth until the "real" JA depth.
insert_last_child(ja_parent, root)
prepare_ja_for_children(ja_parent)  # this line is important. when adding an empty JA to a parent, the content node in the version will be an empty array. This function ensures the content node is an empty dictionary so it can have named children.
for child in reversed(root.children[1:-1]):  # skip intro node and last node which is the new default node
    change_parent(child, ja_parent)
    child.__class__ = JaggedArrayNode  # cast SchemaNode to JaggedArrayNode
    child.nodeType = "JaggedArrayNode"
    child.depth = 1
    child.sectionNames = ["Perek"]  # see comment above about depth of JA
    child.addressTypes = ["Perek"]
i.save()
```

# Convert simple text to complex text:



A simple text is a text with only a Jagged Array node. You can verify a text is simple with the following snippet:

```python
i = library.get_index("Ploni")
i.is_complex()  # If False, index is simple
```

## Convert Jagged Array of simple text to default node of complex text:

The simplest way to convert a simple text to complex is to make the Jagged Array a default node. You can use the following snippet to do this:

```python
from sefaria.helper.schema import convert_simple_index_to_complex

i = library.get_index("Ploni")
convert_simple_index_to_complex(i)
```

## Other ways to convert simple to complex text???
I'm sure there are other ways of converting a simple to complex text besides adding a default node, but not sure what they are.

# Change text according to a pattern
E.g. fixing common typos, replacing one encoding of characters with another, changing punctuation.  In one version, or in many versions.

## Warning
**These methods run EXTREMLEY slowly on production environments**  
It is recommended that this issue be addressed ASAP

### sefaria.helper.text.modify_text_by_function(title:str, vtitle:str, lang:str, rewrite_function:Callable, uid:int, needs_rewrite_function:Callable=lambda x: True, **kwargs) -> None:
More fine-grained approach to modifying text.
Takes title and version and runs `rewrite_function` for every segment.
Parameters:
- title: Title of index
- vtitle: Version title
- lang: Language of version. Either 'he' or 'en'
- rewrite_function: Callable that takes two parameters: text and sections. Text is the current text of the segment. Sections is an array of zero-based section ints
- uid: User ID of user making the change
- needs_rewrite_function: Callable that takes a JaggedArray and returns True if JaggedArray should be modified
- **kwargs: see sefaria.tracker.modify_text (and lower functions) for kwargs

### Example: Replacing dash with space only when vayomer is in segment or is the first segment in the chapter (toy example)

```python
from sefaria.helper.text import modify_text_by_function
def modifier(text, sections):
    if sections[-1] == 0 or "ויאמר" in text:
        return text.replace('־', ' ')
    return text
for title in library.get_indexes_in_category('Tanakh'):
    modify_text_by_function(title, 'Tanach with Text Only', 'he', modifier, 5842, skip_links=True)
```

### sefaria.helper.text.find_and_replace_in_text(title:str, vtitle:str, lang:str, find_string:str, replace_string:str, uid:int) -> None:
Simplest way to find and replace strings in text.
- title: Title of index
- vtitle: Version title
- lang: Language of version. Either 'he' or 'en'
- find_string: String to find
- replace_string: String to replace it with
- uid: User ID of user making the change

### Example: Replacing dash with space in 'Tanach with Text Only' version of Tanakh

```python
from sefaria.helper.text import find_and_replace_in_text
for title in library.get_indexes_in_category('Tanakh'):
    find_and_replace_in_text(title, 'Tanach with Text Only', 'he', '\u05BE', ' ', 5842)  # \u05BE is Hebrew dash
```


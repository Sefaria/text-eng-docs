#Rename Category

There's a utility in Sefaria-Project for renaming categories.
```
from sefaria.helper.category import rename_category
```

```
def rename_category(cat, en, he=None):
    """
    :param cat: (model.Category or List) Either a Category object or a list of category keys defining a category
    :param en:  (String)    The new English name of the category.  If `en`` is a key for a Term, the Term will be used.  
    Otherwise, the `he` is required, and the two will be used to create a new Term.
    :param he:  (String, optional) 
    :return: model.Category - the newly renamed Category
    """
```
In order for the change to show up on the site, cache will need to be refreshed.  `admin/reset/cache` followed by `admin/reset/toc` should do the trick.

In code, this can be accomplished with `library.rebuild(include_toc=True)`

##Examples

```
rename_category(["Midrash", "Aggadic Midrash"], "Aggadah")
rename_category(["Midrash", "Halachic Midrash"], "Halakhah")
```

##Downstream impacts

* Search Filters
* URLs of TOC pages
* Mobile? 

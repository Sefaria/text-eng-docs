# Deploy Category

New categories can be created by script directly on the running production instance.

There's a utility in Sefaria-Project for creating categories.
```
from sefaria.helper.category import create_category
```

```
def create_category(path, en=None, he=None, searchRoot=None):
    """
    Will create a new category at the location in the TOC indicated by `path`. 
    If there is a term for `path[-1]`, then that term will be used for this category. 
    Otherwise, a new Term will be created with titles `en` and `he`. 
    
    :param path: (List) the full path of the category to create
    :param en: (String, optional)
    :param he: (String, optional)
    :param searchRoot: (String, optional) If this is present, then in the context of search filters, this category will appear under `searchRoot`. 
    :return: (model.Category) the new category object
    """
```

In order for the change to show up on the site, cache will need to be refreshed.  `admin/reset/cache` followed by `admin/reset/toc` should do the trick.

In code, this can be accomplished with `library.rebuild(include_toc=True)`


## Examples

```
from sefaria.helper.category import move_index_into, create_category

sor = create_category(["Midrash", "Aggadah", "Seder Olam Rabbah"], "Seder Olam Rabbah", "סדר עולם רבה")
move_index_into("Seder Olam Rabbah", sor)

sor_com = create_category(["Midrash", "Aggadah", "Seder Olam Rabbah", "Commentary"])
for comm in ["Vilna_Gaon_on_Seder_Olam_Rabbah",
             "Meir Ayin on Seder Olam Rabbah",
             "Yaakov Emden on Seder Olam Rabbah"]:
    move_index_into(comm, sor_com)

```

# Move Index into new Category

There's a utility in Sefaria-Project for moving an Index into a new category.
```
from sefaria.helper.category import move_index_into
```

```
def move_index_into(index, cat):
    """    
    :param index: (String)  The primary name of the Index to move. 
    :param cat:  (model.Category or List) Category to move into - either a Category object, or a List with the path leading to the Category
    :return: None
    """
```

In order for the change to show up on the site, cache will need to be refreshed.  `admin/reset/cache` followed by `admin/reset/toc` should do the trick.

In code, this can be accomplished with `library.rebuild(include_toc=True)`


## Examples:
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
#Move Category to new Parent

#Rename Category

There's a utility in Sefaria-Project for renaming categories.
```
from sefaria.helper.category import move_category_into
```

```
def move_category_into(cat, parent):
    """
    Move category `cat` to be a child of `parent`.  If `parent` is None, move `cat` to root.

    :param cat: (model.Category or List) either a Category object, or a list of keys for the path of a category
    :param parent: (model.Category or List) either a Category object, or a list of keys for the path of a category
    :return:    
    """
```
In order for the change to show up on the site, cache will need to be refreshed.  `admin/reset/cache` followed by `admin/reset/toc` should do the trick.

In code, this can be accomplished with `library.rebuild(include_toc=True)`


##Examples
Move the category that was `Tanaitic/Minor Tractates` to be `Talmud/Bavli/Minor Tractates`
```
c = Category().load({'path': ["Tanaitic", "Minor Tractates"]})
p = Category().load({"path": ["Talmud", "Bavli"]})
move_category_into(c, p)
``` 

##Downstream impacts

* Search Filters
* URLs of TOC pages
* Mobile? 

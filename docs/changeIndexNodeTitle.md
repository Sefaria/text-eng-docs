# Change title of index node

**_Major bugs have been found in the helper methods here. Do not attempt such a change at this time_**

### Changing Standard Titles

A convenience function exists. The function `change_node_title` can be found at  
`Sefaria-Project/sefaria/helper/schema.py`  
`change_node_title` accepts four arguments:
* `snode`: The node that is recieving a title change
* `old_title`: The title being replaced
* `lang`: Language. Must be either `'en'` of `'he'`
* `new_title`: Replacement title

**Note on changing English Primary Titles**  
Changing an English primary title requires a *cascade* operation to be performed on the database. This is an expensive and possibly long running operation and should be made with caution. It is recommended not to change primary English titles during peak traffic.


### Changing Shared Titles
**_TODO_**

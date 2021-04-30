# Adding Collective Title to Index

You can add a collective title to an index simply by creating a term with the scheme "commentary_works" and editing the field `collective_title` on the appropriate indexes.

# Adding Collective Titles to Chomat Anakh indexes

```python
Term({
    "scheme" : "commentary_works", 
    "titles" : [
        {
            "lang" : "en", 
            "text" : "Chomat Anakh", 
            "primary" : true
        }, 
        {
            "lang" : "he", 
            "text" : "חומת אנך", 
            "primary" : true
        }
    ], 
    "name" : "Chomat Anakh"
}).save()

iss = library.get_indexes_in_category("Chomat Anakh", include_dependant=True, full_records=True)
for i in iss:
    i.collective_title = "Chomat Anakh"
    i.save()

# Class 20

Live link: [Django Models](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2020/)

## Model primer

This section provides a brief overview of how a model is defined and some of the more important fields and field
arguments.

### Model definition

Models are usually defined in an application's models.py file. They are implemented as subclasses of
django.db.models.Model, and can include fields, methods and metadata. The code fragment below shows a "typical" model,
named MyModelName:

### Metadata

You can declare model-level metadata for your Model by declaring class Meta, as shown.
You do this by specifying the match order in a list of field names to the ordering attribute, as shown above. The
ordering will depend on the type of field (character fields are sorted alphabetically, while date fields are sorted in
chronological order). As shown above, you can prefix the field name with a minus symbol (-) to reverse the sorting
order.

### Methods

- __str__()
  - to return a human-readable string for each object
- get_absolute_url()
  - which returns a URL for displaying individual model records on the website

---

[Source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Models#model_management)
---

## Notes

- Assuming you will use URLs like /myapplication/mymodelname/2 to display individual records for your model (where "2"
  is the id for a particular record), you will need to create a URL mapper to pass the response and id to a "model
  detail view" (which will do the work required to display the record). The reverse() function above is able to "
  reverse" your URL mapper (in the above case named 'model-detail-view') in order to create a URL of the right format.

## Django admin site

### What is?

The Django admin application can use your models to automatically build a site area that you can use to create, view,
update, and delete records. This can save you a lot of time during development, making it very easy to test your models
and get a feel for whether you have the right data. The admin application can also be useful for managing data in
production, depending on the type of website. The Django project recommends it only for internal data management (i.e.
just for use by admins, or people internal to your organization), as the model-centric approach is not necessarily the
best possible interface for all users, and exposes a lot of unnecessary detail about the models.

### things can be done

- Registering models
- Creating a superuser
- Logging in and using the site

---

[for more information](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site)
---

## Things I want to know more about

deal with these topics in practice

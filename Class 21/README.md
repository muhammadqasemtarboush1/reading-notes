# Class 21

Live link: [Django CRUD](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2021/)

## Forms

An HTML Form is a group of one or more fields/widgets on a web page,
which can be used to collect information from users for submission to a server.
Forms are a flexible mechanism for collecting user input because there are suitable
widgets for entering many different types of data, including text boxes, checkboxes, radio buttons,
date pickers and so on. Forms are also a relatively secure way of sharing data with the server, as they allow us
to send data in POST requests with cross-site request forgery protection.

### Django form handling process

Django's form handling uses all of the same techniques that we learned about in previous tutorials (for displaying
information about our models): the view gets a request, performs any actions required including reading data from
the models, then generates and returns an HTML page (from a template, into which we pass a context containing the
data to be displayed). What makes things more complicated is that the server also needs to be able to process data
provided by the user, and redisplay the page if there are any errors.
A process flowchart of how Django handles form requests is shown below, starting with a request for a page containing a form (shown in green).
![procces](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png)

Based on the diagram above, the main things that Django's form handling does are:

- Display the default form the first time it is requested by the user.
  - The form may contain blank fields if you're creating a new record, or it may be pre-populated with initial
  values (for example, if you are changing a record, or have useful default initial values).
  - The form is referred to as unbound at this point, because it isn't associated with any user-entered data
  (though it may have initial values).
- Receive data from a submit request and bind it to the form.
  - Binding data to the form means that the user-entered data and any errors are available when we need to
  redisplay the form.
- Clean and validate the data.
  - Cleaning the data performs sanitization of the input fields, such as removing invalid characters that might
  be used to send malicious content to the server, and converts them into consistent Python types.
  - Validation checks that the values are appropriate for the field (for example, that they are in the right date
  range, aren't too short or too long, etc.)
  - If any data is invalid, re-display the form, this time with any user populated values and error messages for
  the problem fields.
- If all data is valid, perform required actions (such as save the data, send an email, return the result of a
search, upload a file, and so on).
- Once all actions are complete, redirect the user to another page.
Django provides a number of tools and approaches to help you with the tasks detailed above. The most fundamental
is the Form class, which simplifies both generation of form HTML and data cleaning/validation. In the next
section, we describe how forms work using the practical example of a page to allow librarians to renew books.

## Form

The Form class is the heart of Django's form handling system. It specifies the fields in the form, their layout
display widgets, labels, initial values, valid values, and (once validated) the error messages associated with
invalid fields. The class also provides methods for rendering itself in templates using predefined formats (tables,
lists, etc.) or for getting the value of any element (enabling fine-grained manual rendering).
---

### [Source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)

### [Source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Home_page)

### [Source](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Generic_views)

---

## Notes

 The generic class-based detail view expects to be passed a parameter named pk. If you're writing your own
 function view you can use whatever parameter name you like, or indeed pass the information in an unnamed argument.

## Things I want to know more about

How to apply this knowledge in real project

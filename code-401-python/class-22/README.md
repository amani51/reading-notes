# Class-23
## Django CRUD and Forms
#### Django Forms
- An **HTML Form** is a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server. Forms are a flexible mechanism for collecting user input because there are suitable widgets for entering many different types of data, including text boxes, checkboxes, radio buttons, date pickers and so on. Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.
![](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/admin_book_add.png)
- The form is defined in HTML as a collection of elements inside ```<form>…</form>``` tags, containing at least one input element of type="submit".
```HTML
<form action="/team_name_url/" method="post">
  <label for="team_name">Enter name: </label>
  <input
    id="team_name"
    type="text"
    name="name_field"
    value="Default name for team." />
  <input type="submit" value="OK" />
</form>
```
- The field's ```type``` attribute defines what sort of widget will be displayed. 
- The ```name``` and ```id``` of the field are used to identify the field in JavaScript/CSS/HTML
- The ```value``` defines the initial value for the field when it is first displayed.
- The ```submit``` input will be displayed as a button by default.
- he form attributes define the HTTP method used to send the data and the destination of the data on the server (*action*):
    - ```action```: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
    - ```method```: The HTTP method used to send the data: post or get.
        - The ```POST``` method should always be used if the data is going to result in a change to the server's database, because **it can be made more resistant to cross-site forgery request attacks**.
        - The ```GET``` method should only be used for forms that don't change user data (for example, a search form). It is recommended for when you want to be able to bookmark or share the URL.

### Django form handling process
![](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms/form_handling_-_standard.png)
- Based on the diagram above, the main things that Django's form handling does are:

    1. Display the default form the first time it is requested by the user.
        - The form may contain blank fields if you're creating a new record, or it may be pre-populated with initial values.
        - The form is referred to as unbound at this point, because it isn't associated with any user-entered data.
    2. Receive data from a submit request and bind it to the form.
        - Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
    3. Clean and validate the data.
        - Cleaning the data performs sanitization of the input fields, such as removing invalid characters that might be used to send malicious content to the server, and converts them into consistent Python types.
    - Validation checks that the values are appropriate for the field.
    4. If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
    5. If all data is valid, perform required actions (such as save the data, send an email, return the result of a search, upload a file, and so on).
    6. Once all actions are complete, redirect the user to another page.
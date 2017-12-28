Paulo wrote the following code to get the bootstrap tab to switch on button click:

```javascript
<script type="text/javascript">
    $('#changeToResidentMedicalTab').click(function(e) {
      e.preventDefault();
      $('#resident-tab li:eq(1) a').tab('show');
    });
</script>

```

It reads, 

- [ ] Get the id of the button which will be clicked
- [ ] Event prevent default ??
- [ ] the resident-tab id is the ul id of all tabs
- [ ] the list links are zero indexed so we are looking to show tab #2 on button click.


For 1 email field per email:

```javascript
    var form="<input type=\"text\" name=\"email[]\"> <a id="remove_email">remove</a>"
    
    <a href="#" id="add_email">Add email</a>
    <div id="emails">
    
    </div>
    
    $("#add_email").html(form);
    
    params[:email] ["p@watever.com", "other@whatever.com"]
```

- [ ] create a variable containing the field to render upon button click
- [ ] create html container where the field will be rendered
- [ ] give the button to click an id
- [ ] find the correct method (html isn't it, just used as example)



gmail_contacts_import_javascript
================================

Import gmail contacts via javascript to the html page

Usage
-----

1. Insert the contents of the ``google_contacts.html`` to your html file before the ``</body>`` tag or where you want...
2. You have two options:

    2.1 For user communicated contacts getting provide a link or button with ``js-google-contacts`` class. Clicking on it will start gmail contacts getting:
    
    
    ```  
        <a href="#" class="js-google-contacts">Get Gmail contacts</a>
    ```
    
    2.2 To get contacts on page load you need to uncomment the call of **checkAuth()** in **handleClientLoad()** :
    
    ```
        function handleClientLoad() {
            gapi.client.setApiKey(apiKey);
            checkAuth();
        }
    ```
    
3. When gmail contacts are imported, the ``contacts_received`` event is fired by ``authorize-button``, catch it in your code:

    ```
        $(function(){
                $('#authorize-button').on('contacts_received', function(e, contacts){
                    contact=contacts[0] // array of contacts {name,email}
                    alert(contact.name + ' ' + contact.email) //Do here whatever you want
                });
            });
    ```
    

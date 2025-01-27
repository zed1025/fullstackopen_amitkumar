sequenceDiagram
    participant browser
    participant server

    Note right of browser: The notes page(SPA version) has been loaded. I will now try adding a new note through the form

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa payload for new note is sent in header (payload section)
    activate server
    server-->>browser: 201 Response with the response {"message":"note created"}
    deactivate server

    Note right of browser: the browser, updates the notes array to add the new note creatd, 
    Note right of browser: it then calls the redrawNotes() function to update the page and then calls sendToServer() to send notes to the server
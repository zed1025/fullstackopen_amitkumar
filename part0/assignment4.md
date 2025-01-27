sequenceDiagram
    participant browser
    participant server

    Note right of browser: The connection between browser and server has been established. The page displays the list of all notes. I enter some test in the form field and press Save.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: REDIRECT, perform HTTP GET on /exampleapp/notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML File
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [ { "content": "cc cv", "date": "2025-01-27T04:12:15.842Z" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
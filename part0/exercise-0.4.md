```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes "hey" in the form and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (content=hey)
    activate server
    Note right of server: Server saves the new note with timestamp
    server-->>browser: 302 Redirect to /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: Browser executes JS and fetches the updated notes list

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON includes {"content":"hey","date":"2026-02-25T12:18:23.499Z"} among others
    deactivate server

    Note right of browser: Browser renders the updated list of notes (including "hey")
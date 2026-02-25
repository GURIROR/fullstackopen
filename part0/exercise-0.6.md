```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes "heya" and clicks Save (SPA)

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: Payload: {"content":"heya","date":"2026-02-25T18:33:56.237Z"}
    activate server
    Note right of server: Server saves the new note
    server-->>browser: 201 Created (application/json)
    deactivate server

    Note right of browser: Browser updates the notes list in the DOM (no page reload)
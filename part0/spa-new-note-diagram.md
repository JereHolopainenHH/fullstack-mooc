    sequenceDiagram
        participant Browser
        participant Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
        activate Server
        Server->>Browser: HTML-document
        deactivate Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
        activate Server
        Server->>Browser: The CSS file
        deactivate Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
        activate Server
        Server->>Browser: The JavaScript file
        deactivate Server

        Note right of Browser: The Browser starts executing the JavaScript code that fetches The notes

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate Server
        Server->>Browser: [{"content": "Focaccia","date": "2024-12-12T00:45:56.400Z"}, ...]
        deactivate Server

        Note right of Browser: The Browser executes the callback function that renders the notes

        Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa {content: "test", date: "2024-12-12T12:03:56.486Z"}
        Note right of Browser: The Browser sends POST request with a JSON payload {content: "test", date: "2024-12-12T12:03:56.486Z"}
        activate Server
        Server->>Browser: {"message": "note created"}
        Note left of Server: The Server sends a status 201 Created with JSON response {"message": "note created"}
        deactivate Server

        Note right of Browser: The Browser executes the callback function that rerenders the notes without reloading the page
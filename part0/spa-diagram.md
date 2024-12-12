    sequenceDiagram
        participant Browser
        participant Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
        activate Server
        Server->>Browser: HTML-document
        deactivate Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
        activate Server
        Server->>Browser: the CSS file
        deactivate Server

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
        activate Server
        Server->>Browser: the JavaScript file
        deactivate Server

        Note right of Browser: the Browser starts executing the JavaScript code that fetches the notes

        Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate Server
        Server->>Browser: [{"content": "Focaccia","date": "2024-12-12T00:45:56.400Z"}, ...]
        deactivate Server

        Note right of Browser: the Browser executes the callback function that renders the notes
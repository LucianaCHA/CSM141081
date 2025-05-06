sequenceDiagram
  participant browser as browser

  participant view as view

  participant server as server

  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/notes
  server -->>- browser: HTML document
    Note over view: List of notes *Note 1*
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  server -->>- browser: the css file
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  server -->>- browser: the JavaScript file
  Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
  server -->>- browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
  Note right of browser: The browser executes the callback function that renders the notes
  Note over view: The user types text *Note 2* in input
  Note over view: Users clicks on 'Save' button

  browser ->>+ server: POST https://studies.cs.helsinki.fi//exampleapp/
  Note left of server:  note *Note 2*

  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/notes
  server -->>- browser: HTML document
  Note over view: List of notes *Note 1*
  Note over view: List of notes *Note 2*
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
  server -->>- browser: the css file
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
  server -->>- browser: the JavaScript file
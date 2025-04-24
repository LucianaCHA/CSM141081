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
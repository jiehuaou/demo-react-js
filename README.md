# This is a DEMO for Learning React.js

## what is CORS

CORS stands for cross-origin resource sharing.

## how to enable CORS, solution-1 : Server Side

CORS Should Always Be Handled From Server Side!

Here is NodeJs example:
```javascript
    const express = require('express');
    const app = express();
    app.get('/', (req, res) => {
        res.send('Welcome to CORS server 😁')
    })
    app.get('/cors', (req, res) => {

        // show it can be access by any domain.
        res.set('Access-Control-Allow-Origin', '*');
        
        res.send('This has CORS enabled 🎈')
    })
    app.listen(8080, () => {
        console.log('listening on port 8080')
    })
```

## how to enable CORS, solution-2 : use Proxy

Suppose our Web client site is http://host-a:3000/

And our Java Service Site is    http://host-b:8080/api

We can enable proxy at React-js package.json
```json
{
    "dependencies": {
        "react": "^18.2.0",
        "react-dom": "^18.2.0"
    },
    
    "proxy": {
        // route any /search request to google 
        "/search" : {
            "target" : "https://www.google.com",
            "changeOrigin" : true
        },
        // route any /api request to this url 
        "/api" : {
            "target" : "https://host-b:8080",
            "changeOrigin" : true
        }
    }
    
}
```

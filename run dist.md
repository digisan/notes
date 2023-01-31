
'/dist' is from `npm run build`

## node

server.js as below

run `node server.js`

```javascript
// optional: allow environment to specify port
const port = process.env.PORT || 3000

// wire up the module
const express = require('express')

// create server instance
const app = express()

// bind the request to an absolute path or relative to the CWD
app.use(express.static('dist'))

// start the server
app.listen(port, () => console.log(`Listening on port ${port}`))
```

## deno

server.ts as below

run `deno run -A server.ts`

### by opine

```typescript
import { opine, serveStatic } from "https://deno.land/x/opine@2.3.3/mod.ts";

// optional: allow environment to specify port
const port = Deno.env.get('PORT') || 3000

// create server instance
const app = opine();

// bind the request to an absolute path or relative to the CWD
app.use(serveStatic('dist'))

// start the server
app.listen(port, () => console.log(`Listening on port ${port}`));
```

### by express

```typescript
import express from "npm:express"

// optional: allow environment to specify port
const port = Deno.env.get("PORT") || 8080;

// create server instance
const app = express();

// bind the request to an absolute path or relative to the CWD
app.use(express.static("dist"));

// start the server
app.listen(port, () => console.log(`Listening on port ${port}`));
```

## Nginx 

For **ubuntu**, have to define in `/etc/hosts` server name for local ip: e.g. `127.0.0.1 mydomain www.mydomain.com mydomain.com`. If want to use domain to access site.

And in `/etc/nginx/nginx.conf`, `user ***` => `user root`.



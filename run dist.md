
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

## On Client Access Via Domain: 

For **ubuntu** Client, define in `/etc/hosts` server name for local ip: e.g. `127.0.0.1 mydomain www.mydomain.com mydomain.com`. If want to use domain to access site.

For **windows** Client, define in `C:\Windows\System32\drivers\etc\hosts` server name for ip. e.g. `192.168.31.149 data-dictionary.test`. If want to use domain to access site

## Nginx Server Side:

Also, in `/etc/nginx/nginx.conf`, `user ***` => `user root`.

Under `/etc/nginx/sites-available`, create a file named `your-project`, refer to below config text with `sudo vim`. Then

> sudo ln -s /etc/nginx/sites-available/your-project /etc/nginx/sites-enabled/

> sudo nginx -t

> sudo systemctl restart nginx.service

```
server {
        listen  8080;
        server_name sub1.domain.net;
        charset  utf-8;
        location / {
                root /path/to/the/first/dist;
                index index.html;
                try_files $uri $uri/ /index.html;
        }
        error_log /path/to/the/error1.log;
        access_log /path/to/the/access1.log;
}

server {
        listen  8081;
        server_name sub2.domain.net;
        charset  utf-8;
        location / {
                root /path/to/the/second/dist;
                index index.html;
                try_files $uri $uri/ /index.html;
        }
        error_log /path/to/the/error2.log;
        access_log /path/to/the/access2.log;
}
```

```
server {
        server_name sub1.mywebsite.com;
        location / {
                proxy_pass http://localhost:xxxx;
        }
}

server {
        server_name sub2.mywebsite.com;
        location / {
                proxy_pass http://localhost:xxxx;
        }
}
```


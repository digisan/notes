
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
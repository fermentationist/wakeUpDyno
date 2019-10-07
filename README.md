# wakeUpDyno

**wakeUpDyno** is a tiny utility to prevent your Heroku dyno (server) from sleeping when not in use. 

According to [**herokuapp.com**, `If an app has a free web dyno, and that dyno receives no web traffic in a 30-minute period, it will sleep.`](https://devcenter.heroku.com/articles/free-dyno-hours) When a user loads a sleeping heroku app, it may take an uncomfortably long time (up to ten seconds!) for the dyno to spin up and serve the page. This is long enough for many users to assume the site is broken and move on. 

**wakeUpDyno** will perform a simple HTTP request to whatever url you provide, at regular intervals. If you use the url of your free dyno, that single GET request will be sufficient to prevent it from going dormant, so that visitors will not be made to endure unreasonably long loading times.

---

## Use
Import the default export from **wakeUpDyno** (a function) and invoke it after starting up your server. Pass in the url of your dyno as an argument:

```node
/* Example: as used with an Express app */

const express = require("express")
const wakeDyno = require("../wakeUpDyno");

// create an Express app
const app = express();

// start the server, then call wokeDyno(url).start()
app.listen(PORT, () => {
    wakeDyno(DYNO_URL); // DYNO_URL should be the url of your Heroku app
});

```

---
## Credits

**wakeUpDyno** was made by [Dennis Hodges](https://github.com/fermentationist), a Javascript developer.

---
## License

#### Copyright © 2019 Dennis Hodges


__The MIT License__

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

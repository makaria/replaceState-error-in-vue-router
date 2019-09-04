# Quasar App (vue-router-bug)

A Quasar Framework app

## Install the dependencies
```bash
yarn
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
quasar dev
```

### Build the app for production
```bash
quasar build:cdn
```

### Check the bug
Open `localhost:4000` or `your local ip:4000`, you will get an error like:
```
Uncaught DOMException: Failed to execute 'replaceState' on 'History': A history state object with URL 'http://127.0.0.1:4000/' cannot be created in a document with origin 'http://localhost:4000' and URL 'http://localhost:4000/'.
```
Open `127.0.0.1:4000`, there is no error.

 In my case, every file except `index.html` is hosted on `127.0.0.1`, `index.html` is hosted on another domain like `192.168.0.1`, with `<base href="127.0.0.1">`, i can use `static` files like normal except the `replaceState` error. when `<base>` tag is empty,i can not use any `static` file because it's link will be `192.168.0.1/static/`, and the file is actually in `127.0.0.1/static`.

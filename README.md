# Quasar App (vue-router-bug)

A Demo App Reproduce `replaceState` Bug

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
yarn build:cdn
```

### Serve the dist files
```bash
quasar server --history ./dist/spa
```

### Check the bug
Open `localhost:4000`, `your local ip:4000` and `127.0.0.1:4000`, there is no `replaceState` error

### Another bug when developing
However, it will cause a bug when developing.
Run `quasar dev`, open `localhost:8080/list/item`, there will be an error like `GET http://localhost:8080/list/app.js net::ERR_ABORTED 404 (Not Found)`, the solution is modify the file `quasar-config.js` in `node-modules/@quasar/app/lib` `line 483`
```
cfg.build.appBase = cfg.build.vueRouterMode === 'history'
      ? cfg.build.publicPath
      : ''
```
to
```
cfg.build.appBase = cfg.build.vueRouterMode === 'history'
      ? cfg.build.publicPath
      : '/'
```

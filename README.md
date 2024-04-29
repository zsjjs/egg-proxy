# egg-proxy-plugin

Configure proxy middleware for egg. Use [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware).

## Install

```bash
$ npm i egg-proxy-plugin --save
```

## Usage

```js
// {app_root}/config/plugin.js
exports.httpProxy = {
  enable: true,
  package: 'egg-proxy-plugin',
};
```

## Configuration

Proxy `/api` requests to `http://www.example.org`:

```js
// {app_root}/config/config.default.js
exports.httpProxy = {
  '/api': 'http://www.example.org'
};
```

A request to `/api/users` will now proxy the request to `http://www.example.org/api/users`.

If you don't want `/api` to be passed along, we need to rewrite the path:

```js
// {app_root}/config/config.default.js
exports.httpProxy = {
  '/api': {
    target: 'http://www.example.org',
    pathRewrite: {'^/api' : ''}
  }
};
```

For more advanced usages, checkout [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#options) options documentation.

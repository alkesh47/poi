# Create Plugin

You can create a plugin that is reponsible for handling a command or extending webpack config.

A plugin is basically a function with following signature:

```js
function myPlugin(poi) {
  // do something..
}
```

It's common to use a higher-order function if your plugin accepts options:

```js
function myPlugin(options) {
  return poi => {
    // do something..
  }
}
```

Then you can call it like this in `poi.config.js`:

```js
module.exports = {
  plugins: [
    require('./my-plugin')(options)
  ]
}
```

## Handling Command

*To be written..*

## Chain Webpack Config

Use [webpack-chain](https://github.com/mozilla-neutrino/webpack-chain) to modify webpack config.

```js
poi.chainWebpack(config => {
  // chain webpack config..
  // e.g. add a webpack plugin
  config.plugin('some-plugin')
    .use(SomeWebpackPlugin, [pluginOptions])
})
```

The `config` here is a [webpack-chain](https://github.com/mozilla-neutrino/webpack-chain) instance.

## Configure Webpack Config

Directly mutate or merge webpack config:

```js
poi.configureWebpack(config => {
  config.devtool = false
  // Optionally return the config
  // return config
})

// Or use webpack-merge
poi.configureWebpack({
  devtool: false
})
```

## Configure Dev Server

```js
poi.configureDevServer(app => {
  // app is an express instance
})
```

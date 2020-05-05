# Differences in this fork

1. upgraded dependencies
2. "ejs", "html-minifier","uglify-js","loader-utils" have been moved to dependencies from devDependencies

# webpack-ejs3-loader for webpack

[webpack](http://webpack.github.io/) loader use to compile [ejs](https://github.com/mde/ejs) templates.

## Installation

`npm install -D webpack-ejs3-loader`

## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

```javascript
var template = require("webpack-ejs3-loader!./file.ejs");
// => returns the template function compiled with ejs templating engine.

// And then use it somewhere in your code
template(data) // Pass object with data

// Child Templates
// path is relative to where webpack is being run
<%- include templates/child -%>
```

## Options

besides [ejs compile options](https://github.com/mde/ejs#options), you can add these addtion options:

`beautify` — enable or disable uglify-js beautify of template ast

`compileDebug` — see ejs compileDebug option

`htmlmin` — see [htmlminify section](#htmlminify)

`htmlminOptions` - See [all htmlminify options reference](https://github.com/kangax/html-minifier#options-quick-reference)

## webpack config example

```javascript
...
plugins:[
      new HtmlwebpackPlugin({
      title: 'Page Title',
      template: 'webpack-ejs3-loader!' + resolve(__dirname, 'templates/index.ejs'),
    }),
],
module: {
  rules: [
    {
      test: /\.ejs$/,
      loader: "webpack-ejs3-loader",
      options: {
        htmlmin: true,
        htmlminOptions: {
          removeComments: true,
        },
      },
    },
  ]
}
...
```

### Originally authored by:

https://github.com/defims/compile-ejs-loader

## License

MIT (http://www.opensource.org/licenses/mit-license.php)

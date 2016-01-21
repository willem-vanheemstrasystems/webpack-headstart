# webpack-headstart
Webpack - Headstart

Based on https://webpack.github.io/docs/tutorials/getting-started/

Run the project like so:

$ webpack ./entry.js bundle.js

Open index.html in your browser. It should display "It works from content.js".

## About Webpack:

Webpack will analyze your entry file for dependencies to other files. These files (called modules) are included in your bundle.js too. webpack will give each module a unique id and save all modules accessible by id in the bundle.js file. Only the entry module is executed on startup. A small runtime provides the require function and executes the dependencies when required.

Webpack can only handle JavaScript natively, so we need the css-loader to process CSS files. We also need the style-loader to apply the styles in the CSS file.

### Loaders

By prefixing loaders to a module request, the module goes through a loader pipeline. These loaders transform the file content in specific ways. After these transformations are applied, the result is a JavaScript module.

Binding Loaders

We don’t want to write such long requires require("!style!css!./style.css");.
We can bind file extensions to loaders so we just need to write: require("./style.css")

Run the compilation with:

webpack ./entry.js bundle.js --module-bind "css=style!css"

### Config

With the addition of below to the webpack.config.js:

module.exports = {
    entry: "./entry.js",
    output: {
        path: __dirname,
        filename: "bundle.js"
    },
    module: {
        loaders: [
            { test: /\.css$/, loader: "style!css" }
        ]
    }
};

We can now run the compilation simply with:

webpack

The webpack command-line will try to load the file webpack.config.js in the current directory.

A PRETTIER OUTPUT

If the project grows the compilation may take a bit longer. So we want to display some kind of progress bar. And we want colors…

We can achieve this with

webpack --progress --colors

WATCH MODE

We don’t want to manually recompile after every change…

webpack --progress --colors --watch

Webpack can cache unchanged modules and output files between compilations.

When using watch mode, webpack installs file watchers to all files, which were used in the compilation process. If any change is detected, it’ll run the compilation again. When caching is enabled, webpack keeps each module in memory and will reuse it if it isn’t changed.


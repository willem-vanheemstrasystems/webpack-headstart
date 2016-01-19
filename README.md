# webpack-headstart
Webpack - Headstart

Based on https://webpack.github.io/docs/tutorials/getting-started/

Run the project like so:

$ webpack ./entry.js bundle.js

Open index.html in your browser. It should display "It works from content.js".

About Webpack:

Webpack will analyze your entry file for dependencies to other files. These files (called modules) are included in your bundle.js too. webpack will give each module a unique id and save all modules accessible by id in the bundle.js file. Only the entry module is executed on startup. A small runtime provides the require function and executes the dependencies when required.

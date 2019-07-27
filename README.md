# competency-framework

## Building

`grunt build:dev` will produce a development build, where the JS and CSS contain source maps to aid debugging.

`grunt build:prod` will produce a production build.

`grunt watch` will run `build:dev` whenever it notices any changes to any content or source files. Alternatively you can run `grunt build:dev` manually.

## Hosting

This project is designed to be hosted in production on Amazon S3. Below is the bucket configuration you need.

TODO

In develpoment, point a webserver at the `./build` folder.

All extensionless paths must be rewritten to `/`

## Content

All the content lives under `./content`. 

Competencies live under `./content/competencies` and Roles live under `./content/roles`

TODO: These JSON document require a schema

## Styling/CSS 

The CSS is produced by SASS compilation from sources described below.

The source for styles live under `./src/scss`.

`styles.scss` is the entry point, notice the `@imports` at the top.

If you want to add more/separate `.scss` files you need to import them from (probably) `stlyes.scss`

## Javascript

The JS is produced by Uglify-es compilation of the sources described below.

The source for Javascript lives under `./src/js`

All files in this path will be combined together, in file-system order (i.e. the order `ls` shows)

## Assets (images etc)

All assets live under './src/assets'

On build, everything in this folder gets copied to the `./build` output folder.

A `dev` build also copies a `web.config` which enables easy serving of the project under Windows IIS`

## HTML

The HTML is produced by combining the Roles and Cmpetencies JSON with Handlebars.js templates.

### Handlebars.js Helpers

Where in Handlebars.js you create a helper like this:

```
Handlebars.registerHelper('log', function(data) {
  console.log(data);
});
```

In this project, simply make a file called `log.js` under the `./src/helpers` folder, and return the function using `module.exports`

```
module.exports = function(data) {
  console.log(data);
}
```

All the helper files under `./src/helpers` will be automatically detected and registered as helpers.

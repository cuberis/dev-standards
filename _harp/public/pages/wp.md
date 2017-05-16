Cuberis often uses WordPress to create client sites and develops custom functionality through plugin and them integrations as needed.

### Theme Development

Cuberis uses a modified version the Roots.io/sage theme (based on version 8.5). This provides significant development advatages including Gulp powered preprocessing, linting, minification, and concatenation. Additionally, the theme uses Browsersync to smooth testing and allows the ability to navigate pages in multiple browsers.

For documentation specifically related to theme features please refer to the documenation at https://roots.io/sage/docs/.

For more information, see the [Base Theme Repo](https://github.com/cuberis/cuberis-base) or checkout the [Wiki Docs](https://github.com/cuberis/cuberis-base/wiki).

### DRY Methodology
At Cuberis, we make a great effor to conform to the **DRY** principle which simply means **D**on't **R**epeat **Y** ourself. This means if there is ever a case when, you are copying and pasting the same code between multiple templates, you are not being DRY! By adhering to the DRY principle, we ensure that our code is clean, more readable and most importantly, easier to update and maintain.

### Getting Started with the Base Theme

See more information in the [Base Theme Readme](https://github.com/cuberis/cuberis-base/blob/master/README.md).

#### Dependencies
1. Install [gulp](http://gulpjs.com/) and [Bower](http://bower.io/) from the command line globally with `npm install -g gulp bower`.
2. Navigate to the theme directory, then from the command line, run `npm install` (may need to be run with `sudo`).
3. Run `bower install`.

#### Compiling Assets
The base theme is setup to look for all CSS and JS in the `/dist` folder located in the theme. Run the following commands from the command line to auto-compile your assets to that location:

1. `gulp` - compiles all JS and CSS to the `/dist` folder in the theme
2. `gulp js` or `gulp styles` - compiles only the requested Assets
3. `gulp watch` - starts a BrowserSync server at [http://localhost:3000](http://localhost:3000)
4. `gulp --production` - prepares assets for production and compiles to the `/dist` folder

#### BrowserSync
Make sure you update your local URL that you want BroserSync to serve the site from. Update this in `/assets/manifest.json` and change the `devUrl`.

### Theme Templates

Before getting started with templates in the Base Theme, you will want to read up on the [Sage Documentation](https://roots.io/sage/docs/theme-templates/). The base theme does not follow the typical WordPress theme structure. However, it does still use the [WordPress Template Hierarchy](http://codex.wordpress.org/Template_Hierarchy). For more information on how to add/customize template files, see [Sage: Theme Templates](https://roots.io/sage/docs/theme-templates/).

### The Functions File

As a general practice Cuberis embraces the file structure concepts of Sage. Assets and Function are placed in folders and referenced accordingly.

The <code>functions.php</code> file is only used to reference appropriate files in the lib folder.

This allows for subfolders to include advanced functionality including external libraries with out crowding the theme's root directory. An example might be a custom, theme specific external integration to APIs like Zendesk or Stripe.

### File structure

Every WordPress project built on the Base Theme should always follow the following folder structure:

```
|-- acf-json
|-- assets
    |-- fonts
    |-- images
    |-- scripts
        |-- vendor
        |-- main.js
    |-- styles
        |-- base
        |-- components
        |-- layouts
        |-- vendor
        |-- main.scss
    |-- manifest.json
|-- components
|-- lang
|-- lib
|-- templates
```

#### acf-json
This folder is used for syncing Advanced Custom Field Groups with local copies in the theme. For more info, see [ACF: Local JSON](https://www.advancedcustomfields.com/resources/local-json/).

#### assets/images
All images used in the theme live here

#### assets/scripts
All JavaScript used in the theme should live here. All theme specific JS can be included in the main.js file. Typically functions are written as standalone functions outside of the DOM-based routing function. Then inside `var Sage`, you can call your function only on the page(s) that requires it.

#### assets/styles
All styles used in the theme should live here. For CSS, we are using [Sass](http://sass-lang.com/). Modularize your Sass into separate, logically named files and then import into `assets/styles/main.scss`.

#### assets/.../vendor
Any third-party libraries included in the theme should live in the appropriate vendor folder - either `/styles/vendor` or `scripts/vendor`. These assets can then be included in `/assets/manifest.json` to be compiled correctly. This route should only be taken if the library cannot be installed with Bower (see Bower section below).

#### components
Partial files for the Cuberis Components system. See `componify()` in lib/extras.php

#### lib
This is where all of your partial files live for importing into the main `functions.php`. Each file should be modularized and only contain discrete functionality. Additionally, each file should be named appropriately according to the code it contains. For more info, see "The Functions File" section above.

### Bootstrap

Currently we are building on top of [Bootstrap 3](http://getbootstrap.com/) for our framework. Bootstrap is being included via Bower. If you do not need all of the JavaScript components that come with the Bootstrap framework, consider removing theme from the `bower.json` overrides and they will not be included in the build process.

### Bower

Include third-party libraries in your theme using [Bower](http://bower.io/). Overrides can be included in the `bower.json` file if a custom build is desired. The theme's gulpfile will automatically attempt to read the `bower.json` file and include any necessary CSS and JS in the compiling of your theme assets. However, this does not work with every library and in that case, the library can be included directly in your theme assets folder, leaving note of what version of the plugin you are using.

### Plugins

As a rule Cuberis embraces a minimalistic approach to the use of plugins. If functionality can easily be built into the theme, that is prefereable to addition of external plugins. For more complicated enhancements there are several plugins that are used within nearly every project including:

* Advanced Custom Fields
* Gravity Forms
* WordPress SEO
* Backup Buddy

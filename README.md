# Ember Service Worker Asset Cache

This package is a fork of `ember-service-worker-asset-cache`, written by [Marten Schilstra](http://twitter.com/martndemus) and powers a potential offline mode in Ghost. It contains adjustments specific to Ghost, [you probably want the original](https://github.com/DockYard/ember-service-worker-asset-cache).

## F#$& my assets aren't updating in development mode

Turn on the "Update on reload" setting in the `Application > Service Workers`
menu in the Chrome devtools.

## Installation

```
ember install ember-service-worker-ghost-cache
```

## Configuration

You can configure extra files to include and if your app's file are on a CDN,
you can configure the CDN url.

The configuration is done in the `ember-cli-build.js` file:

```js
var EmberAddon = require('ember-cli/lib/broccoli/ember-addon');

module.exports = function(defaults) {
  var app = new EmberAddon(defaults, {
    'asset-cache': {
      // which asset files to include, glob paths are allowed!
      // defaults to `['assets/**/*']`
      include: [
        'assets/admin-engine.js',
        'fonts/font-awesome.*'
      ],

      // which asset files to exclude, glob paths are allowed!
      exclude: [
        '**/*.gif'
      ],

      // manually include extra assets
      manual: [
        'https://cdn.example.com/foo-library.js'
      ],

      // changing this version number will bust the cache
      version: '1',

      // if your files are on a CDN, put the url of your CDN here
      // defaults to `fingerprint.prepend`
      prepend: 'https://cdn.example.com/'
    }
  });

  return app.toTree();
};
```

## Legal

This package is a fork of `ember-service-worker-asset-cache`, written by [Marten Schilstra](http://twitter.com/martndemus) from [DockYard](http://dockyard.com/), Inc. &copy; 2016

[Licensed under the MIT license](http://www.opensource.org/licenses/mit-license.php)

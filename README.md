Semantic UI for Meteor
======================

This package integrates [Semantic UI](http://semantic-ui.com) into Meteor and lets you configure what parts you need.

Installation
------------

    meteor add semantic:ui flemay:less-autoprefixer jquery

Usage
-----

1. create an empty `custom.semantic.json` file within your client library folder. suggested location of `/client/lib/semantic-ui/custom.semantic.json` depending on your applications structure
2. start meteor
3. if you are happy with the default options for Semantic-UI, remove the newly generated `.custom.semantic.json` at this point
4. otherwise edit `custom.semantic.json` (which has now been populated) to select only the definitions and themes you want
5. save the file and it will generate Semantic UI

custom.semantic.json
--------------------

`custom.semantic.json` is the most important file. If it is empty, `semantic:ui` will generate the content with all the definitions and themes. By default, it sets to true all definitions and the theme "default".

```
{
  "definitions": {
    "accordion": true,
    "ad": true,
    "api": true,
    ...
  },
    "themes": {
      "amazon": false,
      "basic": false,
      "bookish": false,
      "bootstrap3": false,
      "chubby": false,
      "classic": false,
      "default": true,
      ...
    }
```

Changing any value will trigger the package to regenerate the files/folders accordingly.

Generated Structure
-------------------

This package generates the following structure based on `custom.semantic.json`

```
+- definitions/
+- site/
+- themes/
|- .custom.semantic.json
|- custom.semantic.json
|- semantic.less
|- theme.config.import.less
|- theme.import.less
```

The following table explains the generated files/folders and if they are editable without losing any changes when generating.

File/Folder | Description | Generated | Editable
--- | --- | --- | ---
definitions/ | contains the `less` and `javascript` definitions for each component | always | no
site/ | contains your current site's theme | only if it does not exist | yes
themes/ | contains *pre-packaged themes* including Semantic's default theme | always | no
.custom.semantic.json | copy of custom.semantic.json (see Generating Trigger) | always | no
custom.semantic.json | contains definitions and themes to be included or not | only if the file is empty | yes
semantic.less | imports the definitions | always | no
theme.config.import.less | defines which theme to use per components | only if the file does not exist | yes
theme.import.less | imports the right themes | always | no

### site/

This folder contains your current site's theme. It is generated only when it does not exist. Therefore if you change `custom.semantic.json` to turn definitions/themes on/off, then it will not affect **site/**. You will either need to add/remove files in **site/** or remove the **site/** folder so it can be regenerated again.

Generating Trigger
------------------

Every time Meteor starts (or refreshes) it calls the package `semantic:ui` to generate Semantic UI.

The package has a simple mechanism based on the difference of `custom.semantic.json` and `.custom.semantic.json` to avoid generating all the time the files and folders.

Therefore if the file `.custom.semantic.json` does not exist or it is different than `custom.semantic.json` then it will generate Semantic UI.  You need to do one of these to make it work the first time.

Dependencies
------------
**[flemay:less-autoprefixer](https://atmospherejs.com/flemay/less-autoprefixer)**: Semantic UI needs autoprefixer to be compiled.

> **Note 1:** You can choose any less-autoprefixer package.
> **Note 2:** Since the package compiles `LESS` files you don't need the `less` package.

**[semantic:ui-data](https://atmospherejs.com/semantic/ui-data)** is being used to get Semantic UI files.

Contributing
-------------

Contributors are very welcome.

License
-------

MIT license

Credits and Acknowledgements
----------------------------

**[nemo64:bootstrap](https://atmospherejs.com/nemo64/bootstrap)**: semantic:ui has been inspired by nemo64:bootstrap. It uses a very similar approach.

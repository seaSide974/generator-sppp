# generator-sppp (SharePoint Pull-n-Push Generator)

> [Yeoman](http://yeoman.io/) generator for SharePoint client-side applications

[![NPM](https://nodei.co/npm/generator-sppp.png?mini=true&downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/generator-sppp/)

[![npm version](https://badge.fury.io/js/generator-sppp.svg)](https://badge.fury.io/js/generator-sppp)
[![Downloads](https://img.shields.io/npm/dm/generator-sppp.svg)](https://www.npmjs.com/package/generator-sppp)

Yeoman generator for SharePoint - lets you quickly set up a project with sensible defaults for pulling and pushing files between SharePoint asset library and local projects sources.

Generated project allows immediately start developing SharePoint client-side solutions in Visual Studio Code or any other editor with instant publishing changes to SharePoint web site and downloading specific assets from SP Document library folder to local project assets which can be enforced with Git Diff algorithm for tracking changes.

----
# New in v 1.5.0

- Live reload functionality is integrated
- Dynamic configuration helpers

----

## Supported SharePoint versions:
- SharePoint Online
- SharePoint 2013
- SharePoint 2016

## How to use:

### Install:

To use Yeoman, one need to has Node.js and NPM installed on the computer. Basic installation process description can be found in [this blog post](https://www.linkedin.com/pulse/preparing-development-machine-client-side-sharepoint-mac-koltyakov?trk=pulse_spock-articles).

Alter Node.js and NPM are staffed, install `Gulp`, `Bower`, `Yeoman` and `generator-sppp` globally in your Node.js environment.

```bash
npm install -g gulp bower yo generator-sppp
```

### Generate:

Make a new directory or clone a blank Git project of your own and navigate to the created folder.

Inside project directory execulte:

```bash
yo sppp [YourProjectName]
```

Then follow the the Yoman wizard instructions:

![Generator in action](http://koltyakov.ru/images/generator-sppp-demo.gif)

### Sync with SharePoint:

Now you can run gulp [sppull](https://www.npmjs.com/package/sppull) task:

```bash
gulp sppull-all
```

![SPPull in action](http://koltyakov.ru/images/generator-sppp-demo-2.gif)

It will deliver all files from assets folder from SharePoint to local directory.

Run gulp watch task before starting editing files:

```bash
gulp watch-assets
```

On files change they are uploaded and published to SharePoint with use of [gulp-spsave](https://www.npmjs.com/package/gulp-spsave).

For publishing all .src project files, `publish` task can be used:

```bash
gulp publish
```

### Additional Gulp tasks:

#### Config validation and prompting

```bash
gulp touch-conf
```

Checks basic minimal configs and prompts on configuration missing.

#### Watch assets changes with live reload

```bash
gulp watch-live
```

Chech [sp-live-reload project page](https://github.com/koltyakov/sp-live-reload) more information.

## SharePoint communication layer

- [sppull](https://github.com/koltyakov/sppull) library is used for downloading files from SharePoint
- [gulp-spsave](https://github.com/s-KaiNet/gulp-spsave) library is used for saving files to SharePoint
- [sp-request](https://github.com/s-KaiNet/sp-request) and [node-sp-auth](https://github.com/s-KaiNet/node-sp-auth) are in charge for low level communication with SharePoint
- [sp-live-reload](https://github.com/koltyakov/sp-live-reload) library is used for instantaneous page reload

Communication layer settings are stored in `./config/_private.conf.json`, parameters settings description can be found [here](https://github.com/koltyakov/generator-sppp/tree/master/docs/authparameters.md).
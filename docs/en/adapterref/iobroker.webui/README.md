# ioBroker.webui

![Number of Installations](https://iobroker.live/badges/webui-installed.svg) 
![Stable version](https://iobroker.live/badges/webui-stable.svg) 
[![NPM version](https://img.shields.io/npm/v/iobroker.webui.svg)](https://www.npmjs.com/package/iobroker.webui)
[![Downloads](https://img.shields.io/npm/dm/iobroker.webui.svg)](https://www.npmjs.com/package/iobroker.webui)

[![NPM](https://nodei.co/npm/iobroker.webui.png?downloads=true)](https://nodei.co/npm/iobroker.webui/)

webui for ioBroker

![image](https://raw.githubusercontent.com/iobroker-community-adapters/ioBroker.webui/master/screenshot.png)

## Tutorial Videos (atm. in german only)

https://www.youtube.com/@jogibear9988

## Description

This is a complete visualization system for ioBroker.

It includes features like:

  - own simple scripting language
  - binding to ioBroker objects including converters & javascript expressions
  - paste of images from clipboard
  - drag drop of external images
  - drag drop of ioBroker objects to automaticy create bindings
  - drag drop of ioBroker objects to Properties to create Bindings to them
  - relative signal paths to ioBroker objects in screens (the full path can be hand over from outside to screen)
  - split view edit of html code
  - global stylesheet support
  - usage of npm packages containing webcomponents
  - screens inside of screens
  - use all icon packages from ioBroker
  - use charts from ioBroker
  - use combined signals object id's  e.g. "webui.0.test3.{webui.0.test3.select}" -> this will use the value from webui.0.test3.select for the signal name

## Installation

### Dependecies

  - You need the Web Adapter installed. It works with the following settings: ![image](https://raw.githubusercontent.com/iobroker-community-adapters/ioBroker.webui/master/web.png)
  
## Concepts

### Description

The Designer uses Webcomponents, so the HTML you Design is inside of a Shdowroot of a Webcomponent. This mens, you cannot style <body> or <html> inside of the Stylesheet. To style the outer Layout, use the ":host" selector.
This also means, you cannot use "on..." eventhandlers. Use the "@..." event assignment.

### Custom Controls in WebUI

You can create own reusable CustomControls in WebUI. This can have individual Javascript, Properties and a template.

You can use Double-Bracket Syntax and Double-Curly-Braket Syntax of "BaseCustomWebcomponent" to create bindings from the Template to the properties defined in the Designer. Curylbrackets create two way Bindings.
If you use the Bindings Dialog, you can Bind to a Property with ??Propertyname and to IoBroker Object in the Property via ?Propertyname.
In Scripts you can also write to Signals defined in Custom Properties.

You could also include Javascript in your CustomControl or Screen. Also you could use export a function "init(instance)" wich will be called when your CustomControl will be instanciated. (and also the connected and disconnected functions could be used)

## Sponsoring

If you want to help the development, sponsor this project at https://github.com/sponsors/jogibear9988

## Developing
  * Install Repository as Adapter in IOBroker
  * Download the Repository to an extra "dev" directory, do not develop inside the ioBroker Node_modules directory.
  * Do the following steps inside of the "dev" dirctory.

  * Install dependencies 
```
  $ npm install
```

  * Compile Typescript after doing changes (or press Ctrl + Shift + B in VsCode and select "tsc watch")
```
  $ npm run tsc
```

  * Adjust 'config.js' to match you ip-adress and port for your iobroker
   (The config.js in the repository root will be replaced with the one in '/config' when running 'npm build')
```
    window.iobrokerHost = '192.168.1.2';
    window.iobrokerPort = '8082';
    window.iobrokerSocketScriptUrl = 'http://' + window.iobrokerHost + ':' + window.iobrokerPort + '/lib/js/socket.io.js';
```

  * Run the app in a local server
```
  $ npm start
```

  * Navigate Chrome to [localhost:8000]() to see the app.

### More about Development

  - Run 
```
  $ npm run reflection
``` 
   to recreate reflection files for Scripting wich are used for the property grid

  - Run 
```
  $ npm run build
``` 
   to copy compiled files and node_modules to www folder so adapter is installable via github

  - Run 
```
  $ npm run release
  $ npm publish
``` 
   to create correct release commit for iobroker, Be carefull this also pushes to git repo.
   Be sure to edit "CHANGELOG.md" before, the text in "## **WORK IN PROGRESS**" in README.Md will be used for version info

## Info about the Adapter.

The Adapter is based on the following Designer component:
https://github.com/node-projects/web-component-designer

You need to create a screen "start", this is the first one called when you open runtime.html, 
but you can change this via query parameter:
runtime.html?screenName=screen2

## Changelog
<!--
	Placeholder for next versions:
	### __WORK IN PROGRESS__
-->
### 1.1.2 (2024-02-27)
- fix broken designer package

### 1.1.1 (2024-02-27)
- designer and docking fixes

### 1.1.0 (2024-02-26)
- support undock to new browser window
- preview fixes for position: static in styles

### 1.0.56 (2024-02-26)
- screenviewer - add also nodes from domparser head

### 1.0.55 (2024-02-22)
- more designer fixes

### 1.0.54 (2024-02-22)
- multiple designer fixes

### 1.0.53 (2024-02-19)
- fix lazy bound lit event name

### 1.0.52 (2024-02-19)
- fix captured local

### 1.0.51 (2024-02-19)
- fix lazy loaded lit elments
- fix script url

### 1.0.50 (2024-02-18)
- again fix in class binding

### 1.0.49 (2024-02-18)
- class is attribute in bindings
- fix error logging

### 1.0.48 (2024-02-17)
- fix wunderbaum error

### 1.0.47 (2024-02-15)
- designer fixes with property grid

### 1.0.46 (2024-02-15)
- designer updates

### 1.0.45 (2024-02-12)
- update designer with bugfixes

### 1.0.44 (2024-02-11)
- fix bindings in designer

### 1.0.43 (2024-02-11)
- refresh tree when controls deleted

### 1.0.42 (2024-02-11)
- fix grid resize
- fix grid extension display

### 1.0.41 (2024-02-10)
- better element drawing (with undo)
- better title extension

### 1.0.40 (2024-02-10)
- dblclick in solution should not change tool
- designer update for performance fixes

### 1.0.39 (2024-02-09)
- upgrade designer package once more to fix some issues

### 1.0.38 (2024-02-09)
- fix blockly
- add blockly templated string
- work on adopted styles
- update designer to fix snaplines

### 1.0.37 (2024-01-31)
- designer fix for background

### 1.0.36 (2024-01-31)
- upgade to new designer for better style encapsulation

### 1.0.35 (2024-01-30)
- package upgrades (fix in designer for css patching)
- typos

### 1.0.34 (2024-01-28)
- indirect signal for $ access

### 1.0.33 (2024-01-24)
- one more designer update

### 1.0.32 (2024-01-24)
- fix for nested stylesheets

### 1.0.31 (2024-01-23)
- string could be null

### 1.0.30 (2024-01-22)
- better script errors

### 1.0.29 (2024-01-22)
- remove a few errors

### 1.0.28 (2024-01-22)
- npm upgrade for error of undoservice

### 1.0.27 (2024-01-22)
- toast message on errors

### 1.0.26 (2024-01-22)
- npm package upgrades

### 1.0.25 (2024-01-21)
- use appendChild

### 1.0.24 (2024-01-21)
- fix later loaded scripts

### 1.0.23 (2024-01-21)
- twoway should only set first value
- fix error with noParse

### 1.0.22 (2024-01-20)
- fix binding with unit
- fix refactor service missing command

### 1.0.21 (2024-01-19)
- fix designer grid overlay
- stecil ackage hacks

### 1.0.20 (2024-01-18)
- fix broken split view

### 1.0.19 (2024-01-17)
- simpler one way bindings with expressions

### 1.0.18 (2024-01-17)
- text selection selects in designer

### 1.0.17 (2024-01-16)
- fix opacity of D&D node

### 1.0.16 (2024-01-16)
- fix drag drop of tree nodes

### 1.0.15 (2024-01-14)
- support upper/lowercase and spaces in screens & controls

### 1.0.13 (2024-01-14)
- correct event name in lit bindings

### 1.0.12 (2024-01-14)
- upgrade baseCustomWebcomp for attribute binding

### 1.0.11 (2024-01-14)
- API for reading object lists

### 1.0.10 (2024-01-14)
- fix selected tool

### 1.0.9 (2024-01-14)
- bugfix controls editor

### 1.0.8 (2024-01-14)
- fix import/export

### 1.0.7 (2024-01-14)
- bigger formula editor when multiline

### 1.0.6 (2024-01-14)
- draw widgets when selected in tree

### 1.0.5 (2024-01-14)
- bind to iobroker objects (via $ prefix)

### 1.0.4 (2024-01-14)
- fix open screens in folders

### 1.0.3 (2024-01-14)
- only lowercase folders

### 1.0.2 (2024-01-14)
- variablen in convertern
- configurable meta tags

### 1.0.1 (2024-01-13)
- fix issue with npm

### 1.0.0 (2024-01-13)
- new script command: CalculateSignalValue
- javascript code completition
- better types in code completition
- fix writing of child nodes if content is bound at design time
- use monaco editor in expressions
- use custom var names in expressions
- Screens & Controls can have subfolders
- decl. shadow dom support in screen viewer
- allow 'local_' as tag prefix for local vars

### 0.23.3 (2024-01-04)
- add local valueAsNumber property

### 0.23.2 (2024-01-03)
- again fix runtime was not initialized

### 0.23.1 (2024-01-03)
- fix runtime was not initialized

### 0.23.0 (2024-01-03)
- todo, support 2way bindings too custom properties
- code completition for iobrokerHandler and runtime
- simple scripts, access value of event

### 0.22.7 (2023-12-25)
- and one more...

### 0.22.6 (2023-12-25)
- and one more fix on importmaps

### 0.22.5 (2023-12-25)
- more fixes with import map

### 0.22.4 (2023-12-25)
- work on export directive

### 0.22.3 (2023-12-25)
- fix missing .js extensions

### 0.22.2 (2023-12-25)
- fix scripts

### 0.22.1 (2023-12-25)
- add open screen in blockly

### 0.22.0 (2023-12-25)
- work on esbuild (but not yet ready, delayed till blockly is ESM)
- bugfixes with scripts
- remove typescript, use javascript directly
- typed value on SetValue function

### 0.21.3 (2023-12-20)
- fix set style

### 0.21.2 (2023-12-20)
- more commands in blockly

### 0.21.1 (2023-12-19)
- fixed paths

### 0.21.0 (2023-12-19)
- start of blockly support

### 0.20.7 (2023-12-15)
- fix importmap creation missed "/"

### 0.20.6 (2023-12-12)
- few wunderbaum fixes

### 0.20.5 (2023-12-11)
- better custom properties view

### 0.20.4 (2023-12-11)
- fix in css prop binding

### 0.20.3 (2023-12-11)
- update designer npm

### 0.20.2 (2023-12-11)
- fix for class binding

### 0.20.1 (2023-12-11)
- binding for classes

### 0.20.0 (2023-12-11)
- allow bindings to css vars

### 0.19.3 (2023-12-10)
- switch loglevel

### 0.19.2 (2023-12-10)
- package updates

### 0.19.1 (2023-12-07)
- fix load error

### 0.19.0 (2023-12-07)
- waitForReady needs to be awaited

### 0.18.15 (2023-12-06)
- fix missing null check

### 0.18.14 (2023-12-06)
- fix normal binding unsubscribe

### 0.18.13 (2023-12-06)
- fix historic binding unsubscribe

### 0.18.12 (2023-12-06)
- remove bindings in customcontrols

### 0.18.11 (2023-12-06)
- fix broken load historic

### 0.18.10 (2023-12-06)
- load historic only when previous load is finished

### 0.18.9 (2023-12-05)
- fix tooltips

### 0.18.8 (2023-12-05)
- lazy remove the title

### 0.18.7 (2023-12-05)
- better fix for monaco

### 0.18.6 (2023-12-05)
- fix for monaco bug
- title removed

### 0.18.5 (2023-12-05)
- code completition for base custom webcomponent
- object property type

### 0.18.4 (2023-12-03)
- better text for historic bindings cancel

### 0.18.3 (2023-12-03)
- fix reload in dynamics editor

### 0.18.2 (2023-12-03)
- ui for historic binding
- fixes in refactor view

### 0.18.1 (2023-12-03)
- fixes in refactor service

### 0.18.0 (2023-12-01)
- tooltip in solution explorer
- npm upgrade of designer
- refactor view for bindings and scripts

### 0.17.0 (2023-11-29)
- remove 2 uneeded files
- designer update

### 0.16.6 (2023-11-28)
- check for invalid propertynames
- move properties

### 0.16.5 (2023-11-27)
- copy screen and custom controls

### 0.16.4 (2023-11-27)
- fix usage of webui in windows

### 0.16.3 (2023-11-24)
- extra style for font declarations, they are not allowed in shadow dom

### 0.16.2 (2023-11-23)
- fix remove script command

### 0.16.1 (2023-11-23)
- additional file dnd

### 0.16.0 (2023-11-23)
- add additional files node and upload

### 0.15.1 (2023-11-22)
- export as xml (screens & controls)
- binding historic with reload
- fix dialog

### 0.15.0 (2023-11-19)
- uncloseable dialog 
- css properties for dialog
- binding to historic data

### 0.14.1 (2023-11-12)
- dialog centered

### 0.14.0 (2023-11-12)
- add simple dialog

### 0.13.1 (2023-11-11)
- two way bindings with expressions

### 0.13.0 (2023-11-09)
- fix upercase screen names in runtime
- raster in designer is now adjustable
- copy object nodes now copies complete string
- context menu to directly edit custom element
- fix handler path in script
- uiChangedView now workin
- error when importing invalid file (for example html instead of json)

### 0.12.3 (2023-09-20)
- after eval removal, functions need a return

### 0.12.2 (2023-09-20)
- events names for 2way bindings need a editor

### 0.12.1 (2023-09-20)
- two way for indirect bindings

### 0.12.0 (2023-09-20)
- support indirect bindings via {...} in signals (like in vis)

### 0.11.2 (2023-09-17)
- check npm package name

### 0.11.1 (2023-09-16)
- fix build on windows

### 0.11.0 (2023-09-11)
- dragdrop fixes
- screen/control size fixes
- connected/disconnected callbacks

### 0.10.0 (2023-09-10)
- new script commands
- bugfix with bindings and empty events
- select exported function in javascript
- bugfix in save of screens
- typescript in scripts
- started work on translateable runtime

### 0.9.0 (2023-09-06)
- signal selector in properties
- screen selector in properties
- new screen had style in scripts
- indirect value/property acces from scripts via editor
- list multiple undo entries (on hold of undo)

### 0.8.0 (2023-09-03)
- update designer to add and fix some commands
- move screen/control scripts out of html code
- add a javascript editor view
- bugfix when states where null after a fresh install
- designer addons do now work again
- docking framework updated, cause of bugs with undocking

### 0.7.0 (2023-09-01)
- screens and controls have now settings (width, height, useGlobalStyle)

### 0.6.0 (2023-09-01)
- removed many uneeded files from installation

### 0.5.1 (2023-09-01)
- show version in ui

### 0.5.0 (2023-09-01)
- signal as property type
- removed svg-image control
- shorter custom control tag name
- better dynamics editor
- dock ui fixes
- control ui from backend (switch view, reload)

### 0.4.0 (2023-08-30)
- remove uneeded files from upload
- remove icons into extra iobroker packages
- support icon adapters
- rename screens & controls

### 0.3.0 (2023-08-29)
- default value for custom properties
- open screens only once
- property bindings default one way

### 0.2.3 (2023-08-28)
- rework how custom controls are initalized

### 0.2.2 (2023-08-28)
- better support & fixes of custom elements
- enum properties in custom controls
- sample custom controls

### 0.2.1 (2023-08-28)
- null ref fix in bindings

### 0.2.0 (2023-08-28)
- Import/Export of Screens/Images/Controls
- Define your own Controls directly in webui
- Drag/Drop of Icons/Images to Properties
- Drag/Drop of objects to Bindings-Editor Signalname
- Basic functionality of CustomControls

### 0.1.0 (2023-08-27)
-   initial public release

## License
The MIT License (MIT)

Copyright (c) 2024 jogibear9988 <jochen.kuehner@gmx.de>

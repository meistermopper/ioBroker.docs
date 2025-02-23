---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.vis-2-widgets-jaeger-design/README.md
title: Spezielle Jaeger Design-Widgets für ioBroker.vis 2.0
hash: Ta+VSlxWD5cdm7oEr2W52PZD5C1t3yo72JsZoutNOjk=
---
![Logo](../../../en/adapterref/iobroker.vis-2-widgets-jaeger-design/admin/vis-2-widgets-jaeger-design.png)

![Anzahl der Installationen](http://iobroker.live/badges/vis-2-widgets-jaeger-design-stable.svg)
![NPM-Version](http://img.shields.io/npm/v/iobroker.vis-2-widgets-jaeger-design.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.vis-2-widgets-jaeger-design.svg)
![NPM](https://nodei.co/npm/iobroker.vis-2-widgets-jaeger-design.png?downloads=true)

# Spezielle Jaeger Design-Widgets für ioBroker.vis 2.0
## Widgets
### Knöpfe und Schalter
### Aktuelle Nachrichten
![Aktuelle Nachrichten](../../../en/adapterref/iobroker.vis-2-widgets-jaeger-design/img/news.png)

Um dieses Widget zu verwenden, müssen Sie ein kleines Skript im Javascript-Adapter erstellen:

```
const axios = require('axios');

function readRss() {
    axios('https://www.n-tv.de/rss')
        .then(resp => setState('javascript.0.rss', resp.data.toString(), true));
}

createState('javascript.0.rss', {type: 'string'}, () => {
    setInterval(() => readRss(), 60000 * 60 * 2); // update rss every 2 hours
    readRss();
});
```

Und verwenden Sie dann das Objekt `javascript.0.rss` in diesem Widget.

<!-- Platzhalter für die nächste Version (am Anfang der Zeile):

### **ARBEIT IN ARBEIT** -->

## Changelog
### 0.6.3 (2023-07-25)
* (bluefox) Added many new features

### 0.6.1 (2023-07-21)
* (bluefox) Added max height/width for floors

### 0.6.0 (2023-07-19)
* (bluefox) Corrected some errors with information

### 0.5.2 (2023-07-02)
* (bluefox) Support of false for scenes

### 0.5.0 (2023-06-28)
* (bluefox) Added support for the new vis
* (bluefox) Added page configurable margins

### 0.4.6 (2023-06-19)
* (bluefox) Corrected sub menu

### 0.4.5 (2023-06-13)
* (bluefox) Corrected visualization of view

### 0.4.0 (2023-05-31)
* (bluefox) Added exclusions
* (bluefox) Added possibility to show information on the very top of layout

### 0.3.2 (2023-04-05)
* (bluefox) Corrected license problem

### 0.3.1 (2023-03-22)
* (bluefox) Corrected build process

### 0.3.0 (2023-03-21)
* (bluefox) Implemented dark mode

### 0.2.3 (2023-03-09)
* (bluefox) update packages

### 0.2.2 (2023-03-06)
* (bluefox) Updated thermostat widget

### 0.2.1 (2023-02-03)
* (bluefox) Mobile views tuned

### 0.2.0 (2023-02-01)
* (bluefox) implemented mobile view

### 0.1.3 (2023-01-30)
* (bluefox) initial commit

## License
Copyright (c) 2022-2023 bluefox <dogafox@gmail.com>
All rights reserved.
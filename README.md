# Dataviz Bordeaux-Métropole: point d'apports volontaires

Cartographie des `940` points de collecte de la région CUB/Bordeaux-Métropole. 
Elle permet de rapidement localiser les points les plus proches pour allez jeter les bouteilles vides suite à une 
soirée ou un événement.  

**en**: Dataviz to visualize different type of trash collecting points in the area of Bordeaux, France.

![dataviz preview](./preview.png)

<!-- MarkdownTOC depth=3 -->

- [Data Sources](#data-sources)
- [Install](#install)
	- [Makefile](#makefile)
	- [Getting started](#getting-started)
- [Want to fork or scaffold a similar project ?](#want-to-fork-or-scaffold-a-similar-project-?)
	- [License](#license)
	- [Tools: GDAL (Geospatial Data Abstraction Library)](#tools-gdal-geospatial-data-abstraction-library)
	- [JavaScript Libraries](#javascript-libraries)
- [Privacy](#privacy)

<!-- /MarkdownTOC -->


## Data Sources

* geo-location come from [official Gironde Open Data portal](http://www.datalocale.fr/dataset/en_empac_p) ;
* adress from [OpenStreetMap Nominatim](http://wiki.openstreetmap.org/wiki/Nominatim).

You may also find the website [Où recycler.fr](http://ourecycler.fr/point-collecte/33800/Bordeaux) interesting.


## Install

Start by cloning the project repository:
```
git clone https://github.com/edouard-lopez/collecte-verre-bordeaux.git
cd collecte-verre-bordeaux
make install
```

This is the minimum to be able to build the app. If you want to dev, try:
 
```
make install-development
```

### Makefile

There is a [makefile](./makefile) that automate the installation and data-mining tasks.

The default task will build a working environment and process data, you only need to run `make` in the project root directory. That is the equivalent to run:

```
make install clean .tmp
make get-emplacements extract-emplacements convert2geojson convert2geojsonVanilla convert2topojson reverse-location2adresses fix-reverse-location
```


### Getting started

Install project dependecy using `npm` and `bower`:
```
npm install
bower install
```
Run a preview with `gulp`:
```
gulp serve
```
Start playing !


## Want to fork or scaffold a similar project ?

### License

The Project under [GPLv3 license](http://choosealicense.com/licenses/gpl-3.0/).


### Tools: GDAL (Geospatial Data Abstraction Library)

To manipulate Shapefile, you need the command [`ogr2ogr`](http://www.gdal.org/ogr2ogr.html) command line, which is 
part of [GDAL library](http://www.gdal.org/). For `JSON` manipulation you will need the [`jq` C-library]
(https://stedolan.github.io/jq/) which is 
avalaible in Linux repo:
```
sudo apt-get install jq gdal-{bin,contrib}
```


### JavaScript Libraries


So start by installing [Gulp webapp generator](https://www.npmjs.org/package/generator-gulp-webapp) for `yeoman`:
```
sudo npm install -g generator-gulp-webapp gulp
```

Continue by scaffolding the application with the `yeoman`'s generator:
```
mkdir my-map-app && cd my-map-app
yo gulp-webapp
```
Then install others dependencies:

* I'm using [LeafletJS for interactive map](http://leafletjs.com/) ;
* and [`d3.js` for the dataviz](http://d3js.org/).

```
npm install --save-dev jq xml2json-command topojson generator-gulp-webapp gulp gulp-sass
bower install --save topojson font-awesome d3 leaflet leaflet.markercluster es6-promise
```

Finish by running `gulp` for building and gulp watch for preview :
```
gulp watch
```


## Privacy

The use of **geo-location is completely optional**. Being done client-side there is no data store or collected by this app.


## Changelog

* 2016-juil.-19: from `913` to `940` entries ;
* 2015-mar-21: update data add 9 new sites.

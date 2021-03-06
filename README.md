# CViTjs - Chromosome Visualization Tool, the JavaScript edition

<table>
  <tr>
    <td width="100%">
**Table of Contents** 
<ul>
  <li> [About](#about) </li>
  <li> [Setup](#setup) </li>
  <li> [PHP](#php) </li>
  <li> [Gulp](#gulp) </li>
  <li> [Roadmap](#roadmap) </li>
</ul> 
    </td>
    <td>
![alt text](img/cvitjs.png?raw=true "CViTjs")
    </td>
  <tr>
</table>
  
## About

CViTjs is an interactive JavaScript implementation of the original Chromosome 
Visualization Tool (<a href="https://sourceforge.net/projects/cvit/">CViT</a>), 
which was written in Perl. CViTjs displays features on chromosomes, linkage groups, or just 
about any sort of backbone that has length and a two-dimensional, linear coordinate system.

**The tool is currently in beta. Feedback is gratefully accepted.**

Functionality:
+ Data is formatted in <a href="http://gmod.org/wiki/GFF3">GFF3</a>
+ Place various types of features on "backbones" (e.g., centromeres, markers, gene models, regions)
+ Similar to genome browsers, CViTjs has a concept of tracks, sets of features organized in a group.
+ A track can be interactively turned on and off
+ Zooming and panning
+ Annotate an image with the drawing tool
+ Export image to a png or svg.

Features:
+ AMD style modules using RequireJS. Makes it easier to manage libraries, avoids polluting the global object, and allows for nicer later expansion.
+ Software stack: Paper.js, RequireJS and jQuery.

[See CViTjs in action](https://awilkey.github.io/cvitjs/?data=test1)

![alt text](img/CViTjs_sample.png?raw=true "CViTjs")

## Setup

CViTjs should work right out of the box. One or more data views are defined in cvit.conf,
which is located in the root folder. Sample views are included in the starting cvit.conf.
~~~~
[general]
data_default = test1

[data.test1]
conf = data/test1/cvit.conf
defaultData = data/test1/data.gff
~~~~
The [general] section and at least one dataset definition is required in cvit.conf.

In this example, to display the test1 dataset the URL would be: your-CViTjs-URL/cvitjs/?data=test1

For each dataset you will need a <a href="http://gmod.org/wiki/GFF3">GFF3</a> file defining the backbones and an image configuration file, typically named cvit.ini. Almost every aspect of the presentation of the image can be controlled in the configuration file. See the sample file in data/test1/ for more information.

## PHP

PHP can launch CViTjs with a calculated set of inputs.

~~~~
coming soon!
~~~~
## Gulp

Though not required for CViTjs to work, there is a gulpfile available for those that care. Right now it is just setup to do basic linting and beautification of the generated source. the default behavior also includes watching, so if you decided to edit any files, it will lint and beautify them for you.

### How to Gulp

If you have never used gulp before, it is a build system for JavaScript that requires NodeJS

Get Node here (or from your package manager): [Get Node](https://nodejs.org/ "Node's Homepage")


+ Navigate your terminal to the root of your copy of CViTjs.
+ type: ``` npm install ```
+ This will use the node package manager (npm) to download local copies of the required gulp and node packages as listed in required.json
+ type: ``` gulp ```
+ This will run all the tasks in the gulpfile. The current tasks are:
	+ lint: Runs a linter against the javascript in js/cvit. Will report out any problems it finds in the terminal.
	+ beautify: Makes the javascript pretty. In this case will go through and remove excess whitespace, and replace tabs with two spaces, as well as starndardize indent levels.
	+ watch: Watches for files in js/cvit to change.
	+ default: Runs all of the above tasks. With watch, this means that it will stay active in that terminal window until stopped (^C or equivalent) and run the lint and beautify tasks whenever it detects a change.
+ Note you can run any task seperately by using ``` gulp <task> ```

## Roadmap
Things to do on the way to the 1.0 release:
+ Upload file manager
	+ Basic data validation
	+ Customized glyphs
+ Advanced URI control 
+ Missing Glyphs:
    + Measure
    	+ Heat
        + Histogram
        + Distance
+ Release unit tests

<br><br>
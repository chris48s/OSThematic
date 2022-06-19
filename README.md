# OSThematic

## ⚠️ Deprecated

This package is now deprecated and archived because the OS Openspace API [has been withdrawn](https://www.ordnancesurvey.co.uk/business-government/products/openspace).

---

Thematic maps are an excellent way to visualise geographically coded data. This library makes it trivial to create beautiful thematic maps using the Ordnance Survey OpenSpace API and continuous univariate data attached to ONS Geography codes.

## Requirements

* An OS OpenSpace API Key - available from: http://www.ordnancesurvey.co.uk/business-and-government/products/os-openspace/api/
* A web browser (some old version of Internet Explorer not supported due to use of `indexOf` - although this can be added using a shim)

## Installation

`npm install osthematic`

## Usage

Pull in the OS OpenSpace API and OSThematic:

```html
<script type="text/javascript" src="https://openspace.ordnancesurvey.co.uk/osmapapi/openspace.js?key=---YOUR-API-KEY-HERE---"></script>
<script type="text/javascript" src="os_thematic.js"></script>
```

Create a div for our map to live in:

```html
<div id="map" style="width: 700px; height: 500px; border: 1px solid black;"></div>
```

Create an OS OpenSpace map:

```js
var osMap = new OpenSpace.Map('map');
osMap.setCenter(new OpenSpace.MapPoint(400000, 400000), 1);
```

Pass it to the constructor of OSThematic:

```js
var ost = new OSThematic(osMap);
```

Give it an array of data:

```js
ost.setData([
  { 'ons_code': 'E15000001', 'value': 477.1},
  { 'ons_code': 'E15000002', 'value': 484.6},
  { 'ons_code': 'E15000003', 'value': 479},
  { 'ons_code': 'E15000004', 'value': 483.4},
  { 'ons_code': 'E15000005', 'value': 480.6},
  { 'ons_code': 'E15000006', 'value': 539.1},
  { 'ons_code': 'E15000007', 'value': 617.8},
  { 'ons_code': 'E15000008', 'value': 567},
  { 'ons_code': 'E15000009', 'value': 495.6},
  { 'ons_code': 'S15000001', 'value': 518.2},
  { 'ons_code': 'W08000001', 'value': 479.4}
]);
```
(for more info on ONS geography coding, see:

* https://www.ons.gov.uk/methodology/geography
* http://en.wikipedia.org/wiki/ONS_coding_system )

..an array of colours to use:

```js
ost.setColours(["#CC99FF", "#9933FF", "#4C1A80"]);
```

..and the layers you want to use:

```js
ost.setLayers(["EUR"]);
```

(full list of available layers at https://www.ordnancesurvey.co.uk/business-and-government/help-and-support/web-services/administrative-boundaries.html )

and now lets visualise it:

```js
ost.drawMap();
```

OSThematic will display the data by banding it into quantiles for you based on the number of colours you've supplied:

* If you supply 4 colours, you will get quartiles
* If you supply 5 colours, you will get quintiles ..and so on.

## Examples

* https://chris48s.github.io/OSThematic/example1.html
* https://chris48s.github.io/OSThematic/example2.html
* https://chris48s.github.io/OSThematic/example3.html

# Map Marker Awesome

This project provides ...

* Nice, simple, scalable SVG map markers
* with any [Font Awesome](http://fontawesome.io/) icon
* that you can use with Google Maps (and beyond)

## Use it two ways

1. [Generate and download individual SVGs](https://jawj.github.io/MapMarkerAwesome/) with your choice of size, colour and [Font Awesome](http://fontawesome.io/) icon.

2. Embed [the JS library](https://github.com/jawj/MapMarkerAwesome/blob/master/built/mma.js) (~130KB gzipped), to dynamically generate markers with any size, colour and icon at run-time (as [data: URIs](https://en.wikipedia.org/wiki/Data_URI_scheme)).

## Library usage examples

Create these markers:

![plain](https://jawj.github.io/MapMarkerAwesome/examples/plain.svg)
![music](https://jawj.github.io/MapMarkerAwesome/examples/music.svg)
![alsoMusic](https://jawj.github.io/MapMarkerAwesome/examples/alsoMusic.svg)
![alsoAlsoMusic](https://jawj.github.io/MapMarkerAwesome/examples/alsoAlsoMusic.svg)
![largeHeart](https://jawj.github.io/MapMarkerAwesome/examples/largeHeart.svg)
![redWithYellowStar](https://jawj.github.io/MapMarkerAwesome/examples/redWithYellowStar.svg)
![home](https://jawj.github.io/MapMarkerAwesome/examples/home.svg)
![bigHome](https://jawj.github.io/MapMarkerAwesome/examples/bigHome.svg)
![arrow](https://jawj.github.io/MapMarkerAwesome/examples/arrow.svg)
![rotatedArrow](https://jawj.github.io/MapMarkerAwesome/examples/rotatedArrow.svg)
![randomColourPlain](https://jawj.github.io/MapMarkerAwesome/examples/randomColourPlain.svg)

Like this:

```javascript
<script src="mma.js"></script>
<script>
  var mapMarkerAwesome = mapMarkerAwesomeFactory(true);

  var plainIconSrc = mapMarkerAwesome();

  var musicIconSrc = mapMarkerAwesome('music');
  var alsoMusicIconSrc = mapMarkerAwesome('fa-music');
  var alsoAlsoMusicIconSrc = mapMarkerAwesome('\uf001');

  var largeHeartIconSrc = mapMarkerAwesome('heart', { height: 52 });
  var redWithYellowStarIconSrc = mapMarkerAwesome('star', { fill: '#f00', icon: '#ff0' });

  var homeIconSrc = mapMarkerAwesome('home');
  var bigHomeIconSrc = mapMarkerAwesome('home', { iconTransform: 'scale(1.25)' });

  var arrowIconSrc = mapMarkerAwesome('arrow-up', { fill: '#fff', icon: '#444', stroke: '#444' });
  var rotatedArrowIconSrc = mapMarkerAwesome('arrow-up', { 
    iconTransform: 'rotate(22.5)', 
    fill: '#fff', 
    icon: '#444', 
    stroke: '#444'
  });

  function randByte() { return Math.floor(Math.random() * 256); }
  var randomColourPlainIconSrc = mapMarkerAwesome(null, { 
    fill: { r: randByte(), g: randByte(), b: randByte() } 
  });
</script>
```

Then pass the resulting image URIs to the Google Maps library, or wherever else you want to use them.

## Library docs

```javascript
var mapMarkerAwesome = mapMarkerAwesomeFactory(dataURI);
```

The `mapMarkerAwesomeFactory` is the only global variable created by the script. Call this function to create your `mapMarkerAwesome` function. The `dataURI` argument to the factory function is a boolean that determines whether the marker icons generated by the returned function will be plain SVG strings (for example, to be saved as image files) or data URIs (for example, for direct use in the Google Maps API).

```javascript
var iconSVG = mapMarkerAwesome(code, opts);
```

`code` is a string identifying the [Font Awesome](http://fontawesome.io/) icon that's required. You can pass either the Font Awesome icon id (with or without the `fa-` prefix) or the equivalent Unicode character — so `star`, `fa-star` or `\uf005` are exactly equivalent. Pass `null` (or nothing) for a plain marker with no icon.

`opts` is an object with the following keys:

* `fill` specifies the color of the body of the marker — default `#4182c3` (a nice mid blue)
* `stroke` specifies the color of the marker outline — default `#fff` (white)
* `icon` specifies the color for the icon on the marker — default `#fff` (white)
* `height` is an integer specifying the size of the markere via the height, in pixels — default `42`
* `transform` is a string specifying any [SVG transforms](https://developer.mozilla.org/en/docs/Web/SVG/Attribute/transform) to be applied to the icon — default `''` (none)

The `transform` property can be used to tweak the display of any particular icon, such as its positioning, size, and rotation. The coordinate origin of the transform is approximately the centre of the icon.

Colour values (`fill`, `stroke` and `icon`) can be specified as any valid SVG colour string (so `white`, `#fff`, `#ffffff`, `rgb(255,255,255)` and `rgba(255,255,255,1)` are all equivalent). 

They can alternatively be specified as an object with `r`, `g`, `b` keys (with integer values 0 – 255) and an optional `a` key (with numeric value 0 – 1).

## Licence

Code released under the [MIT licence](https://opensource.org/licenses/mit-license.html), except [Font Awesome](http://fontawesome.io/) icons, which remain subject to their original licence (I think).


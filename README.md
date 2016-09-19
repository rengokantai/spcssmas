## spcssmas
###chapter3 Debugging and Optimization
####Debugging for UI Responsiveness
CSS properties and values that trigger reflows are particularly expensive. 
######What is a reflow?
relow: change position, dimension  
repaint: change color, opacity  
Most often triggered by DOM operations.  

compare left and transformX:  
In most browsers, transforms don’t trigger reflows, left operation trigger reflows.  
[review css hacks](http://www.paulirish.com/2009/browser-specific-css-hacks/)

####Code-quality Tools
######csslint
```
csslint stylesheet.css > csslintoutput.txt
```
ignore some property checking. If dropped support for Internet Explorer 6 and 7
```
csslint stylesheet.css --ignore=box-sizing
```
helps
```
csslint --list-rules
csslint --help
```
######analyze-css
```
analyze-css --file stylesheet.css
analyze-css --url http://example.com/css/stylesheet.css
analyze-css --file stylesheet.css > nameoffile.json
```
######uncss
```
uncss index.html article-1.html article-2.html > optimized.css
```
###chapter4 Complex Layouts
####Managing the CSS Box Model
Block-level boxes are rendered vertically according to their source order and (except for tables) expand to fill the available width.  
inline elements:
```
inline, inline-block, inline-table, or ruby
```

####Managing Layers with position and z-index
rules:
- Child stacking contexts with a negative stack level (for example, positioned and z-index: -1)
- Non-positioned elements
- Child stacking contexts with a stack level of 0 (for example, positioned and z-index: auto)
- Child stacking contexts with positive stack levels (for example, positioned and z-index: 1)  


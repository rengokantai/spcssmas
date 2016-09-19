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

####Using CSS Multicolumn Layout
Ex: HTML layout
```
<div class="parent">
    <p>1</p>
    <p>2</p>
</div>
```
shorthand syntax
```
.parent{
  columns: 10em 3 //column-width: 10em; column-number: 3
}
```
(Firefox only supports the -moz-columns/columns shorthand. Setting column-number or -moz-column-number will fail to work.)  

Its value should be in length units. ex: column-width: 200px or column-width: 10em.  
Percentages will not work! Initial value is auto.  

column-number property: If column-width is something other than auto, the browser will create columns of that width up to the number of columns specified by column-number. (value must be an integer greater than 0.)  

If column-width: auto, the browser will create the number of columns specified by column-number.  

####Spacing Columns with column-gap and column-rule  

The initial value of column-gap is normal. In most browsers, that’s about 1em.  

Column width is not affected by changes to column-rule. Instead, column rules sit at the midpoint of the column gap.

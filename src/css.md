# CSS Notes


[Usefull link for CSS sstyle](http://www.csszengarden.com)
Note that you could not change html but only style


## 1 CSS rules
what this about


```html
<style>
p {
    color: blue;
    font-size: 20px;
    width: 200px;
}

h1 {
    color: green;
    font-size: 36px;
    width: center;
}
</style>
```

`p` is a selector;

In the curly braces, there is a declaration, containing property ´´´color´´´and value ´´´blue´´´
zero or more declarations are allowed.

The collection of these CSS rules is what's called a stylesheet.

## 2 CSS selectors: Element, Class, and ID Selectors
### 2.1 element selector
`<p> ... </p>`

### 2.2 class selector
``` css
.blue {
    color: blue;
}
```
In html part:
`<p class="blue">...</p>`

### 2.3 id selector
Can only be used once in the HTML document.
``` css
#name {
    color:blue;
}
```
`<p id="name">...</p>`

### 2.4 grouping selectors
``` css
div, .blue{
    color: blue;
}
```

## 3 Combining Selectors
### 3.1 Element with Class Selector 
``` css
//Every p that has a class = "big"
p.big{
    font-size: 20 px
}
```
An example:
``` html
<p class="big"> ... </p> // font-size: 20px
<div class="big"> ... </div>
```


### 3.2 Child Selector
``` css
//every p that is a direct child of article
article > p {  
    color: blue;
}
```
``` html
<article><p>...</p></article> // only this content has blue text.
...
<p>...</p>
<article><div><p>...</p></div></article>
``` 


### 3.3 Descendant Selector
``` css
//every p that is inside (at any level) of article
article p {  
    color: blue;
}
``` 
``` html
<article><p>...</p></article> // Blue text
...
<p>...</p> // Unaffected
<article><div><p>...</p></div></article> // Blue text
``` 


### 3.4 Not Limited to element Selector
``` css
//every p that is inside (at any level) of element with class = colored""
.colored p {  
    color: blue;
}
//every element with class = "colored" that is a direct child of article element
article > .colored{  
    color: blue;
}
``` 

### 3.5 Summary
combining selectors
* Element with class selector: selector.class
* Child(direct) selector: selector>selector
* Descendent selector: selector selector

## 4 Pseudo-Class Selector
`:link`
`:visited`
`:hover`
`:active`
`:nth-child`

Styling links is not exactly as straight forward as styling a regular element, and that's because links have states. And these states can be expressed using our pseudo-classes. 
An example:
``` css
header li {
    list-style: none
}
// visited means that HTML allows that after you click a particular link that a different style can be applied to that link than an unclicked link
// In our case, however, we don't want to differentiate between the two, so we'll style them both together.
a:link, a:visited {  // <a> tag defines a hyperlink, which is used to link from one page to another.
    text-decoration: none;
    background-color: green;
    border: 1px solid blue;
    display: block;  // <a> tag is an inline element. Here we change it to a block-level element.
    width: 200px;
    text-align: center;
    margin-bottom: 1px;
}
// An active is that state when the user actually clicks on the element but hasn't yet released his click. 
a:hover, a:active {
    background-color: red;
    color: purple;
}
// the nth child pseudo-selector allows you to target a particular element within a list.
header li:nth-child(3) {
    font-size: 24px;
}
// Set every odd member has a gray backgroud.
section div:nth-child(odd) {
    background-color: gray
}
// When the cursor hovers on the 4th member, the 4th member change the color to green.
section div:nth-child(4):hover {
    background-color: green;
    cursor: pointer;
}
```

## 5 Style placement
### 5.1 Head style `<style>...</style>`
Head styles are usually there override external ones.
### 5.2 Place style inline
Great for quick testing.
`<p style="text-align: center;">...</p> // not recommended` 
### 5.3 External CSS stylesheet
Mostly-used one in real sites.
`<link rel="stylesheet" href="style.css" `

## 6 Conflict resolution
### 6.1 Origin Precedence 
* when in conflict
Simple rule: last declaration wins
It is based on the principal that HTML is processed sequentially top to bottom.
* when no conflict
Sample rule: declarations merge
``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Cascade of CSS</title>
<link rel="stylesheet" href="external.css"> 
<style>

p {
  color: maroon;
}

</style>
</head>
<body>
<h1>Origin Example</h1>
<p>The rule is simple: last declaration wins.</p> // color: maroon
<p style="color: black;">If there is no conflict, declarations merge into one rule.</p> // color: black
</body>
</html>
```
In external css stylesheet:
``` css
p {
  font-size: 130%;
  background-color: gray;
  color: white;
}
```

### 6.2 Inheritance
If you specify some CSS property on some element, all the children and grandchildren and so on and so on of that element will also inherit that property without you having to specify the property for each and every element.

### 6.3 Specificity
Most specific selector combination wines, which can be evaluated by score:

|      1     |     1    |                1               |      1     |
| ---------- |:--------:|:------------------------------:| ----------:|
| style="..."|    id    | class, pseudo-class, attribute |# of element||

For example, 
`div p {color: green;}` score = 0002
`div #myparag {color: blue;}` score = 0101
`div.big p {color: green;}` score = 0012

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Inheritance in CSS</title>
<style>
header.navigation p { // score = 0012
  color: blue;
}
p.blurb { // score = 0011 
  color: red;
}
p {
  color: green !important;  // !important will override over specificity.
}
</style>
</head>
<body>
<header class="navigation">
  <p class="blurb">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vero soluta enim aut! Nihil nam obcaecati, fugiat sint sit libero voluptate eos incidunt odio neque cum, dignissimos aperiam, magnam nisi debitis.</p>
</header>
</body>
</html>
```

## 7 Styling Text
``` css
.style {
    font-family: Arial, Helvetica, sans-serif;
    color: #0000ff; // first '00': red; middle '00': green: last '00': blue
    font-style: italic;
    font-weight: bold;
    font-size: 24px;
    text-transform: capitalize;
    text-align: center;
    
}

body {
    font-size: 120%; // 120 % by default
}
```
``` html
body {
    font-size: 120%; // default font = 16px; current font = 19px;
}
<div style="font-size: 2em;"> 2em text // font size is two times the currect font - 38px
<div style="font-size: 2em;"> 4em text // font size = 76px
<div style="font-size: .5em;> 2em again! </div> // font size = 76px
</div> 
</div> 
```

## 8 The Box Model
### 8.1 box-sizing 
The box composes of margin, border, and padding.
`box-sizing: border-box;` The width refers to the whole box, which is hihgly recommended.
or `box-sizing: content-box;` The width refers to the content only, the default setting.
However, it should be noted that the `box-sizing` property does not inherit. To solve the problem, we can use `*` selector, which can apply the CSS style inside to all the elements.
``` css
* {
    box-sizing:border-box;
}
``` 

### 8.2 Cumulative Margins
* Horizontal margins are cumulative.
* Vertical magins from two elements will collapse, and larger margin wins.

### 8.3 Content overflow
`overflow: auto`
`overflow: scroll`
`overflow: hidden`
`overflow: invisible`

## 9 Background properties
``` html
<body>
<h1>The background property</h1>
<div id="bg">Wolala</div>
</body>
```
``` css
#bg {
    width: 500px;
    height: 500px;
    background-color: blue;
    background-image: url('cat.png') // Use an image as a background.
    background-repeat: no-repeat // repeat images or not.
    background-position: top right // set image position
    // or background: url('cat.png') no-repeat right center blue
}
```

## 10 Position Elements 
### 10.1 by Floating
``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Two Column Design</title>
<style>

* {
  box-sizing: border-box;
}

div {
  /*background-color: #00FFFF;*/
}
p {
  width: 50%;
  /*border: 1px solid black;*/
  float: left;  // float to the left of the last element.
  padding: 10px;
}

#p1 {
  /*background-color: #A52A2A;*/
}
#p2 {
  /*background-color: #DEB887;*/
}

section {
  clear: left;
}

</style>
</head>
<body>
<h1>Two Column Design</h1>

<div>
  <p id="p1">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quia distinctio aliquid cupiditate perferendis fuga, sit quasi alias vero sunt non, ratione earum dolores nihil! Consequuntur pariatur totam incidunt soluta expedita.</p>
  <p id="p2">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dicta beatae voluptatibus veniam placeat iure unde assumenda porro neque voluptate esse sit magnam facilis labore odit, provident a ea! Nulla, minima.Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eius nemo vitae, cupiditate odio magnam reprehenderit esse eum reiciendis repellendus incidunt sequi! Autem, laudantium, accusamus. Doloribus tempora alias minima laborum, provident!</p>
  <section>This is regular content continuing after the the paragraph boxes.</section>
</div>


</body>
</html>
```

### 10.2 Relative and Absolute Element Positioning
* Static positioning
Normal document flow. 
Default for all, except html.

* Relative Positioning
Element is positioned relative to its position in normal document flow.
Positioning CSS(offset) properties are: top, bottom, left, right.
Html positioning is defaulted by relative

* Absolute Positioning
All offsets(top, bottom, left, right) are relative to the position of the nearst ancestor which has positioning set on it, other than static.

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Positioning Elements</title>
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
h1 {
  margin-bottom: 15px;
}

div#container {
  background-color: #00FFFF;
  position: relative;
  top: 60px; // equivalent to 'from top'
}
p {
  width: 50px;
  height: 50px;
  border: 1px solid black;
  margin-bottom: 15px;
}
#p1 {
  background-color: #A52A2A;
  position: relative;
  top: 65px;
  left: 65px;
}
#p2 {
  background-color: #DEB887;
}
#p3 {
  background-color: #5F9EA0;
  position: absolute; // the absolute positioning needs a relative or an absolute parent or an ancestor.
  top: 0;
  left: 0;
}
#p4 {
  background-color: #FF7F50;
}

</style>
</head>
<body>
<h1>Positioning Elements</h1>

<div id="container">
  <p id="p1"></p>
  <p id="p2"></p>
  <p id="p3"></p>
  <p id="p4"></p>
</div>

</body>
</html>

```

## 11 Media Query Syntax
``` css
@media (max-width: 767px){ // media feature (resolves to true or false)
   p {
     color: blue;
   }
``` 
### Media Query Common Features
`@media(max-width: 800px) {...}`

`@media(max-width: 800px) {...}`

`@media(orientation: portrait){...}`

`@media screen{...}`

`@media print{...}`

### Media Query Common Logical Operators
* Devices with width within a range
`@media(min-width: 768px) and (max-width: 991px){...}`

* Comma is equivalent to OR
`@media(max-width: 768px), (min-width: 991px){...}`

### Media Query Common Approach
``` css
p {color: blue;} // base styles
@media(min-witdh: 1200px)
@media(min-width:992px) and (max-width:1199px) 
// Be sure that two sizes are not overlapped.
```

### An example for how to use media queries
``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Media Queries</title>
<style>

/********** Base styles **********/
h1 {
  margin-bottom: 15px;
}

p {
  border: 1px solid black;
  margin-bottom: 15px;
}
#p1 {
  background-color: #A52A2A;
  width: 300px;
  height: 300px;
}
#p2 {
  background-color: #DEB887;
  width: 50px;
  height: 50px;
}

/********** Large devices only **********/
@media (min-width: 1200px){
    #p1 {
        width: 80%; 
    // p1 at width 1200 pixels or wider will take 80% of our screen
    // when it is below 1200px, the p1 will go back to the original size.
    }
    #p2 {
        width: 150px;
        height: 150px;
    }
}

/********** Medium devices only **********/
@media (min-width: 992px) and (max-width: 1199px){
    #p1{
        width: 50%;
    }
    #p2 {
        width: 100px;
        height: 100px;
    }
}


</style>
</head>
<body>
<h1>Media Queries</h1>

<p id="p1"></p>
<p id="p2"></p>

</body>
</html>
```

### Sumary
* Basic syntax of a media query
** @media(media feature)
** @media(media feature) logical operator (media feature)
* Remember not to overlap breakpoints
* Usually, you provide base styling. Then change or add to them in each media query.
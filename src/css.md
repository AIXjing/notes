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
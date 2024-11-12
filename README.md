# Lektion-11-12

# Repetition of HTML & CSS and Intro DOM Manipulation

## HTML Repetition

HTML Stands for Hypertext Markup Language.
```html
<!-- HTML SYNTAX -->
<div id="attribute" class="attribute"> Here is the content of the html element, could be text content or child elements. </div>

<div class="container">
    <div class="wrapper">
        <p>Like this</p>
    </div>
</div>
```

- `id & class` are very common attributes that can be applied on every HTML element out there. But there are special attributes that are avaliable on certain HTML elements. Like `src` on `<image>` tag. Attributes adds functionality to HTML elements.

### Semantics

Semantics is the art of using the correct html element in the correct situation. Such as using `<main>`, `<nav>`, `<section>`, `<article>`. Using semantic elements helps your website when it comes to search engine optimization and accesability.

## CSS Repetition

CSS Stands for Cascading Style-Sheets
```css
/* SYNTAX CSS */
/*Selector*/
h1 { /*Declaration*/
   /*Property: Value;*/
    color: black;  /* STYLES ALL H1 */
    font-size: 12px;
}

.container {
    width: 100%  /* STYLES ALL CLASSES="CONTAINER" */
    background-color: #2391f1;
}
```
- Selector: The target element we want to style
- Declaration: A collection of all the styles are applied to the target element.
- Property-value: A specific property that styles. It is always paired up with value. 

### Box model

- `Content`: The content inside the html tags can be just be plain text but can be other elements aswell. If there are elements within another element, they are called child elements.

- `Padding`: The transparent area between the border and the content. We can change this area to depending on our needs in form of layout.

- `Border`: Marks the end of the box. Border, padding and content makes up the html element itself. The border is transparent per default but can be styled like _1px solid black;_

- `Margin`: Defines the transparent area outside the box. It can be used to push other content away from the box itself.

When to use padding, border or margin? It all depends on your use case.
`Padding` affects less other boxes than margin. Good to keep in mind.

### CSS Specificity

Specificity is a tool that the browser uses in order to decide which styling to apply to any given element.

Take this example

```css
div {
    background-color: yellow;
    margin-bottom: 1rem;
    padding: 0.5rem;
}

div {
    background-color: mediumaquamarine;
}
```

The first tool it uses is `the order of definition` Since `mediumaquamarine` is defined later in the file. It overrides the first `background-color`. CSS document is read from up to down.

Here is another example:
```css
.box1 {
    background-color: fuchsia;
}

div {
    background-color: yellow;
    margin-bottom: 1rem;
    padding: 0.5rem;
}

div {
    background-color: mediumaquamarine;
}
```
In this case it will use its order tool. Here it will go after Specificity score. 
- Classes has 10 points out of the score system `0,0,0` which will look like `0,1,0` 
- Styling elements as `div {}` is only `0,0,1`
- ID is `1,0,0`
- Using a combination of these are also possible like:
```css
img .mainimg{
    width: 50%;
}
```

- This is specifying an img that will have the class `.mainimg` which will give points `0,1,1` together.

- Lastly, `In-line styling` will give highest Specificity score. This is done in html not css. It gives `10,0,0`
```html
<p style="color: black"> Hello world </p>
```

## Intro DOM Manipulation

THE DOM stands for `Document Object Model` and it represents the structure and content of a HTML documents as a tree of objects, where each object corresponds to a part of the document. These parts can be elements, attributes, text content, comments and more. Everything inside the HTML document can be manipulated via this interface that is the `Document Object Model`

### Key concepts of the DOM

**1. Document**
- The top level object that represents the entire HTML document.
- Accessed using `document` in JS

**2. Node**
- The basic building block of the DOM tree
- Represents different parts of the document, such as elements, attributes and texts
- Common types of nodes include `Element`, `Text`, `Comment` and `Attribute`

**3. Elements**
- Represents an HTML element
- Examples `<div>`, `<p>`, `<span>`

**4. Attribute**
- Represents an attribute of an element.
- In `<div id="example">` the `id` is an attribute node.

**5. Text**
- Represents the text content of an `Element`

**6. Node Tree**
- Represents 

### Create Elements
```js
document.createElement(type) => HTML Element
```

This method is used to create a html element. The parameter "Type" is the kind of element we would like to create, and it must be a `string` It can be a `div`, a `span` or a `section` and so on.

The return value is the created html element which means we can directly store that html element inside a variable. From there we can do other stuff.

```js
const article1 = document.createElement("article");

console.log(article1);
```

This will create the element and store the element on the DOM object but it is not visible. It doesn't have any content whatsoever. If we inspect the element via a console log. We can clearly see that the elements is represented by an object. This object contains many properties that we can use in order to manipulate this element.

In order to see the new element inside the DOM, we need to add it there.

### Appending to DOM

This section contains a couple of methods that we can use in order to add elements to the DOM, and actually see them in the browser and in the inspector element view.

#### appendChild

This method will append a node as the last child element of the element on which this method was invoked. If we would like to append our element from above to the body, we need to invoke this method on the body element. 

HTML can´t exist without an body element so if we don´t have any other elements to use, we can always use / start on body element. How to access the body?
```js
const body = document.body;
```

Lets use this to add our created element.

```js
const article1 = document.createElement("article");

const body = document.body;

body.appendChild(article1);
```

This will append the `article1` to the DOM inside the body element.

### Update

Contains a couple of methods to edit existing HTML elements. With a focus on the content of the HTML element.

#### innerHTML

#### innerText

innerText is a property of every element that exist, whether we create it or it already exists.

Lets take our article as an example

```js
const article1 = document.createElement("article");
// Creates an empty html element.

article1.innerText = "This is an article";
// Will add the given value to the innerText property.
```

We have out article, and then we access the innerText property and just set that value to something. In this case: "This is an article"

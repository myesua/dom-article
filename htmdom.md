# Title

Creating dynamic web content using HTML DOM methods and properties

## Subtitle

HTML DOM methods and properties you should start using as a beginner.

# Table of content

- Introduction
- The web browser
- The HTML document as an object
- Javascript – A language for creating and manipulating web pages
- Why understanding the DOM is important
- DOM – the standard for accessing web documents
- Node and Element
- Methods and Properties
- Finding, creating, manipulating, styling, and removing elements using HTML DOM methods and properties
- Conclusion

> **Prerequisite**: You should have a basic understanding of HTML, CSS, and Javascript.

# Introduction

The World Wide Web was introduced to simplify the sharing of resources between two or more computers through a connected system, called the internet. These resources could be in the form of text, images, or video. They are usually retrieved and displayed in a human-readable format by a web browser. This article briefly explains the web browser, the HTML document, and how to programmatically create dynamic web content.

# The web browser

A web browser, or browser for short, is an application that retrieves data from a remote or local server and renders it in a form that a user can interact with. The process of parsing and displaying data in a human-readable format is usually done by the browser engine, which is sometimes called a rendering engine. You may check here for [different browser engines and comparisons](https://en.wikipedia.org/wiki/Comparison_of_browser_engines).

The browser receives web contents as byte packets and then converts them into a format it understands. What this means is that the bytes are first converted to characters, then to tokens. Tokens are then converted into nodes. This is simply the process through which the document tree is created. We will talk more about this later in this article.

<div style="display: flex; justify-content: center; align-items: center"><img src="https://web-dev.imgix.net/image/C47gYyWYVMMhDmtYSLOWazuyePF2/cSL20piziX7XLekCPCuD.png?auto=format&w=845" alt="Process of creating the DOM tree by the browser" width=650 /></div>
<div style="text-align:center; color: gray">How the DOM tree is being created (Image source: <a href="https://web.dev/critical-rendering-path-constructing-the-object-model/" alt="How the DOM tree is being created" class="grey" target='_blank' no-referrer>web-dev</a>)</div>
<p>&nbsp;</p>
For over two decades now, the web browser has been an important tool for retrieving web pages from the internet. We use it for quite many things including shopping, chatting with friends, getting information about the latest trend, sending and retrieving emails, searching for jobs, and so on. For this reason, makers of browsers are always working hard to optimize rendering and security.
<p>&nbsp;</p>

# The HTML Document as an object

Recall that for the browser to render web pages, it has to process them into a form it understands. During this process, the browser converts the pieces of the web content into nodes. While doing this, the document node or object is created first, which represents the whole HTML (HyperText Markup Language) document. Now, your browser hence understands that document to be an object containing several objects rather than some volume of characters. The image below shows the document object inside the browser's window.

<div style="display: flex; justify-content: center; align-items: center"><img src="https://miro.medium.com/v2/resize:fit:720/1*9oWl_UOcgqyUHa5KRo01Zg.gif" alt="The global window object" width=700 /></div>
<div style="text-align:center; color: gray">The global window object (Image source: <a href="https://medium.com/@reettikgoswami97/document-object-model-dom-c19d66abd235" alt="The global window object" class="grey" target='_blank' no-referrer>medium</a>)</div>
<p>&nbsp;</p>
If this so far is not yet clear to you, please take a breath and read again to this point as it lays the foundation upon which this article is built. You may also use the external links for more explanation.
p>&nbsp;</p>

# Javascript - a language for creating and manipulating web pages

Javascript is simply a scripting language for creating interactive and dynamic web content. For your script to communicate with the browser and web document, it needs an interface or a standard API called the Document Object Model (DOM). As you have learned above, the browser models the HTML or XML document into an object during parsing which then provides you with an interface through which your script can manipulate the web document.

The good news is that Javascript has evolved over the years, it is now used not only for client code but for the server as well.

# Why understanding the DOM is important?

- It is the standard way by which the browser represents an HTML or XML document for fast rendering of the web page.
- It allows you to dynamically style, interact, and manipulate web pages through a script. You can hide a navigation element or dropdown and only show it when a user clicks a particular button. That reduces the browser's load time as it dynamically adds an element when it is needed.
- The DOM transforms a web document into a central object with access to methods and properties.

# DOM - the standard for accessing web documents

A web document could be in HTML or XML format. The DOM is a structured representation of the web document in the browser memory after parsing. It is a tree representing the document object.

[The World Wide Web Consortium (W3C)](https://www.w3.org/) is an organization that handles the standardization of the DOM. It separates the DOM standard into three (3) parts, namely:

- Core DOM - This defines the model for all document types
- HTML DOM - The model for HTML documents
- XML DOM - This standard defines the model for XML documents

The primary focus of this article is the HTML DOM.

# Node and Element

The term "Node" is commonly used as a generic name for any object in the DOM tree. A node could be an element, attribute, text, or comment - [MDN - nodeType](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType). An element is a node with a specified HTML tag such as `<head>`, `<table>`, `<p>`, etc.

# Methods and Properties

Each element in the DOM represents specific data in the web document and responds to some sort of instructions. For you to perform actions such as adding or deleting an element, or even adding an event, you need some sort of command the element responds to.

The HTML DOM provides you with various methods and properties that you can use to manipulate elements. When it comes to working with elements, there are specific actions you can perform using certain methods. On the other hand, properties are values that you can easily obtain or modify as needed. Knowing the distinction between methods and properties is crucial for effectively managing and manipulating elements in your projects. We have quite many of <a href='https://www.w3schools.com/jsref/dom_obj_document.asp#:~:text=The%20Document%20Object,property%20of%20the%20window%20object.' alt='List of Document Object Properties and Methods' target='_blank' no-referrer>them</a>. However, this article explains those you will most likely be using in your scripts.

Before we go ahead, let's write a sample HTML file we will be using for this tutorial. I added the styling code too just for some nice visual output.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Sample HTML Document</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div class="container">
      <div class="parent">
        <h1>Sample HTML Document</h1>
        <div class="wrapper">
          <div class="navigation" id="navigation">
            <button class="dom btn" id="dom" data-name="nav-btn">DOM</button>
            <button class="methods btn" id="methods" data-name="nav-btn">Methods</button>
            <button class="properties btn" id="properties" data-name="nav-btn">Properties</button>
          </div>
         <!--Dynamically add text to div element-->
          <div class="content" id="content"></div>
        </div>
    </div>

    <script></script>
  </body>
</html>
```

You can use the DOM API to manipulate the rendered version of this document. We will see how to do that later in this tutorial.

Here are the styles we have applied

```css
html,
body {
	margin: 0;
	padding: 0;
	font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe
			UI, Roboto, Helvetica Neue, Arial, Noto Sans, sans-serif,
		Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
	scrollbar-width: thin;
	scrollbar-color: #f00;
}
* {
	box-sizing: border-box;
}

.container {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}
.parent {
	height: 200px;
}
.wrapper {
	margin: auto;
	width: 25rem;
	display: grid;
	gap: 2rem;
}
h1 {
	text-align: center;
}
.navigation {
	display: flex;
	gap: 10px;
}
button {
	padding: 8px 15px;
	background-color: #fff;
	border: none;
	outline: none;
	box-shadow: 1px 2px 15px 1px #e0e0e0;
	text-transform: uppercase;
	font-size: 0.92rem;
	font-weight: 500;
	cursor: pointer;
	border-radius: 3px;
	flex-basis: 100%;
}
.content {
	padding: 1px 10px;
	text-align: center;
}

/*Reduce width on devices with a maximum width of 400 pixels*/
@media screen and (max-width: 400px) {
	.wrapper {
		width: 20rem;
	}
}
```

Now, view the file on your browser, you should see something like,

<figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <img src="https://i.imgur.com/bq9mpbT.png" alt="A web page with a heading and three buttons" />
    <figcaption style="color: grey; text-align: center">Image of a web page with three navigation <span style="text-decoration: underline">buttons</span></figcaption>
</figure>

## Finding, creating, manipulating, styling, and removing elements in the document using HTML DOM methods and properties.

Let's say you wanted to retrieve a single element, you may use **`getElementById`** or **`querySelector`**. Either of these two selects an element. The element selected may have children or not. This means you can also access children elements by retrieving their parent and using the `children` or `childNodes` property.

- **getElementById**

  Finding an element in the browser DOM using this method returns the element with the specified id. If more than one element has the same id, it returns the first in the DOM tree. Also note that if the element does not exist, `getElementById` returns null.

  > Unlike the **querySelector** method which returns the generic element type, this method returns a more specific element type.

  Now, let's get the navigation and content element. **_You may add the following code inside the script tag in the html file or you create a separate file for it and link it to the html file._**

  ```js
  const navs = document.getElementById("navigation"); // get element by id
  const content = document.getElementById("content"); // get element by id
  ```

  We called the `getElementById()` method on the document object and specified the `id` of the element we wanted.
  Go ahead and [log](https://www.w3schools.com/jsref/met_console_log.asp) one of those in the console to confirm.

  ```js
  console.log(navs);
  ```

    <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
      <img src="https://i.imgur.com/Fm94ClP.png" alt="Selected node in the DOM using getElementById" />
      <figcaption style="text-align:center; color: gray">Image of selected node using <span style="text-decoration: underline">getElementById</span></figcaption>
  </figure>

  You'd want to do more than just to retrieve elements in your scripts. Now, assuming you wanted to give the first button of the navigation element a different background color, it is as simple as,

  ```js
  navs.firstElementChild.classList.add("active");
  ```

  ```css
  .active {
  	background-color: rgb(1, 29, 29) !important;
  	color: #fff !important;
  }
  ```

  The above code shows that we added a new class to the target element's class list. We also needed to write the class styling code inside our CSS file. Please take note of that. The **`add()`** allows us to add class(es) to an element specified in the script.

  > **`firstElementChild`** is a read-only property that returns the first child element of a specified element.
  >
  > The **`classList`** property returns a token list of the class attribute of an element. CSS class names or tokens of an element are usually separated by a space.
  >
  > The **`add`** method adds one or more class names to an element.

    <p style="color: grey; font-weight: bold">Output</p>
    <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
      <img src="https://i.imgur.com/7SaxCrN.png" alt="First element of a selected node styled differently" />
      <figcaption style="text-align:center; color: gray">Image of selected element with a different style on its first child.<br /> <span style="text-decoration: underline">getElementById</span>, <span style="text-decoration: underline">firstElementChild</span>.</figcaption>
    </figure>
  <hr />

- **querySelector**

  This method like **getElementById** returns the first element in the document with a specified CSS selector(s). The selector could be an `id`, `class name`, `ids`, `class names`, an `attribute`, a `dataset selector`, or even a `tag name`. Assuming you wanted to select the navigation element by its class name, using querySelector you just need to add a dot (`.`) before the class name. If you wanted to select by id, you add the hash symbol (`#`) instead. Like so,

  ```js
  const navs = document.querySelector(".navigation"); // Select by class name
  const content = document.querySelector("#content"); // Select by id
  const firstButton = document.querySelector(".navigation .dom"); // deep select by class name
  ```

  Now, let's create a fourth button and append it to the navigation element.

  ```js
  const fourthButton = document.createElement("button"); // create a new node
  fourthButton.innerText = "Event"; // add inner text
  navs.appendChild(fourthButton); // append child to nav element
  ```

  We have created a button element, added a text node, and append it to `navs`.

  > The **`createElement`** method creates an element node in the browser memory according to a specified tag name.
  >
  > The **`innerText`** property returns the text content of the element and all its children, without CSS hidden text spacing and tags, except `<script>` and `<style>` elements. <a href='https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/innerText'>Read more</a>
  >
  > The **`appendChild`** method add new elements to the end of the list of children. It only accepts a node type.

  <p style="color: grey; font-weight: bold">Output</p>
    <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
      <img src="https://i.imgur.com/E3tCPac.png?1" alt="Append a fourth button element to a selected node" />
      <figcaption style="text-align:center; color: gray">Image of selected element with a newly-added child element.<br /> <span style="text-decoration: underline">querySelector</span>, <span style="text-decoration: underline">createElement</span>, <span style="text-decoration: underline">appendChild</span>.</figcaption>
  </figure>
  <hr />

- **querySelectorAll**

  The **`querySelectorAll`** method returns a list of nodes matching the specified selector. These nodes could be text nodes, element nodes, and attribute nodes. When you query a list of elements using **`querySelectorAll`**, the returned list can only be accessed by their index number.

  Let's select all button elements with a data attribute of `name=nav-btn`. Learn more about [data attribute](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes). After that, we will set an active class on the button that is currently clicked by simply looping through all button elements and determining if the button is the target element clicked.

  ```js
  const buttons = document.querySelectorAll("button[data-name=nav-btn]"); // Retrieve all button elements with a data name `nav-btn`
  console.log(buttons);
  ```

  <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <img src="https://i.imgur.com/nd5ShaL.png" alt="Image of selected nodes using querySelectorAll" />
    <figcaption style="text-align:center; color: gray">Image of selected nodes using <span style="text-decoration: underline">querySelectorAll</span></figcaption>
  </figure>

  ```js
  const buttonsContainer = document.querySelector(".navigation"); // select parent element
  const buttons = document.querySelectorAll("button[data-name=nav-btn]"); // retrieve all elements matching the specified selector
  buttonsContainer.addEventListener("click", (e) => {
  	// add an event listener on the parent element
  	if (e.target.nodeName === "BUTTON") {
  		// only execute if target is a button element
  		buttons.forEach((btn) => {
  			// loop through the array of buttons in the parent element
  			// check if the current click is on the button
  			if (btn == e.target) {
  				// add the active class
  				btn.classList.add("active");
  			} else btn.classList.remove("active"); // otherwise remove the active class
  		});
  	} else return;
  });
  ```

  > The **`addEventListener`** method adds an event to a specified target through a listener. The listener receives a notification whenever an event occurs such as a click.
  >
  > **`forEach`** method iterate over each element of an array and executes the specified function. It returns an undefined value, unlike **map** method which returns a new array.
  >
  > **`remove`** is a method which removes the specified class name from <a href="https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList">DOMTokenList</a>

  <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <video controls autoplay muted>
      <source src="https://i.imgur.com/Mw6XBYv.mp4" type="video/mp4">
    </video>
    <figcaption style="text-align:center; color: gray">A short video of manipulating button elements using <span style="text-decoration: underline">querySelectorAll</span>, <span style="text-decoration: underline">addEventListener</span>.</figcaption>
  </figure>
  <hr />

- **getElementsByClassName**

  This method retrieves a collection of elements matching the specified class name(s). It returns a type of HTMLCollection, which is a list of HTML elements similar to an array but it's not, because you can't call Array methods like `push()`, `pop()`, or `join()` on it.

  ```js
  const buttons = getElementsByClassName("btn");
  console.log(buttons);
  ```

  In the image below, you will see that this method returns a list of elements (<a href="https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection">HTML Collection</a>). One advantage of using `getElementsByClassName` over `querySelectorAll` is the flexibility it offers in accessing elements. While `querySelectorAll` returns a NodeList that can only be accessed by index, `getElementsByClassName` allows you to access each element in the returned list either by index or by name. This makes it easier and more convenient to work with the specific elements you need. For instance, the marked portion in the image indicates that the faded items in the HTMLCollection are the named items, so you can access them by their name like `buttons.namedItem('dom')`.
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <img src="https://i.imgur.com/tmyloV4.png" alt="Image of selected elements using getElementsByClassName" />
    <figcaption style="text-align:center; color: gray">Image of retrieved elements using <span style="text-decoration: underline">getElementsByClassName</span></figcaption>
  </figure>

  Again, we will add a click event to each of the buttons and change the text content of the text element.

  ```js
  const buttonsContainer = document.querySelector(".navigation"); // select parent element
  const buttons = document.getElementsByClassName("btn"); // retrieve all elements matching the specified class name
  const textElement = document.getElementById("content");
  buttonContainer.addEventListener("click", (e) => {
  	// add an event listener on the parent element
  	if (e.target.nodeName === "BUTTON") {
  		// only execute if target is a button element
  		Array.from(buttons).forEach((btn) => {
  			// loop through the array of buttons in the parent element
  			// check if the current click is on the button
  			if (btn == e.target) {
  				// add the active class
  				btn.classList.add("active");
  				textElement.innerText = `This is the ${e.target.innerText} button`;
  			} else btn.classList.remove("active"); // otherwise remove the active class
  		});
  	} else return;
  });
  ```

  Both `getElementsByClassName` and `getElementsByTagName` are useful methods that return an HTML Collection of elements. It's important to note that the list they return is not actually an array, but rather an array-like or iterable object. So if you want to iterate over the list, you need to convert it into an actual array. Thankfully, `Array.from` comes to our rescue by allowing us to easily achieve this conversion.

  > The **`Array.from`** method returns an array from an array-like object or an iterable object. It is used to convert an iterable object to an array.

  <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <video controls autoplay muted>
      <source src="https://i.imgur.com/4f8JUjj.mp4" type="video/mp4">
    </video>
    <figcaption style="text-align:center; color: gray">A short video of manipulating button elements using <span style="text-decoration: underline">getElementsByClassName</span>, <span style="text-decoration: underline">addEventListener</span>.</figcaption>
  </figure>
  <hr />

- **getElementsByTagName**

  `getElementsByTagName` retrieves elements by a given tag name. It accepts only one tag name which must be a string. Similar to `getElementsByClassName`, it returns a list of elements. You can return all elements in the HTML DOM by supplying the `*` as the tag name, e.g.`getElementsByTagName('*')`.

  ```js
  const buttons = getElementsByTagName("*");
  console.log(buttons);
  ```

  <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
    <img src="https://i.imgur.com/k0rUl5i.png" alt="Image of selected elements using getElementsByTagName" />
    <figcaption style="text-align:center; color: gray">Image of retrieved elements using <span style="text-decoration: underline">getElementsByTagName</span></figcaption>
  </figure>

  Now, let's remove the last button element from the DOM.

  ```js
  function renderRemoveButtonAndExecute() {
  	const arrayOfButtons = document.getElementsByTagName("button");
  	const lastElement = arrayOfButtons.item(arrayOfButtons.length - 1);
  	const textElement = document.getElementById("content");
  	textElement.innerHTML = `<button class="remove-btn">Remove last button</button>`;
  	textElement.children[0].addEventListener("click", () =>
  		lastElement.remove()
  	);
  }
  loadRemoveButton();
  ```

  Above, we wrote a function called `renderRemoveButtonAndExecute`. It retrieves an array of navigation buttons, gets the last button from the array, and removes it when the remove button is clicked.

  > The **item** method returns an element with the specified index in an <a href="https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection">HTMLCollection</a>.
  >
  > The **innerHTML** property allows you to set or retrieve the HTML content of an element. See <a href="https://www.w3schools.com/jsref/prop_html_innerhtml.asp">here</a> for reference.

  <p style="color: grey; font-weight: bold">Output</p>
  <figure style="display: flex; flex-direction: column; justify-content: center; align-items: center;">
  <video controls autoplay muted>
    <source src="https://i.imgur.com/zKPjMZM.mp4" type="video/mp4">
  </video>
    <figcaption style="text-align:center; color: gray">A short video of removing an element from the DOM using <span style="text-decoration: underline">getElementsByTagName</span>, <span style="text-decoration: underline">remove</span>.</figcaption>
  </figure>

## Conclusion

The browser is an incredibly powerful tool equipped with a wide array of <a href="https://developer.mozilla.org/en-US/docs/Web/API">APIs</a>. From the HTML DOM to the File API, Web Audio API, Navigation API, and WebRTC, among many others, these APIs enhance the functionality and versatility of the browser. With such capabilities at your fingertips, you can create dynamic web experiences that push boundaries and meet the needs of modern users. For anyone starting out in web development, having a solid grasp on the HTML Document Object Model (DOM) is absolutely essential. It forms the foundation of web page manipulation and interaction. There are numerous methods and properties within the DOM that enable developers to efficiently work with HTML elements. Although this article only covered a handful of them, it aimed to give beginners a taste of what the DOM has to offer.

Now you've come to the end of this tutorial. I hope this article has added to your knowledge.

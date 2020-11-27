# An Introduction to HTML
*A compact introduction to using HTML.*

HyperText Markup Language (HTML) is a [markup language](https://en.wikipedia.org/wiki/Markup_language), i.e. a language which defines the structure and presentation of raw text. As such, no prior programming knowledge is required.

HTML is the standard markup language to use for creating websites and is typically layered under CSS and JavaScript, since HTML alone is only useful as the foundational building blocks of a website.

The aim of this guide is to present HTML in a compact way, as necessary to begin building a functional website. For an extremely comprehensive guide, see [the HTML Living Standard](https://html.spec.whatwg.org/multipage/) or [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML).

## Table of Contents

- [Coding Standards](#coding-standards)
  * [Indentation](#indentation)
  * [Comments](#comments)
  * [Quotes](#quotes)
  * [Names](#names)
- [Elements and Structure](#elements-and-structure)
  * [Document Set Up](#document-set-up)
  * [Elements](#elements)
  * [The Head Element](#the-head-element)
  * [The Body Element](#the-body-element)
  * [The Hierarchy Structure](#the-hierarchy-structure)
  * [Headings](#headings)
  * [Attributes](#attributes)
  * [The `id` and `class` Attributes](#the-id-and-class-attributes)
  * [The Div Element](#the-div-element)
  * [Displaying Text](#displaying-text)
  * [Styling Text](#styling-text)
  * [Empty Tags](#empty-tags)
  * [Breaking Up Text](#breaking-up-text)
  * [Lists](#lists)
  * [Media](#media)
    + [Images](#images)
    + [Videos](#videos)
    + [Audio](#audio)
  * [Links](#links)
- [Tables](#tables)
  * [Table Creation](#table-creation)
  * [Table Rows and Data](#table-rows-and-data)
  * [Table Headings](#table-headings)
  * [Spanning Rows and Columns](#spanning-rows-and-columns)
  * [Table Structure](#table-structure)
- [Forms](#forms)
  * [The Form Element](#the-form-element)
  * [The Input Element](#the-input-element)
    + [Labels](#labels)
  * [The `required` Attribute](#the-required-attribute)
    + [Text Input](#text-input)
    + [Password Input](#password-input)
    + [Number Input](#number-input)
    + [Range Input](#range-input)
    + [Checkbox Input](#checkbox-input)
    + [Radio Input](#radio-input)
  * [Dropdown Lists](#dropdown-lists)
  * [Datalists](#datalists)
  * [The Submit Button](#the-submit-button)
- [Semantic HTML](#semantic-html)
  * [The Header Element](#the-header-element)
  * [The Navigation Element](#the-navigation-element)
  * [The Main Element](#the-main-element)
  * [The Footer Element](#the-footer-element)
  * [The Article Element](#the-article-element)
  * [The Section Element](#the-section-element)
  * [The Aside Element](#the-aside-element)
  * [The Figure and Figure Caption Elements](#the-figure-and-figure-caption-elements)

## Coding Standards

All written code should follow a style guide to ensure that standards are kept consistent across any codebase and make code easier to read. Badly written code is difficult to scale, optimise, and debug. Such is the importance of high coding standards that this guide will discuss it as a separate section before any code is seen.

We follow the standards in the [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html). In particular, this section will act as a reference for language-specific best practices for indentation, comments, quotes, and names, since these can vary across different programming languages. Readability will be covered in greater detail in the [Semantic HTML](#semantic-html) section.

### Indentation

Line breaks and indentation do not affect the displayed output, but should still be used appropriately to make the code easier to read. The standard is to use two spaces for indented code.

### Comments

It can be useful to add comments to our code to help provide more context on what the code does, or to temporarily disable code without having to actually delete it. Comments begin with `<!--` and end with `-->`; can be multi-line; and do not actually display in the webpage output. There is no way to do inline comments (i.e. comments within other HTML elements).

For readability, comments should be written in complete sentences, be indented with the code which it is commenting, and come before the code which it is commenting. Placing the comment after is merciless on a confused reader. Any paragraphs should be separated by a single line, and multi-sentence comments should have two spaces after a sentence-ending period (except after the final sentence).

```HTML
<!-- This is a comment. -->
```

### Quotes

Attribute values need to be wrapped in quotation marks. These should be double quotes `" "`, rather than single quotes `' '`, but functionally either will work.

### Names

All code, and by extension names, should be in lowercase (with the exception of strings). In particular, ID and class names should be written in *kebab-case*, i.e. any word separation should be done with a hyphen `-`.

## Elements and Structure

A standard HTML document should be structured in a certain way so that it can be displayed correctly as a webpage; is properly read by [web crawlers](https://en.wikipedia.org/wiki/Web_crawler); and can be easily understood by other people reading the code.

In this section we will see how a HTML document should be structured to meet the [W3C Standards](https://www.w3.org/standards/) for HTML and behave as expected; and look at some commonly used HTML elements to add content to webpages. A full list of HTML elements can be found [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

### Document Set Up

For a browser to know that a document is a HTML document, it needs to begin with the following *document type declaration*:

```HTML
<!DOCTYPE html>
```

The rest of the HTML code needs to exist within the `<html>` tag (defined in the [Elements](#elements) section) as follows:

```HTML
<!DOCTYPE html>
<html>
  ...
</html>
```

### Elements

HTML is composed of *elements* which structure the webpage and define its content. A basic element consists of an *opening tag*, *content*, and a *closing tag*. In the following example, the opening tag, content, and closing tag are `<p>`, `Hello World!`, and `</p>`, respectively:

```HTML
<p>Hello World!</p>
```

The first character or word in the opening tag is called the *tag name*. In the above example, the tag name is `p`.

### The Head Element

The first element in the HTML element should be the *head element*, which contains the metadata for a webpage, i.e. information about the webpage which isn't directly displayed on the webpage itself.

```HTML
<head>
  <!-- Metadata goes in here. -->
</head>
```

One of the most common pieces of metadata to include in the head element is the title of the browser's tab. This can be done by using the `<title>` tag as follows:

```HTML
<head>
  <title>My First Webpage</title>
</head>
```

Examples of other commonly included pieces of metadata can be seen [here](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML).

### The Body Element

After the head element comes the *body element*. Only content within this element is actually displayed on the webpage.

```HTML
<body>
  <!-- Content to display goes in here. -->
</body>
```

Note that although content outside the body element may be displayed, it's not guaranteed to behave as expected.

### The Hierarchy Structure

If an element A contains element B, then we say that element A is the *parent* of element B, and that element B is the *child* of element A. In particular, we say that the child element is *nested* inside of the parent element.

The family tree terminology is used similarly for other element relationships. This HTML hierarchy is simple, but important, to understand if CSS is to be layered over HTML code, because child elements can inherit behaviour and styling from their parent element.

### Headings

There are six different sizes which *heading elements* come in. In descending size, these are as follows:

```HTML
<h1> </h1>
<h2> </h2>
<h3> </h3>
<h4> </h4>
<h5> </h5>
<h6> </h6>
```

Typically `<h1>` tags are used for main headings, and the smaller headings used for subheadings.

### Attributes

An element can be enriched by adding an *attribute* to the element's opening tag. Attributes consists of a *name* and a *value*. The generic syntax is as follows:

```HTML
<tag-name attribute-name="attribute-value">Content</tag-name>
```

Throughout this guide we'll see several examples of attributes and their uses, but a good list can be found [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes).

### The `id` and `class` Attributes

The `id` and `class` attributes can be added to any element. Typically this is done to add more context to the raw code for readability reasons. Additionally, the value of an `id` attribute may be called upon later by other HTML, CSS or JavaScript code; and the value of a `class` attribute may be called upon later by other CSS or JavaScript code.

The value of an `id` attribute must be unique across the entire code, whereas the value of a `class` attribute does not. In particular, the value of an `id` or `class` attribute should only contain the ASCII letters, underscores, hyphens, and periods. However, words in ID and class names should be separated by a hyphen - see the [Naming](#naming) section.

### The Div Element

It can be helpful to use a *division element*, or *div element*, to add more structure to raw HTML code. It's a generic container for grouping code and changes nothing in the displayed webpage.

```HTML
<body>
  <div>
    <h1>Some Content</h1>
    <p>Some text.</p>
  </div>

  <div>
    <h1>Some More Content</h1>
    <p>Some more text.</p>
  </div>
</body>
```

### Displaying Text

To display text, we can either use a *paragraph element*, which contains a block of plain text, or a *span element*, which typically contains short pieces of text that we wish to separate from other inline content. The following example demonstrates their use:

```HTML
<p><span>Python</span> is one of the most popular programming languages in the world and is commonly learnt as a first programming language.</p>

<p><span>Go, or Golang</span>, is a programming language designed by Google employees.</p>
```

### Styling Text

There are several HTML tags to style text. The commonly used ones are:
- `<b>` for bold text
- `<strong>` for important text (will display as bold)
- `<i>` for italic text
- `<em>` for emphasized text (will display as italics)

Note that although the `<b>` and `<strong>` tags will visually display the same on a webpage, it is preferable to use `<strong>` since screen readers will verbally read this in a certain way to indicate importance. Similarly, it is preferable to use `<em>` over `<i>`.

### Empty Tags

An *empty tag* or a *self-closing tag* is a tag which has an opening tag, but no closing tag. The final `/` in the opening tag is optional. Both of the following syntaxes are valid for a self-closing tag:

```HTML
<tag>
```

```HTML
<tag/>
```

### Breaking Up Text

Since line breaks and indentation in the HTML code don't affect the displayed output, if we want to insert a line break then we need to use the `<br>` empty tag. The following example demonstrates its use:

```HTML
<p>This is the first line.<br>
This is the second line.</p>
```

If we want to insert a thematic break, then we need to use the `<hr>` empty tag, which inserts a horizontal rule. The following example demonstrates its use:

```HTML
<p>This is a paragraph about something.</p>

<hr>

<p>This is a paragraph about something completely different.</p>
```

### Lists

The two most commonly used types of lists are *unordered lists* and *ordered lists*. Typically items in unordered lists are separated by bullet points, and items in ordered lists by numbers.

Unordered lists and ordered lists are created by using the `<ul>` and `<ol>` tags, respectively. Items in those lists use the `<li>` tag. The following example demonstrates their use:

```HTML
<ul>
  <li>This is an item.</li>
  <li>This is another item.</li>
  <li>This is yet another item.</li>
</ul>

<ol>
  <li>This is the first item.</li>
  <li>This is the second item.</li>
  <li>This is the third item.</li>
</ol>
```

Note that the `<ul>` and `<ol>` elements should not hold raw text outside of an `<li>` element - there is no guarantee that they will be displayed correctly.

### Media

Media can be grouped into three main types: images, videos, and audio. It is possible to use the `<embed>` self-closing tag to include any type of media in a webpage. This should be used with the `src` attribute to include the URL of the media.

```HTML
<embed src="some-url"/>
```

However, using this tag should be avoided since it is a deprecated tag, but will often be seen in legacy code. Instead, the `<img>`, `<video>` and `<audio>` tags should be used instead, and these will be detailed in the upcoming sections.

#### Images

The `<img>` tag is a self-closing tag which allows images to be added. The `src` attribute must be included in the tag, where its value is the URL of the image.

```HTML
<img src="some-url"/>
```

For screen readers to correctly describe images, we should also include alternative text via the `alt` attribute, where the value is a description of the image. Additionally, alternative text is useful in the case that the image fails to load; and to aid web crawlers for the purpose of improving a website's [SEO](https://en.wikipedia.org/wiki/Search_engine_optimization) ranking.

```HTML
<img src="some-url" alt="A nice image."/>
```

#### Videos

To add video we can use the `<video>` tag. Similar to the `<img>` tag, we need to use the `src` attribute to include the URL of the video. However, unlike the `<img>` tag, this tag is not self-closing.

Useful attributes to include are the `controls` attribute, to include basic video controls, and the `width` and `height` attributes, to determine the video's display size. It is also typical to include content in the video element, which will only be displayed if the browser is unable to load the video. We should also include the `type` attribute to help the browser identify the video type more easily, and if it can support it.

```HTML
<video src="some-url" type="video/mp4" width="320" height="240" controls>
Your browser does not support this video. <a href="another-url">Here</a> is another link to the video instead.
</video>
```

Not all browsers will support the same video formats, so we can use the source element to provide multiple sources for the browser to choose from.

```HTML
<video width="320" height="240" controls>
  <source src="some-url" type="video/mp4"/>
  <source src="another-url" type="video/webm"/>
Your browser does not support this video. <a href="different-url">Here</a> is another link to the video instead.
</video>
```

Other useful attributes are `autoplay`, to add autoplay functionality, and `loop`, to repeat the video once it has reached the end.

#### Audio

To add audio we can use the `<audio>` tag. This is similar to the `<video>` tag in that we need to include the `src` attribute, to include the URL of the audio, and that it's not self-closing.

A useful attribute to include is the `controls` attribute, to include basic audio controls. We should also include the `type` attribute to help the browser identify the audio type more easily, and if it can support it.

```HTML
<audio src="some-url" type="audio/mpeg" controls>
Your browser does not support this audio. <a href="different-url">Here</a> is another link to the audio instead.
</audio>
```

Not all browsers will support the same file types and audio codecs, so we can use the source element to provide multiple sources for the browser to choose from.

```HTML
<audio controls>
  <source src="some-url" type="audio/mpeg"/>
  <source src="another-url" type="audio/ogg"/>
Your browser does not support this audio. <a href="different-url">Here</a> is another link to the audio instead.
</audio>
```

Other useful attributes are `autoplay`, to add autoplay functionality, and `loop`, to repeat the audio once it has reached the end.

### Links

To add links we can use the *anchor element*, with the text of the link as the content, and the URL of the link as the value of the `href` attribute. Note that the content of the anchor element need not be text - it could also be an image, a video, or audio.

```HTML
<a href="some-url">This is the text of the link</a>
```

If we want the link to open in a new tab, then we can use the `target` attribute with a value of `_blank`. Adding to the above example:

```HTML
<a href="some-url" target="_blank">This is the text of the link</a>
```

If we wish to link to a part of the webpage itself, then we can use the `id` attribute at our target location. The following example demonstrates this (notice the `#` used in the value of the `href` attribute):

```HTML
<p id="top">This is the top of the page.</p>

<p>
A link to the <a href="#top">top</a> and a link to the <a href="#bottom">bottom</a>.
</p>

<p id="bottom">This is the bottom of the page.</p>
```

## Tables

This section will be an introduction to creating tables in HTML to present data on a webpage.

### Table Creation

To instantiate a table we need to use the `<table>` tag, which will contain all of the information associated to the table itself, including how the data is structured and any related formatting.

```HTML
<table>
  <!-- Table content goes in here. -->
</table>
```

### Table Rows and Data

To add rows to an instantiated table, we need to use the `<tr>` tag.

```HTML
<table>
  <tr>
  </tr>
</table>
```

Once rows have been added, data can be inserted into the rows using the `<td>` tag. The following example creates a table with one row and two columns:

```HTML
<table>
  <tr>
    <td>Some text</td>
    <td>1234</td>
  </tr>
</table>
```

### Table Headings

The row or column headings of a table can be created using the `<th>` tag. There is no visual difference between the `<th>` tag and the `<td>` tag, but for code readability and screen readers, it's preferable to use the `<th>` tag for headings. Furthermore, we can differentiate between row and column headings by using the `scope` attribute, where the value is either `row` or `col`. The following example demonstrates this:

```HTML
<table>
  <tr>
    <th></th>
    <th scope="col">Favourite Vegetable</th>
    <th scope="col">Favourite Fruit</th>
  </tr>

  <tr>
    <th scope="row">Alice</th>
    <td>Carrot</td>
    <td>Orange</td>
  </tr>

  <tr>
    <th scope="row">Bob</th>
    <td>Broccoli</td>
    <td>Banana</td>
  </tr>
</table>
```

### Spanning Rows and Columns

Table data can be made to span multiple rows by using the `rowspan` attribute in the `<td>` element, with its value being the number of rows to span. Similarly, spanning multiple columns can be done by using the `colspan` attribute. Of course, table data can span multiple rows and columns at the same time.

In the following example, modified from last section's example, Alice and Bob's both have their favourite vegetable as carrot:

```HTML
<table>
  <tr>
    <th></th>
    <th scope="col">Favourite Vegetable</th>
    <th scope="col">Favourite Fruit</th>
  </tr>

  <tr>
    <th scope="row">Alice</th>
    <td rowspan="2">Carrot</td>
    <td>Orange</td>
  </tr>

  <tr>
    <th scope="row">Bob</th>
    <td>Banana</td>
  </tr>
</table>
```

### Table Structure

The code for a table can become very long. To improve code readability, we can use the `<thead>`, `<tbody>` and `<tfooter>` tags to structure the table's code in a sensible way. These tags are typically used in the following ways:
- The table head contains the column headings.
- The table body contains the main data of the table.
- The table footer contains anything that belongs at the bottom of a table, such as summative results.

The following example, which modifies the previous section's example by adding a footer, demonstrates this:

```HTML
<table>
  <thead>
    <tr>
      <th></th>
      <th scope="col">Favourite Vegetable</th>
      <th scope="col">Favourite Fruit</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">Alice</th>
      <td rowspan="2">Carrot</td>
      <td>Orange</td>
    </tr>

    <tr>
      <th scope="row">Bob</th>
      <td>Banana</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <th scope="row">Unique Total</th>
      <td>1</td>
      <td>2</td>
    </tr>
  </tfoot>
</table>
```

## Forms

There are a variety of ways to collect, restrict, and validate user input. One such way is through the use of HTML forms - in this section we present an introduction to creating these.

### The Form Element

All forms need to exist as the content of the *form element*.

```HTML
<form>
  <!-- Form content goes in here. -->
<form>
```

There are two useful attributes that can be added:
- The `action` attribute, whose value is the location of where the information collected by the form element goes.
- The `method` attribute, whose value is the [HTTP request] to be made. For the purposes of this section, this should be POST.

```HTML
<form action="URL" method="POST">
  <!-- Form content goes in here. -->
<form>
```

Throughout this section we will omit adding attributes to the form element to improve code readability, but in practice the `action` and `method` attribute are needed for the form's input to actually be sent somewhere.

### The Input Element

In this section we'll look at six different inputs. All of these input types will be specified via attributes to the *input element*, which is also a self-closing tag. The `<input tag>` should have a `type` attribute, which will be discussed in further detail later, and a `name` attribute, under which the user input is stored and sent when the form is submitted.

```HTML
<form>
  <input type="some-type" name="some-name"/>
</form>
```

Most input types are also compatible with the `value` attribute, which allows for a default value to be pre-filled when the form is rendered on the webpage.

```HTML
<form>
  <input type="some-type" name="some-name" value="some-value"/>
</form>
```

#### Labels

We can attach a *label element* to an input element to inform the user on what they should input. The label element should have a `for` attribute, whose value is equal to the `id` of the input element to which it is a label for. The label element's content will be displayed as the label's text. Building on the previous example:

```HTML
<form>
  <label for="an-id">Enter some data</label>
  <input id="an-id" type="some-type" name="some-name"/>
</form>
```

### The `required` Attribute

We can force certain inputs in a form to be mandatory by adding the `required` attribute to the corresponding input elements.

```HTML
<form>
  <label for="an-id">Enter some data</label>
  <input id="an-id" type="some-type" name="some-name" required/>
</form>
```

#### Text Input

To specify that an input element should accept text, we can set the value of its `type` attribute to `text`.

```HTML
<form>
  <label for="text-example">Enter some text:</label>
  <input id="text-example" type="text" name="text-field"/>
</form>
```

Alternatively, it is possible to create a larger text field by using the textarea element, which allows users to click and drag on the bottom right corner to expand it. It is also typical to include the `rows` and `cols` attributes, whose values determine how many rows and columns, respectively, that the textarea is initially rendered to the webpage with. If the textarea element includes any contents, then it will appear as pre-filled default text in the text field. The following example demonstrates all of this:

```HTML
<form>
  <label for="textarea-example">Enter a lot of text:</label>
  <textarea id="textarea-example" name="textarea-field" rows="5" cols="20">Some default text.</textarea>
</form>
```

If we wish to restrict the character count of the allowed input, then we can add either, or both, the `minlength` and `maxlength` attributes to the input element, whose values determine the minimum length and maximum length, respectively, of the permissible input. Modifying the first example above:

```HTML
<form>
  <label for="text-example">Enter some text between 10 and 200 characters:</label>
  <input id="text-example" type="text" name="text-field" minlength="10" maxlength="200"/>
</form>
```

We can also restrict the permissible character set by adding the `pattern` attribute to the input element, whose value should be a [regular expression](https://github.com/cnguyen-uk/An-Introduction-to-Regex). Modifying the first example above to only allow letters and numbers:

```HTML
<form>
  <label for="text-example">Enter some text:</label>
  <input id="text-example" type="text" name="text-field" pattern="[a-zA-Z0-9]+"/>
</form>
```

#### Password Input

If a user is to input their password, then the characters of the password should be censored on the webpage. We can specify this behaviour in an input element by setting the value of its `type` attribute to `password`.

```HTML
<form>
  <label for="password-example">Password</label>
  <input id="password-example" type="password" name="password-field"/>
</form>
```

All of the character restriction attributes in the [Text Input](#text-input) section can also be applied here, i.e. `minlength`, `maxlength`, and `pattern`.

#### Number Input

To specify that an input element should only accept numbers (and a few special characters, such as `+`, `-` and `.`), we can set the value of its `type` attribute to `number`. We can also add the `step` attribute, which adds increment and decrement arrows inside the input field, and whose value determines the size of the increment and decrement steps.

```HTML
<form>
  <label for="number-example">Shoe size</label>
  <input id="number-example" type="number" name="number-field" step="0.5"/>
</form>
```

If we wish to restrict the range of the allowed input, then we can add either, or both, the `min` and `max` attributes to the input element, whose values determine the minimum and maximum, respectively, of the permissible input. Following on from the above example:

```HTML
<form>
  <label for="number-example">Shoe size</label>
  <input id="number-example" type="number" name="number-field" step="0.5" min="0" max="12"/>
</form>
```

#### Range Input

To obtain user input via a slider, we can use an input element with a `type` attribute whose value is `range`. The `min` and `max` attributes should also be added, whose values determine the minimum and maximum, respectively, of the slider. Optionally, the `step` attribute can be added, whose value determines the size of the steps that the slider can make.

```HTML
<form>
  <label for="range-example">Volume Control</label>
  <input id="range-example" type="range" name="slider" min="1" max="100" step="1"/>
</form>
```

#### Checkbox Input

To allow for multiple options, from a choice of many, to be selected by users, we can use checkboxes. To do this, we can use input elements with a `type` attribute whose values are `checkbox`. The general syntax is as follows (note the same value of the `name` attribute across all input elements to group them together):

```HTML
<form>
  <p>Tick some boxes:</p>

  <label for="checkbox1">A checkbox</label>
  <input id="checkbox1" type="checkbox" name="choices" value="a checkbox"/>
  <br/>
  <label for="checkbox2">Another checkbox</label>
  <input id="checkbox2" type="checkbox" name="choices" value="another checkbox"/>
  <br/>
  <label for="checkbox3">One more checkbox</label>
  <input id="checkbox3" type="checkbox" name="choices" value="one more checkbox"/>
</form>
```

#### Radio Input

To allow for a single option, from a choice of many, to be selected by users, we can use radio buttons. To do this, we can use input elements with a `type` attribute whose values are `radio`. The general syntax is as follows (similar to checkboxes, we use the same value of the `name` attribute across all input elements to group them together):

```HTML
<form>
  <p>Select one button:</p>

  <label for="button1">A button</label>
  <input id="button1" type="radio" name="selection" value="a button"/>
  <br/>
  <label for="button2">Another button</label>
  <input id="button2" type="radio" name="selection" value="another button"/>
  <br/>
  <label for="button3">One more button</label>
  <input id="button3" type="radio" name="selection" value="one more button"/>
</form>
```

### Dropdown Lists

Dropdown lists are a useful alternative to checkboxes and radio buttons, especially when there are many options to choose from. To do this, we can use the select element, whose contents will consist of option elements as follows:

```HTML
<form>
  <label for="dropdown-list">A dropdown list:</label>
  <select id="dropdown-list" name="dropdown">
    <option value="a choice">A choice</option>
    <option value="another choice">Another choice</option>
    <option value="one more choice">One more choice</option>
  </select>
</form>
```

By default, only one of the options in the dropdown list can be selected. To allow for multiple options to be selected, add the `multiple` attribute to the select element.

### Datalists

Datalists are similar to dropdown lists, but also allow users to type an input - if the option exists in the list, then they can select it, otherwise, they can still use what they typed. This is a useful alternative to dropdown lists, especially when scrolling through all of the dropdown options is too tedious.

To create a datalist, we need to use the input element with the `list` attribute, together with the datalist element, whose contents will consist of `option` elements. In the following general syntax, note that the value of the `list` attribute in the input element is the same as the value of the `id` attribute in the datalist element:

```HTML
<form>
  <label for="datalist">A datalist:</label>
  <input id="datalist-example" type="text" name="example" list="some-choices"/>
  <datalist id="some-choices">
    <option value="A choice"></option>
    <option value="Another choice"></option>
    <option value="One more choice"></option>
  </datalist>
</form>
```

### The Submit Button

All forms should end with a submit button for users to actually send off their inputs. This is done by including the input element with the value of the `type` attribute set to `submit` at the bottom of the form. Optionally, if we want to change the "submit" text on the submit button to something else, then we can include the `value` attribute, whose value will replace the default "submit" text on the submit button.

```HTML
<form>
  <!-- The rest of the form's HTML code goes here -->
  <input type="submit" value="Finished"/>
</form>
```

## Semantic HTML

*Semantic HTML* is about using HTML to provide information on the content of HTML elements, rather than just to define the displayed output. It's best practice to use semantic HTML over non-semantic HTML, where possible, to improve code readability. For example, the div, span, and embed elements provide no context on their contents, and should be replaced by appropriate semantic HTML if available. In this section we present an introduction to commonly used semantic HTML elements, but it is important to also be aware of non-semantic HTML elements for the sake of understanding legacy HTML code.

Other than code readability, there are a couple of other reasons to use semantic HTML. The first reason is accessibility - screen readers and browsers on mobile devices are able to parse semantic HTML better than non-semantic HTML. The second reason is for SEO - web crawlers and search engines are able to identify the most important content of a website better when it's written using semantic HTML.

### The Header Element

The header element is typically used to contain navigational links, or introductory content containing [heading elements](#headings). For example, the following is preferred:

```HTML
<header>
  <h1>An Introduction to HTML</h1>
</header>
```

As a comparison, the following should be avoided:

```HTML
<div id="header">
  <h1>An Introduction to HTML</h1>
</div>
```

### The Navigation Element

The navigation element is used to contain a block of navigation links, such as menus and tables of contents. It's commonly used inside the header element, but it can also be used on its own. The following example demonstrates this:

```HTML
<header>
  <nav>
    <ul>
      <li><a href="#section-1">Section 1</a></li>
      <li><a href="#section-2">Section 2</a></li>
      <li><a href="#section-3">Section 3</a></li> 
    </ul>
  </nav>
</header>
```

### The Main Element

The main element is used to contain the dominant content in a webpage. The following example uses the article element, which will be covered in [a later section](#the-article-element):

```HTML
<main>
  <header>
    <h1>An Introduction to HTML</h1>
  </header>

  <article>
    <p>HTML stands for HyperText Markup Language.</p>
  </article>
</main>
```

### The Footer Element

The footer element is typically located at the bottom of the main content of the webpage. Common information to contain include contact information; copyright information; terms of use; and reference links to the top of the webpage.

```HTML
<footer>
  <p>Email: me@example.com</p>
</footer>
```

### The Article Element

The article element contains standalone webpage content, i.e. it makes sense on its own, such as articles, blog posts, and comments.

```HTML
<article>
  <p>HTML stands for HyperText Markup Language.</p>
</article>
```

### The Section Element

The section element is used to split the content of the main element into parts which contain the same theme, such as chapters, headings, and articles about the same topic.

```HTML
<section>
  <h1>Sports</h1>
</section>

<section>
  <h2>Motorsport</h2>
  <article>
    <p>There are many disciplines in the motorsport world.</p>
  </article>
</section>

<section>
  <h2>Tennis</h2>
  <article>
    <p>The Grand Slam tournaments are held in Australia, France, the USA, and the UK.</p>
  </article>
</section>
```

### The Aside Element

The aside element contains additional information that can enhance other information, but isn't required in order to understand it. This is typically used alongside the article element and the section element. Examples include side notes, endnotes, pull quotes, and editorial comments.

Following on from the previous example:

```HTML
<section>
  <h1>Sports</h1>
</section>

<section>
  <h2>Motorsport</h2>
  <article>
    <p>There are many disciplines in the motorsport world.</p>
  </article>

  <aside>
    <p>Not all of the disciplines are as popular as each other.</p>
  </aside>
</section>

<section>
  <h2>Tennis</h2>
  <article>
    <p>The Grand Slam tournaments are held in Australia, France, the USA, and the UK.</p>
  </article>

  <aside>
    <p>Different countries have different prize funds.</p>
  </aside>
</section>
```

### The Figure and Figure Caption Elements

The figure element is used to contain any figures, such as images, illustrations, and code snippets, which are referenced in the main flow of the webpage. This is typically accompanied with the figure caption element, which is used to describe the figure and possibly to give it a label.

```HTML
<figure>
  <img src="some-url" alt="A nice image."/>
  <figcaption>Figure 1: This figure shows how nice images can be.</figcaption>
</figure>
```

Note that this is different from using the paragraph element - the figure caption element will group the caption with the figure, whereas the paragraph element may result in the caption being displaced from the figure.

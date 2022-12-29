# Code Style: HTML/CSS

## 1. General

### 1.1. General Formatting Rules

### 1.1.1. Indentation

Indent by 2 spaces at a time.

Don’t use tabs or mix tabs and spaces for indentation.

```html
<ul>
  <li>Fantastic
  <li>Great
</ul>
```

```css
.example {
  color: blue;
}
```

### 1.1.2. Capitalization

Use only lowercase.

All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), 
CSS selectors, properties, and property values (with the exception of strings).

```html
<!-- Not recommended -->
<A HREF="/">Home</A>
```

```html
<!-- Recommended -->
<img src="google.png" alt="Google">
```

```html
<!-- Recommended -->
<img src="google.png" alt="Google">
```

```css
/* Not recommended */
color: #E5E5E5;
```

```css
/* Recommended */
color: #e5e5e5;
```

### 1.1.3. Trailing Whitespace

Remove trailing white spaces.

Trailing white spaces are unnecessary and can complicate diffs.

```html
<!-- Not recommended -->
<p>What?_
```

```html
<!-- Recommended -->
<p>Yes please.
```

## 2. HTML

### 2.1. HTML Style Rules

### 2.1.1. HTML Validity

Use valid HTML where possible.

Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.

Use tools such as the [W3C HTML validator](https://validator.w3.org/nu/#textarea) to test.

### 2.1.2. Semantics

Use HTML according to its purpose.

Use elements (sometimes incorrectly called “tags”) for what they have been created for. For example, use p elements for 
paragraphs, a elements for anchors, etc.

Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

```html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>
```

```html
<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

### 2.1.3. Entity References

Do not use entity references.

There is no need to use entity references like `&mdash;`, `&rdquo;`, or `&#x263a;`, assuming the same encoding (UTF-8) 
is used for files and editors as well as among teams.

The only exceptions apply to characters with special meaning in HTML (like `<` and `&`) as well as control or 
"invisible" characters (like no-break spaces).

```html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.
```

```html
<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

### 2.2. HTML Formatting Rules

#### 2.2.1. General Formatting

Use a new line for every block, list, or table element, and indent every such child element.

Also, indent them if they are child elements of a block, list, or table element.

(If you run into issues around whitespace between list items it’s acceptable to put all li elements in one line. A 
linter is encouraged to throw a warning instead of an error.)

```html
<ul>
  <li>Moe
  <li>Larry
  <li>Curly
</ul>
```

#### 2.2.2. HTML Line-Wrapping

Break long lines (optional).

While there is no column limit recommendation for HTML, you may consider wrapping long lines if it significantly 
improves readability.

When line-wrapping, each continuation line should be indented at least 4 additional spaces from the original line.

```html
<md-progress-circular md-mode="indeterminate" class="md-accent"
    ng-show="ctrl.loading" md-diameter="35">
</md-progress-circular>
```

```html
<md-progress-circular
    md-mode="indeterminate"
    class="md-accent"
    ng-show="ctrl.loading"
    md-diameter="35">
</md-progress-circular>
```

#### 2.2.3. HTML Quotation Marks

When quoting attributes values, use double quotation marks.

Use double ("") rather than single quotation marks ('') around attribute values.

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>
```

```html
<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

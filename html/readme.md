# HTML

## Document Type

We always use the HTML5 document type. The only exception is when dealing with HTML for emails.

```html
<!doctype html>
```

While we are still supporting Internet Explorer 8 we need to include the [HTML5Shiv](https://github.com/aFarkas/html5shiv/) to support the new HTML elements such as `header`, `nav`, `main` etc.

```html
<head>
  <!--[if lte IE 8]><script src="/static/js/html5shiv.js"></script><![endif]-->
</head>
```

## Attributes

### Quotes

Use double quotes consistently for HTML attributes `""`. While omitting the quotes is valid HTML5 this can lead properties being misses eg, `class=used missed` would only use the class `.used` where `class="used missing"` would use `.used` and `.missing`.

```html
<!--  bad  -->
<img src=http://placehold.it/100x100.png alt=Placeholder image>

<img src='http://placehold.it/100x100.png' alt="Placeholder image">

<img src='http://placehold.it/100x100.png' alt='Placeholder image'>

<!--  good  -->
<img src="http://placehold.it/100x100.png" alt="Placeholder image">

```

### Order

Ordering HTML attributes makes the code easier to read and aids the compression.

- `class`
- `id`
- `data-*`
- `for|type|href`

Such that your markup looks like:

```html
<a class="" id="" data-modal="" href="">Example link</a>
```

## ARIA Roles

When you use HTML5 sectioning elements it's a good idea to include the appropriate ARIA landmark roles as well. The trick when you're using both HTML5 and ARIA is to put the landmark on the sectioning element itself because this avoids the information being duplicated by screen readers that support both technologies.

Example:

```html
<header role="banner"></header>
```

The following roles map directly to HTML5 sectioning elements:

- `role="complementary"` maps to the `<article>` element
- `role="contentinfo"` maps to the `<footer>` element
- `role="navigation"` maps to the `<nav>` element

The following landmark roles don't map to HTML5 elements, but are still good to use:

- `role="search"`
- `role="main"`
- `role="application"`

## Comments

Use comments to explain the reasoning behind your decisions if they are not straight forward.

### Actions

Prefixing your comments with `TODO` or `FIXME` helps other developers quickly understand if you're pointing out a problem that needs to be revisited, or if you're suggesting a solution to the problem that needs to be implemented.

```html
<!--  @TODO: Need to implement…  -->

<!--  @FIXME: Need to fix…  -->
```

## Forms

Use HTML5 form controls such as `url`, `tel` and `email` as this will trigger the matching keyboard on touch devices. If unsupported by the browsers these will default back to the `text` type.

Forms should be validated both on the client and server side.

## Indentation

Nested elements should be indented once. Use soft-tabs with two spaces. Code readability should always take precedence over code length.

```html
<!--  bad  -->
<article class="post">
∙∙∙∙<h1>Title Text</h1>
</article>

<article class="post">
∙<h1>Title Text</h1>
</article>

<!--  good  -->
<article class="post">
∙∙<h1>Title Text</h1>
</article>
```

## JavaScript

For performance reason we include any JavaScript just before the end of the `</body>`. In exceptions where the JavaScript is needed during the page load, such as it uses `document.write` or similar to insert content into the page, it is acceptable to include this inside `<head></head>`[1].

Including the JavaScript MIME type is not necessary. It will be recognised as the standard `text/javascript` if omitted. It should therefore we always omit it for the sake of brevity.

```html
<!--  bad  -->
<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.8.1/jquery.min.js"></script>

<!--  good  -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8.1/jquery.min.js"></script>
```


- [1] [Best Practices for Speeding Up Your Web Site](http://developer.yahoo.com/performance/rules.html#js_bottom)



## Self-closing Tags

As self-closing tags are valid but no longer required in html5. We do not need to use them in our markup.

```html
<!--  bad  -->
<br />

<img src="http://example.com/example.png" alt="" />

<img src="http://example.com/example.png" alt=""/>

<!--  good  -->
<br>

<img src="http://example.com/example.png" alt="">

```

## Style Sheets

Style Sheets are included within the `<head></head>`.

CSS should not be included inline on an element. If an element needs styling is should be included via a class either as default or toggled via JavaScript.

```html
<!--  bad  -->
<div style="margin-bottom: 1em">
  <p>Example of inline CSS/</p>
</div>

<!--  good  -->
<div class="box">
  <p>The CSS for .box would look like .box { margin-bottom: 1em; }</p>
</div>
```

Including the CSS MIME type is not necessary. It will be recognised as the standard `text/css` if omitted. Therefore we always omit it for the sake of brevity.

```html
<!--  bad  -->
<link rel="stylesheet" type="text/css" href="/static/css/global.css">

<!--  good  -->
<link rel="stylesheet" href="/static/css/global.css">
```

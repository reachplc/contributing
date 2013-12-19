# CSS (LESS)

## Comments

CSS should be human readable. Classes are easier to re-use when we know what they do, without having to search through the code to work it out.

Comments and descriptive names for classes help to describe what they do.

### File Comments

Explain what the CSS in each file collectively controls:

```
/**
 *  Gallery View
 *
 *  - Controls the products displayed in category
 *    and product views.
 *
 */

.gallery {}
.gallery > .gallery-2columns {}
.gallery-object {}

```

### Inline Comments

If it is unclear or important what a attribute does leave a comment explaining for the next person.

```
/**
 *  1. Removes bullets
 *  2. Removes default margin for `ul`
 *  3. Removes default padding
 */

.list {
  list-style:none;  /* 1. */
  margin-top: 0;  /* 2. */
  margin-bottom: 0;  /* 2. */
  padding-left:0;  /* 3. *
}
```

Most comments are removed in the build process. Giving us all the help we need while developing but none of the extra file size in production.

## ID's

ID's `#` are bad for presentational CSS. In our CSS, reusable is the name of the game, ID's are not allow  as we want it to be as reusable.

## Naming Conventions

Taken from [Harry Roberts](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/).

The naming convention follows this pattern:

```
.block {}
.block__element {}
.block--modifier {}
```

- `.block` represents the higher level of an abstraction or component.

- `.block__element` represents a descendent of .block that helps form .block as a whole.
- `.block--modifier` represents a different state or version of .block.

The reason for double rather than single hyphens and underscores is so that your block itself can be hyphen delimited, for example:

```
.site-search {} /* Block */
.site-search__field {} /* Element */
.site-search--full {} /* Modifier */
```

## Qualifying selectors (specificity)

Avoiding over specifying selectors will limit our ability to reuse classes, make extra work for us to extend classes and force the browser to make extra passes through the DOM.


```
//  bad
div.paragraph {}

.article > .p#intro {}

//  good
.article .p--intro {}

.article p:first-child {}
```

## Units

Where possible always supply relative values such as `em` or `%`. That way our code will always be responsive to it's surroundings.

### 0's

As 0 is the same size no matter what unit is used. This lets us omit unit specification after the 0 value.

```
//  bad
.example {
  margin-bottom: 1em;
  padding: 0em;
}

.example {
  margin-bottom: 1em;
  padding: 0px;
}

//  good
.example {
  margin-bottom: 1em;
  padding: 0;
}
```

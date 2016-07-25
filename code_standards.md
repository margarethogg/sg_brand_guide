#Shiftgig SASS Coding Guidelines

This guide is a living reference for our front-end best practices. View its file structure, core assets, class names, etc as a learning tool. Following these guidelines will ensure projects can be easily interpreted by any developer. Failure to follow them will be met with consequence! They're also open to evolution, suggestion and bribery. Please send all whiskey and/or energy drinks to <a href="mailto:nathan@shiftgig.com">Nathan</a>.

<div class="flash-notice"><strong>There's Bourbon in our SASS!</strong><br/> Bourbon provides a wealth of handy SASS shorcuts and functions that help you write styles faster. It is encouarged that you take advantage of these where it makes sense as they'll quickly become second nature. <a href="http://bourbon.io/docs/">Checkout the docs</a>.</div>

####Naming Conventions
Shiftgig's naming conventions consists of structured class names and meaningful hyphens (i.e., not using hyphens merely to separate words). This is to help work around the current limits of applying CSS to the DOM (i.e., the lack of style encapsulation) and to better communicate the relationships between classes.


####JavaScript

syntax: `js-<targetName>`

JavaScript-specific classes reduce the risk that changing the structure or theme of components will inadvertently affect any required JavaScript behaviour and complex functionality. It is not neccesarry to use them in every case, just think of them as a tool in your utility belt. If you are creating a class, which you dont intend to use for styling, but instead only as a selector in JavaScript, you should probably be adding the js- prefix. In practice this looks like this:

`<a href="/login" class="btn btn-primary js-login"></a>`

Again, JavaScript-specific classes should not. be. styled.


####Utilities

Utilities can be applied directly to any element; multiple utilities can be used together; and utilities can be used alongside component classes.

Utilities exist because certain CSS properties and patterns are used frequently. For example: floats, containing floats, vertical alignment, text truncation. Relying on utilities can help to reduce repetition and provide consistent implementations. They also act as a philosophical alternative to functional (i.e. non-polyfill) mixins.

```html
<div class="u-clearfix">
  <p class="u-textTruncate">{$text}</p>
  <img class="u-pullLeft" src="{$src}" alt="">
  <img class="u-pullLeft" src="{$src}" alt="">
  <img class="u-pullLeft" src="{$src}" alt="">
</div>
```

__u-utilityName__

Syntax: `u-<utilityName>`

Utilities must use a camel case name, prefixed with a u namespace. What follows is an example of how various utilities can be used to create a simple structure within a component.

```html
<div class="u-clearfix">
  <a class="u-pullLeft" href="{$url}">
    <img class="u-block" src="{$src}" alt="">
  </a>
  <p class="u-sizeFill u-textBreak">
    …
  </p>
</div>
```

####Components

Syntax: `<componentName>[--modifierName|-descendantName]`

Component driven development offers several benefits when reading and writing HTML and CSS:

It helps to distinguish between the classes for the root of the component, descendant elements, and modifications.
It keeps the specificity of selectors low.
It helps to decouple presentation semantics from document semantics.
You can think of components as custom elements that enclose specific semantics, styling, and behaviour.


#####ComponentName

The component's name must be written in camel case.

```html
.myComponent { /* … */ }
<article class="myComponent">
  …
</article>
```

__componentName--modifierName__

A component modifier is a class that modifies the presentation of the base component in some form. Modifier names must be written in camel case and be separated from the component name by two hyphens. The class should be included in the HTML in addition to the base component class.

```html
/* Core button */
.btn { /* … */ }
/* Default button style */
.btn--default { /* … */ }
<button class="btn btn--primary">…</button>
```

__componentName-descendantName__

A component descendant is a class that is attached to a descendant node of a component. It's responsible for applying presentation directly to the descendant on behalf of a particular component. Descendant names must be written in camel case.

```html
<article class="comment">
  <header class="comment-header">
    <img class="comment-avatar" src="{$src}" alt="{$alt}">
    …
  </header>
  <div class="comment-body">
    …
  </div>
</article>
```

__componentName.is-stateOfComponent__

Use is-stateName for state-based modifications of components. The state name must be Camel case. Never style these classes directly; they should always be used as an adjoining class.

JS can add/remove these classes. This means that the same state names can be used in multiple contexts, but every component must define its own styles for the state (as they are scoped to the component).

```html
.comment { /* … */ }
.comment.is-expanded { /* … */ }
<article class="comment is-expanded">
  …
</article>
```

####Variables

Syntax: `<property>-<value>[--componentName]`

Variable names in our CSS are also strictly structured. This syntax provides strong associations between property, use, and component.

The following variable defintion is a color property, with the value grayLight, for use with the highlightMenu component.

`$color-grayLight--highlightMenu: rgb(51, 51, 50);`

####Colors

When implementing feature styles, you should only be using color variables provided by colors.scss.
Quick Reference: https://kuler.adobe.com/Shiftgig-2-color-theme-3835325/

When adding a color variable to colors.scss, using RGB and RGBA color units are preferred over hex, named, HSL, or HSLA values.

_Right:_

```css
rgb(50, 50, 50);
rgba(50, 50, 50, 0.2);
```

_Wrong:_

```css
#FFF;
#FFFFFF;
white;
hsl(120, 100%, 50%);
hsla(120, 100%, 50%, 1);
```

__z-index scale__

Please use the z-index scale defined in z-index.scss.

`$zIndex-1 - $zIndex-9` are provided. Nothing should be higher then `$zIndex-9`.


####Font Weight

We've made our imported fonts super easy to work with. All 4 weights can be called using, "MuseoSans" then simply adding the weight you want. Eg: `font-weight: 700` Supported weights follow.

```css
font-weight: 100;
font-weight: 300; //Default
font-weight: 700;
font-weight: 900;
```

Refer to _typography.scss for type size, letter-spacing, and line height. Raw sizes, spaces, and line heights should be avoided outside of _typography.scss. Font sizes are generated in _variables.scss

```css
$fontSize-smallest
$fontSize-smaller
$fontSize-small
$fontSize-base //18px
$fontSize-large
$fontSize-larger
$fontSize-largest
$fontSize-tooDamnBig //Reserved for special headings
```


####Line Height

Typography.scss also provides a line height scale. This should be used for blocks of text.

_ex:_

```css
$lineHeight-tighter
$lineHeight-tight
$lineHeight-base //29px
$lineHeight-loose
$lineHeight-looser
```

Alternatively, when using line height to vertically center a single line of text, be sure to set the line height to the height of the container - 1.

```css
.btn {
  height: 50px;
  line-height: 49px;
}
```

####Letter spacing

Letter spacing should also be controlled with the following var scale.

```
$letterSpacing-tightest
$letterSpacing-tighter
$letterSpacing-tight
$letterSpacing-normal
$letterSpacing-loose
$letterSpacing-looser
```


####Formatting

The following are some high level page formatting style rules.

__Spacing__

CSS rules should be comma seperated but live on new lines:

_Right:_

```css
.content,
.content-edit {
  …
}
```

_Wrong:_

```css
.content, .content-edit {
  …
}
```

CSS blocks should be separated by a single new line. not two. not 0.

_Right:_

```css
.content {
  …
}
.content-edit {
  …
}
```

_Wrong:_

```css
.content {
  …
}

.content-edit {
  …
}
```

__Quotes__

Quotes are optional in CSS. We use double quotes as it is visually clearer that the string is not a selector or a style property.

_Right:_

```css
background-image: url("/img/you.jpg");
font-family: "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial;
```

_Wrong:_

```css
background-image: url(/img/you.jpg);
font-family: Helvetica Neue Light, Helvetica Neue, Helvetica, Arial;
```

####Performance

__Specificity__

Although in the name (cascading style sheets) cascading can introduce unnecessary performance overhead for applying styles. Take the following example:

`ul.user-list li span a:hover { color: red; }`

Styles are resolved during the renderer's layout pass. The selectors are resolved right to left, exiting when it has been detected the selector does not match. Therefore, in this example every a tag has to be inspected to see if it resides inside a span and a list. As you can imagine this requires a lot of DOM walking and and for large documents can cause a significant increase in the layout time. For further reading checkout: https://developers.google.com/speed/docs/best-practices/rendering#UseEfficientCSSSelectors

If we know we want to give all a elements inside the .user-list red on hover we can simplify this style to:

```css
.user-list > a:hover {
  color: red;
}
```

If we want to only style specific a elements inside .user-list we can give them a specific class:

```css
.user-list > .link-primary:hover {
  color: red;
}
```



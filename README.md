# Cool CSS

A Cool approach for CSS.

## <a name='TOC'>Table of Contents</a>

1. [Naming](#naming)
    1. [Components](#components)
    1. [Elements](#elements)
    1. [Variants](#variants)
    1. [Utilities](#utilities)
1. [Architecture](#architecture)
1. [References](#references)


## <a name="naming">Naming</a>

> Syntax: `prefixComponent_element.-variant`

### <a name="naming">Components</a>

> Syntax: `prefixComponent` | `damBox`

You can think of Components as custom elements that enclose specific semantics, styling, and behaviour.

The components can be prefixed with a namespace to avoid the potential for collisions between libraries. This makes it clear which components are part of your app.

> Do: Use **camel case**.

> Do: The **prefix** has **2 or 3 letters**.

CSS
```css
.clBox { … }

.clButton { … }
```
HTML
```html
<div class="clBox"> ... </div>

<button class="clButton"> ... </button>
```

### <a name="elements">Elements</a>

> Syntax: `prefixComponent_element` | `damBox_header`

The Elements are things inside the components.

> Do: Use **camel case**.

> Do: Separated from the component by **one underscore**.

PCSS / SCSS
```css
.clBox {
  &_header { ... }
  &_avatar { ... }
  &_footer { ... }
}
```
CSS
```css
.clBox { ... }
.clBox_header { ... }
.clBox_avatar { ... }
.clBox_footer { ... }
```
HTML
```html
<article class="clBox">
  <header class="clBox_header">...</header>
  <img class="clBox_avatar">
  <footer class="clBox_footer">...</footer>
</article>
```

### <a name="variants">Variants</a>

Syntax: `-variant` | `-light`

The variant modifies (overwrite) the style of the base component.

> Do: Use **camel case**.

> Do: Prefixed with **one hyphen**.

> Do: Set below the default style.

> Do: Use as an adjoining class. This means that the same variant can be used in multiple components, but they must define its own styles (as they are scoped to the component).

> Avoid: Never set variants directly without being enclosed in a component.

PCSS / SCSS
```css
.clBox {
  background: blue;
  width: 100%;
  
  &.-light {
    background: white;
  }
  
  &.-small { 
    width: 50%;
  }
  
  &.-disabled { 
    background: gray;
    cursor: default;
  }
}
```
CSS
```css
.clBox {
  background: blue;
  width: 100%;
}
.clBox.-light {
  background: white;
}
.clBox.-small { 
  width: 50%;
}
.clBox.-disabled { 
  background: gray;
  cursor: default;
}
```
HTML
```html
<div class="clBox -light -small -disabled">...</button>
```

### <a name="utilities">Utilities</a>

Syntax: `-uVariant` | `-uTextCenter`

The utilities classes modifies (overwrite) the style of the any components or elements.

> Do: Use **camel case**.

> Do: Prefixed with **one hyphen** and the **u** letter.

> Do: Set globally below the default styles.

> Do: Use directly in any element or component.

CSS
```css
.-uTextC {
  text-align: center;
}
.-uRight {
  float: right;
}
.-uMarginT10 {
  margin-top: 10px;
}
```
HTML
```html
<div class="clBox -light -uTextC -uRight">...</button>
```
## <a name="architecture">Architecture</a>

**styles** folder
- `var.css` | Global variables (colors, sizes, fonts, ...).
- `base.css` | Global elements overwriting (html, body, a, p, ...).
- `theme.css` | Global theme or framework **overwriting** (bootstrap, materialize, etc) (.btn, .modal, ...).
- `utils.css` | Global utility classes (-uTextC, -uRight, ...).

**component** folder
- `component.css` | The style of a specific component (box.css, modal.css, ...).

## <a name="references">References</a>

* [BEM](http://getbem.com/introduction/)
* [SMACSS](http://smacss.com/book)
* [SUIT CSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [OOCSS](http://oocss.org/)
* [oCSS](http://krasimir.github.io/organic-css/)
* [rscss](http://rscss.io/index.html)

# Cool CSS

A Cool approach for CSS.

## <a name='TOC'>Table of Contents</a>

1. [Naming](#naming)
    1. [Components](#components)
    1. [Elements](#elements)
    1. [Variants](#variants)
    1. [Generics](#generics)
1. [Architecture](#architecture)
1. [Tools](#tools)
1. [References](#references)


## <a name="naming">Naming</a>

> Syntax: `prefixComponent_element.-variant.-gGeneric`

### <a name="naming">Components</a>

> Syntax: `prefixComponent` | `clBox`

You can think of Components as custom elements that enclose specific semantics, styling, and behaviour.

The components can be prefixed with a namespace to avoid the potential for collisions between libraries. This makes it clear which components are part of your app.

> Do: Use **camel case**.

> Do: The **prefix** has **2 or 3 letters**.

css
```css
.clBox { … }

.clButton { … }
```
html
```html
<div class="clBox"> ... </div>

<button class="clButton"> ... </button>
```

### <a name="elements">Elements</a>

> Syntax: `prefixComponent_element` | `clBox_header`

The Elements are things inside the components.

> Do: Use **camel case**.

> Do: Separated from the component by **one underscore**.

pcss / scss
```css
.clBox {
  &_header { ... }
  &_avatar { ... }
  &_footer { ... }
}
```
css
```css
.clBox { ... }
.clBox_header { ... }
.clBox_avatar { ... }
.clBox_footer { ... }
```
html
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

pcss / scss
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
css
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
html
```html
<div class="clBox -light -small -disabled">...</button>
```

### <a name="generics">Generics</a>

Syntax: `-gVariant` | `-gTextCenter`

The utilities classes modifies (overwrite) the style of the any components or elements.

> Do: Use **camel case**.

> Do: Prefixed with **one hyphen** and the **g** letter.

> Do: Set globally below the default styles.

> Do: Use directly in any element or component.

css
```css
.-gTextCenter {
  text-align: center;
}
.-gRight {
  float: right;
}
.-gMarginT10 {
  margin-top: 10px;
}
```
html
```html
<div class="clBox -light -gTextC -gRight">...</button>
```
## <a name="architecture">Architecture</a>

**styles** folder
- `var.css` | Global variables (colors, sizes, fonts, ...).
- `base.css` | Global elements overwriting (html, body, a, p, ...).
- `theme.css` | Global theme or framework **overwriting** (bootstrap, materialize, etc) (.btn, .modal, ...).
- `generic.css` | Global generic classes (-gTextCenter, -gRight, ...).

**component** folder
- `component.css` | The style of a specific component (box.css, modal.css, ...).

## <a name="tools">Tools</a>

* [Stylelint](https://stylelint.io/) | To linting the code.
* [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard) | The standard config for Stylelint
* [PostCSS](http://postcss.org/) | To process the css with the superpowers of javascript. (Instead of sass/less)
* [cssnext](http://cssnext.io/) | A PostCSS plugin to get the future of CSS. Review all [features](http://cssnext.io/features/)

## <a name="references">References</a>

* [BEM](http://getbem.com/introduction/)
* [SMACSS](http://smacss.com/book)
* [SUIT CSS](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md)
* [OOCSS](http://oocss.org/)
* [oCSS](http://krasimir.github.io/organic-css/)
* [rscss](http://rscss.io/index.html)

# Fukorl

**Fukorl&trade;** is a lightweight, breakpoint free, completely responsive, element query driven\*, progressive enhancement based grid framework. It exists in this `README` file, in the annotated code example under **The CSS** (below). Just edit the lines marked 'edit me!' to your requirements and apply to an HTML structure like the one illustrated in **The HTML** (below).

(\* Not really, but kind of. See **3**, below.)

## The CSS

```css
.fukorl {
  overflow: hidden; /* 7 */
}

.fukorl-grid {
  display: flex; /* 1 */
  flex-flow: row wrap; /* 2 */
  margin: -0.5em; /* 6 (edit me!) */
}

.fukorl > * {
  flex-basis: 10em; /* 3 (edit me!) */
  flex-grow: 1; /* 4 */
  margin: 0.5em; /* 5 (edit me!) */
}
```

1. **fukorl&trade;** is a Flexbox based grid system. Even Opera Mini supports Flexbox. Older user agents that don't support Flexbox ignore the `display: flex` declaration, degrading to a single column layout. No harm done.
2. This line determines how items are handled. The important part is `wrap` which means items will start a new row if there's not enough room on the current one.
3. This is the "element query" part. Instead of setting an arbitrary number of columns and using breakpoints, we decide how wide we would like each item to be. How many items you get per row depends on the width of the container.
4. This declaration means that items will 'flex' to use up the available space. If an item wraps onto a new row, it will take up 100% of that row's space. If you add another item to that new row and the overall width is more than twice your `flex-basis`, the row will be divided into two. If not, another new row is created.
5. This is for gutters. A `0.5em` margin here means gutters of `1em` (the margins double up).
6. This should always be a negative version of **5**. It compensates for the margins created by the items. It makes sure the outside of the `.fukorl-grid` container remains flush horizontally and no additional margin is added to the vertical flow.
7. Having used negative margins (**6**) on `.fukorl-grid`, a container element is provided for the application of positive margins where desired. The `overflow: hidden` declaration suppresses horizontal scrollbars caused by negayive margins in some browsers and circumstances.

## The HTML

```html
<div class="fukorl">
  <ul class="fukorl-grid">
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
    <li><!-- grid cell/item/child/whatever --></li>
  </ul>
</div>
```

### RTL Grids

Flexbox supports `rtl` already. Just add `dir="rtl"` to the `.fukorl-grid` element and the flex direction will automatically be reversed.

---
title: The “Lobotomised Owl” Selector
tags:
  - css
emoji: 🦉
date: 2020-12-29
---

It may have a strange name but using the universal selector (`*`) with the adjacent sibling selector (`+`) can provide a powerful CSS capability:

```css
* + * {
  margin-top: 1.5em;
}
```

In this example, all elements in the flow of the document that follow other elements will receive `margin-top: 1.5em`.

For more on the "lobotomised owl" selector, read [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) on _A List Apart_.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

## Flow space utility

The flow utility provides flow and rhythm between direct sibling elements. Where `--flow-space` is not defined: the default value is `1em`, which equals the font size of the affected element.

```css
.flow > * + * {
  margin-top: var(--flow-space, 1em);
}
```

By defining `--flow-space` in the CSS of either a child element of `.flow`, or on `.flow` itself: that value will be honoured in line with the cascade and specificity.

For example: if you set `--flow-space: 3rem` on the third element inside of a `.flow` container: only that element will have a 3rem top margin.

<iframe
  height="265"
  style="width: 100%;"
  scrolling="no"
  title="Flow utility"
  src="https://codepen.io/andybelldesign/embed/OJXEWyO?height=265&theme-id=light&default-tab=css,result"
  frameborder="no"
  loading="lazy"
  allowtransparency="true"
  allowfullscreen="true"
>
  See the Pen{' '}
  <a href="https://codepen.io/andybelldesign/pen/OJXEWyO">Flow utility</a> by
  Andy Bell (<a href="https://codepen.io/andybelldesign">@andybelldesign</a>) on{' '}
  <a href="https://codepen.io">CodePen</a>.
</iframe>

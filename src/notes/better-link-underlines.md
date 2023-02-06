---
title: Better link underlines
tags:
  - css
emoji: ⚓️
date: git Last Modified
---

```scss
a {
  &:link,
  &:visited {
    color: red;
    text-decoration: none;
    border-bottom: 2px solid currentColor;

    @supports (text-decoration-thickness: 2px) {
      text-decoration-style: solid;
      text-decoration-line: underline;
      text-decoration-color: currentColor;
      text-decoration-thickness: 2px;
      text-underline-offset: 3px;
      text-decoration-skip: ink;
      border: 0;
    }
  }
}
```

[Browser support](https://caniuse.com/#feat=mdn-css_properties_text-decoration-thickness)

<iframe
  height="265"
  style="width: 100%;"
  scrolling="no"
  title="Better link underlines"
  src="https://codepen.io/mrmartineau/embed/BaNOZoM?height=265&theme-id=light&default-tab=result"
  frameborder="no"
  allowtransparency="true"
  allowfullscreen="true"
>
  See the Pen{' '}
  <a href="https://codepen.io/mrmartineau/pen/BaNOZoM">
    Better link underlines
  </a>{' '}
  by Zander Martineau (<a href="https://codepen.io/mrmartineau">@mrmartineau</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

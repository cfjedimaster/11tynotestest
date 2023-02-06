---
title: Make a button element look like a link
tags:
  - css
emoji: 🔗
date: 2021-01-04
link: https://piccalil.li/quick-tip/make-a-button-element-look-like-a-link/
---

```css
.link-button {
  display: inline;
  padding: 0;
  border: 0;
  font: inherit;
  cursor: pointer;
  background: transparent;
  color: currentColor;
  -webkit-appearance: none;
  text-decoration: underline;
}
```

<iframe
  height="265"
  style="width: 100%;"
  scrolling="no"
  title="Quick Tip: Link Button"
  src="https://codepen.io/andybelldesign/embed/xxZzEgy?height=265&theme-id=light&default-tab=css,result"
  frameborder="no"
  loading="lazy"
  allowtransparency="true"
  allowfullscreen="true"
>
  See the Pen{' '}
  <a href="https://codepen.io/andybelldesign/pen/xxZzEgy">
    Quick Tip: Link Button
  </a>{' '}
  by Andy Bell (<a href="https://codepen.io/andybelldesign">@andybelldesign</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

ℹ️ It is worth noting that `button`s cannot look exactly like an `a` element because browsers override the `display` property and force it to act like `display: inline-block` despite what you define. The one exception is `display: contents` but there are quite a few catches with that property; more alarmingly, that the element semantics are completely removed which is a nightmare for accessibility. Read more about it here: https://www.scottohara.me/blog/2018/10/03/unbutton-buttons.html

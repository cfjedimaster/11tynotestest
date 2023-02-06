---
title: Picture element
tags:
  - html
emoji: 🖼
date: 2020-03-26
---

## Webp + png usage

```jsx
<picture>
  <source
    type="image/webp"
    srcset="/images/free-cash.webp, /images/free-cash@2x.webp 2x"
  />
  <source
    type="image/png"
    srcset="/images/free-cash.png, /images/free-cash@2x.png 2x"
  />
  <img src="/images/free-cash.png" alt="Free Cash!" />
</picture>
```

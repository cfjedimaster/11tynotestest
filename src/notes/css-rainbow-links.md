---
title: Rainbow links
tags:
  - css
link: https://twitter.com/chrisbiscardi/status/1259606045858467840
date: 2020-05-19
---

```css
.rainbow {
  background-image: linear-gradient(
    90deg,
    rgba(251, 89, 74, 1) 0%,
    rgba(251, 222, 75, 1) 25%,
    rgba(112, 228, 112, 1) 50%,
    rgba(51, 183, 255, 1) 75%
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: rgba(255, 255, 255, 0.46);
}
```

<a
style={{
    backgroundImage: `linear-gradient(
    90deg,
    rgba(251, 89, 74, 1) 0%,
    rgba(251, 222, 75, 1) 25%,
    rgba(112, 228, 112, 1) 50%,
    rgba(51, 183, 255, 1) 75%
  )`,
    WebkitBackgroundClip: 'text',
    WebkitTextFillColor: 'rgba(255, 255, 255, 0.46)',
  }}

> This is a rainbow link
> </a>

With object-styles:

```jsx
<a
  style={{
    backgroundImage: `linear-gradient(
    90deg,
    rgba(251, 89, 74, 1) 0%,
    rgba(251, 222, 75, 1) 25%,
    rgba(112, 228, 112, 1) 50%,
    rgba(51, 183, 255, 1) 75%
  )`,
    WebkitBackgroundClip: 'text',
    WebkitTextFillColor: 'rgba(255, 255, 255, 0.46)',
  }}
>
  This is a rainbow link
</a>
```

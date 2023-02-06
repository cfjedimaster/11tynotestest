---
title: Webmentions
tags:
  - javascript
  - html
emoji: 🗣
date: 2020-03-26
---

## Go to webmention.io

Add this to your site:

```html
<link rel="webmention" href="https://webmention.io/zander.wtf/webmention" />
<link rel="pingback" href="https://webmention.io/zander.wtf/xmlrpc" />
```

### Feeds:

- `https://webmention.io/api/mentions.html?token=H1gjIgBV1XU7F6PUO0lUOg`
- `https://webmention.io/api/mentions.atom?token=H1gjIgBV1XU7F6PUO0lUOg`

### API Key

```
H1gjIgBV1XU7F6PUO0lUOg
```

```
https://webmention.io/api/mentions?perPage=500&jsonp=parseWebmentions&target={PAGE_URL}
```

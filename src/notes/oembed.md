---
title: oEmbed
tags:
  - javascript
  - html
link: 'https://oembed.com/'
date: 2020-06-30
---

Default providers list: https://oembed.com/providers.json

Example provider scheme:

```json
{
  "provider_name": "Twitter",
  "provider_url": "http:\/\/www.twitter.com\/",
  "endpoints": [
    {
      "schemes": [
        "https:\/\/twitter.com\/*\/status\/*",
        "https:\/\/*.twitter.com\/*\/status\/*"
      ],
      "url": "https:\/\/publish.twitter.com\/oembed"
    }
  ]
},
```

Example oEmbed link for Twitter

```
https://publish.twitter.com/oembed?url=https://twitter.com/Interior/status/463440424141459456
```

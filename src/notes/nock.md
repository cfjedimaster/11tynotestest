---
title: Nock
tags:
  - testing
  - javascript
emoji: 🧪
link: https://github.com/nock/nock
date: 2020-05-11
---

```js
const nock = require('nock')

const scope = nock('https://api.github.com')
  .get('/repos/atom/atom/license')
  .reply(200, {
    license: {
      key: 'mit',
      name: 'MIT License',
      spdx_id: 'MIT',
      url: 'https://api.github.com/licenses/mit',
      node_id: 'MDc6TGljZW5zZTEz',
    },
  })
```

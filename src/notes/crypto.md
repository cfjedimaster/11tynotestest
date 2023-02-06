---
title: Crypto
tags:
  - node
  - javascript
emoji: 🛂
date: 2020-03-11
modified: 2020-03-26T23:06:06.000Z
---

The crypto module provides cryptographic functionality that includes a set of wrappers for OpenSSL's hash, HMAC, cipher, decipher, sign, and verify functions.

Docs: http://nodejs.org/api/crypto.html#crypto_crypto

```js
import crypto from 'crypto'

const body = {
  uuid: '433d7a1b-e8e1-4b5a-b590-f468e5c18cc7',
  name: 'Zander',
}

const hash = crypto.createHash('sha256')
hash.update(JSON.stringify(body))
const hashedResponse = hash.digest('hex') // 5a7430e6d96dafadc642289eba7e215d3b9cfd7a58f9593749891424e6d75a4f
```

<iframe
  height="400px"
  width="100%"
  src="https://repl.it/@mrmartineau/crypto?lite=true"
  scrolling="no"
  frameborder="no"
  allowtransparency="true"
  allowfullscreen="true"
  sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"
></iframe>

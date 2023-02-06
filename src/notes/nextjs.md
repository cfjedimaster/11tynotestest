---
title: Next.js
link: https://nextjs.org/docs/
tags:
  - react
date: 2021-03-09
---

## Pages

### `_app.tsx`

```tsx
import { AppProps } from 'next/app'
import React from 'react'
import { ThemeProvider } from 'theme-ui'
import { theme } from '../theme'

const App = ({ Component, pageProps }: AppProps) => {
  return (
    <ThemeProvider theme={theme}>
      <Component {...pageProps} />
    </ThemeProvider>
  )
}

export default App
```

## Data fetching

### [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)

> (Static Generation): Fetch data at build time.

If you export an async function called `getStaticProps` from a page, Next.js will pre-render this page at build time using the props returned by `getStaticProps`.

```tsx
import { GetStaticProps } from 'next'

export const getStaticProps: GetStaticProps = async (context) => {
  const res = await fetch(`https://...`)
  const data = await res.json()

  if (!data) {
    return {
      // return a 404
      // notFound: true,

      // or redirect to another page
      redirect: {
        destination: '/',
        permanent: false,
      },
    }
  }

  return {
    props: {}, // will be passed to the page component as props
  }
}
```

### [`getStaticPaths`](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation)

> (Static Generation): Specify dynamic routes to pre-render pages based on data.

If a page has dynamic routes ([documentation](https://nextjs.org/docs/routing/dynamic-routes)) and uses `getStaticProps` it needs to define a list of paths that have to be rendered to HTML at build time.

The `paths` key determines which paths will be pre-rendered. For example, suppose that you have a page that uses dynamic routes named `pages/posts/[id].js`. If you export `getStaticPaths` from this page and return the following for paths:

```tsx
import { GetStaticPaths } from 'next'

export const getStaticPaths: GetStaticPaths = async () => {
  return {
    paths: [
      {
        params: { id: '1' },
      },
      {
        params: { id: '2' },
      },
    ],
    fallback: true, // or false // See the "fallback" section below
  }
}
```

Then Next.js will statically generate `posts/1` and `posts/2` at build time using the page component in `pages/posts/[id].js`.

### [`getServerSideProps`](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)

> (Server-side Rendering)

If you export an `async` function called `getServerSideProps` from a page, Next.js will pre-render this page on each request using the data returned by `getServerSideProps`.

```tsx
import { GetServerSideProps } from 'next'

export const getServerSideProps: GetServerSideProps = async (context) => {
  const res = await fetch(`https://...`)
  const data = await res.json()

  if (!data) {
    return {
      // return a 404
      // notFound: true,

      // or redirect to another page
      redirect: {
        destination: '/',
        permanent: false,
      },
    }
  }

  return {
    props: {}, // will be passed to the page component as props
  }
}
```

## APIs

### next/router

#### useRouter

```tsx
import { useRouter } from 'next/router'

export default function Page() {
  const router = useRouter()
  return <button onClick={() => router.push('/about')}>Click me</button>
}
```

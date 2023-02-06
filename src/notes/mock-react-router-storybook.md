---
title: Mock React Router location inside Storybook stories
tags:
  - storybook
  - react
emoji: 📖
date: 2022-01-14
---

With a component like this:

```tsx
import { useParams } from 'react-router'

export const ParamsComponent = ({ firstName, lastName }) => {
  const params = useParams<{ id: string }>()
  return <div>{JSON.stringify(params, null, 2)}</div>
}
```

And a story like this:

```tsx
import React from 'react'
import { MemoryRouter, Route } from 'react-router'
import { ParamsComponent } from './ParamsComponent'

export default {
  title: 'ParamsComponent',
  component: ParamsComponent,
}

export const Default = () => {
  return (
    <MemoryRouter initialEntries={['/user/108']}>
      <Route path="/user/:id">
        <UserCard />
      </Route>
    </MemoryRouter>
  )
}
```

The story should render this:

```
{ id: '108' }
```

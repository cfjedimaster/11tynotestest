---
title: Immer
tags:
  - react
date: git Last Modified
---

## Basic example

TBC

## useImmer

```tsx
import React from 'react'
import { useImmer } from 'use-immer'

function App() {
  const [person, updatePerson] = useImmer({
    name: 'Michel',
    age: 33,
  })

  function updateName(name) {
    updatePerson((draft) => {
      draft.name = name
    })
  }

  function becomeOlder() {
    updatePerson((draft) => {
      draft.age++
    })
  }

  return (
    <div className="App">
      <h1>
        Hello {person.name} ({person.age})
      </h1>
      <input
        onChange={(e) => {
          updateName(e.target.value)
        }}
        value={person.name}
      />
      <br />
      <button onClick={becomeOlder}>Older</button>
    </div>
  )
}
```

## Update patterns

https://immerjs.github.io/immer/docs/update-patterns

### Object mutations

```js
import produce from 'immer'

const todosObj = {
  id1: { done: false, body: 'Take out the trash' },
  id2: { done: false, body: 'Check Email' },
}

// add
const addedTodosObj = produce(todosObj, (draft) => {
  draft['id3'] = { done: false, body: 'Buy bananas' }
})

// delete
const deletedTodosObj = produce(todosObj, (draft) => {
  delete draft['id1']
})

// update
const updatedTodosObj = produce(todosObj, (draft) => {
  draft['id1'].done = true
})
```

### Array mutations

```js
import produce from 'immer'

const todosArray = [
  { id: 'id1', done: false, body: 'Take out the trash' },
  { id: 'id2', done: false, body: 'Check Email' },
]

// add
const addedTodosArray = produce(todosArray, (draft) => {
  draft.push({ id: 'id3', done: false, body: 'Buy bananas' })
})

// delete by index
const deletedTodosArray = produce(todosArray, (draft) => {
  draft.splice(3 /*the index */, 1)
})

// update by index
const updatedTodosArray = produce(todosArray, (draft) => {
  draft[3].done = true
})

// insert at index
const updatedTodosArray = produce(todosArray, (draft) => {
  draft.splice(3, 0, { id: 'id3', done: false, body: 'Buy bananas' })
})

// remove last item
const updatedTodosArray = produce(todosArray, (draft) => {
  draft.pop()
})

// remove first item
const updatedTodosArray = produce(todosArray, (draft) => {
  draft.shift()
})

// add item at the beginning of the array
const addedTodosArray = produce(todosArray, (draft) => {
  draft.unshift({ id: 'id3', done: false, body: 'Buy bananas' })
})

// delete by id
const deletedTodosArray = produce(todosArray, (draft) => {
  const index = draft.findIndex((todo) => todo.id === 'id1')
  if (index !== -1) draft.splice(index, 1)
})

// update by id
const updatedTodosArray = produce(todosArray, (draft) => {
  const index = draft.findIndex((todo) => todo.id === 'id1')
  if (index !== -1) draft[index].done = true
})

// filtering items
const updatedTodosArray = produce(todosArray, (draft) => {
  // creating a new state is simpler in this example
  // (note that we don't need produce in this case,
  // but as shown below, if the filter is not on the top
  // level produce is still pretty useful)
  return draft.filter((todo) => todo.done)
})
```

### Nested data structures

```js
import produce from 'immer'

// example complex data structure
const store = {
  users: new Map([
    [
      '17',
      {
        name: 'Michel',
        todos: [
          {
            title: 'Get coffee',
            done: false,
          },
        ],
      },
    ],
  ]),
}

// updating something deeply in-an-object-in-an-array-in-a-map-in-an-object:
const nextStore = produce(store, (draft) => {
  draft.users.get('17').todos[0].done = true
})

// filtering out all unfinished todo's
const nextStore = produce(store, (draft) => {
  const user = draft.users.get('17')
  // when filtering, creating a fresh collection is simpler than
  // removing irrelvant items
  user.todos = user.todos.filter((todo) => todo.done)
})
```

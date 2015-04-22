# graphql-types

## Install

```sh
npm install --save graphql-types
```

## Usage

```js
import * as GraphQL from 'graphql-types'

const fragment = new GraphQL.Fragment('Viewer', [
  new GraphQL.Field('name'),
  new GraphQL.Field('email'),
])

const query = new GraphQL.Query('viewer', [4], [
  new GraphQL.Field('id'),
  new GraphQL.Field('profile_picture', [
    new GraphQL.Field('uri'),
  ], null, [ new GraphQL.Call('site', ['mobile']) ]),
], [ fragment ])
```

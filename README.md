# graphql-types

## Install

```sh
npm install --save graphql-types
```

## Usage

### Creating queries

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

### Serializing

Client:

```js
// Serialize the query before sending it
const json = JSON.stringify(query)
```

Server:

```js
// Deserialize the query
const query = GraphQL.Query.fromJSON(JSON.parse(req.body))
```

### Debugging

You can dump queries to easily debug them:

```js
fragment.toString() // {email,name}
query.toString()    // viewer(4){email,id,name,profile_picture.site(mobile){uri}}
```

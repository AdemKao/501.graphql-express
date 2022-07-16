# GraphQL - Demo
Date: 2022/07 by Adem

The sample is learn from [Web Dev Simplified](https://www.youtube.com/watch?v=ZQL7tL2S0oQ&t=1921s) 
## Contents
- [GraphQL - Demo](#graphql---demo)
  - [Contents](#contents)
  - [Summary](#summary)
  - [Install Package](#install-package)
  - [Change package.json content](#change-packagejson-content)
  - [Create a simple Server](#create-a-simple-server)
  - [Create a middleware](#create-a-middleware)
  - [Create GraphQL Object Type](#create-graphql-object-type)
  - [Create GraphQL Schema](#create-graphql-schema)
  - [Create Test Data](#create-test-data)
## Summary
This simple demo is to create a graphQL to CRUD data.

## Install Package
```nodejs
npm i  express express-graphql graphql
npm i --save-dev nodemon
```

## Change package.json content

  -   main  : server.js -> start to server.js
  -   script: nodemon server.js ->use nodemon to keep refreshing server when you update the code
   
```json
{
  "name": "501.graphql-demo",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "devStart":"nodemon server.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.1",
    "express-graphql": "^0.12.0",
    "graphql": "^16.5.0"
  },
  "devDependencies": {
    "nodemon": "^2.0.19"
  }
}
```
## Create a simple Server
create `server.js` file and type these codes
```javascript
//server.js
const express = require("express");
const app = express();

app.listen(5000, () => console.log("Server Running"));
```
Then run server, and you will see the console log `Server Running`
```nodejs
> npm run devStart

[nodemon] 2.0.19
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node server.js`
Server Running
```
But when you open the browser `localhost:5000`,you will get some Error `Cannot GET /` because you do not already write middleware.
Let's create a middleware in next step
## Create a middleware
```javascript
//server.js
...
app.use(
  "/graphql",
  expressGraphQL({
    schema: schema,
    graphiql: true,
  })
);
```
## Create GraphQL Object Type
```javascript
//server.js
...
const BookType = new GraphQLObjectType({...})
const AuthorType = new GraphQLObjectType({...})
const RootQueryType = new GraphQLObjectType({...})
const RootMutationType = new GraphQLObjectType({...})
```
## Create GraphQL Schema
```javascript
//server.js
...
const schema = new GraphQLSchema({
  query: RootQueryType,
  mutation: RootMutationType,
});
```
## Create Test Data
```javascript
//server.js
...
const authors = [...]
const books = [...]
```
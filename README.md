# Redis Manual

## Table of Contents

* [Introduction](#introduction)
* [Data Types](#data-types)
* [Redis Client](#redis-client)
* Strings
* Lists
* Sets
* Hashes
* Sorted Set
* Bitmap
* HyperLogLogs
* GEO
* Pub/Sub

## Introduction

> Remote Dictionary Server

```
- Key-Value data structure store
- Configurable persistent
- Support atomic operations
- Support transactions
- Single threaded
```

## Data Types

```
- Strings
- Lists
- Sets
- Hashes
- Sorted Set
- Bitmap
- HyperLogLogs
- GEO
- Pub/Sub
```

## Redis Client

```javascript
const redis = require('redis')
const client = redis.createClient('6379', 'localhost')

client.on('connect', () => {
  console.log('connected')
})

client.on('error', err => {
  console.error(err)
})
```

## String

```javascript
const redis = require('redis')
const client = redis.createClient('6379', 'localhost')
const { promisify } = require('util')
client.get = promisify(client.get)

client.on('connect', () => {
  console.log('connected') // connected
})

client.on('error', err => {
  console.error(err)
})

client.set('name', 'Yo', redis.print) // Reply: OK
client
  .get('name')
  .then(res => console.log(res)) // Yo
  .catch(err => console.log(err))

client.mset(['name1', 'Yo', 'name2', 'Yea'], redis.print)
client.mget(['name1', 'name2'], (_, res) => console.log(res))
```

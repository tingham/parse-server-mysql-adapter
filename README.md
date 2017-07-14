[![Build Status](https://travis-ci.org/dplewis/parse-server-mysql-adapter.svg?branch=master)](https://travis-ci.org/dplewis/parse-server-mysql-adapter) [![npm version](https://badge.fury.io/js/parse-server-mysql-adapter.svg)](https://badge.fury.io/js/parse-server-mysql-adapter)
# MySQL Parse Server Adapter

This is database adapter to add support of MySQL to Parse Server

## Setup

This only runs on MySQL >= 5.7.

Create **one** Database using the MySQL CLI or Query Expression Editor on your MySQL instance.

```
mysql> CREATE DATABASE `database_here`
```

## Usage

```
const uri = 'mysql://root@localhost:3306/database_here';
const MySQL = require('parse-server-mysql-adapter').MySQL;
const mysql = new MySQL(uri);

var api = new ParseServer({
  databaseAdapter: mysql.getAdapter(),
  appId: 'myAppId',
  masterKey: 'myMasterKey'
  serverURL: 'http://localhost:1337/parse'
  ...
});
```
This adapter is backwards compatible with `node-mysql`. You can pass connection options into the adapter.
You can find a list of available options [here](https://github.com/mysqljs/mysql#connection-options)

---

## Limits in MySQL

Just like other databases MySQL has also some limits that are documented [here](https://dev.mysql.com/doc/refman/5.7/en/limits.html):

# Compatibility with Parse Server

Please remember MySQL has recently added a JSON Type in version 5.7. This adapter tried its best to simulate how Parse Server works with other Databases like Postgres, however these features or functions won't work as you expect. Features including JSON and Array will be improved in future updates.

- **Removing From Array** : You can only `remove` strings from array and only one.
- **Regex** : Limited support for regex.

---

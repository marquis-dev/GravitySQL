# Gravitybot SQL !

## Installation
```npm
npm install @gravitybot/sql
```

## Required
- **[MySQL 2](https://www.npmjs.com/package/mysql2)**

## How to use?
@gravitybot/sql Is a simple module that includes simplified functions of the mysql module

This is an example usage of our package
```js

/**
  * Create the mysql connection
  * Then connect
  */

const mysql = require('mysql2');

const sql = mysql.createConnection({
    host: 'MYSQL_HOST',
    user: 'MYSQL_USER',
    password: 'MYSQL_PASSWORD',
    database: 'MYSQL_DB',
    port: 'MYSQL_PORT' // optionnal
});

sql.connect((err) => {
    if(err) throw new Error(err);
    else console.log('Connected to MySQL2')
})

/**
  * Now create a new Base
  */

const { Base } = require('@gravitybot/sql');

const myBase = new Base(sql, 'myTable', {
    // This is a default values
    name: 'Default Name',
    age: 18
});

; (async () => {

    const new_data = await myBase.create({
        // Some values here
        name: 'Marquis'
    });

    /**
     * Note:
     * When you create a new data the
     * default values will include on the new
     * data with the entred values
     */

    console.log(new_data);

    /**
     * Returns:
     * { name: 'Marquis', age: 18 }
     */

})();
```

<table>
  <tr>
    <th>Function</th>
    <th>Description</th>
    <th>Params</th>
  </tr>
  <tr>
    <td>create</td>
    <td>To create a new data in the table</td>
    <td>values? (optional)</td>
  </tr>
  <tr>
    <td>find</td>
    <td>To get an array of requested data</td>
    <td>where? (optional)</td>
  </tr>
  <tr>
    <td>findOne</td>
    <td>To get an object of requested data</td>
    <td>where? (optional)</td>
  </tr>
  <tr>
    <td>findOneAndDelete</td>
    <td>To delete some data from the table</td>
    <td>where (important)</td>
  </tr>
  <tr>
    <td>findOneAndUpdate</td>
    <td>To update some data in the table</td>
    <td>where (important)<br>values (important)</td>
  </tr>
</table>

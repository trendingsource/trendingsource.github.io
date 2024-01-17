---
layout: post
title: "Getting Started with MongoDB - A Beginner's Guide"
date:   2024-02-04 07:52:34 +0000
categories: "DB"
excerpt_image: https://www.turing.com/blog/wp-content/uploads/2022/02/Mongo-DB-Features.jpg
image: https://www.turing.com/blog/wp-content/uploads/2022/02/Mongo-DB-Features.jpg
---

### Understanding NoSQL and Document Databases
MongoDB is a popular open-source document database which uses JSON-like documents instead of traditional row-based tables. When starting out with any NoSQL database, the concept of document-oriented storage can take some adjustment if you are used to relational databases. **document databases MongoDb** store data in flexible, key-value pair documents that are collected in databases, each of which contain collections of documents rather than tables and rows. 
Documents look very similar to JSON objects and MongoDB gives you the power store and query hierarchical data that doesn't fit neatly into the row-and-column structure of a relational database. This makes MongoDB well-suited for applications that work with unstructured or semi-structured data like user profiles, product catalogs, session logs, and sensor data. The flexibility of documents allows MongoDB to scale horizontally on commodity hardware and handle massive amounts of both structured and unstructured information with high performance.

![](https://i.ytimg.com/vi/_O2alVdFV1k/maxresdefault.jpg)
### Downloading and Installing MongoDB
Getting MongoDB up and running locally is relatively straightforward. To get started, navigate to the MongoDB download page at https://www.mongodb.com/try/download/community and click the download button to grab the latest version for your operating system. Once the download finishes, simply run the installer and follow the standard installation prompts. 
By default, MongoDB will install to C:\Program Files\MongoDB\Server\ on Windows machines or /usr/local/mongodb on Linux and macOS. Make sure to add the MongoDB bin path to your system PATH environment variable so commands can be executed from any shell. With the download and installation completed, you're ready to start MongoDB!
### Starting the MongoDB Database Server
To start MongoDB on Windows, open a command prompt as Administrator and type:
```
mongod
``` 
On Linux and Mac systems, open a terminal window and run: 
```
sudo mongod
```
This will start the MongoDB server daemon in the background. By default, it will run on port 27017 and store data in the /data/db directory. You should see some log output confirming MongoDB has started successfully. At this point you have a single node development cluster up and running locally!
### Using the MongoDB Shell 
To interact with your new MongoDB instance, open a new terminal/command prompt and run the mongo shell:
```
mongo
```
The mongo shell provides an interactive JavaScript interface to your MongoDB deployment, allowing you to execute queries, view database and collection information, insert and remove documents and more. **MongoDB tutorial** Through the shell you can explore MongoDB functionality, test out queries, and get familiar with interacting with documents.
### Creating a Database and Collection
Let's create a basic database and collection to start storing some data. In the mongo shell, use the `use` command to select a database: 
```
use myDatabase
```
Now you have selected the "myDatabase" database. If it didn't already exist, MongoDB automatically created it for you. Next, select a collection within that database using `db.createCollection()` :
```
db.createCollection('myCollection')
```
Now you have selected the "myCollection" collection within the "myDatabase" database. Collections are equivalent to tables in a relational database - this is where your actual application data will reside. Your database is prepared and ready to start inserting documents!
### Inserting Documents 
Now that you have a database and collection defined, you can start inserting documents. Documents in MongoDB resemble JSON objects, with a flexible semi-structured schema. Let's insert a sample document:
```
db.myCollection.insertOne({"name": "John Doe", "age": 30})
```
To verify the insertion was successful, you can view the document like this: 
```
db.myCollection.findOne() 
```
You now have your first document stored in MongoDB! Repeating the `insertOne()` method allows you to populate your collection with more documents as needed for testing. This covers the basics of getting started - you now have MongoDB installed and configured with an example database, collection, and document insertions.
### Querying and Retrieving Documents
One of the powerful features of MongoDB is its convenient querying syntax using JSON-like documents. To retrieve all documents from the collection:
```
db.myCollection.find({})
``` 
You can filter results by specifying query criteria, for example to find all documents with age 30:
```
db.myCollection.find({age: 30}) 
```
Or retrieve only the name field:
```
db.myCollection.find({},{name: 1})
```
MongoDB also supports more complex queries using operators like $gt, $in, $or etc. The full querying capabilities take advantage of MongoDB's flexible document schema. Mastering queries is an important next step for any MongoDB developer.
### Update and Delete Operations
Rounding out the basic CRUD operations, MongoDB provides intuitive methods for updating and deleting documents as well. To update the age field of the first document to 35: 
```
db.myCollection.updateOne({name: "John Doe"},{$set: {age: 35}})
```
And to delete all documents matching a criteria:
```
db.myCollection.deleteMany({age: 35})
```
This covers the essentials of interacting with MongoDB through basic operations like insert, query, update and remove. With this groundwork in place, you're ready to start building applications and taking advantage of MongoDB's powerful features.
### Next Steps with MongoDB
At this point you have the core MongoDB skills to get started with development. Some next steps include:
- Learning more complex queries with aggregation, array operations etc
- Setting up replica sets for high availability and scalability  
- Exploring full-text search, geospatial and graph capabilities
- Building starter applications with drivers in your preferred language
- Deploying to the cloud on MongoDB Atlas for production workloads
- Earning official MongoDB certification through University courses
The MongoDB manual, tutorials on University and resources online provide countless opportunities to deepen your skills. With MongoDB's flexibility and performance, the only limit is your imagination for data-powered applications. Have fun advancing your MongoDB journey!
 ![Getting Started with MongoDB - A Beginner's Guide](https://www.turing.com/blog/wp-content/uploads/2022/02/Mongo-DB-Features.jpg)
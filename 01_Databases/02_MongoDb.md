**MongoDB** is a document-oriented database. This means that it doesn’t use tables and rows to store its data, but instead collections of JSON-like documents.
**MongoDB** is also a schema-less database, so we don’t need to specify the number or type of columns before inserting our data.

Here’s an example of what a **MongoDB** document might look like:

```javascript
    	{
      		_id: ObjectId(3da252d3902a),
     		type: "Tutorial",
    		title: "An Introduction to MongoDB",
      		author: "Coded",
      		tags: [ "mongodb", "compass", "crud" ],
    	}
```

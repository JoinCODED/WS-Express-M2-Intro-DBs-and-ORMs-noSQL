1. Moving to the `taskCreate` method. Mongoose has a model method called `create`, you pass it your fields and it wil return the newly created task from the database.

   ```javascript
   exports.taskCreate = (req, res) => {
     const newTask = Task.create(req.body);
     res.status(201).json(newTask);
   };
   ```

2. As we agreed, **Mongoose methods** are _asynchronous_, so we need an `async await` and a `try-catch` block.

   ```javascript
   exports.taskCreate = async (req, res) => {
     try {
       const newTask = await Task.create(req.body);
       res.status(201).json(newTask);
     } catch (error) {
       res.status(500).json({ message: error.message });
     }
   };
   ```

Let's test it using Postman by sending a `POST` request to `http://localhost:8000/tasks`.

```json
{
  "_id": "616fe9d2d937ac1c22aa7f72",
  "task": "New Task",
  "updatedAt": "2020-04-30T06:57:23.945Z",
  "createdAt": "2020-04-30T06:57:23.945Z"
}
```

It works! Look at this! The database **automagically** generated an `_id`, a `createdAt` and `updatedAt` fields!!

But what about our slug?! Don't worry! I didn't forget it.

1. Let's start with adding a slug field to our model.

   ```javascript
   {
     slug: STRING;
   }
   ```

2. Now, we can still use the `slugify` library, but it will not generate a unique slug each time, so we'll a Mongoose plugin called [`mongoose-slug-plugin`](https://www.npmjs.com/package/mongoose-slug-plugin). Let's take a look at it.

   ```shell
     $ npm i mongoose-slug-plugin
   ```

3. First, we will require our brnad new library

   ```javascript
   const mongooseSlugPlugin = require('mongoose-slug-plugin');
   ```

4. Then **right before** our export in `models/Task.js`, call `TaskSchema.plugin` method, and we will pass it our plugin `mongooseSlugPlugin` and the `source` of our slugs which is the `task`.

   ```javascript
     const TaskSchema = new Schema({
       ...
     });

     TaskSchema.plugin(mongooseSlugPlugin, { tmpl: '<%=task%>' });

     module.exports = model('Task', TaskSchema);
   }
   ```

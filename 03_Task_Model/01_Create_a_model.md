1. Create a file in your `models` folder called `Task.js`. Make sure it's **singular** and starts with **a capital letter!**

2. In this file we will start with importing `model` and `Schema` from mongoose.

   ```javascript
   const { model, Schema } = require('mongoose');
   ```

3. Next, we will **define** our **model**, using `mongoose`'s `Schema` function.

   ```javascript
   const TaskSchema = new Schema();
   ```

4. Next we will define the fields of this model. We will add two fields to our model, `task` and `done`.

   ```javascript
   const TaskSchema = new Schema(
   {
    task: String,
    done: Boolean,
   }
   ```

5. One more thing! **Don't forget to export TaskModel!**

   ```javascript
   module.exports = model('Task', TaskSchema);
   ```

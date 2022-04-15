1. Moving to the update method, let's start by adding the `async await` and `try-catch` block.

   ```javascript
   exports.taskUpdate = async (req, res) => {
     const { taskId } = req.params;
     try {
       // ...
     } catch (error) {
       res.status(500).json({ message: error.message });
     }
   };
   ```

2. Updating a `task` **requires two steps**: **finding** the task with `taskId`, then **updating** this task. To get an item by its ID we will use a method called `.findById()`. `_id` is our _primary key_, which is a unique value that distinguishes between the objects.

   ```javascript
   exports.taskUpdate = async (req, res) => {
     const { taskId } = req.params;
     try {
       const foundTask = await Task.findById(taskId);
     } catch (error) {
       res.status(500).json({ message: error.message });
     }
   };
   ```

3. Then if `foundTask` is true we will use a **Mongoose method** called `findByIdAndUpdate()` that **will take care of updating the task for us**. and we will pass it `{new:true}` as an argument to return the updated document Don't forget to **change the status** to `204` and **end the response**.

   ```javascript
   try {
     const foundTask = await Task.findById(taskId);
     await Task.findByIdAndUpdate({_id:taskId,req.body,{new:true}})
     res.status(204).end();
   }
   ```

4. But what if the task ID sent doesn't exist? The response is `null` with a status code `200`. We need to fix this! We must check if the task is found or not:

   ```javascript
   try {
     const foundTask = await Task.findById(taskId);
     if (foundTask) {
     await Task.findByIdAndUpdate({_id:taskId,req.body,{new:true}})
       res.status(204).end();
     } else {
       res.status(404).json({ message: "Task not found" });
     }
   }
   ```

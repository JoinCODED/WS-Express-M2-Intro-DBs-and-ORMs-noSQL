1. Back to our Express application, install `mongoose`.

   ```shell
   npm install mongoose
   ```

2. Create a file called **database.js** under the project root.

3. Import the **mongoose** module.

   ```javascript
   const mongoose = require('mongoose');
   ```

4. Connect to your database using the connect method from mongoose.

   ```javascript
   const connectDB = async () => {
     const conn = await mongoose.connect('YOUR_CONNECTION_STRING');
     console.log(`mongo connected: ${conn.connection.host}`);
   };
   ```

5. To get your connection string head back to your **Atlas** account and click **Connect** next to your cluster.

![Mongo](https://i.ibb.co/DrytF9K/app-overview-v8.png)

6. A modal will open, select **Connect to your application**.

![Mongo](https://i.ibb.co/59qBLJH/app-overview-v8.png)

7. Copy your connection string and replace it with the connection string from step 4. Don't forget to change `<password>`!

![Mongo](https://i.ibb.co/7RT10Qc/app-overview-v8.png)

8. Export!

   ```javascript
   module.exports = connectDB;
   ```

9. In app.js import the file we just created.

   ```javascript
   const connectDb = require('./database');
   ```

10. Call our method anywhere before `app.listen`.

    ```javascript
    connectDb();
    ```

## Creating your first Cluster

1. Log into your Atlas account.
2. Click on **Build a database**.

![MongoDB](https://i.ibb.co/6HKjtxh/app-overview-v8.png)

3.  Select **Shared** Clusters and click **Create** a Cluster.

![MongoDB](https://i.ibb.co/6sGyyv8/app-overview-v8.png)

4. Select your **Aws** Cloud Provider & **Europe** Region

![MongoDB](https://i.ibb.co/Fbj21WC/app-overview-v8.png)

5. Click on **create** a cluster

Now your cluster is being created and it may take up to 5 mins.

## Add Your Connection IP Address to IP Access List.

In Atlas, you can only connect to a cluster from a trusted IP address. Within Atlas, you can create a list of trusted IP addresses.

Add your IP address to the IP access list by following the steps:

1. On the left panel under **Security** Click on **Network Access**.
2. Click on **Add IP Address**.
3. A modal will open up for you and you can click on **Add current ip address** or **Allow access from anywhere**.
   ![MongoDB](https://i.ibb.co/tqC0mbV/app-overview-v8.png)
4. Click **confirm**.

## Create a Database User for Your Cluster

You must create a database user to access your cluster. For security purposes, Atlas requires clients to authenticate as MongoDB database users to access clusters.

1. On the left panel under **Security** click on **Database Access**.
2. Click on **Add New Database User**.
3. A modal will open up, and select **Password** as an **Authentication Method**.
4. Choose a **username** and a **password** for your user and **save** them because we need them to access our database later.
5. For **Database User Privileges** select **Atlas Admin**.
   ![MongoDB](https://i.ibb.co/wwvWb79/app-overview-v8.png)
6. Click **Add User**.

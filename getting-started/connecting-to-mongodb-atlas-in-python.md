# Connecting to MongoDB Atlas in Python

To connect to our MongoDB Atlas database, you will need to get the connection string for the cluster. Similar to connecting via Compass, you need to click connect and then choose Connect App. There you will find the connection string needed for our code.

Use the following code to connect to our cloud database by replacing the connection string from what we got from MongoDB Atlas.

```py
import pymongo
from pymongo import MongoClient


client = MongoClient("<CONNECTION_STRING>")

print(client.mflix)
```

If there is no error and the database instance is displayed instead, it means that you have successfully connected to MongoDB Atlas

## Analyzing the Connection String

In our connection we have used the string that is similar to the following:

`mongodb://kay:myRealPassword@mycluster0-shard-00-00-wpeiv.mongodb.net:27017,mycluster0-shard-00-01-wpeiv.mongodb.net:27017,mycluster0-shard-00-02-wpeiv.mongodb.net:27017/admin?ssl=true&replicaSet=Mycluster0-shard-0&authSource=admin`

Here the **kay** is the username as **myRealPassword** is the password created when instantiating the cluster. These credentials can also be changed under the security tab of the cluster in the dashboard.

The addresses

`mycluster0-shard-00-00-wpeiv.mongodb.net:27017,mycluster0-shard-00-01-wpeiv.mongodb.net:27017,mycluster0-shard-00-02-wpeiv.mongodb.net:27017`

pertain to the seed list. To note, the are multiple addresses separated by commas. This to ensure that when the **primary** \(which is the first\) fails, the driver will automatically use the other cluster addresses. It can be considered as a replicated alternate database synced in the background. When transacting with Robo3T \(as mentioned in the previous chapter\), the addresses other than the primary only allow read only access.

After the seed list is `/admin` This is the name of the current database which is set to admin. This can be changed when using a different database. Other important information is `Mycluster0-shard-0` which as mentioned earlier, pertains to the name of the cluster.

By here you should be able to connect to your cloud data

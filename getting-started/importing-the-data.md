# Importing the Data

Next thing we need to do is to import the Data we have to MongoDB. The coursera course provides a csv for initial data called [movies.csv](https://s3.amazonaws.com/edu-static.mongodb.com/lessons/coursera/building-an-app/getting-data-into-mongodb/movies_initial.csv) \([https://goo.gl/Sri8qW](https://goo.gl/Sri8qW)\)

We will need to log in to our MongoDB Atlas dashboard. Before proceeding make sure your IP address is linked to our cluster by clicking **Connect** then adding the current IP address in the whitelist. Alternatively there is also an option to allow all IP address from anywhere but caution might be considered as this might cause some security problems.

If the initial data has been downloaded we will need to import this to our cloud instance of mongodb by using the following code

```bash
$ mongoimport --type csv --headerline --db mflix --collection movies_initial --host "<CLUSTER>/<SEED_LIST>" --authenticationDatabase admin --ssl --username <USERNAME> --password <PASSWORD> --file movies_initial.csv
```

The USERNAME and PASSWORD pertains to the credentials added when creating the cluster. While still in the **Connect** dialog,  choose **Connect with the Mongo Shell**. Information for CLUSTER, SEED\_LIST can be found on the next display. Though not very intuitive at first because a commandline is displayed,  after`replicaSet` displays the value needed for CLUSTER. While the values after mongodb:// are the lists needed for our seed list. These values are URLs separated by comma. Copy these values right before the /test. Like I mentioned, this is a bit counter intuitive but hopefully it should work.

## Analyzing the Connection String

A sample connection string provided by MongoDB docs: 

`mongodb://kay:myRealPassword@mycluster0-shard-00-00-wpeiv.mongodb.net:27017,mycluster0-shard-00-01-wpeiv.mongodb.net:27017,mycluster0-shard-00-02-wpeiv.mongodb.net:27017/admin?ssl=true&replicaSet=Mycluster0-shard-0&authSource=admin`

Here the **kay** is the username as **myRealPassword** is the password created when instantiating the cluster. These credentials can also be changed under the security tab of the cluster in the dashboard. 

The addresses 

mycluster0-shard-00-00-wpeiv.mongodb.net:27017,mycluster0-shard-00-01-wpeiv.mongodb.net:27017,mycluster0-shard-00-02-wpeiv.mongodb.net:27017

pertain to the seed list. To note, the are multiple addresses separated by commas. This to ensure that when the **primary** \(which is the first\) fails, the driver will automatically use the other cluster addresses. It can be considered as a replicated alternate database synced in the background. When transacting with Robo3T \(which will be discussed on the next chapter\), the addresses other than the primary only allow read only access.

After the seed list is `/admin` This is the name of the current database which is set to admin. This can be changed when using a different database. Other important information is `Mycluster0-shard-0` which as mentioned earlier, pertains to the name of the cluster. 


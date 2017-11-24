# Importing the Data

Next thing we need to do is to import the Data we have to MongoDB. The coursera course provides a csv for initial data called [movies.csv](https://s3.amazonaws.com/edu-static.mongodb.com/lessons/coursera/building-an-app/getting-data-into-mongodb/movies_initial.csv) \([https://goo.gl/Sri8qW](https://goo.gl/Sri8qW)\)

We will need to log in to our MongoDB Atlas dashboard. Before proceeding make sure your IP address is linked to our cluster by clicking **Connect** then adding the current IP address in the whitelist. Alternatively there is also an option to allow all IP address from anywhere but caution might be considered as this might cause some security problems.

If the initial data has been downloaded we will need to import this to our cloud instance of mongodb by using the following code

```bash
$ mongoimport --type csv --headerline --db mflix --collection movies_initial --host "<CLUSTER>/<SEED_LIST>" --authenticationDatabase admin --ssl --username <USERNAME> --password <PASSWORD> --file movies_initial.csv
```

The USERNAME and PASSWORD pertains to the credentials added when creating the cluster. While still in the **Connect** dialog,  choose **Connect with the Mongo Shell**. Information for CLUSTER, SEED\_LIST can be found on the next display. Though not very intuitive at first because a commandline is displayed,  after`replicaSet` displays the value needed for CLUSTER. While the values after mongodb:// are the lists needed for our seed list. These values are URLs separated by comma. Copy these values right before the /test. Like I mentioned, this is a bit counter intuitive but hopefully it should work.

## 




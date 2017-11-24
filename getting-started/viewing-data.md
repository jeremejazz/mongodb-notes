# Viewing data from your Local Machine

Perhaps the best tool used in order to view our database in the cloud is by using MongoDB Compass. This free tool can be Downloaded here \([https://www.mongodb.com/products/compass\](https://www.mongodb.com/products/compass%29\)

## Connecting via Robo3T

At the time of this writing, the I had a problem in running MongoDB Compass in running inside a Virtual machine due to the the fact that it requires extra GPU power since this was made using electron. Alternatively you can also use [Robo3T](https://robomongo.org/) \(formerly Robomongo though I still call it that way\). According to online forums this feature in Robo3T is new so you might expect a little difficulty in connecting as compared to Compass.

Here are the steps made:

1. In Connection Settings, create a new instance of connection. Name it atlas or whatever you like
2. Use one of the URL from the 'seed' list on the address. You don't need to include the port number from the URL as there is a separate box where it might already be pointing to 27017. 
3. Under the Authentication Tab, activate the fields by checking Perform Authentication. Fill in the credentials. Use **admin** for the database if applicatble and your User credentials for the cluster. The Auth Mechanism used is : SCRAM-SHA1
4. Enable the SSL tab and choose Self-Signed Certificate.
5. Choose Save then Connect. If an error occurs that says about establishing connection try another URL from the seed list.  

Keep in mind that the first address in the seed list \(usually has a shard-00-00-.. \) pertains to the Primary node, that allows read/write access. While the other are like alternative link but only give Read access. Unlike compass you can only put one node for now.



# Why MongoDB?

## Relational Database

For years, the relational database has become the standard when it comes to storing data. There's nothing wrong with using these as time has tested their effectiveness in terms of security and consistency and modern RDBMS has gotten mature over the years. One major problem with the existing design though is as the database structure becomes complex, it became difficult to manage especially when performing complex queries and also gains some problems in performance. 

I remember a few years back then on my previous job when we were developing an e-commerce website, we had to "flatten" the transaction table \(removing relational tables and merging them into one table\) just to keep performance. For a developer, this is a nightmare especially when querying since you would need to adjust your code just to get the results. The same database architecture was used on other projects. This was a startup company back then and I've tried suggesting NoSQL but the boss just wanted a technology that everybody knows and came to grow up with \(and was perhaps afraid to invest in training\). But this kind of mindset might not be applicable today if put into more consideration.

## Document-oriented Database

MongoDB is a document oriented database. This design enables data to be stored along with it's related information. Instead of putting up an additional lookup table, you can instead insert these referenced information. This is no longer the traditional simplification of many-is-to-many where you would need to break down information into separate entities since it is difficult to  store and query this on the existing table. 

MongoDB makes this possible by storing data in JSON format. Well it's actually a serialized form of JSON known as BSON \(Binary-JSON\). 






# MongoDB & Redis C#/.NET
A program that can insert a record into MongoDB and Redis at the same time.
I document here the implementation of the program and how everything is beeing added into both data base's.


# Insert A record
![redis1](https://user-images.githubusercontent.com/80118008/130612914-b71cd475-85c3-427c-8681-156551e45f20.gif)

# Inside MongoDB
![redis2](https://user-images.githubusercontent.com/80118008/130612959-ea1614c1-7a26-43ce-85bc-d19a0166e36e.gif)

# Inside Redis
![rediscli](https://user-images.githubusercontent.com/80118008/130612990-bd426538-9a13-4a63-a8a1-0b99c3e8d8de.gif)



# The Class's
### ● MongoDBCRUD

![mCRUD0](https://user-images.githubusercontent.com/80118008/130611270-f08d6401-cce2-464a-9d10-7a92e3c42456.PNG)

### ● PersonModel

![pERSONMODEL](https://user-images.githubusercontent.com/80118008/130611286-90df9d37-f40c-47f8-bfdc-bdfc19f637cc.PNG)


### ● RedisOperations

I will be calling everyting in one method called DoSome() becasue its roughly easier.

I first create a string called conenctionString which is equal to the redis connection string,
Cratea a ConnectionMultiplexer instance called redis ,
using the Connect function and it should be equal to the connection string.
Create Idatabase instance called dbredis which is getting the database.
And now for me to get the Mongo data base I create an MongoDBCRUD instance called db which will implement the "table" name(from ctor) which is the database name
in the case "Address_Book".

![redisclass0](https://user-images.githubusercontent.com/80118008/130612366-6182ffe0-9434-49b7-942b-5454f5d8ba7d.PNG)

I also created a Random instance for the user id.


I create an instance from PersonModel called p and set the information.the Id is a [BsonId] which is declared inside the PersonModel class and it will be equal to the randomator variable that i made.so the random number should be the id number of the new inserted record and should be dispalyed on both MongoDB and Redis.

![redisclass2](https://user-images.githubusercontent.com/80118008/130612744-4dcb1f5e-6914-4a33-8f0a-0feaa22c1354.PNG)

I insert the record by calling the InserRecord function which is used by the db instance I created from MongoDBCRUD, and the "table" name in this case is users (collection name) and the value which is the instance p where i setted all the information.
I insert the record into Redis by calling StringSet function whic is used by dbredis instance that I created from Idabase interface which is getting the redis db.
![ir](https://user-images.githubusercontent.com/80118008/130612803-04dea1bb-f4d2-492b-9735-97ec571b7265.png)

So the key is to the collection name "users" adding before the recordKey(randomator_) so I could find easily the key by the id number, and I insert the records of p instance.

#### (Full Function Page)

![redisclass1](https://user-images.githubusercontent.com/80118008/130612865-5161e196-1eae-47e8-992c-1b079479721c.PNG)






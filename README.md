# KVStore
A file based key value store made in java


#### How to use?

###### Step 1:
After creating a new class and importing the kvstore(or you can use the EndUser class that I have created in the default package).
Create a KVStore object.

`KVStore obj = new KVStore();`

###### Step 2:
Initialise JSON object with the json value you want.
This initialisation might throw JSONException,so you might have to deal with that.
After creating the JSON object,you can now call the methods that you want(Create,Read,Delete)

```
try {
JSONObject j1 = new JSONObject("{\"name\":\"John\", \"age\":30, \"car\":null }");

obj.create("John" , j1 , 10) // or obj.create("John" , j1);
}
```
__________________

    
### Methods
#### Create
The create function in the KVStore takes either 2 or 3 arguments.

`create(String key , JSONObject value)`

`create(String key , JSONObject value , long TimeToLive)`

If you create include the TimeToLive value while creation,then the created entry will be deleted after TTL seconds.

#### Read
The read function in the KVStore takes either 1 argument.

`read(String key)`

This will return the JSON value stored to the corresponding key.


#### Delete
The delete function in the KVStore takes either 1 argument.

`delete(String key)`

This will delete the key-value pair from the storage.

_____________________






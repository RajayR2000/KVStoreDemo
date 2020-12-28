# KVStore
A file based key value store made in java

The data store will support the following **functional** requirements:

1. It can be initialized using an optional file path. If one is not provided, it will reliably create itself in a reasonable location on the laptop
2. A new key-value pair can be added to the data store using the Create operation. The key is always a string - capped at 32chars. The value is always a JSON object-capped at 16KB.
3. If Create is invoked for an existing key, an appropriate error must be returned.
4. A Read operation on a key can be performed by providing the key, and receiving the value in response, as a JSON object.
5. A Delete operation can be performed by providing the key.
6. Every key supports setting a Time-To-Live property when it is created. This property is optional. If provided, it will be evaluated as an integer defining the number of seconds the key must be retained in the data store. Once the Time-To-Live for a key has expired, the key will no longer be available for Read or Delete operations,
7.Appropriate error responses must always be returned to a client if it uses the data store in unexpected ways or breaches any limits.


The data store will also support the following **non-functional** requirements:

1. The size of the file storing data must never exceed 1GB.
2. More than one client process cannot be allowed to use the same file as a data store at any given time
3. A client process is allowed to access the data store using multiple threads, if it desires to The data store must therefore be thread-safe.
The client will bear as little memory costs as possible to use this data store, while deriving maximum performance with respect to response times for accessing the data store.
__________________________________________

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

### Time-To-Live

The TTL property can be satisfied with the help of the **schedule()** function of the Timer class.

It takes two arguments.

`schedule(task to be performed , time after which the task is to be performed in milliseconds)`
The task to be performed can be mentioned by over-riding run() of the TimerTask.

For example:  ` schedule(task , 1000)` 

Here the mentioned task is performed after 1 second.

Code 
```
public class ClassName extends TimerTask
{
    @Override
    public void run() {
        //TASK
    }

}
```

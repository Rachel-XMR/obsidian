---
LINK:
  - "[[NoSQL]]"
---

# connecting to MongoDB from Python

![](PICTURE/NoSQL%20Database%20Programming%20with%20Python/9c062ba0a8faac5a5f32245abf82af9f_MD5.jpeg)


## install pymongo + dnspython

```python
pip install pymongo
pip install dnspython
```

### dnspython
將python連接到MongoDB Atlas 
將允許使用MongoDB srv URI

## 
```python
import pymongodb
from pymogodb import MongoClient

conn_str = "mongodb+srv://<username>:<password>@<cluster-name>.mongodb.net/myFirstDatabase"
client = MongoClient(conn_str,serverSelectionTimeoutMS=5000)
try:
	print(client.server_info())
	#print("connected to Server")
except Exception:
	print("Unable to connect to the server.")
```

# Performing CRUD Operations in MongoDB Using python

Databases and collections in MongoDB are *created* **lazily**,  meaning none of the commands relating to creating databases and collections performs any operations on the MongoDB server until when the first document is inserted into them

## Basic CRUD Operations in MongoDB Using python

```python
myDB = client["OnlineStore"] #名為OnlineStore的數據庫為對象
myCollection = myDB["phones.items"] #向數據庫中的phones,items集合中插入一個文檔
item_1 = { #item內容
"_id" : "U1IT00007",
"item_name" : "iPhone 13",
"max_discount" : "10%",
"batch_number" : "RR450020FRG",
"price" : 1280,
"category" : "electronic"
}
myCollection.insert_one(item_1) #插入到collection中
print(myCollection.inserted_id)

```


multiple document
```python
#inserting multiple documents
item_2 = {
"_id" : "U1IT00010",
"item_name" : ”Samsong Note 5",
"max_discount" : "5%",
"batch_number" : "RR45054FSR",
"price" : 480,
"category" : ”Electronic"
}
item_3 = {
"_id" : "U1IT00020",
"item_name" : ”Nokia X",
"max_discount" : "10%",
"batch_number" : "RR450020FRG",
"price" : 1280,
"category" : ”Electronic"
}
item_4 = {
"_id" : "U1IT00021",
"item_name" : ”Sony Xperia",
"max_discount" : "10%",
"batch_number" : "RR450020FRG",
"price" : 720,
"category" : "Electronic"
}
. . . .
new_items = [item_2, item_3, item_4, item_5]
myDB = client['OnlineStore']
myCollection = myDB['phones.items']
myCollection.insert_many(new_items)
```















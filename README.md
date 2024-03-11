# MongoDB Task Day - 1 

`This Repository contains a Document file.`  

## <h2 align="left">Programming Language Used :</h2>

<div align="left">
  <img src="https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white" height="40" alt="mongod logo"  />
  <img width="40" />
  </div>


## <h2 align="left">Programming Tool Used :</h2>

<div align="left">
  <img src="https://www.svgrepo.com/show/303232/mongodb-logo.svg" height="100" alt="mongodb logo"  />
  <img width="50" />
  </div>

## Execution of 10 Questions :

**Executed Queries for each Questions**

1. Find all the information about each products

```bash
db.Products.find();
```

2. Find the product price which are between 400 to 800

```bash
db.Products.find({‘product_price’:{$gte:400,$lte:800}});
```

3. Find the product price which are not between 400 to 600

```bash
db.Products.find({‘product_price’:{$not:{$gte:400,$lte:600}}});
```

4. List the four product which are grater than 500 in price

```bash
db.Products.find({‘product_price’:{$gt:500}}).limit(4);
```

5. Find the product name and product material of each products

```bash
db.Products.find({},{‘product_name’:1,’product_material’:1});
```

6. Find the product with a row id of 10

```bash
db.Products.find ({'id':'10'});
```

7. Find only the product name and product material

```bash
db.Products.find ({},{'_id':0,'id':0,'product_price':0,'product_color':0});
```

8. Find all products which contain the value of soft in product material

```bash
db.Products.find ({'product_material':'Soft'});
```

9. Find products which contain product color indigo and product price 492.00

```bash
db.Products.find ({$and:[{'product_color':'indigo'},{'product_price':492}]});
```

10. Delete the products which product price value are same

```bash
db.Products.aggregate([ 
                        {$group: {_id:'$product_price',count:{$sum:1}}},
                        {$match:{count:{$gt:1}}} 
                      ]).forEach((e)=>{ db.Products.deleteMany ({ product_price: e._id });});

```
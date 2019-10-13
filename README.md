# MongoDB Course

## 00. Intro

### Requirements

Basic knowledge in subjects:
1. Relational databases
1. SQL
1. JavaScript
1. JSON data format

To perform the exercises:
1. Install [MongoDB Community Server](https://www.mongodb.com/download-center/community)
1. Install [Robo 3T client](https://robomongo.org/download)
1. Download and import example [companies dataset](https://raw.githubusercontent.com/lsolilo/course-mongodb/master/data/companies.json)

### Presentation

Presentation slides can be found [here](http://htmlpreview.github.io/?https://github.com/lsolilo/course-mongodb/blob/master/slides/00-intro.html).

## 01. Basic Queries

### Accessing all data in collection
```javascript
db.getCollection('companies').find({})
```
or:
```javascript
db.companies.find({})
```

SQL equivalent:
```sql
SELECT * FROM companies
```

### Simple filtering by a field

```javascript
db.getCollection('companies').find({phone_number:'206.219.0537'})
```
or
```javascript
db.getCollection('companies').find({'phone_number':'206.219.0537'})
```

SQL equivalent:
```sql
SELECT * FROM companies WHERE phone_number = '206.219.0537'
```

### Retrieving specified fields from collection

```javascript
db.getCollection('companies').find({phone_number:'206.219.0537'}, {name:1, phone_number:1})
```

SQL equivalent:
```sql
SELECT name, phone_number FROM companies WHERE phone_number = '206.219.0537'
```
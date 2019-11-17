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

Presentation slides can be found [here](https://lsolilo.github.io/slides/mongodb-00-intro.html).

## 01. Basic Queries

### Accessing all data in collection

Retrieve all companies:

```javascript
db.getCollection('companies').find({})
//or
db.companies.find({})
```

SQL equivalent:
```sql
SELECT * FROM companies
```

### Simple filtering by a field

Find company/companies with phone number _206.219.0537_:

```javascript
db.getCollection('companies').find({phone_number:'206.219.0537'})
//or
db.getCollection('companies').find({'phone_number':'206.219.0537'})
```

SQL equivalent:
```sql
SELECT * FROM companies WHERE phone_number = '206.219.0537'
```

### Retrieving specified fields from collection

Find companies with phone number _206.219.0537_, but return only company name and phone number:

```javascript
db.getCollection('companies').find({phone_number:'206.219.0537'}, {name:1, phone_number:1})
//and to hide the document identifier:
db.getCollection('companies').find({phone_number:'206.219.0537'}, {_id:0, name:1, phone_number:1})
```

SQL equivalent:
```sql
SELECT _id, name, phone_number FROM companies WHERE phone_number = '206.219.0537'
```

### Filtering by multiple fields

Find companies founded in May 2008:

```javascript
db.getCollection('companies').find({founded_year:2008, founded_month:2})
```

SQL equivalent:
```sql
SELECT * FROM companies WHERE founded_year = 2008 AND founded_month = 2
```

### Counting elements

Find how many companies were founded in 2008:

```javascript
db.getCollection('companies').find({founded_year:2008}).count()
```

SQL equivalent:
```sql
SELECT COUNT(*) FROM companies WHERE founded_year = 2008
```

### Comparisons

```javascript
db.getCollection('companies').find({founded_year:{$gte:2010}})
```

### Sorting elements

```javascript
db.getCollection('companies').find({founded_year:{$gte:2010}}, {founded_year:1, founded_month:1}).sort({founded_year:1, founded_month:1})
```
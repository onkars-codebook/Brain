
### 1. The Mongo Shell

```javascript
// Start the Mongo Shell
mongo

// List all databases
show dbs

// Switch to a database (or create it)
use myDatabase

// View collections in the database
show collections
```

### 2. How We Store Data (BSON)

```javascript
// BSON Example (JSON-like document)
{
  "_id": ObjectId("507f1f77bcf86cd799439011"),
  "name": "Alice",
  "age": 25,
  "hobbies": ["reading", "gaming"]
}
```
## 3. Document & Collection

```javascript
// Insert a document into a collection
db.users.insertOne({ name: "Alice", age: 25, hobbies: ["reading", "gaming"] });

// Find documents in a collection
db.users.find();
```

## 4. INSERT in DB (InsertOne)

```javascript
db.users.insertOne({ name: "Bob", age: 30 });
```

## 5. INSERT in DB (InsertMany)

```javascript
db.users.insertMany([
  { name: "Charlie", age: 28 },
  { name: "Diana", age: 22 }
]);
```

## 6. FIND in DB

```javascript
// Find all documents
db.users.find();

// Find documents with a specific condition
db.users.find({ age: { $gt: 25 } });
```

## 7. Query Operators

```javascript
// Find users aged 25 or above
db.users.find({ age: { $gte: 25 } });

// Find users with specific hobbies
db.users.find({ hobbies: "reading" });
```

## 8. UPDATE in DB

```javascript
// Update a single document
db.users.updateOne({ name: "Alice" }, { $set: { age: 26 } });

// Update multiple documents
db.users.updateMany({}, { $set: { active: true } });
```

## 9. Nesting

```javascript
// Insert a nested document
db.orders.insertOne({
  orderId: 1,
  customer: { name: "Alice", email: "alice@example.com" },
  items: [{ product: "Book", quantity: 2 }, { product: "Pen", quantity: 5 }]
});

// Query a nested field
db.orders.find({ "customer.name": "Alice" });
```

## 10. DELETE in DB

```javascript
// Delete a single document
db.users.deleteOne({ name: "Charlie" });

// Delete multiple documents
db.users.deleteMany({ age: { $lt: 25 } });
```


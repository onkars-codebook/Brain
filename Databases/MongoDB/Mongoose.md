## 1. Installation & Setup

```bash
# Install MongoDB (Linux Example)
sudo apt update
sudo apt install -y mongodb

# Start MongoDB service
sudo systemctl start mongodb
```

## 2. Schema

```javascript
// Define a schema in Mongoose
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
  hobbies: [String]
});
```

## 3. Models

```javascript
// Create a model in Mongoose
const User = mongoose.model('User', userSchema);

// Use the model to interact with the database
const user = new User({ name: "Eve", age: 29, hobbies: ["cooking"] });
user.save();
```

## 4. Insert in Mongoose

```javascript
User.create({ name: "Frank", age: 35, hobbies: ["cycling"] });
```

## 5. Insert Multiple

```javascript
User.insertMany([
  { name: "Grace", age: 20 },
  { name: "Hank", age: 40 }
]);
```


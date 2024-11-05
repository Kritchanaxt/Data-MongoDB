# Data-MongoDB

### 1. สร้างและลบฐานข้อมูล
- **สร้างฐานข้อมูล**: ใช้คำสั่ง `use` เพื่อเลือกหรือสร้างฐานข้อมูลใหม่
- **ลบฐานข้อมูล**: คำสั่ง `db.dropDatabase()` จะลบฐานข้อมูลปัจจุบันพร้อมข้อมูลทั้งหมด

### 2. เพิ่ม Document
- ใช้คำสั่ง `insertOne` เพิ่มเอกสารเดียว และ `insertMany` เพิ่มหลายรายการในคอลเลกชัน

### 3. เพิ่ม Document แบบ Array & Object
- **Array**: เก็บข้อมูลหลายค่าในฟิลด์เดียว
- **Object**: เก็บข้อมูลหลายฟิลด์ในรูปแบบ JSON ภายในฟิลด์

### 4. สอบถามข้อมูล
- **ค้นหาทั้งหมด**: `find()` ดึงเอกสารทั้งหมดในคอลเลกชัน
- **แบบเงื่อนไข**: กำหนดเงื่อนไขการค้นหา เช่น `{ age: { $gt: 20 } }`

### 5. ตัวดำเนินการเปรียบเทียบและตรรกศาสตร์
- ใช้ `$gt`, `$lt` สำหรับเปรียบเทียบค่า และ `$and`, `$or` สำหรับเงื่อนไขหลายแบบ

### 6. อัพเดทและลบ Document
- ใช้ `updateOne` และ `deleteMany` เพื่อปรับปรุงหรือลบเอกสารตามเงื่อนไขที่กำหนด

### 7. Aggregation Pipeline
- ใช้ `aggregate` เพื่อจัดการข้อมูล เช่น การกรอง, การจัดกลุ่ม, และการนับ

### 8. เชื่อม Collection
- `$lookup`: ดึงข้อมูลที่สัมพันธ์จากคอลเลกชันอื่น


# ตัวอย่างและวิธีใช้งาน
## 1.สร้างและลบฐานข้อมูล
- ### สร้าง:
  ```javascript
  use myDatabase
  ```
- ### ลบ:
  ```javascript
  db.dropDatabase()
  ```

## 2.เพิ่ม Document (insert)
- ### เพิ่มรายการเดียว:
  ```javascript
  db.users.insertOne({ name: "Alice", age: 25 })
  ```
- ### เพิ่มหลายรายการ:
  ```javascript
  db.users.insertMany([{ name: "Bob", age: 30 }, { name: "Carol", age: 22 }])
  ```
- ### เพิ่ม Array:
  ```javascript
  db.orders.insertOne({ items: ["pen", "notebook"], total: 15.5 })
  ```
- ### เพิ่ม Object:
  ```javascript
  db.products.insertOne({ name: "Laptop", specs: { RAM: "16GB", storage: "512GB SSD" } })
  ```

## 3.สอบถามข้อมูล
- **ทั้งหมด**:
  ```javascript
  db.users.find()
  ```
- **แบบเงื่อนไขเดียว**:
  ```javascript
  db.users.find({ age: { $gt: 20 } })
  ```
- **2 เงื่อนไข**:
  ```javascript
  db.users.find({ $and: [{ age: { $gt: 20 } }, { name: "Alice" }] })
  ```
- **Object**:
  ```javascript
  db.products.find({ specs: { RAM: "16GB" } })
  ```
- **Array**:
  ```javascript
  db.orders.find({ items: "pen" })
  ```

## 4.ตัวดำเนินการเปรียบเทียบและตรรกศาสตร์
- **เปรียบเทียบ**:
  ```javascript
  db.users.find({ age: { $gt: 20, $lt: 30 } })
  ```
- **In และ Not In**:
  ```javascript
  db.users.find({ name: { $in: ["Alice", "Bob"] } })
  db.users.find({ name: { $nin: ["Alice", "Bob"] } })
  ```
- **ตรรกศาสตร์**:
  ```javascript
  db.users.find({ $or: [{ age: { $lt: 25 } }, { name: "Carol" }] })
  ```

## 5.อัพเดทและลบ Document
- **อัพเดทรายการเดียว**:
  ```javascript
  db.users.updateOne({ name: "Alice" }, { $set: { age: 26 } })
  ```
- **หลายรายการ**:
  ```javascript
  db.users.updateMany({ age: { $lt: 25 } }, { $set: { isActive: true } })
  ```
- **ลบรายการเดียว**:
  ```javascript
  db.users.deleteOne({ name: "Bob" })
  ```
- **ลบหลายรายการ**:
  ```javascript
  db.users.deleteMany({ age: { $gt: 30 } })
  ```

## 6.Aggregation และ Pipeline
- **$project**:
  ```javascript
  db.users.aggregate([{ $project: { name: 1, age: 1 } }])
  ```
- **$match**:
  ```javascript
  db.users.aggregate([{ $match: { age: { $gt: 20 } } }])
  ```
- **$count**:
  ```javascript
  db.users.aggregate([{ $count: "totalUsers" }])
  ```
- **$sort**:
  ```javascript
  db.users.aggregate([{ $sort: { age: -1 } }])
  ```
- **$limit**:
  ```javascript
  db.users.aggregate([{ $limit: 5 }])
  ```
- **$skip**:
  ```javascript
  db.users.aggregate([{ $skip: 5 }])
  ```
- **$group**:
  ```javascript
  db.users.aggregate([{ $group: { _id: "$age", count: { $sum: 1 } } }])
  ```
- **$push และ $addToSet**:
  ```javascript
  db.orders.aggregate([{ $group: { _id: "$customerId", items: { $push: "$item" } } }])
  ```

## 7.เชื่อม Collection
- **$lookup**:
  ```javascript
  db.orders.aggregate([
    {
      $lookup: {
        from: "customers",
        localField: "customerId",
        foreignField: "_id",
        as: "customer_info"
      }
    }
  ])
  ```


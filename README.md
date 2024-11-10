# 📚 MongoDB
- #### `MongoDB` เหมาะกับโปรเจกต์ที่ต้องการจัดการข้อมูลขนาดใหญ่, ข้อมูลที่มีโครงสร้างยืดหยุ่น, การประมวลผลเรียลไทม์, ระบบ Microservices, และแอปพลิเคชันมือถือที่ต้องการซิงค์ข้อมูล เช่น ระบบ E-commerce, Social Media, CMS, IoT และ Real-Time Analytics 

## ❓คำอธิบายสำหรับคำสั่งต่าง ๆ
### 1. สร้างและลบฐานข้อมูล
- **สร้างฐานข้อมูล**: ใช้ `use <database_name>` เพื่อสร้างหรือเลือกฐานข้อมูล
- **ลบฐานข้อมูล**: ใช้ `db.dropDatabase()` เพื่อลบฐานข้อมูลปัจจุบัน

### 2. เพิ่ม Document
- **เพิ่ม Document (insert)**:
  - ใช้ `insertOne()` เพื่อเพิ่มเอกสารเดียว
  - ใช้ `insertMany()` เพื่อเพิ่มหลายเอกสารในคอลเลกชัน

### 3. เพิ่ม Document Array & Object
- **เพิ่ม Document แบบ Array**: ใช้ `insertOne()` โดยให้ฟิลด์หนึ่งเป็น Array
- **เพิ่ม Document แบบ Object**: ใช้ `insertOne()` โดยให้ฟิลด์หนึ่งเป็น Object ที่มีหลายฟิลด์

### 4. สอบถามข้อมูล
- **find, findOne**:
  - ใช้ `find()` เพื่อค้นหาทุกเอกสารในคอลเลกชัน
  - ใช้ `findOne()` เพื่อค้นหาเอกสารแรกที่ตรงกับเงื่อนไข

### 5. สอบถามข้อมูลแบบเงื่อนไข
- **แบบเงื่อนไขเดียว**: กำหนดเงื่อนไขการค้นหา เช่น `{ age: { $gt: 20 } }`
- **แบบ 2 เงื่อนไข**: ใช้ `$and` หรือ `$or` เพื่อรวมเงื่อนไขหลายข้อ

### 6. สอบถามข้อมูลแบบ Object & Array
- **Object**: ใช้ `find()` โดยระบุฟิลด์ที่เป็น Object
- **Array**: ใช้ `find()` โดยระบุฟิลด์ที่เป็น Array

### 7. ตัวดำเนินการเปรียบเทียบ
- ใช้ตัวดำเนินการ เช่น `$gt`, `$lt`, `$eq` เพื่อตรวจสอบค่า

### 8. In และ Not In
- **In**: ใช้ `$in` เพื่อค้นหาเอกสารที่มีค่าตรงตามที่กำหนด
- **Not In**: ใช้ `$nin` เพื่อค้นหาเอกสารที่ไม่มีค่าตรงตามที่กำหนด

### 9. ตัวดำเนินการตรรกศาสตร์
- ใช้ `$and`, `$or`, และ `$not` เพื่อรวมเงื่อนไข

### 10. อัพเดท Document
- **รายการเดียว**: ใช้ `updateOne()` เพื่อลงทะเบียนการอัพเดทเอกสารหนึ่งรายการ
- **หลายรายการ**: ใช้ `updateMany()` เพื่ออัพเดทเอกสารหลายรายการ

### 11. ลบ Document
- **ลบรายการเดียว**: ใช้ `deleteOne()` เพื่อลบเอกสารหนึ่งรายการ
- **ลบหลายรายการ**: ใช้ `deleteMany()` เพื่อลบเอกสารหลายรายการตามเงื่อนไข

### 12. Aggregation และ Pipeline
- **Aggregation**: ใช้ `aggregate()` เพื่อทำการประมวลผลข้อมูลแบบรวม เช่น การกรอง การนับ
- **Pipeline**: ใช้ `$match`, `$group`, `$sort`, ฯลฯ ใน Pipeline เพื่อจัดการข้อมูลตามขั้นตอน

### 13. การสอบถามข้อมูลด้วย $project
- ใช้ `$project` เพื่อเลือกเฉพาะฟิลด์ที่ต้องการในผลลัพธ์

### 14. การสอบถามข้อมูลด้วย $match
- ใช้ `$match` เพื่อกรองเอกสารตามเงื่อนไขที่กำหนดใน Pipeline

### 15. การนับจำนวนด้วย $count
- ใช้ `$count` เพื่อคำนวณจำนวนเอกสารที่ตรงตามเงื่อนไข

### 16. การเรียงลำดับด้วย $sort
- ใช้ `$sort` เพื่อเรียงลำดับผลลัพธ์ตามฟิลด์ที่กำหนด

### 17. การจำกัดข้อมูลด้วย $limit
- ใช้ `$limit` เพื่อจำกัดจำนวนเอกสารที่ส่งกลับในผลลัพธ์

### 18. การข้าม Document ด้วย $skip
- ใช้ `$skip` เพื่อข้ามเอกสารจำนวนที่กำหนดในผลลัพธ์

### 19. การจัดการข้อมูลด้วย $group
- ใช้ `$group` เพื่อจัดกลุ่มเอกสารตามฟิลด์ที่กำหนดและคำนวณค่าต่าง ๆ

### 20. การเพิ่มข้อมูลกลุ่มด้วย $push และ $addToSet
- **$push**: เพิ่มค่าลงใน Array
- **$addToSet**: เพิ่มค่าเฉพาะที่ไม่ซ้ำกันลงใน Array

### 21. การเชื่อม Collection ด้วย $lookup
- ใช้ `$lookup` เพื่อเชื่อมข้อมูลจากคอลเลกชันอื่นในผลลัพธ์


## 🪀 ตัวอย่างและวิธีใช้งาน 
### 1.สร้างและลบฐานข้อมูล
- #### สร้างฐานข้อมูล:
  ```javascript
  use myDatabase
  ```
- ### ลบฐานข้อมูล:
  ```javascript
  db.dropDatabase()
  ```

### 2.เพิ่ม Document (insert)
- #### เพิ่มรายการเดียว:
  ```javascript
  db.users.insertOne({ name: "Alice", age: 25 })
  ```
- #### เพิ่มหลายรายการ:
  ```javascript
  db.users.insertMany([{ name: "Bob", age: 30 }, { name: "Carol", age: 22 }])
  ```
- #### เพิ่ม Array:
  ```javascript
  db.orders.insertOne({ items: ["pen", "notebook"], total: 15.5 })
  ```
- #### เพิ่ม Object:
  ```javascript
  db.products.insertOne({ name: "Laptop", specs: { RAM: "16GB", storage: "512GB SSD" } })
  ```

### 3.สอบถามข้อมูล
- #### ทั้งหมด:
  ```javascript
  db.users.find()
  ```
- #### แบบเงื่อนไขเดียว:
  ```javascript
  db.users.find({ age: { $gt: 20 } })
  ```
- #### 2 เงื่อนไข:
  ```javascript
  db.users.find({ $and: [{ age: { $gt: 20 } }, { name: "Alice" }] })
  ```
- #### Object:
  ```javascript
  db.employees.find({"general.gender":"man"})
  ```
- #### Array:
  ```javascript
  db.employees.find({"social":["facebook","line"]})
  ```

### 4.ตัวดำเนินการเปรียบเทียบและตรรกศาสตร์
- #### เปรียบเทียบ:
  ```javascript
  db.users.find({ age: { $gt: 20, $lt: 30 } })
  ```
- #### In และ Not In:
  ```javascript
  db.users.find({ name: { $in: ["Alice", "Bob"] } })
  db.users.find({ name: { $nin: ["Alice", "Bob"] } })
  ```
- #### ตรรกศาสตร์:
  ```javascript
  db.users.find({ $or: [{ age: { $lt: 25 } }, { name: "Carol" }] })
  ```

### 5.อัพเดทและลบ Document
- #### อัพเดทรายการเดียว:
  ```javascript
  db.users.updateOne({ name: "Alice" }, { $set: { age: 26 } })
  ```
- #### หลายรายการ:
  ```javascript
  db.users.updateMany({ age: { $lt: 25 } }, { $set: { isActive: true } })
  ```
- #### ลบรายการเดียว:
  ```javascript
  db.users.deleteOne({ name: "Bob" })
  ```
- #### ลบหลายรายการ:
  ```javascript
  db.users.deleteMany({ age: { $gt: 30 } })
  ```

### 6.Aggregation และ Pipeline
- #### $project:
  ```javascript
  db.users.aggregate([{ $project: { name: 1, age: 1 } }])
  ```
- #### $match:
  ```javascript
  db.users.aggregate([{ $match: { age: { $gt: 20 } } }])
  ```
- #### $count:
  ```javascript
  db.users.aggregate([{ $count: "totalUsers" }])
  ```
- #### $sort:
  ```javascript
  db.users.aggregate([{ $sort: { age: -1 } }])
  ```
- #### $limit:
  ```javascript
  db.users.aggregate([{ $limit: 5 }])
  ```
- #### $skip:
  ```javascript
  db.users.aggregate([{ $skip: 5 }])
  ```
- #### $group:
  ```javascript
  db.users.aggregate([{ $group: { _id: "$age", count: { $sum: 1 } } }])
  ```
- #### $push และ $addToSet:
  ```javascript
  db.orders.aggregate([{ $group: { _id: "$customerId", items: { $push: "$item" } } }])
  ```

### 7.เชื่อม Collection
- #### $lookup:
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
## 📗 MongoDB Atlas
- #### คือบริการฐานข้อมูลแบบคลาวด์ที่บริหารจัดการโดย `MongoDB` ซึ่งช่วยให้คุณสามารถใช้ `MongoDB` บนคลาวด์ได้โดยไม่ต้องดูแลการตั้งค่าและการจัดการเซิร์ฟเวอร์เอง `MongoDB Atlas` รองรับการทำงานบนแพลตฟอร์มคลาวด์หลายที่ เช่น **AWS, Google Cloud Platform (GCP)** และ **Microsoft Azure** โดยมุ่งเน้นให้ผู้ใช้งานสามารถใช้งานฐานข้อมูลได้สะดวกและปลอดภัยยิ่งขึ้น

### ข้อดีของ MongoDB Atlas:
1. **การจัดการอัตโนมัติ**: Atlas จัดการการสำรองข้อมูล, การสเกล, การรักษาความปลอดภัย, และการอัปเดตซอฟต์แวร์ให้โดยอัตโนมัติ
2. **การสำรองข้อมูลและความปลอดภัยสูง**: รองรับการเข้ารหัสข้อมูลทั้งระหว่างการส่งผ่านและที่เก็บในฐานข้อมูล รวมถึงการสำรองข้อมูลอัตโนมัติและการกู้คืนข้อมูล
3. **สเกลได้ง่าย**: สามารถเพิ่มลดขนาดของฐานข้อมูลได้ง่าย ทำให้เหมาะสำหรับการใช้งานทั้งขนาดเล็กและขนาดใหญ่
4. **สนับสนุนการทำงานแบบกระจายข้อมูล (Global Clusters)**: ทำให้ข้อมูลอยู่ใกล้กับผู้ใช้มากขึ้น ลดความล่าช้า และเพิ่มประสิทธิภาพในการเข้าถึงข้อมูล
5. **การใช้งานง่าย**: มี UI ที่ใช้งานง่าย และสามารถจัดการผ่าน MongoDB Compass หรือเครื่องมือเชื่อมต่อ MongoDB ต่างๆ ได้

### ฟีเจอร์ที่น่าสนใจ:
- **Atlas Search**: สำหรับการค้นหาข้อมูลแบบ Full-text ในฐานข้อมูล
- **Atlas Data Lake**: สามารถจัดเก็บข้อมูลขนาดใหญ่ได้โดยการรวมข้อมูลจากหลายแหล่งข้อมูล
- **Atlas Triggers**: ช่วยในการสร้าง Trigger สำหรับกระบวนการอัตโนมัติ เช่น เรียกใช้งานฟังก์ชันเมื่อมีการเปลี่ยนแปลงข้อมูล
- **Realm Sync**: ซิงค์ข้อมูลแบบเรียลไทม์ระหว่าง MongoDB และแอปพลิเคชันมือถือ (เมื่อใช้ร่วมกับ Realm)

### การใช้งาน MongoDB Atlas
1. **สมัครบัญชี** ที่ [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. **สร้าง Cluster** เพื่อเริ่มใช้งานฐานข้อมูล
3. **เลือก Plan** ที่เหมาะกับความต้องการ เช่น Free Tier (M0) สำหรับเริ่มต้นเรียนรู้หรือโปรเจกต์ขนาดเล็ก
4. **ตั้งค่าการเชื่อมต่อ** และใช้งานฐานข้อมูลผ่าน MongoDB Compass, Atlas UI หรือเครื่องมืออื่นๆ

#### Atlas เหมาะสำหรับโปรเจกต์ที่ต้องการความสะดวกในการจัดการฐานข้อมูล หรือโปรเจกต์ขนาดใหญ่ที่ต้องการฐานข้อมูลที่สามารถขยายตัวและดูแลรักษาได้ง่าย

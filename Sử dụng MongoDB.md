# Sử dụng MongoDB
Dưới đây là một vài lệnh cơ bản về việc sử dụng MongoDB

1. Hiển thị tất cả Databases 
```
    show dbs
```
2. Tạo Database
```
    use DATABASENAME
```
Lưu ý : Nếu Database chưa tồn tại thì sẽ được tạo mới
3. Tạo Collection 
```
    db.createCollection("COLLECTIONNAME")
```
4. Insert dữ liệu vào Conllections
```
    db.COLLECTIONNAME.insert({'key_name': 'value'})
```
Lưu ý: Trong trường hợp colllection chưa tồn tại thì sẽ được tạo mới. Đây cũng là một cách tạo collections  
5. Lấy tất cả dữ liệu trong collections
```
    db.COLLECTIONNAME.find()
```
6. Lấy 1 dữ liệu trong 1 collection
```
    db.COLLECTIONNAME.findOne({filler})
```
7. Xóa một collections
```
    db.COLLECTIONNAME.drop()
```
8. Update dữ liệu trong collections
```
    db.COLLECTIONNAME.update({DK update},{Dữ liệu update})
```
9. Xóa dữ liệu trong collections
```
Xóa 1 dữ liệu trong collections

        db.collection.removeOne()

Xóa tất cả dữ liệu trong collections

        db.collection.remove()

Xóa nhiều dữ liệu theo bộ lọc

        db.collection.removeMany()
```
10. Tương tác Document trong collections
 - Xóa 1 trường trong Document
 ```
    delete collections.field
 ```


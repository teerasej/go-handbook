
# สร้างโปรเจค

## 1. สร้างโปรเจค

จากโฟลเดอร์ที่ต้องการ ให้รันคำสั่ง

```bash
revel new github.com/teerasej/go-revel-web-api
```

## 2. ตรวจเช็ค package ที่เกี่ยวข้อง

เข้าไปในโฟลเดอร์โปรเจค และรันคำสั่ง `go mod tidy` เพื่อให้ go เช็คความเรียบร้อยของโปรเจค

```
cd go-revel-web-api
go mod tidy
```

## 3. รัน Web Server

```
revel run .
```

จะมี Web server รันขึ้นมาที่ port 9000

### Note 

- หากต้องการกำหนด port ใหม่ ให้ไปแก้ไขในไฟล์ `conf/app.conf` 
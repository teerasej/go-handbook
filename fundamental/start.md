
# Getting Start

## 1. สร้าง module ไฟล์

้สร้าง โฟลเดอร์ `my-first-go` และเปิดขึ้นมาใน Visual Studio Code

รันคำสั่ง

```bash
go mod init github.com/teerasej/my-first-go
```

จะได้ไฟล์ชื่อ `go.mod` 

```
module github.com/teerasej/my-first-go

go 1.16
```

### Note

- สามารถเปลี่ยน `teerasej` เป็นชื่อ user ของ github ที่เราสมัครไว้ก็ได้ **มีผลตอน deploy หรือ share project อีกที**
- คำสั่ง `go mod init` เป็นการสร้างไฟล์ module สำหรับใช้จัดการโปรเจคของเรา


## 2. สร้างไฟล์ main

สร้างไฟล์ `main.go`

```go
package main

import (
	"fmt"
)

func main()  {
	fmt.Println("hello!")
}
```

จากนั้นใน terminal ใช้คำสั่งด้านล่าง เพื่อรันโค้ด go

```bash
go run .

# หรือ
go run main.go

# หรือ
go run github.com/teerasej/my-first-go
```

### Note

- สังเกตว่าถ้ามีการ import package มาใช้ แต่ไม่มีการเรียกใช้ package ดังกล่าวในไฟล์ **จะเกิด error ตอน compile**


## 3. build executable ไฟล์

จาก terminal ให้รันคำสั่ง

```bash
go build .

# หรือ
go build github.com/teerasej/my-first-go 
```

จะได้ไฟล์ executable สามารถทดสอบรันได้จาก Terminal 

```bash
# Windows
go-webservice.exe

# MacOS
./go-webservice
```

### Note

- การ build executble ไฟล์จะได้ไฟล์ตามระบบที่รัน เช่น Windows จะได้ **.exe** 
- ไม่สามารถ build ข้าม OS ได้ 
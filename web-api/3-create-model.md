
# สร้าง Model เพื่อเป็นตัวแทนของข้อมูล User

สร้างไฟล์ `user_model.go`

```go
package main

// ใช้ struct กำหนด UserData 
// มี Userid, Email, และ Password
type UserData struct {
	Userid   int
	Email    string
	Password string
}
```

## Note

- ชื่อ field ที่ขึ้นต้นด้วยตัวใหญ่จะถือเป็น public field สามารถเรียกใช้จากส่วนอื่นได้
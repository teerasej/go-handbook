
# สร้าง UserModel เป็นตัวแทนของข้อมูล JSON ข้อมูลจะถูกส่งเข้ามาทาง POST Request

สร้างไฟล์ `app/models/user.go`

```go
package models

type UserModel struct {
	Email    string
	Password string
}

```
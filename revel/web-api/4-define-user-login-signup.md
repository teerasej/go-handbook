
# สร้าง และกำหนด route สำหรับ user signup และ login

## 1. สร้าง User Controller

สร้างไฟล์ `user.go`

```go
// app/controllers/user.go

package controllers

import (
	"github.com/revel/revel"
)

type User struct {
	*revel.Controller
}

func (c User) Index() revel.Result {
	return c.RenderText("/users")
}

func (c User) Login() revel.Result {
	return c.RenderText("Login")
}

func (c User) SignUp() revel.Result {
	return c.RenderText("Sign up")
}

```

## 2. กำหนด route 

เปิดไฟล์ `conf/route` และเพิ่ม route path ที่เรียกใช้ function ที่เราสร้างไว้ใน `user.go`

```
GET     /users                                    User.Index
POST    /users/login                              User.Login
POST    /users/signup                             User.SignUp

```
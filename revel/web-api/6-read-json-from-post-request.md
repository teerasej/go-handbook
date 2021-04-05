
# อ่าน JSON จาก POST request และเก็บใน struct

```go
// app/controllers/user.go

package controllers

import (
    // เรียกใช้ models package ของโปรเจคเรา
	"go-revel-web-api/app/models"
    // เรียกใช้ http package
	"net/http"

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

    // สร้างตัวแปร struct
	var registerUser models.UserModel

    // อ่าน JSON จาก params ของ Controller 
	err := c.Params.BindJSON(&registerUser)
	if err != nil {
        // reponse Bad Request ถ้าอ่าน JSON ไม่ได้
		c.Response.SetStatus(http.StatusBadRequest)
		return c.RenderText("Error")
	}

    // คืน JSON ที่อ่านได้กลับไปที่ client
	return c.RenderJSON(registerUser)
}

```
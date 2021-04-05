
# สร้าง document ใหม่ใน collection โดยใช้ struct ที่กำหนด tag bson ไว้แล้ว

```go
// app/controllers/user.go

//... 

func (c User) SignUp() revel.Result {

	var registerUser models.UserModel

	err := c.Params.BindJSON(&registerUser)
	if err != nil {
		c.Response.SetStatus(http.StatusBadRequest)
		return c.RenderText("Error")
	}

    // ใช้ address ของ struct กำหนดใช้/สร้าง collection
    // และใช้ address ของ struct ในการสร้าง document ใหม่ใน database
    // ค่าที่ได้จากการสร้าง document ใหม่เช่น objectId จะถูกเขียนมาให้
	err = mgm.Coll(&registerUser).Create(&registerUser)
	if err != nil {
		c.Response.SetStatus(http.StatusInternalServerError)
		return c.RenderText("Internal Server  Error")
	}

	return c.RenderJSON(registerUser)
}

```
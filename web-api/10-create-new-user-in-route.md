
# เรียกใช้ mgm ในการสร้าง user ใหม่

```go
// route_user.go

case http.MethodPost:

    //...

    err = mgm.Coll(&newUser).Create(&newUser)
    if err != nil {
        w.WriteHeader(http.StatusInternalServerError)
        w.Write([]byte("cannot create new user"))
    }

    w.Header().Add("Content-Type", "application/json")
	w.Write([]byte(`{"message":"success"}`))


```

# กำหนดค่าเริ่มต้นให้ mgm ต่อ mongodb

```go
// app/controllers/user.go

package controllers

import (
	"go-revel-web-api/app/models"
	"net/http"

	"github.com/kamva/mgm/v3"
	"github.com/revel/revel"
	"go.mongodb.org/mongo-driver/mongo/options"
)

// กำหนด function เริ่มต้นของ package
func init() {
    // กำหนด ชื่อ database และ connection string 
	err := mgm.SetDefaultConfig(nil, "nextflow", options.Client().ApplyURI("mongodb://localhost:27017"))
	if err != nil {
        // ถ้าเกิดข้อผิดพลาดให้หยุดการทำงาน
		panic(err)
	}
}

//...

```
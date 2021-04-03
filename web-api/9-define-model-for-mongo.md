
# กำหนด struct ให้รองรับการทำงานกับ MongoDB และ MGM


```go
// user_model.go
package main

import (
	"github.com/kamva/mgm/v3"
)

// กำหนด DefaultModel จะเป็นการเพิ่ม field _id, created_at และ updated_at เข้ามาใน model 
// bson เป็นการกำหนด property ให้ document ใน mongoDB
type UserData struct {
	mgm.DefaultModel `bson:",inline"`
	Userid           int    `json:"id"`
	Email            string `json:"email" bson:"email"`
	Password         string `json:"password" bson:"password"`
}

```
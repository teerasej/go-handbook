
# กำหนด struct ให้รับการทำงานกับ mongo ด้วย bson

```go
// app/models/user.go
package models

import (
    // import เครื่องมือของ mgm
	"github.com/kamva/mgm/v3"
)

type UserModel struct {
    // กำหนด default field ของ document ใน mongo collection
	mgm.DefaultModel `bson:",inline"`
    // กำหนดชื่อ field ของ document ด้วย bson tag
	Email            string `json:"email" bson:"email"`
	Password         string `json:"password" bson:"password"`
}

```

# กำหนด route path และ Function จากที่โปรเจคสร้างให้


## 1. สร้าง function สำหรับให้ทำงานกับ Route path 

เปิดไฟล์ `app.go` และเพิ่มโค้ด function เข้าไปด้านล่าง

```go
// app/controllers/app.go

package controllers

import (
	"github.com/revel/revel"
)

type App struct {
    // ทุก struct ที่เป็น controller ต้องมีการกำหนด *revel.Controller เป็นบรรทัดแรก
	*revel.Controller
}

func (c App) Index() revel.Result {
	return c.Render()
}


// เพิ่ม function ApiHello ที่จะทำงานเมื่อมี request เข้ามาที่ GET /api
// คืนค่า response เป็น text
func (c App) ApiHello() revel.Result {
	return c.RenderText("Hello Revel")
}

```

## 2. กำหนด Route path เข้ากับ Controller function


เปิดไฟล์ `conf/route` และเพิ่ม HTTP Method และ Route path ที่จะเรียก controller ที่เราต้องการ

```
GET     /api                                    App.ApiHello
```
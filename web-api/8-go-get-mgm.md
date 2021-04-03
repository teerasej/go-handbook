
# ติดตั้ง และตั้งค่า mgm package

> ขั้นตอนนี้จำเป็นต้องมี MongoDB database server รันทำงานอยู่ที่ localhost port 27017

## 1. รันคำสั่งติดตั้ง package

```bash
go get github.com/kamva/mgm/v3
```

ไฟล์ `go.mod` จะมีการเพิ่ม package

```
module github.com/teerasej/go-web-api-mongo

go 1.16

require github.com/kamva/mgm/v3 v3.1.0 // indirect
```

## 2. กำหนดค่าเริ่มต้นให้ mgm 

```go
package main

import (
	"encoding/json"
	"fmt"
	"io/ioutil"
	"net/http"

    // เรียกใช้งาน mgm
	"github.com/kamva/mgm/v3"
	"go.mongodb.org/mongo-driver/mongo/options"
)

func init() {
	// ตั้งค่า mgm
    // ชื่อ database คือ nextflow
    // connection URI เป็น mongodb://localhost:27017
	err := mgm.SetDefaultConfig(nil, "nextflow", options.Client().ApplyURI("mongodb://localhost:27017"))
	if err != nil {
		panic(err)
	}
}

//...
```


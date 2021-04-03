
# แยกประเภท Method ของ Http Request 

```go
// route_user.go

package main

import (
	"encoding/json"
	"net/http"
)

func GetUsers(w http.ResponseWriter, r *http.Request) {

    // นำ field Method ของ Request มาพิจารณา
	switch r.Method {

    // ถ้า เป็น Method GET ให้คืนค่าเป็น JSON ปกติ
	case http.MethodGet:
		userResponse := UserData{
			Userid:   28566777,
			Email:    "training@nextflow.in.th",
			Password: "1234",
		}
		w.Header().Set("Content-Type", "application/json")
		json.NewEncoder(w).Encode(userResponse)
	}

}

```
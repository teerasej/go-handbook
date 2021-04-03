
# รับ Request แบบ POST Method และตอบกลับ

- เขียนส่วนของการรับ json จาก POST Request มาใช้
- เสร็จแล้วให้รันทดสอบ และส่ง JSON แบบ POST method ไปที่ `http://localhost:8080/users`

```json
// POST http://localhost:8080/users
{
    "email":"training@nextflow.in.th",
    "password":"1234"
}
```

## ไฟล์ route_user.go

```go
// route_user.go

package main

import (
	"encoding/json"
	"fmt"
    // "io/ioutil" ใช้ในการอ่านข้อมูลจาก Request
	"io/ioutil"
	"net/http"
)

func GetUsers(w http.ResponseWriter, r *http.Request) {

	switch r.Method {
	case http.MethodGet:
		userResponse := UserData{
			Userid:   28566777,
			Email:    "training@nextflow.in.th",
			Password: "1234",
		}
		w.Header().Set("Content-Type", "application/json")
		json.NewEncoder(w).Encode(userResponse)

    // เทีย http request แบบ POST Method
	case http.MethodPost:

        // สร้างตัวแปร UserData
		var newUser UserData

        // อ่านข้อมูลจาก Body ของ Request เพื่อให้ได้ JSON string
		bodyBytes, err := ioutil.ReadAll(r.Body)

        // ถ้าพบ err ให้กำหนด response ส่วน header เป็น bad request ส่งกลับ client
		if err != nil {
			w.WriteHeader(http.StatusBadRequest)
			w.Write([]byte("cannot read body"))
		}

        // แปลง JSON string ที่อ่านได้ใส่ไปที่ address ของ newUser
		err = json.Unmarshal(bodyBytes, &newUser)

        // ถ้าพบ err ให้กำหนด response ส่วน header เป็น bad request ส่งกลับ client
		if err != nil {
			w.WriteHeader(http.StatusBadRequest)
			w.Write([]byte("cannot parse JSON"))
		}

        // แสดงค่า newUser ใน Terminal 
		fmt.Println(newUser)

        // ส่ง json ตอบกลับ
		w.Header().Add("Content-Type", "application/json")
		w.Write([]byte(`{"message":"success"}`))
	}

}

```
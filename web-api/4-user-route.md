
# สร้าง Function สำหรับ Route `/users` แยกต่างหาก

## 1. สร้างไฟล์สำหรับ route users

```go
// route_user.go

package main

import (
	"encoding/json"
	"net/http"
)

// สร้าง function สำหรับนำไปใช้กับ http 
// สังเกตว่าตั้งชื่อขึ้นต้นตัวใหญ่ เพื่อให้สามารถเรียกใช้จากไฟล์อื่นได้
func GetUsers(w http.ResponseWriter, r *http.Request) {

    // ใช้ struct สร้างข้อมูลจำลอง
	userResponse := UserData{
		Userid:   28566777,
		Email:    "training@nextflow.in.th",
		Password: "1234", // หากต้องการกำหนดค่าลงใน struct แบบขึ้นบรรทัดใหม่ ให้ลงท้าย property สุดท้ายด้วย ","
	}

    // ใช้ json package เขียน json string ส่งกลับไปให้ client ผ่าน ResponseWriter
	json.NewEncoder(w).Encode(userResponse)
}

```

## 2. นำมาใช้กับ http ใน main.go


```go
// main.go
package main

import (
	"fmt"
	"net/http"
)

func users(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello World"))
}

func handleRequest() {
	http.HandleFunc("/", users)
	http.HandleFunc("/users", GetUsers)
	http.ListenAndServe(":8080", nil)
}

func main() {
	fmt.Println("Server is starting")
	fmt.Println("Server is runnin at port 8080")
    handleRequest()
    
}


```
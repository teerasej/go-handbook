
# สร้าง function สำหรับใช้เป็น Route รับ Request จาก Client 


1. แก้ไขไฟล์ `main.go` เพื่อสร้าง server และ route
2. หลังจากแก้เรียบร้อยแล้วให้ทดสอบรันโปรเจค
3. เปิด web browser หรือใช้ POSTMan ส่ง request ไปที่ GET http://localhost:8080/
4. ควรจะเห็นคำว่า **Hello World** แสดงบนหน้าจอ


```go
// main.go
package main

import (
	
	"fmt"
    // import package เพิ่ม
    "encoding/json"
	"net/http"
)

// สร้าง function ที่ชื่อว่า users
// รับค่าเป็น ResponseWriter สำหรับเขียน Response ส่งกลับ Client
// รับค่าเป็น pointer ของ request object
func users(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello World"))
}

func handleRequest() {
    // กำหนดเรียกใช้ function เมื่อมี request ส่งมาที่ route /
	http.HandleFunc("/", users)

    // กำหนดให้รัน server process ที่ localhost port 8080
	http.ListenAndServe(":8080", nil)
}

func main() {
	fmt.Println("Server is starting")
    fmt.Println("Server is running at port 8080")
    // รัน web server และแสดงข้อความใน terminal
    handleRequest()
    
}

```
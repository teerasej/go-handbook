
# สร้าง module ให้กับโปรเจคใหม่

1. จากโฟลเดอร์ของโปรเจค ให้รันคำสั่ง สร้าง `go.mod`

```bash
go mod init github.com/teerasej/go-web-api-mongo
```

2. สร้างไฟล์ `main.go`

```go
// main.go
package main

import "fmt"

func main() {
	fmt.Println("Server is starting")
}
```

3. ทดสอบรันไฟล์ go

```bash
go run .
```

ควรจะได้ข้อความด้านล่างแสดงขึ้นมาใน Terminal 

```
Server is starting
```
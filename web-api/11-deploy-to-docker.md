
# Deploy to Docker

## 1. สร้าง Dockerfile สำหรับจัดทำ Image 

สร้างไฟล์ชื่อ `Dockerfile` ไว้ในโฟลเดอร์โปรเจค

```dockerfile
FROM golang:alpine
RUN mkdir /app
COPY . /app
WORKDIR /app
RUN go build -o main . 

EXPOSE 8080
CMD ["/app/main"]
```

## 2. สร้าง Docker-compose.yaml สำหรับรันใช้งานกับ MongoDB

สร้างไฟล์ `docker-compose.yaml` ไว้ในโฟลเดอร์โปรเจค

```dockerfile
version: "2"
services: 
  web:
    environment:
      - MONGO_SERVER=mongo
    build: .
    ports:
      - "8080:8080"
    links:
      - mongo

  mongo:
      image: mongo
      ports:
        - "27017:27017"
```

กำหนดค่า mongo server ให้เช็คจาก environment ถ้าไม่มี environment `MONGO_SERVER` ให้ใช้ค่า `localhost` 

```go
// route_user.go

package main

import (
	"encoding/json"
	"fmt"
	"io/ioutil"
	"net/http"
	"os"

	"github.com/kamva/mgm/v3"
	"go.mongodb.org/mongo-driver/mongo/options"
)

func init() {

    // กำหนดค่า mongo server ถ้าไม่มี environment `MONGO_SERVER` ให้ใช้ค่า `localhost`
	var mongoServer = "localhost"

    // เช็คจาก environment  
	var envMongoServer = os.Getenv("MONGO_SERVER")

    // ถ้ามีการกำหนดค่า environment ชื่อ MONGO_SERVER ให้กำหนดลงไปใช้งาน
	if envMongoServer != "" {
		mongoServer = envMongoServer
	}

	err := mgm.SetDefaultConfig(nil, "nextflow", options.Client().ApplyURI("mongodb://"+mongoServer+":27017"))
	if err != nil {
		panic(err)
	}
}

// ...
```


## 3. รันไฟล์ docker compose

```bash
docker-compose up --build
```
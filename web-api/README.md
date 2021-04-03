
# สร้าง Web API ด้วย Go จาก 0

## First route

1. [สร้างโปรเจค](1-go-mod-and-main.md) 
2. [สร้าง function สำหรับใช้เป็น Route รับ Request จาก Client](2-create-route-for-helloworld.md) 

## ตอบกลับ Client เป็น JSON

3. [สร้าง Model เพื่อเป็นตัวแทนของข้อมูล User](2-create-model.md)
4. [สร้าง Function สำหรับ Route `/users` แยกต่างหาก](4-user-route.md)
5. [กำหนดชื่อ field ของ JSON property ใน struct](5-define-json-property-name.md)

## จัดการ Http Request

6. [แยกประเภท Method ของ Http Request](6-identify-http-method.md) 
7. [รับ Request แบบ POST Method และตอบกลับ](7-manage-post-method.md)

## เชื่อมต่อ MongoDB 

8. [ติดตั้ง mgm](8-go-get-mgm.md)
9. [กำหนด struct ให้รองรับการทำงานกับ MongoDB และ MGM](9-define-model-for-mongo.md)
10. [เรียกใช้ mgm ในการสร้าง user ใหม่](10-create-new-user-in-route.md)

## Deploy to Docker 

11. [Deploy to Docker](11-deploy-to-docker.md)

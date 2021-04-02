
# Pointer

- โดยปกติใน Go การส่งค่าตัวแปรเข้ามาใน Function จะเป็นการส่ง ค่าตัวแปรเข้ามาเป็นค่าเริ่มต้น (Pass by Value) ไม่ใช่ Pass by Reference ซึ่งอาจจะทำให้โปรแกรมเมอร์จากภาษาอื่น เข้าใจการทำงานนี้ผิดไป
- `&` เป็นการสร้าง address สำหรับ pointer ที่ชี้ไปที่ค่าตัวแปร (มองว่าเป็นการสร้างกุญแจก็ได้)
- `*` เป็นการเรียกข้อมูลออกมาจาก address pointer มองว่าเป็นการไขกุญแจก็ได้

## การแก้ไขที่เกิดขึ้นเฉพาะใน Function

ทดสอบรันโค้ดนี้ใน [Go Playground](https://play.golang.org/)

```go
package main

import (
 "fmt"
)

type User struct {
 Name string
 Pets []string
}

func (u User) newPet() {
 u.Pets = append(u.Pets, "Lucy")
 fmt.Println(u)
}

func main() {
 u := User{Name: "Anna", Pets: []string{"Bailey"}}
 u.newPet()     // {Anna [Bailey Lucy]} -- ค่าที่ User ถูก print ใน function มี Lucy เพิ่มขึ้นมาใน array
 fmt.Println(u)  // แต่ User ด้านนอกยังไม่มีการเพิ่มชื่อสัตว์เลี้ยงเข้ามา?!
}
```

## การใช้ส่ง Pointer ในการเข้าถึงข้อมูลจริงบน Pointer

ทดสอบรันโค้ดนี้ใน [Go Playground](https://play.golang.org/)

```go
package main

import (
 "fmt"
)

type User struct {
 Name string
 Pet  []string
}

// คราวนี้เราส่งเป็น pointer ของ struct User เข้ามา
// เราใช้ * เพื่อดึงค่า User ออกมาจาก address ที่ส่งเข้ามา
func (p2 *User) newPet() {
 fmt.Println(*p2, "underlying value of p2 before")
 p2.Pet = append(p2.Pet, "Lucy")
 fmt.Println(*p2, "underlying value of p2 after")
}

func main() {
u := User{Name: "Anna", Pet: []string{"Bailey"}} // this time we'll generate a pointer!
 fmt.Println(u, "u before")

p := &u // สร้าง pointer address ที่ชี้ไปที่ตัวแปร U ตอนนี้ตัวแปร p เก็บ address ของตัวแปร U ไว้

p.newPet() // ตอนเรียกใช้ function .newPet() เป็นการเรียกใช้ผ่าน address ของตัวแปร U
 fmt.Println(u, "u after")
}
```

## Note

- ในการเขียนใช้ pointer ในการทำงานแบบ Concurrency **ให้หลีกเลี่ยงการใช้ pointer** เพื่อป้องกันการทำงานที่คาดเดาไม่ได้จากการแก้ไขข้อมูลเดียวกัน จากหลายๆ การทำงาน
- ให้ใช้เทคนิค pass by value ที่ Go ทำเป็นค่าเริ่มต้นแทน
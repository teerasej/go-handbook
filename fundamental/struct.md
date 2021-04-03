
# Struct


## การประกาศ struct

```go
type User struct {

    // field และ data type ของ field
    name       string
    age        int
}
```

## สร้างตัวแปรจาก struct

ประกาศตัวแปรจาก struct โดยกำหนดค่า field เรียงตัว

```go
u := User{"John Doe", 34}
```

ประกาศแบบกำหนด field naming และกำหนดหลายบรรทัด

```go
u := User{
    name:   "John Doe",
    age:    34, 
}
```

## กำหนด function ให้ struct 

```go
package main

import "fmt"

type rect struct {
    width, height int
}

// กำหนดให้รับค่าจาก pointer ของ struct ชื่อ rect มาใช้งานใน function
func (r *rect) area() int {
    return r.width * r.height
}

// กำหนดให้รับค่าจาก value ของ struct ชื่อ rect มาใช้งานใน function
func (r rect) perim() int {
    return 2*r.width + 2*r.height
}

func main() {
    r := rect{width: 10, height: 5}

    fmt.Println("area: ", r.area())
    fmt.Println("perim:", r.perim())

    rp := &r
    fmt.Println("area: ", rp.area())
    fmt.Println("perim:", rp.perim())
}
```


## Struct constructor

หากต้องการสร้าง constructor function ให้ struct สามารถตั้งชื่อ function เป้น `new{ชื่อ struct}` ได้

```go
type User struct {
    name       string
    age        int
}

func newUser(name string, age int) *User {

    p := User{name, age}
    // constructor มักจะ return address ออกไปใช้งาน
    return &p
}
```
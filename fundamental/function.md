
# Function 

## ประกาศ function 

```go
// สร้าง function 
func startServer() {

}

// เรียกใช้ 
startServer() 
```

## ประกาศ parameter function 

```go
// กำหนด parameter function 
func plus(first int, second int) {
    fmt.Println(first + second)
}

// หรือถ้า parameter เป็น type เดียวกันก็ย่อได้แบบนี้ 
func plus(first, second int) {
    fmt.Println(first + second)
}

// เรียกใช้ 
plus(2,3) 
```

อีกตัวอย่างคือ parameter หลาก type

```go
func print(first, second int, name string) {
    fmt.Println(first, second, name)
}

print(1,2,"nextflow")
```

## กำหนด return type 

```go
// กำหนด return type
func plus(first, second int) int {
    return first + second
}

// เรียกใช้ 
fmt.Println(plus(2,3))
```

### กำหนด return type มากกว่า 1 ค่า 

```go
// กำหนด return type 2 ค่า 
func plus(first, second int) (int, error) {

    return first + second, nil
}

// เรียกใช้ 
result, err := plus(2,3)

// ถ้าต้องการ dump ค่าที่ได้ทิ้ง ให้ใช้ _
_, err := plus(2,3) 
// ส่วนนี้ค่า return แรกที่ส่งออกมาจากถูก dump ทิ้ง 
```
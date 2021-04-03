
# Array 

```go
// สร้าง array ที่เก็บ string ได้ 5 item
var products [5]string

// กำหนดค่าเริ่มต้นให้ Array
var ids = [5]int{1, 2, 3, 4, 5}

// แสดงความยาวของ Array 
fmt.Println(len(products))
```

## การเพิ่มค่าเข้าไปใน array

```go
var phones []string

// append()
phones = append(phones, "iPhone")
phones = append(phones, "Galaxy")

phones = append(phones, "P30", "Redmi Note")

fmt.Println(phones)
```

## การให้ Go กำหนด length ของ array 

```go
a := [...]int{3, 5, 7, 9, 11, 13, 17}

fmt.Println(a)
```

## การวนลูป item ใน array ด้วย `range`

```go
daysOfWeek := [7]string{"Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"}

// วนลูป ทีละ value ใน array โดยนับเลข index และ value 
for index, value := range daysOfWeek {
    fmt.Printf("Day %d of week = %s\n", index, value)
}
```
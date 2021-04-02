
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
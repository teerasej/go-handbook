
# Variable ใน Go

## Data Type ใน Go

```go
bool

string

int int8 int16 int32 int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // Represent unicode code point

float32 float64

complex64 complex128
```

## การประกาศตัวแปร

```go
var name string = "Hello, world"
fmt.Println(name)
```

หรือแบบนี้ก็ได้

```go
var name = "Hello, world"
```

หรือประกาศก่อนแล้ว กำหนดค่าที่หลังก็ได้

```go
var name string
name = "Nextflow"

var year int = 2022
year = 2021
```

เราสามารถประกาศตัวแปรประเภทเดียวกันในบรรทัดเดียวกันได้ เช่น 

```go
var index, counter int = 0, 10
// index มีค่า 0
// counter มีค่า 10 
```

## การประกาศตัวแปรแบบย่อ **ภายใน function**

ตัวแปรที่ประกาศใช้ใน function สามารถใช้สัญลักษณ์ `:=` ได้

```go
func main() {
	
    // แทนที่จะใช้ var k = 3 เราสามารถ...
	k := 3

	index, counter := 0, 10

    // และกสามารถกำหนด type แบบผสมได้
	c, python, java := true, false, "no!"

}
```

### การประกาศตัวแปรแบบย่อ **ภายนอก function**


```go
// นอก function ต้องใช้การประกาศแบบเต็ม
var counter = 0

func main() {
	
	k := 3

	c, python, java := true, false, "no!"

}
```
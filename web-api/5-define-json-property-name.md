
# กำหนดชื่อ field ของ JSON property ใน struct


เราสามารถกำหนด **tag** `json:"<property name>"` ให้กับแต่ละ field ใน struct ได้  

```go
package main

type UserData struct {
	Userid   int    `json:"id"`
	Email    string `json:"email"`
	Password string `json:"password"`
}
```

## Note

- tag ดังกล่าวจะถูกใช้โดย package `"encoding/json"` เช่น
  - `json.Marshal(userObject)` 
  - `json.NewEncoder(w).Encode(userResponse)` ใน[การ response JSON กลับไปหา client](4-user-route.md)
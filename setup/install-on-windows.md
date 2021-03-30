
# ติดตั้ง Go บน Windows

## 1. ติดตั้ง Go

1. [ดาวน์โหลดตัวติดตั้ง](https://golang.org/dl/)
2. ทำการติดตั้งให้เรียบร้อย

หลังจากติดตั้งเรียบร้อยแล้ว ให้ทดสอบรันคำสั่ง ใน Command Prompt/Powershell

```bash
go version
```

## 2. ตั้งค่า Workspace ของ Go ด้วย $GOPATH

หลังจากติดตั้งเรียบร้อยแล้ว ให้เปิดโปรแกรม Powershell ขึ้นมา 

และรันคำสั่งด้านล่าง 

```powershell
[Environment]::SetEnvironmentVariable("GOPATH", "C:\Projects\Go", "User")
```

จากนั้นรันคำสั่ง ทดสอบค่า path ด้วย
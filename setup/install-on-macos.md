
# ติดตั้ง Go บน MacOS

## ติดตั้ง Go ผ่าน Homebrew

ต้องติดตั้ง

เปิดโปรแกรม Terminal และรันคำสั่งติดตั้ง

```bash
brew update
brew install go
```

หลังจากติดตั้งเรียบร้อยแล้ว ให้ทดสอบรันคำสั่ง ใน Terminal

```bash
go version
```

## 2. ตั้งค่า Workspace ของ Go ด้วย $GOPATH

1. เปิดโปรแกรม Terminal
2. ถ้ายังไม่มีให้สร้างไฟล์

```bash
# ถ้าใช้ zshell 
touch ~/.zshrc

# ถ้าใช้ bash
touch ~/.bash_profile
```

3. จากนั้น เปิดไฟล์

```bash
# ถ้าใช้ zshell 
open -e ~/.zshrc

# ถ้าใช้ bash
open -e ~/.bash_profile
```

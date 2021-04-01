
# ติดตั้ง Go บน MacOS

## ติดตั้ง Go 


### ผ่าน Homebrew

ต้องติดตั้ง Homebrew ก่อน [ดูวีดีโอวิธีติดตั้งได้ที่นี่](https://www.youtube.com/watch?v=YJAyQREPAy4) 

เปิดโปรแกรม Terminal และรันคำสั่งติดตั้ง

```bash
brew update
brew install go
```

หลังจากติดตั้งเรียบร้อยแล้ว ให้ทดสอบรันคำสั่ง ใน Terminal

```bash
go version
```

### ผ่านตัว Installer

1. [ดาวน์โหลดไฟล์ติดตั้งจากที่นี่](https://golang.org/dl/)
2. เปิดตัวติดตั้ง และดำเนินการติดตั้งให้เรียบร้อย

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

4. วางคำสั่งด้านล่างลงไปในไฟล์ อาจจะเพิ่มเป็นบรรทัดสุดท้ายของไฟล์ก็ได้ 

```bash
export GOPATH=$HOME/go
```

5. บันทึกไฟล์ 
6. รันคำสั่ง เพื่อให้ระบบอ่านค่าใหม่

```bash
# ถ้าใช้ zshell 
source ~/.zshrc

# ถ้าใช้ bash
source ~/.bash_profile
```

7. รันคำสั่งทดสอบดูค่า GOPATH 

```bash
go env
```
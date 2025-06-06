# บันทึกไฟล์จาก LINE ลง Google Drive พร้อมจัดหมวดหมู่ และลงบันทึกใน Google Sheets โดยอัตโนมัติ

## คำอธิบาย

Workflow นี้ใช้สำหรับรับไฟล์ที่ส่งเข้ามาผ่าน LINE Chatbot แล้วบันทึกไฟล์เหล่านั้นลง Google Drive โดยมีการจัดเก็บตามวันที่และประเภทไฟล์ พร้อมทั้งบันทึกข้อมูลของไฟล์ลงใน Google Sheets และสามารถตอบกลับผู้ใช้งานทาง LINE ได้ (ถ้ามีการเปิดใช้งาน)

---

## ขั้นตอนการทำงาน (Workflow Steps)

1. รับไฟล์จาก LINE Webhook
2. อ่านการตั้งค่าจาก Google Sheet (โฟลเดอร์หลัก, ประเภทไฟล์ที่อนุญาต ฯลฯ)
3. ตรวจสอบและสร้างโฟลเดอร์ปลายทาง (ตามวันที่ / ประเภทไฟล์)
4. บันทึกไฟล์ลง Google Drive ในตำแหน่งที่เหมาะสม
5. ลงบันทึกข้อมูลไฟล์ลง Google Sheets (ชื่อไฟล์, ประเภท, วันที่, ลิงก์)
6. (เลือกได้) ตอบกลับผู้ใช้งานทาง LINE พร้อมลิงก์ Google Drive หรือข้อความแจ้งเตือนกรณีผิดพลาด

---

## การตั้งค่า (ผ่าน Google Sheets)

| คีย์ | คำอธิบาย |
|------|----------|
| Parent Folder ID | โฟลเดอร์หลักของ Google Drive |
| Store by Date | จัดเก็บตามวันที่ (true/false) |
| Store by File Type | แยกตามประเภทไฟล์ (true/false) |
| Allow File Types | ประเภทไฟล์ที่อนุญาต เช่น `image/audio/video` |
| Reply Enabled | ตอบกลับ LINE หรือไม่ (true/false) |

---

## Credential ที่ใช้

- Google Drive OAuth2
- Google Sheets OAuth2
- LINE Messaging API Header Auth (Bearer Token)

---

## ลิงก์ประกอบ

- **Google Sheet Template**  - [คลิกเพื่อดูตัวอย่าง Sheet](https://docs.google.com/spreadsheets/d/1iO4ZHU7s0fe1Jn8jcScNDce7rFXQlkRBqsO8IFHbcSc/edit?usp=sharing)

- **ตัวอย่างโฟลเดอร์ Google Drive**  - [เปิดดูโฟลเดอร์](https://drive.google.com/drive/folders/1dK5g2k8-h9zB6keXzyBZW-k6QjKPsxxY)

---
## ⚠️ หมายเหตุสำคัญ

> ❗ Webhook ที่เชื่อมต่อกับ Line **ต้องเป็น HTTPS เท่านั้น**
> 
> แนะนำให้ใช้งานบน  
> - [x] n8n.cloud  
> - [x] n8n ที่ตั้งค่า domain ของตัวเอง (มี SSL แล้ว)  
> - [ ] ❌ ไม่สามารถใช้กับ Self-hosted แบบ Localhost ได้


---
## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=1RtoT0nQEuullUe9Tgh9_ASpZKx_8TVwf&sz=w1200)

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n

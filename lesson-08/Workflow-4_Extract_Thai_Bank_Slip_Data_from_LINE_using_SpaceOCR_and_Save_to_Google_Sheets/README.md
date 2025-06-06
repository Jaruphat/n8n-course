# Extract Thai Bank Slip Data from LINE using SpaceOCR and Save to Google Sheets

##  คำอธิบาย

Workflow นี้ช่วยให้สามารถดึงข้อมูลจากสลิปโอนเงิน (Bank Slip) ที่ผู้ใช้ส่งมาทาง LINE Chatbot ได้โดยอัตโนมัติ โดยผ่านขั้นตอนดังนี้:

- รับภาพสลิปผ่าน LINE Webhook
- ดึงลิงก์ภาพและแปลงเป็น Binary
- อัปโหลดภาพสลิปลง Google Drive
- ส่ง URL ไปวิเคราะห์ด้วย OCR API (OCR.Space)
- แยกข้อมูลที่สำคัญ (ชื่อผู้โอน, บัญชี, ธนาคาร, จำนวนเงิน, ค่าธรรมเนียม, รหัสรายการ ฯลฯ)
- บันทึกข้อมูลลง Google Sheets

---

## ขั้นตอนการทำงาน (Workflow Steps)

1. รับข้อความจาก LINE ผ่าน Webhook
2. แปลง Message ID เป็น URL สำหรับดึงภาพ
3. ดึงภาพจาก LINE API เป็น Binary
4. อัปโหลดภาพไปยัง Google Drive
5. ส่ง URL ไปยัง SpaceOCR API เพื่อดึงข้อความ
6. แยกข้อมูลจากข้อความด้วย JavaScript (Node: Code)
7. บันทึกข้อมูลลง Google Sheet

---

## Node ที่ใช้ใน Workflow

- Webhook (LINE)
- Set, HTTP Request
- Google Drive Upload
- HTTP Request (OCR API)
- Code (JavaScript สำหรับแยกข้อมูล)
- Google Sheets (Append Row)

---

## Credential ที่ต้องใช้

- LINE Bot Channel Access Token *(สำหรับ Auth Header)*
- Google Drive OAuth2
- Google Sheets OAuth2
- OCR.Space API Key

---

## ลิงก์ประกอบ

-  **Google Sheet Template**  -
   [คลิกเพื่อเปิด Sheet](https://docs.google.com/spreadsheets/d/1IpvzcnWmb-aLpSleTIF0xoF8xzbOOJQhuT6ITAeEQks/edit?usp=sharing)

-  **ตัวอย่าง Slip สำหรับทดสอบ**  -
   [คลิกเพื่อดูตัวอย่าง](https://drive.google.com/file/d/1Ufa17FgdZvX1ep0i0igisQv9X3DA5zYi/view)

---

## ฟิลด์ที่ดึงจาก Slip

- `transaction_type` (เช่น โอนเงินพร้อมเพย์)
- `date_time` (วันเวลา)
- `sender_name`, `sender_bank`, `sender_account`
- `receiver_name`, `receiver_bank`, `receiver_account`
- `transaction_id`
- `amount`, `fee`

---

## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=10auZtDjloTVW__S-X94EpJJKJrUQ-KX7&sz=w1200)

---

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n

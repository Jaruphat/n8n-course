# Basic Workflow - 2: สร้างภาพจาก Line แล้วส่งกลับผ่าน Line พร้อมบันทึกลง Google Drive

## คำอธิบาย

Workflow นี้ออกแบบมาเพื่อรับคำสั่งจาก Line Chatbot (ผ่าน Webhook) เพื่อสร้างภาพด้วย AI (OpenAI DALL·E / gpt-image-1) และส่งภาพกลับไปทาง Line พร้อมกับบันทึกรูปภาพลงใน Google Drive

---

## ขั้นตอนการทำงาน (Workflow Steps)

1. **รับคำสั่งผ่าน Line Chatbot**  
   ผู้ใช้พิมพ์ข้อความเพื่อขอภาพ เช่น “หุ่นยนต์บนดวงจันทร์”

2. **Webhook รับข้อมูล**  
   Webhook Node รับข้อความ และ Extract ค่าจาก JSON (ข้อความ และ replyToken)

3. **สร้างภาพด้วย OpenAI (DALL·E)**  
   เรียกใช้ API ของ OpenAI เพื่อสร้างภาพจากข้อความ

4. **แปลงภาพ (base64) เป็นไฟล์ และบันทึกลง Google Drive**  
   Convert base64 → binary file → อัปโหลดไปยังโฟลเดอร์ใน Google Drive

5. **ส่งลิงก์รูปกลับไปที่ Line**  
   ส่งภาพกลับไปยังผู้ใช้ ผ่าน Messaging API

---

## Node ที่ใช้

- [x] Webhook  
- [x] Set Fields (แกะค่าจาก body ของ Line)  
- [x] HTTP Request (OpenAI และ Line API)  
- [x] Convert to File  
- [x] Google Drive Upload

---

## Credential ที่ต้องใช้

- Google Drive Credential (สำหรับอัปโหลดไฟล์)
- OpenAI API Key
- Line Chatbot: Channel Access Token (ผ่าน HTTP Header Auth)

---

## ⚠️ หมายเหตุสำคัญ

> ❗ Webhook ที่เชื่อมต่อกับ Line **ต้องเป็น HTTPS เท่านั้น**
> 
> แนะนำให้ใช้งานบน  
> - [x] n8n.cloud  
> - [x] n8n ที่ตั้งค่า domain ของตัวเอง (มี SSL แล้ว)  
> - [ ] ❌ ไม่สามารถใช้กับ Self-hosted แบบ Localhost ได้

---

## ไฟล์ในโฟลเดอร์นี้

- `lesson-08_2_Line_Webhook_and_GoogleDrive.json` – ไฟล์ Workflow สำหรับ n8n
- `README.md` – ไฟล์อธิบายการใช้งาน

---

## ตัวอย่างผลลัพธ์

ผู้ใช้พิมพ์:  
> ช่วยสร้างรูปคนกำลังสอนคอร์ส n8n Basic Workshop ให้หน่อย

ระบบจะตอบกลับใน Line พร้อมแนบภาพ AI ที่สร้างได้

![Line Result](https://drive.google.com/thumbnail?id=1zHjWPDYo2VnET5wwbgtVECpKI7CHerw6&sz=w500)

---

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n

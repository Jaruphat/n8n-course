# Extract and Structure Thai Documents to Google Sheets using Typhoon OCR

## คำอธิบาย

Workflow นี้ช่วยให้สามารถแปลงไฟล์ PDF ภาษาไทย (เช่น หนังสือราชการ) ให้อยู่ในรูปแบบที่จัดหมวดหมู่แล้ว และบันทึกลงใน Google Sheets โดยใช้ OCR + LLM แบบอัตโนมัติ เหมาะกับงานเอกสารที่ต้องการเก็บข้อมูลเป็นระบบ

---

## สิ่งที่ต้องมี (Pre-requisites)

- ติดตั้ง n8n แบบ Self-hosted (เช่น บน Docker Desktop)
- ติดตั้ง [Typhoon OCR](https://pypi.org/project/typhoon-ocr/)
- เตรียมโฟลเดอร์ `/doc/` สำหรับเก็บไฟล์ PDF
- เชื่อมต่อ Google Sheets API และ OpenRouter API

---

## ขั้นตอนการทำงาน (Workflow Steps)

1. **อ่านไฟล์ PDF ทั้งหมดใน `/doc/*.pdf`**
2. **สั่ง Typhoon OCR อ่านเนื้อหาจาก PDF**
3. **ใช้ AI (LLM) วิเคราะห์เนื้อหา และจัดโครงสร้างข้อมูลให้อยู่ใน JSON**
4. **แปลง JSON ให้อยู่ในรูปแบบที่เหมาะสมกับ Google Sheet**
5. **บันทึกข้อมูลลง Google Sheets โดยแยกเป็นคอลัมน์**

---

## Node ที่ใช้ใน Workflow

- Read/Write File (อ่าน PDF)
- Execute Command (เรียกใช้ Typhoon OCR ผ่าน Python)
- Basic LLM Chain (สร้าง JSON จากข้อความ)
- Code (Parse JSON → Sheet Format)
- Google Sheets (Append ข้อมูล)

---

## Credential ที่ต้องใช้

- Typhoon API *(local only)*
- OpenRouter API
- Google Credential

---

## ตัวอย่างการใช้งาน

**ลิงก์ Google Sheet Template**  - [เปิดดู Sheet](https://docs.google.com/spreadsheets/d/1h70cJyLj5i2j0Ag5kqp93ccZjjhJnqpLmz-ee5r4brU/edit?usp=sharing)

**ลิงก์ตัวอย่างไฟล์ PDF** - [ดาวน์โหลด PDF ตัวอย่าง](https://drive.google.com/file/d/16QZ2X8H0M-hV3lOCCa20vaPuvfX_5ua8/view?usp=sharing)

---

## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=1h29TW-_1ScqEtG31tYXIcZCqQvB1h6JV&sz=w1200)

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n
# Basic Workflow - 1: สร้างภาพจากข้อความด้วย AI และบันทึกผลลง Google Sheet

## คำอธิบาย

Workflow นี้ออกแบบมาเพื่อแปลงแนวคิดหรือคำสั้น ๆ ที่อยู่ใน Google Sheet ให้กลายเป็นภาพสวยงามด้วย AI โดยอัตโนมัติ พร้อมบันทึก Image Prompt และ URL ของภาพกลับเข้าไปยัง Google Sheet เดิม

---

## ขั้นตอนการทำงาน (Workflow Steps)

1. **อ่านข้อมูลจาก Google Sheet**  
   ดึงข้อมูลแนวคิด (Idea) จาก Google Sheet

2. **AI ช่วยคิด Prompt สำหรับสร้างภาพ**  
   ใช้ LLM (ผ่าน OpenRouter หรือ OpenAI) เพื่อแปลงแนวคิดให้กลายเป็น image prompt แบบละเอียด

3. **สร้างภาพด้วย PiAPI**  
   ส่ง prompt ไปยัง PiAPI (Flux Model) เพื่อสร้างภาพ

4. **บันทึกผลกลับเข้า Google Sheet**  
   เพิ่ม prompt ที่ถูกสร้างขึ้น และ URL ของภาพที่ได้จาก AI

---

## Node ที่ใช้

- [x] Manual Trigger  
- [x] Google Sheet (Read & Write)  
- [x] Basic LLM Chain  
- [x] OpenRouter Chat Model *(optional)*  
- [x] HTTP Request  
- [x] Wait Node (สำหรับรอผลการสร้างภาพ)

---

## Credential ที่ต้องใช้

- Google Credential (สำหรับเชื่อม Google Sheets)
- OpenRouter API (หรือใช้ OpenAI ก็ได้)
- PiAPI Key (สำหรับเรียก API สร้างภาพ)

---
## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=1GQI_bJUuTMA5FeuBEb_7ftrad8xH4s9n&sz=w1200)


> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n
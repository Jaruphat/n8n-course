# สร้างวิดีโอคำคมภาษาไทยและอัปโหลดขึ้น YouTube โดยอัตโนมัติด้วย FFmpeg

## คำอธิบาย

Workflow นี้ช่วยให้คุณสามารถสร้างวิดีโอแนวคำคมภาษาไทยจากข้อมูลใน Google Sheet โดยดึงวิดีโอพื้นหลัง เพลงประกอบ และคำคมจาก Google Drive และ Google Sheets มาประกอบกันเป็นคลิปวิดีโอแนว vertical (9:16) แล้วอัปโหลดอัตโนมัติขึ้น YouTube พร้อมทั้งอัปเดตสถานะใน Google Sheets

---

## ขั้นตอนการทำงาน

1. ดึงข้อมูลคำคม (Quotes), วิดีโอพื้นหลัง และเพลงจาก Google Sheet และ Google Drive
2. สุ่มเลือกวิดีโอ 1 เพลง 1 และคำคม 1 ชุด
3. ดาวน์โหลดไฟล์มาบันทึกไว้ในเครื่อง (Docker Volume)
4. แปะข้อความคำคม และชื่อผู้เขียนลงวิดีโอ ด้วย FFmpeg
5. สร้างคลิปวิดีโอแบบ 9:16 พร้อมเพลง
6. อัปโหลดวิดีโอไปยัง YouTube โดยใช้ API แบบ resumable upload
7. อัปเดต Google Sheet ว่าอัปโหลดสำเร็จแล้ว พร้อมแนบลิงก์ YouTube

---

## Node ที่ใช้

- Manual Trigger
- Google Sheets (Quotes / Background / Music)
- Google Drive (List / Download)
- Code (JavaScript สำหรับสุ่มและจัดการข้อความ)
- Execute Command (ใช้ FFmpeg)
- HTTP Request (YouTube API Upload)
- Read/Write File (บันทึกไฟล์ในเครื่อง)

---

## Credential ที่ต้องใช้

- Google Drive OAuth2
- Google Sheets OAuth2
- YouTube OAuth2

---

## ลิงก์ประกอบ

- **Google Sheet Template** - [คลิกเพื่อเปิด Sheet](https://docs.google.com/spreadsheets/d/184-zcrfWSzQpDa-t57Oo_8DLyAF-2B_6yvGrybrcd5I/edit?usp=sharing)

- **Google Drive ตัวอย่างไฟล์** - [เปิดดูโฟลเดอร์](https://drive.google.com/drive/folders/1FToPtZEIjBwRKbrKvhwxSdhdUHzgls0C?usp=sharing)

---

## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=1Df9Ir5l7L_ORbZhclIUHD4Ge4RgbZslO&sz=w1200)

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n

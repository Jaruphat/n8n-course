# สร้างวิดีโอคำคมแนว Cinematic ด้วย AI และอัปโหลดขึ้น YouTube โดยอัตโนมัติ

## คำอธิบาย

Workflow นี้จะช่วยให้คุณสามารถสร้างวิดีโอแนวคำคมแบบ vertical สไตล์ cinematic ได้แบบอัตโนมัติ โดยดึงข้อมูลจาก Google Sheet แล้วใช้ AI สร้างรูปภาพ วิดีโอ เสียงประกอบ และนำมารวมกันเป็นวิดีโอพร้อมอัปโหลดขึ้น YouTube รวมถึงบันทึกสถานะและลิงก์วิดีโอกลับไปที่ Google Sheets

---

## ขั้นตอนการทำงาน

1. ดึงคำคมหรือไอเดียจาก Google Sheet
2. สร้างภาพพื้นหลังด้วย AI (txt2img ผ่าน PiAPI Flux)
3. แปลงภาพให้เป็นวิดีโอแบบแนวตั้งด้วย AI (img2video ผ่าน PiAPI Kling)
4. สร้างเสียงบรรยากาศด้วย ElevenLabs
5. รวมภาพ เสียง คำคม เข้าด้วยกันผ่าน FFmpeg
6. อัปโหลดวิดีโอขึ้น YouTube
7. อัปเดตสถานะและลิงก์วิดีโอกลับไปยัง Google Sheets

---

## Node ที่ใช้

- Google Sheets (อ่าน/อัปเดตข้อมูล)
- HTTP Request (เรียก PiAPI, ElevenLabs, YouTube API)
- Wait (รอ image/video)
- Code (เตรียมข้อความ overlay)
- Read/Write File (จัดการไฟล์ video/audio)
- Execute Command (สั่ง FFmpeg)
- YouTube Upload

---

## Credential ที่ต้องใช้

- Google Credential (Sheets + Drive)
- PiAPI Credential (สำหรับ txt2img และ img2video)
- ElevenLabs API Key
- YouTube OAuth2

---

## ลิงก์ประกอบ

- **Google Sheet Template** - [ดูไฟล์](https://docs.google.com/spreadsheets/d/1p1iPoiu2uI3qGbHi0diS7QwsMcLuzDIqwo3AeSUVrGQ/edit?usp=sharing)

- **Google Drive (Sound BG Examples)** - [ดูโฟลเดอร์](https://drive.google.com/drive/folders/1Sfv2PvIHF0J3-5IOYFdZp2-4LNPOoSX1)

- **สมัครใช้งาน PiAPI สำหรับสร้างรูปและวิดีโอ** - [เข้าสู่เว็บไซต์ PiAPI](https://piapi.ai/workspace?via=jaruphat)

- **สมัครใช้งาน ElevenLabs สำหรับเสียง** - [เข้าสู่เว็บไซต์ ElevenLabs](https://try.elevenlabs.io/ttfjxovolrmk)

---

## ข้อกำหนดเบื้องต้น (Pre-requisite)

- ต้องติดตั้ง FFmpeg ในเครื่องหรือ container ที่รัน n8n
- ฟอนต์ภาษาไทย เช่น `Kanit-Italic.ttf` ต้องมีในระบบเพื่อใช้ overlay
- ใช้ได้เฉพาะใน n8n ที่เป็น self-hosted เท่านั้น เพราะใช้ Execute Command และ community node

---

## ภาพรวม Workflow

![Alt text](https://drive.google.com/thumbnail?id=1BD_GBn35tl_ecW45dmRFhpAD42Am_DXk&sz=w1200)

> สร้างโดย: [Jaruphat J.](https://github.com/Jaruphat) | ใช้ประกอบบทเรียน Chapter 8 คอร์สสอน n8n

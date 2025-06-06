# Lesson 08 – Real-World n8n Workflows

This folder contains real-world n8n workflow examples used in **Lesson 08: ตัวอย่าง Workflow และเทมเพลตที่ใช้งานได้จริง** from the n8n Automation Course.

> 📦 These workflows are designed for practical use and can be imported directly into your n8n instance for experimentation, learning, or customization.

## Prerequisites

Before using these workflows, make sure you have:
- Docker Desktop with `n8n`, `ffmpeg`, and `typhoon-ocr` installed
- Required credentials already set up in n8n:
  - Google OAuth2
  - OpenAI API
  - OpenRouter
  - ElevenLabs
  - PiAPI
  - LINE Bot
  - YouTube API

---

## Workflows Included in `lesson-08/`

| Filename | หัวข้อประกอบบทเรียน |
|----------|------------------------|
| `8.1_google_sheet_basic.json` | **Basic Workflow - 1:** สร้างภาพจากข้อความด้วย AI และบันทึกผลลง Google Sheet |
| `8.2_line_upload_to_drive.json` | **Basic Workflow - 2:** สร้างภาพจาก Line แล้วส่งกลับผ่าน Line พร้อมบันทึกลง Google Drive |
| `8.3_ocr_slip_to_sheet.json` | **Extract and Structure Thai Documents to Google Sheets using Typhoon OCR** |
| `8.4_ai_quote_to_youtube.json` | **Extract Thai Bank Slip Data from LINE using SpaceOCR and Save to Google Sheets** |
| `8.5_product_image_to_facebook.json` | **สร้างวิดีโอคำคมภาษาไทยและอัปโหลดขึ้น YouTube โดยอัตโนมัติด้วย FFmpeg** |
| `8.6_comfyui_ffmpeg_workflow.json` | **บันทึกไฟล์จาก LINE ลง Google Drive พร้อมจัดหมวดหมู่ และลงบันทึกใน Google Sheets โดยอัตโนมัติ** |
| `8.7_autoquote_cinematic_youtube.json` | **สร้างวิดีโอคำคมแนว Cinematic ด้วย AI และอัปโหลดขึ้น YouTube โดยอัตโนมัติ** |


---

## How to Use

1. Open your local or hosted n8n instance.
2. Go to **Workflows** → **Import**.
3. Upload the JSON file from this folder.
4. Make sure to configure any required credentials before executing.

---

## License

These workflow examples are part of the n8n Automation Course and are provided for educational purposes.

---

Enjoy building automation! 🚀

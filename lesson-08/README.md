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

| Filename | Description |
|----------|-------------|
| `8.1_google_sheet_basic.json` | Manual-triggered workflow that logs data into a Google Sheet |
| `8.2_line_upload_to_drive.json` | Receive files from LINE Webhook → Save to Google Drive → Log to Google Sheet |
| `8.3_ocr_slip_to_sheet.json` | Extract data from image slip using Typhoon OCR and save structured data to Sheet |
| `8.4_ai_quote_to_youtube.json` | Generate quote video using AI (image + voice + video) and auto-upload to YouTube |
| `8.5_product_image_to_facebook.json` | Create product image from form input and post automatically to Facebook |
| `8.6_comfyui_ffmpeg_workflow.json` | Use ComfyUI and FFmpeg for AI-generated video workflow |

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

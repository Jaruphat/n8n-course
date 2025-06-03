# N8N Docker Setup with FFmpeg & Typhoon OCR

Complete Docker setup for N8N workflow automation platform with integrated FFmpeg video processing and Typhoon OCR text recognition capabilities.

## 🚀 Features

- **N8N Workflow Automation** - Visual workflow builder and automation platform
- **FFmpeg Integration** - Complete video/audio processing capabilities
- **Typhoon OCR** - Thai language optimized OCR text recognition
- **Font Support** - Custom font integration with automatic cache generation
- **Persistent Storage** - Data persistence across container restarts
- **Flexible Volume Mounting** - Easy integration with external directories

## 📋 Prerequisites

- Docker
- Docker Compose
- Basic understanding of N8N workflows

## 🏗️ Project Structure

```
project-directory/
├── Dockerfile
├── docker-compose.yml
├── fonts/                 # Place your custom fonts here
│   ├── font1.ttf
│   └── font2.otf
├── data/                  # Persistent data directory
└── doc/                   # Document storage directory
```

## 🛠️ Installation & Setup

### 1. Clone or Download Files

Download the `Dockerfile` and `docker-compose.yml` to your project directory.

### 2. Prepare Font Directory (Optional)

If you need custom fonts for text processing:

```bash
mkdir fonts
# Copy your .ttf or .otf font files to the fonts/ directory
```

### 3. Create Required Directories

```bash
mkdir -p data doc
```

### 4. Build and Start Services

```bash
docker-compose up --build
```

Or run in detached mode:

```bash
docker-compose up -d --build
```

## 🔧 Configuration

### Environment Variables

| Variable | Default Value | Description |
|----------|---------------|-------------|
| `N8N_BASIC_AUTH_ACTIVE` | `true` | Enable basic authentication |
| `N8N_BASIC_AUTH_USER` | `admin` | Username for N8N access |
| `N8N_BASIC_AUTH_PASSWORD` | `admin123` | Password for N8N access |
| `TYPHOON_OCR_API_KEY` | `0arzXoos...` | API key for Typhoon OCR service |
| `N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS` | `true` | Enforce file permission settings |

### Volume Mounts

| Host Path | Container Path | Purpose |
|-----------|----------------|---------|
| `n8n_data` (Docker volume) | `/home/node/.n8n` | N8N configuration and workflows |
| `C:/AI/ComfyUI/output` | `/comfy-output` | ComfyUI output integration |
| `./data` | `/data` | General data storage |
| `./doc` | `/doc` | Document processing |

## 🌐 Access

Once running, access N8N at:
- **URL**: http://localhost:5678
- **Username**: admin
- **Password**: admin123

## 📦 Installed Components

### Base System
- **N8N Latest** - Workflow automation platform
- **Python 3** - Required for Typhoon OCR
- **Node.js** - N8N runtime environment

### Media Processing
- **FFmpeg** - Complete multimedia framework
- **Font Config** - Font management system
- **TTF-FreeFont** - Base font collection

### OCR & Text Processing
- **Typhoon OCR** - Thai-optimized OCR engine
- **Poppler Utils** - PDF processing utilities

## 🔄 Common Operations

### Start Services
```bash
docker-compose up -d
```

### Stop Services
```bash
docker-compose down
```

### View Logs
```bash
docker-compose logs -f n8n
```

### Rebuild Container
```bash
docker-compose up --build --force-recreate
```

### Access Container Shell
```bash
docker-compose exec n8n sh
```

## 💡 Usage Examples

### FFmpeg in N8N Workflows
Use the Execute Command node in N8N:
```bash
ffmpeg -i /data/input.mp4 -vf scale=720:480 /data/output.mp4
```

### Typhoon OCR Processing
Python script execution in N8N:
```python
from typhoon_ocr import OCREngine
engine = OCREngine()
result = engine.process_image('/data/image.jpg')
```

### Font Usage
Fonts from the `/fonts` directory are automatically available system-wide in the container.

## 🐛 Troubleshooting

### Permission Issues
If you encounter permission errors:
```bash
sudo chown -R 1000:1000 ./data ./doc
```

### Port Already in Use
Change the port mapping in `docker-compose.yml`:
```yaml
ports:
  - "5679:5678"  # Use port 5679 instead
```

### Memory Issues
Add memory limits to docker-compose.yml:
```yaml
deploy:
  resources:
    limits:
      memory: 2G
```

## 🔒 Security Notes

- Change default credentials before production use
- Consider using environment files (.env) for sensitive data
- Restrict network access in production environments
- Regularly update the base images

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 📞 Support

For issues related to:
- **N8N**: [N8N Community](https://community.n8n.io/)
- **FFmpeg**: [FFmpeg Documentation](https://ffmpeg.org/documentation.html)
- **Typhoon OCR**: [Typhoon OCR Documentation](https://github.com/typhoon-ocr)

---

*Last updated: $(date)*

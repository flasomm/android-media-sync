# Android Media Sync Tool

A bash scripts for backing up media files from Android devices using ADB (Android Debug Bridge).

## Features

- Complete Android backup via ADB
- Automatic file organization (Images/Videos folders)
- Safe file operations (read-only on device)
- Cross-platform compatibility (macOS, Linux)

## Prerequisites

### Required Software
- **ADB (Android Debug Bridge)** - Install via:
  ```bash
  # macOS
  brew install android-platform-tools
  
  # Ubuntu/Debian
  sudo apt-get install android-tools-adb
  
  # Arch Linux
  sudo pacman -S android-tools
  ```

### Android Device Setup
1. **Enable Developer Options**:
   - Go to Settings → About Phone
   - Tap "Build Number" 7 times
   - Developer options will appear in Settings

2. **Enable USB Debugging**:
   - Go to Settings → Developer Options
   - Enable "USB Debugging"
   - Enable "USB Debugging (Security Settings)" if available

3. **Connect Device**:
   - Connect your Android device via USB
   - Select "File Transfer" or "MTP" mode
   - Allow USB debugging when prompted on your device

## Scripts Overview

### backup_android_files - Main Backup Script
Complete backup solution that copies all media files from your Android device to your computer.

**Features:**
- Smart directory detection - Finds all media directories
- Image support - JPG, PNG, HEIC, RAW, and more
- Video support - MP4, AVI, MOV, MKV, and more
- Organized structure - Creates Images/ and Videos/ folders
- Safe operations - Read-only on device, no data loss

**Usage:**
```bash
# Use default destination
./backup_android_files

# Custom destination
./backup_android_files /path/to/backup/folder
```

**Configuration:**
Edit the script to change the default destination:
```bash
DESTINATION_DIR="/Users/yourname/Pictures/Android-phone/$(date +%Y-%m)"
```

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/flasomm/android-media-sync.git
   cd android-media-sync
   ```

2. **Make scripts executable:**
   ```bash
   chmod +x backup_android_files
   ```

3. **Configure your backup destination:**
   Edit `backup_android_files` and modify the `DESTINATION_DIR` variable.

## Usage Examples

### Basic Android Backup
```bash
# Connect your Android device and run:
./backup_android_files

# The script will:
# 1. Detect your Android device
# 2. Scan for media directories
# 3. Let you select which directories to backup
# 4. Copy all files to organized folders
```

### Custom Backup Location
```bash
# Backup to a specific location:
./backup_android_files "/Volumes/ExternalDrive/Android-Backup"
```

## Output Structure

After running the backup script, you'll have:
```
/your/backup/directory/
├── Images/
│   ├── IMG_20240115_103000.jpg
│   ├── Screenshot_20240115_104500.png
│   └── ... (all images)
└── Videos/
    ├── VID_20240115_103000.mp4
    ├── Screen_Recording_20240115.mp4
    └── ... (all videos)
```

## Troubleshooting

### Common Issues

**"ADB not found"**
```bash
# Install ADB:
brew install android-platform-tools  # macOS
sudo apt-get install android-tools-adb  # Ubuntu
```

**"Device unauthorized"**
1. Check USB debugging is enabled
2. Disconnect and reconnect your device
3. Accept the USB debugging prompt on your device
4. Try running the script again

**"No media files found"**
1. Ensure your device is unlocked
2. Check that media files exist in DCIM, Pictures, etc.
3. Verify USB connection mode is "File Transfer"

**"Permission denied"**
```bash
# Make scripts executable:
chmod +x backup_android_files
```

### Debug Mode
Add `set -x` at the beginning of scripts for verbose output:
```bash
#!/bin/bash
set -x  # Add this line for debugging
```

## Supported File Types

### Images
- JPG, JPEG, PNG, GIF, BMP
- TIFF, WebP, HEIC, HEIF
- RAW formats: CR2, NEF, ARW, DNG

### Videos
- MP4, AVI, MOV, MKV, WMV
- FLV, WebM, M4V, 3GP
- MPG, MPEG, TS, MTS, VOB

## Security & Safety

- Read-only on device - Scripts never modify files on your Android device
- Safe operations - All deletions are local only
- Backup verification - Scripts count and verify copied files
- Error handling - Graceful handling of connection issues

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

**Made with ❤️ for Android users who want to keep their memories safe!**

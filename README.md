# VideoStream CMS - Quick Installation Guide

This guide provides simple instructions to get VideoStream CMS up and running quickly. For a more detailed guide, see `INSTALL.md`.

## Installation Options

### Option 1: Production Server Installation (Recommended for VPS/Servers)

For a full server installation with all features including Nginx, SSL, and system service:

```bash
# Make the installer executable
chmod +x install.py

# Run the installer (as root/sudo)
sudo python3 install.py
```

Follow the interactive prompts to configure your installation.

The installer will:
- Install all required dependencies
- Set up directories with proper permissions
- Configure SSL with domain verification (optional)
- Set up Nginx for serving media files
- Create a systemd service for automatic startup
- Configure everything for production use

### Option 2: Local/Development Installation

For a simpler local installation (development or testing):

```bash
# Run the local installer
python3 local_install.py
```

This will:
- Create a local directory structure
- Set up a Python virtual environment
- Install required packages
- Create startup scripts
- Configure for local use

After installation, run the application with:
```bash
# On Linux/Mac
./videostream_local/start.sh

# On Windows
videostream_local\start.bat
```

## Directory Structure

The installation creates these directories:

- **Server Installation (Option 1)**:
  - Main application: `/var/www/videostream/`
  - Media files: 
    - HLS: `/var/www/videostream/hls/`
    - DASH: `/var/www/videostream/dash/`
    - MP4: `/var/www/videostream/mp4/`
    - Thumbnails: `/var/www/videostream/thumbnails/`

- **Local Installation (Option 2)**:
  - Main application: `./videostream_local/`
  - Media files: 
    - HLS: `./videostream_local/media/hls/`
    - DASH: `./videostream_local/media/dash/`
    - MP4: `./videostream_local/media/mp4/`
    - Thumbnails: `./videostream_local/media/thumbnails/`

## SSL/TXT Verification (for Production Only)

If you choose to enable SSL, you'll need to add a TXT record to your domain:

- **Record Type**: TXT
- **Host/Name**: `_videostream-verify.yourdomain.com`
- **Value**: A verification code provided during installation

This confirms domain ownership for secure HTTPS connections.

## Accessing Your Installation

- **Server Installation**: http://yourdomain.com or https://yourdomain.com (if SSL enabled)
- **Local Installation**: http://localhost:5000

## Troubleshooting

If you encounter issues:

1. Check error messages during installation
2. Verify all dependencies are installed
3. Check system logs:
   - Application logs: `sudo journalctl -u videostream`
   - Web server logs: `sudo tail /var/log/nginx/error.log`
4. Ensure directories have proper permissions

## Need More Help?

For detailed instructions including manual installation, advanced configuration options, and troubleshooting tips, see the full `INSTALL.md` document.

# Contributing Guide

Guidelines for adding new sample videos to this repository.

## Directory Structure

```
appreview-samples/
├── ios/        # iPhone screen recordings
├── ipad/       # iPad screen recordings
├── mac/        # Mac screen recordings
└── README.md
```

Each device category has its own directory. Place new recordings in the appropriate directory.

## Adding a New Sample Video

### 1. Record the Screen

- **iPhone/iPad**: Settings → Control Center → add Screen Recording, then record from Control Center
- **Mac**: Use QuickTime Player → File → New Screen Recording, or press `Cmd + Shift + 5`

### 2. Place the File

Move the recording to the corresponding directory:

| Device | Directory | Target Resolution for AppPreview Cutter |
|--------|-----------|----------------------------------------|
| iPhone | `ios/` | 886×1920 (portrait) |
| iPad | `ipad/` | 1200×1600 (portrait) |
| Mac | `mac/` | 1920×1080 (landscape) |

### 3. File Naming Convention

Keep the original filename from the screen recording. This helps identify the device and recording date:

- iOS: `ScreenRecording_MM-DD-YYYY HH-MM-SS.mp4`
- iPad: `ScreenRecording_MM-DD-YYYY HH-MM-SS.mp4`
- Mac: `YYYY-MM-DD HH.MM.SS.mp4`

If there are multiple files in the same directory, keep the original names to avoid confusion.

### 4. File Size Limit

GitHub has a **100 MB** file size limit per file. If your recording exceeds this:

1. Compress the video before committing:
   ```bash
   ffmpeg -i input.mp4 -c:v libx264 -crf 28 -preset slow -c:a aac -b:a 128k output.mp4
   ```

2. Or use [Git LFS](https://git-lfs.github.com/) for large files

### 5. Commit and Push

```bash
git add ipad/your-new-recording.mp4
git commit -m "Add iPad screen recording sample"
git push origin main
```

### 6. Update GitHub Release

After pushing a new sample file, update the release assets:

```bash
# Copy and rename the file for the release
cp ipad/your-recording.mp4 /tmp/ipad-sample.mp4

# Upload to the existing release
gh release upload v1.0.0 /tmp/ipad-sample.mp4
```

Release asset naming convention:

| Device | Release Asset Name |
|--------|--------------------|
| iPhone | `ios-sample.mp4` |
| iPad | `ipad-sample.mp4` |
| Mac | `mac-sample.mp4` |

### 7. Update README

Update the sample files table in `README.md` with the new file's information:

```bash
# Get video info
ffprobe -v quiet -print_format json -show_format -show_streams your-recording.mp4
```

## Recording Tips

- Record for at least **30 seconds** to test both auto-processing and manual trimming
- Show a variety of app interactions (tapping, scrolling, transitions)
- Avoid recording sensitive information
- Use the device's native screen recording feature for best compatibility
- For iPad, record in **portrait orientation** to match App Store Preview requirements

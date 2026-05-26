# Contributing Guide

Guidelines for adding new sample videos to this repository.

## Directory Structure

```
appreview-samples/
├── ios/                # iPhone screen recordings
│   └── iphone-sample.mp4
├── ipad/               # iPad screen recordings
│   └── ipad-sample.mp4
├── mac/                # Mac screen recordings
│   └── mac-sample.mp4
├── README.md
└── CONTRIBUTING.md
```

Each device category has its own directory. Place new recordings in the appropriate directory.

## File Naming Convention

All sample video files follow a unified naming format:

```
{device}-sample.mp4
```

| Device | Directory | Filename |
|--------|-----------|----------|
| iPhone | `ios/` | `iphone-sample.mp4` |
| iPad | `ipad/` | `ipad-sample.mp4` |
| Mac | `mac/` | `mac-sample.mp4` |

Rules:
- Use **lowercase** letters and hyphens only
- Always use `.mp4` extension (convert from `.mov` if needed)
- One sample file per device category — replace the existing file when updating
- The filename in the repo and the release asset name must match

## Adding a New Sample Video

### 1. Record the Screen

- **iPhone/iPad**: Settings → Control Center → add Screen Recording, then record from Control Center
- **Mac**: Use QuickTime Player → File → New Screen Recording, or press `Cmd + Shift + 5`

### 2. Convert to MP4 (if needed)

If the recording is in `.mov` format, convert it:

```bash
ffmpeg -i input.mov -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 256k output.mp4
```

### 3. Place and Rename the File

Move the recording to the corresponding directory with the standard name:

```bash
# Example: replacing the iPad sample
cp your-recording.mp4 ipad/ipad-sample.mp4
```

### 4. File Size Limit

GitHub has a **100 MB** file size limit per file. If your recording exceeds this:

1. Compress the video before committing:
   ```bash
   ffmpeg -i input.mp4 -c:v libx264 -crf 28 -preset slow -c:a aac -b:a 128k output.mp4
   ```

2. Or use [Git LFS](https://git-lfs.github.com/) for large files

### 5. Commit and Push

```bash
git add ipad/ipad-sample.mp4
git commit -m "Update iPad screen recording sample"
git push origin main
```

### 6. Update GitHub Release

After pushing, update the release assets to match:

```bash
# Delete the old asset
gh release delete-asset v1.0.0 ipad-sample.mp4

# Upload the new one
gh release upload v1.0.0 ipad/ipad-sample.mp4
```

### 7. Update README

Update the sample files table in `README.md` with the new file's information:

```bash
# Get video info
ffprobe -v quiet -print_format json -show_format -show_streams ipad/ipad-sample.mp4
```

## Recording Tips

- Record for at least **30 seconds** to test both auto-processing and manual trimming
- Show a variety of app interactions (tapping, scrolling, transitions)
- Avoid recording sensitive information
- Use the device's native screen recording feature for best compatibility
- For iPad, record in **portrait orientation** to match App Store Preview requirements

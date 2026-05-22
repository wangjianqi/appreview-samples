# AppPreview Cutter - Sample Videos

Sample screen recording videos for [AppPreview Cutter](https://github.com/wangjianqi/AppPreviewCutter), a macOS developer tool that converts screen recordings into App Store-compliant preview videos.

These files are also used by Apple App Review to verify the app's functionality.

## Sample Files

| Directory | Device | Resolution | Codec | Duration | Description |
|-----------|--------|------------|-------|----------|-------------|
| `ios/` | iPhone | 1290×2796 | HEVC | ~42s | iPhone screen recording for testing iPhone/iPad device presets and auto-processing |
| `mac/` | Mac | 1920×1050 | H.264 | ~59s | Mac screen recording for testing Mac device presets and manual trimming |
| `ipad/` | iPad | — | — | — | Coming soon |

## Download

Download from [GitHub Releases](https://github.com/wangjianqi/appreview-samples/releases/latest):

- [ios-sample.mp4](https://github.com/wangjianqi/appreview-samples/releases/latest/download/ios-sample.mp4)
- [mac-sample.mp4](https://github.com/wangjianqi/appreview-samples/releases/latest/download/mac-sample.mp4)

## How to Use with AppPreview Cutter

1. Download sample files from the [Releases](https://github.com/wangjianqi/appreview-samples/releases/latest) page
2. Open AppPreview Cutter
3. Drag and drop a sample video onto the app, or click **Import** to select a file
4. The app will auto-detect video info and process it (frame deduplication, duration adjustment)
5. Select a device preset (iPhone / iPad / Mac) from Export Settings
6. Choose a scaling mode (Fit or Fill)
7. Click **Export** to generate an App Store-compliant preview video
8. Check the Compliance panel to verify the output meets App Store requirements

## Features Verifiable with These Samples

- Video import (drag & drop and file picker)
- Auto video processing (frame deduplication, duration adjustment, auto speed-up)
- Manual trimming (select 15–30 second clips)
- Device presets (iPhone, iPad, Mac) with resolution scaling
- Video preview with playback controls
- App Store compliance checking
- MP4 export with H.264/AAC encoding

## Adding New Samples

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on adding new sample videos.

## License

[MIT License](LICENSE)

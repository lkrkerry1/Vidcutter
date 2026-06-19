# Vidcutter

An automatic video editor for Celeste map clears. It detects room completions, berry/cassette collects, and level clears from game events, then cuts your recording into a single highlight clip per level using FFmpeg.

## Requirements

- [Everest](https://everestapi.github.io/) (Celeste mod loader) 1.4673.0+
- Optional: [SpeedrunTool](https://gamebanana.com/mods/150053) 3.27.0+ for savestate support
- Optional: [VivHelper](https://gamebanana.com/mods/150166) 1.14.0+ for inter-room pass detection

## Usage

1. **Configure your video folder** in Mod Options → Vidcutter. Default is your system Videos folder.
2. **Record in .mkv format** (recommended). In OBS: Settings → Output → Recording → Matroska Video (.mkv). .mp4 and other common formats also work, but .mkv is safest — if a recording crashes, .mkv files are still usable while .mp4 files are typically lost.
3. **Launch the game first**, then start recording. The mod uses your game session's log events to find matching video files.
4. **Play through one or more levels** while recording. The mod automatically logs room clears, deaths, collectibles, and level completions.
5. **Stop the recording** after you finish playing. Wait a moment for the file to finalize.
6. **Open Mod Options → Vidcutter → Cut Video(s)**. You will see a list of detected videos with the levels found in each one.
7. **Select the levels** you want to process and choose **Process** (or **Process and Delete rows** to also remove the log entries after cutting).
8. Output clips are saved as `Vidcutter_<LevelName>.mp4` in your video folder.

### Quick-cut from last savestate

Bind a key in the mod settings for **Cut From Last Savestate**. During gameplay, pressing this key will immediately cut a clip from your last savestate to the current moment in the latest recording.

### FFmpeg

If FFmpeg is already installed and available in your PATH, the mod uses it directly. Otherwise it will automatically download FFmpeg on first use.

## Building

```bash
dotnet restore
dotnet build -c Debug       # Debug build
dotnet build -c Release     # Release build + creates .zip package
```

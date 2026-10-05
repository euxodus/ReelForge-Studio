# ReelForge Studio: Installation Guide

ReelForge Studio is an Android video editor: multi-track timeline, 120 subtitle styles, 36 audio effects, a 10-band equalizer, ElevenLabs AI voice and auto captions, and export to MP4, WebM, MKV, MP3, WAV, M4A, Opus, SRT and VTT.

There are two ways to get the APK onto your phone. Option A needs no software on a computer and can be done entirely from a phone.

---

## Option A: Build the APK for free with GitHub (recommended)

GitHub builds the APK in the cloud and gives you a download link.

### 1. Create a GitHub account
Go to https://github.com and sign up (free).

### 2. Create a repository
1. Tap **+** (top right), then **New repository**.
2. Name it `reelforge-studio`.
3. Choose **Public** or **Private** (both work).
4. Tap **Create repository**.

### 3. Upload the project
1. Unzip `ReelForge-Studio.zip` on your computer or phone.
2. In your new repository, tap **uploading an existing file** (or **Add file > Upload files**).
3. Drag in **everything inside** the `ReelForge-Studio` folder: `www`, `scripts`, `resources`, `.github`, `package.json`, `capacitor.config.json`, `.gitignore`, and the guide files.
4. Tap **Commit changes**.

**Important: the `.github` folder.** It is a hidden folder and some phones and file managers skip it. Check that your repository shows a `.github` folder after uploading. If it is missing:
1. Tap **Add file > Create new file**.
2. Type the file name exactly: `.github/workflows/build-apk.yml`
3. Open `build-apk.yml` from the zip in any text editor, copy everything, and paste it in.
4. Tap **Commit changes**.

### 4. Build the APK
1. Open the **Actions** tab of your repository.
2. If GitHub asks, tap **I understand my workflows, go ahead and enable them**.
3. Tap **Build Android APK** on the left, then **Run workflow > Run workflow**.
4. Wait 5 to 8 minutes until the run shows a green check mark.

(Every time you upload changes to the project later, a new APK is built automatically.)

### 5. Download the APK on your phone
1. On your phone, open your repository on github.com.
2. Tap **Releases** (right side on desktop, lower down on mobile).
3. Open the newest release, e.g. **ReelForge Studio, build 1**.
4. Tap the file `ReelForge-Studio-build-1.apk` to download it.

(Alternative: in the **Actions** tab, open the finished run and download **ReelForge-Studio-APK**. This arrives as a zip, so you have to unzip it first. Releases is easier.)

### 6. Install it on your phone
1. Open the downloaded `.apk` (from the notification or the **Files / Downloads** app).
2. If Android says installing unknown apps is not allowed, tap **Settings** and turn on **Allow from this source** for your browser or file manager, then go back.
3. Tap **Install**.
4. If Google Play Protect shows a warning, tap **More details > Install anyway**. This is normal for any app not installed from the Play Store.
5. Open **ReelForge Studio** from your app drawer.

---

## Option B: Build on your computer with Android Studio

1. Install **Node.js 22 or newer**: https://nodejs.org
2. Install **Android Studio**: https://developer.android.com/studio (open it once so it downloads the Android SDK).
3. Open a terminal in the `ReelForge-Studio` folder and run:
   ```
   npm install
   npm run android:create
   npm run android:open
   ```
4. In Android Studio: **Build > Build App Bundle(s) / APK(s) > Build APK(s)**.
5. Click **locate** in the popup. Your APK is at `android/app/build/outputs/apk/debug/app-debug.apk`.
6. Copy it to your phone (USB, Google Drive, email) and install it as in step 6 above.
   Or connect your phone with USB debugging on and press the green **Run** button to install it directly.

After you change files in `www/`, run `npm run android:sync` and build again.

## Try it in a browser first (optional)

On a computer with Node.js installed: run `npm run serve` in the project folder and open http://localhost:8080 in Chrome. Everything works except saving straight to the phone's gallery.

---

## Using the app

**Add media.** Tap **Media** (or the big + button) to pick videos and photos. You can select several at once. Tap **Audio** to add music, sound from a video, or an AI voice.

**Timeline.**
- Swipe the timeline left or right to move the playhead (the white line).
- Pinch with two fingers, or use the zoom buttons, to zoom.
- Tap a clip to select it. Drag the **yellow handles** to trim. Drag a selected audio or text clip to move it.
- **Split** cuts the selected clip (or the clip under the playhead) at the playhead.
- Use the **undo/redo** arrows at the top any time.

**Video and photo clips** (tap a clip): Split, Volume, Voice FX, Equalizer, Extract audio, Filters (12 color looks), Fades, Move left/right, Duplicate, Delete. Photos also have **Duration** and **Motion** (zoom and pan).

**Audio.** Select an audio clip for Volume with fade in/out, **Voice FX** (36 effects: Podcast, Studio voice, Broadcast, Bass mic, Telephone, Megaphone, Robot, Echo, Cathedral, 8D audio and more) and the **Equalizer** (10 bands, 14 presets). Tap an effect to hear it right away.

**Subtitles.**
- **Text** adds a subtitle at the playhead.
- **Styles** opens 120 subtitle styles: word highlight, boxed, outline, neon, one-word and more. Change size and colors underneath.
- Drag any subtitle on the preview to place it anywhere; pinch it to resize. **Position** has quick Top / Middle / Lower / Bottom buttons and an "Apply to all" switch.

**AI voice (ElevenLabs).**
1. Get an API key at https://elevenlabs.io (Profile / Developers > API keys).
2. In the app, tap **AI voice**, paste the key and tap **Save**. Your voices load automatically.
3. Write your script, pick a voice, model, stability, speed and so on.
4. Keep **Turn the script into synced subtitles** on and tap **Generate voice**.
The voice is added to the timeline and the text becomes word-timed subtitles. Drag the voice clip and its subtitles move with it. Trim it, add music, and apply effects like any other audio.

**Auto captions.** Tap **Captions > Generate captions** to transcribe your video's speech with ElevenLabs Speech-to-Text (uses the same API key). You can also import or delete SRT/VTT subtitle files there.

**Format.** Choose 9:16, 16:9, 1:1, 4:5, 4:3, 3:4 or 21:9, fit or fill, and a background (blur or color).

**Export.** Tap **Export** (top right):
- **Video:** MP4, MP4 HEVC/AV1, WebM VP9/VP8/AV1/H.264, MKV. 480p to 4K, 24 to 60 fps, four quality levels, subtitles burned in or not.
- **Audio only:** MP3 (96 to 320 kbps), WAV, M4A, Opus, OGG.
- **Subtitles:** SRT, VTT, TXT.

Files are saved to **Movies/ReelForge** (video), **Music/ReelForge** (audio) or **Documents/ReelForge**. Tap **Share or save to…** to send them to Gallery, Google Drive, WhatsApp and so on.

---

## Good to know

- **Export runs in real time.** A 60-second video takes about 60 seconds. Keep the screen on and the app open while exporting.
- **Formats depend on your phone.** Formats your phone cannot encode are greyed out. MP4 (H.264) works on almost every phone. MOV and AVI are not available.
- **Projects are not saved when you close the app.** Export before leaving.
- **Very long or 4K videos** use a lot of memory. If the app struggles, use shorter clips or export at 1080p.
- **Your ElevenLabs key** is stored only on your phone and sent only to ElevenLabs. ElevenLabs charges your account per character (voice) and per minute (captions).
- **AI voice and captions need internet.** Everything else works offline.

## Troubleshooting

| Problem | Fix |
|---|---|
| No **Build Android APK** in the Actions tab | The `.github/workflows/build-apk.yml` file is missing. Create it as described in step 3. |
| Build failed (red X) | Open the run to read the error. Usually a file was not uploaded; check that `package.json`, `capacitor.config.json`, `www`, `scripts` and `resources` are all in the repository root (not inside an extra folder). Then **Re-run jobs**. |
| "App not installed" | Uninstall any older ReelForge version first, then install again. |
| A video won't import | That video's codec is not supported by the phone. Re-save it as MP4 (H.264) with another app. |
| AI voice error 401 | The API key is wrong or expired. Paste a new one and tap Save. |
| AI voice error 402 or quota | Your ElevenLabs plan has run out of credits. |
| Exported video stutters | Choose a lower resolution or 30 fps, close other apps, and keep the screen on. |
| Can't find the exported file | Tap **Share or save to…** after export and send it to Gallery, Files or Drive. |

## Project structure

```
www/            The app: index.html, css/, js/ (core.js, ui.js, audio.js, presets.js), fonts/, vendor/
resources/      App icon and splash screens
scripts/        patch-android.mjs (adds permissions, icon, portrait mode)
.github/        GitHub workflow that builds the APK
capacitor.config.json, package.json
```

App ID: `com.reelforge.studio`. Requires Android 7.0 or newer.

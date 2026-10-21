# Mandarin Path 2.0

A mobile-first, installable Mandarin-learning PWA built with plain HTML, CSS and JavaScript. No account, backend or framework is required.

## What's included

- A responsive dashboard, progress overview, daily-goal setting and Level 0–10 learning map.
- 11 stages with 3 authored chapter lessons per stage (33 chapters total), with vocabulary, tone-marked Pinyin, English meanings, grammar explanations, examples and tips.
- Guided comprehension questions, feedback, vocabulary review, flashcards, tone practice, listening activity, sentence-order practice, level checkpoints and gated progression.
- Local progress storage with `localStorage`, including chapter completion, scores, review words, goal and preferences.
- PWA manifest, service worker and local SVG illustrations/icons.
- Speech uses a recognisable female Mandarin voice installed on the learner’s device. The app does not silently fall back to bundled synthetic clips or an unknown/male voice.
- Optional browser microphone recording, when supported and permitted.

## Run locally

A service worker and install prompt require `localhost` or HTTPS. Opening `index.html` directly with `file://` will let you inspect the interface but will not enable full PWA/offline features.

### Option A: Python

```bash
python -m http.server 8000
```

Open `http://localhost:8000`.

### Option B: VS Code

Use the Live Server extension and open the project root.

## Deploy to GitHub Pages

1. Create a GitHub repository and upload the contents of this folder (keep the relative paths intact).
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
4. Wait for the deployment URL. Open it over HTTPS once while online so the service worker can cache the app shell.
5. After changing files, update the cache version in `sw.js` (`CACHE`) so returning devices fetch the new app shell.

All URLs are relative, so the project works from a GitHub Pages project subpath.

## Install on devices

- **iPhone / iPad:** Open the deployed HTTPS URL in Safari → Share → Add to Home Screen → Add.
- **Android phone / tablet:** Open the HTTPS URL in Chrome → menu → Install app or Add to Home screen.
- **Desktop:** Open in a supported browser such as Chrome or Edge and use the install icon/menu when offered.

Installation prompts differ by OS and browser. The app can still be used as a website when installation is unavailable.

## Offline behaviour

The service worker precaches the app shell, original mascot illustration and curriculum. After the first successful online load, core lessons and practice screens work offline. A new deployment requires the device to reconnect to receive updated files. Device speech synthesis depends on browser/device support and may not work offline on every platform.

## Progress and privacy

Progress is stored in this browser on this device. There is no login or server sync. Browser storage can be erased by clearing site data; use **Settings → Export progress** to download a JSON backup. The exported file can be kept privately by the learner.

## Audio and teaching limitations

- Audio speaks the Chinese characters using a recognisable female Mandarin voice installed on the device. Voice selection prefers identified female voices and prioritises Standard Mandarin (Mainland China) where available. The Settings screen includes a voice test.
- Browser voice lists do not reliably expose gender or naturalness. If no recognisable female Mandarin voice is available, the app shows a message rather than using an unknown/male voice or synthetic clips. Install/download a female Mandarin voice in device language/accessibility settings and reload.
- The Numbers and Age chapter now explicitly teaches 一到十 (1–10), with tone-marked Pinyin: yī, èr, sān, sì, wǔ, liù, qī, bā, jiǔ, shí.
- Pinyin is curriculum text; speech is synthesized from Chinese characters. The number entries were checked, but the entire 33-chapter curriculum has not yet received a full native-speaker audit. Device TTS can still sound robotic, and no app-side setting can guarantee studio-quality natural speech. For a dependable teaching standard, add licensed native-speaker recordings or a paid high-quality Mandarin TTS service and review every recording against the Pinyin.
- Re-deploy the updated files and reload the app online once. The service worker cache version was incremented.
- Speaking exercises offer listen-and-compare and local recording. There is **no automated tone or pronunciation scoring**.
- Character handwriting stroke animation, detailed speech assessment, advanced spaced-repetition scheduling, authentic licensed media, and a validated CEFR/HSK placement exam are not implemented in this foundation.
- The curriculum is a structured learning foundation, not a guarantee of HSK certification or B2 proficiency. Level 10 should be treated as advanced practice, not a certified B2 equivalence.

## Project files

- `index.html` — app shell and navigation
- `styles.css` — responsive design system
- `app.js` — rendering, interaction, progress, quizzes and settings
- `content.js` — lesson curriculum data
- `assets/img/mascot.svg` — original animated-friendly red-panda learning mascot
- `manifest.webmanifest` — install metadata
- `sw.js` — offline caching
- `assets/img/` — local SVG visuals

## Testing checklist

1. Serve on localhost or HTTPS.
2. Complete Level 0 Chapter 1 and confirm its completion persists after refresh.
3. Confirm subsequent chapters unlock in order.
4. Complete all chapters in a level and pass its checkpoint at 80% to unlock the next level.
5. Add a word to review, refresh, and verify it remains in the review deck.
6. Test the female Mandarin voice button, slow audio setting, number lesson, and microphone recording in a browser that supports them.
7. In Chrome DevTools, use Application → Service Workers and Cache Storage to inspect offline caching; then enable Offline and reload.
8. Test narrow phone width and tablet/desktop layouts.

This is a functional foundation with real authored content across all 11 levels; some advanced learning systems listed above remain future development rather than being represented as complete.

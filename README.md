# Ulric-X MD v3.0
> Powerful Multi-User WhatsApp Bot — INSTANT Pair Codes, Persistent Sessions, 1658+ Commands

**Owner:** ULRIC X SHAH  |  **Number:** +923189335011  |  **Version:** 3.0

---

## 🎉 What's New in v3

### ✅ FIXED: Pair Code Generation
- **Instant pair codes** (1-3 seconds, not 60 seconds like v2)
- Real WhatsApp pair codes via `requestPairingCode()` API
- WhatsApp automatically sends notification to user's phone
- User taps notification → opens Linked Devices → enters code → connected!

### ✅ FIXED: Session Persistence
- Sessions stored in `/sessions/<number>@s.whatsapp.net/`
- Auto-reconnect on disconnect (3-second backoff)
- No logout on bot restart
- Survives Railway/Render redeployments when persistent volume mounted

### ✅ NEW: Beautiful UI
- Dark gradient theme with animated glow orbs
- **Pair code section at TOP** (was at bottom in v2)
- Loading animation with rotating messages
- Mobile-responsive
- Copy-to-clipboard button
- Step-by-step instructions with WhatsApp notification hint

---

## 🚀 Quick Deploy on Railway (NO Credit Card needed!)

### Step 1: Push to GitHub
```bash
cd ulric-x-v3
git init
git add .
git commit -m "Ulric-X MD v3"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/ulric-x-md.git
git push -u origin main
```

### Step 2: Deploy on Railway
1. Go to **https://railway.app** → Login with GitHub
2. **"New Project"** → **"Deploy from GitHub repo"**
3. Select your `ulric-x-md` repo
4. Railway auto-detects Node.js
5. Go to **"Variables"** tab, add:
   ```
   ADMIN_PASS=your_strong_password
   SESSION_SECRET=random_secret_string
   MAX_PAIR_USERS=1000
   NODE_ENV=production
   ```
6. Go to **"Settings"** → **"Networking"** → **"Generate Domain"**
7. Your URL: `https://ulric-x-md-production.up.railway.app`

### Step 3: Add Persistent Volume (CRITICAL)
1. Go to **"Settings"** → **"Volumes"**
2. **"Add Volume"**
3. Mount path: `/app/sessions`
4. Size: 1 GB

This ensures users don't get logged out when Railway redeploys.

---

## 🎯 How Pairing Works (Real Flow)

1. **User visits** `https://YOUR-URL/`
2. **Enters WhatsApp number** with country code (e.g. `923189335011`)
3. **Clicks "Get Pair Code"**
4. **Bot calls Baileys `requestPairingCode()`** → gets 8-digit code in 1-3 seconds
5. **WhatsApp AUTOMATICALLY sends a push notification** to user's phone:
   > "Tap to link a new device"
6. **User taps notification** → opens WhatsApp → Linked Devices screen
7. **User taps "Link a Device"** → "Link with phone number instead"
8. **User enters the 8-digit code** shown on web
9. ✅ **Connected!** Bot sends broadcast notification to owner + groups

---

## 🌐 Web Panel URLs

| URL | Purpose |
|-----|---------|
| `https://YOUR-URL/` | 🟢 Pair page (instant code generation) |
| `https://YOUR-URL/panel` | 🟢 User dashboard (paired users list) |
| `https://YOUR-URL/admin` | 🟢 Admin panel (login + broadcast + unpair) |
| `https://YOUR-URL/api/state` | 🟢 JSON status (use for monitoring) |
| `https://YOUR-URL/api/pair` | 🟢 Pair API (POST with `{"number":"923xxx"}`) |

---

## 📦 Commands (1658 total)

| Category | Count | Examples |
|----------|-------|----------|
| `main`     | 21  | `.menu`, `.allmenu` |
| `owner`    | 33  | `.broadcast`, `.block`, `.autobio` |
| `group`    | 30  | `.kick`, `.tagall`, `.mute` |
| `download` | 90  | `.ytmp3`, `.tiktoknowm`, `.igreel`, `.mediafire`, `.apkpure` |
| `sticker`  | 311 | `.sticker`, `.take`, `.ssepia`, `.stneonpink` |
| `fun`      | 83  | `.ship`, `.8ball`, `.slots`, `.rizz` |
| `game`     | 15  | `.tictactoe`, `.hangman`, `.trivia` |
| `anime`    | 13  | `.anime`, `.manga`, `.waifu` |
| `ai`       | 132 | `.ai`, `.aimage`, `.aianime2`, `.aicyberpunk2` |
| `logo`     | 269 | `.logo1` ... `.logo200`, `.wolflogo` |
| `voice`    | 64  | `.tts`, `.ttsur`, `.ttsen`, `.ttsfr` |
| `image`    | 47  | `.sepia`, `.grayscale`, `.vintage` |
| `media`    | 76  | `.bass`, `.nightcore`, `.slowed`, `.8d` |
| `utility`  | 28  | `.weather`, `.qr`, `.currency`, `.github` |
| `religion` | 10  | `.quran`, `.hadith`, `.prayer`, `.kalima` |
| `info`     | 46  | `.botinfo`, `.system`, `.worldtime` |
| `text`     | 23  | `.fontbold`, `.zalgo`, `.morse` |
| `random`   | 55  | `.dog`, `.cat`, `.quote`, `.fact` |
| `reaction` | 238 | `.hug`, `.kiss`, `.slap`, `.bruh` |
| `convert`  | 17  | `.tojpg`, `.resize`, `.length` |
| `search`   | 43  | `.google2`, `.bing`, `.movie`, `.recipe` |
| `database` | 14  | `.setnote`, `.todo`, `.setmood` |

Run `.menu` in WhatsApp to see all categories. Run `.allmenu` to see all 1658 commands.

---

## 🆓 Free APIs Used (No Key Required)

- **Pollinations.AI** — AI text + image generation
- **Cobalt API** — YouTube, TikTok, Instagram, Facebook, Twitter, Pinterest, Reddit, SoundCloud, Vimeo, Snapchat, Twitch, LinkedIn downloads
- **ytdl-core** — YouTube direct download
- **Google TTS** — 60+ language voice notes
- **AlQuran Cloud** — Quran verses
- **Hadith Gading** — Bukhari, Muslim, etc.
- **Aladhan** — Prayer times, Qibla, Hijri date
- **Jikan** — Anime/manga database
- **Open-Meteo** — Weather + geocoding
- **CoinGecko** — Crypto prices
- **GitHub API** — User/repo info
- **Wikipedia REST API** — 7 language editions
- **NASA APOD** — Astronomy picture
- **TMDB** — Movie/TV info
- **Stack Exchange** — Stack Overflow search
- **+ many more**

---

## 🐳 Docker / VPS / Render Deployment

See `DEPLOYMENT.md` for full Docker, VPS, Render, and Katabump instructions.

---

## 📂 Project Structure

```
ulric-x-v3/
├── index.js              # Entry point
├── pair.js               # INSTANT pair code generator (v3 improved)
├── server.js             # Express web panel
├── handler.js            # Message dispatcher
├── config.js             # Bot config
├── lib/                  # Utilities, store, menu
├── commands/             # 1658 commands (22 files)
├── public/               # Beautiful web UI
│   ├── index.html        # Pair page (pair code at top)
│   ├── panel.html        # User dashboard
│   ├── admin.html        # Admin panel
│   └── style.css         # Gradient theme
├── sessions/             # WhatsApp auth (persistent)
├── database/             # JSON storage
└── logs/                 # PM2 logs
```

---

## 🛡️ Disclaimer

This bot uses the WhatsApp Web API via Baileys (unofficial library). Use responsibly. Authors are not responsible for account bans. Do not use for spam or illegal activities.

---

## 📝 Credits

- **Baileys** by WhiskeySockets — WhatsApp Web API
- **Pollinations.AI** — Free AI generation
- **Cobalt** — Free media downloader
- **All free public APIs** used throughout

Built with ❤️ by **ULRIC X SHAH** for the Ulric-X MD project.

# AI-EMAIL
# 🐉 Dragon AI — Email & Build Status Dashboard
### dragoncomputers.eu · Powered by Claude AI + Easybill

---

## 🚀 Quick Start (5 minutes)

### 1. Install Node.js
Download from **https://nodejs.org** — choose the LTS version.

### 2. Install dependencies
Open a terminal in this folder and run:
```bash
npm install
```

### 3. Add your API keys
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```
Then open `.env` and fill in your keys:

| Key | Where to get it |
|-----|----------------|
| `VITE_ANTHROPIC_KEY` | console.anthropic.com → API Keys |
| `VITE_EASYBILL_KEY` | easybill.de → Settings → API |
| `VITE_OUTLOOK_TOKEN` | graph.microsoft.com/graph-explorer → sign in → copy token |

### 4. Run the app
```bash
npm run dev
```
Open **http://localhost:5173** in your browser. ✅

---

## 🔑 Getting Your API Keys

### Claude API Key
1. Go to **console.anthropic.com**
2. Sign up or log in
3. Go to **API Keys** → Create new key
4. Copy and paste into `.env`

### Easybill API Key
1. Log into **easybill.de**
2. Go to **Einstellungen (Settings) → API**
3. Generate a Bearer token
4. Copy and paste into `.env`

### Outlook Access Token (expires every 60 min)
1. Go to **graph.microsoft.com/graph-explorer**
2. Click **Sign in with Microsoft** (use your work account)
3. Click your avatar (top right) → **Access token** tab
4. Copy the token and paste into `.env`
> **Note:** For production use, set up proper OAuth2 refresh tokens via Azure AD.

---

## 📱 Features

### 🏗 Build Status Tab
- All 44 Firebreather builds from dragoncomputers.eu
- Live cross-check against Easybill parts inventory
- **✅ BUILDABLE** / **⚠️ PARTIAL** / **❌ BLOCKED** per build
- Component-level stock details for every build

### 📧 Inbox Tab
- AI email classification (Order / Budget Build / Stock / Tech Support / Upgrade)
- Auto-generated replies using real catalog data
- "Buildable Matches" shows which Firebreather models are ready to ship

### 🔩 Parts Stock Tab
- Full Easybill inventory by category (CPU / GPU / RAM / Storage)
- Live sync button — refreshes all stock from Easybill

---

## 🛠 Build for Production
```bash
npm run build
```
Files go to the `dist/` folder — deploy anywhere (Netlify, Vercel, your own server).

---

## ⚠️ Security Notes
- Never commit your `.env` file (it's in `.gitignore`)
- The Anthropic API key gives access to paid AI — keep it private
- Outlook tokens expire after 60 minutes

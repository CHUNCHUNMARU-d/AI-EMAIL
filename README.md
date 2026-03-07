# Dragon AI — Setup Guide
### AI-powered email & build intelligence for dragoncomputers.eu

---

## Table of Contents

1. [Requirements](#1-requirements)
2. [Installation](#2-installation)
3. [API Keys — Complete Setup Guide](#3-api-keys--complete-setup-guide)
   - [Claude API Key (Anthropic)](#31-claude-api-key-anthropic)
   - [Easybill API Key](#32-easybill-api-key)
   - [Outlook Access Token (Microsoft)](#33-outlook-access-token-microsoft)
4. [Adding Keys to the App](#4-adding-keys-to-the-app)
5. [Running the App](#5-running-the-app)
6. [Troubleshooting](#6-troubleshooting)

---

## 1. Requirements

Before you start, you need **Node.js** installed on your computer.

**How to install Node.js:**
1. Go to **https://nodejs.org**
2. Click the big green **"LTS"** button (recommended version)
3. Run the downloaded installer
4. Click **Next** through all steps — default settings are fine
5. Restart your computer after installation

**Verify it worked** — open a terminal and type:
```
node --version
```
You should see something like `v20.11.0`. If you see a version number, you're ready.

> **How to open a terminal:**
> - **Windows:** Press `Win + R`, type `cmd`, press Enter
> - **Mac:** Press `Cmd + Space`, type `Terminal`, press Enter

---

## 2. Installation

**Step 1 — Unzip the project**

Unzip the `dragon-ai.zip` file. You will get a folder called `dragon-ai`.

**Step 2 — Open the terminal in that folder**

- **Windows:** Open the `dragon-ai` folder, hold **Shift** and right-click inside it, then click **"Open PowerShell window here"** or **"Open Terminal here"**
- **Mac:** Open Terminal, type `cd ` (with a space after), then drag the `dragon-ai` folder into the terminal window and press Enter

**Step 3 — Install dependencies**

Type this command and press Enter:
```
npm install
```

This downloads everything the app needs. It takes about 30–60 seconds. You will see a lot of text scroll by — that is normal.

---

## 3. API Keys — Complete Setup Guide

The app needs up to **3 API keys**. Below is a step-by-step guide for each one.

> **What is an API key?**
> An API key is like a password that allows the app to connect to an external service (Claude AI, Easybill, Microsoft). Without it, those features won't work.

---

### 3.1 Claude API Key (Anthropic)

This key powers all AI features: email analysis, reply generation, and catalog matching.

**How to get it — step by step:**

1. Go to **https://console.anthropic.com**

2. Click **"Sign Up"** (or log in if you already have an account)

3. After logging in, look at the left sidebar and click **"API Keys"**

4. Click the **"Create Key"** button

5. Give the key a name — for example: `dragon-ai`

6. Click **"Create Key"**

7. **Important:** You will see the key only once. It looks like this:
   ```
   sk-ant-api03-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

8. Click **"Copy"** immediately and paste it somewhere safe (like Notepad)

**Cost:** Anthropic charges per use. Analyzing emails costs roughly **€0.001–0.005 per email** depending on length. For a small shop with ~50 emails/day, the cost is under €5/month.

---

### 3.2 Easybill API Key

This key connects the app to your Easybill inventory so it can read live stock levels.

**How to get it — step by step:**

1. Go to **https://app.easybill.de** and log in to your account

2. Click your **company name** or **profile icon** in the top-right corner

3. In the dropdown menu, click **"Einstellungen"** (Settings)

4. In the settings page, look for the **"API"** section in the left menu and click it

5. You will see a page titled **"API-Zugangsdaten"** (API credentials)

6. Click **"API-Key erstellen"** or look for an existing key

7. The key looks like a long string of random characters:
   ```
   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
   ```

8. Copy it and save it somewhere safe

> **Note:** If you don't have an Easybill account yet, the app still works in demo mode with sample stock data. You can add the key later.

---

### 3.3 Outlook Access Token (Microsoft)

This key allows the app to read your real inbox and send replies from your Microsoft 365 / Outlook account.

> **Important:** This token expires every **60 minutes**. You will need to refresh it each time you restart the app. For a permanent solution, see the note at the bottom of this section.

**How to get it — step by step:**

1. Go to **https://developer.microsoft.com/graph/graph-explorer** in your browser

2. You will see a page that looks like a developer tool with a dark sidebar on the left

3. Click the **"Sign in to Graph Explorer"** button (or the profile icon in the top-right)

4. A Microsoft login window will appear — sign in with your **work or business Microsoft account** (the same one you use for Outlook/Microsoft 365 at Dragon Computers)

5. After signing in, you will see your name appear in the top-right corner

6. Now click on your **profile picture / avatar** in the top-right corner of the page

7. A panel will slide open. Click the tab that says **"Access token"**

8. You will see a very long string of text — this is your access token. It starts with `eyJ...`

9. Click the **"Copy"** button next to it

> **Why does it expire?**
> Microsoft issues temporary tokens for security reasons. For a permanent connection, you would need to set up an Azure AD OAuth2 application — this is a more advanced setup. Contact a developer if you need this.

---

## 4. Adding Keys to the App

**Step 1 — Create the `.env` file**

In your terminal (make sure you are in the `dragon-ai` folder), type:

```
cp .env.example .env
```

This creates a new file called `.env` from the template.

**Step 2 — Open the `.env` file**

Open the `.env` file with any text editor:

- **Windows:** Right-click the file → **"Open with"** → **Notepad**
- **Mac:** Right-click the file → **"Open With"** → **TextEdit**
- **VS Code (recommended):** Type `code .env` in the terminal

The file looks like this when you open it:

```
VITE_ANTHROPIC_KEY=sk-ant-api03-your-key-here
VITE_EASYBILL_KEY=your-easybill-key-here
VITE_OUTLOOK_TOKEN=your-outlook-token-here
```

**Step 3 — Paste your keys**

Replace each placeholder with your actual key. Example:

```
VITE_ANTHROPIC_KEY=sk-ant-api03-ABCDEFGHxxxxxxxxxxxxxxxxxxxxx
VITE_EASYBILL_KEY=12345678-abcd-1234-abcd-123456789abc
VITE_OUTLOOK_TOKEN=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1d...
```

> **Rules:**
> - No spaces around the `=` sign
> - No quotes around the values
> - Each key on its own line

**Step 4 — Save the file**

Press `Ctrl + S` (Windows) or `Cmd + S` (Mac) to save.

---

## 5. Running the App

Once your keys are in the `.env` file, start the app:

```
npm run dev
```

Open your browser and go to:
```
http://localhost:5173
```

The Dragon AI dashboard will load. You will see three tabs at the top:

| Tab | What it does |
|-----|-------------|
| **Build Intelligence** | Shows all 25 Firebreather builds with live buildability status from Easybill stock |
| **Mail Processor** | AI-powered inbox — click any email to analyze it and generate a reply |
| **Parts Inventory** | Live view of all components and their stock levels from Easybill |

**To stop the app:** Go back to the terminal and press `Ctrl + C`

---

## 6. Troubleshooting

### The page is blank when I open the browser

1. Open the browser **developer console**: press **F12**, then click the **"Console"** tab
2. Look for red error messages
3. Common causes:
   - Missing `.env` file → run `cp .env.example .env` again
   - Wrong API key format → check there are no extra spaces or quotes in `.env`
   - Node.js not installed → run `node --version` to check

### `npm install` gives an error

- Make sure you are in the `dragon-ai` folder (not inside a subfolder)
- Try running as administrator:
  - **Windows:** Right-click on PowerShell and select "Run as administrator"
  - **Mac:** Add `sudo` before the command: `sudo npm install`

### The AI analysis doesn't work / gives an error

- Check that your `VITE_ANTHROPIC_KEY` in `.env` is correct (no typos)
- Make sure you have credits in your Anthropic account at **console.anthropic.com → Billing**
- The key must start with `sk-ant-api03-`

### Easybill sync fails

- Check that your `VITE_EASYBILL_KEY` is correct
- The app will continue working with demo stock data if the key is wrong

### Outlook token not working

- The token expires after **60 minutes** — go back to **graph.microsoft.com/graph-explorer** and copy a fresh token
- Make sure you are signed in with your business Microsoft account, not a personal one
- Required permissions: `Mail.ReadWrite` and `Mail.Send` — these are granted automatically when you sign in

### `npm run dev` says "port already in use"

Another app is using port 5173. Either close that app, or change the port in `vite.config.js`:
```js
server: {
  port: 3000  // change to any other number
}
```

---

## Security Notes

- **Never share your `.env` file** with anyone
- The `.env` file is already listed in `.gitignore` — it will never be accidentally uploaded to GitHub
- Your API keys give access to paid services — treat them like passwords
- The Anthropic key in particular can generate costs if shared

---

<p align="center">
  <img src="https://vvcs.tech/logo.png" alt="VideoVCS Logo" width="80" />
</p>

<h1 align="center">VideoVCS</h1>
<h3 align="center">Super Save for Video Editors — Auto-Save, Compare, Share, Review.</h3>

<p align="center">
  <a href="https://vvcs.tech"><img src="https://img.shields.io/badge/🌐_Live_Site-vvcs.tech-6C5CE7?style=for-the-badge&logoColor=white" alt="Live Site" /></a>
  <a href="https://github.com/FARINATTAR/VVC-Releases/releases/latest"><img src="https://img.shields.io/badge/⬇️_Download-Latest_Release-00B894?style=for-the-badge" alt="Download" /></a>
  <a href="https://github.com/FARINATTAR/VVC-Releases/releases/tag/v1.0.0"><img src="https://img.shields.io/badge/version-v1.0.0_Beta-FD79A8?style=for-the-badge" alt="Version" /></a>
  <a href="#"><img src="https://img.shields.io/badge/platform-Windows-0984E3?style=for-the-badge&logo=windows&logoColor=white" alt="Platform" /></a>
</p>

<p align="center">
  <em>"You exported, changed the timeline, and now the client wants the version from 2 hours ago.<br/>But you already overwrote your project file."</em>
</p>

<p align="center">
  <strong>VideoVCS makes sure that never happens again.</strong>
</p>

---

## 🌐 Try It Live

> **Website:** [**https://vvcs.tech**](https://vvcs.tech)
>
> Visit the landing page to see the product in action, explore the interactive demo, and download the desktop app.

---

## 🤔 The Problem

Every video editor has been here:

- 🗑️ **Overwritten cuts** — You tried a new creative direction, saved over the old project, and the client wants the previous version back. It's gone.
- 📱 **WhatsApp chaos** — *"Change the thing at 2:13"* — which version? Which clip? Which timeline?
- 🔄 **Manual backup hell** — `Project_v2_final_FINAL_real_final.prproj` — we've all been there.

---

## ✨ What VideoVCS Does

VideoVCS sits quietly on your desktop and watches over your editing workflow. It's **Git, but built for video editors** — no terminal, no learning curve.

| Feature | What Happens |
|:---|:---|
| 🎬 **Auto-Save on Export** | Every time you export from Premiere Pro or DaVinci Resolve, VideoVCS automatically saves a versioned snapshot of your project file and timeline XML. |
| 🔍 **Visual Timeline Comparison** | Click "Compare" between any two saves and see a **color-coded diff** — 🟢 added, 🔴 removed, 🟡 trimmed, 🔵 moved, 🟣 color graded. No guessing. |
| 🤖 **AI Smart Summaries** | Powered by Google Gemini — automatically generates human-readable changelogs like *"Trimmed intro by 2s, added 3 B-roll shots, applied color grade to interview clip."* |
| 🔗 **Instant Review Links** | One click → shareable public URL. Clients view the comparison and leave **timestamped comments** — no login, no app install needed. |
| ⏪ **One-Click Restore** | Restore any previous version directly to your original project path. VideoVCS backs up your current state first, so nothing is ever lost. |
| 📄 **PDF Changelog Export** | Generate professional PDF reports of changes for client handovers and production documentation. |
| 🔒 **Offline Licensing** | Ed25519 cryptographic licensing — works completely offline. No subscription servers, no internet dependency. |

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                   🎬 NLE Applications                    │
│         Premiere Pro (CEP Panel)  ·  DaVinci Resolve     │
└──────────────────────┬──────────────────────────────────┘
                       │ XML + .prproj / .drp
                       ▼
┌─────────────────────────────────────────────────────────┐
│              👁️ Intelligent File Watcher                 │
│    Temp Filter → Stability Debounce → XML Validation     │
└──────────────────────┬──────────────────────────────────┘
                       │ validated XML
                       ▼
┌─────────────────────────────────────────────────────────┐
│               ⚡ FastAPI Backend (:8000)                  │
│                                                          │
│   ┌─────────────┐  ┌──────────────┐  ┌──────────────┐  │
│   │  XML Parser  │  │  Comparator  │  │ Version Mgr  │  │
│   │  (lxml)      │  │  O(n+m) Diff │  │              │  │
│   └─────────────┘  └──────────────┘  └──────────────┘  │
│                                                          │
│   ┌─────────────┐  ┌──────────────┐  ┌──────────────┐  │
│   │ PDF/HTML     │  │  AI Service  │  │  Thumbnails  │  │
│   │ Reports      │  │  (Gemini)    │  │  (FFmpeg)    │  │
│   └─────────────┘  └──────────────┘  └──────────────┘  │
└──────────────────────┬──────────────────────────────────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
   ┌───────────┐ ┌──────────┐ ┌──────────┐
   │  SQLite   │ │  Local   │ │ Supabase │
   │ (metadata)│ │  Files   │ │  (cloud) │
   └───────────┘ └──────────┘ └──────────┘

┌─────────────────────────────────────────────────────────┐
│                  🖥️ Desktop App                          │
│        Electron Shell  ·  React (Vite) Dashboard         │
└─────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technologies |
|:---|:---|
| **Frontend** | React, Vite, TailwindCSS, Framer Motion |
| **Desktop Shell** | Electron (Windows system tray) |
| **Backend** | Python, FastAPI, Uvicorn, 40+ REST endpoints + WebSocket |
| **Database** | SQLite (local metadata), Supabase (cloud sharing & reviews) |
| **AI Engine** | Google Gemini 2.0 Flash |
| **Parsing** | lxml (FCP7 XML), custom O(n+m) timeline diff algorithm |
| **Licensing** | Ed25519 offline cryptographic signatures |
| **NLE Plugins** | Adobe CEP Panel (Premiere Pro), Python API (DaVinci Resolve) |
| **Hosting** | Cloudflare Pages (landing), Cloudflare R2 (media storage) |

---

## 📥 Download & Install

### Step 1 — Download

Head to the **[Latest Release](https://github.com/FARINATTAR/VVC-Releases/releases/latest)** page and download the Windows installer.

### Step 2 — Install

Run the installer — it sets up the Electron desktop app, the embedded Python backend, and the system tray icon.

### Step 3 — Connect Your NLE

- **Premiere Pro** → Install the CEP extension from the VideoVCS settings panel.
- **DaVinci Resolve** → Run the provided Python integration script.

### Step 4 — Start Editing

Export from your NLE as usual. VideoVCS watches in the background and auto-saves every version. Open the dashboard to compare, restore, or share.

---

## 💰 Pricing

| Plan | Price | What You Get |
|:---|:---|:---|
| **Free** | ₹0 | 2 projects, 10 saves per project |
| **Pro (Lifetime)** | ₹999 one-time (~$19) | Unlimited projects & saves, AI summaries, shareable review links, client feedback portals, PDF exports |

> 💡 **Free Pro access** for early adopters who provide feedback — [reach out](mailto:farinattar@gmail.com)!

---

## 🎬 The 2-Minute Demo

Want to see VideoVCS in action? Here's the flow:

1. **🎯 The Hook** — *"You exported, changed the timeline, client wants the old version. It's gone."*
2. **💾 Auto-Save** — Export from Premiere/Resolve → version instantly appears in the dashboard.
3. **🤯 The WOW Moment** — Click Compare. See the **color-coded visual diff**: green = added, red = cut, yellow = trimmed, purple = effects changed. *This is where people get it.*
4. **🔗 Client Review** — Click Share → open the public link → leave a timestamped comment → it appears live on the desktop app.
5. **⏪ Restore** — One click → old project file is back in Premiere/Resolve.

---

## 📬 Connect

- 🌐 **Website**: [vvcs.tech](https://vvcs.tech)
- 📧 **Email**: [farinattar@gmail.com](mailto:farinattar@gmail.com)
- 🐙 **GitHub**: [FARINATTAR](https://github.com/FARINATTAR)

---

<p align="center">
  <strong>Built with ❤️ for video editors who are tired of losing their best cuts.</strong>
</p>

<p align="center">
  <a href="https://vvcs.tech"><img src="https://img.shields.io/badge/🚀_Try_VideoVCS-vvcs.tech-6C5CE7?style=for-the-badge" alt="Try VideoVCS" /></a>
  <a href="https://github.com/FARINATTAR/VVC-Releases/releases/latest"><img src="https://img.shields.io/badge/⬇️_Download_Now-Latest_Release-00B894?style=for-the-badge" alt="Download Now" /></a>
</p>

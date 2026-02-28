# 🧠 MFLIX PRO — AI Control Center (Gemini Edition)

## 📅 February 28, 2026

---

## Kya Hai Ye?

Tumhari MFLIX PRO website ke andar ek **AI-powered admin assistant** add kiya hai jo:
- Puri website ko **real-time scan** karta hai (Firebase, VPS, Engine, Queue, Tasks)
- Problems **khud detect** karta hai — chhoti se badi tak
- **Google Gemini AI** se baat karo — problem batao, fix milega
- API key aur model **UI se change** kar sakte ho (Firebase mein save hoti hai)
- **Free hai** — Gemini API ka koi charge nahi

---

## 3 Tabs

### 📊 Tab 1: Dashboard
- **Overall Status** — Healthy / Warning / Critical — ek nazar mein pata chal jaye
- **7 Health Checks** — Firebase, Cron Engine, VPS Timer, VPS HubCloud, Queue, Tasks, Errors
- **Link Success Rate Bar** — Visual progress — kitne % links extract hue
- **Error Patterns** — Kaun si error baar-baar aa rahi hai aur kitni baar
- **Quick Ask Buttons** — 8 common problems ke shortcuts — click karo, AI se seedha jawab

### 💬 Tab 2: AI Chat
- Gemini AI se baat karo apni website ki kisi bhi problem ke baare mein
- **Diagnostics auto-attach** — AI ko khud pata hoga system ka current status
- **Conversation history** — pichle messages yaad rakhta hai
- **Token counter** — kitne tokens use hue
- **Model badge** — kaun sa model chala hai
- **Copy button** — response ek click mein copy
- **Clear chat** — pura chat mita do fresh start ke liye

### ⚙️ Tab 3: Settings
- **API Key Management** — Gemini API key add/change karo (encrypted Firebase mein save)
- **Model Selector** — 6 Gemini models mein se koi bhi chuno:

| Model | Speed | Quality | Best For |
|-------|-------|---------|----------|
| **Gemini 2.5 Flash Preview** | ⚡⚡⚡ | ⭐⭐⭐⭐⭐ | Latest & best |
| **Gemini 2.0 Flash** | ⚡⚡⚡ | ⭐⭐⭐⭐ | Recommended default |
| **Gemini 2.0 Flash Lite** | ⚡⚡⚡⚡ | ⭐⭐⭐ | Quick answers |
| **Gemini 1.5 Pro** | ⚡⚡ | ⭐⭐⭐⭐⭐ | Deep analysis |
| **Gemini 1.5 Flash** | ⚡⚡⚡ | ⭐⭐⭐⭐ | Reliable |
| **Gemini 1.5 Flash 8B** | ⚡⚡⚡⚡ | ⭐⭐ | Simple tasks |

- **Custom Instructions** — AI ko extra instructions do (e.g., "hamesha code examples de")
- Settings Firebase mein save hoti hai — refresh/close ke baad bhi rahegi

---

## New Files

| File | Kya Karta Hai |
|------|--------------|
| `app/api/ai/diagnose/route.ts` | 7 health checks — Firebase, Engine, VPS, Queue, Tasks, Errors |
| `app/api/ai/chat/route.ts` | Gemini API chat with full MFLIX system knowledge |
| `app/api/ai/settings/route.ts` | Save/load API key + model + custom instructions from Firebase |
| `components/AiControlCenter.tsx` | Complete AI Control Center UI (Dashboard + Chat + Settings) |

## Modified Files

| File | Kya Badla |
|------|-----------|
| `components/MflixApp.tsx` | Header mein 🧠 AI button + AiControlCenter integration |
| `vercel.json` | AI routes ka maxDuration added |

---

## Setup (2 minutes)

### Step 1: Gemini API Key Lo (FREE)
1. Jao: **https://aistudio.google.com/apikey**
2. Google account se login karo
3. "Create API Key" click karo
4. Key copy karo (AIzaSy... se start hogi)

### Step 2: Website Mein Add Karo
1. Website kholo
2. Header mein **🧠 purple Brain button** click karo
3. **Settings** tab mein jaao
4. API key paste karo
5. Model select karo (default: Gemini 2.0 Flash)
6. **Save Settings** click karo
7. ✅ Done! Ab AI Chat use karo

> ⚡ API key sirf ek baar add karni hai — Firebase mein save ho jayegi

---

## AI Ko Kya Pata Hai?

AI assistant ko in sab ka complete knowledge hai:

- Har API route ka flow (tasks, solve_task, stream_solve, cron, engine-status)
- Firebase collections ka structure (movies_queue, webseries_queue, scraping_tasks)
- Solvers ka kaam (HubCloud, HubDrive, HBLinks, HubCDN, GadgetsWeb, VPS Timer)
- Config values (timeouts, domains, retry limits)
- 4 SAKHT rules (VPS Protection, Zero-Drop, State Hydration, Complete Extraction)
- Common problems aur unke fixes
- Frontend architecture (Shield pattern, 3-layer data, polling)

---

## Architecture

```
Browser
  │
  └─→ 🧠 AI Button (Header)
       │
       └─→ AiControlCenter.tsx
            │
            ├─→ Dashboard Tab
            │    └─→ GET /api/ai/diagnose
            │         ├─→ Firebase check
            │         ├─→ Engine heartbeat
            │         ├─→ VPS Timer ping
            │         ├─→ VPS HubCloud ping
            │         ├─→ Queue analysis
            │         ├─→ Task success rate
            │         └─→ Error patterns
            │
            ├─→ Chat Tab
            │    └─→ POST /api/ai/chat
            │         ├─→ Read settings from Firebase
            │         ├─→ Attach diagnostics
            │         └─→ Google Gemini API
            │
            └─→ Settings Tab
                 └─→ GET/POST /api/ai/settings
                      └─→ Firebase (system/ai_settings)
```

## Firebase New Document

```
Collection: system
Document: ai_settings
Fields:
  - apiKey: string (encrypted Gemini API key)
  - model: string (e.g., 'gemini-2.0-flash')
  - customInstructions: string (max 2000 chars)
  - createdAt: ISO string
  - updatedAt: ISO string
```

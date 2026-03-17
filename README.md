# ContractLedger — Complete Setup & Deployment Guide

## What's Included
- `index.html`   — Full app (dashboard, investors, expenses, workers, reports)
- `sw.js`        — Service Worker (offline support)
- `manifest.json`— PWA manifest (install on Android)
- `icon-192.png`, `icon-512.png` — App icons

---

## Option 1: FREE Hosting — Netlify (Recommended, 5 minutes)

1. Go to https://netlify.com and sign up free
2. Drag-and-drop the entire `contract-tracker` folder onto Netlify dashboard
3. Get a URL like: `https://your-project.netlify.app`
4. Share this URL with all 4-5 team members

### Install on Android Phones:
1. Open the URL in Chrome browser
2. Tap the 3-dot menu → "Add to Home screen"
3. Tap "Add" — app icon appears on home screen
4. Works OFFLINE after first load ✅

---

## Option 2: FREE — GitHub Pages

1. Create GitHub account at github.com
2. Create new repository → upload all files
3. Go to Settings → Pages → Deploy from main branch
4. URL: `https://yourusername.github.io/contract-tracker`

---

## Option 3: Local Network (No Internet Required)

Run a simple server on one computer on the same WiFi:

### Using Python (any laptop):
```bash
cd contract-tracker
python3 -m http.server 8080
```
Access from any phone on same WiFi: `http://192.168.X.X:8080`

### Using Node.js:
```bash
npx serve .
```

---

## Option 4: Deploy to Your Own Server (VPS)

If you have a server (AWS, DigitalOcean, etc.):
```bash
# Upload files via FileZilla or SCP
scp -r contract-tracker/ user@yourserver.com:/var/www/html/

# Or with Nginx
sudo cp -r contract-tracker/* /var/www/html/
```

---

## Data Storage
- All data saved in browser's localStorage on each device
- **Data is per-device** — each user's device has its own data
- Use Backup/Restore to SYNC data between users

---

## Daily Backup Process (Important!)

1. Tap 📤 (backup icon) in header
2. Tap "Export Full Backup (JSON)"
3. Save file to Google Drive / WhatsApp to yourself
4. Other users can restore from backup if needed

### Recommended Daily Routine:
- End of day: One person exports backup
- Save to shared WhatsApp group or Google Drive folder
- Filename includes date automatically: `contractledger_backup_2024-01-15.json`

---

## Multi-User Sync (Manual)

Since this is a lightweight app (no server backend), sync works like this:
1. User A enters today's expenses → exports backup
2. Shares backup file to WhatsApp group
3. User B opens app → Backup → Restore from Backup
4. User B now has same data

### For automatic sync (advanced):
- Use Netlify + Supabase (free tier) for real-time sync
- Contact a developer to add Firebase backend (~2 hours of work)

---

## App Features Summary

| Feature | Details |
|---------|---------|
| Projects | Create multiple projects (Canal, Road, etc.) |
| Investors | Track who invested how much, share % |
| Expenses | 5 categories: Material, Labor, Machinery, Transport, Other |
| Workers | Add workers, daily wage tracking, attendance log |
| Dashboard | Balance, budget usage, 7-day chart |
| Reports | Full P&L, category breakdown, monthly summary |
| Export | PDF report (print), CSV data, JSON backup |
| Offline | Works without internet after first load |
| Install | Add to Android home screen as app |

---

## Browser Support
- ✅ Chrome (Android) — Best
- ✅ Samsung Internet
- ✅ Firefox (Android)
- ✅ Chrome/Edge (Desktop)
- ⚠️ Safari iOS — works but no push notifications

---

## Troubleshooting

**Data disappeared?**
- Each browser/device has separate data
- Restore from last backup

**App not installing?**
- Must be served over HTTPS (Netlify/GitHub Pages handles this)
- Local network (http://) won't show install prompt

**Backup file is large?**
- Normal — it contains all project data in JSON format

---

## Support
App built for: Canal, Road, Bridge, Building construction projects
Supports: Up to 50 projects, unlimited investors/expenses/workers

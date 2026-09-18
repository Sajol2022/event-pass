# EventPass — Professional QR Check-in & Live Cloud Sync

EventPass is a modern, responsive event guest management, ID card printing, and QR check-in platform designed for alumni reunions, jubilee celebrations, and major gatherings.

---

## ☁️ Real-time Cloud Database (Firebase Live Sync)
- **Multi-Device Instant Synchronization:** Mobile phones, laptops, and tablets automatically synchronize guest registrations, profile photos, and check-in statuses in real time (< 100ms latency).
- **Vercel & GitHub Ready:** Zero-backend server architecture. Simply enter your Firebase config in `index.html` (`HARDCODED_FIREBASE_CONFIG`) and push to GitHub.
- **Offline & Storage Resilient:** If internet connectivity drops at the gate, the app falls back transparently to `localStorage` and reconnects as soon as connection is restored.
- **Setup Guide:** See [`FIREBASE_SETUP.md`](FIREBASE_SETUP.md) for a 2-minute step-by-step setup guide.

---

## 🚪 Gate Check-In & Verification
- **One-Click Check-In Confirmation:** When a guest QR is scanned, their photo, name, batch, total headcount, and sub-guest count appear on screen with a prominent **`✓ গেস্ট চেক ইন (Confirm Check-In)`** button.
- **Duplicate Entry Protection:** Already attended guests immediately trigger an amber warning with check-in timestamp and volunteer name.
- **Smart QR:** The QR code encodes guest data directly (`EVENTPASS|ID|Name|Batch|Count|Code|Type`) so even an un-synced scanner can recognize guests immediately.
- **Mobile Camera Controls:** Features lens switcher (Wide, Macro, Telephoto) and gallery image scanner for blurry mobile lenses or dark environments.

---

## 🪪 ID Card & Badge Generation (Reunion Edition)
- **Exact Visual Design:** Clean card (`340px × 490px`) with royal blue layered wave footers, circular 1:1 profile photo ring with soft shadow, and structured info rows.
- **Front Page:** Header branding, institute title, event title, circular photo, full name, guest details, and wave footer.
- **Back Page:** EventPass branding, event title, custom quote, centered high-contrast QR code container, detailed event box, and bottom wave footer.
- **High-Resolution 2-Page PDF Download:** One-click download generates an exact aspect-ratio 2-page PDF ready for printing.
- **Single-Side PNG Downloads & Print Support:** Options to download Front PNG, Back PNG, or trigger browser print preview (`window.print()`).

---

## 👥 Volunteer Access & Gate Security
- **Multi-Gate Volunteers:** Assign volunteers to specific gates (e.g., Gate 1, VIP Gate, Front Desk).
- **Dedicated Scanner Mode:** Fast, full-screen volunteer scanner interface without access to admin dashboard or sensitive settings.
- **Credentials:** Default Volunteer password is `1234`, Admin password is `12345`.

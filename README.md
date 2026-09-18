# EventPass — QR Check-in + Valid User

This build keeps the existing one-time Entry Scan flow and adds a separate **Valid User** verification mode.

## Scanner modes
- **Entry Scan:** first valid scan marks the guest as Checked In; later scans show **Already Attended**.
- **Valid User:** checks whether the scanned QR value exactly matches a registered guest QR. It does **not** change attendance/check-in status.
- The camera uses the full preview for QR detection. The center square is only a visual guide.

## Important security note
This is still a browser/localStorage application. The Valid User mode is an exact registered-QR check, which is useful for preventing arbitrary/unregistered QR values. However, because the guest database and QR payload are stored client-side, this build is **not cryptographically counterfeit-proof**. For strong anti-counterfeit protection across multiple devices/scanners, use a backend (for example, Firebase/Firestore) and signed/random server-issued QR tokens.

## EmailJS
EmailJS settings are entered in Event Settings. The app sends `qr_url` and guest/event variables to the configured EmailJS template.


## ID Card & Badge Generation (Reunion 2026 Edition)
- **Exact Visual Design:** Clean white card (`360px × 610px`) with 3D isometric cube logo, royal blue layered wave footers, circular profile photo ring with soft shadow, and light-blue info cards.
- **Dynamic Event Date & Time:** Event Date and Event Time configured in Event Settings are published automatically to every ID card and throughout the application.
- **Front Page:** Includes isometric EventPass logo, event slogan, SSC Batch, Entry Type, circular photo, full name, role subtitle, and structured info box with blue SVG icons (Guest No, Guest Type, Entry Type, Entry Code, Guest ID, Phone Number, Email Address) and wave footer with event motto.
- **Back Page:** Includes EventPass branding, event title, custom italic quote (*“Same Friends New Stories”*), centered QR code container with "SCAN TO VERIFY" badge, detailed event box (Date & Time, Venue, Organized By, Valid For), elegant cursive *Friends Forever* script, and bottom wave footer.
- **High-Resolution 2-Page PDF Download:** One-click download generates an exact aspect-ratio 2-page PDF ready for printing.
- **Single-Side PNG Downloads & Print Support:** Options to download Front PNG, Back PNG, or trigger browser print preview (`window.print()`).
- **Form Input Styling:** Fully customized dark-theme dropdowns (`<select>`) with custom chevron arrows and sleek file upload button (`::file-selector-button`).

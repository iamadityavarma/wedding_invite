# Wedding Invitation — Aditya & Vineetha

Digital wedding invitation for **Aditya Varma & Vineetha Thrinethri**, December 12, 2026 at Soaring Heights, McKinney, Dallas TX.

Built with HTML, CSS, and vanilla JavaScript. Mobile-first, works on all devices.

---

## Run locally

```bash
npm install
npm run dev
```

Open `http://localhost:8080` in your browser.

---

## Deploy to Netlify (from GitHub)

1. Push this repo to GitHub (set to Private)
2. Go to [app.netlify.com](https://app.netlify.com) → **Add new site → Import from GitHub**
3. Use these build settings:
   - **Build command:** `npm run build:public`
   - **Publish directory:** `public`
4. Deploy — every `git push` will auto-redeploy

---

## Connect RSVP to Google Sheets

1. Create a Google Sheet with headers: `Timestamp | Name | Contact | Sumuhurtham | Lunch | Guests`
2. Open **Extensions → Apps Script**, paste this and save:

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  const data = JSON.parse(e.postData.contents);
  sheet.appendRow([new Date(), data.name, data.contact, data.ceremony, data.lunch, data.guests]);
  return ContentService.createTextOutput('OK');
}
```

3. **Deploy → New Deployment** → Type: Web app → Execute as: Me → Access: Anyone → Copy the URL
4. In `index.html` find this line and paste your URL:

```js
const RSVP_SHEET_URL = "PASTE_YOUR_WEB_APP_URL_HERE";
```

5. Run `npm run build:public` and redeploy

---

## Personalise

| What | Where |
|------|-------|
| Names, dates, venue | `index.html` |
| Couple photo | `assets/images/bg.webp` |
| App icon / favicon | `assets/images/icon-192x192.png` |
| QR code (unlocks Dec 9) | `assets/images/qr.webp` |
| Background music | `assets/music/pure-love-304010.mp3` |
| Colors & theme | `css/guest.css` (bottom section) |

---

## Guest link with name

Add `?to=Name` to the URL to show a personalised greeting:

```
https://your-site.netlify.app/?to=John%20Smith
```

---

## Tech stack

- Bootstrap 5.3.8
- Font Awesome 7.1.0
- AOS (scroll animations)
- Canvas Confetti
- Google Fonts (Sacramento, Josefin Sans)
- esbuild (bundler)

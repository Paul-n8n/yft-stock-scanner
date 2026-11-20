# YFT Stock Scanner

Telegram Mini App for barcode-based stock counting at Young Fishing Tackle.

## Flow
1. Staff opens `@yft_Stock_Count_bot` on Telegram
2. Types `scan` → bot sends a `📷 Open Scanner` button
3. Tap the button → this page opens inside Telegram
4. Point camera at each item's barcode
   - Each scan = +1 to that code's tally
   - Scan the same code again to add qty
   - Edit any row manually (tap qty), delete with ×
5. Tap **Submit** → bot asks `🔄 Recount` or `📋 New Stock Take`
6. Logged to Google Sheet with the staff username

## Tech
- Single-file HTML, no build step
- [html5-qrcode](https://github.com/mebjas/html5-qrcode) for barcode detection (Code 128, EAN-13, UPC, QR, etc.)
- [Telegram WebApp API](https://core.telegram.org/bots/webapps) for in-chat data return
- Hosted free on GitHub Pages

## Local test
Open `index.html` in a browser. Since camera + `sendData` need HTTPS + Telegram, local test shows a fallback alert with the JSON payload.

## Data payload sent to bot
```json
{
  "scans": [
    { "code": "0073113020613", "qty": 5 },
    { "code": "0073113020614", "qty": 2 }
  ],
  "scanned_at": "2026-11-20T..."
}
```

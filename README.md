# Denis Batinic SmArt

Projektstruktur für Cursor.

## Struktur
- index.html
- css/styles.css
- js/app.js
- images/

Hinweis:
- Bilder, Gemälde und weitere Assets können im Ordner images/ abgelegt werden.

## Netlify Deployment

1. Repo mit Netlify verbinden oder lokal deployen:
   ```bash
   npm install
   npx netlify login
   npx netlify init
   npx netlify deploy --prod
   ```
2. Im Netlify Dashboard unter **Site configuration → Environment variables** setzen:
   - `STRIPE_SECRET_KEY` = `sk_live_…`
   - `BASE_URL` = `https://denisbatinicsmart.com` (oder deine Netlify-URL)
3. Custom Domain `denisbatinicsmart.com` in Netlify unter **Domain management** eintragen.

Stripe Checkout läuft als Netlify Function unter `/api/create-checkout-session`.

## Lokaler Stripe-Server (optional)

1. Im [Stripe Dashboard](https://dashboard.stripe.com) API-Keys holen (Test: `sk_test_…`).
2. Im Ordner `server/`:
   ```bash
   cp .env.example .env
   npm install
   npm start
   ```
3. `STRIPE_SECRET_KEY` und `BASE_URL` in `server/.env` setzen.
4. Optional: feste Price ID statt dynamischer Preise – `STRIPE_PRICE_ID=price_123` in `.env`.
5. Für Produktion: Backend deployen (Railway, Render, Fly.io, …) und in `js/app.js` die Variable `STRIPE_API_URL` auf die Backend-URL setzen (oder vor dem Script in `index.html`: `window.STRIPE_API_URL = 'https://…';`).

Erfolgs- und Abbruchseiten: `success.html`, `cancel.html`.

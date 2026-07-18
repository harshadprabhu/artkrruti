# ArtKrruti — storefront

Handmade pooja & festival decor. Static enquiry-cart site: customers browse the
catalogue, build a list, and send it to the business WhatsApp in one tap.

## Structure

```
index.html               entire site (HTML + CSS + JS, no build step)
assets/logo.png          transparent brand logo
assets/logo-white.png    white version for the dark footer
assets/products/*.jpg    900x900 product photos
```

## Changing things

Everything you'll edit day-to-day lives at the top of the `<script>` block in `index.html`.

**WhatsApp number** — one line, change it and every button follows:
```js
const CONFIG = { whatsapp:"919821108371", brand:"ArtKrruti", site:"artkrruti.com" };
```
Format is country code + number, no `+` and no spaces.

**Categories** — `const CATS = [...]`. Each has a key `k`, display name `n`, colour `col`.

**Products** — `const PRODUCTS = [...]`. One object per item:
```js
{ id:"AK-TH1",            // shown to customers, travels into the WhatsApp message
  img:"1000732981",       // filename in assets/products (no .jpg)
  gal:["1000732929"],     // optional extra photos
  c:"thaal",              // category key
  price:649,              // number, or null for "Price on request"
  n:"Paithani Thaal Cover — Red",
  d:"Description shown in the product detail sheet.",
  f:["Ganpati","Diwali"] }// festival tags
```

To add a product: drop a square JPG into `assets/products/`, add one object to
the array. Nothing else to touch.

## Running locally

```
python3 -m http.server 8000
```
Then open http://localhost:8000

## Deploying

Any static host works. With Vercel:
1. Import this repo at vercel.com/new
2. Framework preset: **Other**. No build command, output directory `.`
3. Add your domain under Settings → Domains

## Known TODO

- [ ] Replace placeholder prices with real ones
- [ ] Confirm product sizes in descriptions
- [ ] Swap the placeholder WhatsApp number for the live business number
- [ ] Move the catalogue out of `index.html` into a database + admin panel (phase 2)

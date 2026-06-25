# Portfolio — Anvar Jamgirov

Minimalist single-page portfolio / CV. Toza HTML, CSS, JS — build, dependency yoki framework yo'q. Statik fayllar, istalgan joyga deploy bo'ladi.

```
portfolio/
├── index.html        # barcha kontent shu yerda
├── cv.html           # print uchun CV sahifasi (bundan cv.pdf yasaladi)
├── css/styles.css    # dizayn + light/dark theme
├── js/main.js        # theme toggle, mobil menyu, scroll reveal
├── assets/
│   └── cv.pdf         # Download CV tugmasi shuni oladi (cv.html dan generatsiya qilingan)
└── README.md
```

## 1. Lokal ko'rish

Hech narsa o'rnatish shart emas. `index.html` ni brauzerda ochsangiz ishlaydi.
Yaxshiroq usul (linklar to'g'ri ishlashi uchun) — kichik server:

```bash
# Python (sizda bor)
python3 -m http.server 8000
# keyin brauzerda: http://localhost:8000
```

## 2. To'ldirish kerak bo'lgan joylar (`index.html` ichida `TODO` deb belgilangan)

- [ ] Ism, sarlavha, hero pitch
- [ ] About paragraflari
- [ ] Skills — o'zingiz biladigan texnologiyalar
- [ ] Experience — har bir ish joyi (sana, kompaniya, natijalar)
- [ ] Projects — 2-4 ta eng kuchli loyiha + GitHub/demo linklari
- [ ] Ijtimoiy tarmoq linklari (`USERNAME` ni almashtiring): GitHub, LinkedIn, Telegram
- [ ] `assets/cv.pdf` — CV faylingizni qo'ying
- [ ] (ixtiyoriy) `og:image` — ulashganda ko'rinadigan rasm

## 3. jamgirov.uz domeniga deploy qilish

Eng oson, bepul va tez variantlar (statik sayt uchun ideal):

### Variant A — Cloudflare Pages (tavsiya)
1. Loyihani GitHub'ga push qiling.
2. Cloudflare Dashboard → Pages → "Connect to Git" → repo'ni tanlang.
3. Build sozlamasi: **build command** — bo'sh; **output dir** — `/` (root).
4. Deploy bo'lgach: Custom domains → `jamgirov.uz` qo'shing.
5. Domeningiz registratoridagi DNS'ni Cloudflare ko'rsatgan qiymatga sozlang (CNAME yoki nameserver).

### Variant B — Netlify
1. https://app.netlify.com → "Add new site" → repo'ni ulang (yoki papkani drag-and-drop).
2. Build command bo'sh, publish directory `.` (root).
3. Domain settings → "Add custom domain" → `jamgirov.uz` → DNS yo'riqnomasiga amal qiling.

### Variant C — GitHub Pages
1. Repo → Settings → Pages → Source: `main` branch, root.
2. Custom domain maydoniga `jamgirov.uz` yozing → repo ichida `CNAME` fayli yaratiladi.
3. Domen DNS'da `A` record'larni GitHub Pages IP'lariga / `CNAME`ni `<username>.github.io`ga yo'naltiring.

> HTTPS uch: yuqoridagi 3 variant ham bepul SSL sertifikatini avtomatik beradi.

## CV'ni yangilash

CV matni `cv.html` da. O'zgartirgandan keyin `assets/cv.pdf` ni qayta yasash:

**Oson yo'l:** `cv.html` ni brauzerda oching → `Cmd+P` → "Save as PDF" → `assets/cv.pdf` ga saqlang.

**Avtomatik (Chrome bilan):**
```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless=new --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="assets/cv.pdf" "file://$(pwd)/cv.html"
```

## Maslahatlar (recruiterlar uchun)
- Tezlik muhim: rasm qo'shsangiz siqib qo'ying (WebP), lazy-load qiling.
- Loyihalar bo'limi eng muhimi — har bir loyiha uchun **nima qildingiz + qaysi texnologiya + natija** yozing.
- CV PDF nomini tartibli qiling: `Anvar_Jamgirov_CV.pdf`.
- Linklarni tekshiring (GitHub, LinkedIn) — buzilgan link yomon taassurot qoldiradi.

# Kopelo ya Luthere (ELCB) - app package

Contents: `www/` is the complete app (works offline). Everything else is for building store apps.

## 0. Before anything else
The hymnal is (c) LCSA, first edition 1997. Get written permission from LCSA and any other rights holders before publishing an adapted ELCB version anywhere, including the stores.
Also complete the ELCB customization (publisher, edition note, LCSA-specific prayers) and proofread hymns 202-418, which were extracted automatically from the scan.

## 1. Quickest: install from a web link (no store, no fees)
1. Upload the contents of `www/` to any HTTPS host (GitHub Pages, Netlify, a church web server).
2. Open the link on a phone. iPhone: Safari > Share > Add to Home Screen. Android: Chrome > Install app.
3. It then opens like an app and works without data after the first visit.
Note: the offline install does not work from a claude.ai artifact link; it needs your own HTTPS host.

## 2. Store apps (Capacitor)
Requires Node.js. For iOS also a Mac with Xcode and an Apple Developer account (about USD 99/yr). Google Play needs a developer account (about USD 25 once). Check current fees.
```
npm install
npx cap add android
npx cap add ios
npx cap sync
npx cap open android   # build the AAB in Android Studio
npx cap open ios       # archive in Xcode, upload via App Store Connect
```
Change `appId` in `capacitor.config.json` to your own (e.g. org.elcb.kopelo).

## 3. Store checklist
- App icon 1024x1024 (replace `www/icons`, then use a tool like `@capacitor/assets`)
- Screenshots for phone sizes, short and long description (Setswana and English)
- Privacy policy URL (the app collects no data)
- Apple may question "website in a wrapper" apps; stress offline use, search, text size, hymn codes.

## 4. Updating text
Hymn, liturgy and reading text is in `www/index.html` (arrays `H`, `L`, `D`, `NEWH`; church details in `CFG`). After edits, increase the number in `sw.js` (`kopelo-elcb-v1` > `v2`) so phones pick up the update, then `npx cap sync` for store builds.

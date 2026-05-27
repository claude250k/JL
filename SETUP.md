# JL App – Setup Anleitung (30 Minuten)

## Was du bekommst
Eine vollständige Web App mit:
- E-Mail & Google Anmeldung
- Echtzeit-Feed mit Posts, Bilder-Upload
- Live-Krypto-Charts (CoinGecko API)
- Politik-Abstimmung (anonym)
- Profile, Follower, eigene Channels
- Profil-/Titelbild Upload

---

## SCHRITT 1 – Firebase einrichten (kostenlos)

1. Gehe zu https://console.firebase.google.com
2. Klicke "Neues Projekt erstellen"
3. Projektname: "jl-app" → Weiter → Fertig

### Authentication aktivieren:
1. Links → "Authentication" → "Jetzt loslegen"
2. "E-Mail/Passwort" → Aktivieren → Speichern
3. "Google" → Aktivieren → Speichern

### Firestore Datenbank:
1. Links → "Firestore Database" → "Datenbank erstellen"
2. "Im Testmodus starten" → Weiter → Fertig
3. Gehe zu "Regeln" → Kopiere den Inhalt aus `firestore.rules` → Veröffentlichen

### Storage (für Bilder):
1. Links → "Storage" → "Jetzt loslegen"
2. "Im Testmodus starten" → Weiter → Fertig
3. Gehe zu "Regeln" → Kopiere den Inhalt aus `storage.rules` → Veröffentlichen

### App-Konfiguration holen:
1. Zahnrad → "Projekteinstellungen"
2. Scrolle zu "Deine Apps" → Klicke </> (Web)
3. App-Nickname: "JL Web" → Registrieren
4. Kopiere die firebaseConfig (apiKey, authDomain usw.)

---

## SCHRITT 2 – Config in die App einfügen

Öffne `public/index.html` und suche nach:

```
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  ...
```

Ersetze alle YOUR_... Werte mit deinen echten Werten aus Firebase.

---

## SCHRITT 3 – App online stellen (Netlify – kostenlos)

### Option A: Netlify Drop (am einfachsten, 1 Minute):
1. Gehe zu https://app.netlify.com/drop
2. Ziehe den `public` Ordner auf die Seite
3. Fertig! Du bekommst sofort eine URL wie: `https://zufalls-name.netlify.app`

### Option B: Netlify mit eigenem Domain-Namen:
1. Konto erstellen auf https://netlify.com
2. "Add new site" → "Deploy manually"
3. Ordner `public` hochladen
4. Unter "Domain settings" kannst du eine eigene Domain einstellen

### Option C: Vercel (alternativ):
1. https://vercel.com → Account erstellen
2. "Add New Project" → "Browse" → `public` Ordner hochladen
3. Deploy → fertig

---

## SCHRITT 4 – Google Auth Domain freischalten

Wenn du Google-Login nutzt:
1. Firebase Console → Authentication → Settings → Autorisierte Domains
2. Deine Netlify-URL hinzufügen (z.B. `zufalls-name.netlify.app`)

---

## Live-Krypto-Kurse
Die App nutzt die CoinGecko API (kostenlos, kein API-Key nötig).
- BTC, ETH, SOL, BNB werden automatisch mit echten Preisen geladen
- Aktualisierung alle 60 Sekunden
- Bei Rate-Limiting werden Demo-Daten gezeigt

## Aktien-Charts
Für echte Aktienkurse empfehlen wir:
- Alpha Vantage: https://www.alphavantage.co (kostenloser Plan: 25 Requests/Tag)
- Diese können später in die Chart-Karten integriert werden

---

## Fertig!
Deine JL Web App ist jetzt live und nutzbar:
✅ Anmeldung mit E-Mail oder Google
✅ Posts erstellen mit Bild-Upload
✅ Feed nach Channels filtern
✅ Live-Krypto-Charts
✅ Profil mit Foto und Cover
✅ Eigene Channels erstellen
✅ Andere Nutzer folgen
✅ Politk-Abstimmung (anonym)
✅ Politiker-Info Download

# Politika privatnosti — Nekretnine Tracker

**Poslednje ažuriranje:** 1. jul 2026.

---

## Srpski

### Uvod

Nekretnine Tracker („ekstenzija“) je Chrome ekstenzija za lično praćenje oglasa za nekretnine. **Ne postoji naš server** — ekstenzija ne šalje tvoje podatke na našu infrastrukturu.

### Ko obrađuje podatke

Podatke čuva **Google Chrome** na tvom uređaju, preko API-ja `chrome.storage.sync`, u okviru **Chrome sinhronizacije** tvog Google naloga (ako je sync uključen u Chrome-u).

To znači da se lista oglasa može pojaviti i na drugim računarima gde si prijavljen istim Google nalogom i gde je ista ekstenzija instalirana. Google upravlja tim podacima prema svojoj [politici privatnosti](https://policies.google.com/privacy).

### Koje podatke ekstenzija čuva

Ekstenzija čuva samo ono što ti eksplicitno sačuvaš ili uneseš:

- URL i naslov oglasa
- sajt (domen)
- izvučene podatke sa stranice (cena, kvadratura, sobe, slika, itd.)
- tvoje beleške, ocenu, prioritet, status
- ručno unete cene i kvadrature
- datume dodavanja i izmene

Ekstenzija **ne prikuplja** ime, email, lokaciju, kontakte niti podatke za reklamiranje.

### Šta ekstenzija radi na stranicama

Da bi izvukla podatke o oglasu, ekstenzija na stranici koju otvoriš **čita HTML stranice** lokalno u browseru. Sadržaj stranica **ne šaljemo** na spoljni server.

Dozvola za pristup svim URL-ovima (`<all_urls>`) služi isključivo da možeš sačuvati oglas sa bilo kog sajta oglasa — ne za praćenje tvog surfovanja.

### Deljenje sa trećim stranama

**Ne prodajemo, ne iznajmljujemo i ne delimo** tvoje podatke sa trećim stranama u marketinške svrhe.

Jedino „deljenje“ je sinhronizacija preko Google Chrome sync infrastrukture, ako je uključena na tvom nalogu.

### Analitika i praćenje

Ekstenzija **nema** ugrađenu analitiku, telemetriju, crash reporting servise niti spoljne API pozive za podatke korisnika.

### Izvoz, uvoz i brisanje

- **Izvoz** — JSON backup cele liste (dugme u ekstenziji)
- **Uvoz** — spajanje backup-a sa postojećom listom
- **Brisanje** — pojedinačni oglasi u listi, ili deinstalacija ekstenzije (Chrome briše podatke ekstenzije prema pravilima browsera)

Za prelazak na drugi nalog ili backup van Chrome-a: koristi Izvoz pre deinstalacije.

### Deca

Ekstenzija nije namenjena deci mladjoj od 13 godina i ne prikuplja podatke o deci namerno.

### Bezbednost

Podaci su ograničeni na Chrome storage; pristup imaju samo ova ekstenzija i Chrome na tvom nalogu. Preporučujemo da ne deliš Google nalog i da koristiš Izvoz za sopstveni backup.

### Izmene politike

Ažuriranja objavljujemo na istom URL-u sa novim datumom. Nastavak korišćenja posle izmene znači prihvatanje ažurirane politike.

### Kontakt

Pitanja i prijave: [GitHub Issues](https://github.com/marko1943/nekretnine-tracker/issues)

---

## English

### Introduction

Nekretnine Tracker (the “extension”) is a Chrome extension for personal tracking of real-estate listings. **We do not operate a server** — the extension does not send your data to our infrastructure.

### Who processes your data

Data is stored by **Google Chrome** on your device, via the `chrome.storage.sync` API, as part of **Chrome sync** for your Google account (when sync is enabled in Chrome).

Your saved listings may appear on other computers where you are signed in with the same Google account and have the same extension installed. Google handles that data under its [Privacy Policy](https://policies.google.com/privacy).

### What data the extension stores

The extension stores only what you explicitly save or enter:

- listing URL and title
- website (domain)
- data extracted from the page (price, area, rooms, image, etc.)
- your notes, rating, priority, and status
- manually entered prices and areas
- dates added and updated

The extension does **not** collect your name, email, location, contacts, or advertising data.

### What the extension does on web pages

To extract listing data, the extension **reads the HTML** of pages you open, locally in the browser. We do **not** send page content to an external server.

The all-URLs host permission (`<all_urls>`) exists solely so you can save listings from any real-estate site — not to track your browsing.

### Sharing with third parties

We **do not sell, rent, or share** your data with third parties for marketing.

The only “sharing” is synchronization through Google’s Chrome sync infrastructure when enabled on your account.

### Analytics and tracking

The extension has **no** built-in analytics, telemetry, crash reporting, or external API calls for user data.

### Export, import, and deletion

- **Export** — JSON backup of the full list (button in the extension)
- **Import** — merge a backup with your existing list
- **Delete** — remove individual listings in the app, or uninstall the extension (Chrome removes extension data per its rules)

To move to another account or keep a backup outside Chrome: use Export before uninstalling.

### Children

The extension is not directed at children under 13 and does not knowingly collect children’s data.

### Security

Data is limited to Chrome storage; only this extension and Chrome on your account can access it. Do not share your Google account; use Export for your own backups.

### Changes to this policy

Updates are posted at this URL with a new date. Continued use after changes means you accept the updated policy.

### Contact

Questions and reports: [GitHub Issues](https://github.com/marko1943/nekretnine-tracker/issues)

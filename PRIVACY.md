# Politika privatnosti — Nekretnine Tracker

**Poslednje ažuriranje:** 16. jul 2026.

---

## Srpski

### Uvod

Nekretnine Tracker („ekstenzija“) je Chrome ekstenzija za lično praćenje oglasa za nekretnine. Autori ne vode zajednički multi-tenant server za sve korisnike.

### Ko obrađuje podatke

**Podrazumevano:** podaci ostaju na tvom uređaju u `chrome.storage.local`.

**Opciono (Cloud sync):** ako se registruješ / uloguješ, oglasi idu preko **API-ja ekstenzije** (Cloudflare Worker) u Supabase projekat autora (Postgres + Auth, RLS po nalogu). Worker drži Supabase ključeve; ekstenzija šalje samo auth tokene i podatke oglasa. Supabase: [privacy](https://supabase.com/privacy). Cloudflare: [privacy](https://www.cloudflare.com/privacypolicy/).

### Koje podatke ekstenzija čuva

Ekstenzija čuva samo ono što ti eksplicitno sačuvaš ili uneseš:

- URL i naslov oglasa
- sajt (domen)
- izvučene podatke sa stranice (cena, kvadratura, sobe, slika, itd.)
- tvoje beleške, ocenu, prioritet, status
- ručno unete cene i kvadrature
- datume dodavanja i izmene

Za Cloud sync čuva se sesija (access/refresh token) lokalno i username naloga.

Ekstenzija **ne prikuplja** lokaciju uređaja, kontakte niti podatke za reklamiranje.

### Šta ekstenzija radi na stranicama

Da bi izvukla podatke o oglasu, ekstenzija na stranici koju otvoriš **čita HTML stranice** lokalno u browseru. Sadržaj stranica **ne šaljemo** na server autora ekstenzije.

Dozvola `<all_urls>` služi za čuvanje oglasa sa bilo kog sajta i pozive ka API-ju — ne za praćenje surfovanja.

### Deljenje sa trećim stranama

**Ne prodajemo, ne iznajmljujemo i ne delimo** tvoje podatke sa trećim stranama u marketinške svrhe.

Opciono: API Worker → Supabase kada koristiš Cloud sync.

### Analitika i praćenje

Ekstenzija **nema** ugrađenu analitiku, telemetriju niti crash reporting.

### Izvoz, uvoz i brisanje

- **Izvoz** — JSON backup cele liste
- **Uvoz** — spajanje backup-a sa postojećom listom
- **Brisanje** — u listi; na cloudu soft-delete; deinstalacija briše lokalni storage

### Deca

Ekstenzija nije namenjena deci mlađoj od 13 godina.

### Bezbednost

Koristi jaku lozinku. Supabase ključevi su samo na Workeru; **service_role** se ne koristi u ovom setup-u.

### Izmene politike

Ažuriranja na istom URL-u sa novim datumom.

### Kontakt

[GitHub Issues](https://github.com/marko1943/nekretnine-tracker/issues)

---

## English

### Introduction

Nekretnine Tracker is a Chrome extension for personal real-estate listing tracking. The authors do not run a shared multi-tenant backend for all users.

### Who processes your data

**Default:** data stays on your device in `chrome.storage.local`.

**Optional (Cloud sync):** if you register/sign in, listings go through the extension’s API (Cloudflare Worker) to the author’s Supabase project (RLS per user). The Worker holds Supabase keys. See [Supabase](https://supabase.com/privacy) and [Cloudflare](https://www.cloudflare.com/privacypolicy/) privacy policies.

### What data the extension stores

Only what you save or enter: listing fields, notes, rating, priority, status, timestamps. For Cloud sync: auth session tokens and username locally.

No device location, contacts, or advertising profiles.

### What the extension does on web pages

It reads page HTML locally to extract listing fields. Page HTML is not sent to the extension authors’ servers.

### Sharing with third parties

No marketing sale/rent/share. Optional sync via the API Worker to Supabase.

### Analytics and tracking

None built in.

### Export, import, and deletion

Export/import JSON; delete in UI (cloud soft-delete); uninstall clears local extension storage.

### Children

Not directed at children under 13.

### Security

Use a strong password. Supabase keys stay on the Worker only.

### Contact

[GitHub Issues](https://github.com/marko1943/nekretnine-tracker/issues)

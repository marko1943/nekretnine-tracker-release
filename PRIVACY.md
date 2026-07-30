# Politika privatnosti — Nekretnine Tracker

**Poslednje ažuriranje:** 30. jul 2026.

---

## Srpski

### Uvod

Nekretnine Tracker („ekstenzija“) je Chrome ekstenzija za lično praćenje oglasa za nekretnine. Autori ne vode zajednički multi-tenant server za sve korisnike.

### Ko obrađuje podatke

**Podrazumevano:** podaci ostaju na tvom uređaju u `chrome.storage.local`.

**Opciono (Cloud sync):** ako se registruješ / uloguješ, ekstenzija se **direktno** povezuje na Supabase (Auth + REST API) — bez posrednog servera autora. Ekstenzija sadrži samo javni Supabase URL i tzv. **publishable (anon) ključ**, koji je namenjen da bude javan i korišćen iz klijentskog koda; sam po sebi ne otkriva tuđe podatke. Pristup podacima je ograničen **Row Level Security (RLS)** pravilima — svaki nalog vidi samo svoje oglase. Supabase: [privacy](https://supabase.com/privacy).

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

Dozvola `<all_urls>` (`host_permissions`) služi za dve stvari: čuvanje oglasa sa bilo kog sajta koji otvoriš, i (kada koristiš Cloud sync) mrežne pozive direktno ka `*.supabase.co` radi prijave i čuvanja/preuzimanja tvoje liste. Ne koristi se za praćenje surfovanja.

### Deljenje sa trećim stranama

**Ne prodajemo, ne iznajmljujemo i ne delimo** tvoje podatke sa trećim stranama u marketinške svrhe.

Opciono: ekstenzija → Supabase (direktno) kada koristiš Cloud sync. Nema posrednog servera koji vidi tvoje podatke.

### Analitika i praćenje

Ekstenzija **nema** ugrađenu analitiku, telemetriju niti crash reporting.

### Izvoz, uvoz i brisanje

- **Izvoz** — JSON backup cele liste
- **Uvoz** — spajanje backup-a sa postojećom listom
- **Brisanje** — u listi; na cloudu soft-delete; deinstalacija briše lokalni storage

### Deca

Ekstenzija nije namenjena deci mlađoj od 13 godina.

### Bezbednost

Koristi jaku lozinku. Ekstenzija sadrži samo javni **publishable (anon)** Supabase ključ; **service_role** ključ se nikad ne koristi niti čuva u ekstenziji. Pristup podacima štiti Supabase Auth + RLS po nalogu.

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

**Optional (Cloud sync):** if you register/sign in, the extension connects **directly** to Supabase (Auth + REST API) — there is no middle server operated by the authors. The extension ships only a public Supabase URL and a **publishable (anon) key**, which is designed to be public and used from client-side code; on its own it does not expose anyone's data. Access is restricted by **Row Level Security (RLS)** — each account can only see its own listings. See [Supabase privacy policy](https://supabase.com/privacy).

### What data the extension stores

Only what you save or enter: listing fields, notes, rating, priority, status, timestamps. For Cloud sync: auth session tokens and username locally.

No device location, contacts, or advertising profiles.

### What the extension does on web pages

It reads page HTML locally to extract listing fields. Page HTML is not sent to the extension authors' servers.

The `<all_urls>` `host_permissions` permission is used for two things: saving listings from any site you open, and (when you use Cloud sync) making network requests directly to `*.supabase.co` to sign in and to store/retrieve your list. It is not used to track your browsing.

### Sharing with third parties

No marketing sale/rent/share. Optional sync goes directly from the extension to Supabase — there is no intermediary server that sees your data.

### Analytics and tracking

None built in.

### Export, import, and deletion

Export/import JSON; delete in UI (cloud soft-delete); uninstall clears local extension storage.

### Children

Not directed at children under 13.

### Security

Use a strong password. The extension only ships the public **publishable (anon)** Supabase key; the **service_role** key is never used or stored in the extension. Data access is protected by Supabase Auth and per-account RLS.

### Contact

[GitHub Issues](https://github.com/marko1943/nekretnine-tracker/issues)

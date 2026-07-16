# Changelog

## 1.2.0 — 2026-07-16

### Storage / cloud
- Podaci u **`chrome.storage.local`** (bez Chrome Google sync)
- **Mali API** (Cloudflare Worker) ispred Supabase-a — secreti nisu u ZIP/gitu
- Login/registracija: **username + lozinka** preko API-ja
- U ekstenziji samo javni `apiUrl` (`src/api-config.js`)
- Lista: Cloud status + Sync
- Migracija sa starog `chrome.storage.sync` → local
- Merge po `dateUpdated`; soft-delete

### Docs
- [SERVER.md](SERVER.md), [supabase.sql](supabase.sql), [`server/`](../server/)

### Testovi
- `tests/sync-merge.test.js` — merge / delete / push pravila

## 1.1.1 — 2026-07-02

### Parser (`scrape.js`)
- **novogradnjanis.rs** i slični: cena se sada čita i kad je vrednost u zasebnoj koloni tabele, daleko od oznake „Cena“ (rezervni `parsePrice` nad telom stranice)
- **schema.org microdata** (`itemprop="numberOfRooms"`, `numberOfBedrooms`, `floorSize`) — broj soba i kvadratura i kad sajt nema JSON-LD
- Meta oznake (`og:title`, `og:image`) se čitaju i sa **jednostrukim navodnicima** — slika se više ne gubi
- **Broj spavaćih soba**: kod „X i po“ stanova pola sobe je dnevna, pa je broj spavaćih ceo deo (troiposoban → **3**, dvoiposoban → **2**); cele strukture i dalje minus dnevna (trosoban → 2, dvosoban → 1). Nema više prikaza „2.5 spavaće“.

### Testovi
- Fixture `novogradnjanis-troiposoban` + unit testovi za microdata i cenu iz tabele
- Ažurirana očekivanja za broj spavaćih soba (troiposoban/dvoiposoban) u contract testovima

## 1.1.0 — 2026-07-01

Javna distribucija: [nekretnine-tracker-release](https://github.com/marko1943/nekretnine-tracker-release)

### Lista
- **Grupisanje po ključnim rečima** — polje „Grupiši po: niš, palilula…“; oglasi u više grupa ako odgovaraju više reči
- **Spavaće sobe** na kartici — prikaz u novom redu (`3 spavaće`), ne ukupni broj soba uključujući dnevnu

### Popup
- Posle čuvanja: **Dodaj detalje** — prioritet, status, beleška (ocena ostaje u listi)
- Pouzdaniji re-save i ažuriranje badge brojača

### Parser (`scrape.js`)
- Izvlačenje **spavaćih** iz opisa i JSON-LD (`numberOfBedrooms`)
- Kada postoji samo ukupan broj soba — heuristika **minus dnevna**
- Slične kvadrature više ne tretiraju pogrešno pojedinačan oglas kao projekat (terasa/ostava ispod 12 m²)
- **Povraćaj PDV-a** i **„cena sa PDV-om“** imaju prednost nad `+ PDV` uz cenu; naslov, JSON-LD i opis iz `<script>` JSON-a ulaze u proveru
- Polje **„Spavaća soba N“** u specifikaciji pobeđuje zastareli marketing tekst (npr. „dve spavaće“ uz „Spavaća soba 3“)

### Storage / re-save
- Ponovno čuvanje oglasa **osvežava PDV**, `areaMin`/`areaMax` i `kind` — ne zadržava pogrešne stare vrednosti

### UI
- PDV oznaka (**sa/bez PDV**) odmah pored cene na kartici

### Testovi
- Fixture `nekretnine-kolubarska-trospavace`, `nekretnine-rs-roda-povracaj`, `nekretnine-rs-tolstojeva-sa-pdv` + unit testovi za PDV i spavaće sobe

---

## 1.0.0 — 2026-07-01

Prva javna distribucija (ZIP + privacy policy u [release repo](https://github.com/marko1943/nekretnine-tracker-release)).

### Ekstenzija
- Chrome MV3: čuvanje oglasa, lista, filteri, ocena, prioritet, status, beleške
- Kontekstni meni, popup, badge brojača
- Univerzalno izvlačenje (JSON-LD, OG, heuristike)
- Pametna cena, opseg m² za projekte, PDV, ručni unos cene/kvadrature
- JSON izvoz/uvoz
- **`chrome.storage.sync`** — lista između računara istog Google naloga (`src/storage.js`, migracija sa `storage.local`)
- Chip **Stan** / **Projekat**, UI **Po kvadraturi** za novogradnju

### Testirani sajtovi
- 4zida.rs, nekretnine.rs, cityexpert.rs, stan2.rs, distriktnekretnine.rs, halooglasi.com

### Distribucija i docs
- `docs/PRIVACY.md`, `docs/STORE_LISTING.md`
- GitHub Action → automatski build u javni repo

### Razvoj (nije u ZIP-u)
- CI, coverage badge, pre-commit hook, `npm test` contract nad fixture-ima

---

## Ranije (pre 1.0.0 manifesta)

Razvoj jun 2026 — parser za projekte (`kind`), halooglasi/CityExpert/4zida novogradnja testovi, HANDOFF/BACKLOG. Uključeno u 1.0.0 build.

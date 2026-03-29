# gruengebaut | new.energy.consulting
**Bodo Becker – Interim Manager & Transformation Consultant**

---

## Dateien im Repository

| Datei            | Funktion                                    |
|------------------|---------------------------------------------|
| `index.html`     | Deutsche Landing Page (Hauptseite)          |
| `en.html`        | Englische Coming-Soon-Seite                 |
| `CNAME`          | Custom Domain für GitHub Pages              |
| `sitemap.xml`    | Sitemap für Suchmaschinen                   |
| `robots.txt`     | Crawler-Anweisungen                         |
| `impressum.html` | Pflicht! Selbst anlegen (e-recht24.de)      |
| `datenschutz.html` | Pflicht! Selbst anlegen (e-recht24.de)    |

---

## Schritt 1 – GitHub Repository anlegen

1. GitHub.com → **New repository**
2. Name: `gruengebaut` (oder `bodo-becker.github.io`)
3. Sichtbarkeit: **Public** (Pflicht für kostenlose GitHub Pages)
4. Ohne README initialisieren (wir pushen selbst)
5. **Create repository**

---

## Schritt 2 – Dateien per Git hochladen (Terminal / Git Bash)

```bash
# Einmalig: Git konfigurieren (falls noch nicht geschehen)
git config --global user.name "Bodo Becker"
git config --global user.email "deine@email.de"

# Repository initialisieren
cd /pfad/zum/ordner/mit/den/dateien
git init
git add .
git commit -m "Initial commit: gruengebaut landing page"

# Remote verknüpfen (ersetze DEIN-USERNAME)
git remote add origin https://github.com/DEIN-USERNAME/gruengebaut.git

# Push
git branch -M main
git push -u origin main
```

**Alternativ ohne Terminal:** Auf GitHub.com → Repository → „Add file" → „Upload files" → alle Dateien reinziehen → Commit.

---

## Schritt 3 – GitHub Pages aktivieren

1. Repository → **Settings** (oben rechts)
2. Links im Menü: **Pages**
3. Source: **Deploy from a branch**
4. Branch: `main` | Folder: `/ (root)`
5. **Save**
6. Nach 1–2 Minuten erscheint: `https://DEIN-USERNAME.github.io/gruengebaut`

---

## Schritt 4 – Custom Domain (gruengebaut.de via IONOS)

### In GitHub Pages Settings:
- Field „Custom domain": `gruengebaut.de` eintragen → Save
- Warten bis DNS-Check grün → „Enforce HTTPS" aktivieren

### In IONOS DNS-Einstellungen:
Gehe zu: Mein IONOS → Domains → gruengebaut.de → DNS → DNS-Einträge bearbeiten

| Typ   | Hostname | Wert                              | TTL  |
|-------|----------|-----------------------------------|------|
| A     | @        | 185.199.108.153                   | 3600 |
| A     | @        | 185.199.109.153                   | 3600 |
| A     | @        | 185.199.110.153                   | 3600 |
| A     | @        | 185.199.111.153                   | 3600 |
| CNAME | www      | DEIN-USERNAME.github.io           | 3600 |

> ⏳ DNS-Propagation: 15–60 Minuten, manchmal bis zu 24h

### CNAME-Datei:
Die `CNAME`-Datei **muss** im Repository-Root liegen (ist bereits enthalten).
Inhalt: `gruengebaut.de` – nicht `www.gruengebaut.de`

---

## Schritt 5 – Personalisierung (vor Go-Live)

Folgende Platzhalter in `index.html` und `en.html` anpassen:

- **E-Mail** → `kontakt@gruengebaut.de` durch deine echte Adresse ersetzen (IONOS E-Mail)
- **Telefon** → optional im Kontaktbereich ergänzen
- **Sitemap-Datum** → in `sitemap.xml` das `<lastmod>`-Datum aktualisieren

---

## Schritt 6 – Impressum & Datenschutz (PFLICHT für .de-Domain!)

Als Einzelunternehmer mit gewerblicher Website:

1. Auf **e-recht24.de** → Generatoren → Impressum + Datenschutz erstellen
2. Als `impressum.html` und `datenschutz.html` speichern
3. In den Repository-Root legen und pushen

**Impressum muss enthalten:**
- Vollständiger Name: Bodo Becker
- Anschrift (Troisdorf)
- E-Mail-Adresse
- Ggf. Umsatzsteuer-ID (als Einzelunternehmer)

---

## Updates einspielen (nach erstem Deployment)

```bash
# Datei lokal bearbeiten, dann:
git add index.html
git commit -m "Update: Brand-Text angepasst"
git push

# GitHub Pages deployed automatisch innerhalb ~1 Minute
```

---

## SEO-Checkliste nach Go-Live

- [ ] **Google Search Console**: Property anlegen → gruengebaut.de verifizieren (HTML-Tag im `<head>` oder CNAME)
- [ ] **Sitemap einreichen**: Search Console → Sitemaps → `https://gruengebaut.de/sitemap.xml`
- [ ] **Google My Business**: Profil anlegen (Kategorie: Unternehmensberatung)
- [ ] **LinkedIn-Profil**: URL der Website in „Kontaktinfo" eintragen
- [ ] **IONOS SEO-Check**: IONOS bietet eigene SEO-Tools – nutzen für technische Basis-Checks
- [ ] **OG-Image**: Ein `og-image.jpg` (1200×630px) erstellen und in den Repo-Root legen, dann im `<head>` einbinden: `<meta property="og:image" content="https://gruengebaut.de/og-image.jpg">`
- [ ] **Favicon**: `favicon.ico` oder `favicon.svg` in Repo-Root + `<link rel="icon" href="/favicon.svg">` im `<head>`

---

*Technologie: Vanilla HTML/CSS/JS – kein Build-Tool, kein Node.js, kein Framework. Direkt deploybar.*

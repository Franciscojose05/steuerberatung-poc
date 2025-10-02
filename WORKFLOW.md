# Decap CMS Workflow Guide

## Setup (einmalig)

Starte **zwei Terminals**:

**Terminal 1 - Astro Dev Server:**
```bash
npm run dev
```

**Terminal 2 - CMS Proxy Server:**
```bash
npm run dev:proxy
```

## Editorial Workflow

### 1. Draft erstellen (Entwurf)

1. Gehe zu http://localhost:4321/admin/
2. Klicke auf "New Blog-Artikel"
3. Fülle die Felder aus
4. Klicke **"Save"** (NICHT Publish!)
   - Erstellt einen neuen Git-Branch: `cms/blog/YYYY-MM-DD-dein-titel`
   - Änderungen sind NICHT live auf der Website

### 2. Draft ansehen & testen

**Option A: Im CMS ansehen**
- Gehe zum **"Workflow"** Tab oben
- Dort siehst du alle Drafts
- Klicke auf den Draft zum Bearbeiten

**Option B: Lokal auf der Website ansehen**
```bash
# Zeige alle Branches
git branch -a

# Wechsel zum Draft-Branch
git checkout cms/blog/2025-10-03-mein-artikel

# Dev-Server neu starten
npm run dev

# Jetzt auf http://localhost:4321/blog ansehen
```

### 3. Draft bearbeiten

- Im **"Workflow"** Tab den Draft öffnen
- Änderungen machen
- **"Save"** → aktualisiert den Branch
- Beliebig oft wiederholen bis zufrieden

### 4. Veröffentlichen (Publish)

Im CMS:
1. **"Workflow"** Tab öffnen
2. Draft auswählen
3. **"Set status to ready"** (optional - für Review)
4. **"Publish"** klicken
   - Merged den Branch in `main`
   - Erstellt Git-Commit
   - Jetzt LIVE auf der Website!

Oder direkt beim Bearbeiten:
- **"Publish now"** Button → sofort live

## Änderungen rückgängig machen

### Letzten Commit rückgängig (sauber)
```bash
# Zeige letzte Commits
git log --oneline -5

# Erstellt einen "Rückgängig-Commit" (empfohlen)
git revert HEAD

# Oder einen spezifischen Commit
git revert <commit-hash>
```

### Komplett zurücksetzen (Vorsicht!)
```bash
# Zurück zum vorherigen Commit (löscht Änderungen!)
git reset --hard HEAD~1

# Zurück zu einem spezifischen Commit
git reset --hard <commit-hash>
```

### Einzelne Datei wiederherstellen
```bash
# Datei aus letztem Commit wiederherstellen
git checkout HEAD -- src/content/blog/artikel.md

# Aus spezifischem Commit
git checkout <commit-hash> -- src/content/blog/artikel.md
```

### Draft verwerfen (nicht publishen)
```bash
# Branch löschen
git branch -D cms/blog/2025-10-03-artikel-name
```

## Git-Historie ansehen

```bash
# Letzte 10 Commits
git log --oneline -10

# Mit Dateiänderungen
git log --stat

# Grafische Darstellung
git log --oneline --graph --all

# Was wurde geändert?
git show HEAD
git diff HEAD~1
```

## Nützliche Befehle

```bash
# Aktueller Status
git status

# Alle Branches anzeigen
git branch -a

# Zurück zu main
git checkout main

# Nicht gespeicherte Änderungen verwerfen
git restore .

# Bestimmte Datei wiederherstellen
git restore src/content/blog/artikel.md
```

## Workflow-Zusammenfassung

```
1. Save Draft    → Git-Branch erstellt (cms/blog/artikel)
2. Edit Draft    → Branch wird aktualisiert
3. Test Local    → git checkout cms/blog/artikel
4. Publish       → Branch merged in main → LIVE!
5. Revert (opt)  → git revert HEAD
```

## Troubleshooting

**CMS fragt nach Login?**
- Proxy-Server läuft nicht → `npm run dev:proxy`

**Änderungen nicht sichtbar?**
- Dev-Server neustarten: `npm run dev`
- Browser-Cache leeren

**Draft verschwindet?**
- Branch wurde gelöscht
- Check: `git branch -a`

# Steuerberatung Website mit Astro & Decap CMS

Eine Proof-of-Concept Website für eine Steuerberaterin, gebaut mit Astro und Decap CMS.

## 🚀 Projekt starten

1. **Abhängigkeiten installieren** (falls noch nicht geschehen):
   ```bash
   npm install
   ```

2. **Entwicklungsserver starten**:
   ```bash
   npm run dev
   ```

3. **Website öffnen**:
   - Website: http://localhost:4321
   - **CMS Admin Interface**: http://localhost:4321/admin

## ✨ Features

- ✅ **Astro** - Modernes Static Site Framework
- ✅ **Decap CMS** - Git-basiertes Headless CMS
- ✅ **Content Collections** - Typsichere Content-Verwaltung
- ✅ **Blog System** - Vollständiges Blog mit Übersichts- und Detailseiten
- ✅ **Responsive Design** - Mobile-freundliches Layout

## 📝 Decap CMS nutzen

1. Öffne http://localhost:4321/admin
2. Das CMS läuft im **Test-Modus** - keine Git-Integration erforderlich
3. Du kannst direkt loslegen:
   - **Blog-Artikel** erstellen und bearbeiten
   - **Seiteninhalte** (Startseite, Leistungen) anpassen
   - **Bilder hochladen**

## 📁 Projektstruktur

```
/
├── public/
│   └── admin/          # Decap CMS Admin Interface
│       ├── config.yml  # CMS-Konfiguration
│       └── index.html
├── src/
│   ├── content/
│   │   ├── blog/       # Blog-Artikel (Markdown)
│   │   ├── pages/      # Seiten-Inhalte (Markdown)
│   │   └── config.ts   # Content Collections Schema
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       ├── index.astro      # Startseite
│       ├── leistungen.astro # Leistungen
│       ├── kontakt.astro    # Kontakt
│       └── blog/
│           ├── index.astro      # Blog-Übersicht
│           └── [...slug].astro  # Blog-Detailseite
└── package.json
```

## 🎨 Anpassungen

### CMS-Konfiguration ändern
Die CMS-Konfiguration findest du in `public/admin/config.yml`. Hier kannst du:
- Neue Content-Typen hinzufügen
- Felder anpassen
- Backend-Einstellungen ändern (z.B. für Git Gateway in Produktion)

### Styling anpassen
Die Styles sind direkt in den `.astro` Komponenten definiert. Du kannst:
- Farben in den CSS-Custom-Properties ändern
- Layouts und Komponenten nach Bedarf anpassen

## 📦 Produktion

Für die Produktion solltest du:

1. In `public/admin/config.yml` das Backend auf Git Gateway umstellen
2. Website builden: `npm run build`
3. Build testen: `npm run preview`
4. Deploy auf einen Static Host (Netlify, Vercel, etc.)

## 🧞 Commands

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 🛠 Technologien

- [Astro](https://astro.build)
- [Decap CMS](https://decapcms.org)
- TypeScript
- Markdown

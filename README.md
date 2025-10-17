# Carsten Müller - Sprachkurse und mehr

Eine professionelle, selbst-hostbare Website für Sprachkurse (Spanisch, Englisch, Deutsch), Dolmetscher-Services und Tourguide-Dienste in Santa Cruz, Bolivien.

## 📋 Über diese Website

Diese Website ist eine statische HTML/CSS/JavaScript-Version der ursprünglichen Wix-Website von Carsten Müller. Sie wurde entwickelt, um vollständige Kontrolle über Hosting, Performance und Anpassungen zu ermöglichen.

### Features

- ✅ **Responsive Design** - Perfekt auf Desktop, Tablet und Mobile
- ✅ **Bunte Navigation** - Charakteristisches Farbschema mit verschiedenen Farben pro Link
- ✅ **9 Hauptsektionen** - Hero, Über mich, Rezensionen, Services, Angebot & Preise, Kontakt
- ✅ **9 Testimonials** - Kundenbewertungen mit Fotos
- ✅ **Kontaktformular** - Einfache Kursanmeldung
- ✅ **Smooth Scrolling** - Sanfte Navigation zwischen Sektionen
- ✅ **SEO-optimiert** - Meta-Tags und semantisches HTML
- ✅ **Schnelle Ladezeiten** - Keine externen Abhängigkeiten (außer Google Fonts)

## 🚀 Schnellstart

### Option 1: Lokal öffnen

1. Entpacken Sie die ZIP-Datei
2. Öffnen Sie `index.html` in Ihrem Browser
3. Fertig!

### Option 2: Mit lokalem Server (empfohlen für Entwicklung)

```bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (npx)
npx serve

# PHP
php -S localhost:8000
```

Dann öffnen Sie `http://localhost:8000` in Ihrem Browser.

## 📁 Dateistruktur

```
carsten-mueller-website/
├── index.html              # Haupt-HTML-Datei
├── styles.css              # Stylesheet
├── script.js               # JavaScript für Interaktivität
├── images/                 # Bilder und Assets
│   ├── hero-mountain.jpg   # Hero-Hintergrundbild
│   ├── carsten-portrait.jpg # Porträtfoto
│   ├── bas-klessens.jpg    # Testimonial-Foto
│   └── peter-buchholz.jpg  # Testimonial-Foto
├── README.md               # Diese Datei
└── DEPLOYMENT.md           # Deployment-Anleitungen
```

## 🎨 Anpassungen

### Farben ändern

Öffnen Sie `styles.css` und passen Sie die CSS-Variablen an:

```css
:root {
    --color-green: #7ed957;
    --color-yellow: #ffd966;
    --color-purple: #b4a7d6;
    --color-cyan: #67c7d3;
    --color-pink: #d696bb;
    --color-orange: #ff9966;
    /* ... */
}
```

### Texte ändern

Öffnen Sie `index.html` und bearbeiten Sie die Texte direkt im HTML.

### Bilder ersetzen

Ersetzen Sie die Bilder im `images/` Ordner. Achten Sie darauf, die gleichen Dateinamen zu verwenden, oder passen Sie die Referenzen in `index.html` an.

### Kontaktformular anpassen

Das Kontaktformular verwendet derzeit `mailto:`. Öffnen Sie `script.js` und ändern Sie die E-Mail-Adresse:

```javascript
window.location.href = `mailto:ihre-email@beispiel.com?subject=${subject}&body=${body}`;
```

Für ein echtes Backend-Formular können Sie Dienste wie:
- [Formspree](https://formspree.io/)
- [Netlify Forms](https://www.netlify.com/products/forms/)
- [EmailJS](https://www.emailjs.com/)

verwenden.

## 🌐 Deployment

Siehe [DEPLOYMENT.md](DEPLOYMENT.md) für detaillierte Anleitungen zu:

- GitHub Pages
- Netlify
- Vercel
- Firebase Hosting
- AWS S3
- Eigener Server

## 📧 Kontakt

Bei Fragen oder Problemen wenden Sie sich an:
- **E-Mail**: contact@carsten-mueller.net
- **Website**: https://www.carsten-mueller.net

## 📄 Lizenz

© 2025 Carsten Müller. Alle Rechte vorbehalten.

---

**Hinweis**: Diese Website wurde von der ursprünglichen Wix-Website konvertiert, um mehr Flexibilität und Kontrolle zu ermöglichen.


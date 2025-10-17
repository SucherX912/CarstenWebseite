# Deployment-Anleitung

Diese Anleitung zeigt Ihnen, wie Sie Ihre Website auf verschiedenen Plattformen hosten können.

## 🚀 Deployment-Optionen

### 1. GitHub Pages (Kostenlos & Empfohlen)

**Vorteile:**
- ✅ Kostenlos
- ✅ Einfach einzurichten
- ✅ Automatische HTTPS
- ✅ Eigene Domain möglich

**Schritte:**

1. **GitHub-Account erstellen** (falls noch nicht vorhanden)
   - Gehen Sie zu [github.com](https://github.com)
   - Registrieren Sie sich kostenlos

2. **Repository erstellen**
   - Klicken Sie auf "New Repository"
   - Name: `carsten-mueller-website` (oder ein anderer Name)
   - Wählen Sie "Public"
   - Klicken Sie auf "Create repository"

3. **Code hochladen**
   
   **Option A: Mit Git (empfohlen)**
   ```bash
   cd carsten-mueller-website
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/IHR-USERNAME/carsten-mueller-website.git
   git push -u origin main
   ```

   **Option B: Über die Weboberfläche**
   - Klicken Sie auf "uploading an existing file"
   - Ziehen Sie alle Dateien in das Fenster
   - Klicken Sie auf "Commit changes"

4. **GitHub Pages aktivieren**
   - Gehen Sie zu "Settings" → "Pages"
   - Source: "Deploy from a branch"
   - Branch: `main` → Ordner: `/ (root)`
   - Klicken Sie auf "Save"

5. **Fertig!**
   - Ihre Website ist nach 1-2 Minuten online unter:
   - `https://IHR-USERNAME.github.io/carsten-mueller-website/`

**Eigene Domain verbinden:**
- Gehen Sie zu "Settings" → "Pages" → "Custom domain"
- Geben Sie Ihre Domain ein (z.B. `www.carsten-mueller.net`)
- Folgen Sie den DNS-Anweisungen

---

### 2. Netlify (Sehr einfach, kostenlos)

**Vorteile:**
- ✅ Drag & Drop Deployment
- ✅ Automatische HTTPS
- ✅ Eigene Domain kostenlos
- ✅ Formulare funktionieren automatisch

**Schritte:**

1. Gehen Sie zu [netlify.com](https://www.netlify.com/)
2. Registrieren Sie sich (kostenlos)
3. Klicken Sie auf "Add new site" → "Deploy manually"
4. Ziehen Sie den gesamten Website-Ordner in das Fenster
5. Fertig! Ihre Website ist online

**Eigene Domain:**
- Klicken Sie auf "Domain settings"
- "Add custom domain"
- Folgen Sie den Anweisungen

---

### 3. Vercel (Modern, kostenlos)

**Vorteile:**
- ✅ Sehr schnell
- ✅ Automatische HTTPS
- ✅ Eigene Domain kostenlos
- ✅ Perfekt für statische Websites

**Schritte:**

1. Gehen Sie zu [vercel.com](https://vercel.com/)
2. Registrieren Sie sich mit GitHub
3. Klicken Sie auf "Add New..." → "Project"
4. Wählen Sie Ihr GitHub Repository
5. Klicken Sie auf "Deploy"
6. Fertig!

---

### 4. Firebase Hosting (Google)

**Vorteile:**
- ✅ Sehr schnell (Google CDN)
- ✅ Automatische HTTPS
- ✅ Eigene Domain möglich

**Schritte:**

1. **Firebase CLI installieren**
   ```bash
   npm install -g firebase-tools
   ```

2. **Firebase initialisieren**
   ```bash
   cd carsten-mueller-website
   firebase login
   firebase init hosting
   ```

3. **Konfiguration**
   - Public directory: `.` (aktueller Ordner)
   - Single-page app: `No`
   - Automatic builds: `No`

4. **Deployen**
   ```bash
   firebase deploy
   ```

5. Ihre Website ist online unter: `https://IHR-PROJEKT.web.app`

---

### 5. AWS S3 + CloudFront (Professionell)

**Vorteile:**
- ✅ Sehr skalierbar
- ✅ Professionell
- ✅ Volle Kontrolle

**Schritte:**

1. **S3 Bucket erstellen**
   - Gehen Sie zur [AWS Console](https://aws.amazon.com/)
   - S3 → "Create bucket"
   - Name: `carsten-mueller-website`
   - Region: Wählen Sie eine nahe Region

2. **Static Website Hosting aktivieren**
   - Bucket → "Properties" → "Static website hosting"
   - Enable
   - Index document: `index.html`

3. **Dateien hochladen**
   - Laden Sie alle Dateien in den Bucket hoch
   - Setzen Sie Permissions auf "Public read"

4. **CloudFront Distribution erstellen** (optional, für HTTPS)
   - CloudFront → "Create Distribution"
   - Origin: Ihr S3 Bucket
   - SSL Certificate: Verwenden Sie AWS Certificate Manager

---

### 6. Eigener Server (VPS/Shared Hosting)

**Vorteile:**
- ✅ Volle Kontrolle
- ✅ Kann mit bestehenden Websites kombiniert werden

**Schritte:**

1. **Per FTP/SFTP hochladen**
   - Verwenden Sie FileZilla oder einen anderen FTP-Client
   - Verbinden Sie sich mit Ihrem Server
   - Laden Sie alle Dateien in das `public_html/` oder `www/` Verzeichnis hoch

2. **Per SSH (für VPS)**
   ```bash
   # Auf dem Server
   cd /var/www/html
   
   # Von Ihrem Computer
   scp -r carsten-mueller-website/* user@server:/var/www/html/
   ```

3. **Nginx-Konfiguration** (falls benötigt)
   ```nginx
   server {
       listen 80;
       server_name carsten-mueller.net www.carsten-mueller.net;
       root /var/www/html/carsten-mueller-website;
       index index.html;
       
       location / {
           try_files $uri $uri/ =404;
       }
   }
   ```

4. **Apache .htaccess** (falls benötigt)
   ```apache
   RewriteEngine On
   RewriteCond %{REQUEST_FILENAME} !-f
   RewriteCond %{REQUEST_FILENAME} !-d
   RewriteRule ^(.*)$ index.html [L]
   ```

---

## 🔒 HTTPS einrichten

### Let's Encrypt (Kostenlos)

Für eigene Server:

```bash
# Certbot installieren
sudo apt-get install certbot python3-certbot-nginx

# Zertifikat erstellen
sudo certbot --nginx -d carsten-mueller.net -d www.carsten-mueller.net
```

Für GitHub Pages, Netlify, Vercel: HTTPS ist automatisch aktiviert!

---

## 🌐 Domain verbinden

### DNS-Einstellungen

Fügen Sie bei Ihrem Domain-Anbieter folgende DNS-Records hinzu:

**Für GitHub Pages:**
```
A     @       185.199.108.153
A     @       185.199.109.153
A     @       185.199.110.153
A     @       185.199.111.153
CNAME www     IHR-USERNAME.github.io
```

**Für Netlify:**
```
CNAME www     IHR-SITE.netlify.app
```

**Für Vercel:**
```
CNAME www     cname.vercel-dns.com
```

---

## 📊 Performance-Optimierung

### Bilder komprimieren

Verwenden Sie Tools wie:
- [TinyPNG](https://tinypng.com/)
- [Squoosh](https://squoosh.app/)
- [ImageOptim](https://imageoptim.com/)

### CDN verwenden

Für statische Assets können Sie ein CDN verwenden:
- Cloudflare (kostenlos)
- AWS CloudFront
- Fastly

---

## 🔍 SEO-Optimierung

### Google Search Console

1. Gehen Sie zu [search.google.com/search-console](https://search.google.com/search-console)
2. Fügen Sie Ihre Website hinzu
3. Verifizieren Sie die Eigentümerschaft
4. Reichen Sie Ihre Sitemap ein

### Sitemap erstellen

Erstellen Sie eine `sitemap.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.carsten-mueller.net/</loc>
    <lastmod>2025-01-01</lastmod>
    <priority>1.0</priority>
  </url>
</urlset>
```

---

## 🆘 Troubleshooting

### Website lädt nicht

- Überprüfen Sie, ob alle Dateien hochgeladen wurden
- Überprüfen Sie die Dateiberechtigungen (755 für Ordner, 644 für Dateien)
- Überprüfen Sie die Browser-Konsole auf Fehler (F12)

### Bilder werden nicht angezeigt

- Überprüfen Sie die Dateipfade in `index.html`
- Stellen Sie sicher, dass Bilder im `images/` Ordner sind
- Überprüfen Sie die Groß-/Kleinschreibung der Dateinamen

### Kontaktformular funktioniert nicht

- Das Formular verwendet `mailto:`, das vom E-Mail-Client abhängt
- Für ein echtes Backend verwenden Sie Formspree oder Netlify Forms

---

## 📞 Support

Bei Fragen oder Problemen:
- GitHub Issues: [github.com/IHR-USERNAME/carsten-mueller-website/issues](https://github.com)
- E-Mail: contact@carsten-mueller.net

---

**Viel Erfolg mit Ihrer Website!** 🚀


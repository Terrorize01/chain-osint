# Chain OSINT 🔗

Ein modernes OSINT (Open Source Intelligence) Aggregations-Tool zur Verwaltung und Nutzung von Security & Research Tools - wie OSINT CAT aber besser! 🚀

## Features 🎯

- 🔍 **Tool Aggregation** - 25+ vorinstallierte OSINT Tools
- 🏷️ **Kategorien & Tags** - Intelligent organisiert
- 🔎 **Erweiterte Suche** - Schnelle Filterung nach Keywords, Kategorie, Rating
- ⭐ **Favoriten** - Speichere deine Lieblings-Tools
- 🗳️ **Community Voting** - Bewerte Tools mit Upvotes
- 📱 **Responsive Design** - Funktioniert auf Desktop & Mobil
- 🌙 **Dark Mode UI** - Modernes, angenehmes Design
- 🐳 **Docker Ready** - One-Click Setup

## 🚀 Schnellstart (Docker - EMPFOHLEN)

```bash
# 1. Repository klonen
git clone https://github.com/Terrorize01/chain-osint.git
cd chain-osint

# 2. Docker starten (alles automatisch!)
docker-compose up

# 3. Im Browser öffnen
# Frontend: http://localhost:3000
# Backend API: http://localhost:5000/api

# Die Datenbank wird automatisch mit 25+ Tools gefüllt! ✅
```

**Das wars!** 🎉 Keine zusätzliche Konfiguration nötig!

## 🛠️ Installation ohne Docker

### Voraussetzungen
- Node.js 16+
- MongoDB lokal installiert
- Git

### Setup

```bash
# 1. Repository klonen
git clone https://github.com/Terrorize01/chain-osint.git
cd chain-osint

# 2. Alle Dependencies installieren
npm run install-all

# 3. MongoDB starten (in separatem Terminal)
mongod

# Terminal 1: Backend starten
cd backend
npm run seed    # Datenbank mit Tools füllen
npm run dev     # Server läuft auf http://localhost:5000

# Terminal 2: Frontend starten (neues Terminal)
cd frontend
npm run dev     # App läuft auf http://localhost:3000
```

## 📊 Eingebaute OSINT Tools (25+)

### Domain & IP Lookup
- **Shodan** - Internet Device Search Engine
- **VirusTotal** - Malware & URL Scanner
- **Censys** - Internet Asset Search
- **WHOIS Lookup** - Domain Registration Info
- **Spyse** - IP & SSL Intelligence

### Email Finder
- **TheHarvester** - Email & Subdomain Enumerator
- **Hunter.io** - Company Email Finder
- **EmailRep.io** - Email Reputation Checker

### People Search
- **Maltego** - Link Analysis & Forensics
- **Pipl** - People Search Engine

### Datenbanken & Breaches
- **Have I Been Pwned** - Breach Database
- Weitere...

### Geolocation & Mapping
- **Shodan Maps** - Device Location Mapping
- **Google Maps Timeline** - Location History

### Code & Secrets
- **GitHub Search** - Code Repository Search
- **Google Dorks** - Advanced Google Search

### Metadata & Image Search
- **TinEye** - Reverse Image Search
- **ExifTool** - Metadata Extraction

### DNS & Zertifikate
- **SSL Certificate Search (crt.sh)** - Subdomain Discovery
- **nslookup/dig** - DNS Record Lookup

### Dark Web
- **DarkSearch** - .onion Site Search

### Social Media
- **Twitter Advanced Search** - Tweet & User Search
- **Telegram Search** - Channel & Group Search
- **Truecaller** - Phone Number Lookup
- **Namechk** - Username Search

## 📡 API Dokumentation

### Tools Endpoints

```
GET  /api/tools                          Alle Tools abrufen
GET  /api/tools?search=keyword           Nach Tool suchen
GET  /api/tools?category=Domain/IP Lookup  Nach Kategorie filtern
GET  /api/tools?sort=rating              Nach Rating sortieren (votes, rating, newest)
GET  /api/tools/:id                      Einzelnes Tool abrufen
POST /api/tools/:id/vote                 Tool upvoten
POST /api/tools                          Neues Tool erstellen (Admin)
PUT  /api/tools/:id                      Tool aktualisieren (Admin)
DELETE /api/tools/:id                    Tool löschen (Admin)
```

### Kategorien Endpoints

```
GET  /api/categories              Alle Kategorien mit Tool-Count
GET  /api/categories/:category    Tools einer Kategorie
```

### User Endpoints

```
POST /api/users/register                          Registrieren
POST /api/users/login                            Login
GET  /api/users/:id                              User-Profil mit Favoriten
POST /api/users/:userId/favorites/:toolId        Favorit hinzufügen
DELETE /api/users/:userId/favorites/:toolId      Favorit entfernen
```

## 🏗️ Projektstruktur

```
chain-osint/
├── backend/
│   ├── models/
│   │   ├── Tool.js              MongoDB Tool Schema
│   │   └── User.js              MongoDB User Schema
│   ├── routes/
│   │   ├── tools.js             Tool CRUD & Voting
│   │   ├── users.js             User & Favoriten
│   │   └── categories.js        Kategorie Routes
│   ├── server.js                Express Server
│   ├── seed.js                  Datenbank Seeding (25+ Tools)
│   ├── package.json
│   ├── Dockerfile
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── App.jsx              Hauptkomponente (React)
│   │   ├── App.css              Component Styles
│   │   ├── index.css            Global Styles (Tailwind)
│   │   └── main.jsx             Entry Point
│   ├── package.json
│   ├── vite.config.js           Vite Build Config
│   ├── tailwind.config.js       Tailwind CSS Config
│   ├── postcss.config.js        PostCSS Config
│   ├── index.html               HTML Template
│   └── Dockerfile               Frontend Docker Image
├── docker-compose.yml           Docker Compose Setup
├── package.json                 Root Package.json
├── .gitignore
└── README.md
```

## 🎨 Kategorien

Alle 16 OSINT Kategorien:
1. Social Media
2. Domain/IP Lookup
3. People Search
4. Email Finder
5. Geolocation
6. Dark Web
7. Code Search
8. Image Search
9. Phone Lookup
10. Username Search
11. Database Leaks
12. Web Archive
13. DNS Tools
14. SSL Certificates
15. Metadata Extraction
16. Other

## ⚙️ Konfiguration

### Backend Environment Variables

Erstelle `backend/.env`:

```
MONGODB_URI=mongodb://admin:password123@localhost:27017/chain-osint?authSource=admin
NODE_ENV=development
PORT=5000
JWT_SECRET=dein_super_geheimes_jwt_key_hier
CORS_ORIGIN=http://localhost:3000
```

### Frontend Environment Variables

Erstelle `frontend/.env`:

```
REACT_APP_API_URL=http://localhost:5000/api
```

## 🔐 Sicherheit

- JWT Authentication für User
- Bcrypt Password Hashing
- CORS Protection
- Input Validation mit express-validator
- Environment Variable Secrets

## 📦 Dependencies

### Backend
- express.js - Web Framework
- mongoose - MongoDB ODM
- jsonwebtoken - JWT Auth
- bcryptjs - Password Hashing
- cors - CORS Middleware
- dotenv - Environment Variables

### Frontend
- react - UI Library
- axios - HTTP Client
- react-router-dom - Routing
- tailwindcss - CSS Framework
- lucide-react - Icons
- vite - Build Tool

## 🚢 Deployment

### Mit Docker (Empfohlen)

```bash
docker-compose up -d
```

### Mit Heroku

```bash
heroku create chain-osint
heroku addons:create mongolab
git push heroku main
```

### Mit AWS/GCP/Azure

Siehe Docker Dokumentation - einfach containerisieren und deployen!

## 📝 Lizenz

MIT License - Frei nutzbar für Security Research & Bildung

---

## 🤝 Beiträge

Möchtest du weitere OSINT Tools hinzufügen? 

1. Tool in `backend/seed.js` hinzufügen
2. `npm run seed` ausführen
3. Pull Request erstellen! 🚀

---

**Chain OSINT** - Intelligenz verbinden. Informationen aggregieren. 🔗

Built by **Terrorize01** for OSINT Enthusiasts & Security Researchers 🔍

*Inspired by OSINT CAT - But Better!* 💪

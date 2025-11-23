# WP Changelog Manager PRO - Sistema Automatico

🚀 **Sistema completo per la gestione automatica delle licenze WordPress con protezione anti-frode**

## 📋 Panoramica del Progetto

Sistema automatizzato per:
- ✅ Vendita automatica plugin WordPress PRO
- ✅ Generazione licenze automatiche
- ✅ Verifica licenze in tempo reale
- ✅ Protezione anti-frode PayPal
- ✅ Admin panel per gestione licenze
- ✅ Plugin WordPress con controllo licenze

## 🗂️ Struttura File

### 📱 **Frontend (Sistema Vendita)**
- `index.html` - Homepage principale
- `wp-changelog-manager.html` - Pagina prodotto
- `auto-license.html` - Sistema automatico acquisto
- `siteworld-login.html` - Sistema login SITEWORLD ID
- `admin-dashboard.html` - Dashboard admin principale
- `beta-dashboard.html` - Dashboard beta tester

### 🔐 **Sistema Licenze**
- `license-admin.html` - Panel admin gestione licenze
- `plugin-simulator.html` - Simulatore plugin WordPress
- `api/verify-license.php` - API verifica licenze (da caricare su server)
- `api/sync-licenses.php` - Sincronizzazione database

### 🔌 **Plugin WordPress**
- `wp-changelog-manager-pro.php` - Plugin WordPress completo

### 📚 **Documentazione**
- `README-SISTEMA-AUTOMATICO.md` - Documentazione sistema
- `PLUGIN-INTEGRATION-GUIDE.md` - Guida integrazione plugin

## 🚀 Setup Rapido

### 1. **Clone del Repository**
```bash
git clone https://github.com/TUO-USERNAME/wp-changelog-manager-pro
cd wp-changelog-manager-pro
```

### 2. **Demo Locale**
- Apri `index.html` in un browser
- Credenziali admin: `admin` / `admin123`
- Testa il sistema automatico da `wp-changelog-manager.html`

### 3. **Deploy Produzione**
```bash
# Carica su hosting
- Carica file HTML su hosting principale
- Carica cartella `/api/` su server per API
- Configura EmailJS per email automatiche
- Aggiorna URL API nel plugin WordPress
```

## 🎯 Workflow Sistema

```
Cliente → Inserisce Email → PayPal → Licenza Generata → Email Automatica
                                           ↓
Plugin WordPress → Verifica API ogni 60s → Admin Può Disattivare → Anti-Frode
```

## 🛡️ Features Anti-Frode

- ✅ **Licenze Pending** fino a conferma pagamento
- ✅ **Disattivazione Istantanea** da admin panel
- ✅ **Plugin Auto-Spegnimento** se licenza disattivata
- ✅ **Verifica Continua** ogni 60 secondi
- ✅ **Logging Completo** di tutte le operazioni

## 📊 Statistiche e Monitoraggio

### Admin Dashboard include:
- 📈 Licenze totali generate
- ✅ Licenze attive
- ⏳ Licenze in attesa pagamento
- 💰 Ricavi stimati
- 📊 Analytics dettagliate

## 🔧 Configurazione

### Variabili da Modificare:
1. **URL API**: In `wp-changelog-manager-pro.php` linea 14
2. **EmailJS**: In `auto-license.html` per email automatiche
3. **PayPal URL**: In `wp-changelog-manager.html`
4. **Admin Key**: In `api/sync-licenses.php`

## 📧 Contatti e Supporto

- **Email**: sitworldweb@gmail.com
- **Sviluppatore**: Lorenzo Agosta
- **Versione**: 2.0.0

## 📄 Licenza

Tutti i diritti riservati © 2024 Lorenzo Agosta / SITEWORLD

---

🎉 **Sistema completamente funzionale e pronto per produzione!** 🚀
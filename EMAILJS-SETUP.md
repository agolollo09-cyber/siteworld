# 📧 Configurazione EmailJS per Admin Panel

## 🔧 Setup EmailJS per Pannello Admin

### 1. **Crea Account EmailJS**
1. Vai su [emailjs.com](https://www.emailjs.com/)
2. Registrati gratuitamente
3. Verifica email

### 2. **Crea Servizio Email**
1. Dashboard → **Email Services**
2. Clicca **Add New Service**
3. Scegli provider (Gmail consigliato)
4. Autorizza accesso
5. Copia il **Service ID**

### 3. **Crea Templates Email**

#### Template 1: **Reinvio Licenza** (`resend_license_template`)
```html
Oggetto: 🔑 La Tua Licenza WP Changelog Manager PRO

Ciao {{customer_name}},

Ti reinviamo la licenza per {{product_name}}:

🔑 **CODICE LICENZA**: {{license_key}}
📅 **Data Acquisto**: {{purchase_date}}

📥 **Download Plugin**: {{download_link}}
🛠️ **Installazione**: Carica il file ZIP nel tuo WordPress

🎯 **Come Attivare**:
1. Installa il plugin
2. Vai in Settings → WP Changelog PRO
3. Inserisci il codice licenza: {{license_key}}
4. Clicca "Verifica Licenza"

✅ **Supporto**: {{support_email}}

Saluti,
{{admin_sender}}
SITEWORLD Team
```

#### Template 2: **Notifica Disattivazione** (`deactivation_template`)
```html
Oggetto: ⚠️ Licenza {{license_key}} Disattivata

Ciao {{customer_name}},

La tua licenza per {{product_name}} è stata disattivata:

🔑 **Licenza**: {{license_key}}  
📅 **Data Disattivazione**: {{deactivation_date}}
❓ **Motivo**: {{reason}}

Il plugin si disattiverà automaticamente entro 60 secondi.

🆘 **Hai Domande?**
Se pensi che sia un errore, contattaci: {{support_email}}

Visita: {{website}}

SITEWORLD Team
```

#### Template 3: **Email Benvenuto** (`welcome_template`)
```html
Oggetto: 🎉 Benvenuto in WP Changelog Manager PRO!

Ciao {{customer_name}}!

Grazie per aver acquistato {{product_name}}!

🔑 **LICENZA**: {{license_key}}
📅 **Acquisto**: {{purchase_date}}

🚀 **INIZIA ORA**:
1. 📥 **Download**: {{download_link}}
2. 🛠️ **Test Plugin**: {{admin_url}}
3. ✉️ **Supporto**: {{support_email}}

La tua licenza è a vita e include:
✅ Changelog illimitati
✅ Template personalizzati  
✅ Notifiche email
✅ Dashboard avanzato
✅ Supporto prioritario

Benvenuto nel team PRO! 🌟

SITEWORLD Team
```

### 4. **Configurazione nel Codice**

Nel file `license-admin.html`, sostituisci:

```javascript
// Sostituisci con le tue credenziali EmailJS
emailjs.init("TUO_USER_ID");

// Nel send email:
await emailjs.send(
    'TUO_SERVICE_ID',        // Service ID EmailJS  
    'resend_license_template', // Template ID
    templateParams
);
```

### 5. **Credenziali da Ottenere**
- **User ID**: Dashboard EmailJS → Integration tab
- **Service ID**: Lista servizi EmailJS
- **Template IDs**: 
  - `resend_license_template`
  - `deactivation_template` 
  - `welcome_template`

### 6. **Test Email**
1. Apri admin panel: `license-admin.html`
2. Trova una licenza demo
3. Clicca "📧 Reinvia Email"
4. Verifica che l'email arrivi

### 7. **Limiti Piano Gratuito**
- **200 email/mese** gratis
- Per volumi maggiori: upgrade piano EmailJS

## 🔒 **Sicurezza**

⚠️ **IMPORTANTE**: Le credenziali EmailJS sono visibili nel codice JavaScript. Per produzione considera:
- Backend API per invio email
- Variabili d'ambiente
- Rate limiting

## ✅ **Una Volta Configurato**

Il pannello admin potrà:
- ✅ Reinviare licenze via email
- ✅ Notificare disattivazioni automaticamente
- ✅ Inviare email di benvenuto
- ✅ Gestire comunicazioni clienti

**Configurazione completa per sistema email professionale!** 📧
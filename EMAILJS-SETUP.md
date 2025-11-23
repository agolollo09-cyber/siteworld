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

**⚠️ IMPORTANTE**: I template EmailJS usano `{{variabile}}` NON `{{customer_name}}`

**Soggetto del Template:**
```
🔑 La Tua Licenza WP Changelog Manager PRO
```

**Corpo del Template:**
```html
Ciao {{to_name}},

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
{{from_name}}
SITEWORLD Team
```

**📝 Variabili Template:**
- `{{to_name}}` - Nome destinatario
- `{{to_email}}` - Email destinatario (automatica)
- `{{from_name}}` - Nome mittente
- `{{license_key}}` - Codice licenza
- `{{product_name}}` - Nome prodotto
- `{{purchase_date}}` - Data acquisto
- `{{download_link}}` - Link download
- `{{support_email}}` - Email supporto

#### Template 2: **Notifica Disattivazione** (`deactivation_template`)

**Soggetto del Template:**
```
⚠️ Licenza {{license_key}} Disattivata
```

**Corpo del Template:**
```html
Ciao {{to_name}},

La tua licenza per {{product_name}} è stata disattivata:

🔑 **Licenza**: {{license_key}}  
📅 **Data Disattivazione**: {{deactivation_date}}
❓ **Motivo**: {{reason}}

Il plugin si disattiverà automaticamente entro 60 secondi.

🆘 **Hai Domande?**
Se pensi che sia un errore, contattaci: {{support_email}}

Visita: {{website}}

{{from_name}}
SITEWORLD Team
```

#### Template 3: **Email Benvenuto** (`welcome_template`)

**Soggetto del Template:**
```
🎉 Benvenuto in WP Changelog Manager PRO!
```

**Corpo del Template:**
```html
Ciao {{to_name}}!

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

{{from_name}}
SITEWORLD Team
```

### 4. **Configurazione nel Codice**

Nel file `license-admin.html`, sostituisci:

```javascript
// ⚠️ SOSTITUISCI con le TUE credenziali EmailJS:
emailjs.init("user_TUO_PUBLIC_KEY");  // User ID dalla sezione Integration

// Nel send email:
await emailjs.send(
    'service_TUO_SERVICE',     // Service ID dalla sezione Email Services
    'resend_license_template',  // Template ID dalla sezione Email Templates  
    {
        to_name: license.email.split('@')[0],
        to_email: license.email,
        from_name: 'Admin SITEWORLD',
        license_key: license.key,
        product_name: 'WP Changelog Manager PRO',
        purchase_date: new Date(license.createdAt).toLocaleDateString('it-IT'),
        download_link: 'https://agolollo09-cyber.github.io/Site-World/wp-changelog-manager.html',
        support_email: 'support@siteworld.it'
    }
);
```

#### **🚨 ESEMPIO REALE CON CREDENZIALI:**
```javascript
// Esempio con credenziali vere (sostituisci con le tue):
emailjs.init("user_A1b2C3d4E5");

await emailjs.send(
    'service_gmail_xyz',
    'resend_license_template',
    templateParams
);
```

### 5. **🔑 Dove Trovare le Credenziali - PASSO PER PASSO**

#### **A. User ID (Public Key)**
1. Accedi a [dashboard.emailjs.com](https://dashboard.emailjs.com)
2. Nel menu laterale clicca **"Integration"**
3. In alto vedrai **"Your Public Key"** - COPIALO
4. Esempio: `user_aBcDeFgHiJ1234567890`

#### **B. Service ID**  
1. Dashboard → **"Email Services"** nel menu laterale
2. Vedrai la lista dei servizi (Gmail, Outlook, etc.)
3. Clicca sul servizio che usi
4. In alto c'è **"Service ID"** - COPIALO  
5. Esempio: `service_xyz123`

#### **C. Template IDs**
1. Dashboard → **"Email Templates"** nel menu laterale
2. Per ogni template che crei, vedrai l'**"Template ID"**
3. IDs da creare:
   - `resend_license_template`
   - `deactivation_template` 
   - `welcome_template`

#### **D. Screenshot Posizioni:**
```
📧 EmailJS Dashboard:
├── Integration ← QUI trovi USER ID (Public Key)
├── Email Services ← QUI trovi SERVICE ID  
└── Email Templates ← QUI trovi TEMPLATE IDs
```

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

## 🎯 **ESEMPIO COMPLETO FUNZIONANTE**

### **Credenziali Example (sostituisci con le tue):**
```javascript
// Dopo aver seguito i passi sopra, avrai qualcosa tipo:
emailjs.init("user_A1b2C3d4E5f6G7h8"); // Il tuo User ID

await emailjs.send(
    'service_gmail123',           // Il tuo Service ID Gmail  
    'resend_license_template',    // Il tuo Template ID
    {
        to_name: 'Cliente',       // Nome destinatario
        to_email: 'cliente@email.com', // Email destinatario
        from_name: 'Admin SITEWORLD',   // Il tuo nome
        license_key: 'WPCM-PRO-2025-ABC123-LIFE',
        product_name: 'WP Changelog Manager PRO',
        purchase_date: '23/11/2025',
        download_link: 'https://agolollo09-cyber.github.io/Site-World/wp-changelog-manager.html',
        support_email: 'siteworldweb@gmail.com'
    }
);
```

### **🔧 TROUBLESHOOTING**

#### **❌ "User ID not found"**
- Vai su: `dashboard.emailjs.com` → **Integration**
- Copia esattamente il **"Your Public Key"**
- Deve iniziare con `user_`

#### **❌ "Service ID not found"** 
- Vai su: **Email Services** → Il tuo servizio Gmail
- Copia il **Service ID** (NON il nome del servizio)
- Deve iniziare con `service_`

#### **❌ "Template ID not found"**
- Vai su: **Email Templates** → Il tuo template  
- Copia esattamente il **Template ID**
- Deve essere identico a quello che hai creato

#### **❌ "Forbidden - quota exceeded"**
- Piano gratuito: 200 email/mese
- Controlla usage nella dashboard
- Upgrade piano se necessario

### **✅ TEST RAPIDO**
1. Apri browser console (F12)
2. Vai su: `https://agolollo09-cyber.github.io/Site-World/license-admin.html`
3. Clicca "📧 Reinvia Email" su qualsiasi licenza
4. Controlla console per errori
5. Controlla email in arrivo

**Configurazione completa per sistema email professionale!** 📧
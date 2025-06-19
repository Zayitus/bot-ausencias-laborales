# 📖 Manual de Instalación y Configuración

## Sistema de Gestión de Ausentismo Laboral

Este manual te guiará paso a paso para implementar el sistema completo en tu organización.

---

## 📋 **Prerrequisitos**

### **🔑 Cuentas Necesarias**
- [ ] **n8n Cloud** - [n8n.io](https://n8n.io) (plan gratuito disponible)
- [ ] **Google Workspace** - Con permisos de administrador
- [ ] **Telegram** - Para crear el bot
- [ ] **OpenAI** - API key para OCR de imágenes
- [ ] **Google Cloud** - Para API de Gemini (gratuito)

### **⚙️ Permisos Requeridos**
- [ ] **Google Sheets API** - Lectura/escritura
- [ ] **Google Drive API** - Lectura/escritura/upload
- [ ] **Gmail API** - Envío de emails
- [ ] **Admin en Telegram** - Para crear bots

---

## 🚀 **Instalación Paso a Paso**

### **Paso 1: Configurar Google Cloud APIs**

#### **1.1 Habilitar APIs**
```bash
# Ve a Google Cloud Console (console.cloud.google.com)
# Crea un nuevo proyecto o selecciona uno existente
# Habilita las siguientes APIs:
```

- **Google Sheets API**
- **Google Drive API** 
- **Gmail API**
- **Google AI (Gemini) API**

#### **1.2 Crear Service Account**
```bash
# En Google Cloud Console:
1. Ve a "IAM & Admin" → "Service Accounts"
2. Click "Create Service Account"
3. Nombre: "n8n-bot-ausencias"
4. Rol: "Editor" (o permisos específicos)
5. Descargar JSON key file
```

#### **1.3 Configurar OAuth2 (Para Gmail)**
```bash
# En Google Cloud Console:
1. Ve a "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "OAuth 2.0 Client ID"
3. Application type: "Web application"
4. Authorized redirect URIs: https://[tu-instancia-n8n].app.n8n.cloud/rest/oauth2-credential/callback
```

### **Paso 2: Crear Bot de Telegram**

#### **2.1 Hablar con BotFather**
```bash
# En Telegram, busca @BotFather
/start
/newbot

# Sigue las instrucciones:
Nombre del bot: "Ausencias [Tu Empresa]"
Username: "ausencias[tuempresa]bot"

# Guarda el TOKEN que te da
```

#### **2.2 Configurar Webhook**
```bash
# El webhook será configurado automáticamente por n8n
# URL será: https://[tu-instancia].app.n8n.cloud/webhook/[id-único]
```

### **Paso 3: Configurar APIs de IA**

#### **3.1 OpenAI API Key**
```bash
# Ve a platform.openai.com
1. Crea cuenta o inicia sesión
2. Ve a "API Keys"
3. Click "Create new secret key"
4. Guarda la key (empieza con sk-)
```

#### **3.2 Google Gemini API**
```bash
# Ve a ai.google.dev
1. Click "Get API key"
2. Selecciona tu proyecto de Google Cloud
3. Copia la API key
```

### **Paso 4: Crear Base de Datos (Google Sheets)**

#### **4.1 Crear Planilla Principal**
```bash
# Crea una nueva Google Sheet llamada "Sistema Ausencias"
# URL ejemplo: https://docs.google.com/spreadsheets/d/[ID-ÚNICO]/edit
```

#### **4.2 Configurar Hojas**

**Hoja 1: "Inasistencias"**
```
Columnas necesarias:
A: Numero_Session
B: telegram_id  
C: telegram_first_name
D: telegram_last_name
E: telegram_language
F: fecha_registro
G: nombre_completo
H: motivo 
I: legajo enviado
J: Legajo confirmado
K: certificado
L: notificado_a_rrhh
M: diagnostico
N: dias_reposo
O: fecha_emision_certificado
P: obra_social
Q: nombre_medico
R: matricula_medico
S: fecha_convertida
T: Hora_convertida
U: Sector
```

**Hoja 2: "Session"**
```
Columnas:
A: SESSION
B: STATE
```

**Hoja 3: "Base de Datos de empleados(Mock)"**
```
Columnas:
A: Numero de Legajo
B: Nombre y Apellido
C: Sector
D: Email
```

**Hoja 4: "Recordatorios_Pendientes"**
```
Columnas:
A: Numero_Session
B: chat_id
C: fecha_limite_24h
D: recordatorio_enviado
E: nombre_empleado
```

#### **4.3 Permisos de la Planilla**
```bash
1. Click "Compartir" en Google Sheets
2. Agregar el email del Service Account con permisos de "Editor"
3. Configurar como "Cualquiera con el enlace puede ver"
```

### **Paso 5: Configurar Google Drive**

#### **5.1 Crear Carpeta de Certificados**
```bash
1. Ve a Google Drive
2. Crea carpeta llamada "Certificados"
3. Copia el ID de la carpeta desde la URL
   URL: https://drive.google.com/drive/folders/[FOLDER-ID]
4. Compartir con Service Account como "Editor"
```

### **Paso 6: Configurar n8n Cloud**

#### **6.1 Crear Cuenta n8n**
```bash
1. Ve a n8n.io
2. Sign up para cuenta gratuita
3. Verifica email
4. Accede a tu instancia: https://[tu-nombre].app.n8n.cloud
```

#### **6.2 Configurar Credenciales**

**Telegram Credentials:**
```json
{
  "name": "Telegram Bot",
  "type": "telegramApi",
  "data": {
    "accessToken": "TU_BOT_TOKEN_AQUI"
  }
}
```

**Google Service Account:**
```json
{
  "name": "Google Service Account",
  "type": "googleApi",
  "data": {
    "serviceAccountEmail": "tu-service-account@proyecto.iam.gserviceaccount.com",
    "privateKey": "-----BEGIN PRIVATE KEY-----\n[TU PRIVATE KEY]\n-----END PRIVATE KEY-----\n"
  }
}
```

**Gmail OAuth2:**
```json
{
  "name": "Gmail OAuth2",
  "type": "gmailOAuth2",
  "data": {
    "clientId": "tu-client-id.apps.googleusercontent.com",
    "clientSecret": "tu-client-secret"
  }
}
```

**OpenAI API:**
```json
{
  "name": "OpenAI",
  "type": "openAiApi", 
  "data": {
    "apiKey": "sk-[TU-API-KEY]"
  }
}
```

**Google Gemini:**
```json
{
  "name": "Google Gemini",
  "type": "googlePalmApi",
  "data": {
    "apiKey": "TU_GEMINI_API_KEY"
  }
}
```

### **Paso 7: Importar Workflows**

#### **7.1 Descargar Workflows**
```bash
# Descarga los 4 archivos JSON desde:
# https://github.com/Zayitus/bot-ausencias-laborales/tree/main/workflows
```

#### **7.2 Importar en n8n**
```bash
1. En n8n, click "+" → "Import from file"
2. Importa uno por uno:
   - ChatBot_Ausencias_Laborales_Final.json
   - Procesador_y_Verificador_de_Certificados_OCR.json  
   - Notificador_de_Ausencias_a_RRHH.json
   - Manda_Advertencias_Falta_Documentacion.json
```

#### **7.3 Configurar IDs en los Workflows**

**En cada workflow, actualizar:**
```bash
# Google Sheets Document ID:
- Buscar nodos "Google Sheets"
- Cambiar documentId por tu ID de planilla
- Tu ID está en la URL: /spreadsheets/d/[ESTE-ES-TU-ID]/edit

# Google Drive Folder ID:
- Buscar nodos "Google Drive" 
- Cambiar folderId por tu ID de carpeta Certificados

# Email destinatario:
- En workflow "Notificador RRHH"
- Cambiar "schvartz.g@gmail.com" por email de tu RRHH
```

### **Paso 8: Activar Sistema**

#### **8.1 Activar Workflows**
```bash
# En n8n, para cada workflow:
1. Click en el toggle "Active" (debe estar en ON/azul)
2. Verificar que no hay errores
```

#### **8.2 Verificar Conexiones**
```bash
# Test cada credencial:
1. Ve a "Credentials" en n8n
2. Para cada credencial, click "Test" 
3. Debe mostrar "Connection successful"
```

---

## 🧪 **Testing Inicial**

### **Test 1: Bot de Telegram**
```bash
1. Busca tu bot en Telegram: @[username-de-tu-bot]
2. Envía "/start"
3. Debe responder con menú de motivos
4. Prueba flujo completo con datos mock
```

### **Test 2: OCR de Certificados**
```bash
1. Completa flujo hasta envío de certificado
2. Envía imagen de certificado médico
3. Verifica que se procese y guarde en Drive
4. Revisa que datos se extraigan en Google Sheets
```

### **Test 3: Notificaciones RRHH**
```bash
1. Completa una ausencia
2. Espera 1 minuto (trigger automático)
3. Verifica que llegue email a RRHH
4. Confirma actualización en Sheets
```

---

## 🎯 **Configuración para Producción**

### **Datos Reales**
```bash
1. Reemplazar base de datos mock con empleados reales
2. Configurar email real de RRHH
3. Ajustar horarios de triggers si es necesario
4. Configurar backup de Google Sheets
```

### **Monitoreo**
```bash
1. Activar logs en n8n
2. Configurar alertas por fallos
3. Monitorear uso de API quotas
4. Revisar dashboard semanalmente
```

### **Mantenimiento**
```bash
1. Backup semanal de workflows
2. Revisión mensual de credenciales
3. Actualización de documentación
4. Testing trimestral completo
```

---

## ❓ **Troubleshooting Común**

### **Error: "Webhook not found"**
```bash
# Solución:
1. Reactivar el workflow de ChatBot
2. Verificar que webhook URL esté correcta en Telegram
3. Re-importar workflow si es necesario
```

### **Error: "Google Sheets access denied"**
```bash
# Solución:
1. Verificar permisos del Service Account
2. Confirmar que APIs están habilitadas
3. Re-compartir planilla con Service Account
```

### **Error: "OpenAI API limit exceeded"**
```bash
# Solución:
1. Verificar quota en OpenAI dashboard
2. Ajustar límites de procesamiento
3. Implementar retry logic si es necesario
```

---

## 📞 **Soporte**

Para consultas técnicas durante primeros 30 días:
- **Email**: schvartz.g@gmail.com
- **Documentación**: Este manual
- **Código fuente**: https://github.com/Zayitus/bot-ausencias-laborales

---

**🎉 ¡Sistema listo para usar!** Una vez completados todos los pasos, tu organización tendrá un sistema automatizado completo para gestión de ausencias laborales.

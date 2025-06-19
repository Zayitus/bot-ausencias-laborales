# 👥 Manual de Usuario
## Sistema de Gestión de Ausencias Laborales - TECNOMYL S.A.

---

## 📋 **1. Introducción al Sistema**

Bienvenido al **Sistema Automatizado de Gestión de Ausencias Laborales** de TECNOMYL S.A. Este sistema revoluciona la forma en que reportas y gestionas las ausencias, ofreciendo un proceso **completamente digitalizado, rápido y eficiente**.

### **🎯 Beneficios del Nuevo Sistema:**
- ⚡ **Reporte en 3 minutos** vs 30 minutos del proceso manual
- 🕐 **Disponible 24/7** - No hay horarios de oficina
- 📱 **Interface familiar** - Usa Telegram que ya conocés
- ✅ **Confirmación inmediata** con código de seguimiento
- 🔄 **Recordatorios automáticos** para cumplir plazos

### **🎪 Tipos de Ausencia Soportados:**
- 🏥 **Enfermedad** (requiere certificado médico)
- 👶 **Nacimiento** (requiere acta de nacimiento)
- 😢 **Fallecimiento** (requiere acta de defunción)
- 👨‍👩‍👧‍👦 **Cuidados Familiares** (requiere certificado médico del familiar)

---

## 👤 **2. Para Empleados: Cómo Reportar tu Ausencia**

### **🤖 Paso a Paso: Usando el Chatbot de Telegram**

#### **2.1. Iniciar la Conversación**

**¡Es súper fácil!** Solo necesitás seguir estos pasos:

1. **Abre Telegram** en tu celular o computadora
2. **Busca el bot**: `@Ausencias2Bot`
3. **Presiona "Iniciar"** o envía cualquier mensaje
4. **El bot te saluda** y te muestra el menú de motivos

#### **2.2. Seleccionar Motivo de Ausencia**

**El bot te muestra 4 botones claros:**
- 🏥 **Enfermedad**
- 😢 **Fallecimiento**  
- 👶 **Nacimiento**
- 👨‍👩‍👧‍👦 **Cuidados Familiares**

**Simplemente tocá el botón** correspondiente a tu situación.

#### **2.3. Proporcionar tus Datos**

**El bot te pide información paso a paso:**

1. **Tu nombre completo**
   - Escribí tu nombre tal como aparece en la planilla de empleados
   - Ejemplo: "Juan Carlos Pérez"

2. **Tu número de legajo**
   - Ingresá tu legajo de 5 dígitos
   - Ejemplo: "12345"
   - ✅ Si tu legajo es válido → Confirmación inmediata
   - ⚠️ Si no está en el sistema → Proceso manual de revisión

#### **2.4. ¿Tenés Certificado Médico?**

**Para ausencias por enfermedad, el bot pregunta:**
- **"¿Tenés certificado médico por tu ausencia?"**
- **Respondé**: "Sí" o "No"

**🟢 Si tenés certificado:**
- El bot te pide que lo adjuntes
- Podés enviar **foto** o **archivo PDF**
- Máximo **5 MB** de tamaño

**🟡 Si no tenés certificado:**
- El bot registra que falta documentación
- **Tenés 24 horas** para enviarlo
- Recibirás **recordatorio automático** 2 horas antes del vencimiento

#### **2.5. Adjuntar Documentos**

**💡 Formatos Aceptados:**
- ✅ **Fotos**: JPG, PNG (recomendado para certificados impresos)
- ✅ **PDFs**: Archivo digital del certificado
- ⚠️ **Documentos Word**: En desarrollo (próximamente)

**📱 Cómo Adjuntar:**
1. **Para fotos**: Usar la cámara de Telegram o galería
2. **Para PDFs**: Usar "Adjuntar archivo" en Telegram
3. **Calidad**: Asegurate que el texto se lea claramente

**🚫 Archivo muy grande:**
- Si el archivo supera 5 MB, el bot te avisará
- Reduce la calidad de la imagen o comprímela

#### **2.6. Confirmación del Trámite**

**🎉 ¡Trámite Exitoso!**

Recibirás uno de estos mensajes:

**✅ Trámite Completo:**
```
✅ Trámite completado con éxito.
Hemos recibido y registrado tu certificado.
Tu número de confirmación final es: OK-XXXXXX
```

**🔶 Trámite Provisional:**
```
✅ Hemos recibido y registrado tu certificado.
Tu número de registro provisional es: PROV-XXXXXX
Recursos Humanos revisará tu caso a la brevedad.
```

**📝 Guarda tu código** - Es tu comprobante oficial.

### **🚨 Recordatorios Importantes**

- ⚠️ **El médico laboral** podría concurrir a tu domicilio durante la jornada
- ⏰ **Plazo de certificados**: 24 horas máximo
- 📱 **Recordatorios automáticos**: El sistema te avisará 2 horas antes del vencimiento

---

## 👨‍💼 **3. Para Recursos Humanos: Gestión de Ausencias**

### **📊 3.1. Panel de Control Principal (Google Sheets)**

**Acceso directo a todos los datos:**
```
🔗 https://docs.google.com/spreadsheets/d/1TTBchw8rmSAQ-6d05BcvgRYae6qfbDT6YmKBy6c1t20/edit#gid=2002440872
```

#### **📋 Interpretación de Columnas Clave:**

| Columna | Descripción | Valores Posibles |
|---------|-------------|------------------|
| **Numero_Session** | Código único del trámite | OK-XXXXX, PROV-XXXXX |
| **fecha_registro** | Timestamp del reporte | Fecha/hora automática |
| **nombre_completo** | Empleado que reportó | Texto libre |
| **motivo** | Tipo de ausencia | enfermedad, nacimiento, etc. |
| **legajo enviado** | Legajo ingresado | Número de 5 dígitos |
| **Legajo confirmado** | Validación del legajo | `OK` / `NOK. REVISAR` |
| **certificado** | Estado del documento | `OK` / `NOK. RECORDAR EN 22 HS` |
| **notificado_a_rrhh** | Email enviado | `SI` / `NO` |

#### **🤖 Datos Extraídos por IA (OCR):**

| Campo | Descripción |
|-------|-------------|
| **diagnostico** | Diagnóstico médico extraído |
| **dias_reposo** | Días de reposo prescritos |
| **fecha_emision_certificado** | Fecha del certificado |
| **obra_social** | Obra social del paciente |
| **nombre_medico** | Médico que emitió el certificado |
| **matricula_medico** | Matrícula profesional |

### **📁 3.2. Gestión de Documentos (Google Drive)**

**Carpeta centralizada de certificados:**
```
🔗 https://drive.google.com/drive/folders/1wZQbZobyqgJvBf7yU-h9-AXKJSzocWqW?usp=drive_link
```

#### **📝 Nomenclatura de Archivos:**
```
Formato: sessionId_fecha_legajo.extensión
Ejemplo: 123456_2025-06-19_12345.pdf
```

#### **🔍 Búsqueda de Documentos:**
1. **Por Legajo**: Buscar "12345" encuentra todos los certificados del empleado
2. **Por Fecha**: Buscar "2025-06-19" encuentra certificados del día
3. **Por Session**: Buscar "OK-123456" encuentra el documento específico

### **📧 3.3. Notificaciones Automáticas**

**Sistema de emails automáticos a**: `schvartz.g@gmail.com`

#### **📨 Contenido del Email:**
```
Asunto: Nueva Ausencia Registrada: [Nombre] (Legajo: [Legajo])

Detalles:
• Empleado: [Nombre Completo]
• Legajo: [Número]
• Motivo: [Tipo de ausencia]
• Certificado: [Estado/Link]
• Fecha: [Timestamp]

Enlace al certificado: [URL de Google Drive]
```

#### **⚙️ Configuración de Notificaciones:**
- **Frecuencia**: Revisión cada minuto
- **Filtro**: Solo ausencias con `notificado_a_rrhh = NO`
- **Actualización**: Marca automáticamente como `SI` después del envío

### **📊 3.4. Dashboard Analytics (Looker Studio)**

**Panel interactivo con métricas en tiempo real:**
```
🔗 [Dashboard en desarrollo - próximamente disponible]
```

#### **📈 KPIs Disponibles:**
- **Tasa de finalización**: 88% actual
- **Distribución por motivo**: Enfermedad 85.7%, Cuidados 14.3%
- **Ausencias por sector**: Distribución departamental
- **Timeline**: Evolución temporal de ausencias
- **Personal**: Rankings de empleados con más ausencias

### **🔄 3.5. Flujos de Trabajo Automatizados**

#### **⚡ Procesos que se Ejecutan Solos:**

1. **Detección de Nuevas Ausencias** (cada minuto)
   - Busca registros no notificados
   - Envía email a RRHH
   - Actualiza estado

2. **Procesamiento OCR** (cada minuto)
   - Monitorea carpeta Drive
   - Extrae datos de certificados
   - Actualiza base de datos

3. **Recordatorios** (cada 30 minutos)
   - Calcula plazos vencidos
   - Envía alertas a empleados
   - Notifica a RRHH de incumplimientos

#### **🛠️ Casos que Requieren Intervención Manual:**

**⚠️ Legajo No Encontrado:**
1. Revisar datos del empleado en pestaña "Inasistencias"
2. Verificar contra base de datos de empleados
3. Actualizar campo "Legajo confirmado" manualmente si corresponde

**⚠️ Certificado No Procesado:**
1. Verificar que esté en la carpeta correcta de Drive
2. Confirmar que no supere 5 MB
3. Re-subir si es necesario para trigger del OCR

**⚠️ Información Incompleta:**
1. Contactar al empleado para aclaración
2. Solicitar documentación adicional si es necesaria
3. Actualizar registro manualmente

---

## 🚀 **4. Funcionalidades Próximas (Roadmap)**

### **📋 Fase 2: Multi-Canal (Q2 2025)**
- **Google Forms**: Canal web alternativo para reportes
- **Unificación**: Consolidación de datos Telegram + Forms
- **API REST**: Integración con sistemas externos

### **📱 Fase 3: Mobile & Enterprise (Q3-Q4 2025)**
- **App Móvil**: Aplicación nativa iOS/Android
- **Base de Datos**: Migración a Firebase para mayor robustez
- **Roles y Permisos**: Sistema de autenticación avanzado

### **🤖 Fase 4: IA Avanzada (Q1 2026)**
- **Documentos Word**: Soporte completo para .docx
- **OCR Multiidioma**: Inglés y portugués
- **Validación Médica**: Cross-check con registros oficiales

### **📊 Fase 5: Analytics Predictivo (Q2 2026)**
- **Predicción**: Ausentismo estacional anticipado
- **Anomalías**: Detección automática de patrones inusuales
- **BI Integration**: Conexión con sistemas empresariales

---

## ❓ **5. Preguntas Frecuentes (FAQ)**

### **👤 Para Empleados:**

**❓ ¿Qué pasa si no tengo Telegram?**
- Descargá la app gratuita desde Google Play o App Store
- Es segura y no requiere número de teléfono para usar bots

**❓ ¿Puedo reportar ausencia fuera del horario de oficina?**
- ¡Sí! El sistema está disponible 24/7, todos los días

**❓ ¿Qué pasa si olvido mi código de confirmación?**
- El código queda registrado en el sistema
- RRHH puede consultarlo con tu nombre y fecha

**❓ ¿Cuánto tiempo tengo para enviar el certificado?**
- **24 horas** desde el reporte inicial
- Recibirás recordatorio 2 horas antes del vencimiento

**❓ ¿Qué formato debe tener el certificado?**
- Cualquier formato legible: foto clara o PDF
- Máximo 5 MB de tamaño

### **👨‍💼 Para RRHH:**

**❓ ¿Cómo sé si hay nuevas ausencias?**
- Recibirás email automático en tiempo real
- También podés revisar la planilla directamente

**❓ ¿Qué hago si el legajo no se valida?**
- Revisar contra base de empleados actual
- Contactar al empleado para verificar
- Actualizar manualmente si corresponde

**❓ ¿Cómo accedo a un certificado específico?**
- Buscar por número de sesión en Google Drive
- Usar filtros de fecha o legajo
- Click directo desde el link en la planilla

**❓ ¿Puedo generar reportes personalizados?**
- Sí, usando filtros en Google Sheets
- Dashboard de Looker Studio para analytics avanzado
- Exportar datos a Excel si es necesario

---

## 🆘 **6. Soporte Técnico**

### **📞 Contacto:**
**Equipo de Desarrollo - Grupo 1 PP2**
- **Email principal**: schvartz.g@gmail.com
- **Proyecto**: Sistema Automatizado de Gestión de Ausencias

### **🕐 Horarios de Soporte:**
- **Período académico**: 30 días post-implementación
- **Alcance**: Bugs críticos, configuración inicial, consultas de uso
- **Exclusiones**: Nuevas funcionalidades, modificaciones del sistema

### **📖 Recursos de Ayuda:**
- **Manual de Instalación**: `Manual_de_instalacion.md`
- **Documentación Técnica**: `docs/desarrollo_del_sistema.md`
- **Código Fuente**: https://github.com/Zayitus/bot-ausencias-laborales

---

## 📄 **7. Información Legal**

### **🔒 Privacidad y Datos:**
- Todos los datos se almacenan en Google Cloud (certificado SOC 2)
- Acceso restringido solo a personal autorizado de RRHH
- Cumplimiento con Ley Argentina de Protección de Datos

### **📜 Licencia:**
- Sistema disponible bajo **MIT License**
- Código fuente abierto para modificaciones futuras
- Sin restricciones para uso comercial interno

---

**Copyright (c) 2025 Grupo 1 PP2 - TECNOMYL S.A.**

*Este manual corresponde a la versión MVP del Sistema de Gestión de Ausencias Laborales. Las funcionalidades pueden expandirse según roadmap de desarrollo.*

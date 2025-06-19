# 🏥 Sistema de Gestión de Ausentismo Laboral

Este repositorio contiene el desarrollo de un **sistema automatizado end-to-end** para la gestión integral de ausencias laborales. La solución fue creada como parte de las Prácticas Profesionalizantes para el Centro Educativo Técnico de Nivel Superior "Malvinas Argentinas", realizada en la organización **TECNOMYL S.A.**

El sistema utiliza un chatbot de Telegram como interfaz principal para los empleados y automatiza completamente el registro, procesamiento de documentos, seguimiento y análisis de las inasistencias, culminando en un dashboard interactivo para la toma de decisiones.

## 🎯 **Funcionalidades Clave**

### **💬 Interfaz Conversacional Avanzada**
- **Chatbot en Telegram** con flujo guiado paso a paso
- **Botones interactivos** para selección de motivos de ausencia
- **Sistema de sesiones** que mantiene contexto durante la conversación
- **Validación en tiempo real** de datos ingresados

### **📋 Gestión Integral de Motivos**
- **Enfermedad**: Requiere certificado médico con validación de plazo (24hs)
- **Nacimiento**: Solicita acta de nacimiento
- **Fallecimiento**: Requiere acta de defunción  
- **Cuidados Familiares**: Certificación médica del familiar

### **🔍 Procesamiento Inteligente de Documentos (OCR)**
- **📄 PDFs**: Extracción directa de texto + análisis con IA
- **🖼️ Imágenes**: OCR visual con OpenAI GPT-4O
- **🤖 Análisis con Google Gemini**: Estructura automática de información médica
- **📊 Extracción de datos**: Días de reposo, diagnóstico, médico, matrícula, obra social
- **⚠️ Validación de tamaño**: Control automático de archivos (máx. 5MB)

### **✅ Validación y Trazabilidad**
- **Verificación de legajos** contra base de datos de empleados
- **Nomenclatura automática** de archivos: `sessionId_fecha_legajo.ext`
- **Códigos de confirmación** únicos para cada trámite
- **Auditoría completa** de todo el proceso

### **📧 Automatización de Comunicaciones**
- **Notificaciones automáticas a RRHH** por email
- **Sistema de recordatorios** antes del vencimiento de plazos
- **Alertas de compliance** para casos urgentes
- **Confirmaciones al empleado** con códigos de seguimiento

### **📊 Dashboard y Analytics**
- **Looker Studio**: Tablero interactivo con KPIs en tiempo real
- **Métricas por motivo**: Distribución de tipos de ausencia
- **Análisis por sector**: Tendencias departamentales
- **Timeline de ausencias**: Evolución temporal
- **Tasa de finalización**: Seguimiento de eficiencia del proceso

## 🏗️ **Arquitectura y Tecnologías**

### **🔧 Stack Tecnológico Principal**
- **n8n Cloud**: Motor de automatización y workflows
- **Telegram Bot API**: Interfaz conversacional principal
- **Google Workspace**:
  - **Sheets**: Base de datos flexible y gestión de estados
  - **Drive**: Almacenamiento seguro de certificados
  - **Gmail API**: Notificaciones automatizadas
- **OpenAI GPT-4O**: OCR visual avanzado
- **Google Gemini 2.5**: Análisis y estructuración de texto médico
- **Looker Studio**: Visualización de datos y dashboards

### **📦 Componentes del Sistema**

El ecosistema está compuesto por **4 flujos de trabajo interconectados**:

1. **`ChatBot_Ausencias_Laborales_Final.json`**
   - Flujo principal de conversación
   - Gestión de sesiones y estados
   - Validación de datos y legajos
   - Recepción de documentos

2. **`Procesador_y_Verificador_de_Certificados_OCR.json`**
   - Monitoreo automático de Google Drive
   - OCR multi-formato (PDF, imágenes)
   - Análisis con IA para extracción de datos médicos
   - Estructuración automática en JSON

3. **`Notificador_de_Ausencias_a_RRHH.json`**
   - Detección de nuevas ausencias
   - Envío automático de notificaciones por email
   - Actualización de estados de notificación

4. **`Manda_Advertencias_Falta_Documentacion.json`**
   - Monitoreo de plazos de documentación
   - Recordatorios automáticos 2 horas antes del vencimiento
   - Gestión de compliance temporal

## 🚀 **Roadmap y Futuras Implementaciones**

### **📋 Fase 2: Multi-Channel Integration**
- **Google Forms**: Canal alternativo para registro de ausencias
- **Unificación de datos**: Consolidación de Telegram + Forms en base única
- **API REST**: Endpoints para integración con sistemas externos

### **🔥 Fase 3: Escalabilidad Enterprise**
- **Firebase NoSQL**: Migración a base de datos más robusta
- **Microservicios**: Arquitectura distribuida
- **Authentication**: Sistema de roles y permisos
- **Mobile App**: Aplicación nativa complementaria

### **📄 Fase 4: OCR Avanzado**
- **Soporte .docx completo**: Integración estable con ConvertAPI
- **Múltiples idiomas**: OCR en inglés y portugués
- **Validación médica**: Cross-check con bases de médicos habilitados
- **ML personalizado**: Modelos entrenados específicamente para certificados argentinos

### **📊 Fase 5: Analytics Avanzado**
- **Predictive Analytics**: Predicción de ausentismo estacional
- **Detección de patrones**: Identificación automática de anomalías
- **Reportes ejecutivos**: Dashboards personalizados por rol
- **Integration BI**: Conexión con sistemas de Business Intelligence

## 👥 **Equipo del Proyecto - Grupo 1 PP2**

Este proyecto fue desarrollado en el marco de las Prácticas Profesionalizantes por:

- **Ariel Altamirano**
- **Ezequiel Caballero** 
- **Gastón Schvartz**

**Institución**: Centro Educativo Técnico de Nivel Superior "Malvinas Argentinas"  
**Carrera**: Técnico Superior en Ciencia de Datos e Inteligencia Artificial  
**Organización**: TECNOMYL S.A.

## 🔧 **Instalación y Configuración**

### **📋 Prerrequisitos**
- Cuenta de **n8n Cloud** o instancia self-hosted
- **Bot de Telegram** configurado (vía @BotFather)
- **Google Workspace** con APIs habilitadas:
  - Google Sheets API
  - Google Drive API  
  - Gmail API
- **APIs de IA**:
  - OpenAI API Key
  - Google Gemini API Key
- **Looker Studio** para dashboards

### **⚙️ Pasos de Instalación**

1. **Clonar el repositorio**:
```bash
git clone https://github.com/Zayitus/bot-ausencias-laborales.git
cd bot-ausencias-laborales
```

2. **Configurar credenciales**:
   - Crear archivo `credentials-template.json`
   - Configurar todas las APIs según documentación

3. **Importar workflows en n8n**:
   - Importar los 4 archivos JSON
   - Configurar credenciales en cada nodo
   - Ajustar IDs de Google Sheets según tu entorno

4. **Configurar base de datos mock**:
   - Crear hojas de cálculo en Google Sheets
   - Importar datos de empleados de prueba
   - Configurar permisos de acceso

5. **Activar el sistema**:
   - Activar todos los workflows
   - Verificar conectividad entre componentes
   - Ejecutar tests con datos mock

## 📊 **Métricas de Performance**

### **🎯 Resultados del MVP**
- **88% Tasa de finalización** en conversaciones
- **100% Automatización** de notificaciones a RRHH
- **~30 segundos** tiempo promedio de procesamiento OCR
- **95% Precisión** en extracción de datos de certificados

### **📈 Formatos Soportados**
- ✅ **PDF**: 100% funcional
- ✅ **JPG/PNG**: 100% funcional  
- ⚠️ **DOCX**: En desarrollo (Fase 4)

## 🤝 **Contribuir**

Las contribuciones son bienvenidas. Por favor:

1. Haz fork del proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Haz commit de tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 **Licencia y Soporte**

### **📜 Licencia MIT**
El código fuente y los flujos de trabajo están licenciados bajo **MIT License**. Ver el archivo `LICENSE` para más detalles.

**Copyright (c) 2025 Grupo 1 PP2**

## 📞 **Contacto**

Para consultas sobre el proyecto:

**Gastón Schvartz** - schvartz.g@gmail.com  
**Proyecto Link**: https://github.com/Zayitus/bot-ausencias-laborales

---

⭐ **¡Dale una estrella al proyecto si te resultó útil!**

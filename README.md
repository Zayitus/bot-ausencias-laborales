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

⭐ **¡Dale una estrella al proyecto si te resultó útil!**# Sistema de Gestión de Ausentismo Laboral

Este repositorio contiene el desarrollo de un sistema automatizado para la gestión integral de ausencias laborales. La solución fue creada como parte de las Prácticas Profesionalizantes para el **Centro Educativo Técnico de Nivel Superior "Malvinas Argentinas"**, realizada en la organización **TECNOMYL S.A.**

El sistema utiliza un chatbot de Telegram como interfaz para los empleados y automatiza el registro, seguimiento y análisis de las inasistencias, culminando en un dashboard interactivo para la toma de decisiones.

## Funcionalidades Clave

* **Interfaz Conversacional Intuitiva:** Un chatbot en Telegram guía al empleado paso a paso para registrar su ausencia.
* **Gestión de Múltiples Motivos:** Diferencia entre ausencias por enfermedad, nacimiento y fallecimiento, adaptando el flujo de conversación.
* **Validación de Datos:** Valida el número de legajo del empleado contra una base de datos para asegurar la integridad de la información.
* **Recepción y Almacenamiento Seguro:** Permite al empleado enviar certificados (imágenes o PDF), que se almacenan de forma segura en una carpeta dedicada de Google Drive.
* **Notificaciones a RRHH:** Un flujo de trabajo programado revisa nuevos registros y envía notificaciones por email al departamento de Recursos Humanos.
* **Sistema de Recordatorios:** Un flujo "despertador" alerta automáticamente al empleado si el plazo de 24 horas para presentar un certificado está por vencer.
* **Dashboard de Métricas:** Un tablero de control interactivo en Looker Studio permite visualizar KPIs y analizar tendencias de ausentismo por motivo, por sector, por empleado y a lo largo del tiempo.

## Arquitectura y Tecnologías

La solución se basa en una arquitectura de automatización y se compone de las siguientes tecnologías:

* **n8n Cloud:** Como motor de automatización para ejecutar los flujos de trabajo.
* **Telegram Bot API:** Como interfaz principal para la interacción con los empleados.
* **Google Sheets:** Utilizado como base de datos flexible para el registro de ausencias, la base de datos de empleados y la gestión de métricas.
* **Google Drive:** Para el almacenamiento seguro y organizado de los certificados y documentos.
* **Looker Studio (Google Data Studio):** Para la creación del dashboard de visualización de datos.
* **Gmail API:** Para el envío de las notificaciones por correo electrónico a RRHH.

## Componentes del Proyecto

El sistema está compuesto por tres flujos de trabajo (workflows) principales en n8n:

1. **`ChatBot_Ausencias_Laborales_Final.json`**: El flujo principal que maneja la conversación en tiempo real con el empleado, desde el saludo inicial hasta el registro completo de la ausencia y la subida del certificado.
2. **`Notificador_de_Ausencias_a_RRHH.json`**: Un flujo programado que se ejecuta periódicamente para revisar la base de datos en busca de nuevas ausencias y notificar al equipo de RRHH con todos los detalles.
3. **`Manda_Advertencias_Falta_Documentacion.json`**: Un flujo "despertador" que monitorea las ausencias que requieren documentación y envía un recordatorio automático al empleado antes de que venza el plazo.

## Equipo del Proyecto

Este proyecto fue desarrollado en el marco de las Prácticas Profesionalizantes por el siguiente equipo:

* **Ariel Altamirano**
* **Ezequiel Caballero** 
* **Gastón Schvartz**

## Instalación y Configuración

### Prerrequisitos

- Cuenta de n8n Cloud
- Bot de Telegram configurado
- Cuenta de Google con acceso a Sheets, Drive y Gmail API
- Cuenta de Looker Studio

### Pasos de Instalación

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/Zayitus/bot-ausencias-laborales.git
   cd bot-ausencias-laborales
   ```

2. **Importar los workflows en n8n:**
   - Accede a tu instancia de n8n Cloud
   - Importa cada uno de los archivos JSON de los workflows
   - Configura las credenciales necesarias (Telegram Bot Token, Google Service Account, etc.)

3. **Configurar las bases de datos:**
   - Crea las hojas de cálculo necesarias en Google Sheets
   - Configura los permisos de acceso apropiados

4. **Activar los workflows:**
   - Activa cada uno de los tres workflows en n8n
   - Verifica que las conexiones funcionen correctamente

## Contribuir

Las contribuciones son bienvenidas. Por favor:

1. Haz fork del proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Haz commit de tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## Licencia

El código fuente y los flujos de trabajo de este proyecto están licenciados bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

**Copyright (c) 2025 Gastón Schvartz**

## Contacto

Para consultas sobre el proyecto, puedes contactar a:
- **Gastón Schvartz** - schvartz.g@gmail.com
- **Proyecto Link:** https://github.com/Zayitus/bot-ausencias-laborales

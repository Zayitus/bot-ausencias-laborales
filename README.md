# Sistema de Gestión de Ausentismo Laboral

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

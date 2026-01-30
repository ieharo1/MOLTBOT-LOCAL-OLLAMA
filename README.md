Moltbot Local + Ollama — Guía Completa de Instalación 100% Gratuita
📋 Tabla de Contenidos

    ¿Qué es Moltbot?

    Requisitos del Sistema

    Instalación Paso a Paso

    Configuración Avanzada

    Solucionar Problemas

    Casos de Uso

    FAQ

🤖 ¿Qué es Moltbot?

Moltbot es un framework de automatización con IA que permite crear asistentes inteligentes para diversas plataformas de mensajería. A diferencia de soluciones en la nube, esta implementación local garantiza:

    ✅ 100% gratuito - Sin límites de uso ni suscripciones

    🔒 Privacidad total - Tus datos nunca salen de tu equipo

    ⚡ Control completo - Personaliza cada aspecto del asistente

    🔄 Integraciones - WhatsApp, Telegram, Discord, Slack, y más

🖥️ Requisitos del Sistema
Hardware Mínimo Recomendado

    RAM: 16 GB (8 GB mínimo para modelos pequeños)

    Almacenamiento: 20 GB de espacio libre

    CPU: 4 núcleos o superior

    GPU: Opcional pero recomendada (NVIDIA con 8GB+ VRAM para mejores resultados)

Software Requerido

    Sistema Operativo: Windows 10/11, macOS 10.15+, o Linux (Ubuntu 20.04+)

    Node.js: Versión 22 o superior

    Python: 3.10 o superior (para algunas funcionalidades)

    Git: Para clonar repositorios

    Ollama: Motor de IA local

🚀 Instalación Paso a Paso
Paso 1: Instalar Ollama

Windows:

    Descarga desde ollama.com/download

    Ejecuta el instalador

    Abre PowerShell como administrador y ejecuta:

powershell

ollama serve

macOS:
bash

brew install ollama
ollama serve

Linux:
bash

curl -fsSL https://ollama.com/install.sh | sh
ollama serve

Paso 2: Descargar Modelos de IA

Elige según tu hardware:
Modelo	Tamaño	RAM Requerida	Uso Recomendado
llama3	8B	8 GB	Equilibrado
mistral	7B	8 GB	Rápido y eficiente
llama3.1:8b	8B	10 GB	Mejor rendimiento
qwen2.5:7b	7B	8 GB	Multilenguaje
phi3	3.8B	4 GB	Hardware limitado
bash

# Ejemplo para descargar Llama 3
ollama pull llama3

# Verifica la descarga
ollama list

# Prueba el modelo
ollama run llama3
> Escribe "Hola" y presiona Enter

Paso 3: Instalar Moltbot

Método 1: Script Automático (Recomendado)
bash

# Windows (PowerShell como administrador)
irm https://get.molt.bot/install.ps1 | iex

# macOS/Linux
curl -fsSL https://get.molt.bot/install.sh | bash

Método 2: Instalación Manual
bash

# Clonar el repositorio
git clone https://github.com/molt/molt.git
cd molt

# Instalar dependencias
npm install

# Construir el proyecto
npm run build

# Inicializar configuración
npm run setup

Paso 4: Configuración Básica

Crea el archivo config/local.yml:
yaml

# Configuración Principal
server:
  port: 3000
  host: "localhost"

# Configuración de IA
ai:
  provider: "ollama"
  model: "llama3"
  temperature: 0.7
  max_tokens: 2048

# Base de datos local
database:
  path: "./data/moltbot.db"
  type: "sqlite"

# Logs
logging:
  level: "info"
  file: "./logs/moltbot.log"

Paso 5: Iniciar Moltbot
bash

# Iniciar en modo desarrollo
npm run dev

# Iniciar en modo producción
npm start

# Iniciar con interfaz web
npm run start:web

Accede a la interfaz web en: http://localhost:3000
🔧 Configuración Avanzada
Integración con Telegram

    Crea un bot en Telegram con @BotFather

    Obtén tu token API

    Edita config/telegram.yml:

yaml

telegram:
  enabled: true
  token: "TU_TOKEN_AQUI"
  admins:
    - "TU_ID_DE_TELEGRAM"
  groups:
    - enabled: true
    - whitelist: ["-123456789"] # ID del grupo

    Reinicia Moltbot:

bash

npm restart

Configuración de WhatsApp

    Instalar dependencias adicionales:

bash

npm install @whiskeysockets/baileys

    Configurar en config/whatsapp.yml:

yaml

whatsapp:
  enabled: true
  session_path: "./sessions/whatsapp"
  qr_timeout: 300000

    Escanear código QR con tu teléfono

Automatización de Tareas

Crea acciones personalizadas en actions/custom.js:
javascript

module.exports = {
  name: "recordatorio",
  description: "Crea recordatorios",
  async execute(context, params) {
    // Tu lógica aquí
    return `Recordatorio creado: ${params.text}`;
  }
};

🐛 Solucionar Problemas Comunes
Problema: Ollama no responde
bash

# Verificar servicio
ollama --version

# Reiniciar servicio
pkill ollama
ollama serve

# Verificar modelos
ollama list

Problema: Moltbot no inicia
bash

# Verificar puerto
sudo lsof -i :3000

# Limpiar caché
npm cache clean --force
rm -rf node_modules
npm install

# Verificar logs
tail -f logs/moltbot.log

Problema: Modelo demasiado lento
bash

# Usar modelo más pequeño
ollama pull mistral

# Ajustar configuración
# En config/local.yml:
ai:
  model: "mistral"
  max_tokens: 1024  # Reducir tokens

Problema: Memoria insuficiente
bash

# Liberar memoria
sudo sysctl -w vm.drop_caches=3

# Usar quantización (menos precisión, menos RAM)
ollama pull llama3:7b-q4_0

🎯 Casos de Uso
1. Asistente Personal de WhatsApp

    Respuestas automáticas inteligentes

    Gestión de contactos

    Envío programado de mensajes

    Traducción en tiempo real

2. Bot de Telegram para Negocios

    Atención al cliente 24/7

    Procesamiento de pedidos

    Recordatorios automáticos

    Integración con calendarios

3. Automatización de Discord

    Moderación automática

    Respuestas a comandos

    Gestión de roles

    Notificaciones personalizadas

4. Herramientas de Productividad
yaml

# Ejemplo de configuración
features:
  calendar: true
  reminders: true
  notes: true
  file_processing: true
  web_search: false  # Mantener local

❓ Preguntas Frecuentes
¿Es realmente 100% gratuito?

✅ Sí. Todo el software es open-source y los modelos de IA se ejecutan localmente sin costos de API.
¿Qué pasa con mis datos?

🔒 Tus datos permanecen en tu equipo. No hay servidores externos ni recopilación de información.
¿Puedo usar otros modelos?

🔄 Sí. Ollama soporta 100+ modelos. Lista completa: ollama list available
¿Necesito conocimientos técnicos?

📚 Básicos. Esta guía cubre todo, pero es útil tener familiaridad con línea de comandos.
¿Funciona sin internet?

🌐 Parcialmente. Los modelos funcionan offline, pero algunas integraciones (WhatsApp, Telegram) requieren conexión.
¿Puedo contribuir al proyecto?

👥 ¡Sí! Moltbot es open-source. Repositorio: github.com/molt/molt
📁 Estructura del Proyecto
text

moltbot-local/
├── config/                    # Configuraciones
│   ├── local.yml             # Config principal
│   ├── telegram.yml          # Config Telegram
│   └── whatsapp.yml          # Config WhatsApp
├── data/                     # Base de datos local
├── logs/                     # Archivos de log
├── models/                   # Modelos personalizados
├── actions/                  # Acciones automatizadas
│   ├── weather.js           # Ej: Clima
│   ├── calculator.js        # Ej: Calculadora
│   └── reminder.js          # Ej: Recordatorios
├── scripts/                  # Scripts de utilidad
│   ├── backup.sh            # Backup de datos
│   ├── update-models.sh     # Actualizar modelos
│   └── cleanup.sh           # Limpieza del sistema
└── docs/                     # Documentación
    ├── api-reference.md     # Referencia API
    └── troubleshooting.md   # Solución problemas

🔄 Mantenimiento
Actualizar Moltbot
bash

cd molt
git pull origin main
npm install
npm run build

Actualizar Modelos
bash

# Actualizar Ollama
ollama --version
# Descargar actualización desde sitio web

# Actualizar modelos
ollama pull llama3:latest

Backup de Datos
bash

# Script automático
./scripts/backup.sh

# Manualmente
cp -r data/ backup-$(date +%Y%m%d)

📚 Recursos Adicionales

    Documentación Oficial: docs.molt.bot

    Comunidad Discord: discord.gg/moltbot

    Repositorio GitHub: github.com/molt/molt

    Modelos Ollama: ollama.com/library

⚠️ Limitaciones y Consideraciones

    Rendimiento: Depende de tu hardware

    Precisión: Modelos locales pueden ser menos precisos que GPT-4

    Memoria: Modelos grandes requieren RAM considerable

    Velocidad: Primera respuesta puede ser lenta mientras carga el modelo

👨💻 Autor

Isaac Esteban Haro Torres
@ieharo1

🚀 Fullstack Developer | DevOps Jr | SCRUM Master
💻 Tech Stack: PHP (Laravel) · Python (Django) · React · Angular · JavaScript
🗄️ Databases: SQL · MongoDB · Firebase
🎓 MSc Big Data

📍 TST SOLUTIONS · Ecuador, Quito
🌐 Conecta conmigo:

    Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

    GitHub: github.com/ieharo1

    LinkedIn: linkedin.com/in/isaac-haro

    WhatsApp: +593 98 805 5517

    Twitter/Instagram: @isaac.haro3 / @isaac.h001

📄 Licencia

Este proyecto está bajo licencia MIT.
Puedes usar, modificar y distribuir libremente.

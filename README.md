# Moltbot Local + Ollama — Guía Completa de Instalación 100% Gratuita

Framework de automatización con IA que permite crear asistentes inteligentes para diversas plataformas de mensajería.

---

## 🤖 ¿Qué es Moltbot?

Moltbot es un framework de automatización con IA que permite crear asistentes inteligentes para diversas plataformas de mensajería. A diferencia de soluciones en la nube, esta implementación local garantiza:

- ✅ **100% gratuito** - Sin límites de uso ni suscripciones
- 🔒 **Privacidad total** - Tus datos nunca salen de tu equipo
- ⚡ **Control completo** - Personaliza cada aspecto del asistente
- 🔄 **Integraciones** - WhatsApp, Telegram, Discord, Slack, y más

---

## 🎯 Para qué sirve

- Asistente personal de WhatsApp
- Bot de Telegram para negocios
- Automatización de Discord
- Herramientas de productividad
- Atención al cliente 24/7
- Procesamiento de pedidos

---

## 🏗 Arquitectura

```
Usuario → Plataforma (Telegram/WhatsApp/Discord) → Moltbot (Local)
                                                  ↓
                                            Ollama (IA Local)
```

---

## 💻 Requisitos del Sistema

### Hardware Mínimo Recomendado

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| RAM | 8 GB | 16 GB |
| Almacenamiento | 20 GB | 50 GB |
| CPU | 4 núcleos | 8 núcleos |
| GPU | Opcional | NVIDIA 8GB+ VRAM |

### Software Requerido

- Windows 10/11, macOS 10.15+, o Linux (Ubuntu 20.04+)
- Node.js 22+
- Python 3.10+
- Git
- Ollama

---

## 🚀 Instalación Paso a Paso

### Paso 1: Instalar Ollama

**Windows:**
```powershell
# Descargar desde ollama.com
ollama serve
```

**Linux:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama serve
```

### Paso 2: Descargar Modelos de IA

| Modelo | Tamaño | RAM | Uso |
|--------|--------|-----|-----|
| llama3 | 8B | 8 GB | Equilibrado |
| mistral | 7B | 8 GB | Rápido |
| llama3.1:8b | 8B | 10 GB | Mejor rendimiento |
| qwen2.5:7b | 7B | 8 GB | Multilenguaje |
| phi3 | 3.8B | 4 GB | Hardware limitado |

```bash
ollama pull llama3
ollama list
```

### Paso 3: Instalar Moltbot

```bash
# Windows (PowerShell)
irm https://get.molt.bot/install.ps1 | iex

# macOS/Linux
curl -fsSL https://get.molt.bot/install.sh | bash
```

### Paso 4: Configuración

```yaml
# config/local.yml
server:
  port: 3000

ai:
  provider: "ollama"
  model: "llama3"
  temperature: 0.7

database:
  path: "./data/moltbot.db"
```

---

## 📁 Estructura del Proyecto

```
moltbot-local/
├── config/              # Configuraciones
│   ├── local.yml
│   ├── telegram.yml
│   └── whatsapp.yml
├── data/               # Base de datos
├── logs/               # Logs
├── actions/            # Acciones personalizadas
└── scripts/            # Scripts de utilidad
```

---

## 🔧 Configuración Avanzada

### Telegram
- Crear bot con @BotFather
- Obtener token API
- Configurar en `config/telegram.yml`

### WhatsApp
```bash
npm install @whiskeysockets/baileys
```

---

## 🐛 Solucionar Problemas

**Ollama no responde:**
```bash
ollama --version
pkill ollama
ollama serve
```

**Moltbot no inicia:**
```bash
npm cache clean --force
rm -rf node_modules
npm install
```

---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

## 📄 Licencia

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.


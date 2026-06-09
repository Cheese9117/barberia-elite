# 💈 Barbería Élite — WhatsApp Chatbot

> Chatbot de WhatsApp con IA para gestión automatizada de citas y atención al cliente — construido con n8n + Twilio + Claude AI.

[![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)](https://n8n.io)
[![Twilio](https://img.shields.io/badge/Twilio-F22F46?style=flat-square&logo=twilio&logoColor=white)](https://twilio.com)
[![Claude AI](https://img.shields.io/badge/Claude_AI-D97757?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

---

## ¿Qué hace este bot?

Un asistente virtual de WhatsApp que atiende a los clientes de **Barbería Élite** las 24 horas, sin que el dueño tenga que responder manualmente. Detecta la intención de cada mensaje y responde con la información correcta de forma instantánea.

### Flujo de conversación

```
Cliente escribe → Webhook Twilio → Detección de intención → Respuesta automática
                                         ↓
                              Si es una cita → Guarda en Google Sheets
                                         ↓
                              Confirmación enviada al cliente por WhatsApp
```

### Intenciones que maneja

| Mensaje del cliente | Respuesta del bot |
|---|---|
| "hola", "buenas", "hey" | Menú de bienvenida con opciones |
| "servicios", "precio", "cuánto" | Lista de servicios con precios en COP |
| "agendar", "cita", "reservar" | Solicita datos y guía el proceso de reserva |
| "horarios", "cuándo atienden" | Horarios actualizados del local |
| "ubicación", "dónde quedan" | Dirección + indicaciones para llegar |
| Confirmación de datos | Guarda la cita y envía resumen al cliente |
| "cancelar" | Confirma la cancelación con opción de reagendar |
| Mensaje no reconocido | Menú de ayuda con opciones disponibles |

---

## 🛠️ Stack técnico

| Herramienta | Rol |
|---|---|
| **n8n** | Orquestación del flujo completo (workflow visual) |
| **Twilio** | Recibe y envía mensajes de WhatsApp vía webhook |
| **Claude AI** | Procesamiento de lenguaje natural (intenciones complejas) |
| **Google Sheets** | Base de datos de citas agendadas |
| **JavaScript** | Lógica de detección de intenciones y construcción de respuestas |

---

## 📋 Servicios del negocio

```
✂️  Corte de cabello       $25.000 COP
🧔  Arreglo de barba       $15.000 COP
🔥  Combo (Corte + Barba)  $35.000 COP
🎨  Tinte / Color          $45.000 COP
```

---

## ⚙️ Cómo funciona el flujo en n8n

1. **Twilio Webhook** — recibe el mensaje entrante de WhatsApp
2. **Detect Intent** — nodo de código JS que clasifica la intención del mensaje
3. **Router** — bifurca el flujo según la intención detectada
4. **Is Appointment Confirmation?** — si el cliente está confirmando una cita, activa el guardado
5. **Save to Google Sheets** — registra nombre, fecha, hora y servicio
6. **Send WhatsApp Reply** — envía la respuesta vía API de Twilio

---

## 🚀 Instalación y configuración

### Requisitos

- Cuenta de [n8n](https://n8n.io) (self-hosted o cloud)
- Cuenta de [Twilio](https://twilio.com) con número habilitado para WhatsApp
- API Key de [Claude AI (Anthropic)](https://anthropic.com)
- Google Sheets API habilitada

### Variables de entorno necesarias en n8n

```env
TWILIO_ACCOUNT_SID=ACxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
TWILIO_AUTH_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxx
```

### Importar el workflow

1. Descarga el archivo `barberia.JSON` de este repositorio
2. En n8n, ve a **Workflows → Import from file**
3. Selecciona `barberia.JSON`
4. Configura las credenciales de Twilio y Google Sheets en los nodos correspondientes
5. Activa el workflow y copia la URL del webhook de Twilio
6. En tu consola de Twilio, configura esa URL como webhook de WhatsApp

---

## 📁 Estructura del repositorio

```
/
├── barberia.JSON        # Workflow completo de n8n (importable)
├── barberia2.JSON       # Versión alternativa / respaldo del workflow
└── README.md
```

---

## 💡 Casos de uso similares

Este mismo sistema puede adaptarse para:
- Restaurantes (pedidos y reservas)
- Salones de belleza (citas y catálogo de servicios)
- Clínicas y consultorios (turnos médicos)
- Tiendas locales (consulta de inventario y precios)

---

## 👨‍💻 Autor

**Juan Sebastian Henao** — AI-Powered Web Developer · Medellín, Colombia 🇨🇴

[![Email](https://img.shields.io/badge/juansebastian9117%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:juansebastian9117@gmail.com)
[![Instagram](https://img.shields.io/badge/@sebasxhax__-E4405F?style=flat-square&logo=instagram&logoColor=white)](https://instagram.com/sebasxhax_)

> ¿Querés un chatbot así para tu negocio? Escríbeme.

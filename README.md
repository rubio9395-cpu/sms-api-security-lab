# 📩 SMS API Security Lab

Proyecto educativo que demuestra cómo enviar mensajes SMS utilizando la API de Twilio con Python en Kali Linux.

---

# 🎯 Objetivo

Este proyecto tiene como finalidad:

- Aprender a trabajar con APIs REST.
- Configurar entornos virtuales en Kali Linux.
- Enviar SMS de forma controlada y autorizada.
- Comprender el flujo técnico de una integración con API externa.

---

# 🧰 Requisitos

- Kali Linux
- Python 3
- Cuenta activa en Twilio
- Número telefónico adquirido en Twilio
- Account SID y Auth Token

---

# 1️⃣ Instalar soporte para entornos virtuales

Si no tienes `venv` instalado:

```bash
sudo apt update
sudo apt install python3-venv -y
```

---

# 2️⃣ Crear el entorno virtual

```bash
python3 -m venv sms_env
```

Esto creará una carpeta llamada `sms_env`.

---

# 3️⃣ Activar el entorno virtual

```bash
source sms_env/bin/activate
```

Si se activó correctamente, verás algo similar a:

```
(sms_env) kali@kali:~$
```

---

# 4️⃣ Instalar dependencia necesaria

```bash
pip install twilio
```

Opcional: guardar dependencias

```bash
pip freeze > requirements.txt
```

---

# 5️⃣ Crear el script para enviar SMS

Crear archivo:

```bash
nano sms.py
```

Agregar el siguiente código:

```python
from twilio.rest import Client

account_sid = "TU_ACCOUNT_SID"
auth_token = "TU_AUTH_TOKEN"

client = Client(account_sid, auth_token)

message = client.messages.create(
    body="Mensaje de prueba autorizado.",
    from_="+1XXXXXXXXXX",   # Número de Twilio
    to="+521XXXXXXXXXX"     # Número destino en formato internacional
)

print("Mensaje enviado correctamente.")
print("Message SID:", message.sid)
```

Guardar y salir.

---

# 6️⃣ Ejecutar el script

```bash
python sms.py
```

Si todo funciona correctamente, verás algo como:

```
Mensaje enviado correctamente.
Message SID: SMxxxxxxxxxxxxxxxx
```

---

# 🌐 Flujo Técnico del Envío

```
Script en Kali Linux
        ↓
API REST de Twilio
        ↓
Infraestructura de Twilio
        ↓
Red Celular
        ↓
Teléfono destino
```

El envío ocurre en esta línea del código:

```python
client.messages.create(...)
```

Este método realiza una petición HTTP POST hacia la API de Twilio.

---

# 🔐 Buenas Prácticas

- No subir credenciales reales a GitHub.
- No compartir tu Account SID ni Auth Token.
- Usar variables de entorno en proyectos reales.
- No enviar mensajes sin autorización explícita.

---

---

# ⚠️ Aviso de Uso Responsable y Deslinde de Responsabilidad

## 🔐 Uso Autorizado Únicamente

Este proyecto ha sido desarrollado con fines estrictamente educativos y de aprendizaje en el uso de APIs y automatización.

Al utilizar este software, usted acepta que:

- Solo enviará mensajes SMS a números propios o a números para los cuales tenga autorización expresa y verificable.
- Cumplirá con todas las leyes y regulaciones locales, nacionales e internacionales aplicables.
- Entiende que el envío de mensajes no autorizados puede constituir una violación a leyes de telecomunicaciones, privacidad y protección de datos.

---

## 🚫 Uso Prohibido

Este proyecto NO debe utilizarse para:

- Envío de spam
- Phishing o smishing
- Acoso o hostigamiento
- Ingeniería social sin autorización formal
- Actividades ilegales o maliciosas de cualquier tipo

---

## 📜 Limitación de Responsabilidad

El autor no asume ninguna responsabilidad por el uso indebido de este software.

Cualquier consecuencia legal, daño, pérdida o perjuicio derivado del uso de este proyecto será responsabilidad exclusiva del usuario.

---

## 🧠 Recordatorio Ético

El conocimiento en ciberseguridad y automatización debe utilizarse para:

- Aprender de manera responsable
- Mejorar la seguridad de sistemas
- Realizar pruebas autorizadas
- Proteger a personas y organizaciones

Actúe siempre con ética y profesionalismo.

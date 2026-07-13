# Chuli Facturador — Demo pública

Versión demostrativa de una aplicación web desarrollada en Python y FastAPI para procesar lotes de ventas en formato CSV y emitir comprobantes electrónicos mediante los servicios de ARCA.

> Estado actual: MVP funcional en ambiente de homologación. Este repositorio no contiene credenciales, certificados ni información fiscal real.

## Funcionalidades

- Dashboard administrativo con FastAPI.
- Procesamiento de lotes CSV.
- Emisión de Factura C mediante ARCA.
- Registro local de comprobantes en SQLite.
- Control de duplicados por número de orden.
- Reintentos automáticos ante errores temporales.
- Registro de eventos y errores.
- Gestión y reproceso de facturaciones pendientes.
- Consulta de comprobantes emitidos.
- Configuración mediante variables de entorno.

## Tecnologías

- Python
- FastAPI
- SQLite
- Pandas
- HTML
- CSS
- AFIP SDK
- Git y GitHub

## Requisitos

- Windows 11
- Python 3.11 o superior
- Git
- Certificado y clave privada de ARCA
- Token de acceso para AFIP SDK

## Instalación

Clonar el repositorio:

```bash
git clone https://github.com/laschescottas-cyber/chuli-facturador-demo.git
```

Ingresar en la carpeta:

```bash
cd chuli-facturador-demo
```

Crear un entorno virtual:

```bash
python -m venv venv
```

Activarlo en Windows:

```bash
venv\Scripts\activate
```

Instalar las dependencias:

```bash
pip install -r requirements.txt
```

## Configuración

Copiar el archivo de ejemplo:

```powershell
Copy-Item .env.example .env
```

Completar `.env` con los datos reales de la instalación.

También deben agregarse localmente:

```text
certificado.crt
privada.key
```

Estos archivos no deben subirse a GitHub.

## Ejecución

```bash
uvicorn app.main:app --reload
```

Abrir el dashboard:

```text
http://127.0.0.1:8000
```

## Estructura principal

```text
Chuli-Facturador/
│
├── app/
│   ├── main.py
│   ├── database.py
│   └── logger.py
│
├── static/
│   └── css/
│       └── style.css
│
├── procesar_lote.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
└── MANUAL.md
```

Las carpetas `data/`, `logs/`, `ventas/` y los certificados existen solamente en el entorno local.

## Seguridad

Nunca subir al repositorio:

- `.env`
- Certificados o claves privadas
- Bases SQLite
- Logs
- CSV de ventas
- Tokens
- CUIT reales escritos directamente en el código

Antes de cada commit:

```bash
git diff --cached --name-only
```

## Flujo de trabajo

```bash
git checkout main
git pull origin main
git checkout -b feature/nombre-del-cambio
```

Después de trabajar:

```bash
git add .
git commit -m "Describe claramente el cambio"
git push origin feature/nombre-del-cambio
```

Luego debe crearse un Pull Request en GitHub.

## Documentación

Consultá el procedimiento completo en:

[MANUAL.md](MANUAL.md)

## Alcance de esta demo

Esta copia pública está pensada para mostrar la arquitectura, el flujo de procesamiento y las decisiones técnicas del proyecto. Para utilizarla es necesario aportar credenciales propias y válidas en un archivo `.env` local, además de los certificados correspondientes. Estos archivos nunca deben versionarse.

## Autora

Natalia Chescotta — estudiante de Ciencia de Datos e Inteligencia Artificial y desarrolladora en formación.

GitHub: [laschescottas-cyber](https://github.com/laschescottas-cyber)

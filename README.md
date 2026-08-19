# Autenticacion con Supabase y Streamlit

Ejemplo practico para agregar registro, inicio y cierre de sesion a una aplicacion de Python construida con [Streamlit](https://streamlit.io/) y [Supabase](https://supabase.com/). https://temp-mail.org/en/

## Funcionalidades

- Registro de usuarios mediante correo electronico y contrasena.
- Inicio de sesion con Supabase Auth.
- Estado de sesion conservado durante los reruns de Streamlit.
- Pagina de bienvenida para usuarios autenticados.
- Cierre de sesion.

## Requisitos

- Python 3.12 o superior.
- Una cuenta y un proyecto creado en Supabase.
- [uv](https://docs.astral.sh/uv/) para instalar las dependencias y ejecutar el proyecto.

## Configurar Supabase

1. Crea un proyecto en el [panel de Supabase](https://supabase.com/dashboard).
2. Abre **Authentication > Providers > Email** y habilita el proveedor de correo electronico.
3. Ve a **Project Settings > API** y copia:
   - **Project URL**.
   - La clave publica **Publishable key** o la clave heredada `anon`.

No uses la clave `service_role` en esta aplicacion. Es una credencial privilegiada y no debe exponerse en el cliente.

## Instalacion

Desde la carpeta del ejemplo:

```powershell
cd codes
uv sync
```

Crea el archivo `codes/.env` con las credenciales de tu proyecto:

```dotenv
SUPABASE_URL=https://tu-proyecto.supabase.co
SUPABASE_KEY=tu-clave-publica-de-supabase
```

El archivo `.env` contiene credenciales y no debe subirse al repositorio. Si vas a compartir el proyecto, agrega `.env` al archivo `.gitignore`.

## Ejecutar la aplicacion

```powershell
cd codes
uv run streamlit run main.py
```

Streamlit mostrara una URL local, normalmente `http://localhost:8501`.

## Como probarla

1. Selecciona **Sign Up**.
2. Introduce un correo y una contrasena y pulsa **Register**.
3. Si la confirmacion de correo esta habilitada en Supabase, confirma el correo recibido.
4. Selecciona **Login** e inicia sesion.
5. Pulsa **Logout** para cerrar la sesion.

## Estructura del proyecto

```text
.
|-- README.md
|-- pyvenv.cfg
`-- codes/
	|-- main.py
	|-- pyproject.toml
	`-- README.md
```

- `codes/main.py`: interfaz de Streamlit e integracion con Supabase Auth.
- `codes/pyproject.toml`: dependencias y configuracion del proyecto Python.
- `codes/.env`: credenciales locales; crealo manualmente y no lo compartas.

## Solucion de problemas

### No se encuentra `SUPABASE_URL` o `SUPABASE_KEY`

Comprueba que el archivo se llame exactamente `.env`, que este dentro de `codes/` y que las variables no tengan espacios alrededor del signo `=`.

### El registro no funciona

Revisa que el proveedor **Email** este habilitado en Supabase. Si esta activa la confirmacion de correo, el usuario debe confirmar su direccion antes de iniciar sesion.

### La aplicacion no inicia

Ejecuta los comandos desde `codes/` y vuelve a sincronizar el entorno:

```powershell
cd codes
uv sync
uv run streamlit run main.py
```

## Licencia

Este proyecto se proporciona como material educativo.

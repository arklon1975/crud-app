DF Processing API Documentation
Una API RESTful construida con FastAPI para procesar y manipular archivos PDF.
Descripción
Este proyecto proporciona una API completa para la manipulación de documentos PDF. La aplicación permite realizar operaciones avanzadas como convertir formatos, combinar documentos, extraer texto e información, y más funcionalidades a través de endpoints HTTP bien documentados.
Características

Procesamiento avanzado de archivos PDF
API RESTful completa con FastAPI
Soporte para CORS para desarrollo frontend
Sistema de manejo de errores HTTP personalizado
Configuración modular basada en variables de entorno
Base de datos integrada para almacenar información de documentos
Arquitectura modular con routers y componentes separados
Documentación interactiva con Swagger UI y ReDoc

Requisitos

Python 3.7+
FastAPI
Uvicorn (para servidor ASGI)
SQLAlchemy (para ORM)
PyPDF2/PDFMiner/PyMuPDF (para manipulación de PDFs)
Python-multipart (para manejo de archivos)
Dependencias adicionales listadas en requirements.txt

Instalación

Clonar el repositorio:
bashgit clone https://github.com/tu-usuario/pdf-processing-api.git
cd pdf-processing-api

Crear un entorno virtual:
bashpython -m venv venv

Activar el entorno virtual:

Windows:

bashvenv\Scripts\activate

macOS/Linux:

bashsource venv/bin/activate

Instalar dependencias:
bashpip install -r requirements.txt

Configurar variables de entorno (opcional):

Crear archivo .env basado en .env.example



Uso
Iniciar el servidor
bashuvicorn main:app --reload
El servidor estará disponible en http://localhost:8000
Endpoints disponibles

GET /: Endpoint raíz que devuelve un mensaje de bienvenida
GET /items/{item_id}: Endpoint de ejemplo que devuelve un ítem por ID

Endpoints de PDF

POST /pdfs/upload: Subir un nuevo archivo PDF
GET /pdfs/{pdf_id}: Obtener información de un PDF específico
GET /pdfs/: Listar todos los PDFs disponibles
PUT /pdfs/{pdf_id}: Actualizar información de un PDF
DELETE /pdfs/{pdf_id}: Eliminar un PDF
POST /pdfs/merge: Combinar múltiples PDFs
POST /pdfs/extract-text/{pdf_id}: Extraer texto de un PDF
POST /pdfs/convert: Convertir PDF a otros formatos

Para detalles completos sobre parámetros, cuerpos de solicitud y respuestas, consulta la documentación interactiva de la API.
Documentación de la API
Una vez iniciado el servidor, puedes acceder a la documentación interactiva:

Swagger UI: http://localhost:8000/docs
ReDoc: http://localhost:8000/redoc

Estructura del proyecto
pdf-processing-api/
├── main.py              # Punto de entrada de la aplicación
├── config.py            # Configuración de la aplicación
├── crud.py              # Operaciones CRUD para la base de datos
├── database.py          # Configuración de la base de datos
├── models.py            # Modelos de datos/SQLAlchemy
├── schemas.py           # Esquemas Pydantic/validación
├── requirements.txt     # Dependencias del proyecto
├── README.md            # Este archivo
├── routers/
│   └── pdfs.py          # Router para operaciones con PDFs
└── static/
    ├── components/      # Componentes frontend (si aplica)
    ├── images/          # Imágenes estáticas
    └── styles/          # Archivos CSS
Configuración
La configuración se gestiona a través del archivo config.py y utiliza la clase Settings. Las variables de configuración pueden ser sobrescritas mediante variables de entorno.
Desarrollo
Cómo añadir nuevos endpoints

Crear un nuevo archivo en la carpeta routers/
Definir un nuevo router con APIRouter()
Implementar los endpoints necesarios
Incluir el router en main.py usando app.include_router()

Estructura de código

main.py: Punto de entrada de la aplicación FastAPI
config.py: Configuración usando clases Settings y variables de entorno
database.py: Configuración de SQLAlchemy y sesiones de base de datos
models.py: Modelos ORM para SQLAlchemy
schemas.py: Esquemas Pydantic para validación de datos
crud.py: Funciones CRUD genéricas para operaciones de base de datos
routers/: Módulos separados para diferentes grupos de endpoints

Base de datos
La aplicación utiliza SQLAlchemy como ORM. Las migraciones pueden gestionarse con Alembic. Consulta la documentación completa para detalles sobre el esquema de base de datos y las relaciones.
Contribuciones
Las contribuciones son bienvenidas. Por favor, sigue estos pasos:

Haz fork del repositorio
Crea una rama para tu función (git checkout -b feature/amazing-feature)
Haz commit de tus cambios (git commit -m 'Add some amazing feature')
Haz push a la rama (git push origin feature/amazing-feature)
Abre un Pull Request

Problemas conocidos
Consulta la sección de "Issues" en el repositorio para ver problemas conocidos y limitaciones actuales.
Próximas características

Soporte para firmas digitales
Extracción avanzada de texto con OCR
Interfaz de usuario para gestión de PDFs
Integración con servicios de almacenamiento en la nube

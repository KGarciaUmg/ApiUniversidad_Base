# Universidad Grades API

Una API RESTful robusta construida con **ASP.NET Core 8.0** para gestionar calificaciones universitarias, estudiantes, profesores, cursos e inscripciones.

## 📋 Descripción

La **Universidad Grades API** proporciona un sistema completo para administrar académicamente una institución educativa. Permite gestionar:
- **Estudiantes**: Registro y administración de datos de estudiantes
- **Profesores**: Gestión de profesores por departamento
- **Cursos**: Administración de cursos académicos con asignación de profesores
- **Inscripciones**: Control de inscripciones de estudiantes en cursos
- **Calificaciones**: Registro y cálculo de promedios de calificaciones

## 🚀 Tecnologías

- **Framework**: ASP.NET Core 8.0
- **Lenguaje**: C# 12
- **ORM**: Entity Framework Core 8.0.25
- **Base de Datos**: In-Memory Database
- **Documentación API**: Swagger/OpenAPI (Swashbuckle.AspNetCore 6.6.2)
- **Testing**: xUnit / NUnit (infraestructura lista para pruebas)

## 📁 Estructura del Proyecto

```
ApiUniversidad_Base/
├── src/
│   ├── Controllers/              # Controladores API
│   │   ├── StudentsController.cs
│   │   ├── ProfessorsController.cs
│   │   ├── CoursesController.cs
│   │   ├── EnrollmentsController.cs
│   │   └── GradesController.cs
│   ├── Models/                   # Modelos de dominio
│   │   ├── Student.cs
│   │   ├── Professor.cs
│   │   ├── Course.cs
│   │   ├── Enrollment.cs
│   │   └── Grade.cs
│   ├── DTOs/                     # Data Transfer Objects
│   │   ├── StudentDto.cs
│   │   ├── ProfessorDto.cs
│   │   ├── CourseDto.cs
│   │   ├── EnrollmentDto.cs
│   │   └── GradeDto.cs
│   ├── Data/
│   │   └── AppDbContext.cs       # DbContext de Entity Framework
│   ├── Program.cs                # Punto de entrada y configuración
│   ├── appsettings.json          # Configuración
│   └── UniversityGrades.csproj   # Archivo de proyecto
├── Tests/                        # Pruebas unitarias
│   ├── StudentsControllerTests.cs
│   ├── ProfessorsControllerTests.cs
│   ├── CoursesControllerTests.cs
│   ├── EnrollmentsControllerTests.cs
│   ├── GradesControllerTests.cs
│   ├── TestDbHelper.cs
│   └── UniversityGrades.Tests.csproj
├── ApiUniversidad.sln            # Solución Visual Studio
└── README.md                      # Documentación
```

## 🏃 Instalación y Ejecución

### Requisitos Previos
- .NET 8.0 SDK o superior
- Visual Studio 2022 / Visual Studio Code / JetBrains Rider

### Pasos para Ejecutar

1. **Clonar el repositorio**
   ```bash
   git clone <url-del-repositorio>
   cd ApiUniversidad_Base
   ```

2. **Restaurar dependencias**
   ```bash
   dotnet restore
   ```

3. **Ejecutar la aplicación**
   ```bash
   cd src
   dotnet run
   ```

4. **Ejecutar las pruebas (opcional)**
   ```bash
   # Desde la raíz del proyecto
   dotnet test
   
   # O específicamente las pruebas
   cd Tests
   dotnet test
   ```

5. **Acceder a Swagger UI**
   - La API estará disponible en: `https://localhost:5001` (o el puerto configurado)
   - Documentación interactiva: `https://localhost:5001/swagger`

## 📚 Endpoints de la API

### Estudiantes (`/api/students`)
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/students` | Obtener todos los estudiantes |
| GET | `/api/students/{id}` | Obtener un estudiante por ID |
| GET | `/api/students/{id}/grades` | Obtener calificaciones de un estudiante |
| GET | `/api/students/{id}/average` | Obtener promedio de un estudiante |
| POST | `/api/students` | Crear un nuevo estudiante |
| PUT | `/api/students/{id}` | Actualizar un estudiante |
| DELETE | `/api/students/{id}` | Eliminar un estudiante |

### Profesores (`/api/professors`)
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/professors` | Obtener todos los profesores |
| GET | `/api/professors/{id}` | Obtener un profesor por ID |
| POST | `/api/professors` | Crear un nuevo profesor |
| PUT | `/api/professors/{id}` | Actualizar un profesor |
| DELETE | `/api/professors/{id}` | Eliminar un profesor |

### Cursos (`/api/courses`)
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/courses` | Obtener todos los cursos |
| GET | `/api/courses/{id}` | Obtener un curso por ID |
| POST | `/api/courses` | Crear un nuevo curso |
| PUT | `/api/courses/{id}` | Actualizar un curso |
| DELETE | `/api/courses/{id}` | Eliminar un curso |

### Inscripciones (`/api/enrollments`)
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/enrollments` | Obtener todas las inscripciones |
| GET | `/api/enrollments/{id}` | Obtener una inscripción por ID |
| POST | `/api/enrollments` | Crear una nueva inscripción |
| PUT | `/api/enrollments/{id}` | Actualizar una inscripción |
| DELETE | `/api/enrollments/{id}` | Eliminar una inscripción |

### Calificaciones (`/api/grades`)
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/grades` | Obtener todas las calificaciones |
| GET | `/api/grades/{id}` | Obtener una calificación por ID |
| POST | `/api/grades` | Crear una nueva calificación |
| PUT | `/api/grades/{id}` | Actualizar una calificación |
| DELETE | `/api/grades/{id}` | Eliminar una calificación |

## 📊 Modelos de Datos

### Student
```csharp
{
  "id": 1,
  "firstName": "Juan",
  "lastName": "Pérez",
  "email": "jperez@est.universidad.edu",
  "studentCode": "EST-001"
}
```

### Professor
```csharp
{
  "id": 1,
  "firstName": "Carlos",
  "lastName": "García",
  "email": "cgarcia@universidad.edu",
  "department": "Ingeniería"
}
```

### Course
```csharp
{
  "id": 1,
  "name": "Programación I",
  "code": "PRG-101",
  "credits": 4,
  "professorId": 1
}
```

### Enrollment
```csharp
{
  "id": 1,
  "studentId": 1,
  "courseId": 1,
  "enrollmentDate": "2026-01-15",
  "semester": "2026-1"
}
```

### Grade
```csharp
{
  "id": 1,
  "enrollmentId": 1,
  "score": 85,
  "description": "Parcial 1",
  "gradeDate": "2026-02-15"
}
```

## 🧪 Testing

El proyecto incluye pruebas unitarias en una carpeta separada (`/Tests`) para validar la funcionalidad de cada controlador:

```bash
# Ejecutar todas las pruebas desde la raíz del proyecto
dotnet test

# Ejecutar pruebas del proyecto específico
cd Tests
dotnet test

# Ejecutar pruebas de un controlador específico
dotnet test --filter "StudentsControllerTests"

# Ver cobertura de código
dotnet test /p:CollectCoverage=true
```

### Clases de Prueba
Ubicadas en `/Tests`:
- `StudentsControllerTests.cs` - Pruebas para operaciones de estudiantes
- `ProfessorsControllerTests.cs` - Pruebas para operaciones de profesores
- `CoursesControllerTests.cs` - Pruebas para operaciones de cursos
- `EnrollmentsControllerTests.cs` - Pruebas para operaciones de inscripciones
- `GradesControllerTests.cs` - Pruebas para operaciones de calificaciones
- `TestDbHelper.cs` - Utilidades compartidas para pruebas
- `UniversityGrades.Tests.csproj` - Archivo de proyecto de pruebas

## 🔍 Características Principales

✅ **CRUD Completo**: Operaciones Create, Read, Update, Delete en todas las entidades

✅ **Relaciones Complejas**: Gestión de relaciones entre Estudiantes, Cursos, Profesores y Calificaciones

✅ **Cálculo de Promedios**: Endpoint dedicado para calcular promedios de calificaciones por estudiante y curso

✅ **Validación**: Validaciones de datos a nivel de modelo usando DataAnnotations

✅ **Documentación Interactiva**: Swagger UI para explorar y probar endpoints

✅ **Base de Datos en Memoria**: Datos de semilla para pruebas rápidas sin configuración externa

✅ **Arquitectura Limpia**: Separación clara entre Controladores, Modelos, DTOs y Acceso a Datos

## 🌱 Datos de Semilla

La base de datos se inicializa automáticamente con datos de ejemplo:

**Profesores:**
- Carlos García (Ingeniería)
- María López (Ciencias)

**Estudiantes:**
- Juan Pérez (EST-001)
- Ana Martínez (EST-002)

**Cursos:**
- Programación I (4 créditos)
- Cálculo I (5 créditos)
- Base de Datos (4 créditos)

**Inscripciones y Calificaciones:** 
Datos asociados para los estudiantes y cursos anteriores

## 📝 Ejemplos de Uso

### Obtener todos los estudiantes
```bash
curl -X GET "https://localhost:5001/api/students" \
  -H "accept: application/json"
```

### Crear un nuevo estudiante
```bash
curl -X POST "https://localhost:5001/api/students" \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Pedro",
    "lastName": "González",
    "email": "pgonzalez@est.universidad.edu",
    "studentCode": "EST-003"
  }'
```

### Obtener promedio de calificaciones de un estudiante
```bash
curl -X GET "https://localhost:5001/api/students/1/average" \
  -H "accept: application/json"
```

## 🔧 Configuración

El archivo `appsettings.json` contiene la configuración de la aplicación:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(local);Database=UniversityGradesDb;Trusted_Connection=true;"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

## 🚀 Próximas Mejoras

- [ ] Autenticación y Autorización (JWT)
- [ ] Migración a Base de Datos SQL Server/PostgreSQL
- [ ] Paginación en endpoints GET
- [ ] Filtrado y búsqueda avanzada
- [ ] Rate limiting
- [ ] CORS configurado
- [ ] Logging estructurado
- [ ] CI/CD pipeline

## 📄 Licencia

Este proyecto está disponible bajo la licencia MIT. Ver archivo `LICENSE` para más detalles.

## 👥 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Hacer fork del repositorio
2. Crear una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir un Pull Request

## 📧 Contacto

Para preguntas o sugerencias, contacta a través de:
- Email: asturiasmichael1@gmail.com
- Issues: Crear un issue en el repositorio

---

**Última actualización:** 19 de Abril de 2026
**Versión:** 1.0.0

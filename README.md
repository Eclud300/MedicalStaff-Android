# Medical Staff – Aplicación Móvil Android

Aplicación móvil nativa para Android del ecosistema **Medical Staff**, diseñada para que los pacientes en Ciudad Obregón puedan iniciar sesión de forma segura, explorar consultorios médicos y dentales, agendar citas y consultar el estatus de sus citas programadas.

**Universidad Tecnológica del Sur de Sonora (UTS)**  
**Asignatura:** Desarrollo Móvil Integral  
**Docente:** Miguel Alejandro López Humo

---

## Equipo de Desarrollo
- **Omar Alan Encinas Amarillas** – Tech Lead / Arquitectura Móvil Android
- **Ricardo Eclud Rodríguez Suárez** – Backend / Base de Datos / Seguridad
- **Oswaldo Vega** – Fullstack Operativo
- **Romario Ramos** – Frontend UI / CRUDs

---

## Tecnologías y Versiones
- **IDE:** Android Studio *(colocar versión exacta de Help > About)*
- **Lenguaje:** Kotlin *(colocar versión de `libs.versions.toml`)*
- **UI Framework:** Jetpack Compose + Material Design 3
- **Android SDK:** Compile SDK `37` | Target SDK `37` *(verificar en `build.gradle.kts`)* | Min SDK `26` *(verificar en `build.gradle.kts`)*
- **JDK:** Java 17 (JetBrains Runtime / OpenJDK)
- **Sistema de compilación:** Gradle *(colocar versión de `gradle-wrapper.properties`)*
- **Arquitectura:** MVVM (Model-View-ViewModel)
- **Backend / API:** ASP.NET Core Web API (.NET) + PostgreSQL (Supabase)

---

## Estructura del Proyecto (MVVM)

```text
MedicalStaffAndroid/
├── app/
│   ├── src/main/
│   │   ├── java/com/example/medicalstaffandroid/
│   │   │   ├── data/
│   │   │   │   ├── local/        # Persistencia local (Room / EncryptedSharedPreferences)
│   │   │   │   ├── model/        # DTOs y modelos de dominio
│   │   │   │   ├── remote/       # Cliente HTTP (Retrofit / OkHttp / AuthInterceptor)
│   │   │   │   └── repository/   # Repositorios (fuente única de verdad)
│   │   │   ├── ui/               # Pantallas Jetpack Compose y tema Material 3
│   │   │   ├── viewmodel/        # ViewModels y manejo de estado reactivo
│   │   │   └── MainActivity.kt   # Punto de entrada de la aplicación
│   │   ├── res/                  # Recursos gráficos y de configuración
│   │   └── AndroidManifest.xml   # Permisos (INTERNET) y configuración de la app
│   └── build.gradle.kts          # Dependencias y configuración de SDK del módulo app
├── gradle/                       # Gradle Wrapper y catálogo de versiones
├── .gitignore                    # Exclusión de compilados y archivos locales
├── build.gradle.kts              # Configuración raíz de plugins
└── README.md                     # Documentación de entorno y ejecución
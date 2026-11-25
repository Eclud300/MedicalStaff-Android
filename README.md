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
- **IDE:** Android Studio Quail 1 (`2026.1.1 Patch 2`)
- **Sistema Operativo de referencia:** Windows 11 (64 bits)
- **Lenguaje:** Kotlin `2.2.10` (`org.jetbrains.kotlin.plugin.compose`)
- **Android SDK:** Compile SDK `37` (`minorApiLevel = 1`) | Target SDK `36` | Min SDK `24` (Android 7.0)
- **Application ID / Versión:** `com.example.medicalstaffandroid` (`v1.0`, `versionCode 1`)
- **Java / Runtime:** Source & Target `Java 11` | Runtime JDK `OpenJDK 21.0.10` (JetBrains Runtime)
- **Sistema de Compilación:** Android Gradle Plugin (AGP) `9.2.1` + Version Catalog (`libs.versions.toml`)
- **UI Framework:** Jetpack Compose (`BOM 2026.02.01`), Material Design 3, Activity Compose `1.13.0`
- **Núcleo AndroidX:** Core KTX `1.19.0` | Lifecycle Runtime KTX `2.6.1`
- **Pruebas:** JUnit `4.13.2`, AndroidX JUnit `1.3.0`, Espresso `3.7.0`, Compose UI Test
- **Control de Versiones:** Git `2.53.0.windows.2` + GitHub (GitHub Flow)
- **Arquitectura:** MVVM (Model-View-ViewModel)
- **Backend / API:** ASP.NET Core Web API (.NET 8 / C#) + PostgreSQL 15 (Supabase)

---

## Prerrequisitos del Entorno
1. **Android Studio Quail 1 (2026.1.1 Patch 2 o superior)** con **Embedded JDK 21 (OpenJDK 21.0.10)** configurado en Gradle.
2. **Android SDK Platform 37 (`minorApiLevel 1`)** y **Android SDK Build-Tools** instalados desde `Tools > SDK Manager`.
3. **Dispositivo de pruebas:** emulador **AVD** (ej. Pixel 9 con API 37.0, mínimo API 24) o teléfono físico Android con **Depuración por USB** activada.
4. **Git** instalado (`git --version`).

---

## Instalación y Ejecución

1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/Eclud300/MedicalStaff-Android.git](https://github.com/Eclud300/MedicalStaff-Android.git)
   cd MedicalStaff-Android
   ```

2. **Ubicarse en la rama estable:**
   ```bash
   git checkout main
   ```

3. **Abrir el proyecto en Android Studio:**
    - Seleccionar `File > Open` y elegir la carpeta raíz del proyecto clonado.
    - Esperar a que finalice automáticamente **Gradle Sync** para descargar todas las dependencias.

4. **Configurar la URL de la API (para pruebas con backend):**
    - Abrir o crear el archivo `local.properties` en la raíz del proyecto (no versionado en Git) y añadir:
      ```properties
      API_BASE_URL="https://<url-api-medicalstaff>/api/"
      ```
    - *Nota:* Si se prueba contra un backend local desde el emulador AVD, usar `http://10.0.2.2:<PUERTO>/api/`.

5. **Compilar y ejecutar la aplicación:**
    - Seleccionar el emulador AVD o dispositivo Android conectado en la barra superior de Android Studio.
    - Presionar el botón **Run** o el atajo `Shift + F10`.

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
```

---

## Estrategia de Versionamiento (GitHub Flow)
- **`main`:** Código estable y compilable.
- **`develop`:** Rama de integración de avances por sprint.
- **`feature/*`:** Ramas por módulo o funcionalidad integradas mediante **Pull Requests**.
- **Commits semánticos:** `feat:`, `fix:`, `chore:`, `docs:`, `style:`, `refactor:`.

---

## Solución de Problemas Comunes
- **Error de versión de JDK:** Ir a `Settings > Build, Execution, Deployment > Build Tools > Gradle` y seleccionar **Embedded JDK 21 (JetBrains Runtime 21.0.10)**.
- **Error de AAR metadata / SDK:** Verificar que `compileSdk` esté en `37` (`minorApiLevel 1`) en `app/build.gradle.kts` y que el SDK 37 esté descargado en `SDK Manager`.
- **Error de caché al cambiar de rama:** Ejecutar `Build > Clean Project` y luego `File > Sync Project with Gradle Files`.
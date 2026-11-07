# Aréte

<p align="center">
  <img src="docs/assets/icono.png" width="120" alt="Aréte logo"/>
</p>

<p align="center">
  <strong>Red social descentralizada y mesh — sin servidores centrales obligatorios, sin rastreo y sin censura.</strong>
</p>

<p align="center">
  <img alt="Android" src="https://img.shields.io/badge/Android-26%2B-green?logo=android"/>
  <img alt="Kotlin" src="https://img.shields.io/badge/Kotlin-2.4.0-blueviolet?logo=kotlin"/>
  <img alt="Compose" src="https://img.shields.io/badge/Jetpack%20Compose-BOM%202025.12-blue?logo=jetpackcompose"/>
  <img alt="Tests" src="https://img.shields.io/badge/Unit%20Tests-209%20passed-brightgreen"/>
  <img alt="License" src="https://img.shields.io/badge/License-Proprietary-red"/>
</p>

---

## El nombre: Aréte, una idea colombianizada

**Aréte** surge de un juego de palabras que une dos ideas: la **A** de *anti* y *rete*, palabra latina que significa «red». Esta combinación da forma a una identidad que, además, reinterpreta y colombianiza creativamente *areté* (ἀρετή), concepto de la filosofía griega asociado con la virtud, la excelencia y el desarrollo pleno de las capacidades humanas. Ambas ideas convergen en **Aréte**.

Así, el nombre conecta su identidad con su propósito: cuestionar las formas convencionales de entender las redes y proponer una manera distinta de relacionarnos, crecer y desarrollar nuestro potencial.

La intención no es rechazar la conexión entre personas, sino promover una forma de conectarse más consciente, segura y virtuosa. **Aréte es la colombianización de esa idea:** una identidad cercana, propia y con propósito.

Pero esta visión va más allá del nombre. Aréte nace también de una pregunta: ¿y si las redes sociales hubieran tomado un camino equivocado? ¿Y si, en su afán por mantenernos conectados, hubieran terminado convirtiendo nuestra atención, nuestras emociones y nuestros mecanismos de recompensa en recursos que explotar?

Frente a los sistemas diseñados para prolongar indefinidamente el tiempo de permanencia, alimentar el desplazamiento infinito (*infinite scroll*) y convertir cada interacción en un estímulo para la siguiente, **Aréte propone dar dos pasos atrás para recuperar aquello que alguna vez hicimos bien**. Porque avanzar no siempre significa añadir más funciones, más contenido o más estímulos. A veces, avanzar es reconocer que nos hemos equivocado y atrevernos a pulsar *Ctrl + Z*.

No se trata de regresar al pasado por nostalgia, sino de rescatar lo valioso de aquellos primeros espacios digitales: cuando el feed era, ante todo, un lugar para saber de nuestros amigos, compartir lo que vivíamos y mantenernos cerca, incluso a la distancia. Antes de que la conexión se confundiera con la exposición constante y de que estar al tanto de todo se convirtiera en una obligación interminable.

Por eso, **Aréte recupera el feed centrado en tus amigos y lo extiende a tu localidad**. Un espacio donde las personas que forman parte de tu vida y lo que sucede a tu alrededor tengan prioridad sobre el contenido diseñado para capturar tu atención. Una red que favorezca los vínculos cercanos, la comunidad y el descubrimiento de lo que ocurre en tu entorno, sin fomentar una interconexión innecesaria ni convertir cada instante libre en una oportunidad para retenerte frente a una pantalla.

La tecnología debería acercarnos a la vida, no sustituirla. Por eso, Aréte no aspira a capturar una atención infinita, sino a ofrecer un medio útil para conectar con los demás, descubrir oportunidades, participar en la comunidad y, finalmente, volver al mundo que existe más allá de la aplicación.

**Porque una buena red social no debería necesitar todo tu tiempo para demostrar su valor. Debería ayudarte a aprovechar mejor el tiempo que tienes.**

> De la virtud griega a una red social con propósito: conectar mejor también es una forma de virtud.

*Nota lingüística: esta combinación es una interpretación creativa de marca, no una etimología histórica literal. “Areté” es griego; “rete” es una palabra latina para red.*

---

## ¿Qué es Aréte?

**Aréte** es una aplicación Android de mensajería y red social táctica diseñada para operar casi al **100% sin internet** mediante redes ad-hoc (Bluetooth Low Energy, Bluetooth Classic RFCOMM y Wi-Fi LAN/Direct), con capacidad de sincronización resiliente contra **Supabase** cuando existe conectividad disponible.

> Cuando la infraestructura de telecomunicaciones colapsa —apagones, censura, catástrofes o zonas remotas— Aréte mantiene a las personas comunicadas en la malla.

---

## Documentación Técnica

Para profundizar en el diseño e implementación del sistema, consulta los documentos especializados en el directorio [`docs/`](docs/):

- 🏛️ [**Arquitectura Técnica del Sistema**](docs/ARQUITECTURA.md) — Capas, contratos, protocolos de transporte y criptografía E2EE v4.
- 📋 [**Plan Maestro de Mejoras y Auditoría**](docs/PLAN_MAESTRO_MEJORAS.md) — Plan canónico de refactorización, seguridad y producto.
- 📝 [**Historial de Cambios**](docs/HISTORIAL_CAMBIOS.md) — Cambios por funcionalidad: chats zonales, mascotas, red local/mesh, perfil, cartas, encuentros y seguridad.
- 🔧 [**Historial de Correcciones**](docs/HISTORIAL_CORRECCIONES.md) — Auditorías de seguridad, correcciones BLE/RLS y auditoría integral 2026 (S-01 a S-17, C-01 a C-13).
- 🛡️ [**Modelo de Amenazas**](docs/seguridad/MODELO_DE_AMENAZAS.md) — Superficie de ataque, mitigaciones activas y capas de seguridad (v2.0).
- 🗺️ [**Guía Funcional de Regiones**](docs/GUIA_FUNCIONAL_REGIONES.md) — Diseño funcional del sistema de regiones y chats zonales.
- 👤 [**Implementación de Perfil y Bitácora**](docs/IMPLEMENTACION_PERFIL.md) — Pantalla de perfil, bitácora unificada y campos opcionales.
- 📚 [**Historial de Fases (1–20)**](docs/historial/HISTORIAL_FASES_1_A_20.md) — Consolidación cronológica de todas las fases de desarrollo.

---

## Características Principales

### 🔵 Conectividad Mesh y Red Local
- **Bluetooth Classic (RFCOMM)**: Enlaces punto a punto dedicados con supervisión de ciclo de vida (`SupervisorJob`) y reconexión exponencial.
- **BLE (Bluetooth Low Energy)**: Descubrimiento adaptativo de vecinos y emisión de presencia con control estricto de MTU (evitando errores `ADVERTISE_FAILED_DATA_TOO_LARGE`).
- **GATT Framer**: Protocolo propio de fragmentación y reensamblado seguro de tramas (hasta 64 KB) con limpieza automática de sesiones tras 12 segundos y protección contra tramas duplicadas.
- **Wi-Fi LAN Transport**: Difusión en red de área local con `ThreadPoolExecutor` acotado (16 trabajadores), timeouts estrictos en sockets (`soTimeout = 15s`) y sincronización por `CountDownLatch`.
- **Enrutamiento Mesh**: Algoritmo de propagación con TTL configurable (máximo 7 saltos) y caché de deduplicación de IDs de mensaje.

### 🔒 Privacidad y Criptografía Extremo a Extremo (E2EE)
- **Cifrado E2EE v4**: Curvas Elípticas `ECDH` (P-256 / secp256r1) + `HKDF-SHA256` + `AES-256-GCM`. Formato `ENC:v4:<iv_b64>:<ciphertext_b64>` con **AAD contextual** `remitente|destinatario|chatId` que vincula el ciphertext al canal específico.
- **Autenticidad en malla local**: Firma ECDSA secp256k1 en cada paquete UDP; handshake ECDSA con anti-replay de 60 s en sesiones TCP LAN.
- **Zero-Storage de Claves Privadas**: Claves resguardadas en el almacén de hardware de Android (`EncryptedSharedPreferences` / Android Keystore).
- **Sin Dependencia de Identidad Central**: Sesión local autónoma (`GestorSesionLocal`) que garantiza funcionamiento e identidad táctica sin requerir registro en nube.
- **Indicador de E2EE**: `🔒 E2EE` / `⚠️ Sin clave` visible en la pantalla de chat; envío en claro bloqueado si no hay clave negociada.

### 🔐 Auditoría de Seguridad (nov 2026)
- Auditoría integral con **17 correcciones en backend** (S-01 a S-17) y **9 correcciones en cliente Android** (C-01 a C-13), todas implementadas y verificadas.
- Ver detalle completo: [Historial de Correcciones](docs/HISTORIAL_CORRECCIONES.md) · [Modelo de Amenazas](docs/seguridad/MODELO_DE_AMENAZAS.md) · [Documento de auditoría archivado](docs/seguridad/AUDITORIA_2026.md).

### 🐱 Michi, la mascota 100 % local
- **Sin IA ni servidores**: la mascota (por defecto «Michi», con nombre editable) vive solo en el teléfono; no hay chat con IA ni claves de proveedores.
- **Chispas y medicina se envían desde el mapa**: al tocar un gato cercano (o en la lista de Cercanos) puedes enviarle una chispa ✦ o una medicina 💊. Una mascota enferma solo se cura si alguien le envió medicina antes.

### 📰 Gaceta Comunitaria y Comunidades Persistentes
- **Feed Canónico (`gaceta_feed`)**: Pestaña principal de comunidad como **Gaceta** (📰) respaldada por una vista SQL con cálculo dinámico de `likes`, `comentarios` y estado `liked_por_mi`.
- **Filtros Tácticos**: Segmentación rápida por chips (*Todos, Nuevos, Eventos, Avisos, Debate*).
- **Seguridad RLS por Membresía**: Políticas estrictas de acceso (`es_miembro()`) que garantizan aislamiento entre comunidades públicas y cerradas.
- **Almacenamiento de Medios**: Registro estructurado en `comunidad_publicacion_medios` y almacenamiento en buckets seguros.

### 💬 Salas y Mensajería Unificada
- **Sala General Pinned**: Chat público general fijado al inicio de la lista (`SALA GENERAL #RADAR`), eliminando duplicaciones en la interfaz.
- **Salas Comunitarias y Privadas**: Listado dinámico de las salas asociadas a las comunidades del usuario con soporte de clave de acceso.
- **Push-To-Talk (PTT) y Videollamadas**: Audio dúplex continuo, transmisión PTT en tiempo real y llamadas directas con señalización híbrida.

### 🗺️ Radar Táctico y Asistente de Eventos
- **Botón "Mi Ubicación"**: Mira táctica interactiva en la esquina inferior del mapa que centra suavemente la cámara en la posición actual del dispositivo y reanuda el seguimiento automático.
- **Botón Rápido "+"**: Creación inmediata de eventos personales o de comunidad desde el mapa.
- **Asistente de Eventos Desacoplado**:
  - `lugarId` opcional en la base de datos y modelos; permite crear eventos en cualquier coordenada geográfica directa.
  - Corrección horaria completa mediante `java.time`, preservando la equivalencia horaria local exacta sin desfasajes UTC.
- **Ciclo Día/Noche Solarpunk**: Adaptación ambiental del mapa (`EstiloMapaFactory`) según el horario local (Día 07:00–19:00, Noche 19:00–07:00), independiente del modo de tema del sistema operativo.

---

## Estructura del Proyecto

```
Aréte_Social/
├── .github/workflows/          # Pipeline CI con escaneo Gitleaks y compilación Gradle
├── app/
│   ├── build.gradle.kts        # Configuración de compilación limpia con catálogo toml
│   └── src/
│       ├── main/java/com/renea/antired_social/
│       │   ├── core/           # ContenedorApp (Inyección de Dependencias manual)
│       │   ├── data/           # Repositorios Supabase, GATT, Wi-Fi LAN, BLE, Cifrado
│       │   ├── domain/         # Modelos puros, interfaces y casos de uso
│       │   ├── feature/        # ViewModels (Auth, Comunidades, Eventos, Llamadas, Mensajería)
│       │   └── gui/            # Pantallas Compose (Radar/Mapa, Gaceta, Salas, Tamagotchi)
│       └── test/java/com/renea/antired_social/
│           ├── data/mesh/      # GattFramerTest (reensamblado y resiliencia)
│           ├── domain/crypto/  # CifradorE2eeTest (criptografía asimétrica y AES-GCM)
│           ├── feature/auth/   # GestorSesionLocalTemaTest (persistencia de tema)
│           ├── gui/theme/      # ResolutorCicloDiaTest (horarios solares)
│           └── testutils/      # FakeSharedPreferences y dobles de prueba JVM
├── docs/                       # Documentación técnica consolidada
├── gradle/                     # Wrapper y catálogo de dependencias (libs.versions.toml)
└── supabase/
    ├── schema.sql              # Esquema inicial completo (fuente única)
    └── INSTALACION_DESDE_CERO.md # Guía de configuración en Supabase
```

---

## Instalación inicial de Supabase

El proyecto no requiere aplicar una cadena de migraciones para una instalación nueva. La fuente única del esquema es [`supabase/schema.sql`](supabase/schema.sql). Sigue [`supabase/INSTALACION_DESDE_CERO.md`](supabase/INSTALACION_DESDE_CERO.md) y ejecútalo una sola vez en un proyecto Supabase vacío. No lo ejecutes sobre una base que contenga datos que deban conservarse.

## Configuración segura de Supabase

Copia `local.properties.example` como `local.properties` y reemplaza los valores de ejemplo cuando quieras conectar el backend. Si todavía no has configurado Supabase, la app muestra una pantalla explicativa en lugar de cerrarse durante el arranque; las funciones remotas seguirán sin estar disponibles. Antes de probar la conexión, verifica la configuración con `python3 scripts/validar-configuracion-supabase.py`; el validador no imprime claves. No uses claves `service_role` o `sb_secret_` dentro de Android. Consulta [`docs/historial/HISTORIAL_FASES_1_A_20.md`](docs/historial/HISTORIAL_FASES_1_A_20.md) (Fase 20 — Configuración Android/Supabase).

## Compilación y Ejecución

### Requisitos
- **JDK 21** (OpenJDK o Eclipse Adoptium recomendado; Gradle Wrapper usa JVM 21).
- **Android SDK** con `compileSdk = 37`, `minSdk = 26`.
- Android Studio Ladybug (o Gradle CLI).

### Pasos

1. **Configurar `local.properties`:**
   ```properties
   sdk.dir=/ruta/a/tu/Android/Sdk
   MAPS_API_KEY=tu_google_maps_api_key
   SUPABASE_URL=https://tu-proyecto.supabase.co
   SUPABASE_ANON_KEY=tu_supabase_anon_key
   ```

2. **Ejecutar Suite de Pruebas Unitarias:**
   ```bash
   ./gradlew testDebugUnitTest
   ```
   > Ejecuta las pruebas unitarias definidas en el proyecto (incluye criptografía, Bluetooth GATT, persistencia de temas y ciclo solar). El número y el resultado efectivo dependen de la versión del código y deben confirmarse ejecutando Gradle.

3. **Compilar el APK de Depuración:**
   ```bash
   ./gradlew assembleDebug
   ```

---

## Licencia

Este proyecto es de código **privado y propietario**. Todos los derechos están reservados. Queda prohibida la copia, modificación, distribución o explotación comercial sin el consentimiento expreso y por escrito del autor.

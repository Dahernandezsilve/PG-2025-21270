# PG-2025-21270
Proyecto de Graduación 2025 - Carnet: 21270

## 🌾 Santa Ana Mobile (React Native + Expo)

## 🎥 Video Demo

<video src="./demo/demo.mp4" controls width="700"></video>

Aplicación móvil del **trabajo de graduación en modalidad Trabajo Profesional “Recopilación, visualización y análisis de formularios adaptables en campos de acción agrícola”**, desarrollada para el **Ingenio Santa Ana**.

Permite la **recolección de datos en campo** mediante formularios dinámicos, con soporte **offline**, validaciones locales y sincronización automática al restablecer conexión.

---

## ✨ Características clave

### 🧾 Formularios dinámicos
- Generados desde esquemas JSON enviados por la plataforma web.
- Campos: texto, numéricos, listas, múltiple selección, fechas, firmas, calculados, grupos repetibles.
- Manejo de teclado con `react-native-keyboard-controller`.

### 📶 Operación offline
- SQLite (Expo SQLite) con sincronización diferida.
- Redux Persist + AsyncStorage.
- Compatible con Drizzle Studio Plugin.

### 🔐 Autenticación y seguridad
- Login por QR o credenciales.
- Tokens guardados en Expo Secure Store.

### 📤 Sincronización
- TanStack Query + NetInfo.

### 🖥️ Interfaz centrada en el usuario
- Animaciones con Reanimated 3.
- NativeWind v4 + styled-components.
- Accesibilidad WCAG 2.1.

---

## 🧩 Stack tecnológico

| Categoría | Tecnologías |
|------------|-------------|
| Framework | React Native 0.79 + Expo SDK 53 |
| UI / UX | NativeWind v4, Styled-components, Reanimated 3 |
| Estado | Redux Toolkit + Persist |
| Networking | Axios + TanStack Query |
| Persistencia | SQLite, AsyncStorage |
| Navegación | Expo Router v5 |
| Validaciones | Formik + Yup |
| Plugins | Camera, Secure Store, Notifications |
| Build | EAS Build |

---

## 📋 Requisitos Previos

- Node.js v22.18.0  
- Python 3.12.11  
- Yarn 1.22.22  

---

## 🚀 Instalación y ejecución

### 1️⃣ Clonar
```bash
git clone https://github.com/santa-ana-agroforms/SantaAna_Mobile.git
cd SantaAna_Mobile
```

### 2️⃣ Instalar dependencias
```bash
yarn install
```

### 3️⃣ Ejecutar servidor Metro
```bash
yarn start --clear
```

### 4️⃣ Ejecutar en Android o iOS
```bash
yarn android
yarn ios
```

---

## 📱 Desarrollo (**EJECUCIÓN** para android con DevClient) (EXPO) Dev Client / APK

Este proyecto utiliza **librerías nativas** (Reanimated, Secure Store, Camera, SQLite, Keyboard Controller, etc.), por lo que **NO puede ejecutarse en Expo Go**.

Es necesario usar un **Dev Client personalizado**, que incluye todos los módulos nativos compilados específicamente para esta app. Para ello se incluye un dev-client móvil: el archivo `src/devClient/devClient.zip` contiene el dev-client utilizado (comprimido para poder subirlo al repositorio). Se puede utilizar directamente para trabajar con la app si se prefiere evitar compilar un propio dev-client.

### 🔧 Generar un Dev Client (recomendado para desarrollo + iniciar el proyecto)
```bash
eas build --profile development --platform android
```

Una vez generado, instala el APK en tu dispositivo y ejecuta:

```bash
yarn start --clear
```

Ingresa con la dirección exp://192.168.XXX.XXX:XXXX proporcionada presionando **S** **con el Dev Client**.

### 📦 Generar un APK simple para pruebas internas
```bash
eas build --profile preview --platform android
```
---

## ⚙️ Variables de Entorno

### 📱 `.env.local`
```env
EXPO_PUBLIC_API_BASE_KEY=SANTAANA_API_BASE_KEY
EXPO_PUBLIC_ACCESS_KEY=SANTAANA_ACCESS_KEY
EXPO_PUBLIC_REFRESH_KEY=SANTAANA_REFRESH_KEY
EXPO_PUBLIC_ACCESS_SECRET=7qN11exampleSecret
EXPO_PUBLIC_REFRESH_SECRET=KD4TexampleSecret
EXPO_PUBLIC_QR_MAGIC_CODE=3rb9MxexampleCode
EXPO_PUBLIC_BASE_URL=https://santaana.example.com/api
```

---

## 🧭 Estructura del proyecto

```
app/                      # Rutas manejadas por Expo Router
 ├─ form/                 # Vistas relacionadas a formularios
 ├─ forms/                # Formularios agrupados por tipo
 ├─ redux/                # Rutas o pantallas relacionadas a Redux (si aplica)
 ├─ test/                 # Pantallas de pruebas internas
 ├─ _layout.tsx           # Layout general para navegación
 ├─ index.tsx             # Pantalla principal
 └─ qr.tsx                # Pantalla para escaneo / login por QR

assets/                   # Recursos estáticos
 ├─ fonts/                # Fuentes personalizadas
 └─ images/               # Imágenes, íconos y logos

devClient/                # Instalador Android para probar el modo desarrollo nativo.

src/                      # Lógica principal del proyecto
 ├─ api/                  # Cliente Axios, endpoints y servicios REST
 ├─ auth/                 # Manejo de autenticación, tokens y sesiones
 ├─ background/           # Tareas en segundo plano (sync, workers)
 ├─ components/           # Componentes UI (átomos, moléculas, organismos)
 ├─ db/                   # Configuración de SQLite, modelos y accesos
 ├─ forms/                # Sistema interno para renderizar formularios dinámicos
 ├─ hooks/                # Hooks personalizados reutilizables
 ├─ lib/                  # Funciones auxiliares, helpers y lógica compartida
 ├─ notifications/        # Manejo de notificaciones locales y push
 ├─ pages/                # Pantallas desacopladas del router (legacy o secciones)
 ├─ redux/                # Redux Toolkit slices
 ├─ screens/              # Pantallas principales de la app
 ├─ store/                # Configuración de Redux y Persist
 ├─ sync/                 # Lógica de sincronización offline → online
 ├─ theme/                # Configuración de estilos, colores y tipografías
 └─ utils/                # Utilidades generales del proyecto

```

---

## 👨‍💻 Autor

**Diego Alexander Hernández Silvestre | Carnet: 21270**  
Universidad del Valle de Guatemala – Trabajo de Graduación 2025.

---

## 🔑 Credenciales requeridas para EAS

Para poder generar un **Dev Client** o un **APK** mediante EAS Build, es necesario contar con:

- **Credenciales de desarrollador de Expo**
- **Acceso autorizado al proyecto en la organización**
- **Permisos para ejecutar builds remotas**

Estas credenciales **no se incluyen en el repositorio** y deben ser proporcionadas por el **administrador del sistema** o por el **autor del proyecto**.

Sin estas credenciales, los comandos `eas build` no podrán ejecutarse correctamente.

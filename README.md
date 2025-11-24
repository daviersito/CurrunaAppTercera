# CurrunaAppTercera
Tercera entrega app curruña
# CurruñaApp 

Aplicación Android para la venta y gestión de helados artesanales "Curruña". Permite a los clientes realizar pedidos y a los administradores gestionar el inventario y las órdenes.

##  Descripción

CurruñaApp es un e-commerce móvil nativo desarrollado en Kotlin.
*   **Clientes:** Pueden registrarse, ver el catálogo de helados, añadir productos al carrito, editar su perfil y realizar pedidos.
*   **Administradores:** Tienen un panel exclusivo para crear nuevos productos (con subida de imágenes), editar stock y gestionar el estado de los pedidos de los clientes.

##  Tecnologías Utilizadas

*   **Frontend (Android):**
    *   Kotlin
    *   Retrofit 2 (Comunicación API REST)
    *   OkHttp (Cliente HTTP & Logging)
    *   Glide (Carga de imágenes)
    *   Corrutinas (Manejo asíncrono)
    *   ViewBinding
*   **Backend:**
    *   Xano (No-code Backend & Database)

## ⚙️ Configuración del Proyecto

### 1. Android Studio
1.  Clona este repositorio.
2.  Abre el proyecto en **Android Studio Ladybug** (o superior).
3.  Espera a que Gradle sincronice las dependencias.
4.  Verifica el archivo `Constants.kt` para asegurar que la URL base sea correcta.

### 2. Backend (Xano)
La aplicación se conecta a una API REST en Xano.
*   **Base URL:** `https://x8ki-letl-twmt.n7.xano.io/api:ng05CpE3`

**Endpoints Clave:**
*   `POST /auth/login`: Autenticación.
*   `POST /auth/signup`: Registro.
*   `GET /product`: Listado de helados.
*   `POST /product`: Crear producto (Admin).
*   `POST /upload/image`: Subida de imágenes (Multipart).
*   `POST /order`: Crear pedido.
*   `GET /order`: Historial de pedidos.

##  Usuarios de Prueba (Demo)

Para probar la aplicación, puedes utilizar las siguientes credenciales o registrar un usuario nuevo:

| Rol | Email | Contraseña | Funciones |
| :--- | :--- | :--- | :--- |
| **Administrador** | `admin@curruna.com` | `admin123` | Crear productos, Ver todos los pedidos, Editar Stock. |
| **Cliente** | `cliente@demo.com` | `123456` | Comprar helados, Carrito, Perfil. |

> **Nota:** Si el login falla, asegúrate de registrar un usuario nuevo desde la pantalla de "Registro".

## 📸 Gestión de Imágenes

Las imágenes se almacenan en el servidor de Xano.
*   **Subida:** La App sube las imágenes una por una al endpoint `/upload/image`.
*   **Asociación:** Una vez subidas, la App recibe un objeto de imagen completo y lo asocia al producto mediante un `PATCH /product/{id}`.
*   **Visualización:** Se utiliza la librería **Glide** para renderizar las URLs recibidas en el campo `image` (Array de objetos) del JSON.

## 📄 Estructura de Datos Relevante

**Producto (JSON):**

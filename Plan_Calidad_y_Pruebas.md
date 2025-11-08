# 🧪 PLAN DE CALIDAD Y PRUEBAS - PETOS APP

**Fecha de creación**: Enero 2025
**Versión**: 1.0
**Tipo de pruebas**: Funcionales Manuales + Automatización sugerida
**Alcance**: Frontend (Flutter) + Validación de respuestas Backend (NestJS)

---

## 📋 TABLA DE CONTENIDOS

1. [Introducción](#1-introducción)
2. [Metodología de Pruebas](#2-metodología-de-pruebas)
3. [Configuración del Entorno de Pruebas](#3-configuración-del-entorno-de-pruebas)
4. [Casos de Prueba por Módulo](#4-casos-de-prueba-por-módulo)
5. [Matriz de Pruebas](#5-matriz-de-pruebas)
6. [Casos Extremos y Pruebas de Estrés](#6-casos-extremos-y-pruebas-de-estrés)
7. [Herramientas de Automatización](#7-herramientas-de-automatización)
8. [Reporte de Bugs](#8-reporte-de-bugs)
9. [Checklist Final de Calidad](#9-checklist-final-de-calidad)
10. [Anexos](#10-anexos)

---

## 1. INTRODUCCIÓN

### 1.1 Objetivo del Documento

Este documento define el **plan de pruebas funcionales** para la aplicación Petos, una red social para amantes de mascotas. El objetivo es asegurar que todas las funcionalidades del frontend funcionan correctamente y que el backend responde adecuadamente a las peticiones.

### 1.2 Alcance

**Incluye**:
- ✅ Pruebas funcionales manuales del frontend (Flutter)
- ✅ Validación de respuestas del backend (NestJS)
- ✅ Casos de éxito (happy path)
- ✅ Casos extremos (edge cases)
- ✅ Manejo de errores
- ✅ Validaciones de formularios
- ✅ Flujos de navegación
- ✅ Sugerencias de automatización

**No incluye**:
- ❌ Pruebas unitarias del código backend
- ❌ Pruebas unitarias del código frontend
- ❌ Pruebas de rendimiento/carga
- ❌ Pruebas de seguridad (pentesting)

### 1.3 Criterios de Aceptación

Una funcionalidad se considera **APROBADA** si:
- ✅ Cumple con todos los casos de prueba definidos
- ✅ Maneja correctamente los casos extremos
- ✅ Muestra mensajes de error claros y útiles
- ✅ No presenta crashes o errores no controlados
- ✅ La UI responde correctamente en diferentes tamaños de pantalla
- ✅ El backend responde con los códigos HTTP correctos

Una funcionalidad se considera **RECHAZADA** si:
- ❌ Falla al menos 1 caso de prueba crítico
- ❌ Causa crash de la aplicación
- ❌ No maneja errores de red correctamente
- ❌ Permite datos inválidos en el backend
- ❌ La UI se rompe visualmente

---

## 2. METODOLOGÍA DE PRUEBAS

### 2.1 Tipos de Pruebas

#### 2.1.1 Pruebas Funcionales Manuales
- **Propósito**: Verificar que cada funcionalidad cumple con los requisitos
- **Ejecutor**: QA Tester humano
- **Frecuencia**: Antes de cada release
- **Cobertura**: 100% de funcionalidades críticas

#### 2.1.2 Pruebas de Casos Extremos (Edge Cases)
- **Propósito**: Verificar comportamiento en situaciones límite
- **Ejemplos**: Campos vacíos, textos muy largos, caracteres especiales, sin conexión
- **Ejecutor**: QA Tester humano
- **Frecuencia**: Antes de cada release mayor

#### 2.1.3 Pruebas de Regresión
- **Propósito**: Asegurar que nuevos cambios no rompan funcionalidades existentes
- **Ejecutor**: QA Tester humano + Tests automatizados (sugerido)
- **Frecuencia**: Después de cada cambio significativo

#### 2.1.4 Pruebas de Aceptación de Usuario (UAT)
- **Propósito**: Validar que la app cumple expectativas del usuario final
- **Ejecutor**: Usuarios beta
- **Frecuencia**: Antes del lanzamiento MVP

### 2.2 Niveles de Prioridad

| Prioridad | Descripción | Impacto si falla |
|-----------|-------------|------------------|
| 🔴 **CRÍTICA** | Funcionalidad core, sin ella la app no funciona | Bloqueante de release |
| 🟡 **ALTA** | Funcionalidad importante, afecta UX significativamente | Debe corregirse antes de release |
| 🟢 **MEDIA** | Funcionalidad secundaria, afecta UX moderadamente | Puede ir en release si se documenta |
| ⚪ **BAJA** | Mejora estética o funcionalidad menor | No bloqueante |

### 2.3 Estados de Prueba

| Estado | Símbolo | Descripción |
|--------|---------|-------------|
| No probado | ⬜ | Caso de prueba aún no ejecutado |
| Aprobado | ✅ | Caso de prueba pasó correctamente |
| Fallido | ❌ | Caso de prueba falló |
| Bloqueado | 🚫 | No se puede probar (dependencia bloqueada) |
| En revisión | 🔄 | Bug reportado, esperando fix |

---

## 3. CONFIGURACIÓN DEL ENTORNO DE PRUEBAS

### 3.1 Requisitos Previos

**Hardware**:
- Dispositivo Android (real o emulador) - Android 8.0+
- Dispositivo iOS (real o simulador) - iOS 12.0+
- PC/Mac con Flutter SDK instalado

**Software**:
- Flutter SDK (versión estable latest)
- Android Studio / Xcode
- Postman (para pruebas de API)
- Herramienta de captura de pantalla/video

**Backend**:
- Servidor de desarrollo corriendo en `http://localhost:8080`
- Base de datos PostgreSQL con datos de prueba

### 3.2 Datos de Prueba

#### Usuario de Prueba Principal
```
Email: qa.tester@petos.com
Password: QA_Test123!
Nombre: QA
Apellido: Tester
```

#### Usuarios Adicionales (para pruebas sociales)
```
Usuario 2:
Email: user2@petos.com
Password: User2_Test123!

Usuario 3:
Email: user3@petos.com
Password: User3_Test123!
```

#### Mascotas de Prueba
```
Mascota 1: "Max" - Perro - Golden Retriever - 3 años
Mascota 2: "Luna" - Gato - Siamés - 2 años
Mascota 3: "Rocky" - Perro - Bulldog - 5 años
```

### 3.3 Preparación del Entorno

**Pasos previos a las pruebas**:
1. ✅ Verificar que el backend está corriendo (`GET http://localhost:8080/health`)
2. ✅ Limpiar base de datos o crear datos de prueba frescos
3. ✅ Instalar app en dispositivo de prueba (`flutter run`)
4. ✅ Verificar conexión a internet estable
5. ✅ Configurar herramienta de captura de pantalla
6. ✅ Limpiar caché de la app antes de cada sesión de pruebas

---

## 4. CASOS DE PRUEBA POR MÓDULO

### 4.1 MÓDULO: AUTENTICACIÓN Y REGISTRO

#### CP-AUTH-001: Login con Credenciales Válidas
| Campo | Detalle |
|-------|---------|
| **ID** | CP-AUTH-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Autenticación |
| **Funcionalidad** | Login |

**Precondiciones**:
- Usuario registrado existe en base de datos
- App instalada y abierta en pantalla de login

**Pasos**:
1. Ingresar email: `qa.tester@petos.com`
2. Ingresar password: `QA_Test123!`
3. Tocar botón "Iniciar Sesión"

**Resultado Esperado**:
- ✅ Indicador de carga se muestra mientras se procesa
- ✅ Backend responde con status 200 y token JWT
- ✅ App guarda token en storage local
- ✅ Usuario es redirigido a pantalla de Home Feed
- ✅ Bottom navigation bar es visible

**Validaciones Backend**:
- Response status: `200 OK`
- Response body contiene: `{ access_token: "...", user: {...} }`

**Casos Extremos**:
- ⚠️ **Sin conexión**: Mostrar error "Sin conexión a internet"
- ⚠️ **Backend caído**: Mostrar error "Servidor no disponible, intenta más tarde"

---

#### CP-AUTH-002: Login con Credenciales Inválidas
| Campo | Detalle |
|-------|---------|
| **ID** | CP-AUTH-002 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Autenticación |

**Pasos**:
1. Ingresar email: `qa.tester@petos.com`
2. Ingresar password: `PasswordIncorrecto`
3. Tocar botón "Iniciar Sesión"

**Resultado Esperado**:
- ✅ Backend responde con status 401 Unauthorized
- ✅ App muestra mensaje de error: "Credenciales incorrectas"
- ✅ Usuario permanece en pantalla de login
- ✅ Campos de formulario no se limpian (mantener email)

**Validaciones Backend**:
- Response status: `401 Unauthorized`
- Response body: `{ message: "Invalid credentials", statusCode: 401 }`

---

#### CP-AUTH-003: Validación de Formato de Email
| Campo | Detalle |
|-------|---------|
| **ID** | CP-AUTH-003 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Autenticación |

**Pasos**:
1. Ingresar email inválido: `emailsinformato`
2. Tocar campo de password (blur del campo email)

**Resultado Esperado**:
- ✅ Campo email muestra error: "Formato de email inválido"
- ✅ Botón "Iniciar Sesión" permanece deshabilitado
- ✅ No se hace petición al backend

**Casos a Probar**:
| Email Ingresado | Debe Validar Como |
|-----------------|-------------------|
| `emailsinformato` | ❌ Inválido |
| `email@` | ❌ Inválido |
| `@dominio.com` | ❌ Inválido |
| `email@dominio` | ❌ Inválido |
| `email@dominio.com` | ✅ Válido |
| `email+tag@dominio.com` | ✅ Válido |

---

#### CP-AUTH-004: Registro Multi-Paso - Paso 1 (Datos Usuario)
| Campo | Detalle |
|-------|---------|
| **ID** | CP-AUTH-004 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Registro |

**Precondiciones**:
- App abierta en pantalla de registro
- Paso 1 visible (Datos de Usuario)

**Pasos**:
1. Ingresar nombre: `Nuevo`
2. Ingresar apellido: `Usuario`
3. Ingresar email: `nuevo.usuario@petos.com`
4. Ingresar password: `NuevoUser123!`
5. Confirmar password: `NuevoUser123!`
6. Tocar botón "Siguiente"

**Resultado Esperado**:
- ✅ Todos los campos validan correctamente
- ✅ Indicador de progreso muestra "1/3"
- ✅ Usuario es llevado a Paso 2 (Ubicación)
- ✅ Datos del Paso 1 se mantienen en memoria (si vuelve atrás)

**Validación de Contraseña**:
- ✅ Mínimo 8 caracteres
- ✅ Al menos 1 mayúscula
- ✅ Al menos 1 minúscula
- ✅ Al menos 1 número
- ✅ Opcional: 1 carácter especial

**Casos Extremos**:
| Password | Debe Validar Como |
|----------|-------------------|
| `123456` | ❌ Muy corta (< 8) |
| `abcdefgh` | ❌ Sin mayúsculas ni números |
| `ABCDEFGH` | ❌ Sin minúsculas ni números |
| `Abcdefgh` | ❌ Sin números |
| `Abcdefg1` | ✅ Válida |
| `Abc123!@#` | ✅ Válida |

---

#### CP-AUTH-005: Registro Multi-Paso - Paso 3 (Primera Mascota)
| Campo | Detalle |
|-------|---------|
| **ID** | CP-AUTH-005 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Registro |

**Precondiciones**:
- Usuario completó Paso 1 y Paso 2
- Paso 3 visible (Registrar Primera Mascota)

**Pasos**:
1. Tocar avatar para agregar foto (opcional)
2. Ingresar nombre: `Firulais`
3. Seleccionar tipo: `Perro`
4. Seleccionar raza: `Golden Retriever`
5. Seleccionar fecha de nacimiento: `01/01/2020`
6. Seleccionar sexo: `Macho`
7. Ingresar biografía (opcional): `Mi primer amigo peludo`
8. Tocar botón "Finalizar Registro"

**Resultado Esperado**:
- ✅ Loading indicator se muestra
- ✅ Backend crea usuario nuevo (status 201 Created)
- ✅ Backend crea mascota asociada al usuario
- ✅ Backend genera JWT token
- ✅ App guarda token en storage
- ✅ Usuario es redirigido a Home Feed
- ✅ Mensaje de bienvenida se muestra (opcional)

**Validaciones Backend**:
```json
POST /auth/register
Status: 201 Created
Response: {
  "user": { "id": 1, "email": "...", ... },
  "access_token": "eyJhbGc...",
  "pet": { "id": 1, "name": "Firulais", ... }
}
```

**Casos Extremos**:
- ⚠️ **Email ya existe**: Backend responde 409 Conflict, mostrar "Email ya registrado"
- ⚠️ **Sin conexión durante registro**: Mostrar error, no guardar datos localmente
- ⚠️ **Falla upload de foto**: Continuar registro sin foto, reintentable después

---

### 4.2 MÓDULO: GESTIÓN DE PERFIL DE USUARIO

#### CP-PROFILE-001: Ver Perfil Propio
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PROFILE-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Perfil Usuario |

**Precondiciones**:
- Usuario autenticado
- Bottom navigation visible

**Pasos**:
1. Tocar tab "Perfil" en bottom navigation

**Resultado Esperado**:
- ✅ Backend es consultado: `GET /users/profile`
- ✅ Response status: 200 OK
- ✅ Perfil se muestra con:
  - Avatar del usuario
  - Nombre completo
  - Username
  - Biografía (si existe)
  - Ubicación
  - Estadísticas: # Publicaciones, # Seguidores, # Seguidos
- ✅ Botón "Editar perfil" visible
- ✅ Tabs visibles: Posts, Tagged, Likes
- ✅ Menú (⋮) visible con opciones

**Validaciones Backend**:
```json
GET /users/profile
Status: 200 OK
Response: {
  "id": 1,
  "firstName": "QA",
  "lastName": "Tester",
  "email": "qa.tester@petos.com",
  "avatarUrl": "...",
  "bio": "...",
  "location": "...",
  "stats": {
    "postsCount": 5,
    "followersCount": 10,
    "followingCount": 8
  }
}
```

---

#### CP-PROFILE-002: Editar Perfil de Usuario
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PROFILE-002 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Perfil Usuario |

**Precondiciones**:
- Usuario en su perfil propio

**Pasos**:
1. Tocar botón "Editar perfil"
2. Esperar que modal/pantalla de edición se abra
3. Modificar nombre: `QA Modificado`
4. Modificar biografía: `Nueva biografía de prueba`
5. Tocar botón "Guardar cambios"

**Resultado Esperado**:
- ✅ Backend es consultado: `PATCH /users/profile`
- ✅ Response status: 200 OK
- ✅ Loading indicator durante guardado
- ✅ Modal se cierra automáticamente
- ✅ Perfil se actualiza con nuevos datos
- ✅ Mensaje de éxito: "Perfil actualizado correctamente"

**Validaciones Backend**:
```json
PATCH /users/profile
Body: {
  "firstName": "QA Modificado",
  "bio": "Nueva biografía de prueba"
}
Status: 200 OK
Response: { ...usuario actualizado... }
```

**Casos Extremos**:
| Campo | Valor | Debe |
|-------|-------|------|
| Biografía | 151 caracteres | ❌ Rechazar (máximo 150) |
| Biografía | Texto con emojis 🐶🐱 | ✅ Aceptar |
| Nombre | Vacío | ❌ Rechazar (requerido) |
| Nombre | `<script>alert('xss')</script>` | ✅ Sanitizar/escapar |

---

#### CP-PROFILE-003: Ver Perfil de Otro Usuario
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PROFILE-003 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Perfil Usuario |

**Precondiciones**:
- Usuario autenticado
- Existe otro usuario en la base de datos (ID: 2)

**Pasos**:
1. Desde Home Feed, tocar avatar de otra persona
2. Esperar carga del perfil

**Resultado Esperado**:
- ✅ Backend es consultado: `GET /users/:userId`
- ✅ Response status: 200 OK
- ✅ Perfil se muestra con datos del otro usuario
- ✅ Botón "Seguir" o "Siguiendo" visible (según estado)
- ✅ Botón "Mensaje" visible
- ✅ Menú (⋮) con opciones: "Reportar", "Bloquear"
- ✅ Tabs visibles: Posts, Tagged (NO "Likes" - solo propio)
- ✅ NO debe mostrar botón "Editar perfil"

**Validaciones Backend**:
```json
GET /users/2
Status: 200 OK
Response: {
  "id": 2,
  "firstName": "Usuario",
  "lastName": "Dos",
  "isFollowing": false,
  "isFollowedBy": false,
  ...
}
```

---

#### CP-PROFILE-004: Seguir/Dejar de Seguir Usuario
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PROFILE-004 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Sistema Social |

**Precondiciones**:
- Usuario autenticado viendo perfil de otro usuario
- Usuario NO sigue al otro usuario actualmente

**Pasos - Seguir**:
1. Tocar botón "Seguir"

**Resultado Esperado - Seguir**:
- ✅ Backend: `POST /follows/:userId`
- ✅ Response status: 201 Created
- ✅ Botón cambia a "Siguiendo" inmediatamente
- ✅ Contador de "Seguidos" del usuario actual incrementa +1
- ✅ Contador de "Seguidores" del otro usuario incrementa +1
- ✅ Animación de botón (opcional)

**Pasos - Dejar de Seguir**:
1. Tocar botón "Siguiendo"
2. Confirmar acción (si hay confirmación)

**Resultado Esperado - Dejar de Seguir**:
- ✅ Backend: `DELETE /follows/:userId`
- ✅ Response status: 200 OK
- ✅ Botón cambia a "Seguir" inmediatamente
- ✅ Contadores se decrementan
- ✅ Animación de botón

**Casos Extremos**:
- ⚠️ **Ya sigue al usuario**: Backend responde 409 Conflict, app maneja sin crash
- ⚠️ **Usuario bloqueado**: Backend responde 403 Forbidden, mostrar mensaje
- ⚠️ **Seguir/dejar de seguir rápidamente**: Validar que solo última acción cuenta

---

### 4.3 MÓDULO: GESTIÓN DE MASCOTAS

#### CP-PET-001: Listar Mascotas del Usuario
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PET-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Mascotas |

**Precondiciones**:
- Usuario autenticado
- Usuario tiene al menos 1 mascota registrada

**Pasos**:
1. Desde perfil propio, tocar menú (⋮)
2. Tocar opción "Mis Mascotas"

**Resultado Esperado**:
- ✅ Backend: `GET /pets/my-pets`
- ✅ Response status: 200 OK
- ✅ Lista de mascotas se muestra con cards
- ✅ Cada card muestra:
  - Avatar de la mascota
  - Nombre, tipo, raza
  - Edad
  - Botones: "Ver perfil", "Editar", "Eliminar"
- ✅ Botón flotante (+) para agregar nueva mascota
- ✅ Pull-to-refresh funciona

**Validaciones Backend**:
```json
GET /pets/my-pets
Status: 200 OK
Response: [
  {
    "id": 1,
    "name": "Max",
    "type": "dog",
    "breed": "Golden Retriever",
    "birthDate": "2020-01-01",
    "avatarUrl": "...",
    ...
  }
]
```

**Estado Vacío**:
- ✅ Si no tiene mascotas: Mostrar EmptyState con mensaje "Sin mascotas" y botón "Agregar Mascota"

---

#### CP-PET-002: Agregar Nueva Mascota
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PET-002 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Mascotas |

**Precondiciones**:
- Usuario en pantalla "Mis Mascotas"

**Pasos**:
1. Tocar botón flotante (+)
2. Esperar que modal se abra
3. (Opcional) Tocar avatar para agregar foto
4. Ingresar nombre: `Nuevo Perro`
5. Seleccionar tipo: `Perro`
6. Seleccionar raza: `Labrador`
7. Seleccionar fecha de nacimiento
8. Seleccionar sexo: `Macho`
9. Ingresar biografía (opcional): `Un perro juguetón`
10. Tocar botón "Guardar"

**Resultado Esperado**:
- ✅ Formulario valida todos los campos requeridos
- ✅ Backend: `POST /pets`
- ✅ Si hay foto: Backend recibe `multipart/form-data`
- ✅ Response status: 201 Created
- ✅ Modal se cierra
- ✅ Lista de mascotas se actualiza con nueva mascota
- ✅ Mensaje de éxito: "Mascota agregada correctamente"

**Validaciones Backend**:
```json
POST /pets
Body: {
  "name": "Nuevo Perro",
  "type": "dog",
  "breed": "Labrador",
  "birthDate": "2022-05-15",
  "sex": "male",
  "bio": "Un perro juguetón"
}
Status: 201 Created
Response: { "id": 5, "name": "Nuevo Perro", ... }
```

**Casos Extremos**:
| Campo | Valor | Debe |
|-------|-------|------|
| Nombre | Vacío | ❌ Mostrar error "Campo requerido" |
| Nombre | 51 caracteres | ❌ Rechazar (máximo 50) |
| Biografía | 151 caracteres | ❌ Rechazar (máximo 150) |
| Fecha nacimiento | Fecha futura | ❌ Rechazar "Fecha no puede ser futura" |
| Fecha nacimiento | Hace 30 años | ⚠️ Advertencia "¿Estás seguro?" |
| Foto | Archivo > 10MB | ❌ Rechazar "Archivo muy grande" |
| Foto | Formato .txt | ❌ Rechazar "Solo imágenes" |

---

#### CP-PET-003: Editar Mascota Existente
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PET-003 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Mascotas |

**Precondiciones**:
- Usuario tiene al menos 1 mascota

**Pasos**:
1. Desde "Mis Mascotas", tocar botón "Editar" en una mascota
2. Modal se abre con datos precargados
3. Modificar biografía: `Biografía actualizada`
4. (NO modificar foto)
5. Tocar "Guardar"

**Resultado Esperado**:
- ✅ Backend: `PATCH /pets/:petId`
- ✅ Response status: 200 OK
- ✅ Modal se cierra
- ✅ Card de mascota muestra datos actualizados
- ✅ **IMPORTANTE**: Foto NO se borra (bug conocido, debe estar corregido)

**Validación Crítica**:
- 🔴 **Bug anterior**: Al editar sin cambiar foto, se borraba el avatar
- ✅ **Debe corregirse**: Si no se cambia foto, backend NO debe borrar la foto existente

---

#### CP-PET-004: Eliminar Mascota
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PET-004 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Mascotas |

**Precondiciones**:
- Usuario tiene al menos 2 mascotas (no puede eliminar la última)

**Pasos**:
1. Desde "Mis Mascotas", tocar botón "Eliminar" en una mascota
2. Dialog de confirmación aparece
3. Tocar "Confirmar eliminación"

**Resultado Esperado**:
- ✅ Backend: `DELETE /pets/:petId`
- ✅ Response status: 200 OK
- ✅ Mascota desaparece de la lista
- ✅ Mensaje de éxito: "Mascota eliminada"
- ✅ Contador de mascotas se actualiza

**Caso Extremo**:
- ⚠️ **Última mascota**: Backend debe rechazar (409 Conflict) o app debe prevenir
- ⚠️ **Mascota con publicaciones**: Verificar que no se borran las publicaciones (soft delete)

---

#### CP-PET-005: Ver Perfil de Mascota
| Campo | Detalle |
|-------|---------|
| **ID** | CP-PET-005 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Mascotas |

**Precondiciones**:
- Usuario autenticado
- Mascota existe (ID conocido)

**Pasos**:
1. Desde "Mis Mascotas" o desde publicación, tocar "Ver perfil" o avatar de mascota
2. Esperar carga del perfil

**Resultado Esperado**:
- ✅ Backend: `GET /pets/:petId`
- ✅ Response status: 200 OK
- ✅ Header muestra:
  - Avatar grande
  - Nombre, tipo, raza, edad, sexo, peso
  - Biografía
  - Chips de rasgos
  - Estadísticas: # Fotos, # Posts
- ✅ Tabs visibles: Fotos, Posts, Salud (si es propia)
- ✅ Botón "Editar" visible (si es mascota propia)

**Validaciones Backend**:
```json
GET /pets/1
Status: 200 OK
Response: {
  "id": 1,
  "name": "Max",
  "type": "dog",
  "breed": "Golden Retriever",
  "age": 4,
  "sex": "male",
  "weight": 30,
  "bio": "...",
  "traits": ["Friendly", "Playful"],
  "stats": {
    "photosCount": 10,
    "postsCount": 5
  },
  "isOwner": true
}
```

---

### 4.4 MÓDULO: PUBLICACIONES (POSTS)

#### CP-POST-001: Ver Feed de Publicaciones
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Publicaciones |

**Precondiciones**:
- Usuario autenticado
- Usuario sigue al menos a 1 persona con publicaciones

**Pasos**:
1. App inicia, Home Feed es la pantalla principal

**Resultado Esperado**:
- ✅ Backend: `GET /posts/feed?page=1&limit=10`
- ✅ Response status: 200 OK
- ✅ Lista de publicaciones se muestra
- ✅ Cada post muestra:
  - Avatar y nombre del autor
  - Carousel de imágenes (si múltiples) o video
  - Descripción (con "ver más" si es larga)
  - Mascotas etiquetadas
  - Botones: Like, Comentar, Compartir
  - Contador de likes y comentarios
  - Fecha relativa ("hace 2 horas")
- ✅ Pull-to-refresh funciona
- ✅ Scroll infinito carga más publicaciones

**Estado Vacío**:
- ✅ Si no sigue a nadie: EmptyState "Sin publicaciones" con botón "Crear primera publicación"

---

#### CP-POST-002: Crear Publicación con Imágenes
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-002 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Publicaciones |

**Precondiciones**:
- Usuario autenticado
- Usuario tiene al menos 1 mascota

**Pasos**:
1. Desde Home Feed, tocar botón flotante (+)
2. Pantalla "Crear Publicación" se abre
3. Tocar "Agregar medios"
4. Seleccionar 3 fotos de galería
5. Escribir descripción: "Día de paseo con mis amigos 🐶"
6. Seleccionar mascotas a etiquetar (checkbox de 2 mascotas)
7. Tocar botón "Publicar"

**Resultado Esperado**:
- ✅ Validación: Entre 1-5 imágenes (cumple ✅)
- ✅ Loading indicator durante upload
- ✅ Backend: `POST /posts` con `multipart/form-data`
- ✅ Imágenes se suben a Cloudinary
- ✅ Response status: 201 Created
- ✅ Usuario vuelve a Home Feed
- ✅ Publicación aparece en el feed
- ✅ Mensaje de éxito: "Publicación creada correctamente"

**Validaciones Backend**:
```json
POST /posts
Body (multipart/form-data):
  - description: "Día de paseo con mis amigos 🐶"
  - images: [File, File, File]
  - petIds: [1, 2]

Status: 201 Created
Response: {
  "id": 10,
  "description": "...",
  "images": [
    { "url": "https://cloudinary.../small.jpg", "size": "small" },
    { "url": "https://cloudinary.../medium.jpg", "size": "medium" }
  ],
  "pets": [...]
}
```

**Casos Extremos**:
| Escenario | Debe |
|-----------|------|
| Intentar publicar 0 imágenes | ❌ Botón "Publicar" deshabilitado |
| Intentar publicar 6 imágenes | ❌ Mostrar error "Máximo 5 imágenes" |
| Imagen > 10MB | ❌ Rechazar "Archivo muy grande" |
| Sin descripción (solo imágenes) | ✅ Permitir (descripción opcional) |
| Descripción > 500 caracteres | ❌ Rechazar o truncar |
| Sin conexión durante upload | ❌ Mostrar error, NO publicar |

---

#### CP-POST-003: Crear Publicación con Video
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-003 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Publicaciones |

**Pasos**:
1. Tocar botón (+) en Home Feed
2. Tocar "Agregar medios"
3. Seleccionar 1 video de galería (duración: 30 segundos)
4. Escribir descripción
5. Tocar "Publicar"

**Resultado Esperado**:
- ✅ Validación: Solo 1 video permitido (excluyente con imágenes)
- ✅ Backend: `POST /posts` con video
- ✅ Video se sube a Cloudinary
- ✅ Response status: 201 Created
- ✅ Publicación aparece en feed con video reproducible

**Casos Extremos**:
| Escenario | Debe |
|-----------|------|
| Video > 2 minutos | ❌ Rechazar "Máximo 2 minutos" |
| Video > 50MB | ❌ Rechazar "Archivo muy grande" |
| Intentar agregar imagen + video | ❌ Bloquear UI "Solo imágenes O video" |

---

#### CP-POST-004: Dar Like a Publicación
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-004 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Sistema Social |

**Precondiciones**:
- Usuario autenticado
- Publicación visible en feed

**Pasos**:
1. Tocar botón de "Me gusta" (corazón) en una publicación

**Resultado Esperado**:
- ✅ Botón cambia a color rojo inmediatamente (optimistic update)
- ✅ Contador de likes incrementa +1
- ✅ Animación de corazón (opcional)
- ✅ Backend: `POST /posts/:postId/like`
- ✅ Response status: 201 Created
- ✅ Notificación creada para el autor del post (backend)

**Pasos - Quitar Like**:
1. Tocar botón de "Me gusta" nuevamente

**Resultado Esperado - Quitar Like**:
- ✅ Botón vuelve a color gris
- ✅ Contador decrementa -1
- ✅ Backend: `DELETE /posts/:postId/like`
- ✅ Response status: 200 OK

**Casos Extremos**:
- ⚠️ **Like/unlike rápidamente**: Validar que última acción cuenta
- ⚠️ **Ya dio like**: Backend responde 409 Conflict, app maneja sin crash

---

#### CP-POST-005: Comentar Publicación
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-005 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Sistema Social |

**Precondiciones**:
- Usuario autenticado
- Publicación visible en feed

**Pasos**:
1. Tocar botón "Comentar" en una publicación
2. Modal de comentarios se abre desde abajo
3. Escribir comentario: "¡Qué hermoso! 🐶"
4. Tocar botón "Enviar"

**Resultado Esperado**:
- ✅ Backend: `POST /posts/:postId/comments`
- ✅ Response status: 201 Created
- ✅ Comentario aparece en la lista inmediatamente
- ✅ Campo de texto se limpia
- ✅ Contador de comentarios en el post incrementa +1
- ✅ Notificación creada para el autor del post

**Validaciones Backend**:
```json
POST /posts/10/comments
Body: {
  "content": "¡Qué hermoso! 🐶"
}
Status: 201 Created
Response: {
  "id": 50,
  "content": "¡Qué hermoso! 🐶",
  "user": { "id": 1, "firstName": "QA", ... },
  "createdAt": "2025-01-15T10:30:00Z"
}
```

**Casos Extremos**:
| Escenario | Debe |
|-----------|------|
| Comentario vacío | ❌ Botón "Enviar" deshabilitado |
| Comentario > 500 caracteres | ❌ Rechazar o truncar |
| Comentario solo con espacios | ❌ Rechazar "Campo requerido" |
| Comentario con emojis | ✅ Permitir |

---

#### CP-POST-006: Eliminar Publicación Propia
| Campo | Detalle |
|-------|---------|
| **ID** | CP-POST-006 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Publicaciones |

**Precondiciones**:
- Usuario autenticado
- Usuario tiene al menos 1 publicación propia

**Pasos**:
1. Desde perfil propio, tocar una publicación propia
2. Tocar menú (⋮) en la publicación
3. Tocar "Eliminar publicación"
4. Confirmación aparece
5. Tocar "Confirmar"

**Resultado Esperado**:
- ✅ Backend: `DELETE /posts/:postId`
- ✅ Response status: 200 OK
- ✅ Publicación desaparece del feed
- ✅ Contador de publicaciones del usuario decrementa -1
- ✅ Mensaje de éxito: "Publicación eliminada"

**Validación**:
- 🔴 Solo el autor puede eliminar su publicación
- ❌ Si otro usuario intenta eliminar: Backend responde 403 Forbidden

---

### 4.5 MÓDULO: HISTORIAS (STORIES)

#### CP-STORY-001: Ver Historias de Usuarios Seguidos
| Campo | Detalle |
|-------|---------|
| **ID** | CP-STORY-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Historias |

**Precondiciones**:
- Usuario autenticado
- Al menos 1 usuario seguido tiene historias activas (< 24h)

**Pasos**:
1. Desde Home Feed, ver barra superior de historias
2. Tocar avatar de un usuario con historia

**Resultado Esperado**:
- ✅ Backend: `GET /stories/:userId`
- ✅ Response status: 200 OK
- ✅ Visor de historia abre en fullscreen
- ✅ Historia se reproduce automáticamente
- ✅ Controles superiores visibles:
  - Avatar y nombre del autor
  - Barras de progreso (una por historia)
  - Botón de cerrar (X)
  - Tiempo de publicación
- ✅ Tap derecha: siguiente historia
- ✅ Tap izquierda: historia anterior
- ✅ Mantener tap: pausar
- ✅ Deslizar abajo: cerrar

**Validaciones Backend**:
```json
GET /stories/2
Status: 200 OK
Response: [
  {
    "id": 1,
    "mediaUrl": "https://cloudinary.../story1.jpg",
    "mediaType": "image",
    "createdAt": "2025-01-15T10:00:00Z",
    "expiresAt": "2025-01-16T10:00:00Z"
  }
]
```

---

#### CP-STORY-002: Crear Historia con Imagen
| Campo | Detalle |
|-------|---------|
| **ID** | CP-STORY-002 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Historias |

**Pasos**:
1. Desde Home Feed, tocar tu avatar en barra de historias (o botón +)
2. Seleccionar foto de galería o tomar foto
3. (Opcional) Agregar texto sobre la imagen
4. (Opcional) Cambiar color de fondo del texto
5. Tocar botón "Publicar historia"

**Resultado Esperado**:
- ✅ Backend: `POST /stories` con imagen
- ✅ Response status: 201 Created
- ✅ Historia se sube a Cloudinary
- ✅ Historia aparece en tu perfil con indicador "Tu historia"
- ✅ Historia visible para tus seguidores
- ✅ Historia expira automáticamente en 24 horas

**Validaciones Backend**:
```json
POST /stories
Body (multipart/form-data):
  - media: File (imagen)
  - text: "Texto opcional"
  - backgroundColor: "#FF5733"

Status: 201 Created
Response: {
  "id": 15,
  "mediaUrl": "https://cloudinary.../story15.jpg",
  "mediaType": "image",
  "expiresAt": "2025-01-16T10:00:00Z"
}
```

**Casos Extremos**:
| Escenario | Debe |
|-----------|------|
| Imagen > 10MB | ❌ Rechazar "Archivo muy grande" |
| Sin imagen | ❌ No permitir publicar (requerido) |
| Video > 30 segundos | ❌ Rechazar "Máximo 30 segundos" |

---

#### CP-STORY-003: Eliminar Historia Propia
| Campo | Detalle |
|-------|---------|
| **ID** | CP-STORY-003 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Historias |

**Precondiciones**:
- Usuario tiene al menos 1 historia propia activa

**Pasos**:
1. Ver tu propia historia
2. Tocar menú (⋮)
3. Tocar "Eliminar historia"
4. Confirmar

**Resultado Esperado**:
- ✅ Backend: `DELETE /stories/:storyId`
- ✅ Response status: 200 OK
- ✅ Historia desaparece inmediatamente
- ✅ Si es la última historia, avatar desaparece de la barra

---

### 4.6 MÓDULO: SISTEMA DE NOTIFICACIONES

#### CP-NOTIF-001: Ver Lista de Notificaciones
| Campo | Detalle |
|-------|---------|
| **ID** | CP-NOTIF-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Notificaciones |

**Precondiciones**:
- Usuario autenticado
- Usuario ha recibido al menos 3 notificaciones

**Pasos**:
1. Desde Home Feed, tocar ícono de campana (notificaciones)

**Resultado Esperado**:
- ✅ Backend: `GET /activities?page=1&limit=20`
- ✅ Response status: 200 OK
- ✅ Lista de notificaciones se muestra
- ✅ Cada notificación muestra:
  - Avatar del usuario que generó la notificación
  - Ícono según tipo (❤️ like, 💬 comentario, 👤 seguidor)
  - Texto descriptivo
  - Fecha relativa
  - Thumbnail de publicación (si aplica)
  - Indicador de no leída (punto azul o fondo)
- ✅ Filtros superiores visibles: Todas | No leídas | Me gusta | Comentarios | Seguidores
- ✅ Pull-to-refresh funciona

**Validaciones Backend**:
```json
GET /activities?page=1&limit=20
Status: 200 OK
Response: [
  {
    "id": 1,
    "type": "POST_LIKED",
    "user": { "id": 2, "firstName": "Usuario", "avatarUrl": "..." },
    "post": { "id": 10, "thumbnailUrl": "..." },
    "isRead": false,
    "createdAt": "2025-01-15T09:30:00Z"
  }
]
```

---

#### CP-NOTIF-002: Marcar Notificación como Leída
| Campo | Detalle |
|-------|---------|
| **ID** | CP-NOTIF-002 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Notificaciones |

**Pasos**:
1. Tocar una notificación de tipo "like" o "comentario"

**Resultado Esperado**:
- ✅ Backend: `PATCH /activities/:activityId` (marcar como leída)
- ✅ Response status: 200 OK
- ✅ Notificación cambia visualmente (fondo blanco, sin punto azul)
- ✅ Usuario es redirigido a la publicación correspondiente
- ✅ Contador de notificaciones no leídas decrementa -1

---

#### CP-NOTIF-003: Filtrar Notificaciones por Tipo
| Campo | Detalle |
|-------|---------|
| **ID** | CP-NOTIF-003 |
| **Prioridad** | 🟢 MEDIA |
| **Módulo** | Notificaciones |

**Pasos**:
1. En pantalla de notificaciones, tocar filtro "Me gusta"

**Resultado Esperado**:
- ✅ Backend: `GET /activities?type=POST_LIKED&page=1&limit=20`
- ✅ Response status: 200 OK
- ✅ Solo notificaciones de tipo "like" se muestran
- ✅ Filtro "Me gusta" aparece activo visualmente

**Casos a Probar**:
| Filtro | Tipos de Notificación Mostrados |
|--------|----------------------------------|
| Todas | POST_LIKED, POST_COMMENTED, USER_FOLLOWED |
| Me gusta | POST_LIKED |
| Comentarios | POST_COMMENTED |
| Seguidores | USER_FOLLOWED |
| No leídas | Todas con `isRead: false` |

---

### 4.7 MÓDULO: SERVICIOS MARKETPLACE

#### CP-SERVICE-001: Ver Mapa de Servicios
| Campo | Detalle |
|-------|---------|
| **ID** | CP-SERVICE-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Servicios |

**Precondiciones**:
- Usuario autenticado
- Existen servicios creados en la base de datos

**Pasos**:
1. Tocar tab "Mapa" en bottom navigation
2. Tab "Servicios" seleccionado por defecto

**Resultado Esperado**:
- ✅ Backend: `GET /services`
- ✅ Response status: 200 OK
- ✅ Mapa se muestra con marcadores de servicios
- ✅ Marcador de ubicación del usuario visible
- ✅ Controles de zoom funcionan
- ✅ Panel inferior de filtros visible
- ✅ Contador de servicios encontrados visible

**Validaciones Backend**:
```json
GET /services
Status: 200 OK
Response: [
  {
    "id": 1,
    "title": "Veterinaria Central",
    "category": "veterinary",
    "price": 50,
    "location": "Calle 123",
    "latitude": -34.603722,
    "longitude": -58.381592,
    "images": [...]
  }
]
```

**Caso Extremo**:
- ⚠️ **Carga lenta** (3-5 segundos): Verificar si es problema de backend (falta paginación/índices)

---

#### CP-SERVICE-002: Filtrar Servicios por Categoría
| Campo | Detalle |
|-------|---------|
| **ID** | CP-SERVICE-002 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Servicios |

**Pasos**:
1. En mapa de servicios, tocar panel de filtros
2. Seleccionar categoría "Veterinaria"
3. Tocar "Aplicar filtros"

**Resultado Esperado**:
- ✅ Backend: `GET /services?category=veterinary`
- ✅ Response status: 200 OK
- ✅ Solo marcadores de veterinarias visibles en mapa
- ✅ Contador actualizado: "5 servicios encontrados"

---

#### CP-SERVICE-003: Crear Nuevo Servicio
| Campo | Detalle |
|-------|---------|
| **ID** | CP-SERVICE-003 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Servicios |

**Pasos**:
1. Desde mapa de servicios, tocar botón flotante (+)
2. Completar formulario:
   - Título: "Mi Veterinaria"
   - Descripción: "Atención profesional para tu mascota"
   - Categoría: "Veterinaria"
   - Precio: 100
   - Ubicación: "Calle Falsa 123"
   - Teléfono: "+54 11 1234-5678"
   - Email: "contacto@miveterinaria.com"
3. Agregar 2 imágenes
4. Tocar "Guardar"

**Resultado Esperado**:
- ✅ Backend: `POST /services`
- ✅ Imágenes se suben a Cloudinary
- ✅ Response status: 201 Created
- ✅ Usuario vuelve al mapa
- ✅ Nuevo marcador aparece en el mapa
- ✅ Mensaje de éxito

**Casos Extremos**:
| Campo | Valor | Debe |
|-------|-------|------|
| Título | Vacío | ❌ Error "Campo requerido" |
| Precio | Negativo | ❌ Error "Precio inválido" |
| Email | Formato inválido | ❌ Error "Email inválido" |
| Imágenes | 6 imágenes | ❌ Error "Máximo 5 imágenes" |

---

### 4.8 MÓDULO: EVENTOS

#### CP-EVENT-001: Crear Nuevo Evento
| Campo | Detalle |
|-------|---------|
| **ID** | CP-EVENT-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Eventos |

**Pasos**:
1. Desde mapa, cambiar a tab "Eventos"
2. Tocar botón (+)
3. Completar formulario:
   - Título: "Encuentro de Mascotas"
   - Descripción: "Reunión mensual de dueños"
   - Ubicación: "Parque Central"
   - Fecha: Mañana
   - Hora: 15:00
   - Capacidad: 20
4. Agregar 1 imagen
5. Tocar "Guardar Evento"

**Resultado Esperado**:
- ✅ Backend: `POST /events`
- ✅ Response status: 201 Created
- ✅ Evento aparece en mapa
- ✅ Mensaje de éxito

**Validaciones Backend**:
```json
POST /events
Body: {
  "title": "Encuentro de Mascotas",
  "description": "...",
  "location": "Parque Central",
  "date": "2025-01-16T15:00:00Z",
  "capacity": 20
}
Status: 201 Created
```

**Casos Extremos**:
| Escenario | Debe |
|-----------|------|
| Fecha pasada | ❌ Error "Fecha debe ser futura" |
| Capacidad 0 | ❌ Error "Capacidad inválida" |
| Sin ubicación | ❌ Error "Campo requerido" |

---

### 4.9 MÓDULO: CHAT/MENSAJERÍA

#### CP-CHAT-001: Ver Lista de Conversaciones
| Campo | Detalle |
|-------|---------|
| **ID** | CP-CHAT-001 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Chat |

**Precondiciones**:
- Usuario tiene al menos 1 conversación activa

**Pasos**:
1. Tocar tab "Chats" en bottom navigation

**Resultado Esperado**:
- ✅ Backend: `GET /conversations`
- ✅ Response status: 200 OK
- ✅ Lista de conversaciones ordenada por última actividad
- ✅ Cada conversación muestra:
  - Avatar del otro usuario
  - Nombre
  - Último mensaje (preview)
  - Fecha/hora
  - Badge con contador de no leídos (si hay)

---

#### CP-CHAT-002: Enviar Mensaje
| Campo | Detalle |
|-------|---------|
| **ID** | CP-CHAT-002 |
| **Prioridad** | 🔴 CRÍTICA |
| **Módulo** | Chat |

**Pasos**:
1. Tocar una conversación
2. Escribir mensaje: "Hola, ¿cómo estás?"
3. Tocar botón "Enviar"

**Resultado Esperado**:
- ✅ Backend: `POST /messages`
- ✅ Response status: 201 Created
- ✅ Mensaje aparece en la conversación
- ✅ Campo de texto se limpia
- ✅ Scroll automático al último mensaje
- ✅ Estado de mensaje: ✓✓ (entregado)

---

### 4.10 MÓDULO: BLOQUEO Y REPORTES

#### CP-BLOCK-001: Bloquear Usuario
| Campo | Detalle |
|-------|---------|
| **ID** | CP-BLOCK-001 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Bloqueo |

**Pasos**:
1. Visitar perfil de otro usuario
2. Tocar menú (⋮)
3. Tocar "Bloquear usuario"
4. Confirmar acción

**Resultado Esperado**:
- ✅ Backend: `POST /user-blocks/:userId`
- ✅ Response status: 201 Created
- ✅ Usuario bloqueado desaparece del feed
- ✅ Conversación con usuario bloqueado desaparece
- ✅ No se pueden ver publicaciones del bloqueado

---

#### CP-REPORT-001: Reportar Publicación
| Campo | Detalle |
|-------|---------|
| **ID** | CP-REPORT-001 |
| **Prioridad** | 🟡 ALTA |
| **Módulo** | Reportes |

**Pasos**:
1. En una publicación, tocar menú (⋮)
2. Tocar "Denunciar publicación"
3. Seleccionar categoría: "Spam"
4. Agregar descripción (opcional)
5. Tocar "Enviar reporte"

**Resultado Esperado**:
- ✅ Backend: `POST /reports`
- ✅ Response status: 201 Created
- ✅ Modal se cierra
- ✅ Mensaje de éxito: "Reporte enviado"

---

## 5. MATRIZ DE PRUEBAS

### 5.1 Resumen por Módulo

| Módulo | Total Casos | Críticos | Altos | Medios | Estado |
|--------|-------------|----------|-------|--------|--------|
| Autenticación y Registro | 5 | 4 | 1 | 0 | ⬜ |
| Perfil de Usuario | 4 | 2 | 2 | 0 | ⬜ |
| Gestión de Mascotas | 5 | 3 | 2 | 0 | ⬜ |
| Publicaciones (Posts) | 6 | 4 | 2 | 0 | ⬜ |
| Historias (Stories) | 3 | 2 | 1 | 0 | ⬜ |
| Notificaciones | 3 | 1 | 1 | 1 | ⬜ |
| Servicios Marketplace | 3 | 2 | 1 | 0 | ⬜ |
| Eventos | 1 | 1 | 0 | 0 | ⬜ |
| Chat/Mensajería | 2 | 2 | 0 | 0 | ⬜ |
| Bloqueo y Reportes | 2 | 0 | 2 | 0 | ⬜ |
| **TOTAL** | **34** | **21** | **12** | **1** | **0/34** |

### 5.2 Plantilla de Seguimiento

```
Caso de Prueba: CP-AUTH-001
Fecha: __/__/____
Ejecutor: _________________
Dispositivo: Android / iOS
Versión App: _____________
Resultado: ✅ Aprobado / ❌ Fallido / 🚫 Bloqueado
Observaciones: ___________________________________________
Bug ID (si aplica): ______________________________________
```

---

## 6. CASOS EXTREMOS Y PRUEBAS DE ESTRÉS

### 6.1 Pruebas de Límites de Datos

#### CE-001: Campos de Texto con Límites
| Campo | Límite | Caso de Prueba |
|-------|--------|----------------|
| Nombre usuario | 50 chars | Ingresar 51 caracteres → Rechazar |
| Biografía | 150 chars | Ingresar 151 caracteres → Rechazar |
| Descripción post | 500 chars | Ingresar 501 caracteres → Rechazar |
| Comentario | 500 chars | Ingresar 501 caracteres → Rechazar |

#### CE-002: Caracteres Especiales
- ✅ Emojis en texto: Deben permitirse 🐶🐱❤️
- ✅ Caracteres Unicode: Deben permitirse (ñ, á, ü, etc.)
- ❌ Scripts HTML: `<script>alert('xss')</script>` → Sanitizar
- ❌ SQL Injection: `'; DROP TABLE users; --` → Sanitizar

#### CE-003: Archivos de Medios
| Escenario | Límite | Resultado Esperado |
|-----------|--------|-------------------|
| Imagen > 10MB | 10MB | ❌ Rechazar "Archivo muy grande" |
| Video > 50MB | 50MB | ❌ Rechazar "Archivo muy grande" |
| Video > 2 min | 2 min | ❌ Rechazar "Máximo 2 minutos" |
| Formato no soportado (.txt) | jpg/png/mp4 | ❌ Rechazar "Formato no soportado" |

### 6.2 Pruebas de Conectividad

#### CE-004: Sin Conexión a Internet
**Escenarios a probar**:
1. Login sin conexión → Mostrar error "Sin conexión"
2. Crear publicación sin conexión → Mostrar error, no publicar
3. Cargar feed sin conexión → Mostrar error
4. Enviar mensaje sin conexión → Mostrar indicador de espera

**Resultado esperado**:
- ❌ Nunca crash de la app
- ✅ Mensaje de error claro y útil
- ✅ Posibilidad de reintentar

#### CE-005: Pérdida de Conexión Durante Operación
**Escenarios**:
1. Perder conexión mientras se sube una publicación
2. Perder conexión durante login
3. Perder conexión mientras se envía mensaje

**Resultado esperado**:
- ✅ Operación se cancela o reintenta
- ✅ Mensaje de error: "Conexión perdida, intenta nuevamente"
- ❌ NO debe quedar en estado inconsistente

### 6.3 Pruebas de Concurrencia

#### CE-006: Múltiples Acciones Simultáneas
| Escenario | Acción | Resultado Esperado |
|-----------|--------|-------------------|
| Dar like rápidamente múltiples veces | Tocar botón like 5 veces seguidas | Solo cuenta última acción |
| Seguir/dejar de seguir rápidamente | Alternar 10 veces en 2 segundos | Solo cuenta última acción, sin crash |
| Enviar múltiples mensajes simultáneamente | Tocar "Enviar" 5 veces rápido | Todos los mensajes se envían (no duplicar) |

### 6.4 Pruebas de Sesión

#### CE-007: Token Expirado
**Pasos**:
1. Usuario autenticado
2. Esperar que token JWT expire (backend configurable, ej: 1 hora)
3. Intentar realizar acción (like, comentar, etc.)

**Resultado esperado**:
- ✅ Backend responde 401 Unauthorized
- ✅ App redirige a login automáticamente
- ✅ Mensaje: "Tu sesión ha expirado, inicia sesión nuevamente"

#### CE-008: Cerrar Sesión en Múltiples Dispositivos
**Pasos**:
1. Login en dispositivo A
2. Login en dispositivo B con misma cuenta
3. Cerrar sesión en dispositivo A
4. Intentar acción en dispositivo A

**Resultado esperado**:
- ✅ Dispositivo A redirige a login
- ✅ Dispositivo B sigue funcionando (si se permite sesiones múltiples)

### 6.5 Pruebas de Validaciones Backend

#### CE-009: Manipulación Directa de API
**Escenario**: Usuario malicioso intenta enviar peticiones directamente al backend saltándose validaciones del frontend

**Casos a probar**:
| Petición | Dato Malicioso | Backend Debe |
|----------|----------------|--------------|
| POST /posts | descripción: 1000 caracteres | ❌ 400 Bad Request |
| POST /pets | birthDate: fecha futura | ❌ 400 Bad Request |
| POST /posts/:id/like | Ya dio like | ❌ 409 Conflict |
| DELETE /posts/:id | Post de otro usuario | ❌ 403 Forbidden |
| PATCH /users/profile | email: formato inválido | ❌ 400 Bad Request |

**Herramienta recomendada**: Postman o curl para hacer peticiones directas

---

## 7. HERRAMIENTAS DE AUTOMATIZACIÓN

### 7.1 Testing Frontend (Flutter)

#### 7.1.1 Flutter Integration Tests
**Propósito**: Automatizar casos de prueba funcionales del frontend

**Configuración**:
```yaml
# pubspec.yaml
dev_dependencies:
  integration_test:
    sdk: flutter
  flutter_test:
    sdk: flutter
```

**Ejemplo de test automatizado** (referencia):
```dart
// test_driver/app_test.dart
void main() {
  IntegrationTestWidgetsFlutterBinding.ensureInitialized();

  group('Login Tests', () {
    testWidgets('CP-AUTH-001: Login con credenciales válidas', (tester) async {
      // Iniciar app
      await tester.pumpWidget(MyApp());

      // Ingresar credenciales
      await tester.enterText(find.byKey(Key('emailField')), 'qa.tester@petos.com');
      await tester.enterText(find.byKey(Key('passwordField')), 'QA_Test123!');

      // Tocar botón login
      await tester.tap(find.byKey(Key('loginButton')));
      await tester.pumpAndSettle();

      // Verificar navegación a Home Feed
      expect(find.byKey(Key('homeFeed')), findsOneWidget);
    });
  });
}
```

**Cobertura sugerida**:
- ✅ Flujo de login/registro completo
- ✅ Creación de publicación
- ✅ Interacciones sociales (like, comentar, seguir)
- ✅ Navegación entre pantallas principales

#### 7.1.2 Flutter Widget Tests
**Propósito**: Probar componentes individuales de UI

**Casos sugeridos**:
- Validaciones de formularios
- Comportamiento de botones
- Estados de loading/error

### 7.2 Testing Backend API

#### 7.2.1 Postman Collections
**Propósito**: Automatizar pruebas de API del backend

**Configuración**:
1. Crear colección "Petos API Tests"
2. Organizar por módulos (Auth, Posts, Users, etc.)
3. Agregar tests en cada request

**Ejemplo de test en Postman**:
```javascript
// POST /auth/login - Test
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has access_token", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property('access_token');
});

pm.test("Token is valid JWT", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.access_token).to.match(/^eyJ/);
});
```

**Colecciones sugeridas**:
- ✅ **Auth Flow**: Login, Register, Token refresh
- ✅ **Posts CRUD**: Create, Read, Update, Delete
- ✅ **Social Actions**: Like, Comment, Follow
- ✅ **Validations**: Edge cases, invalid data
- ✅ **Permissions**: Unauthorized access attempts

**Runner de Postman**:
- Ejecutar colección completa con `Newman` (CLI de Postman)
- Integrar en CI/CD para pruebas automáticas pre-deploy

#### 7.2.2 Bruno o Insomnia (Alternativas)
- Alternativas open-source a Postman
- Misma funcionalidad de testing de API

### 7.3 Testing de Performance

#### 7.3.1 Flutter DevTools
**Propósito**: Analizar rendimiento de la app

**Métricas a monitorear**:
- FPS (frames per second) - objetivo: 60 FPS
- Tiempo de carga de pantallas - objetivo: < 2 segundos
- Uso de memoria
- Rebuild de widgets innecesarios

#### 7.3.2 Lighthouse (Web - si aplica)
Si hay versión web de Petos:
- Performance score > 90
- Accessibility score > 90

### 7.4 Testing de Regresión Visual

#### 7.4.1 Percy o Chromatic (sugerido)
**Propósito**: Detectar cambios visuales no intencionales

**Cómo funciona**:
1. Captura screenshots de referencia (baseline)
2. En cada PR, captura nuevos screenshots
3. Compara pixel por pixel
4. Alerta si hay diferencias visuales

**Pantallas a incluir**:
- Login, Registro
- Home Feed
- Perfil de usuario
- Crear publicación
- Formularios (agregar mascota, editar perfil)

### 7.5 Testing de Accesibilidad

#### 7.5.1 Flutter Semantics Test
**Propósito**: Verificar que la app es accesible para screen readers

**Ejemplo**:
```dart
testWidgets('Botón de login tiene semantic label', (tester) async {
  await tester.pumpWidget(LoginView());

  final loginButton = find.byKey(Key('loginButton'));
  expect(tester.getSemantics(loginButton), matchesSemantics(
    label: 'Iniciar Sesión',
    isButton: true,
  ));
});
```

---

## 8. REPORTE DE BUGS

### 8.1 Formato de Reporte

**Plantilla estándar**:

```markdown
# BUG-001: [Título descriptivo del bug]

## 📋 Información General
- **ID**: BUG-001
- **Severidad**: 🔴 Crítica / 🟡 Alta / 🟢 Media / ⚪ Baja
- **Prioridad**: P1 (Urgente) / P2 (Alta) / P3 (Media) / P4 (Baja)
- **Módulo**: [Autenticación / Perfil / Posts / etc.]
- **Estado**: Abierto / En progreso / Resuelto / Cerrado
- **Reportado por**: [Nombre del QA]
- **Fecha**: [DD/MM/YYYY]
- **Versión de la app**: [1.0.0]
- **Dispositivo**: [Android 12 / iOS 16]

## 🐛 Descripción
Descripción clara y concisa del problema.

## 📝 Pasos para Reproducir
1. Abrir la app
2. Navegar a pantalla X
3. Tocar botón Y
4. Observar el error

## ✅ Resultado Esperado
Qué debería suceder correctamente.

## ❌ Resultado Actual
Qué sucede en realidad (el bug).

## 📸 Evidencia
- Screenshot: [Adjuntar imagen]
- Video: [Adjuntar video si aplica]
- Logs: [Adjuntar logs de consola si aplica]

## 🔄 Frecuencia
- ✅ Siempre reproducible (100%)
- ⚠️ Frecuente (>50%)
- 🔸 Ocasional (<50%)
- ⚪ Rara vez (<10%)

## 🌐 Entorno
- Backend: http://localhost:8080
- Usuario de prueba: qa.tester@petos.com
- Datos de prueba: [Especificar si aplica]

## 🔍 Información Adicional
Cualquier información relevante que ayude a reproducir o resolver el bug.
```

### 8.2 Clasificación de Severidad

| Severidad | Descripción | Ejemplo |
|-----------|-------------|---------|
| 🔴 **Crítica** | Bloquea funcionalidad core, app crash, pérdida de datos | Login no funciona, app crashea al crear post |
| 🟡 **Alta** | Afecta funcionalidad importante pero hay workaround | Like no funciona, pero se puede comentar |
| 🟢 **Media** | Afecta UX pero no bloquea funcionalidades | Animación incorrecta, texto mal alineado |
| ⚪ **Baja** | Problema cosmético o mejora sugerida | Color de botón no ideal, typo en texto |

### 8.3 Flujo de Manejo de Bugs

```
[Bug Reportado] → [Triaje] → [Asignado a Desarrollador]
                                       ↓
[QA Verifica Fix] ← [Desarrollador Corrige] ← [En Desarrollo]
       ↓
[Bug Cerrado] ✅
```

---

## 9. CHECKLIST FINAL DE CALIDAD

### 9.1 Pre-Release Checklist

Antes de cada lanzamiento, verificar:

#### ✅ Funcionalidades Core
- [ ] Login funciona correctamente
- [ ] Registro multi-paso completo funciona
- [ ] Crear publicación con imágenes funciona
- [ ] Crear publicación con video funciona
- [ ] Feed carga y muestra publicaciones
- [ ] Like, comentar, compartir funcionan
- [ ] Seguir/dejar de seguir funciona
- [ ] Crear/ver historias funciona
- [ ] Notificaciones se reciben correctamente
- [ ] Chat/mensajería funciona
- [ ] Crear/ver mascotas funciona
- [ ] Registros de salud funcionan
- [ ] Mapa de servicios carga correctamente
- [ ] Crear/editar servicios funciona
- [ ] Crear/editar eventos funciona

#### ✅ Validaciones y Seguridad
- [ ] Campos de formulario validan correctamente
- [ ] Backend rechaza datos inválidos
- [ ] Sesión expira correctamente
- [ ] Tokens JWT se manejan correctamente
- [ ] No hay XSS ni SQL Injection posible
- [ ] Usuarios bloqueados no pueden interactuar

#### ✅ UX y Navegación
- [ ] Todas las pantallas cargan en < 2 segundos
- [ ] Pull-to-refresh funciona en todas las listas
- [ ] Animaciones son fluidas (60 FPS)
- [ ] Botón back funciona correctamente
- [ ] Estados vacíos se muestran correctamente
- [ ] Loading indicators se muestran durante operaciones largas
- [ ] Mensajes de error son claros y útiles

#### ✅ Manejo de Errores
- [ ] Sin conexión: Muestra error claro
- [ ] Backend caído: Muestra error claro
- [ ] Token expirado: Redirige a login
- [ ] Operaciones fallidas: Permiten reintentar
- [ ] No hay crashes no controlados

#### ✅ Dispositivos y Plataformas
- [ ] Probado en Android (versión mínima: 8.0)
- [ ] Probado en iOS (versión mínima: 12.0)
- [ ] Probado en diferentes tamaños de pantalla
- [ ] Probado en orientación portrait y landscape (si aplica)

#### ✅ Performance
- [ ] App inicia en < 3 segundos
- [ ] Feed carga en < 2 segundos
- [ ] Imágenes se cargan progresivamente (caché funciona)
- [ ] No hay memory leaks evidentes
- [ ] Scroll es fluido sin lag

#### ✅ Accesibilidad
- [ ] Todos los botones tienen semantic labels
- [ ] Contraste de colores cumple WCAG AA
- [ ] Tamaño de elementos táctiles > 44x44 puntos
- [ ] Screen reader puede navegar la app

### 9.2 Sign-Off de Release

**Checklist de aprobación**:
```
Versión: ___________
Fecha: __/__/____

✅ Todos los casos de prueba críticos aprobados
✅ Bugs críticos resueltos (0 abiertos)
✅ Bugs altos resueltos o documentados
✅ Performance aceptable (< 2s carga pantallas)
✅ Sin crashes en testing manual extensivo
✅ Aprobado por Product Owner: _________________
✅ Aprobado por QA Lead: _____________________

🚀 RELEASE APROBADA PARA PRODUCCIÓN
```

---

## 10. ANEXOS

### 10.1 Comandos Útiles

**Flutter**:
```bash
# Ejecutar app en dispositivo
flutter run

# Ejecutar tests de integración
flutter test integration_test/app_test.dart

# Generar coverage report
flutter test --coverage

# Analizar código
flutter analyze

# Limpiar build
flutter clean
```

**Backend**:
```bash
# Iniciar servidor de desarrollo
cd petos-backend
yarn dev

# Ejecutar tests (cuando existan)
yarn test

# Verificar health endpoint
curl http://localhost:8080/health
```

### 10.2 URLs de Referencia

**Documentación del proyecto**:
- [Análisis Funcional](./Analisis%20Funcional.md)
- [Análisis de Diseño UI/UX](./Analisis_Diseno_UI_UX.md)
- [CLAUDE.md (Reglas de Desarrollo)](../CLAUDE.md)

**Herramientas**:
- Flutter: https://flutter.dev
- Postman: https://www.postman.com
- Percy (Visual testing): https://percy.io

### 10.3 Glosario

| Término | Definición |
|---------|------------|
| **Happy Path** | Flujo de uso normal sin errores |
| **Edge Case** | Caso extremo o límite de uso |
| **Regression** | Bug que reaparece después de haber sido corregido |
| **Smoke Test** | Prueba rápida de funcionalidades básicas |
| **Sanity Test** | Prueba rápida después de un cambio menor |
| **Flaky Test** | Test que a veces pasa y a veces falla |
| **Mock** | Simulación de datos o servicios para testing |

---

## CONCLUSIÓN

Este plan de calidad y pruebas proporciona una guía completa para asegurar que **Petos App** cumple con los estándares de calidad necesarios para su lanzamiento.

### Próximos Pasos Recomendados:

1. **Ejecutar todos los casos de prueba manuales** (34 casos totales)
2. **Reportar y trackear todos los bugs** encontrados
3. **Implementar tests automatizados** de casos críticos (Flutter Integration Tests)
4. **Crear colección de Postman** con tests de API
5. **Realizar UAT** con usuarios beta antes del lanzamiento
6. **Aprobar release** solo si 100% de casos críticos pasan

### Contacto

Para dudas o reporte de bugs:
- QA Lead: [Nombre]
- Email: [email]
- Herramienta de tracking: [Jira / Trello / GitHub Issues]

---

**Documento creado por**: Claude AI
**Última actualización**: Enero 2025
**Versión**: 1.0

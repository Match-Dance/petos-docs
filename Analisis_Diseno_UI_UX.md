# 🎨 ANÁLISIS COMPLETO DE DISEÑO UI/UX - PETOS APP

**Fecha de análisis**: Enero 2025
**Versión**: 1.0
**Estado del proyecto**: Pre-lanzamiento MVP

---

## 📋 TABLA DE CONTENIDOS

1. [Resumen Ejecutivo](#resumen-ejecutivo)
2. [Metodología de Análisis](#metodología-de-análisis)
3. [Paleta de Colores](#1-paleta-de-colores)
4. [Botones](#2-botones)
5. [Inputs y TextFields](#3-inputs-y-textfields)
6. [Cards y Sombras](#4-cards-y-sombras)
7. [Tipografía](#5-tipografía)
8. [Componentes Reutilizables](#6-componentes-reutilizables)
9. [Navegación](#7-navegación)
10. [Espaciado y Alineación](#8-espaciado-y-alineación)
11. [Animaciones y Transiciones](#9-animaciones-y-transiciones)
12. [Accesibilidad](#10-accesibilidad)
13. [Plan de Acción Priorizado](#plan-de-acción-priorizado)
14. [Checklist de Homogeneización](#checklist-de-homogeneización)
15. [Conclusión y Próximos Pasos](#conclusión-y-próximos-pasos)

---

## RESUMEN EJECUTIVO

### 🎯 Objetivo del Análisis

Evaluar el estado actual del diseño UI/UX de Petos para:
- ✅ Identificar inconsistencias visuales
- ✅ Detectar componentes que necesitan estandarización
- ✅ Proponer mejoras para lograr homogeneidad visual
- ✅ Asegurar buenas prácticas de diseño pet-friendly
- ✅ Mejorar usabilidad y accesibilidad

### 🎨 Filosofía de Diseño Objetivo (Estilo Pinterest/Moderno)

**Visión**: Lograr un estilo **limpio, moderno y minimalista** inspirado en aplicaciones como Pinterest, donde el contenido es protagonista sin distracciones visuales excesivas.

**Principios fundamentales**:
1. **Cards blancos con sombras sutiles** - Sin bordes de colores
2. **Uso controlado del gradiente** - Solo para CTAs principales (máximo 1 por pantalla)
3. **Iconos monocromáticos** - Paleta limitada (70% gris, 20% primario, 10% gradiente)
4. **Paleta de colores reducida** - Balance 80% blanco/gris/primario, 20% pet colors
5. **Sin fondos de colores en cards** - Excepto pet colors sutiles como acento
6. **Tipografía consistente** - Solo usar `AppTextStyles.*`
7. **Componentes reutilizables** - Centralizar estilos, evitar código custom

**Referencia visual**: Aplicaciones modernas de diseño como Pinterest, Notion, Linear - donde predomina el blanco, las sombras sutiles y la información clara sin saturación visual.

### 📊 Evaluación General

| Categoría | Puntuación | Estado |
|-----------|------------|--------|
| Paleta de Colores | 7/10 | ⚠️ Necesita ajustes |
| Botones | 8/10 | ✅ Bueno |
| Inputs/TextFields | 8/10 | ✅ Bueno |
| Cards y Sombras | 4/10 | 🔴 Crítico |
| Tipografía | 9/10 | ✅ Excelente |
| Componentes Reutilizables | 6/10 | ⚠️ Faltan componentes |
| Navegación | 6/10 | ⚠️ Problemas de stack profundo |
| Espaciado | 8/10 | ✅ Bueno |
| Animaciones | 7/10 | ✅ Bueno |
| Accesibilidad | 5/10 | ⚠️ Necesita mejora |
| **PROMEDIO GENERAL** | **6.8/10** | ⚠️ **Requiere mejoras** |

### 🚨 Hallazgos Críticos

1. **🔴 CRÍTICO**: No existe componente `AppCard` → Sombras inconsistentes en 15+ archivos
2. **🔴 CRÍTICO**: Múltiples definiciones de sombras contradictorias
3. **🟡 ALTA**: Gradiente sobreusado → Pierde impacto visual
4. **🟡 ALTA**: Faltan componentes clave (`AppDialog`, `AppBottomSheet`)
5. **🟡 ALTA**: Colores pet-friendly infrautilizados

### ✅ Fortalezas del Diseño Actual

1. ✅ Sistema de colores pet-friendly bien pensado
2. ✅ Tipografía (Roboto) perfecta para la app
3. ✅ Botones completamente redondos (pet-friendly)
4. ✅ Componentes base sólidos (AppButton, AppTextField, AppAvatar)
5. ✅ Sistema de espaciado consistente (AppDimensions)

---

## METODOLOGÍA DE ANÁLISIS

### Archivos Revisados

**Archivos de constantes:**
- `lib/shared/constants/app_colors.dart` - Paleta de colores
- `lib/shared/constants/app_dimensions.dart` - Espaciado y dimensiones
- `lib/shared/constants/app_text_styles.dart` - Tipografía

**Componentes reutilizables:**
- `lib/shared/widgets/atoms/app_button.dart`
- `lib/shared/widgets/atoms/app_text_field.dart`
- `lib/shared/widgets/atoms/app_dropdown.dart`
- `lib/shared/widgets/atoms/app_avatar.dart`
- `lib/shared/widgets/molecules/avatar_picker.dart`
- `lib/shared/widgets/molecules/media_picker_bottom_sheet.dart`
- `lib/shared/widgets/molecules/empty_state.dart`
- `lib/shared/widgets/atoms/app_media_picker.dart`

**Auditoría de código:**
- Búsqueda de `BoxShadow` en 15+ archivos
- Búsqueda de valores hardcodeados
- Análisis de uso de componentes vs código custom

**Documentos de referencia:**
- `CLAUDE.md` - Reglas de estilo visual actuales

### Criterios de Evaluación

Cada categoría se evalúa según:
- ✅ **10/10 - Excelente**: Sin problemas, listo para producción
- ✅ **8-9/10 - Bueno**: Pequeñas mejoras opcionales
- ⚠️ **6-7/10 - Aceptable**: Necesita ajustes moderados
- 🔴 **4-5/10 - Problemático**: Requiere corrección urgente
- 🔴 **0-3/10 - Crítico**: Inaceptable, debe corregirse YA

---

## 1. 🎨 PALETA DE COLORES

### Puntuación: 7/10 ⚠️

### 📂 Archivo: `lib/shared/constants/app_colors.dart`

### Paleta Actual

```dart
// Primary Colors - Calming Blue
static const Color primary = Color(0xFF219CD9);      // Azul medio
static const Color primaryLight = Color(0xFFB3E5FC); // Azul claro
static const Color primaryDark = Color(0xFF006DA4);  // Azul oscuro

// Secondary Colors - Warm Orange
static const Color secondary = Color(0xFFFF7043);      // Naranja vibrante
static const Color secondaryLight = Color(0xFFFFAB91);
static const Color secondaryDark = Color(0xFFE64A19);

// Accent Colors - Fresh Mint/Teal
static const Color accent = Color(0xFF4DB6AC);       // Menta/Verde azulado
static const Color accentLight = Color(0xFFB2DFDB);
static const Color accentDark = Color(0xFF00796B);

// Pet Themed Colors
static const Color petPaw = Color(0xFF8D6E63);       // Marrón (patas)
static const Color petNose = Color(0xFF4E342E);      // Marrón oscuro (nariz)
static const Color petFur = Color(0xFFEFEBE9);       // Beige (pelaje)
static const Color petEyes = Color(0xFF26B1DE);      // Azul (ojos)
static const Color petTreat = Color(0xFFF9CF58);     // Amarillo (premio)

// System Colors
static const Color success = Color(0xFF249689);      // Verde
static const Color error = Color(0xFFFF5963);        // Rojo/Rosa
static const Color warning = Color(0xFFF9CF58);      // Amarillo
static const Color info = Color(0xFF4DB6AC);         // Menta
```

### ✅ Fortalezas

1. **Paleta pet-friendly bien pensada**
   - Azul calmante (#219CD9) → Transmite confianza y tranquilidad
   - Naranja cálido (#FF7043) → Energía y alegría
   - Menta fresca (#4DB6AC) → Salud y bienestar

2. **Colores temáticos de mascotas**
   - `petPaw`, `petNose`, `petFur`, `petEyes`, `petTreat` → Excelente idea conceptual

3. **Sistema de colores completo**
   - Primary, Secondary, Accent bien definidos
   - System colors (success, error, warning, info)
   - Colores de texto (textPrimary, textSecondary, textTertiary)

4. **Neutrales limpios**
   - Grises azulados fríos → Coherente con el azul primary
   - Fondos: `background` (#F1F4F8), `surface` (#FFFFFF)

### ❌ Problemas Identificados

#### **PROBLEMA #1: Gradiente SOBREUSADO** 🔴

**Ubicación del gradiente:**
```dart
LinearGradient(
  begin: Alignment(-1.0, -0.5),  // ~120 grados
  end: Alignment(1.0, 0.5),
  colors: [AppColors.primary, AppColors.primaryDark],
)
```

**Dónde se usa actualmente:**
- ✅ AppButton (primary) → Correcto
- ⚠️ AppAvatar (borde) → Aceptable
- ❌ EmptyState (ícono) → Sobreuso
- ❌ Iconos de perfil → Sobreuso
- ❌ FloatingActionButton → Sobreuso
- ❌ Badges → Sobreuso

**Impacto negativo:**
- El gradiente pierde su efecto de "llamar la atención"
- La app se ve demasiado "colorida" y menos profesional
- Fatiga visual del usuario

**Solución propuesta:**

**Regla de Oro del Gradiente:**
```markdown
USAR gradiente SOLO en:
✅ Botón primario de CTA (1 por pantalla máximo)
✅ FloatingActionButton principal (solo si es la acción más importante)
✅ Bordes de avatares (AppAvatar) - ya funciona bien

NO USAR gradiente en:
❌ Botones secundarios → Usar color sólido primary
❌ Iconos pequeños → Usar color sólido primary
❌ Fondos de cards → Usar blanco
❌ Badges de notificación → Usar color sólido secondary
❌ EmptyState iconos → Usar color sólido primary
```

**Archivos a modificar:**
- `lib/shared/widgets/molecules/empty_state.dart` → Quitar gradiente del ícono
- `lib/features/auth/views/user_profile_view.dart` → Revisar iconos con gradiente
- Buscar todos los `LinearGradient` y evaluar si son necesarios

---

#### **PROBLEMA #2: Colores Pet-Friendly INFRAUTILIZADOS** ⚠️

**Colores definidos pero NO usados:**
```dart
static const Color petPaw = Color(0xFF8D6E63);    // ❌ NO se usa
static const Color petNose = Color(0xFF4E342E);   // ❌ NO se usa
static const Color petFur = Color(0xFFEFEBE9);    // ❌ NO se usa
```

**Oportunidad perdida:**
Estos colores podrían dar personalidad única a la app.

**Solución propuesta:**

**Dónde usar colores pet-friendly:**

| Color | Dónde Usar | Ejemplo |
|-------|------------|---------|
| `petPaw` (Marrón #8D6E63) | Iconos de patas decorativos, botones de mascotas | Icono de "Agregar Mascota", paw prints en fondos |
| `petFur` (Beige #EFEBE9) | Fondos suaves en secciones de mascotas | Fondo de tarjetas de perfil de mascota |
| `petNose` (Marrón oscuro) | Acentos en elementos de mascotas | Bordes de fotos de mascotas, iconos destacados |
| `secondary` (Naranja) | "Me gusta", CTAs secundarios, badges | Corazones de like, badges de notificaciones |
| `accent` (Menta) | Info de salud, tips, elementos educativos | Cards de consejos de salud, sección de veterinaria |

**Implementación:**
```dart
// Ejemplo: Card de perfil de mascota
Container(
  decoration: BoxDecoration(
    color: AppColors.petFur,  // ← Fondo beige suave
    borderRadius: BorderRadius.circular(AppDimensions.radiusM),
    border: Border.all(
      color: AppColors.petPaw,  // ← Borde marrón
      width: 2,
    ),
  ),
  child: // ... contenido
)

// Ejemplo: Botón de agregar mascota
AppButton(
  text: 'Agregar Mascota',
  type: AppButtonType.solid,
  color: AppColors.petPaw,  // ← Color marrón en lugar de primary
  icon: Icon(Icons.pets),
)
```

---

### 📋 Recomendaciones - Paleta de Colores

#### **Recomendación #1: Documentar uso correcto de colores**

Agregar a `CLAUDE.md`:

```markdown
### Guía de Uso de Colores

#### Primary (Azul #219CD9)
**Usar para:**
- ✅ Botones principales (solo si tiene gradiente: 1 por pantalla)
- ✅ Links y textos clickeables
- ✅ Tabs activos
- ✅ Progress indicators
- ✅ Iconos de acciones principales

**NO usar para:**
- ❌ Fondos grandes (muy llamativo)
- ❌ Texto largo (dificulta lectura)

#### Secondary (Naranja #FF7043)
**Usar para:**
- ✅ CTAs secundarios
- ✅ "Me gusta" / Favoritos
- ✅ Badges de notificaciones
- ✅ Elementos destacados

#### Accent (Menta #4DB6AC)
**Usar para:**
- ✅ Información de salud
- ✅ Tips y consejos
- ✅ Estados de éxito
- ✅ Elementos educativos

#### Pet Colors (Marrón, Beige)
**Usar para:**
- ✅ Secciones exclusivas de mascotas
- ✅ Fondos suaves (petFur)
- ✅ Iconos y decoraciones temáticas
```

#### **Recomendación #2: Crear paleta de gradientes**

```dart
// Agregar a app_colors.dart

class AppGradients {
  // Gradiente principal - USAR CON MODERACIÓN
  static const LinearGradient primary = LinearGradient(
    begin: Alignment(-1.0, -0.5),
    end: Alignment(1.0, 0.5),
    colors: [AppColors.primary, AppColors.primaryDark],
  );

  // Gradiente secundario - Para CTAs secundarios
  static const LinearGradient secondary = LinearGradient(
    begin: Alignment(-1.0, -0.5),
    end: Alignment(1.0, 0.5),
    colors: [AppColors.secondary, AppColors.secondaryDark],
  );

  // Gradiente pet-friendly - Para secciones de mascotas
  static const LinearGradient pet = LinearGradient(
    begin: Alignment(-1.0, -0.5),
    end: Alignment(1.0, 0.5),
    colors: [AppColors.petPaw, AppColors.petNose],
  );
}
```

---

## 2. 🔘 BOTONES

### Puntuación: 8/10 ✅

### 📂 Archivo: `lib/shared/widgets/atoms/app_button.dart`

### Estado Actual

**Componente**: `AppButton` completamente reutilizable

**Variantes disponibles:**
```dart
enum AppButtonType {
  primary,      // Con gradiente
  secondary,    // Color sólido secondary
  outline,      // Solo borde
  text,         // Sin fondo
  destructive,  // Rojo para acciones peligrosas
}

enum AppButtonSize {
  small,   // 32px altura
  medium,  // 44px altura
  large,   // 56px altura
}
```

**Características:**
- ✅ Bordes completamente redondos (`radiusCircle = 999`)
- ✅ Sombras aplicadas (primary, secondary, outline, destructive)
- ✅ Estados: `isLoading`, `isDisabled`
- ✅ Soporte para iconos
- ✅ Width personalizable

### ✅ Fortalezas

1. **Botones completamente redondos - PERFECTO para app pet-friendly** 🐾
   - Los botones redondos transmiten: Amigable, accesible, juguetón
   - Contraste vs botones cuadrados: Corporativo, rígido, formal

2. **Componente bien diseñado**
   - Todas las variantes necesarias
   - Estados manejados correctamente
   - Código reutilizable

3. **Sombras aplicadas correctamente**
   ```dart
   boxShadow: [
     BoxShadow(
       color: Colors.black.withValues(alpha: 0.12),
       blurRadius: 10,
       spreadRadius: 1,
       offset: const Offset(0, 4),
     ),
   ]
   ```

### ❌ Problemas Identificados

#### **PROBLEMA #1: Todos los botones primarios tienen gradiente**

**Código actual:**
```dart
case AppButtonType.primary:
  return Container(
    decoration: BoxDecoration(
      gradient: isEnabled ? const LinearGradient(...) : null,  // ← Siempre gradiente
```

**Por qué es problema:**
- En formularios largos con múltiples botones primarios, todos tienen gradiente
- Demasiado llamativo y cansador visualmente
- No hay opción para botón primario sin gradiente

**Ejemplo problemático:**
```dart
// Formulario de crear servicio con 2 botones primarios
AppButton(text: 'Guardar Borrador', type: AppButtonType.primary),  // ← Gradiente
AppButton(text: 'Publicar Servicio', type: AppButtonType.primary), // ← Gradiente
// Resultado: Ambos llaman demasiado la atención
```

**Solución:**
Crear nuevo tipo `AppButtonType.solid` (primary sin gradiente):

```dart
enum AppButtonType {
  primary,      // Con gradiente - SOLO para CTA principal
  solid,        // NUEVO - Color sólido primary - Para formularios
  secondary,
  outline,
  text,
  destructive,
}
```

---

#### **PROBLEMA #2: Tamaños no siempre se usan**

**Evidencia:**
Algunos lugares crean botones custom sin usar `AppButton`:
- Botón de mensaje en perfil (creado manualmente con Container + GestureDetector)
- Algunos FloatingActionButtons custom

**Impacto:**
- Inconsistencia visual
- Código duplicado

**Solución:**
- Auditoría completa buscando `ElevatedButton`, `OutlinedButton`, `TextButton` sin `AppButton`
- Migrar todos a usar `AppButton`

---

### 📋 Recomendaciones - Botones

#### **Recomendación #1: Crear AppButtonType.solid**

```dart
// En app_button.dart

case AppButtonType.solid:
  return ElevatedButton(
    onPressed: isEnabled ? onPressed : null,
    style: ElevatedButton.styleFrom(
      backgroundColor: isEnabled ? AppColors.primary : AppColors.greyMedium,
      foregroundColor: AppColors.onPrimary,
      elevation: 0,
      shadowColor: Colors.transparent,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(AppDimensions.radiusCircle),
      ),
      padding: EdgeInsets.zero,
    ),
    child: _buildButtonContent(),
  );
```

#### **Recomendación #2: Documentar cuándo usar cada tipo**

Agregar a `CLAUDE.md`:

```markdown
### Guía de Uso de Botones

#### AppButton - Cuándo usar cada tipo

**Primary (con gradiente)**
- ✅ **USAR**: CTA principal de la pantalla (1 por pantalla máximo)
- ✅ **USAR**: Acción de alta prioridad que requiere atención
- ✅ **Ejemplos**: "Publicar", "Crear", "Confirmar", "Pagar"
- ❌ **NO USAR**: Múltiples botones en un formulario
- ❌ **NO USAR**: Botones secundarios

**Solid (NUEVO - sin gradiente)**
- ✅ **USAR**: Botones principales en formularios con múltiples acciones
- ✅ **USAR**: Acciones importantes pero no críticas
- ✅ **Ejemplos**: "Guardar", "Agregar Mascota", "Editar Perfil"
- ✅ **Ventaja**: Menos llamativo que primary, pero sigue siendo importante

**Secondary**
- ✅ **USAR**: Acciones alternativas o complementarias
- ✅ **Ejemplos**: "Filtrar", "Ordenar", "Opciones"

**Outline**
- ✅ **USAR**: Cancelar, retroceder, descartar
- ✅ **USAR**: Acciones terciarias
- ✅ **Ejemplos**: "Cancelar", "Saltar", "Más tarde"

**Text**
- ✅ **USAR**: Links sutiles
- ✅ **USAR**: Acciones de baja prioridad
- ✅ **Ejemplos**: "Ver más", "Detalles", "Info"

**Destructive**
- ✅ **USAR**: Eliminar, bloquear, acciones peligrosas
- ✅ **SIEMPRE**: Con diálogo de confirmación
- ✅ **Ejemplos**: "Eliminar Mascota", "Bloquear Usuario", "Cerrar Cuenta"

#### Regla de Oro

✅ **CORRECTO**: Botones completamente redondos (`radiusCircle`)
- Transmite: Amigable, accesible, pet-friendly, moderno

❌ **INCORRECTO**: Botones cuadrados o muy poco redondeados
- Transmite: Corporativo, rígido, formal, frío

#### Ejemplo de Uso Correcto

```dart
// Pantalla con CTA principal
Column(
  children: [
    // ... contenido

    // CTA principal - CON gradiente
    AppButton(
      text: 'Publicar Historia',
      type: AppButtonType.primary,  // ← Único botón con gradiente
      size: AppButtonSize.large,
      onPressed: () => controller.publish(),
    ),

    SizedBox(height: 12),

    // Acción secundaria - SIN gradiente
    AppButton(
      text: 'Guardar Borrador',
      type: AppButtonType.solid,  // ← Color sólido
      size: AppButtonSize.medium,
      onPressed: () => controller.saveDraft(),
    ),

    SizedBox(height: 12),

    // Cancelar
    AppButton(
      text: 'Cancelar',
      type: AppButtonType.outline,
      size: AppButtonSize.medium,
      onPressed: () => Get.back(),
    ),
  ],
)
```
```

---

## 3. 📝 INPUTS Y TEXTFIELDS

### Puntuación: 8/10 ✅

### 📂 Archivo: `lib/shared/widgets/atoms/app_text_field.dart`

### Estado Actual

**Componente**: `AppTextField<T>` completamente reutilizable

**Tipos disponibles:**
```dart
enum AppTextFieldType {
  text,
  email,
  password,
  phone,
  number,
  multiline,
}
```

**Características:**
- ✅ BorderRadius medio (`radiusM = 12px`) - **PERFECTO**
- ✅ Sombras sutiles aplicadas
- ✅ Validación con `reactive_forms`
- ✅ Prefix/suffix icons
- ✅ Helper text, error messages
- ✅ Contador de caracteres (maxLength)
- ✅ Toggle password visibility

### ✅ Fortalezas

1. **BorderRadius medio (12px) - Equilibrio perfecto**
   - No muy cuadrado (rígido)
   - No muy redondo (parece botón)
   - **Resultado**: Profesional y amigable

2. **Sombra sutil**
   ```dart
   boxShadow: [
     BoxShadow(
       color: Colors.black.withValues(alpha: 0.05),
       blurRadius: 8,
       offset: Offset(0, 2),
     ),
   ]
   ```
   - Da profundidad sin ser intrusivo

3. **Integración con reactive_forms**
   - Validación automática
   - Mensajes de error personalizables
   - Estados touched/dirty bien manejados

4. **Manejo de estados**
   - Error state (borde rojo)
   - Focus state (borde primary)
   - Disabled state

### ❌ Problemas Identificados

#### **PROBLEMA #1: Todos los inputs tienen sombra**

**Por qué es problema:**
- En formularios largos (5+ campos), se ve sobrecargado visualmente
- Demasiadas sombras compiten por atención

**Ejemplo problemático:**
```dart
// Formulario de crear evento con 8 campos
Column(
  children: [
    AppTextField(formControlName: 'titulo'),      // ← Sombra
    AppTextField(formControlName: 'descripcion'), // ← Sombra
    AppTextField(formControlName: 'ubicacion'),   // ← Sombra
    AppTextField(formControlName: 'fecha'),       // ← Sombra
    AppTextField(formControlName: 'hora'),        // ← Sombra
    AppTextField(formControlName: 'capacidad'),   // ← Sombra
    // ... Demasiadas sombras juntas
  ],
)
```

**Solución:**
Crear variante `flat` sin sombra para formularios largos.

---

#### **PROBLEMA #2: Solo existe versión outline**

**Oportunidad:**
Material Design define 2 estilos principales:
- **Outline**: Borde visible, fondo transparente
- **Filled**: Sin borde, fondo de color

**Ventaja de tener ambas:**
- Mayor flexibilidad visual
- Diferenciación de contextos (formularios vs búsqueda vs filtros)

---

### 📋 Recomendaciones - Inputs

#### **Recomendación #1: Crear variantes de AppTextField**

```dart
enum AppTextFieldVariant {
  outlined,  // Default - Con sombra
  flat,      // Sin sombra - Para formularios largos
  filled,    // Con fondo de color
}

class AppTextField<T> extends StatefulWidget {
  final AppTextFieldVariant variant;

  const AppTextField({
    this.variant = AppTextFieldVariant.outlined,
    // ... otros parámetros
  });
}
```

**Implementación de variantes:**

```dart
// Variante FLAT (sin sombra)
if (widget.variant == AppTextFieldVariant.flat) {
  return Container(
    decoration: BoxDecoration(
      borderRadius: BorderRadius.circular(AppDimensions.radiusM),
      // SIN boxShadow
    ),
    child: ReactiveTextField(...),
  );
}

// Variante FILLED (con fondo)
if (widget.variant == AppTextFieldVariant.filled) {
  return ReactiveTextField(
    decoration: InputDecoration(
      filled: true,
      fillColor: AppColors.surfaceVariant,
      border: OutlineInputBorder(
        borderRadius: BorderRadius.circular(AppDimensions.radiusM),
        borderSide: BorderSide.none,  // Sin borde
      ),
      // ...
    ),
  );
}
```

#### **Recomendación #2: Documentar cuándo usar cada variante**

Agregar a `CLAUDE.md`:

```markdown
### Guía de Uso de Inputs

#### AppTextField - Cuándo usar cada variante

**Outlined (con sombra)** - DEFAULT
- ✅ **USAR**: Formularios simples (1-3 campos)
- ✅ **USAR**: Inputs destacados
- ✅ **USAR**: Búsqueda principal
- ✅ **Ejemplos**: Login, búsqueda en AppBar

**Flat (sin sombra)** - NUEVO
- ✅ **USAR**: Formularios largos (5+ campos)
- ✅ **USAR**: Múltiples inputs juntos
- ✅ **USAR**: Cuando ya hay muchas sombras en la pantalla
- ✅ **Ejemplos**: Crear evento, editar perfil, formularios complejos
- ✅ **Ventaja**: Menos sobrecarga visual

**Filled** - NUEVO
- ✅ **USAR**: Cuando el fondo de la pantalla ya tiene color
- ✅ **USAR**: Para diferenciación visual en contextos especiales
- ✅ **USAR**: Filtros y búsquedas secundarias
- ✅ **Ejemplos**: Barra de búsqueda en header, filtros en modals

#### Regla de Oro

✅ **CORRECTO**: BorderRadius medio (12px)
- Equilibrio entre profesional y amigable
- No muy cuadrado (rígido), no muy redondo (parece botón)

❌ **INCORRECTO**: Inputs cuadrados (4px)
- Muy rígido, poco amigable

❌ **INCORRECTO**: Inputs muy redondos (999px)
- Parece botón, confunde al usuario
```

---

## 4. 🃏 CARDS Y SOMBRAS

### Puntuación: 4/10 🔴 CRÍTICO

### 📂 Archivos afectados: 15+ archivos

### Estado Actual

**❌ NO EXISTE** componente `AppCard` reutilizable

**Resultado:**
- Cada card se crea manualmente con `Container`
- Sombras inconsistentes en toda la app
- Código duplicado en múltiples lugares

### 🔴 Problemas Críticos

#### **PROBLEMA #1: NO EXISTE AppCard**

**Archivos con cards custom (sin componente):**
```
✓ 15 archivos encontrados con BoxShadow:
  - map/widgets/service_card.dart
  - map/widgets/event_card.dart
  - map/views/create_event_view.dart
  - map/views/create_service_view.dart
  - map/widgets/event_details_panel.dart
  - map/widgets/service_details_view.dart
  - auth/views/user_profile_view.dart
  - auth/views/profile_view.dart
  - auth/views/following_view.dart
  - ... y 6 más
```

**Cada archivo tiene su propia implementación:**
```dart
// Ejemplo 1: service_card.dart
Container(
  decoration: BoxDecoration(
    borderRadius: BorderRadius.circular(12),
    boxShadow: [
      BoxShadow(
        color: Colors.grey.withOpacity(0.2),  // ← Diferente
        blurRadius: 8,
        offset: Offset(0, 2),
      ),
    ],
  ),
)

// Ejemplo 2: event_card.dart
Container(
  decoration: BoxDecoration(
    borderRadius: BorderRadius.circular(16),  // ← Diferente
    boxShadow: [
      BoxShadow(
        color: Colors.black.withOpacity(0.1),  // ← Diferente
        blurRadius: 10,  // ← Diferente
        offset: Offset(0, 4),  // ← Diferente
      ),
    ],
  ),
)
```

**Impacto:**
- Inconsistencia visual en toda la app
- Código duplicado (100+ líneas)
- Difícil de mantener

---

#### **PROBLEMA #2: MÚLTIPLES SOMBRAS CONTRADICTORIAS**

**Sombra #1 - CLAUDE.MD dice:**
```dart
boxShadow: [
  BoxShadow(
    color: const Color(0xFF808080).withValues(alpha: 0.25),
    blurRadius: 10,
    spreadRadius: 0,
    offset: const Offset(0, 3),
  ),
]
```

**Sombra #2 - AppButton usa:**
```dart
boxShadow: [
  BoxShadow(
    color: Colors.black.withValues(alpha: 0.12),  // ← DIFERENTE
    blurRadius: 10,
    spreadRadius: 1,  // ← DIFERENTE
    offset: const Offset(0, 4),  // ← DIFERENTE
  ),
]
```

**Sombra #3 - EmptyState usa:**
```dart
boxShadow: [
  BoxShadow(
    color: Colors.black.withValues(alpha: 0.05),  // ← DIFERENTE
    blurRadius: 15,  // ← DIFERENTE
    offset: const Offset(0, 2),  // ← DIFERENTE
  ),
]
```

**Sombra #4 - AppTextField usa:**
```dart
boxShadow: [
  BoxShadow(
    color: Colors.black.withValues(alpha: 0.05),
    blurRadius: 8,  // ← DIFERENTE
    offset: Offset(0, 2),
  ),
]
```

**Problema:**
- **4 definiciones diferentes** de sombra
- **CLAUDE.MD no se respeta** en el código
- **Resultado**: App visualmente inconsistente

---

### 📋 Recomendaciones - Cards y Sombras

#### **Recomendación #1: CREAR AppCard (PRIORIDAD CRÍTICA)** 🔥

**Archivo nuevo**: `lib/shared/widgets/atoms/app_card.dart`

```dart
import 'package:flutter/material.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_dimensions.dart';

enum AppCardElevation {
  none,   // Sin sombra
  low,    // Sombra sutil
  medium, // Sombra normal (DEFAULT)
  high,   // Sombra pronunciada
}

class AppCard extends StatelessWidget {
  final Widget child;
  final EdgeInsets? padding;
  final VoidCallback? onTap;
  final AppCardElevation elevation;
  final BorderRadius? borderRadius;
  final Color? backgroundColor;

  const AppCard({
    super.key,
    required this.child,
    this.padding = const EdgeInsets.all(AppDimensions.paddingM),
    this.onTap,
    this.elevation = AppCardElevation.medium,
    this.borderRadius,
    this.backgroundColor,
  });

  @override
  Widget build(BuildContext context) {
    final effectiveBorderRadius = borderRadius ??
        BorderRadius.circular(AppDimensions.radiusM);

    return Container(
      decoration: BoxDecoration(
        color: backgroundColor ?? AppColors.surface,
        borderRadius: effectiveBorderRadius,
        boxShadow: [_getShadow(elevation)],
      ),
      child: Material(
        color: Colors.transparent,
        borderRadius: effectiveBorderRadius,
        child: InkWell(
          onTap: onTap,
          borderRadius: effectiveBorderRadius,
          child: Padding(
            padding: padding!,
            child: child,
          ),
        ),
      ),
    );
  }

  /// Sombra unificada según elevación
  static BoxShadow _getShadow(AppCardElevation elevation) {
    switch (elevation) {
      case AppCardElevation.none:
        return const BoxShadow(color: Colors.transparent);

      case AppCardElevation.low:
        return BoxShadow(
          color: const Color(0xFF808080).withValues(alpha: 0.15),
          blurRadius: 6,
          spreadRadius: 0,
          offset: const Offset(0, 2),
        );

      case AppCardElevation.medium:  // ← USAR ESTE POR DEFECTO
        return BoxShadow(
          color: const Color(0xFF808080).withValues(alpha: 0.25),
          blurRadius: 10,
          spreadRadius: 0,
          offset: const Offset(0, 3),
        );

      case AppCardElevation.high:
        return BoxShadow(
          color: const Color(0xFF808080).withValues(alpha: 0.35),
          blurRadius: 15,
          spreadRadius: 0,
          offset: const Offset(0, 5),
        );
    }
  }
}
```

**Uso:**
```dart
// Simple
AppCard(
  child: Text('Contenido del card'),
)

// Con tap
AppCard(
  onTap: () => print('Tapped!'),
  child: Text('Card clickeable'),
)

// Con elevación personalizada
AppCard(
  elevation: AppCardElevation.low,
  padding: EdgeInsets.all(AppDimensions.paddingL),
  child: Column(
    children: [
      Text('Título'),
      Text('Contenido'),
    ],
  ),
)
```

---

#### **Recomendación #2: UNIFICAR SOMBRAS (PRIORIDAD CRÍTICA)** 🔥

**Crear**: `lib/shared/constants/app_shadows.dart`

```dart
import 'package:flutter/material.dart';

class AppShadows {
  /// Sombra para cards y containers
  /// Usar esta para TODOS los cards de la app
  static BoxShadow card({double elevation = 1.0}) {
    return BoxShadow(
      color: const Color(0xFF808080).withValues(alpha: 0.25 * elevation),
      blurRadius: 10 * elevation,
      spreadRadius: 0,
      offset: Offset(0, 3 * elevation),
    );
  }

  /// Sombra sutil para inputs y elementos pequeños
  static BoxShadow subtle = BoxShadow(
    color: const Color(0xFF808080).withValues(alpha: 0.15),
    blurRadius: 6,
    spreadRadius: 0,
    offset: const Offset(0, 2),
  );

  /// Sombra pronunciada para elementos flotantes
  static BoxShadow elevated = BoxShadow(
    color: const Color(0xFF808080).withValues(alpha: 0.35),
    blurRadius: 15,
    spreadRadius: 0,
    offset: const Offset(0, 5),
  );

  /// Sin sombra (para elementos planos)
  static BoxShadow none = const BoxShadow(
    color: Colors.transparent,
  );
}
```

**Actualizar todos los componentes:**
```dart
// AppButton
boxShadow: [AppShadows.card()],

// AppTextField
boxShadow: [AppShadows.subtle],

// EmptyState
boxShadow: [AppShadows.subtle],

// AppCard
boxShadow: [AppShadows.card(elevation: elevationValue)],
```

---

#### **Recomendación #3: Documentar reglas de sombras**

Actualizar en `CLAUDE.md`:

```markdown
### Sombras Estandarizadas

**UNA SOLA SOMBRA** por nivel de elevación.

#### Niveles de Elevación

**None** (Sin sombra):
- ✅ **Usar**: Elementos completamente planos
- ✅ **Ejemplos**: Dividers, decoraciones, fondos

**Low/Subtle** (Sombra sutil):
- ✅ **Usar**: Inputs, elementos pequeños, cards sutiles
- ✅ **Valores**: `alpha: 0.15, blur: 6, offset: (0,2)`
- ✅ **Ejemplos**: AppTextField, chips, badges

**Medium** (Sombra normal) - DEFAULT:
- ✅ **Usar**: Cards normales, la mayoría de contenedores
- ✅ **Valores**: `alpha: 0.25, blur: 10, offset: (0,3)`
- ✅ **Ejemplos**: AppCard, post cards, service cards, event cards

**High/Elevated** (Sombra pronunciada):
- ✅ **Usar**: Elementos flotantes, modals, elementos destacados
- ✅ **Valores**: `alpha: 0.35, blur: 15, offset: (0,5)`
- ✅ **Ejemplos**: FloatingActionButton, bottom sheets, dialogs

#### Regla de Oro

**SIEMPRE usar**:
- ✅ Color base: `Color(0xFF808080)` (gris neutro)
- ✅ SpreadRadius: `0` (sin expansión de sombra)
- ✅ Offset X: `0` (sombra solo hacia abajo, no lateral)

**NUNCA usar**:
- ❌ `Colors.black.withOpacity()` → Muy oscuro, poco natural
- ❌ Sombras de colores (amarillo, azul, rojo) → Solo para efectos especiales
- ❌ Diferentes valores de blur/spread arbitrarios → Rompe consistencia
- ❌ `Colors.grey.withOpacity()` → Poco predecible, usar Color(0xFF808080)

#### Componente AppShadows

Usar `AppShadows` para todas las sombras:

```dart
// Cards normales
boxShadow: [AppShadows.card()]

// Inputs y elementos sutiles
boxShadow: [AppShadows.subtle]

// Elementos flotantes
boxShadow: [AppShadows.elevated]

// Elementos planos
boxShadow: [AppShadows.none]
```
```

---

#### **Recomendación #4: MIGRAR 15+ archivos a AppCard**

**Plan de migración:**

**Archivos a migrar (Prioridad Alta):**
1. `map/widgets/service_card.dart` → Usar `AppCard`
2. `map/widgets/event_card.dart` → Usar `AppCard`
3. `features/pets/widgets/pet_card.dart` (si existe) → Usar `AppCard`
4. Todos los demás 12 archivos con `BoxShadow`

**Antes:**
```dart
// service_card.dart (Antes)
Container(
  decoration: BoxDecoration(
    color: Colors.white,
    borderRadius: BorderRadius.circular(12),
    boxShadow: [
      BoxShadow(
        color: Colors.grey.withOpacity(0.2),
        blurRadius: 8,
        offset: Offset(0, 2),
      ),
    ],
  ),
  child: Padding(
    padding: EdgeInsets.all(16),
    child: Column(
      children: [
        // contenido
      ],
    ),
  ),
)
```

**Después:**
```dart
// service_card.dart (Después)
AppCard(
  onTap: () => navigateToDetails(),
  child: Column(
    children: [
      // contenido (mismo)
    ],
  ),
)
```

**Beneficios:**
- ✅ Reduce ~30 líneas de código por archivo
- ✅ Sombras 100% consistentes
- ✅ Fácil de mantener (cambio centralizado)
- ✅ Mejor legibilidad

---

## 5. 📐 TIPOGRAFÍA

### Puntuación: 9/10 ✅ Excelente

### 📂 Archivo: `lib/shared/constants/app_text_styles.dart`

### Estado Actual

**Fuente principal**: **Roboto**

**Sistema completo de estilos:**
- Display (32px, 28px, 24px) - Bold
- Headline (22px, 20px, 18px) - Bold/Semi-bold
- Title (16px, 14px, 12px) - Semi-bold
- Body (16px, 14px, 12px) - Regular
- Label (14px, 12px, 10px) - Medium
- Button (16px, 14px, 12px) - Semi-bold
- Utility (caption, overline)

### ✅ Fortalezas

1. **Roboto - Fuente PERFECTA para app pet-friendly**
   - Legible, amigable, moderna
   - No muy formal (como Times) ni muy casual (como Comic Sans)
   - Gratis y bien soportada en Flutter

2. **Line-heights bien definidos**
   ```dart
   height: 1.5,  // Body - Legibilidad óptima
   height: 1.4,  // Title - Compacto pero legible
   height: 1.2,  // Button - Compacto
   ```

3. **Jerarquía clara**
   - Display → Headlines importantes
   - Headline → Títulos de secciones
   - Title → Subtítulos
   - Body → Texto normal
   - Label → Labels de inputs
   - Button → Texto de botones

4. **Pesos correctos**
   - 700 (Bold) → Display, Headline
   - 600 (Semi-bold) → Title, Button
   - 500 (Medium) → Label
   - 400 (Regular) → Body

### ⚠️ Oportunidad de Mejora

**Agregar fuente "display" más juguetona para headlines destacados**

**Propuesta**: Agregar **Poppins** o **Quicksand**

**Razón:**
- Más juguetona y pet-friendly
- Diferenciación visual para títulos importantes
- Contraste con Roboto (profesional) vs Poppins (juguetón)

**Dónde usar:**
- Título de bienvenida en onboarding
- Nombre de la app en splash screen
- Headlines de secciones destacadas
- Títulos de celebración (match, nuevo seguidor, etc.)

### 📋 Recomendaciones - Tipografía

#### **Recomendación #1: Agregar fuente Poppins**

**1. Descargar fuente:**
- https://fonts.google.com/specimen/Poppins

**2. Agregar a proyecto:**
```yaml
# pubspec.yaml
flutter:
  fonts:
    - family: Roboto
      fonts:
        - asset: assets/fonts/Roboto-Regular.ttf
        - asset: assets/fonts/Roboto-Medium.ttf
          weight: 500
        - asset: assets/fonts/Roboto-Bold.ttf
          weight: 700

    - family: Poppins  # ← NUEVO
      fonts:
        - asset: assets/fonts/Poppins-Regular.ttf
        - asset: assets/fonts/Poppins-SemiBold.ttf
          weight: 600
        - asset: assets/fonts/Poppins-Bold.ttf
          weight: 700
```

**3. Agregar estilos en `app_text_styles.dart`:**
```dart
// Display Styles PLAYFUL - Poppins Bold
static const TextStyle displayLargePlayful = TextStyle(
  fontFamily: 'Poppins',
  fontSize: 32,
  fontWeight: FontWeight.w700,
  color: AppColors.textPrimary,
  height: 1.2,
  letterSpacing: -0.5,  // ← Más ajustado, moderno
);

static const TextStyle displayMediumPlayful = TextStyle(
  fontFamily: 'Poppins',
  fontSize: 28,
  fontWeight: FontWeight.w700,
  color: AppColors.textPrimary,
  height: 1.25,
  letterSpacing: -0.5,
);

static const TextStyle displaySmallPlayful = TextStyle(
  fontFamily: 'Poppins',
  fontSize: 24,
  fontWeight: FontWeight.w700,
  color: AppColors.textPrimary,
  height: 1.3,
  letterSpacing: -0.3,
);
```

**4. Usar en contextos apropiados:**
```dart
// Splash screen
Text(
  'Petos',
  style: AppTextStyles.displayLargePlayful,  // ← Poppins
)

// Onboarding welcome
Text(
  '¡Bienvenido a Petos!',
  style: AppTextStyles.displayMediumPlayful,  // ← Poppins
)

// Match celebration
Text(
  '¡Match!',
  style: AppTextStyles.displaySmallPlayful,  // ← Poppins
)

// Títulos normales
Text(
  'Mis Mascotas',
  style: AppTextStyles.headlineMedium,  // ← Roboto (sin cambios)
)
```

---

#### **Recomendación #2: Documentar uso de tipografía**

Agregar a `CLAUDE.md`:

```markdown
### Guía de Tipografía

#### Fuentes

**Roboto** (Principal):
- ✅ **Usar**: Body, títulos normales, botones, labels, inputs
- ✅ **Razón**: Legible, profesional, amigable
- ✅ **Ejemplos**: Todo el contenido estándar de la app

**Poppins** (Display - NUEVO):
- ✅ **Usar**: Headlines destacados, títulos importantes, celebraciones
- ✅ **Razón**: Más juguetón, pet-friendly, crea diferenciación visual
- ✅ **Ejemplos**: Splash screen, onboarding, match, bienvenida

#### Jerarquía de Textos

**Display** (32-24px):
- ✅ Títulos muy grandes, splash, onboarding
- ✅ Usar Poppins para display destacados
- ✅ Usar Roboto para display normales

**Headline** (22-18px):
- ✅ Títulos de secciones, AppBar titles
- ✅ SIEMPRE Roboto

**Title** (16-12px):
- ✅ Subtítulos, nombres de cards
- ✅ SIEMPRE Roboto

**Body** (16-12px):
- ✅ Texto de contenido, descripciones
- ✅ SIEMPRE Roboto

**Label** (14-10px):
- ✅ Labels de inputs, hints, helpers
- ✅ SIEMPRE Roboto

**Button** (16-12px):
- ✅ Texto de botones
- ✅ SIEMPRE Roboto

#### Regla de Oro

✅ **CORRECTO**: Roboto para todo, Poppins solo para display destacados
❌ **INCORRECTO**: Mezclar fuentes en el mismo contexto
❌ **INCORRECTO**: Usar Poppins en body text (dificulta lectura)
```

---

## 6. 🔄 COMPONENTES REUTILIZABLES

### Puntuación: 6/10 ⚠️

### Auditoría Completa

### ✅ Componentes que EXISTEN (8 componentes)

| # | Componente | Archivo | Estado | Uso |
|---|------------|---------|--------|-----|
| 1 | `AppButton` | `atoms/app_button.dart` | ✅ Excelente | Usado consistentemente |
| 2 | `AppTextField` | `atoms/app_text_field.dart` | ✅ Bueno | Usado en formularios |
| 3 | `AppDropdown` | `atoms/app_dropdown.dart` | ✅ Bueno | Usado en formularios |
| 4 | `AppAvatar` | `atoms/app_avatar.dart` | ✅ Excelente | Usado en toda la app |
| 5 | `AvatarPicker` | `molecules/avatar_picker.dart` | ✅ Bueno | Formularios con avatar |
| 6 | `MediaPickerBottomSheet` | `molecules/media_picker_bottom_sheet.dart` | ✅ Bueno | Selección imagen/video |
| 7 | `EmptyState` | `molecules/empty_state.dart` | ✅ Excelente | 11 archivos migrados |
| 8 | `AppMediaPicker` | `atoms/app_media_picker.dart` | ✅ Bueno | Publicaciones, servicios |

**Total**: 8 componentes reutilizables

---

### ❌ Componentes que FALTAN (6 componentes críticos)

| # | Componente | Prioridad | Razón | Archivos Afectados |
|---|------------|-----------|-------|---------------------|
| 1 | **`AppCard`** | 🔴 CRÍTICA | Sombras inconsistentes en toda la app | 15+ archivos con BoxShadow custom |
| 2 | **`AppDialog`** | 🔥 ALTA | Estructura estándar existe en CLAUDE.MD pero no componentizada | 10+ dialogs custom |
| 3 | **`AppBottomSheet`** | 🟡 MEDIA | Múltiples bottom sheets con estilos diferentes | 8+ archivos |
| 4 | **`AppChip`** | 🟡 MEDIA | Tags, categorías, filtros se crean manualmente | 5+ lugares |
| 5 | **`AppBadge`** | 🟢 BAJA | Contadores, notificaciones sin estándar | 3+ lugares |
| 6 | **`AppListTile`** | 🟢 BAJA | Items de listas sin estándar | 10+ archivos |

**Total**: 6 componentes faltantes

---

### 📋 Plan de Creación de Componentes

#### **COMPONENTE #1: AppCard** 🔴 CRÍTICA

**Ya documentado en sección 4 (Cards y Sombras)**

Ver implementación completa arriba.

---

#### **COMPONENTE #2: AppDialog** 🔥 ALTA

**Problema actual:**
- Estructura estándar definida en CLAUDE.MD
- Pero cada dialog se crea manualmente
- Código duplicado en 10+ dialogs

**Solución:**

**Archivo nuevo**: `lib/shared/widgets/molecules/app_dialog.dart`

```dart
import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_dimensions.dart';
import 'package:petos/shared/constants/app_text_styles.dart';
import 'package:petos/shared/widgets/atoms/app_button.dart';

class AppDialog extends StatelessWidget {
  final String title;
  final Widget content;
  final String? confirmText;
  final String? cancelText;
  final VoidCallback? onConfirm;
  final VoidCallback? onCancel;
  final bool isLoading;
  final AppButtonType confirmButtonType;

  const AppDialog({
    super.key,
    required this.title,
    required this.content,
    this.confirmText,
    this.cancelText = 'Cancelar',
    this.onConfirm,
    this.onCancel,
    this.isLoading = false,
    this.confirmButtonType = AppButtonType.primary,
  });

  @override
  Widget build(BuildContext context) {
    return Dialog(
      backgroundColor: Colors.white,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(AppDimensions.radiusL),
      ),
      child: Container(
        constraints: BoxConstraints(
          maxHeight: MediaQuery.of(context).size.height * 0.85,
        ),
        decoration: const BoxDecoration(
          color: Colors.white,
          borderRadius: BorderRadius.all(
            Radius.circular(AppDimensions.radiusL),
          ),
        ),
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            // Header
            Padding(
              padding: const EdgeInsets.all(AppDimensions.paddingL),
              child: Text(
                title,
                style: AppTextStyles.headlineSmall.copyWith(
                  color: AppColors.textPrimary,
                  fontWeight: FontWeight.bold,
                ),
                textAlign: TextAlign.center,
              ),
            ),

            // Scrollable Content
            Flexible(
              child: SingleChildScrollView(
                padding: const EdgeInsets.symmetric(
                  horizontal: AppDimensions.paddingL,
                ),
                child: content,
              ),
            ),

            // Action buttons
            Padding(
              padding: const EdgeInsets.all(AppDimensions.paddingL),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.end,
                children: [
                  if (cancelText != null) ...[
                    AppButton(
                      text: cancelText!,
                      type: AppButtonType.outline,
                      size: AppButtonSize.medium,
                      onPressed: onCancel ?? () => Get.back(),
                    ),
                    const SizedBox(width: AppDimensions.spaceM),
                  ],
                  if (confirmText != null)
                    AppButton(
                      text: confirmText!,
                      type: confirmButtonType,
                      size: AppButtonSize.medium,
                      onPressed: onConfirm,
                      isLoading: isLoading,
                    ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }

  /// Muestra el dialog
  static Future<T?> show<T>({
    required String title,
    required Widget content,
    String? confirmText,
    String? cancelText = 'Cancelar',
    VoidCallback? onConfirm,
    VoidCallback? onCancel,
    AppButtonType confirmButtonType = AppButtonType.primary,
  }) {
    return Get.dialog<T>(
      AppDialog(
        title: title,
        content: content,
        confirmText: confirmText,
        cancelText: cancelText,
        onConfirm: onConfirm,
        onCancel: onCancel,
        confirmButtonType: confirmButtonType,
      ),
      barrierDismissible: false,
    );
  }

  /// Dialog de confirmación simple
  static Future<bool> confirm({
    required String title,
    required String message,
    String confirmText = 'Confirmar',
    String cancelText = 'Cancelar',
    AppButtonType confirmButtonType = AppButtonType.primary,
  }) async {
    final result = await show<bool>(
      title: title,
      content: Text(
        message,
        style: AppTextStyles.bodyMedium,
        textAlign: TextAlign.center,
      ),
      confirmText: confirmText,
      cancelText: cancelText,
      confirmButtonType: confirmButtonType,
      onConfirm: () => Get.back(result: true),
      onCancel: () => Get.back(result: false),
    );
    return result ?? false;
  }

  /// Dialog de confirmación destructiva
  static Future<bool> confirmDestructive({
    required String title,
    required String message,
    String confirmText = 'Eliminar',
    String cancelText = 'Cancelar',
  }) {
    return confirm(
      title: title,
      message: message,
      confirmText: confirmText,
      cancelText: cancelText,
      confirmButtonType: AppButtonType.destructive,
    );
  }
}
```

**Uso:**
```dart
// Dialog custom
AppDialog.show(
  title: 'Agregar Mascota',
  content: PetFormContent(),
  confirmText: 'Guardar',
  onConfirm: () => controller.savePet(),
);

// Confirmación simple
final confirmed = await AppDialog.confirm(
  title: 'Publicar Historia',
  message: '¿Estás seguro de que quieres publicar esta historia?',
);

if (confirmed) {
  // Publicar
}

// Confirmación destructiva
final confirmed = await AppDialog.confirmDestructive(
  title: 'Eliminar Mascota',
  message: '¿Estás seguro? Esta acción no se puede deshacer.',
  confirmText: 'Eliminar',
);
```

---

#### **COMPONENTE #3: AppBottomSheet** 🟡 MEDIA

**Archivo nuevo**: `lib/shared/widgets/molecules/app_bottom_sheet.dart`

```dart
import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_dimensions.dart';
import 'package:petos/shared/constants/app_text_styles.dart';

class AppBottomSheet extends StatelessWidget {
  final String? title;
  final Widget content;
  final double? height;
  final bool isDismissible;
  final bool showDragHandle;

  const AppBottomSheet({
    super.key,
    this.title,
    required this.content,
    this.height,
    this.isDismissible = true,
    this.showDragHandle = true,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      height: height,
      decoration: BoxDecoration(
        color: AppColors.surface,
        borderRadius: const BorderRadius.vertical(
          top: Radius.circular(AppDimensions.radiusL),
        ),
      ),
      child: SafeArea(
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            if (showDragHandle) ...[
              // Drag handle
              Container(
                margin: const EdgeInsets.only(
                  top: AppDimensions.paddingM,
                  bottom: AppDimensions.paddingS,
                ),
                width: 40,
                height: 4,
                decoration: BoxDecoration(
                  color: AppColors.outline.withValues(alpha: 0.3),
                  borderRadius: BorderRadius.circular(AppDimensions.radiusS),
                ),
              ),
            ],

            if (title != null) ...[
              // Título
              Padding(
                padding: const EdgeInsets.symmetric(
                  horizontal: AppDimensions.paddingL,
                  vertical: AppDimensions.paddingM,
                ),
                child: Text(
                  title!,
                  style: AppTextStyles.headlineSmall.copyWith(
                    fontWeight: FontWeight.bold,
                    color: AppColors.textPrimary,
                  ),
                ),
              ),
            ],

            // Contenido
            Flexible(
              child: content,
            ),
          ],
        ),
      ),
    );
  }

  /// Muestra el bottom sheet
  static Future<T?> show<T>({
    String? title,
    required Widget content,
    double? height,
    bool isDismissible = true,
    bool isScrollControlled = true,
    bool showDragHandle = true,
  }) {
    return Get.bottomSheet<T>(
      AppBottomSheet(
        title: title,
        content: content,
        height: height,
        isDismissible: isDismissible,
        showDragHandle: showDragHandle,
      ),
      backgroundColor: Colors.transparent,
      isDismissible: isDismissible,
      isScrollControlled: isScrollControlled,
    );
  }
}
```

**Uso:**
```dart
// Bottom sheet simple
AppBottomSheet.show(
  title: 'Filtros',
  content: FiltersContent(),
);

// Bottom sheet sin título
AppBottomSheet.show(
  content: OptionsListContent(),
  showDragHandle: true,
);

// Bottom sheet fullscreen
AppBottomSheet.show(
  title: 'Comentarios',
  content: CommentsListContent(),
  height: MediaQuery.of(context).size.height * 0.9,
);
```

---

#### **COMPONENTE #4: AppChip** 🟡 MEDIA

**Archivo nuevo**: `lib/shared/widgets/atoms/app_chip.dart`

```dart
import 'package:flutter/material.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_dimensions.dart';
import 'package:petos/shared/constants/app_text_styles.dart';

enum AppChipType {
  filled,    // Fondo de color, texto blanco
  outlined,  // Sin fondo, borde de color
  subtle,    // Fondo claro, texto de color
}

class AppChip extends StatelessWidget {
  final String label;
  final AppChipType type;
  final Color? color;
  final VoidCallback? onTap;
  final VoidCallback? onDelete;
  final Widget? icon;
  final bool isSelected;

  const AppChip({
    super.key,
    required this.label,
    this.type = AppChipType.filled,
    this.color,
    this.onTap,
    this.onDelete,
    this.icon,
    this.isSelected = false,
  });

  @override
  Widget build(BuildContext context) {
    final effectiveColor = color ?? AppColors.primary;

    return GestureDetector(
      onTap: onTap,
      child: Container(
        padding: EdgeInsets.symmetric(
          horizontal: onDelete != null
              ? AppDimensions.paddingS
              : AppDimensions.paddingM,
          vertical: AppDimensions.paddingS,
        ),
        decoration: _getDecoration(effectiveColor),
        child: Row(
          mainAxisSize: MainAxisSize.min,
          children: [
            if (icon != null) ...[
              icon!,
              const SizedBox(width: AppDimensions.spaceXS),
            ],
            Text(
              label,
              style: AppTextStyles.labelMedium.copyWith(
                color: _getTextColor(effectiveColor),
                fontWeight: FontWeight.w500,
              ),
            ),
            if (onDelete != null) ...[
              const SizedBox(width: AppDimensions.spaceXS),
              GestureDetector(
                onTap: onDelete,
                child: Icon(
                  Icons.close,
                  size: 16,
                  color: _getTextColor(effectiveColor),
                ),
              ),
            ],
          ],
        ),
      ),
    );
  }

  BoxDecoration _getDecoration(Color color) {
    switch (type) {
      case AppChipType.filled:
        return BoxDecoration(
          color: isSelected ? color : color.withValues(alpha: 0.9),
          borderRadius: BorderRadius.circular(AppDimensions.radiusCircle),
        );
      case AppChipType.outlined:
        return BoxDecoration(
          color: isSelected ? color.withValues(alpha: 0.1) : Colors.transparent,
          borderRadius: BorderRadius.circular(AppDimensions.radiusCircle),
          border: Border.all(
            color: color,
            width: 1.5,
          ),
        );
      case AppChipType.subtle:
        return BoxDecoration(
          color: color.withValues(alpha: 0.15),
          borderRadius: BorderRadius.circular(AppDimensions.radiusCircle),
        );
    }
  }

  Color _getTextColor(Color color) {
    switch (type) {
      case AppChipType.filled:
        return AppColors.onPrimary;
      case AppChipType.outlined:
      case AppChipType.subtle:
        return color;
    }
  }
}
```

**Uso:**
```dart
// Chip filled
AppChip(
  label: 'Perro',
  type: AppChipType.filled,
  color: AppColors.petPaw,
)

// Chip outlined
AppChip(
  label: 'Veterinaria',
  type: AppChipType.outlined,
  color: AppColors.accent,
  isSelected: true,
)

// Chip con delete
AppChip(
  label: 'Grooming',
  type: AppChipType.subtle,
  onDelete: () => removeFilter(),
)

// Chip con icono
AppChip(
  label: 'Premium',
  icon: Icon(Icons.star, size: 14, color: Colors.white),
  color: AppColors.secondary,
)
```

---

#### **COMPONENTE #5: AppBadge** 🟢 BAJA

**Archivo nuevo**: `lib/shared/widgets/atoms/app_badge.dart`

```dart
import 'package:flutter/material.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_text_styles.dart';

enum AppBadgeSize {
  small,   // 16x16
  medium,  // 20x20
  large,   // 24x24
}

class AppBadge extends StatelessWidget {
  final int count;
  final AppBadgeSize size;
  final Color? backgroundColor;
  final Color? textColor;

  const AppBadge({
    super.key,
    required this.count,
    this.size = AppBadgeSize.medium,
    this.backgroundColor,
    this.textColor,
  });

  @override
  Widget build(BuildContext context) {
    if (count <= 0) return const SizedBox.shrink();

    final dimension = _getDimension();
    final fontSize = _getFontSize();
    final displayCount = count > 99 ? '99+' : count.toString();

    return Container(
      width: dimension,
      height: dimension,
      decoration: BoxDecoration(
        color: backgroundColor ?? AppColors.error,
        shape: BoxShape.circle,
        boxShadow: [
          BoxShadow(
            color: Colors.black.withValues(alpha: 0.2),
            blurRadius: 4,
            offset: const Offset(0, 2),
          ),
        ],
      ),
      child: Center(
        child: Text(
          displayCount,
          style: AppTextStyles.labelSmall.copyWith(
            color: textColor ?? AppColors.onPrimary,
            fontSize: fontSize,
            fontWeight: FontWeight.w600,
            height: 1.0,
          ),
        ),
      ),
    );
  }

  double _getDimension() {
    switch (size) {
      case AppBadgeSize.small:
        return 16;
      case AppBadgeSize.medium:
        return 20;
      case AppBadgeSize.large:
        return 24;
    }
  }

  double _getFontSize() {
    switch (size) {
      case AppBadgeSize.small:
        return 9;
      case AppBadgeSize.medium:
        return 10;
      case AppBadgeSize.large:
        return 11;
    }
  }
}

/// Badge posicionado sobre un widget
class AppBadgePosition extends StatelessWidget {
  final Widget child;
  final int count;
  final AppBadgeSize size;
  final Color? backgroundColor;
  final Alignment alignment;

  const AppBadgePosition({
    super.key,
    required this.child,
    required this.count,
    this.size = AppBadgeSize.medium,
    this.backgroundColor,
    this.alignment = Alignment.topRight,
  });

  @override
  Widget build(BuildContext context) {
    return Stack(
      clipBehavior: Clip.none,
      children: [
        child,
        if (count > 0)
          Positioned(
            top: alignment == Alignment.topRight || alignment == Alignment.topLeft ? -4 : null,
            right: alignment == Alignment.topRight || alignment == Alignment.bottomRight ? -4 : null,
            bottom: alignment == Alignment.bottomRight || alignment == Alignment.bottomLeft ? -4 : null,
            left: alignment == Alignment.topLeft || alignment == Alignment.bottomLeft ? -4 : null,
            child: AppBadge(
              count: count,
              size: size,
              backgroundColor: backgroundColor,
            ),
          ),
      ],
    );
  }
}
```

**Uso:**
```dart
// Badge sobre icono
AppBadgePosition(
  count: 5,
  child: Icon(Icons.notifications),
)

// Badge sobre tab
AppBadgePosition(
  count: unreadMessages,
  child: Icon(Icons.chat),
  backgroundColor: AppColors.secondary,
)

// Badge solo
AppBadge(
  count: 12,
  size: AppBadgeSize.large,
)
```

---

#### **COMPONENTE #6: AppListTile** 🟢 BAJA

**Archivo nuevo**: `lib/shared/widgets/molecules/app_list_tile.dart`

```dart
import 'package:flutter/material.dart';
import 'package:petos/shared/constants/app_colors.dart';
import 'package:petos/shared/constants/app_dimensions.dart';
import 'package:petos/shared/constants/app_text_styles.dart';

class AppListTile extends StatelessWidget {
  final Widget? leading;
  final String title;
  final String? subtitle;
  final Widget? trailing;
  final VoidCallback? onTap;
  final Color? backgroundColor;
  final EdgeInsets? padding;
  final bool showDivider;

  const AppListTile({
    super.key,
    this.leading,
    required this.title,
    this.subtitle,
    this.trailing,
    this.onTap,
    this.backgroundColor,
    this.padding,
    this.showDivider = false,
  });

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Material(
          color: backgroundColor ?? Colors.transparent,
          child: InkWell(
            onTap: onTap,
            child: Padding(
              padding: padding ?? const EdgeInsets.symmetric(
                horizontal: AppDimensions.paddingL,
                vertical: AppDimensions.paddingM,
              ),
              child: Row(
                children: [
                  if (leading != null) ...[
                    leading!,
                    const SizedBox(width: AppDimensions.spaceM),
                  ],
                  Expanded(
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text(
                          title,
                          style: AppTextStyles.bodyMedium.copyWith(
                            fontWeight: FontWeight.w500,
                            color: AppColors.textPrimary,
                          ),
                        ),
                        if (subtitle != null) ...[
                          const SizedBox(height: 2),
                          Text(
                            subtitle!,
                            style: AppTextStyles.bodySmall.copyWith(
                              color: AppColors.textSecondary,
                            ),
                          ),
                        ],
                      ],
                    ),
                  ),
                  if (trailing != null) ...[
                    const SizedBox(width: AppDimensions.spaceM),
                    trailing!,
                  ],
                ],
              ),
            ),
          ),
        ),
        if (showDivider)
          Divider(
            height: 1,
            thickness: 1,
            color: AppColors.borderLight,
            indent: leading != null ? 72 : AppDimensions.paddingL,
          ),
      ],
    );
  }
}
```

**Uso:**
```dart
// List tile simple
AppListTile(
  title: 'Configuración',
  leading: Icon(Icons.settings),
  trailing: Icon(Icons.chevron_right),
  onTap: () => navigateToSettings(),
)

// Con subtitle
AppListTile(
  title: 'Notificaciones',
  subtitle: 'Gestiona tus notificaciones',
  leading: Icon(Icons.notifications),
  trailing: Switch(value: true),
  showDivider: true,
)

// Con avatar
AppListTile(
  title: 'Max',
  subtitle: 'Golden Retriever',
  leading: AppAvatar(
    imageUrl: pet.avatarUrl,
    size: AppAvatarSize.medium,
  ),
  onTap: () => navigateToPetProfile(),
)
```

---

### 📋 Resumen de Componentes

#### Componentes Existentes: 8
- ✅ AppButton
- ✅ AppTextField
- ✅ AppDropdown
- ✅ AppAvatar
- ✅ AvatarPicker
- ✅ MediaPickerBottomSheet
- ✅ EmptyState
- ✅ AppMediaPicker

#### Componentes a Crear: 6
- 🔴 AppCard (CRÍTICO)
- 🔥 AppDialog (ALTA)
- 🟡 AppBottomSheet (MEDIA)
- 🟡 AppChip (MEDIA)
- 🟢 AppBadge (BAJA)
- 🟢 AppListTile (BAJA)

**Total de componentes reutilizables objetivo**: 14 componentes

---

## 7. 🧭 NAVEGACIÓN

### Puntuación: 6/10 ⚠️

### Estado Actual

**Sistema de navegación**: GetX con rutas nombradas

**Problemas identificados** (ya documentados en `CLAUDE.md`):

1. **Deep Navigation Problem** (Stack profundo 6-7+ niveles)
   - Usuario puede quedar "atrapado" sin forma fácil de volver

2. **No hay botón "Home"** cuando stack > 3 niveles

3. **Navegación desde modals confusa**
   - Abrir perfil desde modal de comentarios crea confusión visual

4. **No se usa `preventDuplicates: true`**
   - Se pueden apilar el mismo perfil múltiples veces

### ✅ Tareas de Navegación Ya Documentadas

Ya existen **6 tareas detalladas** en `CLAUDE.md` sección "Fixes Críticos de Navegación":

**PRIORIDAD ALTA 🔥:**
1. Implementar botón "Home" (Escape Hatch)
2. Fix navegación desde Modal de Comentarios → Perfil Usuario

**PRIORIDAD MEDIA 🟡:**
3. Implementar Quick View Sheet para Mascotas (desde Matching)
4. Implementar Quick View Sheet para Usuarios (desde Seguidores/Siguiendo)
5. Usar Modals/FullscreenDialog cuando stack > 3 niveles
6. Agregar `preventDuplicates: true` en todas las navegaciones

### 📋 Recomendación

**No se requiere análisis adicional** - Ya está completamente documentado en `CLAUDE.md`.

---

## 8. 📏 ESPACIADO Y ALINEACIÓN

### Puntuación: 8/10 ✅

### 📂 Archivo: `lib/shared/constants/app_dimensions.dart`

### Estado Actual

**Sistema de espaciado**: Escala de 8px

```dart
// Spacing
static const double spaceXS = 4.0;
static const double spaceS = 8.0;
static const double spaceM = 16.0;
static const double spaceL = 24.0;
static const double spaceXL = 32.0;
static const double spaceXXL = 40.0;

// Padding (mismos valores)
// Margin (mismos valores)

// Border Radius
static const double radiusXS = 4.0;
static const double radiusS = 8.0;
static const double radiusM = 12.0;
static const double radiusL = 16.0;
static const double radiusXL = 24.0;
static const double radiusCircle = 999.0;
```

### ✅ Fortalezas

1. **Sistema de 8px bien implementado**
   - 4, 8, 16, 24, 32, 40 → Progresión consistente
   - Aliases útiles (xs, sm, md, lg, xl)

2. **Border radius bien definidos**
   - XS (4px) → Sutil
   - S (8px) → Pequeño
   - M (12px) → Medio (usado en inputs, cards)
   - L (16px) → Grande
   - XL (24px) → Muy grande
   - Circle (999px) → Completamente redondo (botones)

3. **Dimensiones específicas**
   - Button heights: 32, 44, 56
   - Icon sizes: 12, 16, 24, 32, 48
   - Avatar sizes: 32, 48, 64, 80, 96
   - Input heights: 40, 48, 56

### ⚠️ Problema Identificado

**No siempre se usan las constantes**

**Evidencia** (búsqueda en código):
- Algunos lugares usan valores hardcodeados:
  ```dart
  padding: EdgeInsets.all(16.0)  // ❌ Debería ser AppDimensions.paddingM
  SizedBox(height: 8.0)          // ❌ Debería ser AppDimensions.spaceS
  BorderRadius.circular(12)      // ❌ Debería ser AppDimensions.radiusM
  ```

**Impacto:**
- Dificulta cambios globales
- Rompe consistencia

### 📋 Recomendaciones - Espaciado

#### **Recomendación #1: Auditoría de valores hardcodeados**

**Buscar y reemplazar**:
```bash
# Buscar padding hardcodeado
grep -r "EdgeInsets.all(16" lib/

# Buscar SizedBox hardcodeado
grep -r "SizedBox(height: 8" lib/

# Buscar BorderRadius hardcodeado
grep -r "BorderRadius.circular(12)" lib/
```

**Reemplazar por constantes:**
```dart
// ❌ Antes
padding: EdgeInsets.all(16.0)
SizedBox(height: 8.0)
BorderRadius.circular(12)

// ✅ Después
padding: EdgeInsets.all(AppDimensions.paddingM)
SizedBox(height: AppDimensions.spaceS)
BorderRadius.circular(AppDimensions.radiusM)
```

---

#### **Recomendación #2: Documentar regla en CLAUDE.MD**

Agregar a `CLAUDE.md`:

```markdown
### Espaciado y Dimensiones

#### Regla de Oro

**SIEMPRE usar `AppDimensions`, NUNCA valores hardcodeados**

❌ **INCORRECTO**:
```dart
padding: EdgeInsets.all(16.0)
SizedBox(height: 8.0)
margin: EdgeInsets.symmetric(horizontal: 24.0)
BorderRadius.circular(12)
```

✅ **CORRECTO**:
```dart
padding: EdgeInsets.all(AppDimensions.paddingM)
SizedBox(height: AppDimensions.spaceS)
margin: EdgeInsets.symmetric(horizontal: AppDimensions.marginL)
BorderRadius.circular(AppDimensions.radiusM)
```

#### Razón

- ✅ Facilita cambios globales (cambiar 1 línea vs 100 archivos)
- ✅ Mantiene consistencia visual
- ✅ Mejora legibilidad del código

#### Escala de Espaciado

**Spacing** (4-8-16-24-32-40):
- XS (4px): Espacios mínimos
- S (8px): Espacios pequeños dentro de componentes
- M (16px): Espacios estándar entre elementos
- L (24px): Espacios grandes entre secciones
- XL (32px): Espacios muy grandes
- XXL (40px): Espacios máximos

**Border Radius**:
- XS (4px): Bordes sutiles
- S (8px): Bordes pequeños
- M (12px): Bordes medios (inputs, cards) - DEFAULT
- L (16px): Bordes grandes
- XL (24px): Bordes muy grandes
- Circle (999px): Completamente redondo (botones)
```

---

## 9. ✨ ANIMACIONES Y TRANSICIONES

### Puntuación: 7/10 ✅

### Estado Actual

**Animaciones existentes:**
- ✅ Transiciones de GetX (page routes)
- ✅ Loading states en botones (AppButton)
- ✅ Micro-interacciones en botones (InkWell, ripple)

### ⚠️ Oportunidad de Mejora

**Falta componente `AnimationUtils` centralizado**

Actualmente:
- Duraciones hardcodeadas (`Duration(milliseconds: 300)`)
- Curves hardcodeadas (`Curves.easeInOut`)
- Código duplicado

### 📋 Recomendaciones - Animaciones

#### **Recomendación #1: Crear AnimationUtils**

**Archivo nuevo**: `lib/shared/utils/animation_utils.dart`

```dart
import 'package:flutter/material.dart';

class AnimationUtils {
  // --- Durations ---
  static const Duration instant = Duration(milliseconds: 0);
  static const Duration fast = Duration(milliseconds: 150);
  static const Duration normal = Duration(milliseconds: 300);
  static const Duration slow = Duration(milliseconds: 500);
  static const Duration verySlow = Duration(milliseconds: 800);

  // --- Curves ---
  static const Curve defaultCurve = Curves.easeInOut;
  static const Curve smoothCurve = Curves.decelerate;
  static const Curve sharpCurve = Curves.easeOut;
  static const Curve bouncyCurve = Curves.elasticOut;
  static const Curve overshootCurve = Curves.easeOutBack;

  // --- Helper Methods ---

  /// Fade in widget
  static Widget fadeIn({
    required Widget child,
    Duration? duration,
    Curve? curve,
  }) {
    return TweenAnimationBuilder<double>(
      tween: Tween(begin: 0.0, end: 1.0),
      duration: duration ?? normal,
      curve: curve ?? defaultCurve,
      builder: (context, value, child) {
        return Opacity(
          opacity: value,
          child: child,
        );
      },
      child: child,
    );
  }

  /// Scale in widget
  static Widget scaleIn({
    required Widget child,
    Duration? duration,
    Curve? curve,
  }) {
    return TweenAnimationBuilder<double>(
      tween: Tween(begin: 0.8, end: 1.0),
      duration: duration ?? normal,
      curve: curve ?? overshootCurve,
      builder: (context, value, child) {
        return Transform.scale(
          scale: value,
          child: child,
        );
      },
      child: child,
    );
  }

  /// Slide in from bottom
  static Widget slideInFromBottom({
    required Widget child,
    Duration? duration,
    Curve? curve,
    double offset = 50.0,
  }) {
    return TweenAnimationBuilder<double>(
      tween: Tween(begin: offset, end: 0.0),
      duration: duration ?? normal,
      curve: curve ?? smoothCurve,
      builder: (context, value, child) {
        return Transform.translate(
          offset: Offset(0, value),
          child: child,
        );
      },
      child: child,
    );
  }

  /// Delayed animation wrapper
  static Widget delayed({
    required Widget child,
    required Duration delay,
  }) {
    return TweenAnimationBuilder<double>(
      tween: Tween(begin: 0.0, end: 1.0),
      duration: delay,
      builder: (context, value, child) {
        return value == 1.0 ? child! : const SizedBox.shrink();
      },
      child: child,
    );
  }
}
```

**Uso:**
```dart
// Fade in
AnimationUtils.fadeIn(
  child: Text('Hello'),
)

// Scale in con bounce
AnimationUtils.scaleIn(
  child: AppButton(text: 'Click'),
  curve: AnimationUtils.bouncyCurve,
)

// Slide in from bottom
AnimationUtils.slideInFromBottom(
  child: AppCard(child: Text('Card')),
  duration: AnimationUtils.slow,
)

// Delayed animation
AnimationUtils.delayed(
  delay: AnimationUtils.normal,
  child: AnimationUtils.fadeIn(child: Text('Appears later')),
)
```

---

#### **Recomendación #2: Documentar en CLAUDE.MD**

```markdown
### Animaciones y Transiciones

#### AnimationUtils

**SIEMPRE usar `AnimationUtils`, NUNCA valores hardcodeados**

❌ **INCORRECTO**:
```dart
Duration(milliseconds: 300)
Curves.easeInOut
```

✅ **CORRECTO**:
```dart
AnimationUtils.normal
AnimationUtils.defaultCurve
```

#### Duraciones

- `instant` (0ms): Sin animación
- `fast` (150ms): Animaciones rápidas (hover, ripple)
- `normal` (300ms): Animaciones estándar (DEFAULT)
- `slow` (500ms): Animaciones lentas (transitions, reveals)
- `verySlow` (800ms): Animaciones muy lentas (splashes, onboarding)

#### Curves

- `defaultCurve`: easeInOut - Uso general
- `smoothCurve`: decelerate - Entradas suaves
- `sharpCurve`: easeOut - Salidas rápidas
- `bouncyCurve`: elasticOut - Efectos juguetones (pet-friendly)
- `overshootCurve`: easeOutBack - Micro-interacciones destacadas

#### Helpers

**fadeIn**: Fade in suave
**scaleIn**: Scale in con bounce opcional
**slideInFromBottom**: Slide desde abajo
**delayed**: Delay antes de mostrar
```

---

## 10. ♿ ACCESIBILIDAD

### Puntuación: 5/10 ⚠️

### Problemas Identificados

#### **PROBLEMA #1: Falta `Semantics` en componentes** ⚠️

**Componentes sin labels semánticos:**
- AppButton → Sin `Semantics`
- AppAvatar → Sin `Semantics(label: ...)`
- AppCard → Sin `Semantics`
- Iconos decorativos sin `ExcludeSemantics`

**Impacto:**
- Screen readers (TalkBack, VoiceOver) no funcionan correctamente
- Usuarios con discapacidad visual no pueden usar la app

---

#### **PROBLEMA #2: Contrastes de color** ⚠️

**Posibles problemas de contraste:**
- `textSecondary` (#546E7A) sobre `background` (#F1F4F8) → Verificar contraste
- `textTertiary` (#90A4AE) sobre `surface` (#FFFFFF) → Puede no cumplir WCAG AA

**WCAG Requirements:**
- Texto normal (< 18px): Contraste mínimo 4.5:1
- Texto grande (>= 18px): Contraste mínimo 3:1

---

#### **PROBLEMA #3: Tamaños de toque** ⚠️

**Área mínima recomendada**: 44x44 px

**Posibles violaciones:**
- Botones small (32px altura) → Menor a 44px
- Iconos pequeños sin padding suficiente
- Chips muy pequeños

---

### 📋 Recomendaciones - Accesibilidad

#### **Recomendación #1: Agregar Semantics a componentes**

**AppButton:**
```dart
// En app_button.dart
@override
Widget build(BuildContext context) {
  return Semantics(
    button: true,
    enabled: isEnabled,
    label: text,
    onTap: isEnabled ? onPressed : null,
    child: Container(
      // ... implementación actual
    ),
  );
}
```

**AppAvatar:**
```dart
// En app_avatar.dart
@override
Widget build(BuildContext context) {
  return Semantics(
    label: 'Avatar de ${name ?? "usuario"}',
    image: imageUrl != null,
    child: Container(
      // ... implementación actual
    ),
  );
}
```

**Iconos decorativos:**
```dart
// Iconos puramente decorativos
ExcludeSemantics(
  child: Icon(Icons.decorative_icon),
)
```

---

#### **Recomendación #2: Verificar contrastes**

**Herramientas:**
- https://webaim.org/resources/contrastchecker/
- https://colorable.jxnblk.com/

**Verificar:**
```dart
// textSecondary sobre background
textSecondary: #546E7A
background: #F1F4F8
// Verificar contraste

// textTertiary sobre surface
textTertiary: #90A4AE
surface: #FFFFFF
// Verificar contraste
```

**Ajustar si necesario:**
```dart
// Si no cumple WCAG AA, oscurecer textSecondary
static const Color textSecondary = Color(0xFF455A64); // Más oscuro
```

---

#### **Recomendación #3: Asegurar tamaños de toque**

**AppButton small:**
```dart
// Asegurar mínimo 44px
static const double buttonHeightS = 44.0;  // Cambiar de 32 a 44
```

**Iconos pequeños:**
```dart
// Agregar padding para alcanzar 44x44
Padding(
  padding: EdgeInsets.all(12),  // 16 + 12*2 = 40, aproximado a 44
  child: Icon(Icons.small_icon, size: 16),
)
```

---

#### **Recomendación #4: Documentar en CLAUDE.MD**

```markdown
### Accesibilidad

#### Checklist de Accesibilidad

**Texto**:
- ✅ Contraste mínimo 4.5:1 para texto normal (< 18px)
- ✅ Contraste mínimo 3:1 para texto grande (>= 18px)
- ✅ Usar `Semantics` con labels descriptivos en todos los componentes interactivos
- ✅ Tamaños de fuente mínimos: Body 14px, Label 12px

**Interacción**:
- ✅ Área de toque mínima: 44x44 px
- ✅ Feedback visual en todos los botones/links (InkWell, ripple)
- ✅ Estados de foco visibles para navegación por teclado
- ✅ Indicadores de carga accesibles (Semantics con "Cargando...")

**Imágenes**:
- ✅ `Semantics(label: ...)` en avatares, iconos informativos
- ✅ `ExcludeSemantics` en iconos puramente decorativos
- ✅ Descripciones de imágenes importantes

**Formularios**:
- ✅ Labels claros para screen readers
- ✅ Mensajes de error descriptivos y específicos
- ✅ Ayudas contextuales (helperText)
- ✅ Indicadores de campos requeridos

**Colores**:
- ✅ NUNCA usar solo color para transmitir información (agregar iconos, texto)
- ✅ Verificar contrastes con herramientas WCAG
- ✅ Modo oscuro accesible

#### Herramientas

- https://webaim.org/resources/contrastchecker/ - Verificar contrastes
- https://colorable.jxnblk.com/ - Paleta accesible
- Flutter DevTools → Inspector → "Enable Semantics" - Testing
```

---

## PLAN DE ACCIÓN PRIORIZADO

### Estimación de Tiempo Total: 25-30 horas

---

### **FASE 1 - CRÍTICO** 🔴 (Hacer YA)

**Tiempo estimado**: 7-9 horas

#### **1.1 Crear componente `AppCard`** ⏱️ 3-4 horas

**Prioridad**: 🔴 CRÍTICA

**Tareas**:
- [x] Crear `lib/shared/widgets/atoms/app_card.dart`
- [ ] Implementar 4 niveles de elevación (none, low, medium, high)
- [ ] Agregar soporte para onTap, padding, borderRadius
- [ ] Migrar 15+ archivos a usar AppCard:
  - [ ] `map/widgets/service_card.dart`
  - [ ] `map/widgets/event_card.dart`
  - [ ] `features/pets/widgets/pet_card.dart` (si existe)
  - [ ] Otros 12 archivos con BoxShadow
- [ ] Testing manual

**Beneficio**:
- ✅ Sombras 100% consistentes
- ✅ Reduce ~500 líneas de código duplicado
- ✅ Facilita mantenimiento futuro

---

#### **1.2 Unificar sombras en toda la app** ⏱️ 2 horas

**Prioridad**: 🔴 CRÍTICA

**Tareas**:
- [ ] Crear `lib/shared/constants/app_shadows.dart`
- [ ] Definir 4 niveles de sombra (none, subtle, card, elevated)
- [ ] Actualizar componentes existentes:
  - [ ] AppButton → `AppShadows.card()`
  - [ ] AppTextField → `AppShadows.subtle`
  - [ ] EmptyState → `AppShadows.subtle`
  - [ ] AppCard → `AppShadows.card(elevation: ...)`
- [ ] Actualizar CLAUDE.MD con reglas de sombras
- [ ] Testing manual

**Beneficio**:
- ✅ UNA sola fuente de verdad para sombras
- ✅ Fácil de cambiar globalmente

---

#### **1.3 Reducir uso de gradiente** ⏱️ 2-3 horas

**Prioridad**: 🔴 CRÍTICA

**Tareas**:
- [ ] Crear `AppButtonType.solid` (primary sin gradiente)
- [ ] Actualizar botones en formularios a usar `solid`:
  - [ ] Formularios de servicios
  - [ ] Formularios de eventos
  - [ ] Formularios de mascotas
  - [ ] Dialogs con múltiples botones
- [ ] Quitar gradiente de EmptyState iconos
- [ ] Reservar gradiente SOLO para CTAs principales
- [ ] Actualizar CLAUDE.MD con reglas de gradiente
- [ ] Testing manual

**Beneficio**:
- ✅ Gradiente recupera su impacto visual
- ✅ App menos sobrecargada visualmente

---

### **FASE 2 - ALTA PRIORIDAD** 🔥 (Hacer después de Fase 1)

**Tiempo estimado**: 8-10 horas

#### **2.1 Crear componente `AppDialog`** ⏱️ 2 horas

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Crear `lib/shared/widgets/molecules/app_dialog.dart`
- [ ] Implementar variantes:
  - [ ] Custom dialog
  - [ ] Confirm dialog
  - [ ] Destructive confirm dialog
- [ ] Migrar 10+ dialogs existentes
- [ ] Testing manual

---

#### **2.2 Crear variantes de AppTextField** ⏱️ 1-2 horas

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Agregar enum `AppTextFieldVariant`
- [ ] Implementar variante `flat` (sin sombra)
- [ ] Implementar variante `filled` (con fondo)
- [ ] Actualizar formularios largos a usar `flat`
- [ ] Actualizar CLAUDE.MD con guía de uso
- [ ] Testing manual

---

#### **2.3 Usar colores pet-friendly** ⏱️ 1 hora

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Aplicar `petPaw` (marrón) en botones de mascotas
- [ ] Aplicar `petFur` (beige) en fondos de cards de mascotas
- [ ] Aplicar `secondary` (naranja) en "me gusta" y badges
- [ ] Aplicar `accent` (menta) en info de salud
- [ ] Actualizar CLAUDE.MD con guía de colores

---

#### **2.4 Crear componente `AppBottomSheet`** ⏱️ 2 horas

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Crear `lib/shared/widgets/molecules/app_bottom_sheet.dart`
- [ ] Implementar drag handle, título opcional
- [ ] Migrar 8+ bottom sheets existentes
- [ ] Testing manual

---

#### **2.5 Agregar fuente Poppins** ⏱️ 1 hora

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Descargar fuente Poppins
- [ ] Agregar a `pubspec.yaml`
- [ ] Crear estilos `displayLargePlayful`, etc.
- [ ] Usar en splash screen, onboarding, títulos destacados
- [ ] Testing manual

---

#### **2.6 Crear `lib/shared/constants/app_shadows.dart`** ⏱️ 1 hora

**Prioridad**: 🔥 ALTA

**Tareas**:
- [ ] Ya cubierto en Fase 1.2

---

### **FASE 3 - MEDIA PRIORIDAD** 🟡 (Hacer después de Fase 2)

**Tiempo estimado**: 6-8 horas

#### **3.1 Crear componente `AppChip`** ⏱️ 1 hora

**Tareas**:
- [ ] Crear `lib/shared/widgets/atoms/app_chip.dart`
- [ ] Implementar variantes: filled, outlined, subtle
- [ ] Usar en tags, filtros, categorías
- [ ] Testing manual

---

#### **3.2 Crear componente `AppBadge`** ⏱️ 1 hora

**Tareas**:
- [ ] Crear `lib/shared/widgets/atoms/app_badge.dart`
- [ ] Implementar 3 tamaños (small, medium, large)
- [ ] Crear `AppBadgePosition` wrapper
- [ ] Usar en notificaciones, counters
- [ ] Testing manual

---

#### **3.3 Mejorar accesibilidad** ⏱️ 3-4 horas

**Tareas**:
- [ ] Agregar `Semantics` a AppButton
- [ ] Agregar `Semantics` a AppAvatar
- [ ] Agregar `Semantics` a AppCard
- [ ] Agregar `ExcludeSemantics` a iconos decorativos
- [ ] Verificar contrastes de color con herramientas WCAG
- [ ] Ajustar colores si necesario
- [ ] Asegurar tamaños de toque mínimos (44x44)
- [ ] Testing con screen reader (TalkBack/VoiceOver)

---

#### **3.4 Crear `AnimationUtils`** ⏱️ 1 hora

**Tareas**:
- [ ] Crear `lib/shared/utils/animation_utils.dart`
- [ ] Definir duraciones (instant, fast, normal, slow, verySlow)
- [ ] Definir curves (default, smooth, sharp, bouncy, overshoot)
- [ ] Crear helpers (fadeIn, scaleIn, slideInFromBottom, delayed)
- [ ] Actualizar CLAUDE.MD con guía de animaciones

---

### **FASE 4 - BAJA PRIORIDAD** 🟢 (Mejoras futuras)

**Tiempo estimado**: 4-5 horas

#### **4.1 Auditoría de valores hardcodeados** ⏱️ 2-3 horas

**Tareas**:
- [ ] Buscar `EdgeInsets.all(16` en código → Reemplazar por `AppDimensions.paddingM`
- [ ] Buscar `SizedBox(height: 8` → Reemplazar por `AppDimensions.spaceS`
- [ ] Buscar `BorderRadius.circular(12)` → Reemplazar por `AppDimensions.radiusM`
- [ ] Buscar `Duration(milliseconds: 300)` → Reemplazar por `AnimationUtils.normal`
- [ ] Testing manual

---

#### **4.2 Crear componente `AppListTile`** ⏱️ 1-2 horas

**Tareas**:
- [ ] Crear `lib/shared/widgets/molecules/app_list_tile.dart`
- [ ] Migrar items de listas en 10+ archivos
- [ ] Testing manual

---

#### **4.3 Documentar todo en CLAUDE.MD** ⏱️ 2 horas

**Tareas**:
- [ ] Reglas de gradiente
- [ ] Reglas de sombras
- [ ] Guía de uso de AppButton (cada tipo)
- [ ] Guía de uso de AppTextField (cada variante)
- [ ] Guía de uso de colores
- [ ] Guía de tipografía
- [ ] Guía de espaciado
- [ ] Guía de animaciones
- [ ] Checklist de accesibilidad

---

## CHECKLIST DE HOMOGENEIZACIÓN

### **Componentes Reutilizables**

#### Existentes (8):
- [x] AppButton ✅
- [x] AppTextField ✅
- [x] AppDropdown ✅
- [x] AppAvatar ✅
- [x] AvatarPicker ✅
- [x] MediaPickerBottomSheet ✅
- [x] EmptyState ✅
- [x] AppMediaPicker ✅

#### A Crear (6):
- [ ] AppCard 🔴 **CRÍTICO**
- [ ] AppDialog 🔥 **NECESARIO**
- [ ] AppBottomSheet 🟡 **RECOMENDADO**
- [ ] AppChip 🟡 **RECOMENDADO**
- [ ] AppBadge 🟢 **OPCIONAL**
- [ ] AppListTile 🟢 **OPCIONAL**

**Total objetivo**: 14 componentes

---

### **Estándares Visuales**

#### Sombras:
- [ ] Crear AppShadows 🔴 **CRÍTICO**
- [ ] Unificar 4 niveles (none, subtle, card, elevated) 🔴 **CRÍTICO**
- [ ] Migrar todos los componentes 🔴 **CRÍTICO**

#### Gradientes:
- [ ] Reducir uso de gradiente 🔴 **CRÍTICO**
- [ ] Crear AppButtonType.solid 🔴 **CRÍTICO**
- [ ] Reservar gradiente solo para CTAs 🔴 **CRÍTICO**

#### Colores:
- [ ] Usar colores pet-friendly 🔥 **RECOMENDADO**
- [ ] Documentar guía de colores 🔥 **RECOMENDADO**
- [ ] Verificar contrastes WCAG 🟡 **OPCIONAL**

#### Tipografía:
- [ ] Agregar fuente Poppins 🔥 **RECOMENDADO**
- [ ] Usar en headlines destacados 🔥 **RECOMENDADO**

#### Espaciado:
- [ ] Auditoría de valores hardcodeados 🟢 **OPCIONAL**
- [ ] Reemplazar por AppDimensions 🟢 **OPCIONAL**

#### Animaciones:
- [ ] Crear AnimationUtils 🟡 **RECOMENDADO**
- [ ] Documentar duraciones y curves 🟡 **RECOMENDADO**

#### Accesibilidad:
- [ ] Agregar Semantics a componentes 🟡 **RECOMENDADO**
- [ ] Verificar contrastes 🟡 **RECOMENDADO**
- [ ] Asegurar tamaños de toque 🟡 **RECOMENDADO**

---

### **Documentación**

- [ ] Reglas de gradiente en CLAUDE.MD 🔥
- [ ] Reglas de sombras en CLAUDE.MD 🔥
- [ ] Guía de botones en CLAUDE.MD 🔥
- [ ] Guía de inputs en CLAUDE.MD 🔥
- [ ] Guía de colores en CLAUDE.MD 🔥
- [ ] Guía de tipografía en CLAUDE.MD 🟡
- [ ] Guía de espaciado en CLAUDE.MD 🟡
- [ ] Guía de animaciones en CLAUDE.MD 🟡
- [ ] Checklist de accesibilidad en CLAUDE.MD 🟡

---

## CONCLUSIÓN Y PRÓXIMOS PASOS

### 📊 Estado Actual del Diseño

**Petos tiene una base sólida** con:
- ✅ Sistema de colores pet-friendly bien pensado
- ✅ Tipografía perfecta (Roboto)
- ✅ Componentes base sólidos (8 componentes)
- ✅ Botones completamente redondos (pet-friendly)
- ✅ Sistema de espaciado consistente

**PERO necesita**:
- 🔴 **CRÍTICO**: Crear AppCard y unificar sombras (inconsistencia visual grave)
- 🔴 **CRÍTICO**: Reducir uso de gradiente (sobrecarga visual)
- 🔥 **IMPORTANTE**: Crear componentes faltantes (AppDialog, AppBottomSheet)
- 🟡 **MEJORA**: Usar colores pet-friendly correctamente
- 🟡 **MEJORA**: Mejorar accesibilidad

---

### 🎯 Objetivo Final

**App visualmente cohesiva, profesional y pet-friendly** con:
- ✅ 14 componentes reutilizables
- ✅ Sombras 100% consistentes
- ✅ Gradiente usado con moderación
- ✅ Colores pet-friendly bien aprovechados
- ✅ Accesibilidad mejorada (Semantics, contrastes, touch targets)
- ✅ Documentación completa en CLAUDE.MD

---

### ⏱️ Estimación de Tiempo

| Fase | Tiempo | Prioridad |
|------|--------|-----------|
| Fase 1 - Crítico | 7-9 horas | 🔴 Hacer YA |
| Fase 2 - Alta | 8-10 horas | 🔥 Siguiente |
| Fase 3 - Media | 6-8 horas | 🟡 Después |
| Fase 4 - Baja | 4-5 horas | 🟢 Futuro |
| **TOTAL** | **25-30 horas** | - |

---

### 🚀 Siguiente Paso Inmediato

**¿Quieres que empiece con la FASE 1 (Crítico) ahora mismo?**

Puedo empezar creando:
1. Componente `AppCard` (3-4 horas)
2. Unificar sombras con `AppShadows` (2 horas)
3. Reducir uso de gradiente creando `AppButtonType.solid` (2-3 horas)

**Resultado después de Fase 1**:
- ✅ Sombras 100% consistentes en toda la app
- ✅ Gradiente usado solo donde debe estar
- ✅ ~500 líneas de código menos (gracias a AppCard)
- ✅ App visualmente más cohesiva

---

**FIN DEL ANÁLISIS**

---

**Documentado por**: Claude Code
**Fecha**: Enero 2025
**Versión**: 1.0

# 🧮 Calculadora Práctica #4 · Clis

> Proyecto desarrollado como parte del programa  
> **Master Ingeniería de Software en la Era IA** · *Marlene Faria*

---

## 📋 Descripción

**Calculadora Práctica #4 Clis** es una calculadora técnica profesional construida como un único archivo `index.html` autocontenido. Combina una interfaz *dark mode* de estética 2026 con una lógica de cálculo robusta, sin dependencias externas ni frameworks, lista para abrir en cualquier navegador moderno.

---

## ✨ Características

| Categoría | Detalle |
|---|---|
| 🎨 **Diseño** | Dark mode 2026 · paleta azul-aqua-profundo · grid ambiental |
| 🔠 **Tipografía** | `DM Mono` (display numérico) + `Syne` (botones / UI) |
| ⚡ **Operaciones** | Suma · Resta · Multiplicación · División |
| 🔁 **Encadenado** | Permite operaciones en cadena sin pulsar `=` entre ellas |
| 🛡️ **Errores** | División por cero · overflow de dígitos · estado de error recuperable |
| ⌨️ **Teclado** | Soporte completo (`0-9`, `.`, `+`, `-`, `*`, `/`, `Enter`, `Backspace`, `Escape`) |
| 💡 **UX** | Operador activo resaltado · animación *pop* en resultado · efecto ripple en botones |
| 📱 **Responsive** | Adaptable a móvil, tablet y escritorio · padding generoso para no pegarse al borde |
| 📦 **Sin dependencias** | Un solo archivo `.html` — no requiere Node, npm ni servidor |

---

## 🗂️ Estructura del proyecto

```
calculadora-clis-4/
├── index.html      ← aplicación completa (HTML + CSS + JS)
└── README.md       ← este archivo
```

---

## 🚀 Cómo usar

### Abrir directamente en el navegador
1. Descarga o clona el repositorio.
2. Haz doble clic en `index.html`.
3. ¡Listo! La calculadora funcionará localmente sin necesidad de internet.


## ⌨️ Atajos de teclado

| Tecla | Acción |
|---|---|
| `0` – `9` | Ingresar dígito |
| `.` | Punto decimal |
| `+` `-` `*` `/` | Operadores aritméticos |
| `Enter` o `=` | Calcular resultado |
| `Backspace` | Borrar último dígito |
| `Escape` o `Delete` | Limpiar todo (igual que **C**) |

---

## 🧠 Arquitectura de la lógica

La calculadora usa una **máquina de estados explícita** con cuatro variables principales:

```
accumulator  →  primer operando almacenado (number)
pendingOp    →  operador pendiente: '+' | '-' | '*' | '/'
inputStr     →  cadena visible en pantalla (string)
freshInput   →  flag: true = próximo dígito inicia número nuevo
```

### Flujo de una operación encadenada

```
Usuario:  5  ×  4  =
          │  │  │  └─ applyOp(5, 4, '*') → 20 ✅
          │  │  └──── inputStr = '4', freshInput = false
          │  └─────── accumulator = 5, pendingOp = '*', freshInput = true
          └────────── inputStr = '5'
```

### Manejo de errores

```javascript
case '/':
  if (fb === 0) throw new RangeError('División por 0');
  return fa / fb;
```

Al producirse un error, la pantalla muestra `DIV/0  ERR` en rojo y la calculadora queda en un **estado de error recuperable**: cualquier dígito nuevo limpia el error y reinicia la entrada.

---

## 🎨 Sistema de diseño

```css
/* Paleta principal */
--ink-0:  #04060b   /* fondo profundo           */
--ink-2:  #0f1420   /* superficie de la tarjeta */
--aqua:   #00e5ff   /* acento principal          */
--eq-bg:  #0050d8   /* botón igual              */
--red:    #ff3860   /* estado de error           */
```

Todas las propiedades visuales están centralizadas en **CSS custom properties** (`var(--*)`) dentro de `:root`, facilitando el theming.

---

## 🛠️ Tecnologías

- **HTML5** semántico
- **CSS3** — custom properties, grid, animaciones, gradientes en capas
- **JavaScript ES6+** — IIFE, arrow functions, manejo de excepciones
- **Google Fonts** — DM Mono · Syne (carga optimizada con `preconnect`)

---

## 👩‍💻 Autora

**Marlene Faria**  
Master Ingeniería de Software en la Era IA

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia **MIT**.  
Libre para usar, modificar y distribuir con atribución.
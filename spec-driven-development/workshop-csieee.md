# 🚗 Workshop: Spec-Driven Development (SDD) con IA

Bienvenido al workshop **"Spec-Driven Development (SDD) con IA"**.

Este recurso está diseñado para acompañarte durante la sesión en vivo y servir como guía de referencia post-workshop. En esta edición construiremos una pequeña aplicación web para **registrar vehículos en venta y mostrar un catálogo público de vehículos disponibles**, utilizando especificaciones como fuente de verdad para guiar a la IA.

La demo está deliberadamente acotada: el objetivo no es construir un marketplace completo, sino demostrar cómo una petición informal puede transformarse en **arquitectura, especificaciones funcionales, pruebas y código** mediante SDD.

---

## 📌 Tabla de Contenidos

- [👨‍💻 Acerca de Pablo Herrera](#-acerca-de-pablo-herrera)
- [🎯 Objetivos del Workshop](#-objetivos-del-workshop)
- [⚖️ SDD vs. Vibe Coding](#️-sdd-vs-vibe-coding)
- [🛠️ Stack Tecnológico](#️-stack-tecnológico)
- [💻 Requisitos Previos](#-requisitos-previos)
- [🚀 Paso a Paso del Workshop](#-paso-a-paso-del-workshop)
  - [0. La Petición Informal](#0-la-petición-informal-raw-request)
  - [1. Creación del Proyecto](#1-creación-del-proyecto)
  - [2. Definición de Especificaciones](#2-definición-de-especificaciones-spec)
  - [3. Estrategia TDD y Prompts para la IA](#3-estrategia-tdd-y-prompts-para-la-ia)
  - [4. Pruebas E2E con Playwright](#4-pruebas-e2e-con-playwright)
- [🧪 Ejecución de Pruebas](#-ejecución-de-pruebas)
- [⏱️ Agenda / Timeline](#️-agenda--timeline)
- [💡 Preguntas Frecuentes y Buenas Prácticas](#-preguntas-frecuentes-y-buenas-prácticas)

---

## 👨‍💻 Acerca de Pablo Herrera

<table>
  <tr>
    <td width="25%" align="center" valign="top">
      <img src="../img/pabloherrera.png" alt="Pablo Herrera" width="160" style="border-radius: 50%; max-width: 100%;"/><br/><br/>
      <b>Redes Sociales:</b><br/>
      🎬 <a href="https://www.youtube.com/@TestingConPabloHerrera" target="_blank">YouTube</a><br/>
      💼 <a href="https://ec.linkedin.com/in/pablo-herrera-ec" target="_blank">LinkedIn</a>
    </td>
    <td width="75%" valign="top">
      <p>Soy un profesional apasionado por la tecnología con más de 10 años de experiencia en la industria. Mi trayectoria combina un sólido background en Desarrollo de Software y una especialización profunda en Control de Calidad y Automatización (QA Automation).</p>
      <p>Mi objetivo es claro: ayudar a los equipos de software a alcanzar la excelencia, garantizando productos de alta calidad, escalables y confiables.</p>
      <h3>🛠️ Mis Habilidades Técnicas</h3>
      <p>Como <b>QA Automation Engineer</b>, poseo experiencia práctica en la creación e implementación de <i>frameworks</i> de automatización robustos, utilizando herramientas y lenguajes líderes en el sector:</p>
      <table>
        <thead>
          <tr>
            <th>Categoría</th>
            <th>Tecnologías y Herramientas Clave</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><b>Lenguajes de Programación</b></td>
            <td>Java, Python, JavaScript</td>
          </tr>
          <tr>
            <td><b>Herramientas de QA</b></td>
            <td>Selenium WebDriver, Playwright, Appium, Cypress, Postman</td>
          </tr>
          <tr>
            <td><b>Metodologías</b></td>
            <td>Agile (Scrum/Kanban), Testing de Rendimiento, Testing Funcional</td>
          </tr>
          <tr>
            <td><b>Otros</b></td>
            <td>Git, Integración Continua (CI/CD)</td>
          </tr>
        </tbody>
      </table>
    </td>
  </tr>
</table>

---

## 🎯 Objetivos del Workshop

1. **Comprender la metodología SDD (Spec-Driven Development):** transformar una petición informal en especificaciones claras que sirvan como fuente única de verdad.
2. **Reducir la ambigüedad antes de programar:** identificar qué necesita realmente la demo y qué queda fuera del alcance.
3. **Separar arquitectura y funcionalidad:** mantener una especificación de arquitectura independiente de las especificaciones de cada dominio.
4. **Implementar TDD + E2E:** utilizar pruebas unitarias para las reglas de negocio y Playwright para validar los flujos principales de usuario.
5. **Demostrar cómo una IA puede trabajar con contratos:** entregar a la IA instrucciones y archivos `.md` concretos en lugar de pedirle simplemente "hazme una página web".

---

## ⚖️ SDD vs. Vibe Coding

| Característica | 🎲 Vibe Coding | 📐 Spec-Driven Development |
| :--- | :--- | :--- |
| **Punto de partida** | "Hazme una página para vender autos". | Requerimientos, arquitectura y funcionalidades documentadas. |
| **Arquitectura** | La IA decide cómo organizar el proyecto. | La arquitectura se define antes de generar código. |
| **Alcance** | Puede crecer innecesariamente durante la conversación. | La especificación establece qué entra y qué queda fuera. |
| **Testing** | Se agrega al final o puede omitirse. | Las pruebas forman parte del diseño. |
| **Cambios** | Se realizan directamente sobre el código. | Se actualiza la especificación y luego se implementa. |
| **Control** | La IA toma muchas decisiones implícitas. | El desarrollador gobierna las decisiones explícitas. |

---

## 🛠️ Stack Tecnológico

- **Entorno de Desarrollo / Agente de IA:** Antigravity AI / VS Code.
- **Backend:** Node.js (v18+) con Express.
- **Frontend:** HTML5 semántico, JavaScript Vanilla modular y Tailwind CSS vía CDN.
- **Persistencia:** almacenamiento en memoria para la demo.
- **Pruebas Unitarias:** Node.js Test Runner (`node:test` y `node:assert`).
- **Pruebas End-to-End (E2E):** Playwright.

---

## 💻 Requisitos Previos

Si vas a realizar el ejercicio en tu equipo local:

1. **Node.js v18 o superior**
   ```bash
   node -v
   ```

2. **Antigravity AI / IDE configurado** para trabajar con el agente de IA.

> ℹ️ **Nota:** El proyecto, las dependencias, las especificaciones, el código y las pruebas se construirán durante el workshop.

---

# 🚀 Paso a Paso del Workshop

## 0. La Petición Informal (Raw Request)

Imagina que recibes la siguiente solicitud verbal:

> *"Necesitamos con urgencia una página web para venta de autos. El cliente quiere ver una demo el día de mañana y yo le dije que ya la tenemos lista. Lo que quiere ver es, una página donde pueda registrar el vehículo que quiero vender, lo que él quiere ver es la página donde se registren los vehículos y ya la página del listado de los vehículos disponibles. Eso es todo ¿cuánto tiempo te va a tardar hacerlo?"*

### 🔎 ¿Qué problemas encontramos en esta petición?

A primera vista parece sencilla, pero todavía existen muchas decisiones sin definir:

- ¿Qué información tiene un vehículo?
- ¿Qué campos son obligatorios?
- ¿Qué tipos de vehículos se pueden registrar?
- ¿Cómo se valida el precio?
- ¿Cómo se identifica un vehículo?
- ¿Qué significa exactamente "disponible"?
- ¿Cómo se muestran los vehículos en el listado?
- ¿Existe una pantalla de detalle?
- ¿Hay autenticación?
- ¿Hay edición o eliminación?
- ¿Hay base de datos?
- ¿Hay fotografías reales?
- ¿Hay filtros?
- ¿Hay pagos?
- ¿Hay contacto con el vendedor?

Para la demo **no intentaremos resolver todo esto**.

### 🎯 Alcance definido para esta demo

La demo tendrá únicamente dos capacidades principales:

1. **Registrar un vehículo para venta.**
2. **Mostrar los vehículos disponibles en una landing page.**

Quedan explícitamente fuera de alcance:

- Autenticación.
- Registro de usuarios.
- Pagos.
- Gestión de compradores.
- Chat.
- Favoritos.
- Edición y eliminación.
- Persistencia en base de datos.
- Integración con servicios externos.
- Carga real de imágenes.
- Filtros avanzados.
- Panel administrativo.

Esta decisión es importante en SDD: **una buena especificación no solamente define qué hacer; también define qué NO hacer.**

---

## 1. Creación del Proyecto

Abrir Antigravity IDE y abrir una carpeta vacía donde estará el proyecto.

Ejecutar:

```bash
npm init -y
npm install express cors
npm install -D @playwright/test
npx playwright install chromium
```

---

# 2. Definición de Especificaciones (`spec/`)

En esta versión del workshop no tendremos un único `requirements.md`.

La documentación se dividirá por responsabilidad:

```text
spec/
├── arquitectura/
│   └── ar01-arquitectura.md
├── auto/
│   └── auto01-registro.md
└── venta/
    └── venta01-landing.md
```

### ¿Por qué usar `ar01`, `auto01` y `venta01`?

El prefijo permite identificar la primera versión de cada documento.

Por ejemplo:

```text
ar01-arquitectura.md
ar02-arquitectura.md
```

podría representar una evolución posterior de la arquitectura.

De la misma forma:

```text
auto01-registro.md
auto02-registro.md
```

permite conservar la trazabilidad de cambios en la especificación funcional.

---

## 📄 `spec/arquitectura/ar01-arquitectura.md`

Crea el archivo:

```text
spec/arquitectura/ar01-arquitectura.md
```

con el siguiente contenido:

```markdown
# Especificación de Arquitectura — Venta de Autos

## 1. Estructura de Directorios y Carpetas Requerida

El proyecto DEBE ser organizado de forma modular con la siguiente estructura:

car-sale-demo/
├── spec/
│   ├── arquitectura/
│   │   └── ar01-arquitectura.md
│   ├── auto/
│   │   └── auto01-registro.md
│   └── venta/
│       └── venta01-landing.md
├── src/
│   ├── controllers/
│   │   └── autosController.js
│   ├── routes/
│   │   └── apiRoutes.js
│   └── services/
│       └── autosService.js
├── public/
│   ├── index.html
│   ├── registrar.html
│   ├── js/
│   │   ├── api.js
│   │   ├── app.js
│   │   └── registro.js
│   └── css/
│       └── styles.css
├── tests/
│   ├── unit/
│   │   └── autos.test.js
│   └── e2e/
│       ├── registro-auto.spec.js
│       └── listado-autos.spec.js
├── playwright.config.js
├── server.js
└── package.json

## 2. Principios de Arquitectura

- La aplicación DEBE utilizar Node.js + Express en el backend.
- El frontend DEBE utilizar HTML, JavaScript Vanilla y Tailwind CSS mediante CDN.
- El almacenamiento de vehículos será EN MEMORIA para esta demo.
- El backend DEBE exponer una API REST para registrar y consultar vehículos.
- La lógica de negocio NO DEBE estar dentro de las páginas HTML.
- La manipulación del DOM DEBE permanecer en módulos JavaScript.
- El consumo de la API DEBE estar centralizado en `public/js/api.js`.
- La lógica de validación y procesamiento de vehículos DEBE permanecer en el backend.
- El mecanismo de recepción y almacenamiento de la fotografía DEBE estar encapsulado en el backend y ser transparente para el resto de la aplicación.
- La fotografía asociada a cada vehículo DEBE poder ser servida por la aplicación para su visualización en el catálogo.

## 3. Separación de Responsabilidades

### Backend

- `server.js`
  - Punto de entrada de la aplicación.
  - Configuración de Express.
  - Configuración de archivos estáticos.

- `src/routes/apiRoutes.js`
  - Definición de endpoints REST.

- `src/controllers/autosController.js`
  - Recibir las peticiones.
  - Validar los datos.
  - Delegar la lógica de negocio.
  - Construir las respuestas HTTP.

- `src/services/autosService.js`
  - Mantener la colección de vehículos en memoria.
  - Registrar vehículos.
  - Consultar vehículos disponibles.

### Frontend

- `public/index.html`
  - Landing page.
  - Presentación de la propuesta.
  - Listado de vehículos disponibles.

- `public/registrar.html`
  - Formulario para registrar un vehículo.

- `public/js/api.js`
  - Funciones `fetch` para consumir la API.

- `public/js/app.js`
  - Cargar vehículos.
  - Renderizar tarjetas del catálogo.
  - Gestionar eventos de la landing page.

- `public/js/registro.js`
  - Gestionar el formulario de registro.
  - Enviar información al backend.
  - Mostrar mensajes de éxito o error.

## 4. Restricciones Arquitectónicas

- PROHIBIDO colocar lógica de negocio dentro de archivos HTML.
- PROHIBIDO colocar llamadas `fetch` directamente dentro de `index.html`.
- PROHIBIDO crear un único archivo JavaScript monolítico para toda la aplicación.
- PROHIBIDO instalar frameworks frontend adicionales.
- NO implementar base de datos para esta demo.
- NO implementar autenticación.
- NO implementar pagos.
- NO implementar funcionalidades fuera del alcance definido en las especificaciones funcionales.

## 5. API Requerida

### GET `/api/autos`

Devuelve la lista de vehículos disponibles.

### POST `/api/autos`

Registra un nuevo vehículo.

La petición DEBE permitir enviar los datos del vehículo junto con su fotografía.

La respuesta DEBE indicar claramente si el registro fue exitoso o si existen errores de validación.
```

---

## 📄 `spec/auto/auto01-registro.md`

Crea:

```text
spec/auto/auto01-registro.md
```

con:

```markdown
# Especificación Funcional — Registro de Autos

## 1. Objetivo

Permitir que una persona registre un vehículo que desea publicar para venta.

Esta funcionalidad forma parte de la demo y utiliza almacenamiento en memoria.

## 2. Datos del Vehículo

El formulario DEBE solicitar:

| Campo | Tipo | Obligatorio | Regla |
| :--- | :--- | :---: | :--- |
| Marca | Texto | Sí | Entre 2 y 30 caracteres |
| Modelo | Texto | Sí | Entre 1 y 40 caracteres |
| Año | Número | Sí | Año válido entre 1950 y el año actual |
| Precio | Número | Sí | Mayor que 0 |
| Kilometraje | Número | Sí | Mayor o igual a 0 |
| Ciudad | Texto | Sí | Entre 2 y 40 caracteres |
| Descripción | Texto | Sí | Entre 10 y 500 caracteres |
| Fotografía | Archivo de imagen | Sí | Debe corresponder al vehículo que se está registrando |

## 3. Reglas de Negocio

1. Todos los campos obligatorios DEBEN ser validados.
2. `marca`, `modelo`, `ciudad` y `descripcion` DEBEN conservar el contenido proporcionado por el usuario, salvo eliminación de espacios innecesarios al inicio y al final.
3. `año` DEBE ser un número entero.
4. `precio` DEBE ser mayor que cero.
5. `kilometraje` DEBE ser mayor o igual a cero.
6. La descripción DEBE tener al menos 10 caracteres.
7. La fotografía del vehículo ES OBLIGATORIA durante el registro.
8. La fotografía DEBE ser un archivo de imagen.
9. La fotografía registrada DEBE quedar asociada al vehículo y estar disponible para mostrarse posteriormente en el listado de ventas.
10. Cada vehículo DEBE recibir un identificador único generado por el backend.
9. Cada vehículo nuevo DEBE registrarse inicialmente con estado `DISPONIBLE`.
10. Un vehículo registrado DEBE aparecer en el listado de vehículos disponibles.

## 4. Modelo de Datos

Ejemplo:

{
  "id": "AUTO-001",
  "marca": "Toyota",
  "modelo": "Corolla",
  "anio": 2022,
  "precio": 18500,
  "kilometraje": 35000,
  "ciudad": "Quito",
  "descripcion": "Vehículo en excelente estado.",
  "fotografia": "ruta-o-referencia-de-la-imagen",
  "estado": "DISPONIBLE"
}

## 5. API

### POST `/api/autos`

Request:

{
  "marca": "Toyota",
  "modelo": "Corolla",
  "anio": 2022,
  "precio": 18500,
  "kilometraje": 35000,
  "ciudad": "Quito",
  "descripcion": "Vehículo en excelente estado.",
  "fotografia": "<archivo-de-imagen>"
}

### Respuesta exitosa

HTTP 201

{
  "message": "Vehículo registrado correctamente",
  "auto": {
    "id": "AUTO-001",
    "estado": "DISPONIBLE"
  }
}

### Respuesta de validación

HTTP 400

{
  "error": "Descripción inválida"
}

## 6. Comportamiento de la Pantalla

La pantalla DEBE:

1. Mostrar un título claro.
2. Mostrar el formulario de registro.
3. Identificar visualmente los campos obligatorios.
4. Permitir seleccionar y visualizar una vista previa de la fotografía antes de enviar el formulario.
5. Permitir enviar el formulario.
6. Mostrar un mensaje de éxito cuando el vehículo sea registrado.
7. Mostrar mensajes comprensibles cuando existan errores de validación.
8. Después de un registro exitoso, ofrecer una forma clara de volver al listado de vehículos.

## 7. Fuera de Alcance

Esta funcionalidad NO incluye:

- Login.
- Registro de usuarios.
- Edición.
- Eliminación.
- Galería de fotografías múltiples.
- Edición avanzada de fotografías.
- Base de datos.
- Gestión de vendedores.
- Gestión de compradores.
- Pagos.
```

---

## 📄 `spec/venta/venta01-landing.md`

Crea:

```text
spec/venta/venta01-landing.md
```

con:

```markdown
# Especificación Funcional — Landing Page de Venta de Autos

## 1. Objetivo

Crear una landing page sencilla para mostrar al cliente una primera versión visual del sitio de venta de autos.

La página DEBE concentrarse en presentar la propuesta y mostrar los vehículos disponibles.

NO se pretende construir un marketplace completo.

## 2. Estructura de la Landing Page

La página principal (`public/index.html`) DEBE contener:

### 2.1 Header

Debe mostrar:

- Nombre o logotipo de la aplicación.
- Enlace "Vehículos".
- Botón "Vender mi auto".

El botón "Vender mi auto" DEBE dirigir a:

`/registrar.html`

### 2.2 Hero

Debe contener:

- Título principal relacionado con la venta de vehículos.
- Texto breve explicando la propuesta.
- Botón principal "Ver vehículos".
- Botón secundario "Vender mi auto".

Ejemplo conceptual:

"Encuentra tu próximo auto"

"Explora vehículos disponibles o publica el tuyo."

### 2.3 Sección de Vehículos Disponibles

Debe mostrar una sección titulada:

"Vehículos disponibles"

Los vehículos DEBEN obtenerse mediante:

`GET /api/autos`

Cada vehículo DEBE visualizarse como una tarjeta.

La tarjeta DEBE mostrar como mínimo:

- Fotografía del vehículo.
- Marca y modelo.
- Año.
- Precio.
- Kilometraje.
- Ciudad.
- Estado.

### 2.4 Estado sin vehículos

Si no existen vehículos registrados, la página DEBE mostrar un mensaje amigable, por ejemplo:

"Todavía no tenemos vehículos disponibles."

Y debe mostrar una llamada a la acción para registrar un vehículo.

### 2.5 Footer

Debe mostrar información sencilla de la aplicación.

No es necesario implementar enlaces funcionales a redes sociales, términos legales ni políticas de privacidad para esta demo.

## 3. Diseño Visual

La landing page DEBE:

- Ser responsive.
- Utilizar una apariencia moderna relacionada con el sector automotriz.
- Tener una jerarquía visual clara.
- Priorizar la lectura del precio y los datos principales del vehículo.
- Utilizar Tailwind CSS mediante CDN.
- Evitar una interfaz excesivamente compleja.

## 4. Interacción

Al cargar la página:

1. Se debe solicitar la lista de vehículos mediante `GET /api/autos`.
2. Se deben renderizar las tarjetas incluyendo la fotografía asociada a cada vehículo.
3. Si la API responde con error, se debe mostrar un mensaje comprensible.
4. El botón "Vender mi auto" debe llevar al formulario de registro.
5. El botón "Ver vehículos" debe desplazar al usuario hacia la sección del catálogo.

## 5. Alcance de la Demo

La landing page NO DEBE incluir:

- Login.
- Registro de usuarios.
- Filtros avanzados.
- Ordenamiento.
- Favoritos.
- Comparación de vehículos.
- Chat.
- Pagos.
- Financiamiento.
- Reserva de vehículos.
- Detalle individual del vehículo.
- Panel administrativo.

Estas funcionalidades podrían formar parte de futuras especificaciones.

## 6. Criterio de Aceptación Principal

Cuando exista al menos un vehículo registrado:

1. El usuario entra a la landing page.
2. Visualiza la sección "Vehículos disponibles".
3. Visualiza una tarjeta por cada vehículo disponible.
4. La tarjeta muestra la fotografía y los datos principales del vehículo.
5. El usuario puede acceder al formulario mediante "Vender mi auto".
```

---

# 3. Especificación de Pruebas

Para mantener el enfoque SDD + TDD, las pruebas se derivarán de las especificaciones anteriores.

## 📄 `tests/unit/autos.test.js`

Los casos unitarios obligatorios son:

### Caso 1 — Registro exitoso

Registrar un vehículo válido.

Verificar:

- Se crea un identificador.
- El vehículo queda con estado `DISPONIBLE`.
- Los datos principales se almacenan correctamente.
- La fotografía queda asociada al vehículo.

### Caso 2 — Marca inválida

Intentar registrar un vehículo sin marca.

Resultado esperado:

- HTTP 400.
- Mensaje de validación.

### Caso 3 — Precio inválido

Intentar registrar un vehículo con precio `0` o negativo.

Resultado esperado:

- HTTP 400.

### Caso 4 — Kilometraje inválido

Intentar registrar un vehículo con kilometraje negativo.

Resultado esperado:

- HTTP 400.

### Caso 5 — Año inválido

Intentar registrar un año fuera del rango permitido.

Resultado esperado:

- HTTP 400.

### Caso 6 — Descripción demasiado corta

Intentar registrar una descripción con menos de 10 caracteres.

Resultado esperado:

- HTTP 400.

### Caso 7 — Consulta de vehículos

Registrar uno o más vehículos y consultar la lista.

Resultado esperado:

- Los vehículos registrados aparecen en la colección disponible.

---

## 📄 Pruebas E2E con Playwright

Ubicación:

```text
tests/e2e/
├── registro-auto.spec.js
└── listado-autos.spec.js
```

### `registro-auto.spec.js`

Flujo:

1. Navegar a `http://localhost:3000/registrar.html`.
2. Verificar que exista el formulario.
3. Completar:
   - Marca: `Toyota`
   - Modelo: `Corolla`
   - Año: `2022`
   - Precio: `18500`
   - Kilometraje: `35000`
   - Ciudad: `Quito`
   - Descripción: `Vehículo en excelente estado`
   - Fotografía: seleccionar un archivo de imagen de prueba.
4. Verificar que se muestre la vista previa de la fotografía.
5. Enviar el formulario.
6. Verificar que aparezca el mensaje de registro exitoso.
7. Verificar que exista una opción para regresar al listado.

### `listado-autos.spec.js`

Flujo:

1. Navegar a `http://localhost:3000`.
2. Verificar el título principal.
3. Verificar la sección `Vehículos disponibles`.
4. Verificar que se carguen los vehículos registrados.
5. Verificar que una tarjeta contenga:
   - Fotografía del vehículo.
   - Marca.
   - Modelo.
   - Año.
   - Precio.
   - Kilometraje.
   - Ciudad.
6. Verificar que la fotografía visible corresponda al vehículo registrado.
7. Verificar que el botón `Vender mi auto` dirija a `/registrar.html`.

---

# 4. Estrategia TDD & Prompts para la IA

## 🤖 Prompt 1 — Analizar las especificaciones

```text
Lee cuidadosamente todos los archivos dentro de la carpeta spec/.

En particular:

- spec/arquitectura/ar01-arquitectura.md
- spec/auto/auto01-registro.md
- spec/venta/venta01-landing.md

Antes de generar código:

1. Identifica la arquitectura requerida.
2. Identifica las entidades y reglas de negocio.
3. Identifica los endpoints requeridos.
4. Identifica las pruebas unitarias y E2E que deberán existir.
5. Respeta estrictamente el alcance definido en las especificaciones.

No agregues funcionalidades que no estén especificadas.
```

---

## 🤖 Prompt 2 — Fase RED: pruebas unitarias

```text
Lee:

- spec/arquitectura/ar01-arquitectura.md
- spec/auto/auto01-registro.md

Siguiendo TDD, genera únicamente:

tests/unit/autos.test.js

Utiliza el test runner nativo de Node.js:

- node:test
- node:assert

Implementa los casos de prueba definidos en la especificación.

No implementes todavía el controlador ni la lógica de negocio.

El objetivo es ejecutar las pruebas y comprobar que inicialmente fallen.
```

---

## 🤖 Prompt 3 — Fase GREEN: backend

```text
Lee todos los archivos de la carpeta spec/.

Implementa el backend respetando estrictamente:

spec/arquitectura/ar01-arquitectura.md
spec/auto/auto01-registro.md

Debes crear:

- src/controllers/autosController.js
- src/routes/apiRoutes.js
- src/services/autosService.js
- server.js

Implementa únicamente:

- GET /api/autos
- POST /api/autos

El almacenamiento debe ser en memoria.

No agregues autenticación, base de datos, edición, eliminación ni funcionalidades no especificadas.

El objetivo es hacer pasar las pruebas unitarias existentes.
```

---

## 🤖 Prompt 4 — Frontend

```text
Lee:

- spec/arquitectura/ar01-arquitectura.md
- spec/auto/auto01-registro.md
- spec/venta/venta01-landing.md

Implementa el frontend respetando exactamente la estructura y restricciones definidas.

Debes crear:

- public/index.html
- public/registrar.html
- public/js/api.js
- public/js/app.js
- public/js/registro.js
- public/css/styles.css

El formulario de registro DEBE permitir seleccionar una fotografía del vehículo, mostrar una vista previa y enviarla al backend. La fotografía debe quedar asociada al vehículo y posteriormente mostrarse en la landing page.

Utiliza HTML semántico, JavaScript Vanilla y Tailwind CSS mediante CDN.

No coloques lógica de negocio ni llamadas fetch dentro de los archivos HTML.
```

---

## 🤖 Prompt 5 — Pruebas E2E

```text
Lee todos los archivos de la carpeta spec/.

Genera las pruebas E2E con Playwright:

- tests/e2e/registro-auto.spec.js
- tests/e2e/listado-autos.spec.js

Las pruebas deben cubrir únicamente los flujos descritos en las especificaciones.

Además genera o actualiza:

playwright.config.js

No agregues escenarios que no estén definidos en las especificaciones.
```

---

# 5. Pruebas E2E con Playwright

## Ejemplo de flujo de registro

```javascript
test('Registrar un vehículo correctamente', async ({ page }) => {
  await page.goto('http://localhost:3000/registrar.html');

  await page.fill('#marca', 'Toyota');
  await page.fill('#modelo', 'Corolla');
  await page.fill('#anio', '2022');
  await page.fill('#precio', '18500');
  await page.fill('#kilometraje', '35000');
  await page.fill('#ciudad', 'Quito');
  await page.fill('#descripcion', 'Vehículo en excelente estado');

  await page.click('button[type="submit"]');

  await expect(page.locator('#mensaje')).toContainText(
    'Vehículo registrado correctamente'
  );
});
```

## Ejemplo de flujo del catálogo

```javascript
test('Mostrar vehículos disponibles en la landing page', async ({ page }) => {
  await page.goto('http://localhost:3000');

  await expect(
    page.getByRole('heading', { name: 'Vehículos disponibles' })
  ).toBeVisible();

  await expect(page.locator('[data-testid="auto-card"]').first()).toBeVisible();
});
```

---

# 🧪 Ejecución de Pruebas

## Ejecutar pruebas unitarias

```bash
node --test tests/unit/autos.test.js
```

## Ejecutar pruebas E2E

```bash
npx playwright test
```

## Ejecutar Playwright con interfaz

```bash
npx playwright test --ui
```

## Iniciar la aplicación

```bash
node server.js
```

Abrir:

```text
http://localhost:3000
```

Formulario:

```text
http://localhost:3000/registrar.html
```

---

# ⏱️ Agenda / Timeline sugerida

| Tiempo | Fase | Actividad |
| :--- | :--- | :--- |
| **00:00 - 00:08** | Contexto | Petición informal y problema de ambigüedad. |
| **00:08 - 00:18** | SDD | Transformar la petición en alcance y especificaciones. |
| **00:18 - 00:28** | Arquitectura | Crear `ar01-arquitectura.md` y explicar separación de responsabilidades. |
| **00:28 - 00:38** | Funcionalidades | Crear `auto01-registro.md` y `venta01-landing.md`. |
| **00:38 - 00:48** | TDD | Generar pruebas unitarias y demostrar RED → GREEN. |
| **00:48 - 00:58** | E2E | Generar y ejecutar Playwright. |
| **00:58 - 01:00** | Cierre | Mostrar la aplicación y explicar cómo evolucionarían las specs. |

---

# 💡 Preguntas Frecuentes y Buenas Prácticas

## 1. ¿Por qué separar `arquitectura`, `auto` y `venta`?

Porque no todo requisito tiene la misma naturaleza.

La arquitectura define **cómo se organiza el sistema**.

`auto` define **qué significa registrar un vehículo**.

`venta` define **cómo se presenta la experiencia de venta en esta demo**.

Esta separación facilita que cada documento tenga una responsabilidad clara.

---

## 2. ¿Por qué `ar01-arquitectura.md` y no simplemente `arquitectura.md`?

El prefijo permite mantener trazabilidad de la evolución de las especificaciones.

Si posteriormente cambia la arquitectura, podríamos documentar una nueva versión:

```text
ar01-arquitectura.md
ar02-arquitectura.md
```

Así podemos identificar cuál fue la definición inicial.

---

## 3. ¿Por qué no hacer directamente una página completa de venta de autos?

Porque el objetivo de la demo es mostrar SDD, no construir un marketplace completo.

Una petición como "una página para vender autos" puede crecer rápidamente hacia:

- usuarios,
- vendedores,
- compradores,
- fotografías,
- filtros,
- favoritos,
- pagos,
- financiamiento,
- reservas,
- chat,
- notificaciones,
- administración.

Para una demo de aproximadamente una hora, definir el alcance es parte fundamental del ejercicio.

---

## 4. ¿Qué pasa si mañana el cliente pide filtros?

No deberíamos modificar directamente el código sin actualizar primero el contrato.

Podríamos crear una nueva especificación o versión, por ejemplo:

```text
spec/venta/venta02-filtros.md
```

y solicitar a la IA que implemente únicamente ese cambio utilizando como contexto las especificaciones existentes.

---

## 5. ¿Qué pasa si el cliente pide una base de datos?

La arquitectura actual establece almacenamiento en memoria.

Ese cambio debería provocar una revisión de la arquitectura.

Por ejemplo, podríamos crear:

```text
spec/arquitectura/ar02-arquitectura.md
```

y definir allí la nueva arquitectura de persistencia.

La idea es que **el cambio arquitectónico quede documentado antes de modificar el código**.

---

## 6. ¿Por qué incluir pruebas desde el principio?

Porque las pruebas también son una forma de especificación ejecutable.

La prueba unitaria expresa reglas de negocio como:

> "Un precio no puede ser cero o negativo."

La prueba E2E expresa comportamiento del usuario como:

> "Un usuario puede registrar un vehículo y posteriormente visualizarlo en el catálogo."

Esto permite utilizar la IA para implementar código contra criterios verificables.

---

# 🎯 Idea central de la demo

La petición original fue:

> "Necesitamos con urgencia una página web para venta de autos..."

Al final del ejercicio, esa frase informal se transforma en:

```text
Petición informal
       ↓
Definición de alcance
       ↓
Arquitectura
       ↓
Especificaciones funcionales
       ↓
Casos de prueba
       ↓
Implementación
       ↓
Pruebas unitarias
       ↓
Pruebas E2E
       ↓
Demo funcional
```

Ese es el punto principal de este workshop:

**No se trata de pedirle a la IA que programe más rápido.**

**Se trata de darle mejores especificaciones para que pueda construir exactamente lo que necesitamos.**

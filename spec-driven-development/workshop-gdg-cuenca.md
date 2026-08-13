# 🚀 Workshop: Spec-Driven Development (SDD) con IA

Bienvenido al workshop **"Spec-Driven Development (SDD) con IA"**.

Este recurso está diseñado para acompañarte durante la sesión en vivo y servir como guía de referencia post-workshop. Aquí encontrarás la metodología, especificaciones, prompts, código estructurado y la suite completa de pruebas (**TDD + E2E con Playwright**) utilizando **Antigravity AI**.

---

## 📌 Tabla de Contenidos

- [👨‍💻 Acerca de Pablo Herrera](#-acerca-de-pablo-herrera)
- [🎯 Objetivos del Workshop](#-objetivos-del-workshop)
- [⚖️ SDD vs. Vibe Coding](#️-sdd-vs-vibe-coding)
- [🛠️ Stack Tecnológico](#️-stack-tecnológico)
- [💻 Requisitos Previos (Para los Asistentes)](#-requisitos-previos-para-los-asistentes)
- [🚀 Paso a Paso del Workshop](#-paso-a-paso-del-workshop)
  - [1. La Petición Informal (Raw Request)](#1-la-petición-informal-raw-request)
  - [2. Definición de Especificaciones (`spec/`)](#2-definición-de-especificaciones-spec)
  - [3. Estrategia TDD & Prompts para la IA](#3-estrategia-tdd--prompts-para-la-ia)
  - [4. Pruebas E2E con Playwright](#4-pruebas-e2e-con-playwright)
- [🧪 Ejecución de Pruebas](#-ejecución-de-pruebas)
- [⏱️ Agenda / Timeline (60 min)](#️-agenda--timeline-60-min)
- [💡 Preguntas Frecuentes y Buenas Prácticas](#-preguntas-frecuentes-y-buenas-prácticas)
- [📚 Qué puedo aprender a continuación](#-qué-puedo-aprender-a-continuación)

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

1. **Comprender la metodología SDD (Spec-Driven Development):** Diseñar software asistido por IA utilizando especificaciones como fuente única de verdad (*Single Source of Truth*).
2. **Superar el "Vibe Coding":** Eliminar la generación de código monolítico, acoplado y sin pruebas.
3. **Implementar TDD + E2E:** Guiar a la IA (Antigravity) para escribir primero pruebas unitarias fallidas (`node:test`) y automatizar la UI con **Playwright**.
4. **Arquitectura Limpia y Modular:** Mantener separación de responsabilidades (SoC) estricta entre Frontend (Vanilla JS + Tailwind CDN) y Backend (Node.js + Express MVC).

---

## ⚖️ SDD vs. Vibe Coding

| Característica | 🎲 Vibe Coding (Improvisación) | 📐 Spec-Driven Development (SDD) |
| :--- | :--- | :--- |
| **Enfoque** | Prompts ambiguos sobre la marcha. | Definición previa de contratos y arquitectura. |
| **Estructura** | Un archivo `index.html` gigante con JS embebido. | Estructura modular por capas (MVC / Controller-Service). |
| **Mantenibilidad** | Frágil, propenso a bugs y alucinaciones. | Altamente mantenible y escalable. |
| **Testing** | Inexistente o tests manuales frágiles. | TDD unitario + Pruebas E2E automatizadas con Playwright. |
| **Control** | La IA decide la arquitectura por ti. | El desarrollador gobierna las reglas y la arquitectura. |

---

## 🛠️ Stack Tecnológico

- **Entorno de Desarrollo / Agente de IA:** [Antigravity AI](https://antigravity.google) / VS Code.
- **Backend:** Node.js (v18+) con Express (En memoria).
- **Frontend:** HTML5 Semántico, JavaScript Vanilla modular, Tailwind CSS via CDN.
- **Pruebas Unitarias:** Node.js Test Runner nativo (`node:test` y `node:assert`).
- **Pruebas End-to-End (E2E):** [Playwright](https://playwright.dev/).

---

## 💻 Requisitos Previos (Para los Asistentes)

Si vas a acompañar el workshop realizando los ejercicios en tu equipo local, asegúrate de contar únicamente con las siguientes herramientas instaladas antes de iniciar la sesión:

1. **Node.js (v18 o superior):**
   - Verifica la instalación ejecutando `node -v` en tu terminal.
2. **Antigravity AI (IDE / Extensión):**
   - Asegúrate de tener instalado y configurado el entorno de **Antigravity AI** para interactuar con la IA durante la sesión.

> ℹ️ **Nota:** Todo el proyecto, la inicialización del directorio local, las dependencias (`npm install`), las librerías de prueba (Playwright) y las especificaciones se construirán desde cero durante el workshop en vivo en tu máquina local. No es necesario clonar ni descargar repositorios previos de GitHub.

---

## 🚀 Paso a Paso del Workshop

### 0. La Petición Informal (Raw Request)
Imagína que recibes la siguiente solicitud verbal o correo informal:
> *"Necesitamos con urgencia una página web para inscribir alumnos a nuestros 3 cursos. Debe pedir cédula/identidad (máx 10 dígitos), nombre, apellido, país y ciudad (país y ciudad se guardan siempre en MAYÚSCULAS). Debe mostrar la lista abajo en una tabla y necesitamos pruebas unitarias y automatizadas."*

---

### 1. Creación del proyecto 

1. Abrir Antigravity IDE
2. Abrir una carpeta vacia (donde va a estar el proyecto)
3. Ejecutar los comandos en este orden:

npm init -y
npm install express cors
npm install -D @playwright/test
npx playwright install chromium


---

### 2. Definición de Especificaciones (`spec/`)

#### 📄 `spec/requirements.md`
Crea el archivo `spec/requirements.md` copiando y pegando el siguiente contenido:

```markdown
# Especificación Funcional y Arquitectura: Sistema de Inscripción

## 1. Estructura de Directorios y Carpetas Requerida
El proyecto DEBE ser organizado de forma modular con la siguiente estructura exacta:

sdd-course-registration/
├── spec/
│   ├── requirements.md
│   └── testing.md
├── src/
│   ├── controllers/
│   │   └── inscripcionesController.js
│   └── routes/
│       └── apiRoutes.js
├── public/
│   ├── index.html
│   └── js/
│       ├── api.js
│       └── app.js
├── tests/
│   ├── unit/
│   │   └── inscripciones.test.js
│   └── e2e/
│       └── registration.spec.js
├── playwright.config.js
├── server.js
└── package.json

## 2. Entidades de Datos
- `identidad`: Texto numérico de EXACTAMENTE 10 dígitos (Ej: "0928374651").
- `nombre`: Texto de máximo 25 caracteres.
- `apellido`: Texto de máximo 25 caracteres.
- `pais`: Texto de máximo 15 caracteres. Convertir a MAYÚSCULAS.
- `ciudad`: Texto de máximo 15 caracteres. Convertir a MAYÚSCULAS.
- `cursoId`: ID del curso seleccionado de la lista predefinida.

## 3. Datos Mock Iniciales (Cursos)
1. "Desarrollo Web con Node.js"
2. "IA Aplicada a la Programación"
3. "Testing y Automatización"

## 4. Endpoints Backend
- `GET /api/cursos`: Lista de cursos.
- `GET /api/inscripciones`: Lista de inscritos.
- `POST /api/inscripciones`: Recibe datos, valida y guarda en memoria.
  - *Validaciones:* 
    - Identidad != 10 dígitos -> Error 400.
    - Nombre/Apellido > 25 caracteres -> Error 400.
    - `pais` y `ciudad` transformados a mayúsculas antes de almacenar.

## 5. Requisitos de Arquitectura y Separación de Responsabilidades
- **PROHIBIDO** incluir bloques `<script>` con lógica de negocio o Fetch dentro de `public/index.html`.
- **Backend (Node.js/Express):**
  - `server.js`: Punto de entrada del servidor Express y configuración de estáticos.
  - `src/routes/apiRoutes.js`: Definición de rutas Express.
  - `src/controllers/inscripcionesController.js`: Lógica de validación, almacenamiento en memoria y respuesta HTTP.
- **Frontend (Vanilla JS + Tailwind CDN):**
  - `public/index.html`: Solo estructura markup de la UI (formulario y tabla) sin lógica script embebida.
  - `public/js/api.js`: Módulo/Funciones encargadas del consumo de la API REST (`fetch`).
  - `public/js/app.js`: Módulo principal para manipulación del DOM, eventos de formulario y renderizado de tabla.
```

#### 📄 `spec/testing.md`
Crea el archivo `spec/testing.md` copiando y pegando el siguiente contenido:

```markdown
# Especificación de Estrategia de Pruebas (TDD + E2E)

## 1. Pruebas Unitarias (TDD con Node Test Runner / Jest)
Ubicación: `tests/unit/inscripciones.test.js`

Casos de prueba obligatorios para `inscripcionesController.js`:
- **Caso 1 (Éxito):** Registrar inscripción válida. Verificar que `pais` y `ciudad` se conviertan a MAYÚSCULAS.
- **Caso 2 (Error 400):** Rechazar registro si `identidad` no tiene exactamente 10 dígitos numéricos (ej. "12345" o "ABC1234567").
- **Caso 3 (Error 400):** Rechazar registro si `nombre` excede los 25 caracteres.
- **Caso 4 (Error 400):** Rechazar registro si el `cursoId` no existe.

*Estrategia TDD:* Escribir primero las pruebas unitarias basándote en esta spec, ejecutarlas para verificar que fallan (RED), y luego escribir el controlador para hacerlas pasar (GREEN).

## 2. Pruebas End-to-End (E2E con Playwright)
Ubicación: `tests/e2e/registration.spec.js`

Flujo E2E completo a simular:
1. Navegar a `http://localhost:3000`.
2. Verificar que el selector `#cursoId` cargue los cursos predefinidos.
3. Llenar el formulario con datos válidos:
   - Identidad: "0987654321"
   - Nombre: "Carlos"
   - Apellido: "Pérez"
   - País: "ecuador" (en minúsculas en el input)
   - Ciudad: "quito" (en minúsculas en el input)
   - Seleccionar primer curso.
4. Hacer clic en "Guardar Inscripción".
5. Verificar que la tabla de inscritos muestre una nueva fila con:
   - Identidad: "0987654321"
   - Alumno: "Carlos Pérez"
   - Ubicación: "QUITO, ECUADOR" (confirmar conversión a mayúsculas visual)
   - Nombre del curso correspondiente.
```

---

### 3. Estrategia TDD & Prompts para la IA

#### 🤖 Prompt 1: Generación de Pruebas Unitarias (Fase RED)
```text
Lee atentamente spec/requirements.md y spec/testing.md.
Siguiendo el enfoque TDD, genera ÚNICAMENTE el archivo de pruebas unitarias en tests/unit/inscripciones.test.js utilizando el test runner nativo de Node.js (node:test y node:assert). No crees aún el controlador.
```

#### 🤖 Prompt 2: Implementación de Código (Fase GREEN)
```text
Ahora implementa el código del backend (src/controllers/inscripcionesController.js, src/routes/apiRoutes.js, server.js) y del frontend (public/index.html, public/js/api.js, public/js/app.js) para hacer pasar las pruebas unitarias.
Adicionalmente, genera la configuración playwright.config.js y el archivo de prueba E2E en tests/e2e/registration.spec.js según lo especificado en spec/testing.md.
```

---

### 4. Pruebas E2E con Playwright

El script de Playwright simula la interacción real del usuario:
```javascript
test('Flujo completo de inscripción de alumno con validación en UI', async ({ page }) => {
  await page.goto('http://localhost:3000');
  await page.fill('#identidad', '0987654321');
  await page.fill('#nombre', 'Carlos');
  await page.fill('#apellido', 'Pérez');
  await page.fill('#pais', 'ecuador');
  await page.fill('#ciudad', 'quito');
  await page.click('button[type="submit"]');

  const tabla = page.locator('#tablaInscritos');
  await expect(tabla).toContainText('QUITO, ECUADOR');
});
```

---

## 🧪 Ejecución de Pruebas

### Ejecutar Pruebas Unitarias (TDD)
```bash
node --test tests/unit/inscripciones.test.js
```

### Ejecutar Pruebas E2E (Playwright)
```bash
# Ejecución en modo headless
npx playwright test

# Ejecución con interfaz UI interactiva
npx playwright test --ui
```

### Iniciar Aplicación en Desarrollo
```bash
node server.js
# Abrir navegador en: http://localhost:3000
```

---

## ⏱️ Agenda / Timeline (60 min)

| Bloque | Fase | Descripción |
| :--- | :--- | :--- |
| **00:00 - 00:10** | **Intro & Comparativa** | SDD vs. Vibe Coding. El problema del "Monolito Spaghetti". |
| **00:10 - 00:22** | **Fase 1: Especificaciones** | Redacción de `requirements.md` y `testing.md`. |
| **00:22 - 00:35** | **Fase 2: TDD & Código** | Generación de tests unitarios (RED) y código con Antigravity AI (GREEN). |
| **00:35 - 00:50** | **Fase 3: E2E Playwright** | Automatización de navegador y verificación visual. |
| **00:50 - 01:00** | **Cierre & Q&A** | Refactorización segura y mejores prácticas. |

---

## 💡 Preguntas Frecuentes y Buenas Prácticas

1. **¿Por qué usar el Test Runner nativo de Node (`node:test`)?**  
   Para mantener el entorno ultraliviano sin requerir dependencias adicionales como Jest en demos de tiempo limitado.
2. **¿Qué pasa si cambian las reglas de negocio?**  
   Una alternativa es actualizar `spec/requirements.md` y `spec/testing.md`, y le pides a la IA que refactorice código y tests simultáneamente. ¡El contrato sigue mandando!. Como buena práctica se recomienda especificar los cambios en otro archivo .md de tal manera que conservas el requerimiento original y pides que únicamente se incluya los nuevos cambios, usando como contexto el requerimiento inicial.
3. **¿Cómo garantizo que la IA no introduzca código no deseado?**  
   Definiendo explícitamente restricciones de arquitectura en la especificación (ej. "Prohibido scripts embebidos en el HTML").

---

## 📚 Qué puedo aprender a continuación

Para profundizar en el desarrollo guiado por especificaciones y llevar esta metodología a proyectos de escala empresarial, te recomendamos explorar las siguientes herramientas y estándares:

### 🐙 GitHub Spec Kit
**GitHub Spec Kit** es una suite de herramientas e inspiraciones orientadas a estandarizar y estructurar cómo se especifican requisitos y arquitecturas antes de escribir código o delegar tareas a agentes de inteligencia artificial.
- **Ventajas:**
  - Facilita la creación de contratos de software claros y reutilizables.
  - Mejora la alineación entre desarrolladores, QA y modelos/agentes de IA.
  - Promueve buenas prácticas en la documentación técnica y pruebas integradas.
- 🔗 **Sitio oficial / Repositorio:** [GitHub Spec Kit](https://github.com/github/spec-kit) *(o documentación en [github.com](https://github.com))*

### 🌐 OpenSpec
**OpenSpec** es un formato y estándar abierto diseñado para definir especificaciones de aplicaciones y APIs de forma interoperable, legible tanto por humanos como por agentes de IA.
- **Ventajas:**
  - **Interoperabilidad:** Funciona con múltiples herramientas y plataformas sin estar atado a un proveedor específico.
  - **Single Source of Truth:** Permite generar documentación, mocks, validaciones y suites de pruebas automatizadas a partir de una única especificación.
  - **Automatización AI-Native:** Optimizado para que los LLMs y agentes lean los contratos y generen código conforme al estándar.
- 🔗 **Sitio oficial:** [OpenSpec (openspec.io)](https://openspec.io/)

---
¡Gracias por participar en el workshop!

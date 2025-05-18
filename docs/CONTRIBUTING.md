# Guía de Contribución para Randomizer Supreme

¡Gracias por tu interés en contribuir a Randomizer Supreme! Estamos emocionados de ver cómo la comunidad puede ayudar a que este proyecto sea aún más caóticamente maravilloso. Ya sea que estés reportando un error, sugiriendo una nueva característica aleatoria, o escribiendo código, tu ayuda es valiosa.

Esta guía te proporcionará todo lo que necesitas saber para realizar contribuciones efectivas.

## Tabla de Contenidos

*   [Código de Conducta](#código-de-conducta)
*   [Cómo Contribuir](#cómo-contribuir)
    *   [Reportando Errores](#reportando-errores)
    *   [Sugiriendo Mejoras o Nuevas Características](#sugiriendo-mejoras-o-nuevas-características)
    *   [Tu Primera Contribución de Código](#tu-primera-contribución-de-código)
    *   [Contribuciones Mayores](#contribuciones-mayores)
*   [Guía de Desarrollo](#guía-de-desarrollo)
    *   [Configuración del Entorno](#configuración-del-entorno)
    *   [Estructura del Proyecto](#estructura-del-proyecto)
    *   [Estilo de Código](#estilo-de-código)
    *   [Pruebas (Testing)](#pruebas-testing)
    *   [Mensajes de Commit](#mensajes-de-commit)
*   [Proceso de Pull Request (PR)](#proceso-de-pull-request-pr)
*   [Reconocimientos](#reconocimientos)

## Código de Conducta

Este proyecto y todos los que participan en él se rigen por el [Código de Conducta de Randomizer Supreme](CODE_OF_CONDUCT.md). Al participar, se espera que respetes este código. Por favor, reporta cualquier comportamiento inaceptable a [emaildelproyecto@ejemplo.com](mailto:emaildelproyecto@ejemplo.com).

## Cómo Contribuir

Las contribuciones pueden tomar muchas formas. Aquí hay algunas maneras en que puedes ayudar:

### Reportando Errores

Si encuentras un error, un comportamiento inesperado, o algo que simplemente no parece lo suficientemente aleatorio (o es *demasiado* predeciblemente aleatorio), por favor, ¡háznoslo saber!

Antes de crear un reporte de error:

1.  **Busca en los Issues Existentes:** Es posible que alguien ya haya reportado el mismo error. Si es así, puedes añadir información adicional al issue existente.
2.  **Verifica la Versión:** Asegúrate de que estás utilizando la última versión de Randomizer Supreme. El error podría haber sido solucionado en una actualización reciente.
3.  **Intenta Reproducirlo:** Si es posible, intenta reproducir el error de manera consistente. Esto ayudará enormemente a los desarrolladores a identificar y solucionar el problema.

Al crear un reporte de error, por favor incluye la siguiente información:

*   **Título Claro y Descriptivo:** Por ejemplo, "`rs.getInt(1, 10)` devuelve `undefined` cuando la semilla es 'paradoja'".
*   **Versión de Randomizer Supreme:** (ej. `v1.2.3`)
*   **Versión de Node.js:** (ej. `v18.16.0`)
*   **Sistema Operativo:** (ej. `Windows 10`, `macOS Ventura`, `Ubuntu 22.04`)
*   **Pasos Detallados para Reproducir el Error:** Proporciona un fragmento de código mínimo y reproducible que demuestre el error.
*   **Comportamiento Esperado:** ¿Qué esperabas que sucediera?
*   **Comportamiento Actual:** ¿Qué sucedió en realidad? Incluye cualquier mensaje de error o stack trace.
*   **Contexto Adicional (Opcional):** Cualquier otra información que creas que podría ser relevante.

Crea tu reporte de error en la [sección de Issues del repositorio de GitHub](https://github.com/yourusername/randomizer-supreme/issues).

### Sugiriendo Mejoras o Nuevas Características

¿Tienes una idea para una nueva forma de generar aleatoriedad? ¿Una nueva distribución, un nuevo tipo de estructura de datos caótica, o una forma aún más diabólica de manipular datos? ¡Nos encantaría escucharla!

Al sugerir una mejora:

1.  **Busca en los Issues Existentes:** Alguien podría haber sugerido algo similar.
2.  **Describe Claramente tu Idea:**
    *   ¿Qué problema resuelve tu sugerencia o qué nueva capacidad añade?
    *   ¿Cómo funcionaría idealmente desde la perspectiva del usuario (ejemplos de código API)?
    *   ¿Hay casos de uso específicos que tengas en mente?
    *   ¿Existen alternativas o soluciones existentes (incluso en otras bibliotecas)?

Crea tu sugerencia en la [sección de Issues del repositorio de GitHub](https://github.com/yourusername/randomizer-supreme/issues), utilizando una etiqueta como `enhancement` o `feature-request`.

### Tu Primera Contribución de Código

Si eres nuevo contribuyendo a proyectos de código abierto, ¡bienvenido! Randomizer Supreme puede ser un lugar divertido para empezar.

Busca issues etiquetados como `good first issue` o `help wanted`. Estos suelen ser problemas más pequeños o tareas bien definidas que son un buen punto de partida.

No dudes en pedir ayuda si te atascas. Puedes comentar en el issue o unirte a nuestro canal de discusión (si tenemos uno, ¡deberíamos crearlo!).

### Contribuciones Mayores

Si deseas realizar una contribución más grande, como implementar una nueva característica compleja o refactorizar una parte significativa del código, es una buena idea discutirlo primero.

1.  **Abre un Issue:** Describe tu propuesta y por qué crees que sería una buena adición o cambio. Esto permite una discusión temprana con los mantenedores y la comunidad.
2.  **Diseño (si es necesario):** Para características complejas, podría ser útil esbozar un pequeño documento de diseño o discutir la API propuesta.

Esto ayuda a asegurar que tu trabajo esté alineado con la dirección del proyecto y evita que inviertas tiempo en algo que podría no ser aceptado.

## Guía de Desarrollo

### Configuración del Entorno

Para empezar a desarrollar en Randomizer Supreme, necesitarás:

1.  **Node.js y npm/yarn:** Asegúrate de tener una versión reciente de Node.js instalada (preferiblemente la LTS actual o superior). npm viene con Node.js; yarn puede instalarse por separado.
2.  **Git:** Para clonar el repositorio y gestionar las versiones.
3.  **Un Editor de Código:** VS Code, WebStorm, Sublime Text, Vim, etc.

Pasos para configurar:

```bash
# 1. Clona el repositorio
_# Reemplaza yourusername con tu nombre de usuario de GitHub si has hecho un fork
_git clone https://github.com/yourusername/randomizer-supreme.git
cd randomizer-supreme

# 2. Instala las dependencias
npm install
# o si usas yarn
# yarn install

# 3. Ejecuta las pruebas para asegurarte de que todo está configurado correctamente
npm test
# o
# yarn test
```

### Estructura del Proyecto (Ejemplo)

Una estructura típica podría ser:

```
randomizer-supreme/
├── lib/                     # Código fuente principal de la biblioteca
│   ├── core/                # Lógica central, generadores base
│   ├── distributions/       # Implementaciones de distribuciones aleatorias
│   ├── structures/          # Generadores de estructuras de datos complejas
│   └── utils/               # Funciones de utilidad
├── test/                    # Pruebas unitarias e de integración
│   ├── core.test.js
│   └── ...
├── examples/                # Ejemplos de uso
├── docs/                    # Documentación (si se genera aparte)
├── .eslintrc.js             # Configuración de ESLint
├── .gitignore
├── package.json
├── README.md
└── CONTRIBUTING.md
```

Familiarízate con cómo está organizado el código antes de empezar a hacer cambios.

### Estilo de Código

*   **Consistencia:** Intentamos mantener un estilo de código consistente en todo el proyecto.
*   **Linter y Formateador:** Usamos ESLint para el linting y Prettier para el formateo del código. La configuración se encuentra en `.eslintrc.js` y `.prettierrc.js` (o en `package.json`).
*   **Ejecuta el Linter:** Antes de hacer commit, ejecuta `npm run lint` (o `yarn lint`) para verificar si hay problemas de estilo. Algunos problemas pueden ser corregidos automáticamente con `npm run lint:fix`.
*   **Comentarios:** Escribe comentarios claros y concisos donde sea necesario, especialmente para lógica compleja o decisiones de diseño no obvias.
*   **Nombres Descriptivos:** Usa nombres de variables y funciones que sean descriptivos y reflejen su propósito.

### Pruebas (Testing)

¡Las pruebas son cruciales, especialmente para una biblioteca que se basa en la aleatoriedad controlada!

*   **Framework de Pruebas:** Usamos [Jest](https://jestjs.io/) (o el framework que se haya elegido, ej. Mocha, Jasmine).
*   **Cobertura de Código:** Intenta mantener o aumentar la cobertura de código con tus contribuciones. Puedes verificar la cobertura con `npm run coverage`.
*   **Escribe Pruebas Nuevas:**
    *   Para correcciones de errores: Añade una prueba que falle sin tu corrección y pase con ella.
    *   Para nuevas características: Añade pruebas que cubran los diferentes aspectos de la nueva funcionalidad.
*   **Tipos de Pruebas:**
    *   **Pruebas Unitarias:** Prueban unidades aisladas de código (funciones, métodos).
    *   **Pruebas de Integración:** Prueban cómo interactúan diferentes partes del sistema.
    *   **Pruebas de Semilla (Seed Testing):** Para funciones aleatorias, es vital probar que con la misma semilla se obtienen los mismos resultados.
*   **Ejecución de Pruebas:** Ejecuta `npm test` o `yarn test` para correr todas las pruebas.

```javascript
// Ejemplo de una prueba en Jest para una función aleatoria con semilla
describe('Randomizer.getInt()', () => {
  it('debería devolver el mismo número para la misma semilla', () => {
    const rs1 = new Randomizer('test-seed');
    const rs2 = new Randomizer('test-seed');
    expect(rs1.getInt(1, 100)).toBe(rs2.getInt(1, 100));
  });

  it('debería devolver números diferentes para diferentes semillas', () => {
    const rs1 = new Randomizer('seed-a');
    const rs2 = new Randomizer('seed-b');
    expect(rs1.getInt(1, 100)).not.toBe(rs2.getInt(1, 100)); // Podría fallar por casualidad, ¡la aleatoriedad!
  });
});
```

### Mensajes de Commit

Sigue un estilo de mensajes de commit consistente para mantener un historial claro y legible. Recomendamos el formato [Conventional Commits](https://www.conventionalcommits.org/).

**Formato Básico:**

```
<tipo>[ámbito opcional]: <descripción>

[cuerpo opcional]

[footer opcional]
```

*   **Tipos Comunes:**
    *   `feat`: Una nueva característica.
    *   `fix`: Una corrección de error.
    *   `docs`: Cambios en la documentación.
    *   `style`: Cambios que no afectan el significado del código (espacios, formato, etc.).
    *   `refactor`: Un cambio de código que no corrige un error ni añade una característica.
    *   `perf`: Un cambio de código que mejora el rendimiento.
    *   `test`: Añadir pruebas faltantes o corregir pruebas existentes.
    *   `chore`: Cambios en el proceso de build, herramientas auxiliares, etc.

**Ejemplos:**

```
feat(generator): añadir generador de números de Fibonacci aleatorios

Implementa rs.getFibonacci(maxLength) para generar secuencias.
```

```
fix(rng): corregir problema de distribución sesgada en getFloat con semilla específica

El algoritmo anterior no distribuía uniformemente los valores de punto flotante
cuando se usaba una semilla que resultaba en un estado interno particular.

Closes #123
```

## Proceso de Pull Request (PR)

Una vez que tus cambios estén listos y probados, es hora de crear un Pull Request.

1.  **Haz Commit de tus Cambios:** Asegúrate de que tus mensajes de commit sean claros (ver [Mensajes de Commit](#mensajes-de-commit)).
2.  **Haz Push a tu Fork:** Sube tus cambios a tu fork del repositorio en GitHub.
    ```bash
    git push origin tu-rama-de-caracteristica
    ```
3.  **Abre un Pull Request:**
    *   Ve al repositorio original de Randomizer Supreme en GitHub.
    *   Verás un mensaje sugiriendo crear un PR desde tu rama recién subida. Haz clic en él.
    *   **Base:** La rama principal del proyecto (ej. `main` o `master`).
    *   **Compare:** Tu rama con los cambios.
    *   **Título del PR:** Claro y descriptivo, siguiendo el formato de Conventional Commits si es posible.
    *   **Descripción del PR:**
        *   Resume los cambios realizados.
        *   Enlaza cualquier issue relevante (ej. `Closes #123`, `Fixes #456`).
        *   Describe cómo has probado tus cambios.
        *   Añade capturas de pantalla o GIFs si es relevante (especialmente para cambios visuales, aunque menos común para una biblioteca como esta).
4.  **Revisión de Código:**
    *   Los mantenedores revisarán tu PR. Pueden solicitar cambios o hacer preguntas.
    *   Participa en la discusión y realiza los cambios solicitados.
    *   Las pruebas automatizadas (CI/CD) también se ejecutarán en tu PR. Asegúrate de que pasen.
5.  **Merge:** Una vez que el PR sea aprobado y todas las comprobaciones pasen, un mantenedor lo fusionará con la rama principal.

¡Felicidades y gracias por tu contribución!

## Reconocimientos

Todas las contribuciones, grandes o pequeñas, serán reconocidas. Podríamos tener una sección en el `README.md` o un archivo `CONTRIBUTORS.md` para agradecer a todos los que han ayudado a hacer de Randomizer Supreme la maravilla caótica que es.

---

Si tienes alguna pregunta sobre el proceso de contribución, no dudes en abrir un issue o contactar a los mantenedores.

*¡Feliz aleatorización!*

# Randomizer Supreme

[![NPM Version](https://img.shields.io/npm/v/randomizer-supreme.svg)](https://www.npmjs.com/package/randomizer-supreme)
[![NPM Downloads](https://img.shields.io/npm/dm/randomizer-supreme.svg)](https://www.npmjs.com/package/randomizer-supreme)
[![Build Status](https://img.shields.io/travis/com/yourusername/randomizer-supreme.svg)](https://travis-ci.com/yourusername/randomizer-supreme)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Randomizer Supreme** es una biblioteca de Node.js versátil y potente diseñada para inyectar un delicioso caos y aleatoriedad en tus aplicaciones. Si necesitas generar datos impredecibles, simular comportamientos erráticos o simplemente añadir un toque de anarquía digital, Randomizer Supreme es tu herramienta ideal.

## Descripción Detallada

Este paquete no es para los débiles de corazón. Va más allá de la simple generación de números aleatorios. Randomizer Supreme ofrece un conjunto completo de herramientas para crear escenarios complejos y aleatorios, desde la generación de estructuras de datos anidadas y caóticas hasta la simulación de eventos de red no deterministas y la manipulación aleatoria de flujos de datos.

**Advertencia:** El uso excesivo de Randomizer Supreme puede llevar a resultados inesperados y a una profunda contemplación sobre la naturaleza del orden y el caos. Úsalo bajo tu propio riesgo.

## Características Principales

*   **Generación Aleatoria Avanzada:**
    *   Números aleatorios con diversas distribuciones (Uniforme, Gaussiana, Poisson, Exponencial, etc.).
    *   Cadenas de texto aleatorias con control sobre juegos de caracteres, longitud y patrones.
    *   Booleanos aleatorios con pesos configurables.
    *   Fechas y horas aleatorias dentro de rangos específicos o con patrones temporales.
*   **Estructuras de Datos Caóticas:**
    *   Generación de arrays con elementos aleatorios de tipos mixtos.
    *   Creación de objetos con claves y valores generados aleatoriamente, incluyendo anidamiento profundo.
    *   Generación de árboles y grafos con estructuras y conexiones aleatorias.
*   **Simulación de Eventos Impredecibles:**
    *   Simulación de latencia de red aleatoria.
    *   Introducción de errores aleatorios en flujos de datos.
    *   Disparadores de eventos aleatorios basados en tiempo o condiciones.
*   **Manipulación Aleatoria:**
    *   Selección aleatoria de elementos de arrays u objetos.
    *   Barajado aleatorio de colecciones.
    *   Mutación aleatoria de cadenas o estructuras de datos.
*   **Modo "Caos Total":** Una función especial que aplica una serie de operaciones aleatorias a un conjunto de datos de entrada, garantizando resultados verdaderamente impredecibles.
*   **Sembrado Controlado:** Permite la reproducibilidad de secuencias aleatorias para pruebas y depuración (si te atreves a intentar controlar el caos).
*   **Extensibilidad:** API para definir tus propios generadores y manipuladores aleatorios personalizados.

## Instalación

Instala Randomizer Supreme usando npm:

```bash
npm install randomizer-supreme
```

O con yarn:

```bash
yarn add randomizer-supreme
```

## Uso Básico

```javascript
const Randomizer = require('randomizer-supreme');

// Inicializar con una semilla para resultados reproducibles (opcional)
const seed = 'elCaosEsMiPastor';
const rs = new Randomizer(seed);

// Generar un número aleatorio entre 1 y 100
const randomNumber = rs.getInt(1, 100);
console.log(`Número aleatorio: ${randomNumber}`);

// Generar una cadena aleatoria de 10 caracteres alfanuméricos
const randomString = rs.getString(10, 'alphanumeric');
console.log(`Cadena aleatoria: ${randomString}`);

// Generar un booleano con un 70% de probabilidad de ser true
const randomBoolean = rs.getBoolean(0.7);
console.log(`Booleano aleatorio: ${randomBoolean}`);

// Generar un array de 5 elementos con tipos mixtos
const randomArray = rs.getArray(5, ['int', 'string', 'boolean']);
console.log('Array aleatorio:', randomArray);
```

## Uso Avanzado: Desatando el Caos

### Ejemplo 1: Generar un Objeto de Configuración Caótico

```javascript
const Randomizer = require('randomizer-supreme');
const rs = new Randomizer();

const chaoticConfig = rs.getObject({
    depth: 3, // Profundidad máxima de anidamiento
    maxKeys: 5, // Máximo de claves por objeto
    keyTypes: ['string'],
    valueTypes: ['int', 'string', 'boolean', 'null', 'object', 'array'],
    arrayConfig: {
        maxLength: 4,
        elementTypes: ['int', 'string']
    }
});

console.log('Configuración Caótica Generada:');
console.dir(chaoticConfig, { depth: null });
```

Este ejemplo generará un objeto JavaScript con hasta 3 niveles de anidamiento. Cada nivel tendrá un número aleatorio de claves (hasta 5), y los valores pueden ser de tipos primitivos, otros objetos o arrays. Los arrays internos también tendrán una longitud y tipos de elementos aleatorios.

### Ejemplo 2: Simular un Flujo de Datos Corrupto

```javascript
const Randomizer = require('randomizer-supreme');
const rs = new Randomizer();

function processData(data) {
    // Simular corrupción de datos en un 15% de los casos
    if (rs.getBoolean(0.15)) {
        const corruptionType = rs.getChoice(['bitflip', 'truncate', 'injectNoise']);
        let corruptedData = data;

        switch (corruptionType) {
            case 'bitflip':
                // Voltear un bit aleatorio en una cadena (simplificado)
                if (typeof data === 'string' && data.length > 0) {
                    const index = rs.getInt(0, data.length - 1);
                    const charCode = data.charCodeAt(index);
                    corruptedData = data.substring(0, index) +
                                   String.fromCharCode(charCode ^ (1 << rs.getInt(0, 7))) +
                                   data.substring(index + 1);
                }
                console.warn('¡Datos corrompidos (bitflip)!');
                break;
            case 'truncate':
                // Truncar los datos a una longitud aleatoria
                if (typeof data === 'string' && data.length > 1) {
                    corruptedData = data.substring(0, rs.getInt(1, data.length -1));
                }
                console.warn('¡Datos corrompidos (truncate)!');
                break;
            case 'injectNoise':
                // Añadir ruido aleatorio
                if (typeof data === 'string') {
                    corruptedData += rs.getString(5, 'symbols');
                }
                console.warn('¡Datos corrompidos (injectNoise)!');
                break;
        }
        return corruptedData;
    }
    return data;
}

let mySensitiveData = "Este es un mensaje muy importante que no debe alterarse.";
console.log('Original:', mySensitiveData);

for (let i = 0; i < 5; i++) {
    mySensitiveData = processData(mySensitiveData);
    console.log(`Procesado ${i+1}:`, mySensitiveData);
}
```

Este ejemplo muestra cómo se puede usar Randomizer Supreme para simular la corrupción de datos en un flujo de procesamiento.

### Ejemplo 3: El Modo "Caos Total"

```javascript
const Randomizer = require('randomizer-supreme');
const rs = new Randomizer();

const initialData = {
    id: 1,
    name: "Objeto Ordenado",
    values: [10, 20, 30],
    active: true,
    metadata: {
        timestamp: new Date().toISOString(),
        source: "manual"
    }
};

console.log("Datos Iniciales:");
console.dir(initialData, {depth: null});

const utterlyChaoticData = rs.totalChaos(initialData, {
    iterations: rs.getInt(3, 7), // Aplicar entre 3 y 7 transformaciones aleatorias
    mutationProbability: 0.6, // Probabilidad de que un valor sea mutado
    structuralChangeProbability: 0.4 // Probabilidad de cambios estructurales (añadir/quitar claves)
});

console.log("\nDatos Después del Caos Total:");
console.dir(utterlyChaoticData, {depth: null});
```
El modo `totalChaos` toma un objeto o array de entrada y le aplica una serie de transformaciones aleatorias, incluyendo mutación de valores, adición/eliminación de claves/elementos, y cambio de tipos de datos.

## API de Randomizer Supreme

La instancia de `Randomizer` expone los siguientes métodos (lista no exhaustiva):

### Generadores Básicos

*   `getInt(min, max)`: Devuelve un entero aleatorio en el rango `[min, max]`.
*   `getFloat(min, max, decimals?)`: Devuelve un número de punto flotante aleatorio.
*   `getString(length, charset?)`: Devuelve una cadena aleatoria. `charset` puede ser `'alphanumeric'`, `'alpha'`, `'numeric'`, `'hex'`, `'symbols'`, o un string personalizado.
*   `getBoolean(trueWeight?)`: Devuelve `true` o `false`. `trueWeight` es la probabilidad de `true` (defecto 0.5).
*   `getDate(startDate?, endDate?)`: Devuelve un objeto `Date` aleatorio.
*   `getChoice(array)`: Devuelve un elemento aleatorio de `array`.
*   `shuffle(array)`: Baraja `array` in-place y lo devuelve.

### Generadores de Estructuras

*   `getArray(length?, config?)`: Genera un array aleatorio.
    *   `length`: Longitud fija o un objeto `{min: number, max: number}`.
    *   `config.elementTypes`: Array de tipos de elementos (ej: `['int', 'string', {type: 'object', config: nestedObjectConfig}]`).
    *   `config.elementGenerator`: Función `(index) => value` para generación personalizada.
*   `getObject(config?)`: Genera un objeto aleatorio.
    *   `config.depth`: Profundidad máxima de anidamiento.
    *   `config.minKeys`, `config.maxKeys`: Número de claves.
    *   `config.keyTypes`: Tipos para las claves (generalmente `['string']`).
    *   `config.keyGenerator`: Función para generar claves.
    *   `config.valueTypes`: Tipos para los valores, similar a `elementTypes` de `getArray`.
    *   `config.valueGenerator`: Función `(key) => value` para generación personalizada.

### Manipuladores y Simuladores

*   `mutate(data, config?)`: Aplica mutaciones aleatorias a `data`.
    *   `config.probability`: Probabilidad de mutación por elemento/propiedad.
    *   `config.mutators`: Objeto que define funciones de mutación por tipo de dato.
*   `simulateNetworkDelay(minMs, maxMs)`: Devuelve una Promesa que se resuelve después de un tiempo aleatorio.
*   `injectError(data, probability, errorGenerator?)`: Intenta inyectar un error en `data`.
*   `totalChaos(data, config?)`: Aplica una secuencia de transformaciones aleatorias intensivas.
    *   `config.iterations`: Número de pases de transformación.
    *   `config.mutationProbability`: Probabilidad de mutar valores existentes.
    *   `config.structuralChangeProbability`: Probabilidad de añadir/eliminar/reordenar elementos o propiedades.
    *   `config.typeChangeProbability`: Probabilidad de cambiar el tipo de un valor.

### Control

*   `setSeed(seed)`: Establece la semilla para el generador de números pseudoaleatorios.
*   `getState()`: Devuelve el estado interno del generador (para guardar y restaurar).
*   `setState(state)`: Restaura un estado previamente guardado.

## Casos de Uso Avanzados

*   **Pruebas de Robustez (Fuzz Testing):** Genera entradas inesperadas y malformadas para probar la estabilidad de tus aplicaciones.
*   **Generación de Datos de Prueba Complejos:** Crea grandes volúmenes de datos de prueba realistas pero aleatorios para bases de datos y APIs.
*   **Simulaciones Monte Carlo:** Utiliza las diversas distribuciones para modelar sistemas complejos.
*   **Arte Generativo y Contenido Procedural:** Crea patrones, texturas o narrativas impredecibles.
*   **Gamificación del Caos:** Introduce elementos aleatorios e impredecibles en aplicaciones para mantener a los usuarios alerta (¡o frustrados!).
*   **Seguridad:** Simula ataques o comportamientos anómalos para probar sistemas de detección de intrusos.

## Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas para nuevas funciones aleatorias, mejoras en el caos existente, o encuentras una forma de hacer que Randomizer Supreme sea aún más impredecible, por favor, abre un issue o envía un pull request.

1.  Haz un fork del repositorio.
2.  Crea una nueva rama (`git checkout -b feature/nueva-aleatoriedad-cosmica`).
3.  Realiza tus cambios.
4.  Asegúrate de que los tests pasen (o añade nuevos tests para tu nueva aleatoriedad).
5.  Envía un Pull Request.

## Próximas Características (A merced del Azar)

*   Integración con WebAssembly para un rendimiento aleatorio aún más rápido.
*   Generadores de funciones aleatorias (funciones que se escriben a sí mismas de forma aleatoria).
*   Un "Oráculo del Caos" que proporciona predicciones aleatorias sobre el futuro de tu proyecto.
*   Soporte para aleatoriedad cuántica (si podemos encontrar un generador de números cuánticos verdaderamente aleatorios y barato).

## Licencia

Randomizer Supreme se distribuye bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.

---

*Que la aleatoriedad te acompañe.*

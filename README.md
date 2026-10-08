# Generador Procedural de Islas

Proyecto experimental desarrollado con Three.js para generar islas de forma procedural utilizando montañas, dunas y ruido Simplex.

## Características

- Terreno generado mediante malla de 101x101 vértices.
- Montañas con altura y radio aleatorios.
- Dunas independientes del relieve principal.
- Uso de ruido Simplex para añadir irregularidades naturales.
- Nivel del mar configurable.
- Control libre de cámara mediante OrbitControls.
- Sistema de semillas para regenerar siempre el mismo mundo.
- Preparado para futuras expansiones como:
  - Bosques
  - Ríos
  - Biomas
  - Volcanes
  - Pueblos
  - Erosión

## Tecnologías

- Three.js
- Simplex Noise
- JavaScript ES Modules

## Cómo funciona

El terreno se construye a partir de una malla plana.

Cada montaña se define mediante:

- Posición
- Altura
- Radio

Posteriormente se aplica una función gaussiana para calcular la influencia de cada montaña sobre los vértices cercanos.

```js
mountain(
    x,
    y,
    centerX,
    centerY,
    height,
    radius
);
```

El ruido Simplex se añade después para romper la forma perfecta de las montañas y obtener un aspecto más natural.

## Sistema de semillas

El proyecto utiliza un generador pseudoaleatorio basado en semillas.

Esto permite generar exactamente la misma isla introduciendo la misma semilla.

Ejemplo:

```js
const seed = "MiIsla123";
```

Dos ejecuciones con la misma semilla producirán el mismo terreno.

## Controles

### Ratón

- Botón izquierdo: rotar cámara
- Botón derecho: mover cámara
- Rueda: zoom

## Estado actual

Actualmente el proyecto genera:

- Terreno principal
- Montañas
- Dunas
- Agua
- Arena

## Próximos objetivos

- Optimización de generación procedural.
- Distribución inteligente de montañas.
- Coloreado según altura.
- Generación de costas.
- Sistema de biomas.
- Vegetación procedural.
- Erosión y suavizado del terreno.

## Capturas

Pendiente.

## Autor

Proyecto personal de aprendizaje sobre generación procedural y gráficos 3D con Three.js.

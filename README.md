# Generador Procedural de Islas

Generador de islas 3D procedural desarrollado con Three.js.

El proyecto crea terrenos utilizando una combinación de montañas gaussianas, ruido Simplex y modificadores de forma para generar islas reproducibles mediante semillas.

---

## Características actuales

- Generación procedural de terreno.
- Sistema de semillas reproducibles.
- Montañas de distintos tamaños.
- Dunas independientes.
- Ruido Simplex para irregularidades naturales.
- Control del nivel del mar.
- Control de redondez de la isla.
- Generación instantánea desde interfaz gráfica.
- Cámara libre mediante OrbitControls.
- Arena, agua y terreno renderizados por separado.

---

## Tecnologías

- Three.js
- Simplex Noise
- JavaScript ES Modules
- OrbitControls

---

## Controles

### Cámara

- Click izquierdo: rotar
- Click derecho: desplazar
- Rueda del ratón: zoom

### Panel lateral

#### Nivel del agua

Permite modificar la altura del mar en tiempo real.

#### Redondez de la isla

Controla cuánto se atenúa el relieve conforme se acerca al borde del mapa.

Valores bajos:

- Islas más irregulares.
- Bordes más agresivos.

Valores altos:

- Forma más circular.
- Costas más suaves.

#### Semilla

Permite regenerar exactamente el mismo mundo.

Ejemplo:

```text
MiIsla123
```

Cualquier semilla generará siempre el mismo resultado.

#### Semilla aleatoria

Genera automáticamente una nueva semilla y reconstruye el terreno.

---

## Funcionamiento

### Montañas

Cada montaña se representa mediante:

```js
{
    x,
    y,
    altura,
    radio
}
```

Su influencia sobre el terreno se calcula utilizando una distribución gaussiana:

```js
height * Math.exp(
    -(dx * dx + dy * dy) /
    (2 * radius * radius)
);
```

Esto permite obtener perfiles de montaña suaves y naturales.

---

### Ruido Simplex

Se agrega ruido Simplex para romper la forma perfecta de las montañas:

```js
noise(x * 0.01, y * 0.01)
```

Esto añade detalles y variaciones al relieve.

---

### Máscara de isla

El borde de la isla se genera mediante una función Smoothstep:

```js
smoothstep(
    0.6,
    1,
    distanciaNormalizada
);
```

Esto hace que el terreno pierda altura progresivamente hasta alcanzar el nivel del mar.

---

## Estructura del terreno

El escenario se compone de tres elementos:

### Terreno

- Montañas
- Relieve principal
- Forma general de la isla

### Arena

- Dunas independientes
- Relieve suave

### Agua

- Plano transparente
- Nivel configurable

---

## Rendimiento

La generación utiliza listas de montañas y dunas:

```js
[
    {
        x,
        y,
        altura,
        radio
    }
]
```

en lugar de recorrer mapas completos de 101x101 posiciones.

Esto reduce enormemente el número de cálculos necesarios para construir el terreno.

---

## Próximas mejoras

### Terreno

- Coloreado por altura.
- Biomas.
- Acantilados.
- Cordilleras.
- Volcanes.

### Naturaleza

- Árboles.
- Bosques.
- Rocas.
- Vegetación procedural.

### Mundo

- Ríos.
- Lagos.
- Cuevas.
- Archipiélagos.

### Optimización

- Spatial partitioning.
- Chunk generation.
- Level of Detail (LOD).

---

## Capturas

## Capturas

### Vista general

screenshots/isla1.png

### Diferente semilla

screenshots/isla2.png

### Panel de control

screenshots/controles.png
``

## Autor Daniel Diaz Ramirez

Proyecto personal desarrollado con fines de aprendizaje sobre:

- Generación procedural.
- Matemáticas aplicadas a terrenos.
- Three.js.
- Renderizado 3D en navegador.

# Planilla Cotización

Cotización libre de proyectos GL (zona norte: Antofagasta, Arica, Calama, Copiapó, Iquique). El contratista ingresa sus precios por ítem y la app calcula la diferencia contra el precio Base Renova, agregándola como Mano de Obra Industrial (MOI) por categoría.

Repositorio independiente, extraído de [nota-de-venta-abastible](https://github.com/devece/nota-de-venta-abastible).

## Archivos

- `Planilla_Cotizacion.html` — aplicación (una sola página, sin backend).
- `base_datos.xlsx` — base de precios por centro/categoría. La app la carga con `fetch()` al abrir la página; para actualizar precios basta con reemplazar este archivo (misma estructura de columnas: `descripción`, `código`, `categoria`, `unidad_medida`, `centro`, `precio`; una hoja por categoría).
- `libs/exceljs.min.js` — librería usada para exportar la cotización a Excel.

## Despliegue

Pensado para Vercel como sitio estático. `vercel.json` redirige `/` a la app.

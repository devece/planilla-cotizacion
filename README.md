# Planilla Cotización

Cotización libre de proyectos GL (zona norte: Antofagasta, Arica, Calama, Copiapó, Iquique). El contratista ingresa sus precios por ítem y la app calcula la diferencia contra el precio Base Renova, agregándola como Mano de Obra Industrial (MOI) por categoría.

Repositorio independiente, extraído de [nota-de-venta-abastible](https://github.com/devece/nota-de-venta-abastible).

## Archivos

- `Planilla_Cotizacion.html` — aplicación (una sola página, sin backend).
- `base_datos.xlsx` — base de precios por centro/categoría. La app la carga con `fetch()` al abrir la página; para actualizar precios basta con reemplazar este archivo (misma estructura de columnas: `descripción`, `código`, `categoria`, `unidad_medida`, `diametro`, `centro`, `precio`; una hoja por categoría).
- `impovar.xlsx` — planilla trimestral nativa de Impovar con el material de cañería de cobre (hoja "MATERIAL CAÑERIAS", igual formato que en [nota-de-venta-abastible](https://github.com/devece/nota-de-venta-abastible)). Al ingresar cantidad en un ítem de CAÑERIAS AP/MP/BP, la app agrega automáticamente una subfila con el material Impovar del mismo diámetro (metros = cantidad × 1.05 redondeado a tira de 6m), al mismo precio en Renova y Contratista (pass-through, sin MOI). Para actualizar precios basta con reemplazar este archivo.
- `contratistas.xlsx` — listado de contratistas (columnas `Código Proveedor`, `Rut`, `Razón Social`, `Nombre representante`, `Zona`, `Jefe de Proyectos`, `Correo Electronico`, `Telefono`; una o más hojas). La app la carga con `fetch()` y usa sólo los registros de la zona `Norte Grande` (constante `ZONA_APP` en `Planilla_Cotizacion.html`) para autocompletar Nombre/Contacto/Teléfono al ingresar el N° de Proveedor.
- `libs/exceljs.min.js` — librería usada para exportar la cotización a Excel.

## Despliegue

Pensado para Vercel como sitio estático. `vercel.json` redirige `/` a la app.

# Calculadora de presupuestos de escapes

Aplicación web sencilla para estimar el precio de fabricar tramos de escape en acero inoxidable. Esta primera versión se ejecuta en el navegador y no requiere instalación, cuenta ni servidor.

## Cómo abrirla

Abre [`outputs/calculadora-escapes.html`](outputs/calculadora-escapes.html) en un navegador moderno. Los valores que cambies se guardan en el almacenamiento local de ese navegador. **Nuevo** restaura los valores iniciales. **Imprimir / PDF** permite imprimir o guardar el resumen; **Copiar resumen** copia el desglose.

## Documentación

- [Análisis de requisitos](docs/analisis-requisitos.md)
- [Casos de uso](docs/casos-de-uso.md)
- [Funcionalidades](docs/funcionalidades.md)
- [Flujo de la aplicación](docs/flujo-app.md)
- [Guía de edición y modularización](docs/guia-edicion-modularizacion.md)

## Estructura y documentación del código

- `outputs/calculadora-escapes.html`: interfaz, estilos y lógica en un único archivo.
- `README.md`: introducción y visión general del proyecto.
- `docs/analisis-requisitos.md`: objetivo, requisitos funcionales y no funcionales, y reglas de cálculo.
- `docs/casos-de-uso.md`: actores y recorridos paso a paso.
- `docs/funcionalidades.md`: funciones disponibles y límites actuales.
- `docs/flujo-app.md`: diagrama y secuencia de uso y cálculo.
- `docs/guia-edicion-modularizacion.md`: pasos para editar el HTML y dividirlo en módulos más adelante.
- Este README también recoge los límites de la versión actual y el plan de escalabilidad.

El HTML incluye comentarios para orientar por secciones. Los comentarios del JavaScript describen el cálculo, la representación del resumen, la interacción y el guardado local. La lógica se mantiene en el mismo archivo porque esta versión no requiere compilación.

## Catálogo y precios

Proveedor de referencia: [Weldracingparts](https://weldracingparts.com/es/). El HTML enlaza productos y categorías con algunos precios observados como orientación. Comprueba siempre la variante concreta, longitud, diámetro, disponibilidad, IVA y envío. El campo de €/m lo introduce el taller: no se deduce automáticamente del precio publicado para una pieza.

## Límites de la primera versión

- Los precios mostrados como referencia están escritos en el HTML y no se actualizan solos.
- El coste es genérico; aún no hay una lista de materiales distinta para cada tipo de tramo.
- El precio del downpipe se introduce manualmente y depende del vehículo y la conexión.
- No se guardan varios clientes, vehículos o presupuestos. Solo se conservan las entradas del último cálculo en el navegador actual.
- No hay PDF con logotipo, número de presupuesto, datos fiscales, validez ni condiciones comerciales.
- La doble salida define la configuración, pero puntas, bifurcaciones y piezas relacionadas se añaden como otros materiales.

## Plan de escalabilidad

### Etapa 1 — Mejorar el cálculo del taller

- Añadir un catálogo configurable de tubo recto, codos, bridas, flexos, silenciosos, puntas, abrazaderas y consumibles.
- Asociar precio y referencia a diámetro, espesor, acabado, unidad y proveedor.
- Crear plantillas para línea completa, tramo intermedio y tramo final simple o doble.
- Separar número de salidas, puntas y silenciosos para representar configuraciones reales.
- Añadir desperdicio de material, preparación y ajuste de complejidad.

### Etapa 2 — Presupuestos reutilizables

- Añadir datos de cliente y vehículo, notas y alcance del trabajo.
- Crear presupuestos con identificador, fecha, caducidad, estado y detalle visible para el cliente.
- Guardar varios presupuestos, duplicarlos y modificarlos.
- Exportar un PDF con logotipo, datos del taller, condiciones, IVA y aceptación del cliente.
- Importar y exportar catálogo y tarifas mediante CSV o JSON.

### Etapa 3 — Catálogo conectado y mantenimiento

- Normalizar referencias, descripción, medidas, coste neto, IVA, proveedor, URL y fecha de revisión.
- Actualizar precios por importación o integración permitida; no depender de extraer páginas de la tienda sin comprobar sus condiciones y estabilidad.
- Mostrar la fecha de actualización y avisar cuando un coste necesite revisión.
- Mantener un historial de precios para explicar cambios entre presupuestos.

### Etapa 4 — Varios dispositivos y usuarios

- Sustituir el guardado local por una API y una base de datos cuando se necesite compartir presupuestos.
- Añadir autenticación, permisos por taller, copias de seguridad y registro de cambios.
- Mantener la interfaz separada de las reglas de cálculo para admitir clientes web o móvil.
- Guardar en cada presupuesto una instantánea de costes y reglas para conservar el importe ofertado.

### Arquitectura sugerida cuando crezca

1. **Interfaz**: formulario, validación y desglose; sin precios de catálogo fijos.
2. **Cálculo**: funciones independientes para cantidades, costes, margen e impuestos.
3. **Catálogo**: materiales, unidades, proveedores, referencias y precios fechados.
4. **Persistencia**: presupuestos y clientes en una base de datos cuando deban compartirse entre dispositivos.
5. **Exportación**: PDF a partir de una instantánea para conservar exactamente lo ofertado.

## Criterios de aceptación sugeridos

- Cambiar cantidades, costes, horas, margen o IVA actualiza desglose y total.
- La doble salida no cambia los silenciosos; el usuario indica las unidades reales.
- El downpipe suma coste y horas solo al activarlo en línea completa.
- El cálculo sigue las fórmulas documentadas y presenta los importes como moneda.
- Al recargar el mismo navegador se restauran las entradas; **Nuevo** las limpia.
- El resumen impreso incluye tipo de trabajo, medidas, desglose e importe total.

## Glosario breve

- **Almacenamiento local**: espacio que ofrece el navegador para guardar datos en ese dispositivo; no se sincroniza con otros navegadores.
- **API**: interfaz que permite que dos programas intercambien datos, por ejemplo la aplicación y un servidor.
- **Base de datos**: sistema organizado para guardar y consultar información como clientes, materiales y presupuestos.
- **CSV / JSON**: formatos de archivo habituales para importar y exportar tablas o datos estructurados.



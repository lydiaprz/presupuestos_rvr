# Guía de edición y modularización

## Cómo editar la versión actual

La aplicación está concentrada en `index.html`; puedes editarla con un editor de texto o código y volver a abrirla en el navegador.

- **Textos y campos**: modifica el HTML. Cada entrada tiene un `id` que usa el JavaScript; si cambias un `id`, actualízalo también en `ids` y en las referencias `$()` del script.
- **Apariencia**: edita las reglas dentro de `<style>`. Las reglas `@media(max-width:760px)` adaptan la interfaz a móvil y `@media print` prepara la impresión.
- **Precios iniciales**: cambia los atributos `value` de los campos. Son valores de partida, no una tarifa sincronizada con el proveedor.
- **Reglas de cálculo**: edita `calc()`. Mantén cada coste como una partida explícita y actualiza el desglose si añades una nueva.
- **Interacciones**: el bloque que registra `addEventListener` y `onclick` conecta los campos con el recálculo, el botón Nuevo y la copia del resumen.
- **Guardar nuevos campos**: añade su `id` a `ids`; así se incluyen en la recuperación y guardado local.

Después de editar, abre el HTML en el navegador y comprueba manualmente los tres tipos de trabajo, la opción de downpipe, la salida doble, el IVA y la impresión. Evita reutilizar un mismo `id` en dos controles: el navegador y el script esperan que cada `id` sea único.

## Modularización futura

Cuando el archivo resulte difícil de mantener, conviene dividirlo por responsabilidad. Una posible estructura, sin cambiar aún la tecnología, sería:

```text
presupuestos_rvr/
├── index.html                 # Estructura de la página
├── README.md                  # Requisitos, flujo y mantenimiento
├── css/
│   └── app.css                # Diseño, móvil e impresión
└── js/
    ├── app.js                 # Eventos e inicio de la aplicación
    ├── calculator.js          # Fórmulas puras del presupuesto
    ├── catalog.js             # Materiales, tarifas y referencias
    ├── storage.js             # Guardado y recuperación local
    └── quote.js               # Resumen, copia e impresión
```

Orden recomendado para dividirla sin mezclar cambios grandes:

1. Mover primero los estilos a `css/app.css` y enlazarlos desde `index.html`.
2. Extraer las fórmulas a `js/calculator.js`. Esa parte debe recibir datos y devolver un desglose, sin leer ni modificar el DOM.
3. Mover precios y referencias a `js/catalog.js`; incluir unidades y fecha de revisión de cada precio.
4. Mover `localStorage` a `js/storage.js`, con funciones separadas para cargar, guardar y limpiar.
5. Dejar `js/app.js` como coordinador de eventos y actualización de pantalla; trasladar la copia y formato de impresión a `js/quote.js`.
6. Mantener los mismos resultados en cada paso y validar la aplicación antes de añadir funciones nuevas.

Si se usan módulos nativos de JavaScript (`import` / `export`), algunos navegadores restringen su apertura directa con `file://`. En ese momento, sirve la carpeta con un servidor local de desarrollo. Un backend y una base de datos solo hacen falta cuando el usuario necesite cuentas, compartir presupuestos o sincronizar varios dispositivos.




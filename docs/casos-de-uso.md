# Casos de uso

## Actores

- **Operario del taller**: configura el trabajo y prepara el presupuesto.
- **Cliente**: recibe el resumen copiado o impreso; no interactúa directamente con la aplicación en esta versión.
- **Navegador**: conserva los campos del último cálculo en almacenamiento local.

## CU-01 — Crear una estimación

**Actor principal:** Operario del taller  
**Precondición:** La página está abierta.

**Flujo principal:**

1. El operario selecciona línea completa, tramo intermedio o tramo final.
2. Introduce diámetro, longitud de tubo, número de codos, horas y tarifa.
3. Añade silenciosos, otros materiales y consumibles que correspondan.
4. La aplicación actualiza el desglose, el precio antes de IVA y el total con IVA.
5. El navegador guarda las entradas del cálculo.

**Resultado:** Se muestra una estimación desglosada para el trabajo configurado.

## CU-02 — Añadir un downpipe

**Actor principal:** Operario del taller  
**Precondición:** Está seleccionada la línea completa.

**Flujo principal:**

1. El operario activa **Incluir downpipe**.
2. Introduce el coste de sus piezas y las horas adicionales.
3. La aplicación añade ambos conceptos al coste de materiales y mano de obra.

**Alternativa:** En los otros tipos de trabajo no se muestra la opción de downpipe.

## CU-03 — Configurar una o dos salidas

**Actor principal:** Operario del taller  
**Precondición:** Está seleccionado el tramo final.

**Flujo principal:**

1. El operario elige una salida o doble salida.
2. Introduce por separado el número real de silenciosos y su coste.
3. La aplicación refleja el tipo de salida en el resumen.

**Regla:** La doble salida no duplica automáticamente los silenciosos ni otros componentes. El operario debe añadir las cantidades reales en sus campos.

## CU-04 — Ajustar precios y condiciones

**Actor principal:** Operario del taller

1. El operario modifica precios unitarios, consumibles, herrajes, tarifa por hora, margen o IVA.
2. La aplicación recalcula el presupuesto y guarda los campos modificados en el navegador.

## CU-05 — Recuperar un cálculo anterior

**Actor principal:** Operario del taller

1. El operario vuelve a abrir o recarga la página en el mismo navegador.
2. La aplicación recupera las entradas guardadas y reconstruye el cálculo.

**Alternativa:** Si el navegador no permite almacenamiento local o los datos no se pueden leer, se utilizan los valores iniciales.

## CU-06 — Copiar el resumen

**Actor principal:** Operario del taller

1. El operario pulsa **Copiar resumen**.
2. La aplicación copia el tipo de trabajo, descripción y desglose al portapapeles.
3. El operario pega el texto en su canal de comunicación o documento habitual.

**Alternativa:** Si el navegador no concede acceso al portapapeles, la aplicación muestra que la copia no está disponible.

## CU-07 — Imprimir o guardar como PDF

**Actor principal:** Operario del taller

1. El operario pulsa **Imprimir / PDF**.
2. El navegador abre el diálogo de impresión con el resumen preparado.
3. El operario imprime o selecciona guardar como PDF.

## CU-08 — Empezar un cálculo nuevo

**Actor principal:** Operario del taller

1. El operario pulsa **Nuevo**.
2. La aplicación borra los campos guardados y recarga los valores iniciales.

**Resultado:** Se puede configurar un trabajo distinto sin reutilizar los parámetros anteriores.


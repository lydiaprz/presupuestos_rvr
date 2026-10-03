# Análisis de requisitos



### Objetivo

Calcular una estimación consistente del coste y del precio de venta de un trabajo de fabricación de escape, separando materiales, mano de obra y consumibles.

### Requisitos funcionales

1. Seleccionar línea completa, tramo intermedio o tramo final.
2. Elegir un diámetro habitual o introducir uno personalizado, e indicar metros de tubo.
3. Indicar codos, horas de trabajo y tarifa por hora.
4. En una línea completa, incluir opcionalmente un downpipe con coste de piezas y horas adicionales.
5. En un tramo final, indicar una o dos salidas y el número de silenciosos.
6. Configurar precios unitarios de tubo, codo y silencioso, además de consumibles y otros herrajes.
7. Calcular el coste, aplicar margen e IVA y actualizar el desglose al cambiar los datos.
8. Copiar o imprimir el presupuesto y conservar los parámetros en el mismo navegador.

### Requisitos no funcionales

- Interfaz en español, adaptable a móvil y escritorio.
- Los datos del presupuesto no se envían a un servidor.
- Los costes se pueden editar porque las piezas y variantes del proveedor cambian de precio.
- Los precios del proveedor son referencias orientativas, no una conexión automática al catálogo.

### Reglas de cálculo actuales

- **Tubo** = metros × coste por metro.
- **Codos** = número de codos × coste por unidad.
- **Silenciosos** = número indicado × coste por silencioso. La doble salida no duplica automáticamente los silenciosos; sus unidades se indican aparte.
- **Mano de obra** = (horas normales + horas del downpipe, si aplica) × tarifa horaria.
- **Materiales** = tubo + codos + silenciosos + piezas del downpipe + otros materiales.
- **Coste estimado** = materiales + consumibles + mano de obra.
- **Precio antes de IVA** = coste estimado × (1 + margen / 100).
- **Total** = precio antes de IVA × (1 + IVA / 100).

El margen es un porcentaje añadido al coste, no un porcentaje del precio final. El cálculo no incluye envío, homologación, otros impuestos ni operaciones que no se hayan introducido.




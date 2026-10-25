# Instrucciones para Copilot

## Proyecto y arquitectura

- La aplicación es una página web independiente en `index.html`: contiene HTML semántico, CSS integrado y JavaScript simple en un solo archivo. No tiene servidor, manifiesto de paquetes ni dependencias de ejecución; abre el archivo directamente en un navegador.
- El JavaScript está dentro de una función autoejecutable (IIFE) con modo estricto. El estado en memoria tiene la forma `{ clients: [...] }`; cada cliente contiene un arreglo `entries` de movimientos `debt` y `payment`. La página se representa a partir de ese estado mediante `render()`, `renderClients()` y `renderDetail()`.
- `localStorage` es la capa de persistencia, bajo la clave `libreta-del-fiado-v1`. `readState()` carga e interpreta los datos al iniciar; `saveState()` guarda el estado propuesto antes de reemplazar el estado en memoria. Si falla el guardado, no muestres el cambio como exitoso.
- El repositorio no define comandos de compilación, pruebas o lint, ni cuenta con un ejecutor de pruebas. Valida los cambios abriendo `index.html` en un navegador y probando el flujo afectado.

## Usuario y experiencia

- La app está dirigida a dueños de bodegas en Perú con poca experiencia tecnológica; prioriza una interfaz simple y botones grandes.
- Todo el texto visible para el usuario debe estar en español.
- Las deudas se muestran en rojo con el texto «Debe» y los clientes al día en verde con «Al día»; nunca comuniques esos estados solo con color.
- Antes de terminar cualquier cambio, pruébalo en el navegador integrado.

## Comandos

- Para ejecutar la aplicación: abre `index.html` en un navegador. No se necesita servidor ni instalación.
- Compilación, pruebas, lint o ejecución de una prueba individual: este repositorio no define scripts ni herramientas para estas tareas.

## Convenciones

- Mantén la aplicación autocontenida y sin dependencias dentro de `index.html`, salvo que el cambio solicitado requiera explícitamente otra arquitectura.
- Guarda los montos como centavos enteros. `getBalance()` suma los movimientos `debt` y resta los movimientos `payment`; `parseAmount()` valida que los montos sean positivos y tengan como máximo dos decimales. En `addEntry()`, valida los pagos contra el saldo actual del cliente; no dependas únicamente del atributo `max` del formulario.
- Crea un nuevo objeto de estado para cada modificación, persístelo con `saveState()` y llama a `render()` solo después de guardar correctamente.
- Los formularios y botones de clientes se vuelven a crear al renderizar. Por eso, sus eventos se delegan desde elementos padre estables (`#detail-panel` y `#client-list`).
- Antes de insertar en plantillas HTML texto proporcionado por el usuario, pásalo por `escapeHtml()`. Para actualizar texto simple, usa `textContent`.
- Da formato a montos y fechas con los formateadores `Intl` existentes para `es-PE` y `PEN`.
- Usa propiedades personalizadas de CSS para los colores, incluidos los estados relacionados de deuda y cuenta al día. Los colores oscuros se definen en `@media (prefers-color-scheme: dark)`; al cambiar estilos, mantén sincronizadas ambas paletas y los puntos de quiebre responsivos existentes.

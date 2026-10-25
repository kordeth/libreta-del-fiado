# Libreta del Fiado

## Problemática

En las bodegas de barrio del Perú, el fiado suele anotarse en cuadernos que se pierden o se llenan de tachones. A veces se olvida cobrar y pueden surgir discusiones sobre los montos registrados.

## Usuario objetivo

Dueños de bodegas en Perú con poca experiencia tecnológica.

## Objetivo de la solución

Ofrecer una libreta digital sencilla para registrar las cuentas de cada cliente, consultar cuánto debe y anotar sus pagos, con la información guardada en el navegador.

## Funcionalidades principales

- Registrar clientes con nombre y teléfono.
- Registrar fiados con monto, descripción y fecha.
- Registrar pagos y consultar el saldo pendiente por cliente.
- Consultar el total por cobrar de la bodega.
- Buscar clientes por nombre.
- Eliminar movimientos con confirmación.
- Preparar un recordatorio amable por WhatsApp con el saldo pendiente.
- Validar celulares peruanos de nueve dígitos que empiezan con 9.
- Usar la aplicación en modo claro u oscuro, según el tema del dispositivo.
- Guardar los datos en el navegador del dispositivo.

## Tecnologías

La aplicación está hecha con HTML, CSS y JavaScript en un solo archivo (`index.html`), sin dependencias ni servidor.

## Instrucciones de ejecución

- **En local:** abre `index.html` directamente en un navegador.
- **En línea:** visita [Libreta del Fiado](https://kordeth.github.io/libreta-del-fiado/).

## Limitación

Los datos se guardan solo en el navegador del dispositivo. No se sincronizan con otros dispositivos y pueden perderse si se borran los datos del navegador.

## Uso de GitHub Copilot

Seguí el workshop **“GitHub Copilot app tour”**, incluidas las lecciones 0 a 8 y la lección 12.

| # | Decisión | Motivo |
|---|---|---|
| 1 | Usé el selector de elementos para mostrar las deudas en rojo. | El verde confundía porque se asocia con una cuenta al día. |
| 2 | `/init` falló sin indicación, así que lo repetí con una petición. Después agregué las reglas de experiencia de usuario que faltaban en las instrucciones generadas. | Las instrucciones iniciales no incluían las necesidades de los bodegueros ni el uso de estados con texto además de color. |
| 3 | Rechacé configurar Playwright. | Añadía dependencias innecesarias a una aplicación autocontenida. |
| 4 | Al eliminar movimientos, elegí bloquear el borrado si dejaba el saldo negativo. | Así no se eliminan fiados que respaldan pagos ya registrados. |
| 5 | En modo Plan, precisé la validación del teléfono y el texto del mensaje antes de aprobar. | El formato del celular y el mensaje debían quedar definidos antes de implementar el recordatorio. |
| 6 | Rechacé la recomendación de hacer el teléfono opcional. | La aplicación no permite editar el teléfono después de crear el cliente. |
| 7 | Al probar, descubrí que se podían registrar teléfonos inválidos y pedí validarlos al crear el cliente. | La validación debía aplicarse también al registro, no solo al preparar el enlace de WhatsApp. |
| 8 | Como uso Copilot Free, hice manualmente la revisión del pull request. | La revisión no estaba automatizada en mi flujo. |

## Evidencias

Agrega aquí capturas del proyecto y del flujo de la aplicación:

### Lista de clientes y saldos

<!-- Agregar captura aquí -->

### Historial de movimientos y confirmación al eliminar

<!-- Agregar captura aquí -->

### Recordatorio por WhatsApp

<!-- Agregar captura aquí -->

### Aplicación en modo oscuro

<!-- Agregar captura aquí -->

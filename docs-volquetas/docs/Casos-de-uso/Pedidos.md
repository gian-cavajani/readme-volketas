### CU01 - Crear Nuevo Pedido

|**Código**|**Título**|**Descripción**|**Actor**|**Precondición**|**Postcondición**|
|---|---|---|---|---|---|
|CU01|Crear Nuevo Pedido|El usuario puede crear un nuevo pedido seleccionando un cliente (empresa o particular), una obra asociada, un tipo de pedido, y otros detalles opcionales.|Usuario|1. Usuario autenticado.  <br>2. Usuario con permisos para crear pedidos.  <br>3. Debe existir al menos una empresa o particular registrado, o el usuario puede agregar uno nuevo.|El pedido se crea correctamente en el sistema y el usuario es redirigido a la vista de detalles del pedido creado.|

| **Flujo Alternativo** | **Descripción**                                                                                                                                                                                                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CU01-A1               | El cliente no está registrado:  <br>1. El usuario selecciona "Nuevo" en el estado del cliente y elige si es "Empresa" o "Particular".  <br>2. El sistema muestra un formulario para agregar un nuevo cliente.  <br>3. El usuario completa el formulario y agrega el cliente. |
| CU01-A2               | El cliente está registrado:  <br>1. El usuario selecciona "Registrado" en el estado del cliente y elige si es "Empresa" o "Particular".  <br>2. El sistema permite seleccionar un cliente existente.                                                                         |
| CU01-A3               | El cliente tiene múltiples obras:  <br>1. El sistema muestra una lista de obras asociadas al cliente.  <br>2. El usuario selecciona la obra deseada.  <br>3. Si la obra no existe, el usuario puede agregar una nueva obra.                                                  |
| CU01-A4               | Error al crear el pedido:  <br>1. Si ocurre un error al intentar crear el pedido, el sistema muestra un mensaje de error.  <br>2. El usuario puede corregir los datos ingresados y volver a intentar.                                                                        |

| **Flujo Principal** | **Acción del Usuario**                                                                                                                                   | **Respuesta del Sistema**                                                                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CU01-A1             | El usuario accede a la pantalla para crear un nuevo pedido.                                                                                              | El sistema muestra el formulario para crear un nuevo pedido, permitiendo seleccionar el tipo de cliente (empresa o particular) y el estado del cliente (nuevo o registrado). |
| CU01-A2             | El usuario selecciona el estado del cliente (nuevo o registrado) y el tipo de cliente (empresa o particular).                                            | El sistema actualiza el formulario según la selección, permitiendo al usuario buscar un cliente existente o registrar un nuevo cliente.                                      |
| CU01-A3             | Si el cliente es nuevo:  <br>- El usuario completa el formulario de creación de cliente.  <br>- El usuario selecciona el cliente recién creado.          | El sistema guarda la información del nuevo cliente y permite al usuario seleccionarlo para el pedido.                                                                        |
| CU01-A4             | El usuario selecciona la obra asociada al cliente.                                                                                                       | El sistema muestra una lista de obras disponibles para el cliente seleccionado.                                                                                              |
| CU01-A5             | El usuario selecciona un permiso, si aplica, y completa los demás campos del formulario (descripción, número de pesada, chofer, horario sugerido, etc.). | El sistema permite al usuario ingresar y seleccionar toda la información necesaria para el pedido.                                                                           |
| CU01-A6             | El usuario selecciona el tipo de pedido (simple, múltiple, entrega/levante) y especifica la cantidad si es un pedido múltiple.                           | El sistema ajusta el formulario según el tipo de pedido seleccionado, permitiendo al usuario especificar detalles adicionales si es necesario.                               |
| CU01-A7             | El usuario selecciona el tipo de pago y el precio, y marca si el pedido está pagado o no.                                                                | El sistema permite al usuario ingresar esta información.                                                                                                                     |
| CU01-A8             | El usuario revisa toda la información ingresada y hace clic en "Crear Pedido".                                                                           | El sistema valida los datos ingresados y crea el pedido en el sistema, mostrando un mensaje de éxito y redirigiendo al usuario a la página de detalles del pedido.           |

### CU02 - Modificar Pedido

| **Código** | **Título**       | **Descripción**                                                                                                                    | **Actor** | **Precondición**                                                                                       | **Postcondición**                                                                                |
| ---------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| CU01       | Modificar Pedido | El usuario puede modificar los detalles de un pedido existente, incluyendo descripción, permiso, número de pesada y obra asociada. | Usuario   | 1. Usuario autenticado.  <br>2. Usuario con permisos para modificar pedidos.  <br>3. Pedido existente. | El pedido se modifica correctamente en el sistema y se actualiza la información correspondiente. |

|**Paso**|**Acción del Usuario**|**Respuesta del Sistema**|
|---|---|---|
|1|El usuario abre la interfaz de modificación para un pedido específico.|El sistema muestra el formulario con los detalles actuales del pedido.|
|2|El usuario edita la descripción, el número de pesada, selecciona una nueva obra, y/o un nuevo permiso.|El sistema permite al usuario editar los campos.|
|3|Si se selecciona "Crear Nuevo Permiso":  <br>- El usuario ingresa los detalles del nuevo permiso.|El sistema permite al usuario ingresar los datos del nuevo permiso (fecha de creación, fecha de vencimiento, y número de permiso).|
|4|El usuario guarda los cambios.|El sistema valida los datos ingresados.|
|5||El sistema actualiza la información del pedido con los nuevos datos y muestra un mensaje de éxito.|
|6||El sistema cierra la interfaz de modificación.|

| **Código** | **Título**                                  | **Descripción**                                                                                                           |
| ---------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| CU01-A1    | Error al obtener las obras del cliente      | Si ocurre un error al obtener las obras del cliente, el sistema muestra un mensaje de error.                              |
| CU01-A2    | Error al obtener los permisos de la empresa | Si ocurre un error al obtener los permisos de la empresa, el sistema muestra un mensaje de error.                         |
| CU01-A3    | Descripción excede los 255 caracteres       | Si la descripción excede los 255 caracteres, el sistema muestra un mensaje de error y el usuario debe corregirla.         |
| CU01-A4    | Error al modificar el pedido                | Si ocurre un error al modificar el pedido, el sistema muestra un mensaje de error y permite al usuario volver a intentar. |


#### CU03 Visualizar Lista de Pedidos

| **Código** | **Título**                  | **Descripción**                                                                       | **Actor** | **Precondición**                                   | **Postcondición**                                            |
| ---------- | --------------------------- | ------------------------------------------------------------------------------------- | --------- | -------------------------------------------------- | ------------------------------------------------------------ |
| CU03       | Visualizar Lista de Pedidos | El usuario puede visualizar una lista de todos los pedidos registrados en el sistema. | Usuario   | Usuario autenticado con permisos para ver pedidos. | Se muestra una lista de pedidos según los filtros aplicados. |

| **Flujo de trabajo** | **Acción del Usuario**                                          | **Respuesta del Sistema**                                                                                                                      |
| -------------------- | --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 1                    | El usuario navega a la sección de "Pedidos".                    | El sistema carga y muestra una lista de todos los pedidos registrados en el sistema.                                                           |
| 2                    | El usuario observa la lista de pedidos.                         | La lista muestra información básica de cada pedido, como fecha, cliente, dirección, precio, estado de pago, sugerencias y últimos movimientos. |
| 3                    | El usuario puede desplazarse por la lista para ver más pedidos. | El sistema permite desplazarse por la lista completa si hay más pedidos de los que caben en la pantalla visible.                               |
#### CU04: Filtrar Pedidos por Cliente

| **Código** | **Título**                  | **Descripción**                                                                       | **Actor** | **Precondición**                                   | **Postcondición**                                                               |
| ---------- | --------------------------- | ------------------------------------------------------------------------------------- | --------- | -------------------------------------------------- | ------------------------------------------------------------------------------- |
| CU04       | Filtrar Pedidos por Cliente | El usuario puede filtrar los pedidos según el tipo de cliente (empresa o particular). | Usuario   | Usuario autenticado con permisos para ver pedidos. | Se muestra una lista de pedidos filtrada según el tipo de cliente seleccionado. |

| Flujo de trabajo | **Acción del Usuario**                                                          | **Respuesta del Sistema**                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 1                | El usuario selecciona un filtro para el tipo de cliente (empresa o particular). | El sistema filtra la lista de pedidos y muestra solo aquellos que corresponden al tipo de cliente seleccionado (empresa o particular). |
| 2                | El usuario observa la lista filtrada de pedidos.                                | La lista muestra solo los pedidos que cumplen con el criterio de filtro seleccionado.                                                  |
#### CU05: Filtrar Pedidos por Estado de Pago

|**Código**|**Título**|**Descripción**|**Actor**|**Precondición**|**Postcondición**|
|---|---|---|---|---|---|
|CU03|Filtrar Pedidos por Estado de Pago|El usuario puede filtrar los pedidos según su estado de pago (pagado o no pagado).|Usuario|Usuario autenticado con permisos para ver pedidos.|Se muestra una lista de pedidos filtrada según el estado de pago seleccionado.|

| **Flujo de trabajo** | **Acción del Usuario**                                                       | **Respuesta del Sistema**                                                                                      |
| -------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 1                    | El usuario selecciona un filtro para el estado de pago (pagado o no pagado). | El sistema filtra la lista de pedidos y muestra solo aquellos que corresponden al estado de pago seleccionado. |
| 2                    | El usuario observa la lista filtrada de pedidos.                             | La lista muestra solo los pedidos que cumplen con el criterio de filtro seleccionado.                          |
#### CU06: Filtrar Pedidos por Movimiento

| **Código** | **Título**                     | **Descripción**                                                                                       | **Actor** | **Precondición**                                   | **Postcondición**                                                                 |
| ---------- | ------------------------------ | ----------------------------------------------------------------------------------------------------- | --------- | -------------------------------------------------- | --------------------------------------------------------------------------------- |
| CU04       | Filtrar Pedidos por Movimiento | El usuario puede filtrar los pedidos según su último movimiento (sin entregar, entregado, levantado). | Usuario   | Usuario autenticado con permisos para ver pedidos. | Se muestra una lista de pedidos filtrada según el último movimiento seleccionado. |

| **Flujo de trabajo** | **Acción del Usuario**                                                                           | **Respuesta del Sistema**                                                                                          |
| -------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| 1                    | El usuario selecciona un filtro para el tipo de movimiento (sin entregar, entregado, levantado). | El sistema filtra la lista de pedidos y muestra solo aquellos que corresponden al tipo de movimiento seleccionado. |
| 2                    | El usuario observa la lista filtrada de pedidos.                                                 | La lista muestra solo los pedidos que cumplen con el criterio de filtro seleccionado.                              |
#### CU07: Ver Detalle de Pedido

|**Código**|**Título**|**Descripción**|**Actor**|**Precondición**|**Postcondición**|
|---|---|---|---|---|---|
|CU05|Ver Detalle de Pedido|El usuario puede ver el detalle de un pedido específico al hacer clic en su fila correspondiente en la lista.|Usuario|Usuario autenticado con permisos para ver pedidos.|Se muestra el detalle completo del pedido seleccionado.|

| **Flujo de trabajo** | **Acción del Usuario**                                               | **Respuesta del Sistema**                                                                                              |
| -------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 1                    | El usuario hace clic en un pedido específico en la lista de pedidos. | El sistema navega a la pantalla de detalles del pedido seleccionado, mostrando información detallada sobre ese pedido. |
| 2                    | El usuario revisa la información detallada del pedido.               | El sistema muestra información completa del pedido, incluyendo cliente, obra, descripción, permisos, movimientos, etc. |


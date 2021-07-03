# Primeros pasos: TecPyme POS (solo teclado) #
#### Redactado el 26 de mayo de 2020

> Este artículo está orientado para explicar los atajos de TecPyme POS cuando nos encontramos en un ambiente donde solo disponemos del teclado.

TecPyme POS es nuestro producto estrella, un punto de venta simple, rápido y que ofrece más de lo que usted necesita. Actúa como cliente híbrido.

![Ilustración de IvyPOS Login](/data/assets/ivypos-login.png)

> Así es, hecho con mucho <3 por TecPyme. Ilustración del login del cliente POS.


## 👨🏽‍🏫️ Introducción

TecPyme POS se divide en dos ramas. Una, cuando se utiliza la opción "Accesibilidad táctil" y otra la que no. En esta entrada, vamos a discutir del POS cuando no está orientado para ser "táctil".

![Ilustración de IvyPOS sin tactil](/data/assets/ivypos.png)

## ⌨️ Atajos de teclado

| Tecla   | Acción                 | Descripción                                                                                                                                                                                  |
|---------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **F1**  | Clientes               | Despliega el menú de clientes, aquí se podrán seleccionar  clientes del sistema, editar y crear nuevos.                                                                                      |
| **F2**  | Búsqueda de artículos  | Despliega el menú de búsqueda de artículos. Aquí el cajero podrá buscar artículos en el sistema y seleccionar el deseado, para agregarlo en la cuenta actual.                                |
| **F3**  | Cambio de moneda       | Hace un intercambio de monedas. Por defecto se encuentra el MXN, si se pulsa esta tecla se cambiará a USD. Si está en USD se cambiará a MXN y así viceversa.                                 |
| **F4**  | Eliminar cuenta        | Mostrará un diálogo de confirmación para eliminar la cuenta que se tiene en el momento.                                                                                                      |
| **F5**  | Finalizar cuenta       | Mostrará un diálogo de confirmación para finalizar la cuenta y pasar al pago de la misma.                                                                                                    |
| **F6**  | Utilidades             | Despliega el menú de utilidades. Desde aquí podra suspender cuentas, hacer reimpresiones, tablajerías, etc.                                                                                  |
| **F7**  | Verificador de precios | Pregunta por el código de barras y si encuentra coincidencias, muestra el precio total de la primera coincidencia.                                                                           |
| **F8**  | Movimientos de caja    | Despliega el menú de movimientos. Aquí el cajero podrá hacer movimientos de caja como retiros, préstamos, etcétera.                                                                          |
| **F9**  | Pagos a proveedores    | Inicia el asistente de pagos a proveedores. Pregunta a qué proveedor y luego despliega una ventana con todos los documentos pendientes por pagar.                                            |
| **F10** | Compras                | Inicia el asistente de compras. Pregunta qué proveedor y luego muestra sus ordenes de compra y en caso de no existir, permite generar nuevas.                                                |
| **F11** | Gastos                 | Inicia el asistente de gastos. Pregunta qué proveedor y posteriormente despliega un menú preguntando qué concepto desea aplicar.                                                             |
| **F12** | Pedidos de clientes    | Despliega un menú con las comandas rápidas que se tienen almacenadas. Aquí el cajero podrá suspender una cuenta como pedido y generar comandas, dependiendo de la configuración del sistema. |

## Comandos del escáner de códigos

Estos atajos comienzan con palabras reservadas. Algunos requieren de argumentos para su acción. Estos atajos fueron heredados del POS legacy de TecPyme POS. Si usted ya está acostumbrado a ellos, no tendrá ningún problema en reacomodarse en el nuevo sistema.

| Palabra    | Descripción                                             | Ventas | Pasarela | Argumentos                                                   | Ejemplo                                                                                                                                                             |
|------------|---------------------------------------------------------|--------|----------|--------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **CAN**    | Cancela un concepto de la cuenta en curso.              | Sí.    | Sí.      | - Código de barras del concepto.                             | **CAN0011** Cancela el concepto 0011 completamente. El concepto será cancelado en su totalidad.                                                                     |
| **SBT**    | Se pasa al estado de pagar cuenta en curso.             | Sí.    | No.      | Ninguno.                                                     | **SBT** Se termina la venta de la cuenta en curso y se pasa al pago.                                                                                                |
| **E**      | Recibe efectivo.                                        | No.    | Sí.      | - Cantidad en efectivo a recibir, incluyendo decimales.      | **E100** Se recibe 1.00 de MXN y se agrega al pago en curso.                                                                                                        |
| **D**      | Recibe dolares                                          | No.    | Sí.      | - Cantidad de dolares a recibir, incluyendo decimales.       | **D100** Se recibe 1.00 de USD y se agrega al pago en curso.                                                                                                        |
| **T**      | Recibe tarjeta (dato informativo)                       | No.    | Sí.      | - Cantidad de tarjeta a recibir, incluyendo decimales.       | **T100** Se recibe 1.00 de MXN en tarjeta y se agrega al pago en curso                                                                                              |
| **V**      | Recibe vales (dato informativo)                         | No.    | Sí.      | - Cantidad de vales en MXN a recibir, incluyendo decimales.  | **V100** Se recibe 1.00 de MXN en vales y se agrega al pago en curso.                                                                                               |
| **RT**     | Reimprime un ticket dado.                               | Sí.    | No.      | - Folio del ticket. - Caja del ticket (opcional).            | **RT1100** Reimprime el ticket con folio 1100 de la caja en actual.  **RT1300*3** Reimprime el ticket con folio 1300 de la caja 3.                                  |
| **RTL**    | Reimprime el último ticket hecho.                       | Sí.    | Sí.      | - Ninguno.                                                   | **RTL** Reimprime el ticket anterior.                                                                                                                               |
| **RC**     | Reimprime un corte Z dato.                              | Sí.    | No.      | - Folio de corte. - Caja del corte.                          | **RC3*1** Reimprime el corte con folio 3 de la caja 1.                                                                                                              |
| **RR**     | Reimprimir  retiro **SOLO RETIROS EN  MONEDA LOCAL**    | Sí.    | No.      | - Folio del retiro. - Caja del retiro (opcional).            | **RR8*4** Reimprime el retiro con folio 8 de la caja 4.                                                                                                             |
| **RD**     | Reimprime retiro de **dólares**                         | Sí.    | No.      | - Folio del retiro en dólares. - Caja del retiro (opcional). | **RD9*2** Reimprime el retiro de dólares con folio 8 de la caja 2.                                                                                                  |
| **RP**     | Reimprime movimiento de préstamo en caja.               | Sí.    | No.      | - Folio del movimiento. - Caja del movimiento. (opcional)    | **RP4** Reimprime el préstamo con folio 4 de la caja en curso.                                                                                                      |
| **RO**     | Reimprime la comanda de un pedido dado por su folio.    | Sí.    | Sí.      | - Folio del pedido.                                          | **RO4** Reimprimir comanda de pedido con folio 4.                                                                                                                   |
| **ROL**    | Reimprime la última comanda hecha.                      | Sí.    | Sí.      | - Ninguno                                                    | Reimprime la última comanda hecha.                                                                                                                                  |
| **DE**     | Procede a hacer una devolución del ticket dado.         | Sí.    | No.      | - Folio del ticket a devolver. - Caja del ticket. (opcional) | **DE12** Procede a hacer la devolución del ticket con folio 12 de la caja en curso.  **DE20*2** Procede a hacer la devolución del ticket con folio 20 de la caja 2. |
| **CAJON**  | Abre el cajón. Depende de la configuración del sistema. | Sí.    | Sí.      | Ninguno.                                                     | **CAJON** Abre el cajón de efectivo. Se pedirá autorización si la configuración del  sistema así lo indica.                                                         |
| **SEPARO** | Procede a hacer el separo de la cuenta actual.          | Sí.    | No.      | Ninguno.                                                     | **SEPARO** Procede a hacer el separo de la cuenta actual. Si el cliente es el público en general indicado en la config. del sistema, se arrojará un error.          |
| **CORTEX** | Hacer corte tipo X.                                     | Sí.    | No.      | Ninguno.                                                     | **CORTEX** Se mostrará el diálogo para confirmar el corte de caja tipo X.                                                                                           |
| **CORTEZ** | Hacer corte tipo Z.                                     | Sí.    | No.      | Ninguno.                                                     | **CORTEZ** Se mostrará el diálogo para confirmar el corte de caja tipo Z.                                                                                           |
| **SUSP**   | Muestra el diálogo de suspen- siones.                   | Sí.    | No.      | Ninguno.                                                     | **SUSP** Muestra el diálogo de suspensiones.                                                                                                                        |
| **SALIR**  | Cierra la sesión de la caja actual.                     | Sí.    | No.      | Ninguno.                                                     | **SALIR** Cierra la sesión de la caja actual. Esto se ve afectado por la config. del sistema.                                                                       |

Con el paso del tiempo esta entrada se estará actualizando a medida que nuestro producto agrege más funcionalidades.
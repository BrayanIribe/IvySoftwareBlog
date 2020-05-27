# Primeros pasos: IvyPOS (solo teclado) #
#### Redactado el 26 de mayo de 2020

> Este artículo está orientado para explicar los atajos de IvyPOS cuando nos encontramos en un ambiente donde solo disponemos del teclado.

IvyPOS es nuestro producto estrella, un punto de venta simple, rápido y que ofrece más de lo que usted piensa. Actualmente, funciona como cliente de TecPyME POS y se sincroniza con el para hacer sus tickets.

![Ilustración de IvyPOS Login](/data/assets/ivypos-login.png)

> Así es, hecho con mucho <3 por TecPyME. Ilustración del login de IvyPOS.


## 👨🏽‍🏫️ Introducción

IvyPOS se divide en dos ramas. Una, cuando se utiliza la opción "Accesibilidad táctil" y otra la que no. En esta entrada, vamos a discutir del POS cuando no está orientado para ser "táctil".

![Ilustración de IvyPOS sin tactil](/data/assets/ivypos-not-touch.png)

El cliente está pensado para ser táctil principalmente, así que por eso el diseño vemos que no "encaja" muy bien. Pero no se preocupe, a countinuación explicamos comandos que puede utilizar dentro del POS.

## ⌨️ Shortcuts

| Tecla   |  Acción                   | Descripción                                                                                                                                                                           |
|---------|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **F1**  | Clientes                  | Despliega el menú de clientes, aquí se podrán seleccionar  clientes del sistema, editar y crear nuevos.                                                                               |
| **F2**  | Utilidades                | Despliega un menu que contiene todas las utilidades del sistema, como hacer corte de caja, hacer movimientos, etc.                                                                    |
| **F3**  | Búsqueda de artículos     | Despliega el menú de búsqueda de artículos. Aquí el cajero podrá buscar artículos en el sistema y seleccionar el deseado, para agregarlo en la cuenta actual.                         |
| **F4**  | Cambio de moneda          | Hace un intercambio de monedas. Por defecto se encuentra el MXN, si se pulsa esta tecla se cambiará a USD. Si está en USD se cambiará a MXN y así viceversa.                          |
| **F5**  | Eliminar cuenta           | Mostrará un diálogo de confirmación para eliminar la cuenta que se tiene en el momento.                                                                                               |
| **F6**  | Finalizar cuenta          | Mostrará un diálogo de confirmación para finalizar la cuenta y pasar al pago de la misma.                                                                                             |
| **F7**  | Abrir cajón               | Si el cajero tiene permiso de abrir el cajón, se abrirá sin mostrar ningún diálogo. De lo contrario, pedirá autorización. Varía según la configuración del sistema.                   |
| **F8**  | Movimientos de caja       | Despliega el menú de movimientos. Aquí el cajero podrá hacer movimientos de caja como retiros, préstamos, etcétera.                                                                   |
| **F9**  | Reimpresión de documentos | Despliega el menú de reimpresión de documentos. Si el cajero tiene permisos de hacerlo, se procederá sin autorización. Esto varía según la configuración del sistema.                 |
| **F10** | Suspensiones de cuentas   | Despliega el menú de suspensiones. Aquí el cajero podrá suspender la cuenta actual y seleccionar cuentas suspendidas. Esto puede cambiar dependiendo de la configuración del sistema. |
| **F11** | Corte de caja             | Despliega el díalogo de corte de caja. Dependiendo de la configuración del sistema, se pedirá autorización o no.                                                                      |
| **F12** | Cierre de sesión          | Muestra un diálogo para confirmar el cierre de sesión del cajero en curso.                                                                                                            |

#### Shortcuts del escáner de códigos

Estos shortcuts comienzan con palabras reservadas. Algunos requieren de argumentos para su acción. Estos shortcuts fueron heredados del POS legacy de TecPyME POS. Así que si usted ya está acostumbrado a ellos, no tendrá ningún problema en reacomodarse en el nuevo sistema.
| Palabra    | Descripción                                                | Ventas | Pasarela | Argumentos                                                      | Ejemplo                                                                                                                                                                                 |
|------------|------------------------------------------------------------|--------|----------|-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **CAN**    | Cancela un concepto de la<br>cuenta en curso.              | Sí.    | No.      | - Código de barras del concepto.<br><br>- Cantidad (opcional).  | **CAN0011**<br>Cancela el concepto 0011 completamente.<br><br>**CAN0011*2**<br>Cancela 2 piezas del concepto 0011.                                                                      |
| **SBT**    | Se pasa al estado de pagar<br>cuenta en curso.             | Sí.    | No.      | Ninguno.                                                        | **SBT**<br>Se termina la venta de la cuenta en curso<br>y se pasa al pago.                                                                                                              |
| **E**      | Recibe efectivo.                                           | No.    | Sí.      | - Cantidad en efectivo a recibir,<br>incluyendo decimales.      | **E100**<br>Se recibe 1.00 de MXN y se agrega al pago<br>en curso.                                                                                                                      |
| **D**      | Recibe dolares                                             | No.    | Sí.      | - Cantidad de dolares a recibir,<br>incluyendo decimales.       | **D100**<br>Se recibe 1.00 de USD y se agrega al pago<br>en curso.                                                                                                                      |
| **T**      | Recibe tarjeta<br>(dato informativo)                       | No.    | Sí.      | - Cantidad de tarjeta a recibir,<br>incluyendo decimales.       | **T100**<br>Se recibe 1.00 de MXN en tarjeta y se<br>agrega al pago en curso                                                                                                            |
| **V**      | Recibe vales<br>(dato informativo)                         | No.    | Sí.      | - Cantidad de vales en MXN a<br>recibir, incluyendo decimales.  | **V100**<br>Se recibe 1.00 de MXN en vales y se<br>agrega al pago en curso.                                                                                                             |
| **RT**     | Reimprime un ticket dado.                                  | Sí.    | No.      | - Folio del ticket.<br>- Caja del ticket (opcional).            | **RT1100**<br>Reimprime el ticket con folio 1100 de la<br>caja en actual.<br><br>**RT1300*3**<br>Reimprime el ticket con folio 1300 de la<br>caja 3.                                    |
| **RC**     | Reimprime un corte dato.                                   | Sí.    | No.      | - Folio de corte.<br>- Caja del corte.                          | **RC3*1**<br>Reimprime el corte con folio 3 de la<br>caja 1.                                                                                                                            |
| **RR**     | Reimprimir  retiro<br>**SOLO RETIROS EN <br>MONEDA LOCAL** | Sí.    | No.      | - Folio del retiro.<br>- Caja del retiro (opcional).            | **RR8*4**<br>Reimprime el retiro con folio 8 de la<br>caja 4.                                                                                                                           |
| **RD**     | Reimprime retiro de<br>**dólares**                         | Sí.    | No.      | - Folio del retiro en dólares.<br>- Caja del retiro (opcional). | **RD9*2**<br>Reimprime el retiro de dólares con<br>folio 8 de la caja 2.                                                                                                                |
| **RP**     | Reimprime movimiento de<br>préstamo en caja.               | Sí.    | No.      | - Folio del movimiento.<br>- Caja del movimiento. (opcional)    | **RP4**<br>Reimprime el préstamo con folio 4<br>de la caja en curso.                                                                                                                    |
| **DE**     | Procede a hacer una<br>devolución del ticket dado.         | Sí.    | No.      | - Folio del ticket a devolver.<br>- Caja del ticket. (opcional) | **DE12**<br>Procede a hacer la devolución del ticket<br>con folio 12 de la caja en curso.<br><br>**DE20*2**<br>Procede a hacer la devolución del ticket<br>con folio 20 de la caja 2. |
| **FA**     | Procede a hacer una factura<br>del ticket dado.            | Sí.    | No.      | - Folio del ticket a devolver.<br>- Caja del ticket. (opcional) | **FA12**<br>Procede a hacer la facturación del<br>ticket con folio 12 de la caja actual.<br><br>**FA28*2**<br>Procede a hacer la facturación del<br>ticket con folio 28 de la caja 2.   |
| **CAJON**  | Abre el cajón. Depende de<br>la configuración del sistema. | Sí.    | Sí.      | Ninguno.                                                        | **CAJON**<br>Abre el cajón de efectivo. Se pedirá<br>autorización si la configuración del <br>sistema así lo indica.                                                                      |
| **SEPARO** | Procede a hacer el separo de<br>la cuenta actual.          | Sí.    | No.      | Ninguno.                                                        | **SEPARO**<br>Procede a hacer el separo de la cuenta<br>actual. Si el cliente es el público en<br>general indicado en la config. del sistema,<br>se arrojará un error.                  |
| **CORTEX** | Hacer corte tipo X.                                        | Sí.    | No.      | Ninguno.                                                        | **CORTEX**<br>Se mostrará el diálogo para confirmar el<br>corte de caja tipo X.                                                                                                         |
| **CORTEZ** | Hacer corte tipo Z.                                        | Sí.    | No.      | Ninguno.                                                        | **CORTEZ**<br>Se mostrará el diálogo para confirmar<br>el corte de caja tipo Z.                                                                                                         |
| **SUSP**   | Muestra el diálogo de suspen-<br>siones.                   | Sí.    | No.      | Ninguno.                                                        | **SUSP**<br>Muestra el diálogo de suspensiones.                                                                                                                                         |
| **SALIR**  | Cierra la sesión de la caja<br>actual.                     | Sí.    | No.      | Ninguno.                                                        | **SALIR**<br>Cierra la sesión de la caja actual.<br>Esto se ve afectado por la config.<br>del sistema.                                                                                  |

Con el paso del tiempo esta entrada se estará actualizando a medida que nuestro producto agrege más funcionalidades.
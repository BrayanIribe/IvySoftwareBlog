# Sincronización de productos Ivy #
#### Redactado el 8 de mayo de 2020

> Este artículo está orientado para explicar cómo funciona la sincronización en los diversos productos Ivy cuando estos la ofrecen.

Actualmente, los productos IvyStore e IvyMailer incorporan sincronización integrada con otras aplicaciones. Sin embargo... internamente, funcionan de una manera muy interesante.

![Ilustración de ejemplo](/data/assets/ivystore-sync.png)

> Ilustración de ejemplo, donde nos muestra un problema por el cual posiblemente te encuentres aquí. Esto sucede debido al algoritmo punto a punto con el que cuentan estos productos.


## 🔑 Los token

Antes de llegar al grano, tenemos que discutir un poco sobre este tema y su funcionamiento.

> Como desarrolladores, nos preocupamos por la seguridad de nuestros productos. Siempre nos hacemos la pregunta ¿Y si nuestro producto se llegáse a comprometer? ¿Hasta donde podría llegar el atacante?

Cuando entramos a la configuración de estos sistemas, antes de entrar, nos pide una "autorización" que coloquialmente, la llamamos "modo sudo" (esto por la forma en la que se comporta la consola linux con sudo).

![Sudo request](/data/assets/sudo-mode.png)

> Famosa pantalla "sudo" donde se nos requiere reescribir la contraseña una vez más.

Además de que hacer algo así nos ofrece una capa más de seguridad para evitar cambios en la configuración no autorizados, esto internamente hace todo un procedimiento.

Cuando usted reescribe su contraseña y presiona "Autorizar", le pregunta al servidor si puede generar un **token**. El servidor le responde con un sí o no, dependiendo si escribió bien la contraseña. Si esto sucede, entonces le devuelve dicho token.

Este token, contiene la contraseña escrita, pero cifrada bajo un fuerte algoritmo que, **ni si quiera nosotros podríamos saber su contenido**.

Entonces, este dato es almacenado silenciosamente en su navegador para futuro uso. Cabe aclarar, no toda configuración necesita de este token. Pero sí que en el servidor se está validando que exista un token de estos para proceder a hacer los cambios pertinentes.

## 📦 Instalando aplicaciones en los productos Ivy

Cuando se va a instalar una nueva aplicación en uno de estos productos, se piden datos **muy, muy sensibles**. Por lo cual, tenemos que asegurarnos de que nosotros mismos, no podamos ver los datos. Esto se le conoce como **cifrado de punto a punto**.

> Entendemos que esto puede molestarle a usted como cliente, pero nos tomamos la seguridad muy, muy enserio y no queremos que un día a las 5:00 a.m. nos marque reclamándonos "¡No tengo las facturas de todo el año, el sistema está en blanco, ¿qué paso?!"

### Entonces... ¿Cómo funciona?

Cuando usted rellena el formulario de la aplicación a instalar con los datos requeridos y pulsa "Enviar", sucede una serie de pasos.

- Considerando que ya está en modo sudo y por ende, cuenta con su token entonces...

- El servidor recibe su petición y hace las validaciones pertinentes.

- Si la solicitud procede, entonces se toman sus datos y se comienza a trabajar en ellos internamente. El resultado de esto es un cifrado donde la llave, **es el token que usted creó al momento de hacer sudo**.

- Esto quiere decir que, **¡Ni si quiera nosotros sabemos las credenciales de esa aplicación instalada!**

- Por tanto... Se hace incapié en que, si usted llega a reestablecer su contraseña o, **simplemente, se le olvida** entonces no habrá marcha atrás. Será imposible saber el contenido y por ende, dejará de poder sincronizar con dicha aplicación.

## 🔄 Las sincronizaciones

> En IvySoftware, no podemos compartir como funciona internamente las sincronizaciones automáticas, pero, ¡trabajan bajo un algoritmo muy complejo que, no podríamos explicarlo por aquí!

Cuando instala la aplicación correctamente y, tiene los permisos de sudo el usuario que instaló la aplicación, entonces puede hacer **sincronizaciones**.

![IvyMailer sync menu](/data/assets/ivymailer-sync.png)


El funcionamiento de las sincronizaciones es muy extenso, es tanto que no podríamos abarcarlo completamente en esta entrada pero lo que sí podemos decir, es qué funciona diferente, dependiendo de la aplicación instalada y el producto Ivy en sí.

**Usted solo busque un botón que diga "Hacer sincronización".**

Y listo, con esto estaría sincronizando los datos de la aplicación instalada. Los datos sincronizados depende de la aplicación en sí.

## 🤔 Yo estoy aquí porque perdí mi contraseña...

Bueno, ¡como ya lo hemos dicho! Su contraseña era la única llave para hacer sincronizaciones, si la perdió entonces no podemos hacer nada **por nuestra parte**.

Pero, no se preocupe... No es tan grave esto. Simplemente, **reinstale la aplicación** y podrá hacer sincronizaciones de nuevo, nada grave.
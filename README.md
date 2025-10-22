Este proyecto está organizado de una forma muy clara para entender cómo funciona un pequeño sistema bancario. Todo empieza en la clase principal, que pone en marcha la aplicación. Desde allí, las operaciones se reparten entre diferentes capas para mantener el código ordenado y fácil de mantener.

La primera capa es el controlador (BankController). Piensa en él como la “recepción del banco”: es el que recibe las solicitudes del usuario, como crear un cliente, hacer un depósito, retirar dinero, transferir entre cuentas o consultar los movimientos. El controlador no hace los cálculos ni toma decisiones importantes; simplemente revisa que lo que llegue tenga sentido y luego se lo pasa al servicio que realmente ejecuta la acción.

La lógica principal del banco está en la interfaz BankService y su implementación BankServiceImpl. Aquí es donde se aplican las reglas del negocio. Por ejemplo, antes de permitir un retiro o una transferencia, revisa si la cuenta existe, si el monto es válido y si hay suficiente dinero. También es este servicio quien registra los movimientos (transacciones) y actualiza los saldos. Si algo no se puede hacer porque rompe una regla, se lanza una excepción especial llamada DomainException que explica el problema.

Las clases del modelo representan los elementos reales del banco. Customer es el cliente y guarda sus cuentas. Account es la base de lo que significa tener una cuenta y maneja el saldo y los movimientos. Hay dos tipos de cuenta: CheckingAccount (cuenta corriente) y SavingsAccount (de ahorro), y cada una puede tener condiciones distintas. Transaction es como el recibo de cada movimiento realizado, y Money encapsula el manejo del dinero para evitar errores al trabajar con montos.

La persistencia del sistema, es decir, dónde se guardan los datos, se hace con JsonRepository. Aquí se almacenan clientes, cuentas y transacciones en archivos JSON. FileManager es quien realmente escribe y lee los archivos, mientras que JsonUtil se encarga de convertir los objetos de Java a JSON y viceversa. Es una forma simple y funcional de guardar datos, ideal para practicar, aunque no sería la mejor opción si se necesitara manejar muchos usuarios o trabajar con varias personas al mismo tiempo.

Un detalle interesante es el uso del patrón Estrategia para calcular intereses. Con la interfaz InterestStrategy y sus dos versiones (SimpleRateStrategy y TieredRateStrategy), se puede cambiar la forma de calcular intereses sin tocar el resto del código. Es como tener distintas “fórmulas” que se pueden activar según la necesidad.

Finalmente, hay una clase de prueba en src/test que verifica que la aplicación funciona y arranca bien. Aunque es un buen inicio, sería positivo ampliar estas pruebas para asegurar que depósitos, retiros, transferencias y la parte de guardado en archivos también se comporten correctamente.

En conjunto, el proyecto está bien hecho para aprender: separa muy bien cada parte, aplica reglas claras, registra los movimientos y usa buenas prácticas como el patrón estrategia. Para seguir mejorándolo, podrías agregar más pruebas, validar algunas cosas con más detalle y, si algún día se quiere hacer más grande, usar una base de datos más robusta.

COMO CREAR UN CLIENTE EN THUNDER CLIENN:

Para crear un cliente en Thunder Client, abre la extensión en VS Code y crea una nueva petición(new Request). Selecciona el método POST (que es el que se usa para registrar o crear datos) e ingresa la URL del endpoint donde tu API recibe nuevos clientes. Luego ve a la sección Body, elige el tipo JSON y escribe allí los datos del cliente que quieres crear, como el nombre, identificación y correo.

Cuando tengas todo listo, presiona Send y verás la respuesta al lado derecho, donde podrás confirmar si la creación del cliente fue exitosa. Si lo fue, normalmente aparecerá el cliente creado junto con su ID. Finalmente, puedes guardar esta petición dentro de una colección en Thunder Client para usarla en futuras pruebas sin tener que volver a configurarla.

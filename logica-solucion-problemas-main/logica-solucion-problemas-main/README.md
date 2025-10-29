# 🏦 BankApp – Sistema Bancario con Spring Boot 3

**BankApp** es una aplicación RESTful desarrollada con **Spring Boot 3.5.6** y **Java 21** que permite gestionar clientes, cuentas y transacciones bancarias de forma sencilla.
El proyecto implementa una arquitectura modular basada en capas, persistencia mediante archivos JSON, manejo de excepciones personalizadas y documentación automática con **Swagger (OpenAPI)**.

---

## 🚀 Tecnologías utilizadas

| Tecnología                  | Descripción                                                         |
| --------------------------- | ------------------------------------------------------------------- |
| **Java 21**                 | Lenguaje principal del proyecto.                                    |
| **Spring Boot 3.5.6**       | Framework para el desarrollo del backend REST.                      |
| **Spring Web**              | Permite exponer los endpoints HTTP.                                 |
| **Spring Validation**       | Validación de datos en los modelos y controladores.                 |
| **Springdoc OpenAPI 2.6.0** | Documentación automática con Swagger UI.                            |
| **JSON (Archivos locales)** | Mecanismo de persistencia ligera para cuentas y clientes.           |
| **Maven**                   | Herramienta de gestión de dependencias y construcción del proyecto. |

---

## 🧩 Estructura del proyecto

```
bank-app/
├── src/
│   ├── main/java/com/logsoluprobl/appbank/
│   │   ├── app/                     # Clase principal
│   │   │   └── BankAppApplication.java
│   │   ├── model/                   # Modelos de dominio (Account, Customer, etc.)
│   │   ├── service/                 # Lógica de negocio
│   │   ├── repository/              # Persistencia con JSON
│   │   ├── controller/              # Controladores REST
│   │   ├── exception/               # Excepciones personalizadas
│   │   ├── util/                    # Utilidades de lectura/escritura JSON
│   │   └── config/                  # Configuración de OpenAPI (Swagger)
│   └── resources/
│       ├── application.properties   # Configuración de Spring
│       ├── data/
│       │   ├── customers.json
│       │   └── accounts.json
│       └── static/
│
└── pom.xml
```

---

## 🧠 Arquitectura

El proyecto está diseñado con una **arquitectura en capas** para mantener separación de responsabilidades:

```
Controller → Service → Repository → Data (JSON)
```

* **Controller:** expone los endpoints REST.
* **Service:** contiene la lógica del negocio.
* **Repository:** gestiona la persistencia en archivos JSON.
* **Model:** representa las entidades del dominio (clientes, cuentas, transacciones).
* **Exception:** define excepciones del dominio para manejo de errores.

---

## ⚙️ Instalación y ejecución

### 1️⃣ Clonar el repositorio

```bash
git clone https://github.com/DanielDev87/bank-app.git
cd bank-app
```

### 2️⃣ Compilar el proyecto

```bash
mvn clean install
```

### 3️⃣ Ejecutar la aplicación

```bash
mvn spring-boot:run
```

Por defecto, la aplicación se ejecutará en:
👉 **[http://localhost:8080](http://localhost:8080)**

---

## 📖 Documentación con Swagger

El proyecto utiliza **Springdoc OpenAPI** para generar documentación automática de la API.

### 🔗 Endpoints principales:

* Swagger UI: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)
* Documentación JSON: [http://localhost:8080/v3/api-docs](http://localhost:8080/v3/api-docs)

### 🧾 Información configurada:

Archivo: `OpenApiConfig.java`

```java
.title("Bank App API")
.description("API REST para la gestión de clientes, cuentas y transacciones bancarias")
.version("1.0.0")
.contact(new Contact().name("Daniel Felipe Agudelo Molina").email("daniel.agudelomo@amigo.edu.co"))
```

---

## 🔐 Endpoints disponibles

| Método   | Endpoint                                                 | Descripción                                           |
| -------- | -------------------------------------------------------- | ----------------------------------------------------- |
| **POST** | `/api/bank/customers`                                    | Crea un nuevo cliente.                                |
| **GET**  | `/api/bank/customers`                                    | Lista todos los clientes.                             |
| **GET**  | `/api/bank/customers/{customerId}`                       | Busca un cliente por su ID.                           |
| **POST** | `/api/bank/customers/{customerId}/accounts`              | Crea una cuenta (Savings o Checking) para un cliente. |
| **GET**  | `/api/bank/customers/{customerId}/accounts`              | Lista las cuentas de un cliente.                      |
| **GET**  | `/api/bank/accounts/{accountId}`                         | Consulta una cuenta específica.                       |
| **POST** | `/api/bank/accounts/{accountId}/deposit?amount={valor}`  | Realiza un depósito.                                  |
| **POST** | `/api/bank/accounts/{accountId}/withdraw?amount={valor}` | Realiza un retiro.                                    |
| **POST** | `/api/bank/accounts/{fromAccountId}/transfer`            | Transfiere dinero entre cuentas.                      |
| **GET**  | `/api/bank/accounts/{accountId}/transactions`            | Lista las transacciones de una cuenta.                |
| **POST** | `/api/bank/accounts/{accountId}/apply-interest`          | Aplica intereses a la cuenta.                         |

---

## 🧰 Ejemplo de uso (cURL)

### Crear un cliente

```bash
curl -X POST http://localhost:8080/api/bank/customers \
-H "Content-Type: application/json" \
-d '{"id": "CUST001", "name": "Juan Pérez", "email": "juan@example.com"}'
```

### Crear una cuenta de ahorros

```bash
curl -X POST http://localhost:8080/api/bank/customers/CUST001/accounts \
-H "Content-Type: application/json" \
-d '{"type": "SAVINGS", "accountId": "ACC001", "parameter": 0.03}'
```

### Realizar un depósito

```bash
curl -X POST "http://localhost:8080/api/bank/accounts/ACC001/deposit?amount=500"
```

---

## ⚠️ Manejo de errores

El controlador utiliza una excepción personalizada `DomainException` para capturar y devolver mensajes claros de error.

Ejemplo de respuesta:

```json
{
  "error": "Retiro fallido: Saldo insuficiente o cuenta no encontrada."
}
```

---

## 🧩 Próximas mejoras

* ✅ Integración con base de datos (H2 o PostgreSQL).
* ✅ Autenticación y autorización (Spring Security / JWT).
* ✅ Tests unitarios y de integración.
* ✅ Frontend React / Angular para panel de administración.
* ✅ Despliegue en contenedor Docker.

---

## 👨‍💻 Autor

**Daniel Felipe Agudelo Molina**
Ingeniero de Software – Docente y desarrollador backend & móvil
📧 [daniel.agudelomo@amigo.edu.co](mailto:daniel.agudelomo@amigo.edu.co)
🌐 [LinkedIn](https://www.linkedin.com/in/daniel-felipe-agudelo-molina)
💻 [GitHub](https://github.com/DanielDev87)

---

## 📝 Licencia

Este proyecto está licenciado bajo los términos de la [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

---

⭐ *Si este proyecto te resulta útil, no olvides dejar una estrella en GitHub.*

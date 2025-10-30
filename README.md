# 🏦 BankApp - Resumen Detallado

Este proyecto representa un pequeño **sistema bancario** diseñado con una estructura clara y organizada, ideal para aprender buenas prácticas de **programación orientada a objetos** y **arquitectura por capas**.

---

## 🧩 Estructura General del Proyecto

El proyecto está dividido en varias capas, cada una con una función específica que ayuda a mantener el código limpio, ordenado y fácil de mantener.

### 1️⃣ Capa de Controlador (`BankController`)
Esta capa actúa como **la recepción del banco**.  
Su tarea principal es **recibir las solicitudes del usuario**, como:

- Crear un cliente  
- Realizar depósitos o retiros  
- Transferir dinero entre cuentas  
- Consultar movimientos  

El controlador **no realiza cálculos** ni aplica reglas de negocio; solo **valida los datos** y delega la ejecución al servicio correspondiente.

---

### 2️⃣ Capa de Servicio (`BankService` / `BankServiceImpl`)
Aquí se encuentra **la lógica principal del negocio bancario**.  
Esta capa se encarga de:

- Verificar la existencia de las cuentas  
- Validar los montos y saldos disponibles  
- Registrar los movimientos y actualizar los saldos  

Si ocurre un problema (por ejemplo, intentar retirar más dinero del disponible), se lanza una **`DomainException`** explicando el error.

---

### 3️⃣ Capa de Modelo (`model`)
Las clases del modelo representan los elementos reales del banco:

- **`Customer`** → Representa al cliente y almacena sus cuentas.  
- **`Account`** → Clase base de las cuentas, maneja el saldo y movimientos.  
- **`CheckingAccount`** → Cuenta corriente.  
- **`SavingsAccount`** → Cuenta de ahorros (con posibles intereses).  
- **`Transaction`** → Registra cada movimiento realizado.  
- **`Money`** → Encapsula el manejo del dinero para evitar errores en cálculos.

---

### 4️⃣ Capa de Persistencia (`JsonRepository`)
Esta capa se encarga de **guardar y recuperar los datos** del sistema.

- **`JsonRepository`** → Administra el almacenamiento de clientes, cuentas y transacciones en archivos JSON.  
- **`FileManager`** → Se encarga de leer y escribir los archivos.  
- **`JsonUtil`** → Convierte objetos Java a JSON y viceversa.  

👉 Es una solución simple y funcional para prácticas, aunque en un entorno real se usaría una base de datos más robusta.

---

### 5️⃣ Patrón Estrategia (`InterestStrategy`)
Se utiliza el **patrón de diseño Estrategia** para calcular intereses.  
Esto permite cambiar fácilmente la “fórmula” de cálculo sin alterar el resto del código.

- **`InterestStrategy`** → Interfaz principal.  
- **`SimpleRateStrategy`** → Cálculo simple de intereses.  
- **`TieredRateStrategy`** → Cálculo por niveles.

---

### 6️⃣ Pruebas (`src/test`)
Incluye una clase de prueba que verifica que la aplicación se ejecute correctamente.  
Se recomienda **ampliar las pruebas** para cubrir depósitos, retiros, transferencias y almacenamiento en archivos.

---

## 🚀 Cómo Crear un Cliente en Thunder Client

Puedes usar **Thunder Client (VS Code)** para probar los endpoints de tu API.  
Sigue estos pasos para **crear un nuevo cliente**:

1. Abre **Thunder Client** en VS Code.  
2. Crea una nueva petición (**New Request**).  
3. Selecciona el método **POST** (se usa para crear o registrar datos).  
4. Escribe la URL del endpoint de tu API, por ejemplo:
   http://localhost:8080/api/customers

<img width="1919" height="1077" alt="image" src="https://github.com/user-attachments/assets/7b35c222-eae3-4f56-aa8a-c795052f0fcf" />
<img width="1917" height="1074" alt="image" src="https://github.com/user-attachments/assets/d2e8d595-2bcf-4d0c-b159-90f608d0e71b" />
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/aa1a78ac-4c13-43ef-9da6-426090b58f46" />

---
## 💬Postman

<img width="1919" height="970" alt="image" src="https://github.com/user-attachments/assets/18261515-4188-4ade-9c63-7bc622fad07e" />

<img width="1919" height="1025" alt="image" src="https://github.com/user-attachments/assets/66f0b132-683b-4fdd-8445-ab6f8d1fedc1" />

<img width="1919" height="971" alt="image" src="https://github.com/user-attachments/assets/0ea0f39e-3f1f-40c5-b58d-d38111a6d753" />

<img width="1919" height="971" alt="image" src="https://github.com/user-attachments/assets/dd813f12-2a78-40be-9536-dc20fd6736b1" />

<img width="1919" height="966" alt="image" src="https://github.com/user-attachments/assets/bdc9ddb6-7a95-4fc7-9919-ef7533f28eca" />

<img width="1919" height="1031" alt="image" src="https://github.com/user-attachments/assets/a8808629-454b-4268-9fa3-8457915a2106" />

<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/921aa4dd-8a49-447b-ac4c-8e0db27eb971" />

<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/c5025f4d-b29d-4fba-9ea7-7d2006e6aaa3" />

<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/0eec81dd-ff51-43ae-b99f-02afa62fdcad" />

<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/23f7799b-0301-479e-9d13-025bb584922b" />


---

## 🌐Swagger

<img width="1919" height="971" alt="image" src="https://github.com/user-attachments/assets/badc1e1b-7b96-4acf-b0bf-2a62b2951ff4" />

<img width="1919" height="962" alt="image" src="https://github.com/user-attachments/assets/5e5bbe23-5dad-4574-92fa-bf25bcfe9881" />

<img width="1919" height="970" alt="image" src="https://github.com/user-attachments/assets/82811e4a-2a12-433d-904e-8c3842dea19c" />

<img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/89913f0a-de8a-416f-8e71-2e40c4057993" />

<img width="1919" height="1024" alt="image" src="https://github.com/user-attachments/assets/9cb4102a-c499-4c8b-9856-12cd59ccf1a7" />

<img width="1919" height="1024" alt="image" src="https://github.com/user-attachments/assets/3978129d-1ac9-49de-8f29-4d087395d313" />

<img width="1919" height="1022" alt="image" src="https://github.com/user-attachments/assets/fc4f15cb-d744-4127-8d8e-912075e7124d" />

<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/ae564af1-4341-4237-9fa7-44745b379c78" />

<img width="1917" height="1029" alt="image" src="https://github.com/user-attachments/assets/9e9f41c9-f5c2-4933-bd43-a5122eba61fa" />

<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/d65ba41f-2edf-4d55-983d-b99c08f0d50b" />

<img width="1919" height="1022" alt="image" src="https://github.com/user-attachments/assets/c75a3cc7-fbbb-4be3-ab45-e9f57ee81fde" />

<img width="1919" height="1075" alt="image" src="https://github.com/user-attachments/assets/1e21db8c-18f8-4b6f-b924-5b2c722b826b" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/89f64e59-b588-42a4-bbd2-fa15f679110a" />































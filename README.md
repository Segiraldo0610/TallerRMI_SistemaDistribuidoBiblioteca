# 📚 Sistema de Biblioteca Distribuido con gRPC
*Taller de Sistemas Distribuidos — Febrero 2026*

👨‍💻 *Integrantes*
- Jose Guerrero  
- Samuel Giraldo  
- Marianne Coy  
- Daniel Diaz  

---

## 📖 Descripción del Proyecto

Este proyecto implementa un *sistema distribuido de gestión de préstamos de biblioteca* utilizando arquitectura *Cliente–Servidor*.

El sistema permite consultar, prestar y devolver libros mediante comunicación remota usando *gRPC*.

- 🔹 El *Servidor* administra la lógica del sistema y la base de datos.
- 🔹 El *Cliente* consume los servicios remotamente mediante una interfaz gráfica.
- 🔹 Ambos se ejecutan en *computadores diferentes*, demostrando comunicación distribuida real.

---

## 🏗 Arquitectura del Sistema


                 ┌────────────────────┐
                 │     CLIENTE GUI     │
                 │   (Java Swing)     │
                 └─────────┬──────────┘
                           │ gRPC
                           │
                    Red / TCP-IP
                           │
                 ┌─────────▼──────────┐
                 │      SERVIDOR       │
                 │   gRPC + Java       │
                 │                     │
                 │   SQLite Database   │
                 └─────────────────────┘


---

## 📂 Estructura del Proyecto


proyecto/
│
├── server/
│   ├── db/
│   │   └── biblioteca.db
│   └── src/main/resources/
│       ├── schema.sql
│       └── seed.sql
│
└── cliente/
    ├── app/
    │   └── src/main/java/com/example/cliente/
    │       ├── BibliotecaGUI.java
    │       └── ClienteMain.java
    │
    └── proto/
        └── library.proto


---

## 🚀 Ejecución del Sistema

### 🖥️ 1. Ejecutar el Servidor

📍 *Debe ejecutarse en el computador servidor*

bash
cd server
mvn clean package
mvn exec:java -Dexec.args="50051"


✅ Características:

- La base de datos SQLite se crea automáticamente.
- El servidor queda escuchando en el puerto *50051*.
- Centraliza toda la lógica del sistema.

---

### 💻 2. Ejecutar el Cliente

📍 *Debe ejecutarse en otro computador*

bash
cd cliente/app
mvn compile
mvn exec:java


Al iniciar:

1. Ingresar la *IP del servidor*
2. Puerto: 50051
3. Presionar *Conectar*

---

## ⚙️ Funcionalidades Implementadas

✅ *Consultar libro por ISBN*
- Verifica existencia
- Muestra ejemplares disponibles

✅ *Préstamo por ISBN*
- Registra préstamo
- Genera fecha de devolución automática (7 días)

✅ *Préstamo por Título*
- Búsqueda alternativa del libro

✅ *Devolución de Libro*
- Actualiza disponibilidad en tiempo real

Todas las operaciones se realizan mediante *RPC síncrono*.

---

## 📚 Libros Iniciales del Sistema

| ISBN | Título |
|------|--------|
| 9780307474278 | Libro 1 |
| 9788437604947 | Libro 2 |
| 9788466333978 | Libro 3 |
| 9780060883287 | Libro 4 |
| 9789500721507 | Libro 5 |

---

## 🧰 Tecnologías Utilizadas

- ☕ Java 17  
- 📦 Maven  
- 🔗 gRPC  
- 📜 Protocol Buffers  
- 🗄 SQLite  
- 🖥 Java Swing  

---

## 🌐 Características de Sistemas Distribuidos

Este proyecto demuestra:

- ✔ Arquitectura Cliente–Servidor  
- ✔ Comunicación remota mediante RPC  
- ✔ Separación cliente / servidor  
- ✔ Base de datos centralizada  
- ✔ Ejecución en múltiples computadores  
- ✔ Servicios distribuidos sobre red TCP/IP  

---

## 📸 Evidencia Esperada

Para la validación del taller:

- Servidor ejecutándose en una máquina
- Cliente ejecutándose en otra máquina
- Conexión mediante IP real
- Operaciones exitosas entre nodos

- link Video: https://drive.google.com/file/d/111_ZIPO7beguF9903jV2GrLotwukdgLI/view?usp=sharing

---

## ✅ Estado del Proyecto

✔ Implementación completa  
✔ Comunicación distribuida funcional  
✔ Interfaz gráfica operativa  
✔ Persistencia en base de datos  

---

⭐ *Proyecto desarrollado para la asignatura Sistemas Distribuidos — 2026*

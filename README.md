# Medi Connect Gateway

Repositorio correspondiente al **API Gateway / Backend For Frontend (BFF)** del sistema distribuido de gestión de citas médicas.

---

## 🧩 Descripción

Este componente actúa como punto de entrada principal del sistema.

El frontend no se comunica directamente con los microservicios, sino que envía todas sus solicitudes al Gateway, el cual se encarga de redirigirlas internamente.

Esto simplifica la arquitectura y mejora la seguridad, mantenibilidad y escalabilidad de la solución.

---

## 🎯 Función principal

* Centralizar las peticiones del cliente.
* Redirigir solicitudes a microservicios internos.
* Ocultar la complejidad del sistema distribuido.
* Unificar el acceso a la API.
* Actuar como Backend For Frontend (BFF).

---

## 🛠️ Tecnologías utilizadas

* Java 17
* Spring Boot
* Spring Cloud Gateway
* HTML5
* JavaScript
* Bootstrap
* Maven
* Docker
* Swagger/OpenAPI

---

## 🧱 Arquitectura

Este repositorio cumple el rol de:

* 🌐 API Gateway
* 🔄 Backend For Frontend (BFF)

El sistema sigue una arquitectura de microservicios donde el Gateway actúa como intermediario entre el cliente y los servicios internos.

### Microservicios integrados

* ms-pacientes
* ms-doctores
* ms-citas

---

## 🔗 Rutas principales

* `/api/pacientes` → ms-pacientes
* `/api/doctores` → ms-doctores
* `/api/citas` → ms-citas

---

## 🔗 Repositorios relacionados

### 📚 Recursos (Pacientes y Doctores)

https://github.com/Matyrawr/medi-connect-resources

### ⚙️ Core (Citas)

https://github.com/Matyrawr/medi-connect-core

---

## 🧠 Patrones de diseño aplicados

### API Gateway Pattern

Centraliza todas las solicitudes realizadas por el cliente.

### Facade Pattern

Oculta la complejidad interna del sistema y ofrece una interfaz única de acceso.

### DTO Pattern

Permite controlar la información intercambiada entre servicios.

### Singleton Pattern

Utilizado por Spring para administrar componentes y servicios.

---

## 🎯 Justificación técnica

El uso de un Gateway permite:

* Reducir el acoplamiento entre frontend y backend.
* Mejorar la seguridad del sistema.
* Facilitar la escalabilidad.
* Simplificar la comunicación entre servicios.
* Centralizar configuraciones y reglas de acceso.

Ejemplo:

El cliente solo conoce una única URL de acceso, mientras que el Gateway administra internamente la comunicación con múltiples microservicios.

---

## 🚀 Beneficios

* Arquitectura modular.
* Mejor mantenibilidad.
* Mayor control del tráfico de red.
* Escalabilidad independiente por servicio.
* Integración sencilla de nuevos microservicios.

---

## 📄 Documentación API

Los microservicios integrados exponen documentación interactiva mediante Swagger/OpenAPI, permitiendo validar y probar los endpoints REST sin herramientas externas.

---

## 💾 Persistencia

La solución utiliza bases de datos H2 en modo archivo para asegurar la persistencia de la información.

Esto permite mantener los datos almacenados incluso después de reiniciar la aplicación o los contenedores Docker.

---

## 🧪 Pruebas Unitarias

Se implementaron pruebas unitarias utilizando:

* JUnit 5
* Mockito

Las pruebas validan la lógica de negocio de los microservicios y contribuyen a una cobertura global superior al 60%, cumpliendo los requisitos establecidos en la pauta de evaluación.

---

## ▶️ Ejecución

Para levantar el sistema completo se recomienda utilizar Docker Compose desde el repositorio Core:

```bash
docker-compose up
```

### Ejecución local

```bash
mvn spring-boot:run
```

---



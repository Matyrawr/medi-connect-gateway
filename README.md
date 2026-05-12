# Medi Connect Gateway

Repositorio correspondiente al **API Gateway / Backend For Frontend (BFF)** del sistema distribuido de gestión de citas médicas.

---

## 🧩 Descripción

Este componente actúa como punto de entrada principal del sistema.

El frontend no se comunica directamente con los microservicios, sino que envía todas sus solicitudes al Gateway, el cual se encarga de redirigirlas internamente.

Esto simplifica la arquitectura y mejora la seguridad y mantenibilidad.

---

## 🎯 Función principal

- Centralizar las peticiones del cliente
- Redirigir solicitudes a microservicios internos
- Ocultar la complejidad del sistema
- Unificar el acceso a la API

---

## 🛠️ Tecnologías utilizadas

- Java 17
- Spring Boot
- Spring Cloud Gateway
- HTML5
- JavaScript
- Bootstrap
- NPM
- Docker

---

## 🧱 Arquitectura

Este repositorio cumple el rol de:

- 🌐 API Gateway  
- 🔄 Backend For Frontend (BFF)

El sistema sigue una arquitectura de microservicios donde el Gateway actúa como intermediario entre el cliente y los servicios internos.

---

## 🔗 Rutas principales (ejemplo)

- `/api/pacientes` → ms-pacientes  
- `/api/doctores` → ms-doctores  
- `/api/citas` → ms-citas  

---

## 🔗 Repositorios relacionados

- 📚 Recursos (Pacientes y Doctores)  
  https://github.com/Matyrawr/medi-connect-resources  

- ⚙️ Core (Citas + Docker)  
  https://github.com/Matyrawr/medi-connect-core  

---

## 🧠 Patrones de diseño aplicados

- Facade Pattern → simplifica el acceso al sistema  
- API Gateway Pattern → centraliza peticiones  
- DTO Pattern → control de datos enviados  
- Singleton → gestión eficiente de instancias (Spring Beans)

---

## 🎯 Justificación técnica

El uso de un Gateway permite:

- Reducir el acoplamiento entre frontend y backend
- Mejorar la seguridad
- Facilitar la escalabilidad
- Simplificar la comunicación entre servicios

Ejemplo:
El cliente solo conoce una URL, mientras que el Gateway gestiona múltiples servicios internamente.

---

## 🚀 Beneficios

- Arquitectura más ordenada
- Mejor mantenibilidad
- Mayor control del tráfico
- Sistema preparado para crecer

---

## ▶️ Ejecución

Para levantar el sistema completo se recomienda utilizar Docker Compose desde el repositorio core:

```bash
docker-compose up

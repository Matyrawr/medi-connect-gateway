# Plan de Pruebas Unitarias y Cobertura

Este documento detalla la estructura de las pruebas unitarias implementadas en los distintos microservicios, sus propósitos y las herramientas tecnológicas utilizadas para asegurar la calidad del código.

---

## Detalle de los Tests por Módulo

### Pacientes
**Archivo:** `PacienteServiceTest.java`

* `crearGuardaYDevuelvePacienteDTO()`: Comprueba que al crear un paciente el servicio transforma el DTO de entrada, llama al repositorio y devuelve un DTO con el ID y los datos guardados.
* `buscarPorIdCuandoNoExisteLanzaExcepcion()`: Valida que, si el repositorio no encuentra al paciente, el servicio lance una excepción `IllegalArgumentException`.

> **Propósito:** Asegurar que el alta de pacientes funcione correctamente y que el servicio falle de forma controlada cuando no existe el registro.

---

### Doctores
**Archivo:** `DoctorServiceTest.java`

* `crearGuardaYDevuelveDoctorDTO()`: Verifica que el servicio crea un doctor correctamente, guarda la entidad y devuelve el DTO con los campos de especialidad, horario y duración de la cita.
* `buscarPorIdCuandoNoExisteLanzaExcepcion()`: Comprueba el mismo patrón de error controlado si el doctor no existe en el sistema.

> **Propósito:** Validar el alta y la consulta básica de doctores aislándolo de la base de datos real.

---

### Citas
**Archivo:** `CitaServiceTest.java`

* `agendarGuardaYDevuelveCita()`: Confirma que una cita se agenda bien, se marca con el estado `AGENDADA`, se persiste en la base de datos y la respuesta devuelve los datos esperados.
* `disponibilidadOmitioLosSlotsOcupados()`: Comprueba que el servicio calcula la disponibilidad por hora y excluye correctamente los turnos que ya están ocupados.
* `cancelarCambiaEstadoACancelada()`: Valida que una cita existente cambie su estado a `CANCELADA`.
* `cancelarCuandoNoExisteLanzaExcepcion()`: Verifica el error controlado si se intenta cancelar una cita inexistente.

> **Propósito:** Cubrir la lógica clave del módulo más crítico del sistema: el agendamiento, la gestión de disponibilidad y las cancelaciones.

---

## Dependencias y Herramientas Utilizadas

Las pruebas y el entorno de desarrollo se sustentan en las siguientes configuraciones dentro de los archivos `pom.xml` (`ms-pacientes/pom.xml`, `ms-doctores/pom.xml` y `ms-citas/pom.xml`):

### Núcleo de Testing
* **`spring-boot-starter-test`**: Aporta la suite de JUnit 5, aserciones, el soporte nativo de Spring Test y Mockito para la creación de entornos aislados.
* **`MockitoExtension`**: Extensión encargada de habilitar y procesar las anotaciones `@Mock` e `@InjectMocks` junto con JUnit 5.
* **`ArgumentCaptor`**: Utilizado para capturar los objetos que el servicio transfiere hacia el repositorio, permitiendo verificar que la entidad se construyó con las propiedades correctas.
* **`jacoco-maven-plugin`**: Plugin encargado de analizar la ejecución de los tests y generar los reportes de cobertura de código correspondientes.

### Herramientas de Soporte (No asociadas directamente a los tests)
* **`springdoc-openapi-starter-webmvc-ui`**: Habilita la interfaz de documentación interactiva de Swagger (no interviene en la lógica de pruebas).
* **`com.h2database:h2`**: Base de datos en memoria utilizada para el funcionamiento general de la aplicación en desarrollo y el acceso a su consola local.
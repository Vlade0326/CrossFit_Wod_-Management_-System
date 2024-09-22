# CrossFit_Wod_-Management_-System
Sistema de administración de clases para un box de CrossFit.

# CrossFit Class Management System

## Descripción

Este es un sistema de administración de clases para un *box de CrossFit, desarrollado en **Java (Spring Boot)* para el backend y *React* para el frontend, con *MySQL* como base de datos. El sistema permite a los administradores gestionar los WODs (Workouts of the Day), inscribir a los atletas, ver resultados, clasificaciones y generar gráficos de progreso de los atletas a lo largo del tiempo. También permite a los atletas registrarse, anotar sus resultados y ver su progreso. Además, incluye funcionalidades para enviar notificaciones por correo a los usuarios y exportar reportes en formato *PDF* o *CSV*.

## Características Principales

- *Autenticación y Roles*: Autenticación de usuarios mediante JWT con roles diferenciados de administrador y atleta.
- *Gestión de WODs*: CRUD para WODs, permitiendo la creación, edición y eliminación de entrenamientos.
- *Matriculación de Atletas*: Inscripción de atletas a los WODs disponibles según el horario.
- *Resultados y Clasificaciones*: Registro de resultados y visualización de clasificaciones por horario de WOD.
- *Progreso y Estadísticas*: Gráficos avanzados que muestran el progreso de los atletas y predicciones de rendimiento futuro.
- *Notificaciones por Correo: Integración con **SendGrid* para enviar notificaciones sobre inscripciones, resultados y recordatorios.
- *Exportación de Reportes: Exportación de resultados y progreso en formato **PDF* y *CSV*.

## Tecnologías Utilizadas

- *Backend*: 
  - Java con *Spring Boot* (controladores REST)
  - JWT para autenticación
  - Integración con *SendGrid* para notificaciones
  - Servicios para exportación de datos en *PDF* y *CSV*

- *Frontend*: 
  - *React* con gestión de estado
  - *Chart.js* para gráficos de progreso

- *Base de Datos*:
  - *MySQL* para almacenar usuarios, WODs, resultados y datos de progreso

## Instalación

### Requisitos

- *Java 11+*
- *Node.js 14+* y *npm* (para frontend)
- *MySQL* (con un servidor en ejecución)
- *SendGrid* API Key

### Backend

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/usuario/crossfit-class-management.git
   cd crossfit-class-management/backend

2. Configurar el archivo application.properties en src/main/resources con las credenciales de MySQL y la API Key de SendGrid:

spring.datasource.url=jdbc:mysql://localhost:3306/crossfit
spring.datasource.username=root
spring.datasource.password=tu_contraseña
sendgrid.api.key=TU_SENDGRID_API_KEY


3. Compilar y ejecutar el backend:

./mvnw clean install
java -jar target/crossfit-management.jar



Frontend

1. Navegar al directorio del frontend:

cd ../frontend


2. Instalar las dependencias:

npm install


3. Ejecutar la aplicación React:

npm start



La aplicación React estará disponible en http://localhost:3000.

Base de Datos

1. Crear la base de datos MySQL:

CREATE DATABASE crossfit;


2. Ejecutar las migraciones (si usas una herramienta como Flyway o Liquibase) o importar un script SQL que defina las tablas necesarias:

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50),
    password VARCHAR(255),
    role VARCHAR(20)
);

CREATE TABLE wods (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    description TEXT,
    date DATE,
    time TIME,
    level VARCHAR(20)
);

-- Otras tablas como athletes, wod_results, etc.



Uso

Como Administrador

Crear, editar y eliminar WODs.

Inscribir atletas a WODs programados.

Ver clasificaciones y resultados.

Enviar notificaciones por correo a los atletas.

Exportar reportes en PDF y CSV.


Como Atleta

Inscribirse a los WODs disponibles.

Registrar resultados tras completar el WOD.

Ver gráficos de progreso personal y predicciones.


API Endpoints

Autenticación:

POST /auth/login: Iniciar sesión y obtener JWT.

POST /auth/register: Registrar un nuevo usuario.


WODs:

GET /wods: Listar todos los WODs disponibles.

POST /wods: Crear un nuevo WOD (solo administrador).

PUT /wods/{id}: Actualizar un WOD (solo administrador).

DELETE /wods/{id}: Eliminar un WOD (solo administrador).


Atletas:

GET /athletes: Listar atletas registrados (solo administrador).

POST /athletes/wod/{wodId}/register: Inscribir atleta en un WOD.


Resultados:

POST /results: Registrar resultados de un WOD.

GET /results/wod/{wodId}: Ver resultados de un WOD.


Progreso:

GET /progress/{athleteId}: Ver el progreso del atleta a lo largo del tiempo.



Licencia

Este proyecto está bajo la licencia MIT.

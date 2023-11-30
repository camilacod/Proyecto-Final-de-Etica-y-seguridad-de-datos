# Proyecto-Final-de-Etica-y-seguridad-de-datos

Aquí tienes un esquema mejorado para el README del informe de tu proyecto:

---

# Proyecto de Privacidad y Ética en Datos

## Contexto e Introducción al Proyecto

Este proyecto aborda la privacidad y la ética en el manejo de datos, aplicando técnicas avanzadas para garantizar la seguridad de la información sin comprometer su utilidad en análisis y modelado. El proyecto se enfoca en un conjunto de datos específico, se centra en el análisis del dataset [Health Insurance Cross Sell Prediction](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction) que contiene 381,000 filas. Se han aplicado prácticas anonimizacón, de privacidad diferencial y evaluaciones de impacto en la protección de datos (DPIA), mientras se incorporan consideraciones éticas sobre sesgo algorítmico, transparencia y consentimiento.

## Sobre la base de datos y las transformaciones previas necesarias

El dataset original contiene las siguientes variables:

| Variable              | Descripción                                                   |
|----------------------|---------------------------------------------------------------|
| Gender               | Género del cliente                                            |
| Age                  | Edad del cliente                                              |
| Previously_Insured   | 1 : Cliente tiene seguro de vehículo, 0 : Cliente no tiene seguro de vehículo |
| Vehicle_Age          | Tiempo del vehículo                                           |
| Vehicle_Damage       | 1 : Cliente dañó su vehículo en el pasado. 0 : Cliente no dañó su vehículo en el pasado |
| Annual_Premium       | Monto que necesita pagar el cliente como premium en el año   |
| Policy_Sales_Channel | Código anónimo del canal de comunicación con el cliente (Correo, persona, teléfono, etc) |
| Vintage              | Número de días que el cliente ha estado asociado con la compañía |
| Response             | 1 : Cliente interesado, 0 : Cliente no interesado              |


Sobre la data real, se agregará data mock que puede ser considerada sensible sobre cada cliente incluyendo:

| Variable      | Descripción                                      |
|---------------|--------------------------------------------------|
| id            | Identificador único para el usuario              |
| name          | Nombre de la persona                             |
| surname       | Apellido de la persona                           |
| password      | Contraseña del usuario                           |
| SSN           | Código único                    |
| email         | Correo electrónico de la persona                 |
| blocked       | Indicador de si el usuario está bloqueado        |
| user_id       | Identificador del usuario (referencia a `users`) |
| vehicle_id    | Identificador único para el vehículo             |
| brand         | Marca del vehículo                               |
| model         | Modelo del vehículo                              |
| year          | Año del vehículo                                 |
| car_vin       | Número de identificación del vehículo (VIN)      |
| use_place     | Lugar de uso del vehículo                        |
| insurance_id  | Identificador único para el seguro               |
| username      | Nombre de usuario para intentos de login        |
| timestamp     | Marca de tiempo del intento de login fallido    |




La estructura de la base de datos se detalla en las siguientes tablas:

```sql
CREATE TABLE users(
    id int NOT NULL AUTO_INCREMENT,
    name varchar(100) NOT NULL,
    surname varchar(100) NOT NULL,
    password varchar(100) NOT NULL,
    SSN varchar(100) UNIQUE NOT NULL,
    email varchar(100) UNIQUE NOT NULL,
    blocked bool NOT NULL,
    PRIMARY KEY(id)
);

CREATE TABLE vehicles(
    user_id int UNIQUE NOT NULL,
    vehicle_id varchar(100) UNIQUE NOT NULL,
    brand varchar(20) NOT NULL,
    model varchar(30) NOT NULL,
    year int NOT NULL,
    car_vin varchar(100) UNIQUE NOT NULL,
    use_place varchar(100) NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id),
    PRIMARY KEY(vehicle_id)
);

CREATE TABLE insurance(
    user_id int UNIQUE NOT NULL,
    insurance_id varchar(100) UNIQUE NOT NULL,
    previously_insured bool NOT NULL,
    vintage int,
    response bool NOT NULL, 
    FOREIGN KEY (user_id) REFERENCES users(id),
    PRIMARY KEY(insurance_id)
);

CREATE TABLE failed_login_attempts(
    id int NOT NULL AUTO_INCREMENT,
    username varchar(100) NOT NULL,
    timestamp timestamp NOT NULL,
    PRIMARY KEY(id)
);


```

## Breve descripción

   - Se evaluaron los riesgos de privacidad y éticos del conjunto de datos tanto,describiendo las posibles vulnerabilidades en términos de privacidad y confidencialidad de la información. antes como después de aplicar un plan de anonimización.
   - Realización de DPIA para identificar y mitigar riesgos.
   - Reflexión sobre sesgos algorítmicos, transparencia y consentimiento.
   - La implementación se llevo a cabo en un jupyter notebook.




## Estrategias de Uso Seguro de los Datos



## Plan de Respuesta ante Incidentes de Seguridad



## Recomendaciones de Protección de Datos Futura



---

&copy; 2023 Proyecto de Privacidad y Ética en Datos

---


# Parqueadero AparClic

### Problemática
En la actualidad, la gestión eficiente de los espacios de estacionamiento se ha convertido en un desafío significativo para empresas, centros comerciales, aeropuertos y otros establecimientos con gran afluencia de vehículos. La creciente demanda de espacios de parqueo y la necesidad de optimizar el uso de estos espacios han llevado a la búsqueda de soluciones tecnológicas avanzadas. Una de estas soluciones es el sistema de parqueadero basado en el reconocimiento de matrículas (License Plate Recognition), LPR.

### Solución
Este sistema de parqueadero basado en LPR aborda estas problemáticas mediante la implementación de tecnologías avanzadas de reconocimiento de matrículas y automatización de procesos. Este sistema ofrece las siguientes ventajas

* Automatización del Control de Acceso: El reconocimiento automático de matrículas permite la apertura y cierre de barreras de manera rápida y precisa, reduciendo el tiempo de espera y mejorando el flujo de vehículos.

* Mejora de la Seguridad: Al registrar de manera automática y precisa cada vehículo que ingresa y sale, se mejora la seguridad del parqueadero. Además, se pueden generar alertas para vehículos no autorizados o sospechosos.

* Generación de Datos y Reportes: El sistema recopila datos valiosos sobre el uso del parqueadero, permitiendo a la administración generar reportes específicos. Esta información es crucial para la toma de decisiones estratégicas y para mejorar continuamente el servicio ofrecido.

### Objetivo del Proyecto

El objetivo principal de este proyecto es desarrollar e implementar un sistema de parqueadero basado en el reconocimiento de matrículas que mejore la eficiencia operativa. Este sistema debe ser capaz de integrarse con los dispositivos de control de acceso existentes, proporcionar una interfaz de usuario amigable y generar reportes específicos para la administración del parqueadero.


## Análisis: Definición de requerimientos. 

### Requisitos Funcionales

#### RF1: Detección y Reconocimiento de Matrículas: 
+ Captura de imágenes de los vehículos que entran y salen del parqueadero.
+ Procesamiento de las imágenes para identificar y extraer las matrículas.
+ Conversión de las imágenes de las matrículas a texto (OCR)

#### RF2: Gestión de Entradas y Salidas:
+ Registro de la hora de entrada y salida de cada vehículo.
+ Almacenamiento de la información de las matrículas en una base de datos.


#### RF3: Control de Acceso:
+ Validación de matrículas autorizadas para permitir la entrada/salida automática.
+ Generación de alertas para matrículas no autorizadas (Placas No nacionales).

#### RF4: Interfaz de Usuario:
+ Panel de control para los operadores del parqueadero.
+ Interfaz web para usuarios finales para consultar información sobre su vehículo, estado del parqueadero y cancelación de parking.

#### RF5: Generación de Reportes:
+ Reportes de ventas del parqueadero.
+ Historial de entradas y salidas.

### Requisitos No Funcionales

#### RNF1: Performance:
+ Alta precisión y rapidez en el reconocimiento de matrículas.
+ Tiempo de respuesta bajo para la apertura de barreras.

#### RNF2: Seguridad:
+ Protección de la información almacenada.
+ Mecanismos de autenticación y autorización para usuarios del sistema.

#### RNF3: Escalabilidad:
+ Capacidad para manejar un incremento en el número de vehículos y cámaras.
+ Facilidad para agregar nuevas funcionalidades.

#### RNF4: Fiabilidad:
+ Disponibilidad constante del sistema.
+ Tolerancia a fallos.

#### RNF5: Usabilidad:
+ Interfaz intuitiva y fácil de usar.
+ Capacitación mínima requerida para los operadores.


[Documentación IEEE 830](https://drive.google.com/file/d/1ErPhPICtgThQhz2olz8FUP8MQobRVnwi/view?usp=drive_link)


## Diseño Base de Datos
#### Tabla de Vehiculos
| Campo          | Tipo         | Clave         | Descripción                     |
|----------------|--------------|---------------|---------------------------------|
| id             | INT          | PK            | Identificador único             |
| matricula      | VARCHAR(10)  | UNIQUE        | Matrícula del vehículo          |
| horaEntrada    | DATETIME     |               | Hora de entrada al parqueadero  |
| horaSalida     | DATETIME     |               | Hora de salida del parqueadero  |
| autorizado     | BOOLEAN      |               | Indica si el vehículo está autorizado |

#### Tabla de Operadores
| Campo          | Tipo         | Clave         | Descripción                     |
|----------------|--------------|---------------|---------------------------------|
| id             | INT          | PK            | Identificador único             |
| nombreOperador | VARCHAR(50)  | UNIQUE        | Nombre del operador             |
| contraseña     | VARCHAR(50)  |               | Contraseña del operador         |

#### Tabla de Reportes
| Campo          | Tipo         | Clave         | Descripción                     |
|----------------|--------------|---------------|---------------------------------|
| id             | INT          | PK            | Identificador único             |
| tipoReporte    | VARCHAR(50)  |               | Tipo de reporte                 |
| fechaGeneracion| DATETIME     |               | Fecha de generación del reporte |
| contenido      | TEXT         |               | Contenido del reporte           |


> Script de la Base de Datos

```sql
DROP DATABASE IF EXISTS Parqueadero;

    CREATE DATABASE Parqueadero;

    USE cultivo;

-- Tabla de Vehiculos
CREATE TABLE Vehiculos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    matricula VARCHAR(10) UNIQUE,
    horaEntrada DATETIME,
    horaSalida DATETIME,
    autorizado BOOLEAN
);

-- Tabla de Operadores
CREATE TABLE Operadores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombreOperador VARCHAR(50) UNIQUE,
    contraseña VARCHAR(50)
);

-- Tabla de Reportes
CREATE TABLE Reportes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    tipoReporte VARCHAR(50),
    fechaGeneracion DATETIME,
    contenido TEXT
);

```


## Diagramas UML
Estos diagramas proporcionarán una representación visual y comprensible de los diferentes componentes y flujos del sistema.

### Diagrama de Clases
El diagrama de clases modela la estructura estática del sistema, mostrando las clases, sus atributos, métodos y las relaciones entre ellas.

![Diagrama de Clases](Imagenes/Diagrama%20de%20Clases.png)

### Diagrama de Secuencias
El diagrama de secuencia ilustra cómo interactúan los diferentes objetos del sistema a lo largo del tiempo para llevar a cabo un proceso específico.

![Diagrama de Secuenias](Imagenes/Diagrama%20de%20Secuencia.png)

### Diagrama de Casos de Uso
El diagrama de casos de uso describe las interacciones entre los actores (conductor y administrador) y el sistema de parqueadero, destacando los principales casos de uso o funcionalidades.

![Diagrama de Casos](Imagenes/Diagrama%20de%20Casos%20de%20Uso.png)

## Mockup
El diseño de modelado se centra en la interfaz gráfica e interactiva desde la perspectiva tanto del usuario como del administrador. En él, se incluyen componentes como pagos, facturación, liquidación y inicio de sesión. Puedes encontrar la visualización respectiva en el siguiente enlace.

### [Link Modelado](https://temenico.my.canva.site/aparclic)
![Home](Imagenes/Home%20Service.png)

## Ver Planificacion
La planificación del proyecto en el marco de trabajo para desarrollo ágil de Software Scrum, se puede ver en el siguiente enlace redireccionado a Trello y al Drive:

### | [Google Drive](https://drive.google.com/drive/u/1/folders/138pIiy6212PmfVG_FhAQEK_8RMzvf2i0) | [Trello ](https://trello.com/b/21BfO6vM/proyecto) |


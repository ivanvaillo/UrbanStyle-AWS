# UrbanStyle AWS E-commerce Architecture

## Descripción

UrbanStyle es un proyecto de diseño e implementación de una arquitectura cloud para una plataforma de comercio electrónico basada en WordPress y WooCommerce.

El objetivo del proyecto es construir una infraestructura segura, escalable y altamente disponible utilizando servicios de Amazon Web Services (AWS).

## Arquitectura

La arquitectura propuesta utiliza una infraestructura distribuida en dos Availability Zones, con diferentes componentes destinados a mejorar la disponibilidad, escalabilidad y seguridad de la aplicación.

### Diagrama lógico

El siguiente diagrama representa de forma simplificada los principales componentes funcionales de la plataforma.

![Diagrama lógico](diagrams/logical-diagram.jpg)

### Diagrama de arquitectura

El siguiente diagrama muestra la arquitectura propuesta en AWS y la relación entre los diferentes servicios que forman parte de la solución.

![Diagrama de arquitectura](diagrams/aws-architecture-diagram.png)

## Servicios AWS

### Servicios implementados

Durante el despliegue práctico se implementaron y validaron los siguientes componentes:

- **Amazon VPC** — infraestructura de red y aislamiento de los recursos.
- **Amazon EC2** — ejecución de las instancias de WordPress.
- **EC2 Auto Scaling** — gestión y escalabilidad automática de las instancias.
- **Application Load Balancer** — distribución del tráfico entre las instancias.
- **Target Group** — registro y comprobación del estado de las instancias.
- **Amazon RDS** — base de datos MySQL gestionada.
- **Security Groups** — control del tráfico entre los diferentes componentes.

### Servicios contemplados en el diseño

La arquitectura también contempla el uso de los siguientes servicios:

- **Amazon Route 53** — gestión del DNS.
- **AWS Certificate Manager (ACM)** — gestión de certificados SSL/TLS.
- **AWS WAF** — protección de la aplicación frente a tráfico malicioso.
- **Amazon CloudWatch** — monitorización de los recursos.
- **AWS Backup** — gestión de copias de seguridad.
- **AWS IAM** — gestión de identidades y permisos.

Estos servicios forman parte del diseño de la solución, pero no pudieron implementarse durante el despliegue práctico debido a las limitaciones de recursos y permisos del entorno de laboratorio.

## Implementación

La implementación práctica se centró en los principales componentes de infraestructura disponibles en el entorno de laboratorio.

La VPC se configuró utilizando dos Availability Zones, permitiendo distribuir los recursos y mejorar la disponibilidad de la aplicación.

Las instancias EC2 se gestionan mediante un Auto Scaling Group y utilizan una Launch Template para mantener una configuración consistente.

El Application Load Balancer distribuye el tráfico hacia las instancias registradas en el Target Group. Las dos instancias desplegadas aparecen en estado `Healthy`, demostrando que los destinos se encuentran disponibles para recibir tráfico.

Amazon RDS se utiliza como servicio gestionado para la base de datos MySQL de la aplicación.

## Alta disponibilidad

La infraestructura se distribuye entre dos Availability Zones para reducir el impacto de posibles fallos en una única zona.

El Application Load Balancer distribuye las peticiones entre las instancias EC2 gestionadas por el Auto Scaling Group.

Las instancias se encuentran distribuidas entre diferentes Availability Zones y registradas en el Target Group, donde se realizan comprobaciones de estado para verificar su disponibilidad.

## Escalabilidad

El Auto Scaling Group permite gestionar la capacidad de la aplicación de forma automática.

La configuración establece un número mínimo y máximo de instancias, permitiendo adaptar la capacidad disponible a las necesidades de la aplicación.

La utilización de una Launch Template permite que las nuevas instancias creadas por Auto Scaling utilicen una configuración consistente.

## Base de datos

La aplicación utiliza Amazon RDS con MySQL como sistema de gestión de base de datos.

RDS permite utilizar una base de datos gestionada por AWS, reduciendo la necesidad de administrar directamente la infraestructura subyacente.

El entorno utiliza un DB Subnet Group asociado a las Availability Zones de la VPC.

## Seguridad

La arquitectura utiliza Security Groups para controlar las comunicaciones entre los diferentes componentes de la infraestructura.

Se configuraron Security Groups independientes para:

- Application Load Balancer.
- Instancias EC2.
- Amazon RDS.

Cada grupo permite controlar el tráfico necesario para la comunicación entre las diferentes capas de la aplicación.

La arquitectura completa contempla además AWS WAF, ACM e IAM como mecanismos adicionales de protección y control, aunque estos servicios no pudieron implementarse debido a las limitaciones del entorno de laboratorio.

## Evidencias del despliegue

Las evidencias del despliegue se encuentran en la carpeta `screenshots/`.

Las capturas muestran diferentes elementos de la infraestructura implementada, incluyendo:

- Launch Template.
- Auto Scaling Group.
- Availability Zones.
- Integración con el Load Balancer.
- Configuración de capacidad de Auto Scaling.
- Target Group.
- Instancias en estado `Healthy`.
- Application Load Balancer.
- Amazon RDS.
- RDS Subnet Group.
- Security Groups.
- VPC y configuración de networking.
- Aplicación WordPress funcionando.

## Resultado final

La aplicación WordPress de UrbanStyle fue desplegada correctamente sobre una infraestructura AWS distribuida entre dos Availability Zones.

El tráfico es distribuido mediante el Application Load Balancer hacia las instancias EC2 gestionadas por Auto Scaling, mientras que Amazon RDS proporciona la capa de base de datos.

La implementación permite demostrar conceptos de alta disponibilidad, escalabilidad horizontal, balanceo de carga, segmentación de red y control de acceso mediante Security Groups.

## Conocimientos aplicados

Este proyecto permite demostrar conocimientos prácticos en:

- Diseño de arquitecturas cloud.
- Amazon VPC y networking.
- Amazon EC2.
- EC2 Auto Scaling.
- Application Load Balancer.
- Target Groups.
- Amazon RDS y MySQL.
- Security Groups.
- Alta disponibilidad.
- Escalabilidad horizontal.
- Seguridad en AWS.
- Diseño siguiendo principios del AWS Well-Architected Framework.

## Limitaciones del entorno

El proyecto se desarrolló en un entorno de laboratorio con determinadas restricciones de recursos y permisos.

Como consecuencia, algunos servicios incluidos en el diseño arquitectónico no pudieron implementarse durante la fase práctica:

- Amazon Route 53.
- AWS Certificate Manager.
- AWS WAF.
- Amazon CloudWatch.
- AWS Backup.
- AWS IAM.

Estos componentes se mantienen en la arquitectura propuesta como parte de una solución orientada a un entorno de producción, pero no se presentan como servicios desplegados y validados en el laboratorio.

## Conclusiones

El proyecto permitió diseñar e implementar una arquitectura cloud para una aplicación de comercio electrónico basada en WordPress y WooCommerce.

La implementación práctica permitió trabajar con componentes fundamentales de AWS como VPC, EC2, Auto Scaling, Application Load Balancer, Target Groups, RDS y Security Groups.

La solución resultante proporciona una base escalable y distribuida entre dos Availability Zones, aplicando principios de alta disponibilidad, seguridad y escalabilidad.

Las limitaciones del entorno de laboratorio impidieron implementar algunos servicios adicionales contemplados en el diseño, pero estos fueron considerados dentro de la arquitectura propuesta para completar una solución orientada a producción.

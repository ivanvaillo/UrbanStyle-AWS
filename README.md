# UrbanStyle AWS E-commerce Architecture

Arquitectura cloud en AWS para una tienda online ficticia basada en WordPress, diseñada para alta disponibilidad y escalabilidad horizontal.

**Documentación completa:** [documentation/UrbanStyle-AWS-Documentacion.md](documentation/UrbanStyle-AWS-Documentacion.md)

## Highlights

- VPC multi-AZ con segmentación de red y Security Groups por capas
- Application Load Balancer + Target Group con instancias `Healthy`
- Auto Scaling (min 2 / max 4) con Launch Template y política por CPU
- Amazon RDS MySQL como capa de datos gestionada
- Documentación clara de lo **implementado en laboratorio** frente al **diseño objetivo**

## Stack

Amazon VPC · EC2 · Auto Scaling · ALB · Target Groups · RDS MySQL · Security Groups · WordPress

## Arquitectura (vista rápida)

![Diagrama de arquitectura AWS](diagrams/aws-architecture-diagram.png)

## Estructura del repositorio

```text
README.md
diagrams/          Diagramas lógico y de arquitectura
documentation/     Documentación técnica completa + PDF de diseño
screenshots/       Evidencias del despliegue en AWS
```

## Lectura recomendada

1. [Documentación completa](documentation/UrbanStyle-AWS-Documentacion.md)
2. Diagrama lógico y de arquitectura en `diagrams/`
3. Evidencias en `screenshots/`

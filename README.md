# Trabajo práctico anual Diseño de Sistemas

Este repositorio corresponde al **Trabajo Práctico Anual (TPA)** de la materia **Diseño de Sistemas**.  
El proyecto consiste en un **Sistema para la Mejora del Acceso Alimentario en Contextos de Vulnerabilidad Socioeconómica**, desarrollado en **Java** utilizando **Javalin** como framework web, **Mustache** para el renderizado de vistas y **MySQL** como motor de base de datos. Además, el sistema cuenta con **observabilidad** de métricas mediante la integración con **Prometheus** y **Grafana**.

## Equipo de trabajo

| Nombre | Contacto |
|--------|---------------------------|
| Franco Callero | fcallero@frba.utn.edu.ar |
| Felipe Alborch De Guzman | falborchdeguzman@frba.utn.edu.ar |
| Mora Hidalgo | mohidalgo@frba.utn.edu.ar |
| Tomás Francou | tfernndezfrancou@frba.utn.edu.ar |
| Tomás Watson | twatson@frba.utn.edu.ar |

## Video demostrativo
[Ver video explicativo y demo del sistema](https://drive.google.com/file/d/1yfd7Edm6xTKeaUdNtwGrxW7-nEMhjcqs/view?usp=sharing)

## 📂 Documentación

En la carpeta **`Documentacion/`** se encuentran los documentos generados durante el desarrollo del TP, incluyendo:
- Diagrama de casos de uso
- Diagrama de clase
- Diagramas de secuencia
- Diagramas de componentes y despliegue
- Diagrama de entidad Relacion (DER)
- Especificación de la api del servicio de atención médica
- Justificaciones de diseño
- Enunciado del TP con los requerimientos del sistema

## Observabilidad 

### Puertos
- prometeus: puerto 7080
- grafana: puerto 3000
- prometeus query explorer: puerto 9090 

### Iniciar Prometheus
1. Descargar Prometeus
2. configurar el archivo "prometheus.yml" con
```yml
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
scrape_configs:
  - job_name: "javalin"
    scrape_interval: 1s

    static_configs:
      - targets: ["localhost:7080"]
        labels:
            group: 'app'
`````
3. ejecutar prometheus por terminal con: " .\prometheus.exe --config.file=prometheus.yml"

``Nota: antes descargar prometheus e iniciar el TP``

### Usar grafana
1. ir a http://localhost:3000
2. Iniciar seccion username: "admin"  pass:"admin" (despues te pide crear una cuenta)
2. Connections > Data sources
3. click en Add data source
4. en Connection pones la url "http://localhost:9090"
5. click en save and test
6. Luego ir a Explore y usar

``Nota: antes descargar grafana e iniciar Prometheus``
### Metricas
- <b>http_server_requests_seconds_count</b> : cantidad de requests a ese endpoint
- <b>http_server_requests_seconds_sum</b> : suma de segundos en ejecutar todos los request a ese endpoint
- <b>http_server_requests_seconds_max</b> : duración en segundos, que tardo en ejecutar el request que mas tardó en ese endpoint

## Licencia
Este proyecto fue desarollado con fines académicos en el marco de la materia Diseño de Sistemas (dentro de la carrea de ingeniería en sistemas de información).

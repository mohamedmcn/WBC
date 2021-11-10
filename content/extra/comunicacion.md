---
title: "comunicación cliente/Servidor"
date: 2021-09-29T16:24:25+02:00
draft: false
---
{{< mermaid >}}
sequenceDiagram
    participant Cliente
    participant Servidor web
    participant Servidor dns
    participant Servidor dns
    Note left of Cliente: introduce una</br> URL en el navegador
     Cliente->>Servidor dns: Consulta dns
     loop Hasta que encuentre la ip
        Servidor dns->Servidor dns: Pregunta al siguiente en la jerarquia
        end
    Servidor dns->> Servidor dns: guardan la informacion
    Note right of Servidor dns: los dns por los </br>que pasa la peticion
     Servidor dns->>Cliente: Respuesta dns
     Cliente->>Servidor web: peticion web(request)
    Servidor web->>Servidor web: procesa la petición
    Servidor web->>Servidor web: inserta la informacion(solicitada) 
    Servidor web->>Cliente:informacion solicitada

{{< /mermaid >}}

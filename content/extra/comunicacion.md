---
title: "comunicación cliente/Servidor"
date: 2021-09-29T16:24:25+02:00
draft: false
---
{{< mermaid >}}
sequenceDiagram
    participant Cliente
    participant Servidor dns
    participant Servidor 
    Note left of Cliente: introduce una</br> URL en el navegador
     Cliente->>Servidor dns: Consulta dns
     loop Hasta que encuentre la ip
        Servidor dns->Servidor dns: Pregunta al siguiente en la jerarquía
        end
    Servidor dns->> Servidor dns: guardan la información
    Note right of Servidor dns: los dns por los </br>que pasa la petición
     Servidor dns->>Cliente: Respuesta dns
     Cliente->>Servidor : peticion web(request)
    Servidor ->>Servidor : procesa la petición
    Note  right of Servidor : leer abajo para </br> más información
    Servidor ->>Servidor : inserta la información(solicitada) 
    Servidor ->>Cliente:información solicitada

{{< /mermaid >}}

#### Métodos de peticion HTTP
Cuando nos comunicamos con el servidor debemos indicarle la acción que queremos realizar para un recurso en concreto, para ello usamos los HTTP verbs.   Estos son algunos de los metodos usados:

**GET:** este método permite el envío de datos añadiendo los datos codificados a la URI.

**PUT:** con put remplazamos todas las representaciones actuales del recurso, dicho de otro modo, se crea un nuevo elemento o se reemplaza.

**HEAD:** es similar al método get solo que no nos devuelve el cuerpo solo la cabecera.

**POST:** a diferencia del método get post añade la información al cuerpo pero cumple la misma función.

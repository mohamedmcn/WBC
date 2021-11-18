---
title: "comunicación cliente/Servidor web"
date: 2021-09-29T16:24:25+02:00
draft: false
---
{{< mermaid >}}
sequenceDiagram
    participant Cliente
    participant Servidor  dns
    participant Servidor web  
    Note left of Cliente: introduce una</br> URL en el navegador
     Cliente->>Servidor  dns: Consulta dns
     loop Hasta que encuentre la ip
        Servidor  dns->Servidor  dns: Pregunta al siguiente en la jerarquía
        end
    Servidor  dns->> Servidor  dns: guardan la información
    Note right of Servidor  dns: los dns por los </br>que pasa la petición
     Servidor  dns->>Cliente: Respuesta dns
     Cliente->>Servidor web : peticion web(request)
    Servidor web ->>Servidor web : procesa la petición
    Note  right of Servidor web : leer abajo para </br> más información
    Servidor web ->>Servidor web : inserta la información(solicitada) 
    Servidor web ->>Cliente:información solicitada

{{< /mermaid >}}

#### Métodos de peticion HTTP
Cuando nos comunicamos con el servidor web debemos indicarle la acción que queremos realizar para un recurso en concreto, para ello usamos los HTTP verbs.   Estos son algunos de los metodos usados:

**GET:** este método permite el envío de datos añadiendo los datos codificados a la URI.

**PUT:** con put remplazamos todas las representaciones actuales del recurso, dicho de otro modo, se crea un nuevo elemento o se reemplaza.

**HEAD:** es similar al método get solo que no nos devuelve el cuerpo solo la cabecera.

**POST:** a diferencia del método get post añade la información al cuerpo pero cumple la misma función.

#### Funcionamiento servidor web
En el proceso de comunicacion cliente servidor  no se trata de una simple extraccion de un archivo, en muchos otro casos el servidor web debe "ejecutar un codigo".

**-Ejemplo:** 

Si un cliente solicitara un archivo con la extension php, el servidor web solicitaria la intervencion del interprete PHP que estaría funcionando en el servidor web.
El interprete leería el archivo que ha solicitado el cliente y procesaría el código, se suele dar el caso de que el interprete se comunique con un gestor de bases de datos para solicitar cierta información. Cuando el interprete termina de ejecutar el codigo envía el resultado al servidor web web y este a la vez se lo envia al cliente que mediante el navegador muestra la información. 

#### renderizado

Cuando cargamos una pagina web solicitamos al servidor un archivo determinado,por ejemplo podríamos solicitar index.php y cuando el servidor nos devuelva el resultado, también se podría dar el caso de que se tuviese que solicitar el css. ya con lo necesario el motor de renderizado analiza los documentos crea el árbol de renderizacion y nos muestra la información.
**Flujo basico de un motor de renderizado**

{{<mermaid align="left">}}
graph LR;
    A[Analiza el HTML para</br> construir el árbol dom] -->     B[renderizado </br> del arbol]--> 
    C[diseño del arbol</br> de renderizado]-->D[dibuja </br> el arbol]
{{< /mermaid >}}

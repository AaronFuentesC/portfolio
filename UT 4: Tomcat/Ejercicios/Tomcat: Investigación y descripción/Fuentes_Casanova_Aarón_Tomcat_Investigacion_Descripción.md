# Componentes principales de Apache Tomcat

## Introducción

**Apache Tomcat** es un servidor web y contenedor de servlets de código abierto que permite ejecutar aplicaciones web desarrolladas en Java. Se encarga de recibir peticiones HTTP, procesarlas y devolver las respuestas correspondientes al navegador.

## 1. Catalina

Catalina es el contenedor de servlets de Tomcat y constituye uno de sus componentes principales.

-   Se encarga de gestionar la ejecución de servlets y aplicaciones web Java.
-   Administra los diferentes contenedores internos de Tomcat.
-   Controla el ciclo de vida de las aplicaciones, desde su inicio hasta su finalización.
-   Gestiona las peticiones que llegan a las aplicaciones web.
-   Su implementación se encuentra principalmente en las clases Java del paquete `org.apache.catalina`, dentro del código de Tomcat.

## 2. Coyote

Coyote es el componente encargado de gestionar las conexiones y los protocolos de comunicación de Tomcat.

-   Actúa como conector entre los clientes (navegadores) y el servidor.
-   Recibe las peticiones HTTP y HTTPS.
-   Interpreta las peticiones y las transforma en solicitudes que Catalina pueda procesar.
-   Se encarga de enviar las respuestas HTTP de vuelta al cliente.
-   Su implementación se encuentra en el código de Tomcat, principalmente en el paquete `org.apache.coyote`.

## 3. Jasper

Jasper es el motor de Tomcat encargado de procesar las páginas JSP (JavaServer Pages).

-   Transforma las páginas JSP en código fuente Java.
-   Compila ese código Java para convertirlo en servlets.
-   Permite ejecutar páginas dinámicas cuyo contenido puede cambiar dependiendo de la petición.
-   Gestiona la compilación de las páginas JSP cuando es necesario.
-   Su implementación se encuentra principalmente en el paquete `org.apache.jasper`, dentro del código de Tomcat.

## 4. Manager y Host Manager

Son dos aplicaciones web que incorpora Tomcat para facilitar la administración del servidor.

### Manager

-   Permite administrar las aplicaciones web que están instaladas en Tomcat.
-   Permite desplegar nuevas aplicaciones mediante archivos `.war`.
-   Permite iniciar, detener, reiniciar y eliminar aplicaciones.
-   También permite consultar información sobre las aplicaciones desplegadas y sus sesiones.
-   Se encuentra normalmente en el directorio `webapps/manager` y se accede mediante `http://localhost:8080/manager`.

### Host Manager

-   Permite administrar los hosts virtuales de Tomcat.
-   Permite crear, eliminar, iniciar y detener hosts virtuales.
-   Facilita la gestión de diferentes sitios web dentro de una misma instalación de Tomcat.
-   Su configuración se relaciona con el archivo `server.xml`.
-   Se encuentra normalmente en el directorio `webapps/host-manager` y se accede mediante `http://localhost:8080/host-manager`.

## 5. Estructura básica de directorios

Tomcat organiza sus archivos en diferentes directorios, cada uno con una función específica. En una instalación estándar, destacan los siguientes:

| Directorio | Función |
|---|---|
| `bin/` | Contiene los ejecutables y scripts necesarios para iniciar, detener y administrar Tomcat. En Linux incluye scripts como `startup.sh` y `shutdown.sh`. |
| `conf/` | Almacena los archivos de configuración del servidor. Destaca `server.xml`, donde se configuran los puertos, conectores y hosts virtuales. |
| `webapps/` | Contiene las aplicaciones web que Tomcat puede desplegar y ejecutar. Aquí se encuentran archivos `.war` y carpetas de aplicaciones. |
| `lib/` | Contiene las bibliotecas Java (`.jar`) necesarias para el funcionamiento de Tomcat y sus componentes. |
| `logs/` | Almacena los registros del servidor, incluyendo información sobre su funcionamiento y posibles errores. |
| `work/` | Almacena archivos temporales generados durante la ejecución de las aplicaciones, como archivos compilados de JSP. |
| `temp/` | Contiene archivos temporales utilizados por Tomcat durante su funcionamiento. |

Estas carpetas forman parte de la estructura lógica de Tomcat, pero no tienen por qué encontrarse todas juntas. En instalaciones realizadas mediante los repositorios de Ubuntu, los archivos se distribuyen en diferentes ubicaciones del sistema.

Por último, es importante distinguir entre las variables `CATALINA_HOME` y `CATALINA_BASE`: la primera hace referencia al directorio de instalación de Tomcat, mientras que la segunda identifica el directorio de configuración y datos de una instancia concreta.

## 6. Flujo interno de funcionamiento

El funcionamiento interno de Tomcat sigue una serie de pasos desde que
un usuario accede a una aplicación web hasta que recibe una respuesta.

1.  **Recepción de peticiones:** el navegador envía una petición HTTP o
    HTTPS al servidor Tomcat, normalmente a través del puerto 8080.
2.  **Procesamiento con Coyote:** el conector recibe la petición,
    interpreta el protocolo y la prepara para que pueda ser procesada.
3.  **Entrada en Catalina:** la petición llega al motor de contenedores,
    que se encarga de gestionar su procesamiento.
4.  **Distribución entre contenedores:** Catalina organiza el
    procesamiento mediante diferentes niveles:
    -   **Engine:** representa el motor que procesa las peticiones.
    -   **Host:** identifica el servidor virtual al que va dirigida la
        petición.
    -   **Context:** representa una aplicación web concreta.
    -   **Wrapper:** representa un servlet individual dentro de esa
        aplicación.
5.  **Ejecución de la aplicación:** el servlet correspondiente procesa
    la petición. Si se solicita una página JSP, Jasper se encarga de
    traducirla a código Java y compilarla como servlet cuando sea
    necesario.
6.  **Envío de la respuesta:** una vez procesada la petición, Tomcat
    devuelve la respuesta al navegador mediante Coyote.

### Despliegue de aplicaciones

El despliegue es el proceso mediante el cual Tomcat instala y pone en funcionamiento una aplicación web.

-   Se copia un archivo `.war` o una carpeta de aplicación dentro de `webapps` (si se utiliza el despliegue automático).
-   Tomcat detecta la aplicación y la despliega.
-   Si se trata de un archivo `.war`, Tomcat puede descomprimirlo en una carpeta.
-   Catalina crea y configura el contenedor `Context` correspondiente.
-   Una vez desplegada, la aplicación queda disponible para recibir peticiones HTTP.

## 7. Bibliografía y fuentes de información

-   [Apache Tomcat -- Introduction](https://tomcat.apache.org/tomcat-10.1-doc/introduction.html).
    Explica los componentes y la estructura de directorios.
-   [Apache Tomcat -- Architecture](https://tomcat.apache.org/tomcat-10.1-doc/architecture/overview.html).
    Describe la arquitectura interna del servidor.
-   [Apache Tomcat -- Manager App](https://tomcat.apache.org/tomcat-10.1-doc/manager-howto.html).
    Explica las funciones de Manager.
-   [Apache Tomcat -- Host Manager](https://tomcat.apache.org/tomcat-10.1-doc/host-manager-howto.html).
    Explica la administración de hosts virtuales.
-   [Apache Tomcat -- Configuration Reference](https://tomcat.apache.org/tomcat-10.1-doc/config/).
    Documentación de configuración del servidor.


## GlassFish
Es un **Servidor de Aplicaciones** para Jave EE / Jakarta EE. Un servidor web básico (como Nginx o Apache HTTP) solo entrega archivos estáticos como imágenes o HTML estáticos. En cambio, un servidor de aplicaciones como GlassFish incluye un entorno completo capaz de:
- **Ejecutar código Java en el servidor** en respuesta a peticiones HTTP del usuario.
- **Transformar y compilar automáticamente** páginas JSP en código ejecutable Java (Servlets).
- **Gestionar el ciclo de vida** de los servlets, sesiones de usuario y seguridad.
- **Manejar conexiones a bases de datos** (como Java DB/Derby) mediante _pools_ de conexiones.
### Ciclo de vida de una JSP
Cuando el usuario entra a `http://localhost:8080/TuProyecto/index.jsp`:
1. **Petición HTTP:** El navegador solicita la página a GlassFish.
2. **Traducción:** Si es la primera vez que se pide o si ha cambiado, GlassFish **traduce el archivo `.jsp` a un archivo `.java`** (un Servlet).
3. **Compilación:** GlassFish compila ese Servlet Java a bytecode (`.class`).
4. **Ejecución:** Se ejecuta el Servlet, resolviendo todo el código Java encerrado en `<% ... %>`.
5. **Respuesta HTML:** El Servlet imprime código **HTML puro** y se lo envía al navegador.

### Servlet
- Clase Java que corre en el servidor web (GlassFish)
- Su único trabajo es recibir peticiones de un navegador web (HTTP) y devolver una respuesta.
- Cliente-servidor:
	- El navegador es el cliente: hace una petición HTTP
	- El servlet es el servidor: recibe la peticion y responde el código HTML respuesta
- Flujo:
	1. index.jsp: Archivo donde hay HTML + etiquetas (`<% ... %>`)
	2. index_jsp.java: Codigo fuente servlet. GlassFish traduce la plantilla .jsp a una clase de Java estándar
	3. index_jsp.class: Bytecode ejecutable. GlassFish invoca al compilador de Java para convertir index_jsp.java en un archivo .class
	4. Ejecución: GlassFish carga index_jsp.class en memoria, ejecuta las instrucciones y le manda la respuesta HTML al navegador del usuario
- En la misma carpeta de Servlet en SOurce Packages puedes tener 
### Crear uno a mano
 - Ir a la pestaña `Projects`
- Click derecho encima de `Source Packages`
- `New`> `Servlet`
	- Class Name: `testServlet`
	- Package: `servlet`
- En el fichero generado (e.g. `testServlet.java`) la anotación `@WebServlet(urlPatterns = {"/testServlet"})`sirve para que GrlassFish sepa que URL les corresponde
## BBDD
### Creación
 - Ir a la pestaña `Services`
 - Click izquierdo encima de `Databases`
 - Click derecho encima de `Java DB`
 - `Create Database`> `Name` + `User` + `Password`
### Conexión y uso
- Click izquiero sobre (e.g.) jdbc:derby://localhost:1527/pr2 \[pr2 on PR2] y `Connect`
- El icono de enchue pasará a estar conectado
- Desplegar la conexión para ver la BBDD PR2
	- Si ahora desplegamos PR2, veremos sus `Tables`. `Views`, etc
### Ejecución
- Click derecho encima de `Tables`
- `Execute command` > Se abre una pestaña para ejecutar SQL > Escribimos lo que sea
- Finalmente, `Run SQL` (desde el botón de al lado de la conexión o con CTRL + SHIFT + E)
- En la pestaña `Output` vemos que las sentencias se han creado correctamente y en el apartado `Tables` de PR2 aparecen las tablas creadas
## Conectar Servlet con Java DB
- Disponible en el código del servlet (`testServlet.java`)
- No olvidar que, para comprovar que funciona, se tiene que acceder a `http://localhost:8080/L1/testServlet`
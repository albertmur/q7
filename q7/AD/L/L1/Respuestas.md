## Creación
### a)
El navegador se conecta correctamente a http://localhost:8080/L1/
### b)
El navegador (cliente) solo ha recibido el código HTML estático. El flujo ha sido:
- GlassFhish coge el archivo index.jsp y genera un archivo Java de verdad (un servlet)
- Lo que esta fuera de `<% %>` GlassFish asume que es texto HTML estático y lo envuelve en instrucciones Java como:
```java
out.write("<html><head>...</head><body><h1>Hello World!</h1></body></html>");
```
- Lo que está dentro de `<% %>` GlassFhish no lo añade ningún `out.write()` y lo copia tal cual dentro del método principal del servlet
- Compila ese archivo Java a un archivo ejecutable  .class (que es el servlet) y lo ejecuta.

## Modificación del codigo
### a)
Se ha añadido un subapartado
### b)
Probadas distintas cosas
### c)
Para ver el servlet:
- Ir a la pestaña `Projects`
- Click derecho encima de `index.jsp` > `View Servlet`

Las instrucciones en lenguaje Java que muestran el código html no generado con `out.println()` en la página jsp son `out.write()`

## Crear servlet
- Ir a la pestaña `Projects`
- En `Source Packages` > Click derecho
- `New` > `Servlet`
	- Class name: lo que queramos
	- package: nombre que queramos
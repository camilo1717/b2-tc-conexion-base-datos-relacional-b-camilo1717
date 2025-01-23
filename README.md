# Trabajo Consulta: Conexión Base de Datos Relacional
# Indicaciones
Genere un repositorio en github y documente los siguientes puntos en la wiki o archivo README:

# ¿Qué es JDBC y cuáles son sus componentes?

Java Database Connectivity (JDBC) es una API (Interfaz de Programación de Aplicaciones) de Java que permite a las aplicaciones Java conectarse y ejecutar operaciones en bases de datos. JDBC proporciona un conjunto de interfaces y clases que permiten a los desarrolladores interactuar con diversas bases de datos de manera uniforme y sencilla.
# Documente 2 librerías de Scala que permitan conectarse a una base de datos relacional. En una tabla resuma sus diferencias.

Slick
Es una librería de mapeo funcional relacional (FRM) para Scala que permite escribir consultas SQL de manera funcional y segura en tiempo de compilación

Doobie
Es una librería de mapeo funcional reactivo (FRP) para Scala que utiliza IO de Cats Effect para manejar operaciones asincrónicas

| Caracteristica | Slick | Doobie |
|--------------|--------------|--------------|
| # Tipo de Mapeo| Mapeo Funcional Relacional (FRM)	|Mapeo Funcional Reactivo (FRP)|
| Fila 2, Col 1| Fila 2, Col 2| |
| Fila 3, Col 1| Fila 3, Col 2| Fila 3, Col 3|

# Documentar cómo establecer una conexión a una base de datos relacional (mysql). Siga los siguientes pasos:
# Genere una base de datos en mysql
# Genere una tabla con datos de prueba
# Desde Scala establezca la conexión a la base datos
# (opcional) Desde Scala realice la consulta de todos los datos de la tabla de prueba. 

El tercer punto lo documenta adjuntando capturas de pantalla. Adjuntar referencias.

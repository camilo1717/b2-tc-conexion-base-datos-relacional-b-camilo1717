# Trabajo Consulta: Conexión Base de Datos Relacional
# Indicaciones
Genere un repositorio en github y documente los siguientes puntos en la wiki o archivo README:

# ¿Qué es JDBC y cuáles son sus componentes?

Java Database Connectivity (JDBC) es una API (Interfaz de Programación de Aplicaciones) de Java que permite a las aplicaciones Java conectarse y ejecutar operaciones en bases de datos. JDBC proporciona un conjunto de interfaces y clases que permiten a los desarrolladores interactuar con diversas bases de datos de manera uniforme y sencilla.
# Documente 2 librerías de Scala que permitan conectarse a una base de datos relacional. En una tabla resuma sus diferencias.

Slick:

Es una librería de mapeo funcional relacional (FRM) para Scala que permite escribir consultas SQL de manera funcional y segura en tiempo de compilación

Doobie:

Es una librería de mapeo funcional reactivo (FRP) para Scala que utiliza IO de Cats Effect para manejar operaciones asincrónicas

| Caracteristica | Slick | Doobie |
|--------------|--------------|--------------|
|Tipo de Mapeo| Mapeo Funcional Relacional (FRM)	|Mapeo Funcional Reactivo (FRP)|
| Seguridad en tiempo de compilacion| Si (El compilador verifica las consultas)|Si (El compilador verifica las consultas) |
| Composabilidad|Alta - Permite componer consultas como colecciones de Scala|Media - Permite componer consultas, pero con un enfoque más reactivo|
| API Asincrónica | Si - utiliza "Future" y sigue la interfaz Reactive Streams| Si - Utiliza IO de Cats Effect y sigue la interfaz Reactive Streams|
| Soporte de SQL | Si - Permite escribir consultas en SQL directamente | Si - Permite escribir consultas en SQL directamente |

# Documentar cómo establecer una conexión a una base de datos relacional (mysql). Siga los siguientes pasos:
- Genere una base de datos en mysql
  
Primero creé una base de datos en MySQL Workbench
```sql
CREATE DATABASE PFyR;
USE PFyR;
```
- Genere una tabla con datos de prueba

Luego generé los datos de la tabla

```sql
CREATE TABLE equipos_futbol_ecuador (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    ciudad VARCHAR(50) NOT NULL,
    fundacion DATE,
    titulos_nacionales INT
);

INSERT INTO equipos_futbol_ecuador (nombre, ciudad, fundacion, titulos_nacionales) VALUES 
('Barcelona Sporting Club', 'Guayaquil', '1925-05-01', 16);

INSERT INTO equipos_futbol_ecuador (nombre, ciudad, fundacion, titulos_nacionales) VALUES 
('Club Sport Emelec', 'Guayaquil', '1929-04-28', 14);

INSERT INTO equipos_futbol_ecuador (nombre, ciudad, fundacion, titulos_nacionales) VALUES 
('Liga Deportiva Universitaria de Quito', 'Quito', '1930-01-11', 11);

INSERT INTO equipos_futbol_ecuador (nombre, ciudad, fundacion, titulos_nacionales) VALUES 
('Club Deportivo El Nacional', 'Quito', '1964-03-01', 13);

INSERT INTO equipos_futbol_ecuador (nombre, ciudad, fundacion, titulos_nacionales) VALUES
('Libertad Futbol Club', 'Loja', '2017-05-17', 0);
```
- Desde Scala establezca la conexión a la base datos

1. **Dependencia y Configuración de la conexión:**
   
   Agrego la depencia en Scala que permite interactuar con MySQL

![image](https://github.com/user-attachments/assets/4e7e3347-fd97-4653-96a7-a3753ab47022)

   - Luego agrego la ruta de acceso:
     
   - `url`: Ruta de acceso a la base de datos, que incluye el nombre de la base (`PFyR`) y `useSSL=false` para deshabilitar el uso de SSL.
   - `usuario` y `contraseña`: Credenciales para acceder al servidor MySQL.
     
![image](https://github.com/user-attachments/assets/115b2ab1-4fff-4426-96db-a9d6ddfd9e4b)

3. **Registrar el driver JDBC:**
   Se utiliza `Class.forName("com.mysql.cj.jdbc.Driver")` para cargar el driver necesario.

4. **Establecer conexión:**
   - Se utiliza `DriverManager.getConnection` con los parámetros definidos.

5. **Ejecutar una consulta:**
   - Se crea un `Statement` con `conexion.createStatement()`.
   - La consulta `SELECT * FROM equipos_futbol_ecuador` se ejecuta y el resultado se almacena en `resultSet`.

6. **Procesamiento resultados:**
   - Se recorren las filas de `resultSet` para construir objetos `Equipo`.

7. **Libero recursos:**
   - Se cierran los recursos en el bloque `finally` para evitar fugas de memoria.


- (opcional) Desde Scala realice la consulta de todos los datos de la tabla de prueba. 

El tercer punto lo documenta adjuntando capturas de pantalla. Adjuntar referencias.

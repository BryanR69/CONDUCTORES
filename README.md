# CONDUCTORES

`demo_jdbc` es una aplicación Java que utiliza JDBC para interactuar con una base de datos y proporciona estadísticas de la Fórmula 1 a través de una interfaz gráfica de usuario (GUI).

### Descripción de los Archivos

- **Main.java**: Punto de entrada de la aplicación. Maneja la lógica principal para recuperar y mostrar datos de estadísticas de la Fórmula 1.
- **demo_jdbc.models**: Contiene las clases de modelo para `Circuit`, `DriverResult` y `Season`.
- **demo_jdbc.repositories**: Contiene las clases de repositorio que manejan las operaciones de base de datos para los diferentes modelos.

## Instalación y Ejecución

### Prerrequisitos

- Java Development Kit (JDK) 17 o superior.
- Apache Maven.

### Instrucciones de Instalación

1. Compila el proyecto utilizando Maven:
    ```sh
    mvn clean install
    ```

### Ejecución de la Aplicación

1. Ejecuta la aplicación desde la línea de comandos o desde tu IDE preferido:
    ```sh
    mvn exec:java -Dexec.mainClass="demo_jdbc.Main"
    ```

2. La aplicación mostrará una interfaz gráfica donde podrás seleccionar el año y ver las estadísticas de la Fórmula 1.

### Ejemplo de Ejecución

A continuación, se muestra una captura de pantalla de la aplicación en ejecución:

![Formula 1 Statistics]( https://github.com/BryanR69/CONDUCTORES/blob/main/Captura%20de%20pantalla%202024-07-08%20235515.png)

![Formula 1 Statistics]( https://github.com/BryanR69/CONDUCTORES/blob/main/Captura%20de%20pantalla%202024-07-08%20143614.png)

## Descripción de la Funcionalidad

### Interfaz Gráfica

La aplicación proporciona una interfaz gráfica para visualizar estadísticas de la Fórmula 1. Los usuarios pueden seleccionar el año deseado y la aplicación mostrará una tabla con los siguientes datos:

- **Nombre del Piloto**
- **Victorias**
- **Puntos Totales**
- **Rango**

### Flujo de Trabajo del Código

1. **DriverResultRepository**:
    - Recupera los resultados de los pilotos para un año específico.
    - Ejemplo: `driverResultRepository.getResultByYear(2000)`

2. **CircuitRepository**:
    - Recupera la lista de circuitos.
    - Ejemplo: `circuitRepository.getCircuits()`

3. **Main.java**:
    - Crea instancias de los repositorios y maneja la lógica para recuperar y mostrar los datos en la GUI.

### Ejemplo de Código

```java
public class Main {
    public static void main(String[] args) {
        DriverResultRepository driverResultRepository = new DriverResultRepository();
        var results = driverResultRepository.getResultByYear(2000);
        
        for (DriverResult rs : results) {
            System.out.println(rs.getDriverName() + "\t" + rs.getWins() + "\t" + rs.getTotalPoints());
        }
        
        CircuitRepository circuitRepository = new CircuitRepository();
        var circuits = circuitRepository.getCircuits();
        
        System.out.println("Total circuits: " + circuits.size());
        
        String country = "Russia";
        var circuitsByCountry = circuitRepository.getCircuitsByCountry(country);
    }
}

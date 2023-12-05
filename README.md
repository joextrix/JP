# JP
Ejercicio de Automatización E2E
********************************

Proyecto_1JP

Usamos como interprete Intellij
 versión 2.0.84 de Serenity BDD

build: System : Maven
Maven Type Archetype 
src
*main
*test
mpom.xml  Este sera nuestro archivo en donde se configurara las dependencias y configuraciones del proyecto Maven 

Estructura Básica del Proyecto
Directorio Principal (src/main y src/test):

src/main/java: Contiene el código fuente principal de la aplicación.
src/test/java: Contiene los archivos de prueba.
Paquetes en src/main/java:

com.ejercicio.pages: Contiene las clases Page Objects.
com.ejercicio.util: Puedes tener clases de utilidad aquí si es necesario.
Otros paquetes según la arquitectura y la lógica de tu aplicación.
Paquetes en src/test/java:

com.ejercicio.features: Contiene archivos .feature que definen los escenarios de prueba.
com.ejercicio.steps: Contiene clases con los pasos de Cucumber.
com.ejercicio.runners: Contiene clases de ejecución de pruebas (runners).
Directorio de Recursos (src/test/resources):

com.ejercicio.features: Contiene archivos .feature (pueden ir aquí en lugar de src/test/java).
com.ejercicio.conf: Puedes tener archivos de configuración aquí (por ejemplo, serenity.conf).
Otros recursos según las necesidades del proyecto.

CLASE MAIN
ES MI PUNTO DE PARTIDA Y CUMPLE CON SU PROPOSITO DE SER EL PUNTO DE ENTRADA DEL PROGRAMA EN ESTE CASO SIMPLEMENTE IMPRIME UN MENSAJE EN LA CONSOLA 

********************************************************************************************************************************************************
package com.ejemplo;

public class Main {
    public static void main(String[] args) {
        System.out.println("Hola, este es el punto de entrada principal.");
    }
}

package com.ejemplo;: Indica que la clase Main pertenece al paquete com.ejemplo. Esto es importante para organizar y estructurar tu código.

public class Main { ... }: Define la clase Main. La palabra clave public significa que la clase es accesible desde cualquier otro paquete.

public static void main(String[] args) { ... }: Este es el método principal (main) que se ejecutará cuando inicies tu programa. Es el punto de entrada para la ejecución.

System.out.println("Hola, este es el punto de entrada principal.");: Imprime el mensaje "Hola, este es el punto de entrada principal." en la consola. Este es un ejemplo simple para demostrar el funcionamiento del programa.



COMPRA TEST 
ES MI ARCHIVO DE PRUEBA QUE UTILIZA EL FRAMEWORK SERENITY BDD PARA REALIZAR UNA PRUEBA DE AUTOMATIZACION
*************************************************************************************************************************************

package com.ejemplo;

import com.ejemplo.steps.FlujoCompraSteps;
import net.serenitybdd.junit.runners.SerenityRunner;
import net.thucydides.core.annotations.Steps;
import org.junit.Test;
import org.junit.runner.RunWith;

@RunWith(SerenityRunner.class)
public class CompraTest {

    @Steps
    private FlujoCompraSteps flujoCompraSteps;

    @Test
    public void realizarCompraTest() {
        flujoCompraSteps.realizarFlujoCompra(
                new String[]{"Producto1", "Producto2"},
                "usuario@ejemplo.com",
                "Nombre",
                "Apellido",
                "Calle 123",
                "Ciudad",
                "12345",
                "País",
                "123456789",
                "Your order has been placed!"
        );
    }
}

@RunWith(SerenityRunner.class): Esta anotación indica que estás utilizando el corredor de Serenity para ejecutar las pruebas.

@Steps: Esta anotación se utiliza para inyectar instancias de las clases de pasos (en este caso, FlujoCompraSteps). La clase CompraTest utiliza métodos de FlujoCompraSteps para realizar acciones en tu prueba.

private FlujoCompraSteps flujoCompraSteps;: Aquí se declara una instancia de FlujoCompraSteps. Serenity se encargará de inicializar esta instancia automáticamente.

@Test: Esta anotación indica que el método realizarCompraTest() es un método de prueba JUnit.

public void realizarCompraTest() { ... }: Este método contiene la lógica de tu prueba. En este caso, parece que estás utilizando el método realizarFlujoCompra de FlujoCompraSteps para simular un flujo de compra.

Argumentos del Método realizarFlujoCompra: Estás proporcionando varios argumentos al método para simular la realización de un flujo de compra. Estos podrían incluir productos, información de usuario, dirección, etc.


ARCHIVO POM.XML

MI ARCHIVO PRINCIPAL 

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.ejemplo</groupId>
    <artifactId>automatizacion-opencart</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <!-- Dependencias de Serenity BDD y Selenium -->
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-core</artifactId>
            <version>2.0.84</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-junit</artifactId>
            <version>2.0.84</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>net.serenity-bdd</groupId>
            <artifactId>serenity-screenplay</artifactId>
            <version>2.0.84</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>




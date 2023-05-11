# Excepciones 

Existen varios tipos fundamentales de excepciones:

* Error: Excepciones que indican problemas muy graves, que suelen ser no recuperables y no deben casi nunca ser capturadas.
* Exception: Excepciones no definitivas, pero que se detectan fuera del tiempo de ejecución.
* RuntimeException: Excepciones que se dan durante la ejecución del programa.

Todas las excepciones tienen como clase base la clase Throwable, que está incluida en el paquete java.lang

* Excepciones Checked: Objetos de la clase Exception o cualquier otra clase que hereda de ella, excepto si heredan de RuntimeException.
* Excepciones Unchecked: Objetos de la clase RuntimeException o de cualquiera otra clase que herede de ella.

Para que el sistema de gestión de excepciones funcione, se ha de trabajar en dos partes de los programas:

* Definir qué partes de los programas crean una excepción y bajo qué condiciones. Para ello se utilizan las palabras reservadas throw y throws.
* Comprobar en ciertas partes de los programas si una excepción se ha producido, y actuar en consecuencia. Para ello se utilizan las palabras reservadas try, catch y finally.


Cuando el programador va a ejecutar un trozo de código que pueda provocar una excepción (por ejemplo, una lectura en un fichero), debe incluir este fragmento de código dentro de un bloque try:

```java
try {

// Código posiblemente problemático

}
```

## Ejemplos 

```java
class TempException extends Exception {

}

public class Test {


    public void test() throws RuntimeException {
        throw new RuntimeException();
    }

    public void test2() throws TempException {
        throw new TempException();
    }

    public static void main(String[] args) throws Exception {


        try {

            int a = 5 / 0;
        } catch (ArithmeticException e) {
            System.out.println("ArithmeticException");
            try {
                throw new RuntimeException();
            } catch (RuntimeException runtimeException) {
                System.out.println("RuntimeException");
            }
        } catch (RuntimeException runtimeException) {
            System.out.println("RuntimeException");
        } catch (Exception exception) {
            System.out.println("Exception");
        } finally {
            System.out.println("finally");
            throw new Exception("finally");
        }


    }


}

```


### try-with-resources
```java
try (Connection conector = ...) //iniciar la conexion a bd
{
    //operaciones con la conexion a bd
    try (PreparedStatement pstmt = conector.prepareStatement("SELECT ... ")) {
        pstmt.setParameter(1, ...);
        try (ResultSet rs = pstmt.executeQuery()) {
            //...
        }
    }
} catch (SQLException e) {
    //siempre se deben manejar las excepciones
    //por lo menos registra la excepción en la salida del programa
    System.out.println("Error en las operaciones a base de datos.");
    e.printStackTrace(System.out);
    //si te lo preguntas, sí, existen mejores opciones
    //pero esta es la más básica para tus primeros pasos
}

```
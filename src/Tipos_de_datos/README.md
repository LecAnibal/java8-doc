# Tipos de datos

En Java existen ocho tipos de datos, también conocidos como tipos primitivos : byte, short, int, long, char, float, double y boolean. A partir de estos tipos de datos nosotros podemos clasificarlos en cuatro grupos:

## Enteros
Este grupo incluye byte, short, int y long. Estos tipos de datos nos permiten trabajar con números enteros ya sean positivos o negativos.

| Nombre   |      bytes      |  rango |
|----------|:-------------:|------:|
| long |  8 | –9,223,372,036,854,775,808 a 9,223,372,036,854,775,807 |
| int |    4   |   –2,147,483,648 a 2,147,483,647 |
| short | 2 |   –32,768 to 32,767 |
| byte | 1 |    –128 to 127 |

En la mayoria de los casos usaremos el tipo de dato int para números positivos.

"cuando hacemos una suma o multiplicacion, short y byte se promueven a int antes de que se hagan los cálculos"

entonces :

```java
byte a =  127 ;
short b =  -128 ;
short sum = (short) a + (short) b ;
System.out.println (sum) ;
```
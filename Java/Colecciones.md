# COLECCIONES
Las Colecciones son para almacenar objetos, agrupar y tiene dos grandes tipos: Collection y Map (Diccionarios).
Los collection es un API para agrupación de objetos, consta de tres tipos: 
* List: Almacena objetos en una secuencia determinada
* Set: No permite elementos duplicados y no mantiene el orden de sus elementos. Es una interfaz que hereda de Collections
* Map: Almacena información en base a parejas de llaves y valores.

## Set (Collection)
```
Set<String> hs = new HashSet<>();
hs.add("uno");
hs.add("dos");
hs.add("tres");
hs.add("cuatro");
hs.add("cinco");

System.out.println("hs = " + hs); // hs = [cinco, uno, dos, tres, cuatro]
System.out.println("Permite datos duplicados = " + hs.add("tres")); // Permite datos duplicados = false
```
> Siempre definir el tipo más genérico en este caso set. Será un HashSet de tipo Set.
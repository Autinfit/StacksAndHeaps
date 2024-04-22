# StacksAndHeaps

## Key Difference Between Stack and Heap Memory

- **_"Stack" is a linear data structure, while "Heap" is a higher data structure._**
- **_"Stack" memory will never be fragmented, while "Heap" memory can become fragmented when memory blocks are first allocated and then freed._**
- **_"Stack" accesses local variables only while "Heap" allows you to access variables globally._**
- **_"Stack" variables cannot be resized, while "Heap" variables can be resized._**
- **_"Stack" memory is allocated in a contiguous block, while "Heap" memory is allocated in any random order._**
- **_"Stack" does not require deallocating variables, while in "Heap" you do need to deallocate them._**
- **_"Stack" allocation and deallocation are done by compiler instructions, while "Heap" allocation and deallocation are done by the programmer._**

## Other differences associated with "Stack" and "Heap"

**_They are different data structures but, sometimes, it can be difficult to identify their differences, especially when you are just learning programming. In this post I will briefly explain the differences between both data structures._**

### The "Call" stack

**_The "call" Stack, execution stack, function stack, control stack, runtime stack or simply call stack is a dynamic data structure that stores information about the active subroutines of a running program. When we make a call to a function, a block at the top of the stack is reserved to store the local variables along with some data necessary to guarantee the proper functioning of the structure (such as the address to which the thread of execution will have to return). when the function ends). After returning, the stack block occupied by the call is freed so it can be used later if necessary._**

**_It is called execution stack because it is a data structure that works under the concept of L.I.F.O. (last in first out). This makes it easier to keep track of which blocks need to be released, since it will be the one at the top of the stack._**

**_Multiple execution stacks can exist in a program when it is multithreaded; Each thread has its own stack with which it will maintain control of its function calls._**

![image](https://github.com/Autinfit/StacksAndHeaps/assets/155406623/9000bb50-38a4-4635-b9e2-99dd074e1d91)

### The heap (Free Storage)

**_The free heap, free zone, free storage or heap is a dynamic data structure used to store running data. Unlike the execution stack, which only stores the variables declared in the blocks prior to their execution, the heap allows memory to be reserved dynamically, that is, it is responsible for making the "magic" of dynamic memory happen. Global and static variables are also stored in it._**

**_As this data structure does not follow any methodology, it is a bit complicated to maintain control of the reserved memory blocks since spaces can be occupied and freed at any time._**

![image](https://github.com/Autinfit/StacksAndHeaps/assets/155406623/6721c342-ab30-40c3-b8d2-ddfd75f6d4da)

**_Traducido del español:_**

## Diferencia clave entre la memoria de pila y de montón

- **_"Stack" es una estructura de datos lineal, mientras que "Heap" es una estructura de datos más alta._**
- **_La memoria Stack nunca se van fragmentando, mientras que la memoria de montón puede fragmentarse cuando los bloques de memoria se asignan primero y luego se liberan._**
- **_"Stack" accede a variables locales solo mientras que "Heap" le permite acceder a variables de manera global._**
- **_Las variables Stack no se pueden cambiar de tamaño, mientras que las variables de montón se pueden cambiar dicho tamaño._**
- **_La memoria de pila se asigna en un bloque contiguo, mientras que la memoria Heap se asigna en cualquier orden aleatorio._**
- **_"Stack" no requiere desasignar variables, mientras que en "Heap" sí se necesita desasignar éstas._**
- **_La asignación y desasignación de la pila se realizan mediante instrucciones del compilador, mientras que la asignación y desasignación del montón las realiza el programador._**

## Otras diferencias asociadas a Stack y Heap

**_Son estructuras de datos distintas pero, a veces, puede llegar a ser complicado identificar sus diferencias, principalmente cuando recién aprendes programación. En esta entrada te explicaré de forma breve las diferencia entre ambas estructuras de datos._**

### La pila de llamadas (call Stack)

**_La pila de llamadas, pila de ejecución, pila de función, pila de control, pila de tiempo de ejecución o simplemente call stack es una estructura dinámica de datos que almacena la información sobre las sub-rutinas activas de un programa en ejecución. Cuando hacemos una llamada a una función, un bloque en el tope de la pila es reservado para guardar las variables locales junto con algunos datos necesarios para garantizar el funcionamiento adecuado de la estructura (como la dirección a la que tendrá que retornar el hilo de ejecución cuando termine la función). Después de retornar, el bloque de la pila que ocupaba el llamado, se libera para poder utilizarse más adelante de ser necesario._**

**_Se llama pila de ejecución porque es una estructura de datos que funciona bajo el concepto de L.I.F.O. (last in first out). Esto hace que sea más sencillo mantener el control de los bloques que deben ser liberados, puesto que será aquel que esté en el tope de la pila._**

**_Pueden existir múltiples pilas de ejecución en un programa cuando este es multihilo; cada hilo tiene su propia pila con la que mantendrá el control de sus llamadas a funciones._**

![image](https://github.com/Autinfit/StacksAndHeaps/assets/155406623/40786d04-df4c-40cb-b740-30586e0d339a)

### El heap (almacenamiento libre)

**_El montículo libre, zona libre, almacenamiento libre o "heap" es una estructura dinámica de datos utilizada para almacenar datos en ejecución. A diferencia de la pila de ejecución que solamente almacena las variables declaradas en los bloques previo a su ejecución, el heap permite reservar memoria dinámicamente, es decir, es el encargado de que la «magia» de la memoria dinámica ocurra. Las variables globales y estáticas también son almacenadas en él._**

**_Como esta estructura de datos no sigue ninguna metodología, es un poco complicado mantener el control de los bloques de memoria reservados puesto que se pueden ocupar y liberar espacios en cualquier momento._**

![image](https://github.com/Autinfit/StacksAndHeaps/assets/155406623/6180a7d5-4014-4d91-a43b-49f597ff3f76)

## Ejemplo de heap vs stack

**_Si compilas y ejecutas el siguiente ejemplo, podrás tener una idea general de cómo se comportan el stack y el heap:_**

```
#include <stdio.h>
#include <stdlib.h>
void foo(int valor) {
  unsigned char c;
  unsigned char *ptr = malloc(1);
  printf("Stack: %p | Heap: %p\n", &c, ptr);
  if(valor <= 0) return;
  foo(valor - 1);
}
int main(){
  foo(10);
  return 0;
}
```
**_Ejemplo de salida:_**

![image](https://github.com/Autinfit/StacksAndHeaps/assets/155406623/c2e28004-b9d3-4594-8093-2dc999c02308)

**_Explicación: La variable ```c``` nos permite mostrar la pila porque es declarada como variable interna en cada recursión de ```foo()```. El apuntador ```*ptr``` nos permite visualizar el heap porque utilizamos ```malloc()``` para reservar memoria dinámicamente durante la ejecución del programa. Que las direcciones de memoria incrementen o disminuyan depende de la arquitectura del equipo con el que trabajes._**

**_Como pudiste darte cuenta, la pila de ejecución y el heap son estructuras que se usan para almacenar datos durante la ejecución de nuestros programas, sin embargo, sus diferencias son muy marcadas y es necesario aprender a identificarlas para administrar mejor la memoria de nuestros equipos._**

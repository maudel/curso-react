## Funciones Flecha

ES6 ofrece una nueva sintaxis para tratar con `this` que es nuestro conexto :"funciones de flecha ". La función de flecha también hace que sea más fácil trabajar con funciones de "orden superior" (funciones que toman funciones como parámetros).

La nueva notación de "flecha gruesa" se puede usar para definir funciones anónimas de una manera más simple.

### Ejemplo Basico

Escribamos a una funcion para sumar dos numeros.

    var sum = function( a, b ) {
        return a + b;
    };

Usando functiones flecha ( `=>` ), vamos a reescribir la funcion en dos pasos.

**Paso 1** : reemplaza la palabra `function` por una flecha.

    var sum = ( a, b ) => {
        return a + b;
    };
    
**Paso 2**: Si el valor que retorna la funcion puede escribirse por una expresion, y el cuerpo de la funcion no tiene efectos secundarios, entonces podemos omitir y la palabra `return` tambien.

    var sum = ( a, b ) => a + b;
    
Si una funcion tiene un solo argumento, los parentesis no son necesarios a la izquierda de la flecha:

    var square = a => a * a;
    
### Ejemplo Medio

Considere el siguiente ejemplo:

      items.forEach (función (x) {
        console.log (x);
        incrementedItems.push (x + 1);
      });

Esto se puede reescribir como una "función de flecha" usando la siguiente sintaxis:

      items.forEach ((x) => {
        console.log (x);
        incrementedItems.push (x + 1);
      });
    
Las funciones que calculan una sola expresión y devuelven sus valores se pueden definir incluso más simple:

      incrementedItems = items.map ((x) => x + 1);
    
Este último es casi el equivalente a lo siguiente:

      incrementedItems = items.map (function (x) {
        devuelve x + 1;
      });

Sin embargo, hay una diferencia importante: **las funciones de flecha no establecen una copia local de `this`,` argumentos`, `super` o` new.target`**. Cuando `this` se usa dentro de una función de flecha, JavaScript usa` this` del ámbito externo.
   

### Ejercicios

**Ejercicio 1**: Escribe una funcion flecha que retorne `'Hello World!'`.

**Ejercicio 2**: Escribe una funcion que esperar un array de enteros, y retorna la suma de los elementos del array. Usa el metodo `reduce` en el argumento del array.

**Ejercicio 3**: Reescribe el siguiente codigo usando funciones flecha functions donde veas que tiene sentido:

    var Entity = function( name, delay ) {
      this.name = name;
      this.delay = delay;  
    };
    
    Entity.prototype.greet = function() {
        setTimeout( function() {
            console.log( 'Hi, I am ' + this.name );
        }.bind( this ), this.delay );
    };
    
    var java = new Entity( 'Java', 5000 );
    var cpp = new Entity( 'C++', 30 );
    
    java.greet();
    cpp.greet();

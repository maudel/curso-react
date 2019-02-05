## Funciones Flecha

ES6 ofrece una nueva sintaxis para tratar con `this` que es nuestro conexto :"funciones de flecha ". La función de flecha también hace que sea más fácil trabajar con funciones de "orden superior" (funciones que toman funciones como parámetros).

La nueva notación de "flecha gruesa" se puede usar para definir funciones anónimas de una manera más simple.


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
    

Sin embargo, hay una diferencia importante: las funciones de flecha no establecen una copia local de `this`,` argumentos`, `super` o` new.target`. Cuando `this` se usa dentro de una función de flecha, JavaScript usa` this` del ámbito externo. Considere el siguiente ejemplo:

    Toppings de clase {
      constructor (ingredientes) {
        this.toppings = Array.isArray (toppings)? ingredientes: [];
      }
      outputList () {
        this.toppings.forEach (función (superación, i) {
          console.log (superando, i + '/' + this.toppings.length); // no este
        })
      }
    }
    
    var ctrl = Nuevos ingredientes (['queso', 'lechuga'));
    
    ctrl.outputList ();
    


Parámetros predeterminados

Antigua forma de ES5 para establecer parámetros predeterminados

Enfoque 1: forma fácil.

    // Esto es lo que la gente hace normalmente en ES5 para establecer parámetros predeterminados
    enlace de función (altura, color, callbackFn) {
      var altura = altura || 50;
      var color = color || 'rojo';
      var callbackFn = callbackFn || función () {};
    
      // contenido de la función ...
    }
    

Funciona bien, pero en la implementación anterior no tuvimos en cuenta los valores falsos. Por ejemplo: `0, '', null, NaN, false` son [valores falsos] (https://dorey.github.io/JavaScript-Equality-Table).


Enfoque 2: mejor manera.

    // Entonces hay una mejor manera de hacer esto, comprueba que param no está definido realmente o no:
    enlace de función (altura, color, callbackFn) {
      var altura = tipo de altura! == 'indefinido'? altura: 50;
      var color = tipo de color! == 'indefinido'? color rojo';
      var callbackFn = typeof callbackFn! == 'undefined'? callbackFn: function () {};
    
      // contenido de la función ...
    }
    
ES6 forma de escribir parámetros por defecto
-------------------------------

Enfoque 3: ES6 camino, se pone mucho mejor.


    enlace de función (altura = 50, color = 'rojo', devolución de llamadaFn = () => {}) {
      // contenido de la función ...
    }
    
    // o usando ES6 const y let
    const noop = () => {};
    enlace const = (altura = 50, color = 'rojo', callbackFn = noop) => {
      // contenido de la función ...
    };
    

Otras lecturas:[https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/default\_parameters◆(https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions / default_parameters)
* [http://tc39wiki.calculist.org/es6/default-parameter-values/◆ (http://tc39wiki.calculist.org/es6/default-parameter-values/)
* [http://exploringjs.com/es6/ch\_parameter-handling.html◆ (http: //exploringjs.com/es6/ch_parameter-handling.html)
* [https://dorey.github.io/JavaScript-Equality-Table◆(https://dorey.github.io/JavaScript-Equality-Table)
Send feedback
History
Saved
Community

### Ejercicios

**Ejercicio 1.** Escribe una funcion que ejecute una funcion que ejecute otra funcion despues de un determinado retraso en milisegundos. El valor por defecto del retraso es un segundo.


**Exercise 2.** Change the below code such that the second argument of `printComment` has a default value that's initially `1`, and is incremented by `1` after each call.

    function printComment( comment, line ) {
        console.log( line, comment );
    }

**Exercise 3** Determine the values written to the console.

+

    function argList( productName, price = 100 ) {
        console.log( arguments.length );
        console.log( productName === arguments[0] );
        console.log( price === arguments[1] );
    };
    
    argList( 'Krill Oil Capsules' );
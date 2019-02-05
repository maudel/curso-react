## Template Literals

En el JavaScript tradicional, el texto incluido entre las marcas `" `o` `` coincidentes se considera una cadena. El texto entre comillas dobles o simples solo puede estar en una línea. Tampoco había forma de insertar datos en estas cadenas. Esto resultó en un montón de código de concatenación feo que parecía:

    nombre var = 'Sam';
    edad var = 42;

    console.log ('hola mi nombre es' + nombre + 'Soy' + edad + 'años');
    // = 'hola mi nombre es Sam tengo 42 años'
    

ES6 introduce un nuevo tipo de cadena literal que está marcado con marcas de retroceso (\ `). Estos literales de cadena _can_ incluyen nuevas líneas, y hay un nuevo mecanismo para insertar variables en cadenas:

    nombre var = 'Sam';
    edad var = 42;
    
    console.log (`hola mi nombre es $ {nombre}, y tengo $ {edad} años`);
    // = 'Hola, me llamo Sam y tengo 42 años'
    

El `$ {}` funciona bien con cualquier tipo de expresión, incluyendo expresiones de miembros y llamadas a métodos.

    nombre var = 'Sam';
    edad var = 42;
    
    console.log (`hola mi nombre es $ {name.toUpperCase ()}, y tengo $ {age / 2} años ');
    // = 'Hola, mi nombre es SAM y tengo 21 años'
    

Hay todo tipo de lugares donde este tipo de cadenas puede ser útil, y el desarrollo web frontal es uno de ellos.


###Otras lecturas
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template\_literals◆(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference / Template_literals)
[https://developers.google.com/web/updates/2015/01/ES6-Template-Strings?hl=en◆(https://developers.google.com/web/updates/2015/01/ES6 -Template-Strings? Hl = en)
* [https://ponyfoo.com/articles/es6-template-strings-in-depth◆(https://ponyfoo.com/articles/es6-template-strings-in-depth)
* [http://exploringjs.com/es6/ch\_template-literals.html◆ (http: //exploringjs.com/es6/ch_template-literals.html)
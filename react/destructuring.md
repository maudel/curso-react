## Destructuring

Destructuring es una forma de extraer rápidamente los datos de un `{}` o `[]` sin tener que escribir mucho código.

    deja foo = ['uno', 'dos', 'tres'];
    
    sea ​​uno = foo [0];
    dejar dos = foo [1];
    vamos a tres = foo [2];
    

dentro

    deja foo = ['uno', 'dos', 'tres'];
    vamos [uno, dos, tres] = foo;
    console.log (uno); // 'uno'
    

Esto es bastante interesante, pero al principio puede ser difícil ver el caso de uso. ES6 también admite la desestructuración de objetos, lo que podría hacer que los usos sean más obvios:



    deja myModule = {
      drawSquare: función drawSquare (longitud) {/ * implementación * /},
      drawCircle: función drawCircle (radio) {/ * implementación * /},
      drawText: función drawText (texto) {/ * implementación * /},
    };
    
    vamos a {drawSquare, drawText} = myModule;
    
    dibujar cuadrado (5);
    drawText ('hola');
    

La destrucción también se puede usar para pasar objetos a una función, lo que le permite extraer propiedades específicas de un objeto de manera concisa. También es posible asignar valores predeterminados a los argumentos desestructurados, lo que puede ser un patrón útil si se pasa un objeto de configuración.



    let jane = {firstName: 'Jane', lastName: 'Doe'};
    let john = {firstName: 'John', lastName: 'Doe', middleName: 'Smith'}
    función sayName ({firstName, lastName, middleName = 'N / A'}) {
      console.log (`Hello $ {firstName} $ {middleName} $ {lastName}`)
    }
    
    sayName (jane) // -> Hello Jane N / A Doe
    sayName (john) // -> Helo John Smith Doe
    

El operador de propagación permite expandir una expresión en lugares donde se esperan múltiples argumentos (para llamadas a funciones) o múltiples elementos (para literales de matriz) o múltiples variables (para desestructurar la asignación).


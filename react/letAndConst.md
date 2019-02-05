## Variables `let` y `const`

ES6 introduce el concepto de contexto de bloque. El alcance del bloque será familiar para los programadores de otros lenguajes como C, Java o incluso PHP. En ES5 JavaScript, y anteriormente, `var`s están orientados a` function`s, y pueden "ver" fuera de sus funciones al contexto externo.

    var cuatro = 4;
    var otroTres = tres; // error
    
    función f1 () {
      var tres = 3;
      var otroCuatro = cuatro; // == 4
      var otroSiete = siete; // error
    }
    
    función f2 () {
      var siete = 7;
      var otroCuatro = cuatro; // == 4
      var otroTres = tres; // error
    }
    

En ES5, las funciones eran esencialmente contenedores que podían "verse" desde, pero no dentro.

En ES6 `var` todavía funciona de esa manera, utilizando funciones como contenedores, pero hay dos nuevas formas de declarar variables:` const` y `let`. `const`, y` let` usan `{`, y `}` como contenedores, por lo tanto, "ámbito de bloque".

El alcance del bloque es más útil durante los bucles. Considera lo siguiente:

    var i;
    para (i = 0; i <10; i + = 1) {
      var j = i;
      sea ​​k = i;
    }
    console.log (j); // 9
    console.log (k); // undefined
    

A pesar de la introducción del alcance del bloque, las funciones siguen siendo el mecanismo preferido para tratar con la mayoría de los bucles.

`let` funciona como` var` en el sentido de que sus datos son de lectura / escritura. `let` también es útil cuando se usa en un bucle for. Por ejemplo, sin dejar:

    for (var x = 0; x <5; x ++) {
      setTimeout (() => console.log (x), 0)
    }
    

Saldría `5,5,5,5,5`. Sin embargo, cuando se utiliza `let` en lugar de` var`, el valor se aplicará de forma que la gente pueda esperar.

    para (sea x = 0; x <5; x ++) {
      setTimeout (() => console.log (x), 0)
    }
    
Alternativamente, `const` es de solo lectura. Una vez que se ha asignado `const`, el identificador no se puede reasignar, el valor es [no es inmutable] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const ).

Por ejemplo:

    const myName = 'pat';
    deja tuNombre = 'jo';
    yourName = 'sam'; // asigna
    myName = 'jan'; // error
    
La naturaleza de solo lectura puede ser demostrada con cualquier objeto:

    const literal = {};
    literal.attribute = 'test'; // bien
    literal = []; // error
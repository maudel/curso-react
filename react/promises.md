##Promesas

Las promesas están incorporadas en ES6.

    espera de const (ms) => {
      devolver nueva promesa ((resolver, rechazar) => {
        setTimeout (resolver, ms);
      });
    }
    espere (1000) .then (() => console.log ('tick'));
    
Promesas vs devoluciones de llamada

Para solicitudes HTTP, nuestra solución existente es utilizar devoluciones de llamada:

    solicitud (url, (error, respuesta) => {
      // manejar el éxito o el error.
    });
    hacer algo más();
    
Algunos problemas existen con las devoluciones de llamada. Uno se conoce como ["Callback Hell"] (http://callbackhell.com/). Un problema mayor es la descomposición.

El patrón de devolución de llamada requiere que especifiquemos la tarea y la devolución de llamada al mismo tiempo. En contraste, las promesas nos permiten especificar y enviar la solicitud en un solo lugar:


    promesa = fetch (url); // fetch es un reemplazo para XMLHttpRequest
    

y luego para agregar la devolución de llamada más tarde, y en un lugar diferente:

    promesa.then (respuesta => {
      // manejar la respuesta.
    });
    
Esto también nos permite adjuntar múltiples controladores a la misma tarea:

    promesa.then (respuesta => {
      // manejar la respuesta.
    });
    promesa.then (respuesta => {
      // haz algo más con la respuesta.
    });
    
Más sobre promesas

`.then ()` siempre devuelve una promesa. Siempre.

    p1 = getDataAsync (consulta);
    
    p2 = p1.then (
      resultados => transformData (resultados));
    
`p2` ahora es una promesa independientemente de lo que` transformData () `haya devuelto. Incluso si algo falla.


Si la función de devolución de llamada devuelve un valor, la promesa se resuelve a ese valor:

    p2 = p1.then (resultados => 1);
    

`p2` se resolverá a" 1 ".


Si la función de devolución de llamada devuelve una promesa, la promesa se resuelve en una promesa funcionalmente equivalente:

    p2 = p1.then (resultados => {
      dejar que newPromise = getSomePromise ();
      devuelve newPromise;
    });
    

`p2` ahora es funcionalmente equivalente a newPromise.

    p2 = p1.then (
      resultados => lanzar error ('Oops'));
    
    p2.then (resultados => {
      // Te estarás preguntando por qué esto nunca es
      // llamado.
    });
    

`p2` sigue siendo una promesa, pero ahora será rechazado con el error de lanzamiento.

¿Por qué la segunda devolución de llamada nunca será llamada?

### Manejo de Errores

La función pasada a `then` toma un segundo argumento, es decir,` error`, que representa la captura de errores dentro de la cadena de promesa.

    fetch ('http://ngcourse.herokuapp.com/api/v1/tasks')
      .then (response => response.data)
      .then (tareas => filterTasksAsynchronously (tareas))
      .then (tareas => {
        $ log.info (tareas);
        vm.tasks = tareas;
      })
      .entonces(
        nulo,
        error => log.error (error)
      );
    

Tenga en cuenta que una captura al final es a menudo suficiente.

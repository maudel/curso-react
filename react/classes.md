## Las clases

El concepto de prototipos y herencia prototípica en ES5 es difícil de entender para muchos desarrolladores que están pasando de otro lenguaje de programación al desarrollo de JavaScript.

Las clases de ES6 introducen **_syntactic sugar_** para hacer que los prototipos se vean como herencia clásica.
Por esta razón, algunas personas aplauden las clases, ya que hace que JavaScript les parezca más familiar.

Otras personas parecen haber lanzado una guerra santa contra las clases, afirmando que la sintaxis de la clase es errónea y elimina las principales ventajas del uso de JavaScript.

En algún nivel, todas las opiniones tienen mérito. Mi consejo para usted es que el mercado siempre tiene la razón. Conocer las clases le brinda la ventaja de que puede mantener el código escrito en la sintaxis de la clase. No significa que tengas que usarlo. Si su juicio justifica que se utilicen las clases, ¡adelante!

No conocer la sintaxis de clase es una desventaja.

El juicio sobre la sintaxis de clase, u ofrecer alternativas está fuera del alcance de esta sección.

### Herencia prototípica en ES5

Comencemos con un ejemplo, donde implementamos un escenario de herencia clásico en JavaScript.

    function Shape( color ) {
        this.color = color;
    }

    Shape.prototype.getColor = function() {
        return this.color;
    }

    function Rectangle( color, width, height ) {
        Shape.call( this, color );
        this.width = width;
        this.height = height;
    };

    Rectangle.prototype = Object.create( Shape.prototype );
    Rectangle.prototype.constructor = Rectangle;

    Rectangle.prototype.getArea = function() {
        return this.width * this.height;
    };

    let rectangle = new Rectangle( 'red', 5, 8 );
    console.log( rectangle.getArea() );
    console.log( rectangle.getColor() );
    console.log( rectangle.toString() );
    

`Shape' es una función constructora. Aunque no había clases en ES5, muchas personas denominaban funciones de constructor y sus clases de extensiones de prototipo.

Creamos una instancia de una clase con la palabra clave `new`, creando un objeto fuera de ella. En la terminología ES5, las funciones del constructor devuelven objetos nuevos, habiendo definido las propiedades y operaciones.

La herencia prototípica se define entre `Shape` y` Rectangle`. Por lo tanto, podemos llamar al método `getColor` en un ` Rectangle`.


La herencia de prototips se define implícitamente entre `Object` y` Shape`. Como la cadena del prototipo es transitiva, podemos llamar el método incorporado `toString` en un objeto rectangular, incluso si proviene del prototipo de` Object`.


El código parece un poco extraño, y los fragmentos de código que deben estar juntos están separados.


###  Como se puede hacer en ES6

Veamos la versión ES6. Como veremos más adelante, las dos versiones no son equivalentes entre sí, solo describimos el mismo dominio de problema con el código ES5 y ES6.

    class Shape {
        constructor( color ) {
            this.color = color;
        }

        getColor() {
            return this.color;
        }
    }

    class Rectangle extends Shape {
        constructor( color, width, height ) {
            super( color );
            this.width = width;
            this.height = height;
        }

        getArea() {
            return this.width * this.height;
        }
    }

    let rectangle = new Rectangle( 'red', 5, 8 );
    console.log( rectangle.getArea() );
    console.log( rectangle.getColor() );
    console.log( rectangle.toString() );

Las clases pueden encapsular

* una función constructora
* Operaciones adicionales que amplían el prototipo.
* Referencia al prototipo padre.

Note lo siguiente:


* la palabra clave `extends` define la relación entre` Shape` y `Rectangle`. Todas las instancias de `Rectangle` también son instancias de` Shape`.
* El método `constructor` es un método que se ejecuta cuando se crea una instancia de una clase. Puedes llamar al método constructor de tu clase padre con `super`. Más sobre `super` más tarde.
* Los métodos se pueden definir dentro de las clases. Todos los objetos pueden llamar a los métodos de su clase y a todas las clases que son más altas en la cadena de herencia.
* La creación de instancias funciona exactamente de la misma manera que la creación de instancias de una función constructora de ES5.

Puede observar el código ES5 equivalente pegando el código anterior en el [editor en línea de BabelJs] (http://babeljs.io/repl/).

+

La razón por la que el código generado no es equivalente con el código ES5 que estudiamos es que la sintaxis de clase viene con características adicionales. Nunca necesitará la protección provista por estas características durante el uso regular. Por ejemplo, si llama al nombre de la clase como una función regular, o si llama a un método de la clase con el operador `new` como constructor, obtendrá un error.


> Su código se vuelve más legible, cuando pone mayúsculas en los nombres de clase, e inicia los nombres de objetos y métodos con una letra minúscula. Por ejemplo, `Person` debe ser una clase, y` person` debe ser un objeto.
>
> +

### Súper
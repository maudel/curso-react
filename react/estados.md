### Agregando un estado a un Componente


Siguiente en la lista es el estado Anteriormente, hablamos sobre cómo administrar las interfaces de usuario es difícil porque generalmente tienen muchos estados diferentes. Esta área es donde React realmente comienza a brillar. Cada componente tiene la capacidad de administrar su propio estado y pasar su estado a componentes secundarios si es necesario. Volviendo al ejemplo de Twitter anterior, el componente UserInfo (resaltado en rosa arriba) es responsable de administrar el estado (o datos) de la información de los usuarios. Si otro componente también necesitara este estado / datos, pero ese estado no era un hijo directo del componente UserInfo, entonces crearía otro componente que sería el padre directo de UserInfo y el otro componente (o ambos componentes que requerían ese estado). ), luego pasaría el estado hacia abajo como accesorios en los componentes secundarios. En otras palabras, si tiene una jerarquía de componentes múltiples, un componente padre común debe administrar el estado y transmitirlo a sus componentes hijos a través de accesorios.

Veamos un componente de ejemplo utilizando su propio estado interno.

    class HelloUser extends React.Component {
    constructor(props) {
        super(props)

        this.state = {
        username: 'tylermcginnis'
        }
    }
    render() {
        return (
        <div>
            Hello {this.state.username}
        </div>
        )
    }
    }

Hemos introducido una nueva sintaxis con este ejemplo. El primero que notará es el método constructor. De la definición anterior, el método del constructor es "La forma en que establece el estado de un componente". En otros términos, cualquier información que coloque en este estado dentro del constructor formará parte del estado de ese componente. En el código anterior le estamos diciendo a nuestro componente que queremos que mantenga un registro de un nombre de usuario. Este nombre de usuario ahora se puede usar dentro de nuestro componente haciendo {this.state.username}, que es exactamente lo que hacemos en nuestro método de procesamiento.

Lo último de lo que se debe hablar con el estado es que nuestro componente necesita la capacidad de modificar su propio estado interno. Hacemos esto con un método llamado setState. ¿Recuerda antes cuando hablamos sobre la representación de la dom virtual cuando los datos cambian?

Señal para notificar a nuestra aplicación que algunos datos han cambiado → Volver a renderizar DOM virtual -> Difundir DOM virtual anterior con DOM virtual nuevo -> Actualizar solo DOM real con los cambios necesarios.

Esa "señal para notificar a nuestra aplicación que algunos datos han cambiado" en realidad es solo setState. Cuando se llama a setState, el DOM virtual se vuelve a representar, se ejecuta el algoritmo diff y el DOM real se actualiza con los cambios necesarios.

Como una nota al margen, cuando introducimos setState en el código a continuación, también presentaremos algunos eventos que están en nuestra lista. Dos pájaros, una piedra.

Entonces, en el siguiente ejemplo de código, vamos a tener un cuadro de entrada que cada vez que alguien lo escriba, actualizará automáticamente nuestro estado y cambiará el nombre de usuario.

<iframe src="https://codesandbox.io/embed/73qww711zx" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

Tenga en cuenta que hemos introducido algunas cosas más. Lo primero es el método handleChange. Este método se llamará cada vez que un usuario escriba en el cuadro de entrada. Cuando se llame a handleChange, se llamará a setState para redefinir nuestro nombre de usuario con cualquier cosa que se haya escrito en el cuadro de entrada (e.target.value). Recuerde, siempre que se llame a setState, React crea un nuevo DOM virtual, realiza la diferencia y luego actualiza el DOM real.

Ahora veamos nuestro método de renderizado. Hemos agregado una nueva línea que contiene un campo de entrada. El tipo de campo de entrada obviamente será texto. El valor será el valor de nuestro nombre de usuario que se definió originalmente en nuestro método getInitialState y se actualizará en el método handleChange. Observe que hay un nuevo atributo que probablemente nunca haya visto antes, en Cambiar. onChange es una cosa React y llamará al método que especifique cada vez que cambie el valor en el cuadro de entrada, en este caso el método que especificamos fue handleChange.

El proceso para el código anterior sería algo así.

Un usuario escribe en el cuadro de entrada → Se invoca handleChange → el estado de nuestro componente se establece en un nuevo valor → React muestra las representaciones del DOM virtual → React Diffs el cambio → Real DOM se actualiza.

Más adelante, cuando cubramos los accesorios, veremos algunos casos de uso más avanzados del estado de manejo.

¡Estamos llegando! Si no puede explicar los elementos en negrita a continuación, vuelva a leer esa sección. Un consejo para REALMENTE aprender React, no permitas que leer esto de forma pasiva te dé una falsa sensación de seguridad de que realmente sabes lo que está pasando y que puedes recrear lo que estamos haciendo. Diríjase a CodeSandbox e intente recrear (o crear sus propios componentes) sin mirar lo que he hecho. Es la única manera en la que realmente comenzarás a aprender cómo construir con React. Esto va para este tutorial y lo siguiente por venir.
## Tu primer Hola mundo con React

<iframe src="https://codesandbox.io/embed/kyl0z8yv5" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>



Observe que el único método en nuestra clase es renderizar. Se requiere que cada componente tenga un método de renderizado. El motivo de esto es que la representación está describiendo la IU (interfaz de usuario) para nuestro componente. Entonces, en este ejemplo, el texto que se mostrará en la pantalla donde se representa este componente es Hello World! Ahora veamos lo que está haciendo ReactDOM. ReactDOM.render toma dos argumentos. El primer argumento es el componente que desea representar, el segundo argumento es el nodo DOM donde desea representar el componente. (Tenga en cuenta que estamos usando ReactDOM.render y no React.render. Este fue un cambio realizado en React .14 para hacer que React sea más modular. Tiene sentido cuando piensa que React puede generar más cosas que solo un elemento DOM). En el ejemplo anterior, le estamos diciendo a React que tome nuestro componente HelloWorld y lo represente al elemento con un ID de raíz. Debido a las relaciones padre / hijo hijo de React de las que hablamos anteriormente, por lo general, solo tiene que usar ReactDOM.render una vez en su aplicación porque al representar la mayoría del componente padre, todos los componentes hijos también se procesarán.

Ahora, en este punto, es posible que se sienta un poco extraño al lanzar "HTML" en su JavaScript. Desde que comenzó a aprender el desarrollo web, se le ha dicho que debe mantener su lógica fuera de la vista, también conocido como JavaScript que no está acoplado de su HTML. Este paradigma es fuerte, pero tiene algunas debilidades. No quiero prolongar este tutorial para convencerte de que esta idea es un paso en la dirección correcta, por lo que si esta idea aún te molesta, puedes consultar este enlace. A medida que aprendas más sobre React, esta inquietud debería disminuir rápidamente. El "HTML" que estás escribiendo en el método de render no es en realidad HTML, pero es lo que React llama "JSX". JSX simplemente nos permite escribir una sintaxis HTML que, eventualmente, se transforma en objetos JavaScript ligeros. React puede entonces tomar estos objetos de JavaScript y de ellos formar un "DOM virtual" o una representación de JavaScript del DOM real. Esto crea una situación de ganar / ganar en la que obtiene la accesibilidad de las plantillas con el poder de JavaScript.

Mirando el ejemplo a continuación, esto es en lo que eventualmente se compilará su JSX.

    class HelloWorld extends React.Component {
    render() {
        return React.createElement("div", null, "Hello World");
      }
    }
Ahora, que vimos la fase de transformación de JSX -> JS y escribir tus componentes React como el código anterior, pero como puedes imaginar, eso sería bastante complicado. No conozco a nadie que no esté usando JSX. Para obtener más información acerca de lo que JSX compila, revise React Elements vs React Components

Hasta este punto, no hemos enfatizado realmente la importancia de este nuevo paradigma de DOM virtual al que nos estamos lanzando. La razón por la que el equipo de React optó por este enfoque es que, dado que el DOM virtual es una representación de JavaScript del DOM real, React puede hacer un seguimiento de la diferencia entre el DOM virtual actual (calculado después de algunos cambios de datos), con el DOM virtual anterior. (computado antes de algunos cambios de datos). React luego aísla los cambios entre el DOM virtual antiguo y el nuevo y luego solo actualiza el DOM real con los cambios necesarios. En términos más simples, debido a que la manipulación del DOM real es lenta, React puede minimizar las manipulaciones del DOM real al realizar un seguimiento de un DOM virtual y solo actualizar el DOM real cuando sea necesario y solo con los cambios necesarios. (Más información aquí). Normalmente, las UI tienen muchos estados, lo que dificulta su administración. Al volver a representar el DOM virtual cada vez que se produce un cambio de estado, React hace que sea más fácil pensar en qué estado se encuentra su aplicación. El proceso se ve algo así:

Algún evento de usuario que cambia el estado de su aplicación → Volver a renderizar DOM virtual -> Difundir DOM virtual anterior con DOM virtual nuevo -> Actualizar solo DOM real con los cambios necesarios.

Debido a que existe este proceso de transformación de JSX a JS, necesita configurar algún tipo de fase de transformación a medida que se desarrolla. En la parte 2 de esta serie, presentaré Webpack y Babel para realizar esta transformación.

Echemos un vistazo a nuestra lista de verificación "Las partes más importantes de React" y veamos dónde estamos ahora.


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
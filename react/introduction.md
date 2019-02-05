## React

Es una libreria para vistas de codigo  creado por Facebook.

### JSX

JSX es una herramienta que, aunque no es necesaria, hace que trabajar con React sea mucho más fácil de escribir y entender. JSX es compilar en Javascript nativo / regular.


### Componente

Si usted viene de Angularjs, el componente básico de Reactjs es muy similar a las directivas. Es una colección de HTML, CSS y JS. El componente puede tener componente dentro. Son una de las principales formas que tiene para definir las imágenes y las interacciones que conforman lo que las personas ven cuando usan su aplicación.


    var Component = React.createClass ({
        render: function () {
            regreso(
                <div>
                    <h1> Hola de React </h1>
                    <p> Fui renderizado desde el componente de la aplicación! </p>
                </div>
            )
        }
    });
    
    ReactDOM.render (
      <Componente />,
      document.getElementById ('contenedor')
    );
    

##### Componente Stateful 

Se crean con `React.createClass` y deben tener el método` render` que devuelve el componente regular. Este componente puede incluir cosas como el estado, los métodos de ayuda y otros enlaces avanzados en el DOM. Se preocupan por cómo funcionan las cosas, proporcionan los datos y el comportamiento a la presentación u otros componentes del contenedor y tienden a servir como fuentes de datos.


Ejemplos: UserPage, FollowersSidebar, StoryContainer, FollowedUserList.


##### Componente sin estado (presentación)

Muchos de los componentes que podemos crear son simplemente el código de plantilla que se inyecta en otro componente, por lo que se convierte en una gran cantidad de pequeños bloques de código reutilizables.



Con los componentes sin estado, podemos eliminar todo el código de la placa de la caldera y mantener todo (en algunos casos) una sola línea de código.



Las funciones sin estado están destinadas simplemente a devolver una plantilla específica que puede tomar propiedades dinámicas, que podrían ser componentes de nivel superior, como listas, entradas, etc. No tendrán ningún objeto estatal vinculado a ellos.


Ejemplos: Página, Barra lateral, Historia, Información del usuario, Lista.


    // componente sin estado
    var TextInput = function (props) {
return(
            <div className = {props.wrapperClass}>
          <label htmlFor = {props.name}> {props.label} </label>
          <div className = 'field'>
            <entrada
              tipo = 'texto'
              name = {props.name}
              className = 'form-input'
              valor = {props.value} />
          </div>
        </div>
        )
    }
    
    // Componente de Estado
    var Form = React.createClass ({
        getDefaultProps: function () {
            regreso{
                Nombre: "Jack",
                Apellido: "Stevenson"
            }
        }
        render: function () {
return(
                <div>
                    <TextInput
                        wrapperClass = 'form-group'
                        name = 'firstName'
                        label = 'Nombre'
                        value = {this.props.firstName}
                    />
                    <TextInput
                        wrapperClass = 'form-group'
                        name = 'lastName'
                        label = 'Apellido'
                        value = {this.props.lastName}
                    />
                </div>
            )}
    });
    
    ReactDOM.render (<Form />, document.getElementById ('container'));
    

### Variables

Use {} para representar la variable dentro de JSX.

+

    var Content = React.createClass ({
        render: function () {
            nombre var = "John Smith"
            regreso (
                <div>
                    <h1> Hola {nombre} </h1>
                </div>
            )
        }
    });
    
    ReactDOM.render (
      <Contenido />,
      document.getElementById ('contenedor')
    );
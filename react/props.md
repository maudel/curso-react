##Props

 Según nuestra definición anterior, props son los datos que se pasan al componente secundario desde el componente principal. Esto permite que nuestra arquitectura React se mantenga bastante sencilla. Maneje el estado en el componente primario más alto que necesite usar los datos específicos, y si tiene un componente secundario que también necesita esos datos, transfiéralos como props.

Aquí hay un ejemplo muy básico de usar accesorios.


<iframe src="https://codesandbox.io/embed/myjnox93mp" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>

Veamos un ejemplo más avanzado. Vamos a tener dos componentes ahora. Un padre, un hijo. El padre va a hacer un seguimiento del estado y pasará una parte de ese estado al niño como accesorios. Veamos primero ese componente padre.

### Componente principal:

    class FriendsContainer extends React.Component {
    constructor(props) {
        super(props)

        this.state = {
        name: 'Tyler McGinnis',
        friends: ['Jake Lingwall', 'Sarah Drasner', 'Merrick Christensen']
        }
    }
    render() {
        return (
        <div>
            <h3> Name: {this.state.name} </h3>
            <ShowList names={this.state.friends} />
        </div>
        )
    }
    }
### Componente Secundario:

    class ShowList extends React.Component {
    render() {
        return (
        <div>
            <h3> Friends </h3>
            <ul>
            {this.props.names.map((friend) => <li>{friend}</li>)}
            </ul>
        </div>
        )
    }
    }
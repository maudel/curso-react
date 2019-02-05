Componentes sin estado

* Super simple
* Dado algún estado (como props) ... devolver algunos DOM (o componentes adicionales)

     import react desde 'react';
    
     función HelloMessage ({nombre}) {
       regreso(
         <div> Hola {nombre} </div>
       );
     };
    
     HelloMessage.propTypes = {name: React.PropTypes.string};
     HelloMessage.defaultProps = {name: 'World'};
    
     ReactDOM.render (<HelloMessage name = "Alice" />, mountNode);
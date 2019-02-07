
### React Fundamentos 

#### Menu 

- renderizar el campo title DATA en un <h1>
- representar en una lista <ul> con cada uno de los elementos como un <li> y mostrar el nombre
- limitar la lista a solo comida nacional (pista: usa DATA.items.filter (...))
- ordena los artículos en orden alfabético por nombre
(sugerencia: use sort-by https://github.com/staygrimm/sort-by#example)

Algo mas desafiante 

- agrega un menú desplegable de selección para hacer que el filtrado en `type` sea dinámico
- agregar un botón para cambiar el orden de clasificación
- Sugerencia: necesitarás una función `updateThePage` que llame a` render`,
y luego deberás llamarlo en los controladores de eventos de los controles de formulario




#### Composicion de Menus

1. Haz un componente `Menu` que reciba una lista de
    artículos como prop
2. Haz un componente `MenuItem` y pásalo los accesorios
    necesita hacer
3. Renderice dos menús al mismo tiempo, uno para
    Comida mexicana y una para comida inglesa.
4. Pase un "nombre" personalizado a cada Menú
Módulos
=======

ES6 también introduce el concepto de un módulo, que funciona de manera similar a otros idiomas. Definir un módulo ES6 es bastante sencillo: se supone que cada archivo define un módulo y especificaremos sus valores exportados usando la palabra clave export.

+

     importar Parse desde 'parse';
     importar {myFunc} desde './myModule';
     importar * como myModule desde './myOtherModule';
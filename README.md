# Novedades en JavaScript: Repaso a todas ellas, desde la versión ES5 hasta la ES12

JavaScript es un lenguaje ligero e interpretado, dialecto del estándar ECMAScript, orientado a objetos con funciones de primera clase. Se utiliza principalmente en su forma del lado del cliente, implementando como parte de un navegador web permitiendo mejoras en la interfaz de usuario y páginas web dinámicas.

Actualmente el estándar ECMAScript, se encuentra en la versión ECMAScript 2019. A partir de las versiones ES5 y ES6 agregaron cambios significativos al lenguaje. Veremos algunos de ellos en este tutorial hasta la actual versión ES12.

## Indice

[Versión ES5 y ES6](#versión-es5-y-es6)

## Versión ES5 y ES6

#### Función Arrow

Para crear un código más limpio y claro. Veamos un ejemplo:

```js
// ES5
// Imaginemos una variable data que incluye un array de objetos
var data = [{...}, {...}, {...}, ...];
data.forEach(function(elem){
// Tratamos el elemento
console.log(elem)
})
```

En la versión ES6 se vería de la siguiente manera el código anterior:

```js
//ES6
var data = [{...}, {...}, {...}, ...];
data.forEach(elem => {
console.log(elem);
})
```

#### Clases

Ahora JavaScript tendrá clases con todo lo que conlleva, como por ejemplo, la herencia. Son muy parecidas a las funciones constructoras de objetos que realizábamos en el estándar anterior.

```js
class matematicas extends Libro {
  constructor(tematica, paginas) {
    super(tematica, paginas);
    this.capitulos = [];
    this.precio = "";
    // ...
  }
  metodo() {
    // ...
  }
}
```

#### This

La variable this anteriormente teníamos que cachearla en otra variable ya que solo hace referencia al contexto en el que nos encontremos. Por ejemplo, en el siguiente código si no hacemos var that = this dentro de la función document.addEventListener, this haría referencia a la función que pasamos por Callback y no podríamos llamar a foo().

```js
//ES3
var obj = {
  foo : function() {...},
  bar : function() {
    var that = this;
    document.addEventListener("click", function(e) {
      that.foo();
    });
  }
}
```

La función Arrow en la versión ES6 es más sencilla y visual:

```js
//ES6
var obj = {
  foo : function() {...},
  bar : function() {
    document.addEventListener("click", (e) => this.foo());
  }
}
```

#### Let y Const

Ahora podemos declarar variables con let en lugar de var si no queremos que sean accesibles más allá de un ámbito. Por ejemplo:

```js
//ES6
(function () {
  if (true) {
    let x = "hola mundo";
  }
  console.log(x);
  //Da error, porque "x" ha sido definida dentro del "if"
})();
```

#### Template Strings

Con ES6 podemos interpolar Strings de una forma más sencilla que como estábamos haciendo hasta ahora. Por ejemplo:

```js
//ES6
let nombre1 = "JavaScript";
let nombre2 = "awesome";
console.log(`Sólo quiero decir que ${nombre1} is ${nombre2`);
```

#### Destructuring

Tenemos nuevas formas de asignar valores a Arrays y a Objetos. Veamos unos ejemplos:

```js
var [a, b] = ["Buenos", "días"];
console.log(a); // "Buenos"
console.log(b); // "días"

var obj = { nombre: "Pepito", apellido: "Perez" };
var { nombre, apellido } = obj;
console.log(nombre); // "Pepito"
```

#### Valores por defecto

Otra de sus novedades es asignar valores por defecto a sus variables, que se pasan por parámetros en las funciones. Antes teníamos que comprobar si la variable ya tenía un valor. Ahora con ES6 se la podremos asignar según creemos la función:

```js
//ES6
function(valor = "foo") {...};
```

#### Módulos

A esto lo llamo un browserify nativo. Ahora JavaScript se empieza a parecer a lenguajes como Python o Ruby. Llamamos a las funciones desde los propios Scripts, sin tener que importarlos en el HTML, si usamos JavaScript en el navegador.

```js
//File: lib/person.js
module "person" {
  export function hello(nombre) {
  return nombre;
  }
}
```

También se pueden exportar de esta manera:

```js
export function hello(nombre) {...};
```

Y desde otro fichero:

```js
//File: app.js
import { hello } from "person";

var app = {
  foo: function() {
    hello("Pepe");
  }
}

export app;
```

## Versión ES7

#### Array.prototype.includes(var)

Comprueba si un array contiene el valor pasado por parámetro. Básicamente, funciona igual que la función String.prototype.includes(var) para cadenas de texto (tratada en este post), pero para arrays. Con esta función ya no tendremos que utilizar el indexOf() para comprobar si un determinado valor está en un array.

```js
const array = [1, ‘string’, true, 33];
console.log(array.includes(‘string’)); //true
console.log(array.includes(2)); //false
```

#### Operador de exponenciación ()\*\*

Este operador nos permite calcular la potencia de número. Le indicamos el número base y el exponente y nos hará el cálculo elevando el número base al exponente. Anteriormente, esto mismo, se podía hacer con la función Math.pow($base, $exponente), pero ahora no es necesario utilizarla gracias al operador \*\*.

```js
const base = 3;
const exponente = 10;
console.log(base \*\* exponente);
console.log(Math.pow(base, exponente));
```

Ambos ejemplos de código anteriores se verían de la siguiente forma:

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_1.jpg

## Versión ES8

#### Funciones asíncronas

La novedad más importante de esta versión son las funciones asíncronas, que devuelven promesas y se tienen que declarar con la keyword asinc delante de la declaración de la función. Solamente dentro de estas funciones podemos usar await e indicará que se detenga hasta que no esté resuelta la promesa de la función y cuando lo esté continuará con la ejecución normal. Utilizando async/await, se simplificará todo mucho mucho más pudiendo ejecutar código asíncrono como si fuese síncrono.

```js
const base = 3;
const exponente = 10;
console.log(base \*\* exponente);
console.log(Math.pow(base, exponente));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_2.jpg

Vamos a usar el paquete node-fetch, el cual nos permitirá usar la función fetch en Node.js, que es el entorno donde estamos ejecutando el código en Repl.it. Si lo estas ejecutando en tu local en un navegador directamente, sin Node.js, no te hará falta instalar el paquete, ya que la función fetch es una función nativa de JS.

#### Object.entries(obj)

Es un método añadido a Object que recibe como parámetro un objeto y lo que nos devuelve es un array que contiene tantos arrays como propiedades tenga el objeto con la clave y el valor de las propiedades.

```js
const obj = { test: 1, foo: true, string: "nombre" };
console.log(Object.entries(obj));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_3.jpg

#### Object.values(obj)

Este es otro método añadido a Object. Como el anterior, también recibe un objeto como parámetro y lo que nos devuelve son los valores de las propiedades del objeto pasado. Ejemplo:

```js
const obj = { test: 1, foo: true, string: "nombre" };
console.log(Object.values(obj));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_4.jpg

#### string.padStart(num, string)

padStart nos permite rellenar una cadena de texto desde el inicio de ésta hasta la longitud que hayamos indicado con los caracteres que queramos. Ejemplo:

```js
console.log("string".padStart(10));
console.log("string".padStart(10, "abc"));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_5.jpg

#### string.padEnd(num, string)

padEnd funciona igual que el anterior, pero en vez de rellenarlos por el principio de la cadena, lo rellena por el final de la cadena (último carácter).

```js
console.log("string".padEnd(10));
// "string "
console.log("string".padEnd(10, "abc"));
// stringabca
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_6.jpg

#### object.getOwnPropertyDescriptors()

El método Object.getOwnPropertyDescriptors() devuelve la descripción de las propiedades del objeto pasado por parámetro.

```js
const obj = {
  test: 1,
  foo: true,
  string: "nombre",
};
console.log(Object.getOwnPropertyDescriptors(obj));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_7.jpg

## Versión ES9

#### rest/spread properties

Es similar a lo que se puede hacer con los parámetros de las funciones y los arrays desde ES6 pero con propiedades de objetos.

```js
const obj = {
  name: "John",
  age: "32",
  city: "New York",
  address: "Address...",
};

// Rest
const { name, age, ...rest } = obj;
console.log(name, age, rest); // John 32 { city: 'New York', address: 'Address...' }

// Spread
const newObj = { name, job: "Developer", ...rest };
console.log(newObj);
const copyObj = { ...newObj };
console.log(copyObj, newObj);
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_8.jpg

#### promise: finally()

Es una función introducida en las promesas que se ejecutará siempre al finalizar la promesa, es decir, se ejecutará tanto si la promesa se ejecuta con éxito o es rechazada. Si lo has utilizado alguna vez y lo recuerdas, vendría a ser como él always del Ajax de jQuery.

Por tanto, ahora tendríamos tres posibles funciones callback para las promesas que serían `.then()`, `.catch()` y `.finally()`.

```js
const fetch = require("node-fetch");

// Promise: finally()
fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json())
  .then((json) => console.log(json))
  .catch((error) => console.log(error))
  .finally(() => console.log("Esto se mostrará siempre!"));
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_9.jpg

#### Iteración asíncrona

Se ha introducido el await para bucles for, lo cual permite iterar sobre iterables asíncronos(promesas). Se tiene que utilizar dentro de funciones asíncronas como cualquier await. El bucle quedaría así:

```js
for await (const variable of iterable) {
  ...
}
```

Ejemplo:

```js
var asyncIterable = {
  [Symbol.asyncIterator]() {
    return {
      i: 0,
      next() {
        if (this.i < 3) {
          return Promise.resolve({ value: this.i++, done: false });
        }
        return Promise.resolve({ done: true });
      },
    };
  },
};

(async function () {
  for await (let num of asyncIterable) {
    console.log(num);
  }
})();
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_10.jpg

#### Cambios en RegExp

Se puede dar un nombre a los grupos de captura para referirse a ciertas partes de una cadena y que de esta manera que más claro. Por ejemplo:

```js
let {
  groups: { one, two },
} = /^(?<one>._):(?<two>._)$/u.exec("foo:bar");
console.log(`one: ${one}, two: ${two}`);
```

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_11.jpg

#### Mira detrás de las afirmaciones

Hay dos versiones para mirar detrás de las afirmaciones: positiva y negativa.

##### Positivo(?<=...)

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_12.jpg

##### Negativo(?<!...)

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_13.jpg

#### RegExp Unicode Property Escapes

Ahora podemos buscar caracteres mencionando su propiedad Unicode dentro `/p{}`

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_14.jpg

## Versión ES10

#### Array.flat()

Método crea una nueva matriz con todos los elementos de la submatriz concatenados en ella recursivamente hasta la profundidad específica.

```js
let array1 = [1, 2, [3, 4]];
array1.flat();
//[1, 2, 3, 4]

let array2 = [1, 2, [3, 4, [5, 6]]];
array2.flat();
//[1, 2, 3, 4, [5, 6]]

var array3 = [1, 2, [3, 4, [5, 6]]];
array3.flat(2);
//[1, 2, 3, 4, 5, 6]
```

#### Array.flatMap()

Método que usando una función de mapeo, mapea cada elemento, y luego aplana el resultado en una nueva matriz.

```js
let array = [1, 2, 3, 4, 5];
array.map((x) => [x, x * 2]);

//[Array(2), Array(2), Array(2)]
//0: (2)[1, 2]
//1: (2)[2, 4]
//2: (2)[3, 6]

arr.flatMap((v) => [v, v * 2]);
//[1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
```

#### Object.fromEntries()

Método transforma una lista de pares `clave-valor` en un objeto.

```js
var obj = {
  key1: ‘value 1’,
  key2: ‘value 2’,
  key3: ‘value 3’
}

var entries = Object.entries(obj)

//(3) [Array(2), Array(2), Array(2)]
//0: (2) [“key1”, “value 1”]
//1: (2) [“key2”, “value 2”]
//2: (2) [“key3”, “value 3”]

var fromEntries = Object.fromEntries(entries)
//{key1: “value 1”, key2: “value 2”, key3: “value 3”}
```

#### String.trimStart() & String.trimEnd()

El `trimStart()` es un método que elimina los espacios en blanco desde el principio de una cadena.

El `trimEnd()` es un método que elimina los espacios en blanco del final de una cadena.

Puedes pensar por qué otro método nuevo ya tiene dos métodos `trimRight()` y `trimLeft()` será un alias de los métodos nuevos.

#### Enlace de captura opcional

Permitir que los desarrolladores utilicen try/ catch sin crear un enlace no utilizado. Eres libre de seguir adelante haciendo uso del bloque catch sin un parámetro.

```js
try{
  throw new Error(“some error”);
} catch {
  console.log(“no params for catch”);
}
```

#### Function.toString()

Método devuelve una cadena que representa el código fuente de la función. Más espacios blancos, las nuevas líneas y los comentarios se eliminarán cuando lo haga, se conservarán con el código fuente original.

```js
function hello(text){
  var name = text;
  //print name
  console.log(‘Hello ${name}’)
}

console.log(hello.toString())
// function hello(text){
  // var name = text;
  // print name
  //console.log(‘Hello${name}’)
//}
```

#### Symbol.description

Propiedad de solo lectura es una cadena que devuelve la descripción opcional de los Symbol objetos.

```js
var mySymbol = ‘My Symbol’
var symObj = Symbol(mySymbol)

console.log(symObj) //Symbol(My Symbol)
console.log(String(symObj) === ‘Symbol(${mySymbol})’) //true
console.log(symObj.description) //My Symbol
```

#### JSON.Stringify()

Este método convierte un objeto o valor de JavaScript en una cadena de texto JSON, opcionalmente reemplaza valores si se indica una función de reemplazo, o si se especifican las propiedades mediante un array de reemplazo.

```js
console.log(JSON.stringify({ x: 5, y: 6 })); // expected output: "{"x":5,"y":6}" console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)])); // expected output: "[3,"false",false]" console.log(JSON.stringify({ x: [10, undefined, function(){}, Symbol('')] })); // expected output: "{"x":[10,null,null,null]}" console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5))); // expected output: ""2006-01-02T15:04:05.000Z""
```

## ES11

#### import()

_Importaciones Dinámicas (Dynamic Imports)_

Algo que pasaba mucho en JavaScript, es que no podíamos importar módulos según sean necesarios.

```js
// Importación de Módulos antes de ES11
import * as myModule from "./someModule.js/";
// o
import { myModule } from "./someModule.js/";

const button = document.getElementById("button");

button.addEventListener("click", () => myModule.doSomething());
```

En este ejemplo estaríamos utilizando el método doSomething() de myModule, en el evento click de algún botón. Independientemente de cuando ocurra el evento click, aquí hay varios temas que debemos tener en cuenta:

La importación de nuestro modulo se produce durante el tiempo de carga del módulo actual.
No hay forma de cambiar la “dirección” u “origen” de nuestro modulo, dinámicamente.
Muy probablemente nuestro módulo quede sin usarse (aunque este ya haya sido cargado), si no se produce el click tan esperado.
Todo esto afecta el rendimiento de la aplicación que estemos desarrollando.

Con los imports dinámicos, nos despedimos de estos problemas:

```js
// Importación dinámica de módulos implementada en ES11
const customPath = someExpression ? "./somePath" : "./anotherPath";

const button = document.getElementById("button");

button.addEventListener("click", async () => {
  const myModule = await import(`${customPath}/myModule.js`);
  myModule.doSomething();
});
```

**Import** recibe el path donde se encuentra nuestro módulo y devuelve una promesa al terminar.

#### BigInt

_Números Enteros más “grandes”_

Hasta ahora en JavaScript podíamos hacer cálculos matemáticos cuyos resultados no sean mayores a 2⁵³ — 1, es decir, hasta **Number.MAX_SAFE_INTEGER**.

Les muestro un ejemplo sencillo de que pasa cuando nos sobrepasamos de este valor.

```js
Number.MAX_SAFE_INTEGER;
// 9007199254740991
Number.MAX_SAFE_INTEGER + 1;
// 9007199254740992
Number.MAX_SAFE_INTEGER + 2;
// 9007199254740992
Number.MAX_SAFE_INTEGER + 3;
// 9007199254740994
```

Con este ejemplo sabemos que JavaScript, no es capaz de representar cálculos matemáticos que superen el valor de **Number.MAX_SAFE_INTEGER**.

Para solventar este problema se ha añadido un nuevo tipo de dato numérico, llamado BigInt que como su nombre indica solo soporta números enteros.

La forma de utilizar este tipo de dato, es igual que **Number** o con la terminación “n” precedido del número.

```js
BigInt(Number.MAX_SAFE_INTEGER);
// 9007199254740991n
BigInt(Number.MAX_SAFE_INTEGER) + BigInt(1);
// 9007199254740992n
BigInt(Number.MAX_SAFE_INTEGER) + BigInt(2);
// 9007199254740993n
BigInt(Number.MAX_SAFE_INTEGER) + BigInt(3);
// 9007199254740994n

BigInt(Number.MAX_SAFE_INTEGER) + 3n;
// 9007199254740994n
9007199254740991n + 3n;
// 90071992547409914n
```

_BigInt y Number, no son compatibles entre sí por lo que no podemos hacer operaciones entre ambos._

#### Promise.allSettled()

Este método para las promesas viene añadir una característica que le faltaba al **Promise.all()**, el cual era resolver todas las promesas que le pasábamos independientemente de que alguna sea rechazada.

Recordemos **Promise.all()** lo que hacía es devolver un array con las respuestas de todas nuestras promesas SIEMPRE Y CUANDO NO HAYA SIDO RECHAZADA NINGUNA, en tal caso devolvería el error de la promesa rechazada y perderíamos el valor de las promesas que si fueron exitosas.

```js
var promise1 = Promise.resolve(3);
var promise2 = new Promise((resolve, reject) =>
  setTimeout(() => reject("Error from PromiseAll"), 1000)
);
var promises = [promise1, promise2];

Promise.all(promises).then((results) => console.log(results));

// Output: Uncaught (in promise) Error from PromiseAll
```

Respuesta del método all, cuando una promesa es rechazada o tuvo un error

```js
var promise1 = Promise.resolve(3);
var promise2 = new Promise((resolve, reject) =>
  setTimeout(() => reject("Error from PromiseAllSettled"), 1000)
);
var promises = [promise1, promise2];

Promise.allSettled(promises).then((results) => console.log(results));

/* Output:

[
   {
      status: 'fulfilled',
      value: 3
   },
   {
      status: 'rejected',
      reason: 'Error from PromiseAllSettled'
   }
]

*/
```

_Respuesta del método allSettled, cuando una promesa es rechazada o tuvo un error_

A diferencia de de **Promise.all(), Promise.allSettled()** devuelve un array de objetos.

```js
var promise1 = Promise.resolve(3);
var promise2 = new Promise((resolve, reject) =>
  setTimeout(() => resolve("Promesa Exitosa"), 1000)
);
var promises = [promise1, promise2];

Promise.all(promises).then((results) => console.log(results));

// Output: [3, 'Promesa Exitosa']
```

_Respuesta del método all, cuando todas las promesas fueron exitosas_

```js
var promise1 = Promise.resolve(3);
var promise2 = new Promise((resolve, reject) =>
  setTimeout(() => resolve("Promesa Exitosa"), 1000)
);
var promises = [promise1, promise2];

Promise.allSettled(promises).then((results) => console.log(results));

/* Output:

[
   {
      status: fulfilled,
      value: 3
   },
   {
      status: 'fulfilled',
      reason: 'Promesa Exitosa'
   }
]

*/
```

_Respuesta del método allSettled, cuando todas las promesas fueron exitosas_

Entonces en resumen, **Promise.allSettled()** devuelve un array de objetos con los estados de todas las promesas (resueltas y rechazadas) y sus respectivos valores o errores (según sea el caso).

#### Nullish Coalescing Operator (??)

_“Operador de fusión nulo”_

En realidad no supe como traducir esto de una forma comprensible 😢

Este operador se denota con dos símbolos de interrogación cerrados ??, su funcionamiento es similar al operador OR, salvo algunas cositas 😁

Me gustaría explicar estas cositas con ejemplos:

```js
const video = {
  title: "My awasome video",
  views: 0,
};

const views = video.views || "Views not available yet";
// views: 'Views not available yet
```

_Evaluando la condición con el operador OR (||)_
Si tenemos esta expresión, ¿Qué valor tendrá nuestra constante **views**?

Ya sabemos que nuestro video tiene 0 visitas 😥, pero queremos mostrar este valor en algún lado de la aplicación utilizando la constante **views**, lo que estaremos haciendo es mostrar ‘Views not available yet’ y no 0 precisamente porque el operador OR interpreta el cero como falso e inmediatamente se le asigna el valor por defecto.

Pero esto no está bueno, porque en realidad las views si las tenemos, en este caso es 0, de ser null o undefined si sería correcto asignar el valor por defecto.

```js
const video = {
  title: "My awasome video",
  views: 0,
};

const views = video.views ?? "Views not available yet";
// views: 0
```

_Evaluando la condición con el operador de fusión nulo (??)_

En resumen (||) es similar a (??), con la única excepción de que último solo contempla valores null o undefined para evaluar la siguiente expresión.

#### Optional Chaining (?.)

Utilizando en el mismo ejemplo del video, que pasa si queremos obtener el nombre del autor a partir del siguiente código:

```js
const video = {
  title: "My awasome video",
  views: 0,
  author: {
    name: "Diego",
  },
};

const authorName = video.author.name || "Unknown";
// authorName: 'Diego'

const video2 = {
  title: "My awasome video",
  views: 0,
};

const authorName2 = video2.author.name || "Unknown";
// Output: Uncaught TypeError: Cannot read property 'name' of undefined
```

Como verán en **authorName** logramos obtener el nombre del autor del video sin problemas, pero en **authorName2** obtenemos un error, esto se debe a que la propiedad **author** no existe en el objeto **video2**, debemos verificar si existe antes de intentar recuperarla, una de las formas que teníamos de hacer esto eran las siguientes:

```js
const video = {
  title: "My awesome video",
  views: 0,
};

const authorName = (video.author || {}).name || "Unknown";
// authorName: 'Unknown'

// OR

const authorName = (video.author && video.author.name) || "Unknown";
// authorName: 'Unknown'
```

_Varias alternativas de acceder de manera segura al nombre del autor_
Estas son solo alguna de las formas que tenemos para acceder a propiedades de objeto de manera segura, y las expresiones pueden llegar a ser mucho más extensas si tenemos muchos subniveles.

Para solucionar esto llegaron los “Encadenamientos Opcionales” denotados con el símbolo de interrogación cerrado (?) y ubicados antes de cada (.), usando este nuevo operador podemos simplificar nuestra expresión sin obtener errores, el ejemplo anterior quedaría de la siguiente forma:

```js
const video = {
  title: "My awesome video",
  views: 0,
};

const authorName = video.author?.name || "Unknown";
// authorName: 'Unknown'
```

Si alguna vez trabajaron con angular recordaran que esta característica estaba soportaba en el template de los componentes, pero no en nuestros archivos con typescript.

#### GlobalThis

Como sabemos JavaScript es un lenguaje multiplaforma, es muy versátil y nos permite platorma. Uno de los inconvenientes que teníamos era poder acceder al objeto “global” de nuestro entorno, y es que según en donde estemos ejecutando nuestro lenguaje la manera de acceder a este objeto global cambiaba.

Si quisiéramos obtener este objeto global independientemente del entorno, teníamos que realizar algo similar a esto:

```js
const globalObject = () => {
  if (typeof self !== "undefined") {
    return self;
  } // Web Workers
  if (typeof window !== "undefined") {
    return self;
  } // Web Workers
  if (typeof global !== "undefined") {
    return self;
  } // Web Workers
  throw new Error("can not find globalObject");
};
```

Ahora con el **globalThis** no hace falta, ya que podemos acceder desde cualquier entorno/plataforma con solo llamarlo.

#### String.prototype.matchAll

Este nuevo método nos devuelve un iterador con todos los resultados coincidentes en una cadena de texto usando una expresión regular.

```js
const myArrayOfPromises = [
  Promise.resolve(myPromise),
  Promise.reject(0),
  Promise.resolve(anotherPromise),
];

Promise.AllSettled(myArrayOfPromises).then((result) => {
  // Do your stuff
});
```

## ES12

[Repositorio de funcionalidades ya integradas por año en Javascript](https://github.com/tc39/ecma262)

#### Logical Assignment Operators (&&= ||= ??=)

_Operador de asignación lógica_

Los operadores lógicos `&&`, `||` y `??` ahora también pueden usarse para asignar valores de una forma más sencilla y corta. Perfecto para asignar valores por defecto a variables.

```js
// Si x es falsy, se le asigna y
x ||= y;
// Equivale a...
x || (x = y);

// Si x es truthy, se le asigna y
x &&= y;
// Equivale a...
x && (x = y);

// Si x es null o undefined, se le asigna y
x ??= y;
// Equivale a...
x ?? (x = y);
```

Hay que tener en cuenta que en estas asignaciones, además, entra el juego la evaluación short-circuit. Esto quiere decir que estas asignaciones lógicas se evaluan de izquierda a derecha. **Si una expresión lógica no se cumple, no se evalúa la siguiente.**

Esto es importante para no cometer errores:

```js
// este nuevo tipo de asignación con &&
x &&= y;
// ✅ es equivalente a...
x && (x = y);
// ❌ NO es equivalente a...
x = x && y;
// ya que la asignación ocurre siempre independientemente de la evaluación
```

#### Numeric Separator

Leer algunas cifras en JavaScript puede ser una tarea difícil. Para solucionar esto, el nuevo separador numérico \_ te permite identificar de manera más sencilla cualquier número.

```js
// Es difícil saber qué cifra representa
1000000000;
19436871.42;

// ¡Con Numeric Separator es más fácil!
1_000_000_000; // Ah, es mil millones
100_000_000; // Y esto es cien millones
19_436_871.42; // ¡De un vistazo!
```

#### Promise.any

¿Alguna vez has querido esperar una lista de promesas y que, al resolverse correctamente una cualquiera, continuar con la ejecución de tu código? Pues para eso se incorpora **Promise.any().**

```js
const promises = [
  fetch("/from-external-api"),
  fetch("/from-memory"),
  fetch("/from-new-api"),
];

try {
  // espera a la primera respuesta correcta que termine
  const first = await Promise.any(promises);
  // La más rápida fue la de memoria
  console.log(first); // respuesta desde 'from-memory'
} catch (error) {
  // ¡Todas las promesas han fallado!
  console.assert(error instanceof AggregateError);
  // Log the rejection values:
  console.log(error.errors);
  // → [
  //     <TypeError: Failed to fetch /from-external-api>,
  //     <TypeError: Failed to fetch /from-memory>,
  //     <TypeError: Failed to fetch /from-new-api>
  //   ]
}
```

#### AggregateError

Como has podido ver en el ejemplo anterior, ahora cuando la promesa falla, se devuelve una instancia de `AggregateError`. Este error es una instancia de `Error` y tiene una propiedad llamada `errors` que contiene una lista de errores para cada promesa que falló.

##### - La diferencia con Promise.race…

`Promise.race` y `Promise.any` son muy similares. La diferencia es que `Promise.race` se resuelve cuando cualquier promesa ha sido resuelta o rechazada. En cambio `Promise.any` ignora las promesas que son rechazadas y sólo se resuelve cuando se resuelve la primera… o se rechaza cuando todas las promesas se han rechazado.

##### - La tabla de diferencias de Promise

Para que lo veas más claro, he preparado una pequeña tabla para diferenciar los diferentes métodos de Promise a la hora de trabajar con un array de promesas, para que eligas la que más encaje con tu caso de uso.

| Método             | Descripción                                      | Añadida en... |
| ------------------ | ------------------------------------------------ | ------------- |
| Promise.allSettled | Espera a todas las promesas se resuelvan o no    | ES2020        |
| Promise.all        | Se para cuando una promesa es rechazada          | ES2015        |
| Promise.race       | Se para cuando una promesa es rechaza o resuelta | ES2015        |
| Promise.any        | Se para cuando una promesa es resuelta           | ES2021        |

#### Método .replaceAll()

Hasta ahora, reemplazar todas las instancias de una cadena de texto en una cadena de texto te obligaba a usar `Regex` ya que `replace`, si le pasabas un string, lo que hacía era sólo reemplazar la primera instancia encontrada.

```js
// ¡Quiero cambiar las manzanas por bananas!
"🍏🍏🍋🍋🍊🍊".replace("🍏", "🍌");
// Pero qué...
// -> '🍌🍏🍋🍋🍊🍊'

// ¡Tienes que usar Regex para conseguirlo!
"🍏🍏🍋🍋🍊🍊".replace(/🍏/g, "🍌");

// ¡Hasta ahora! ¡Hola replaceAll!
"🍏🍏🍋🍋🍊🍊".replaceAll("🍏", "🍌");
```

`replaceAll` queda mucho más legible en nuestro código y hace justo lo que esperaba: cambiar todas las instancias de una cadena de texto en una cadena de texto.

Podemos asi obviar la expresión regular que permitía simular este comportamiento mediante `.replace()`, integrada por defecto en el nuevo `.replaceAll()`.

#### Métodos de clase privados

A los métodos constructores, accesorios, estáticos y prototípicos de las clases se unen los métodos privados, que prefijándolos con una almohadilla verán su alcance limitado a la clase donde están definidos.

En caso de tratar de accederlos, obtendremos un valor undefined con su correspondiente excepción de tipo:

```js
class Invoice {
  /* ... */

  #addDiscount(val) {
    this.subtotal -= val;
  }
}

const invoice = new Invoice();
invoice.addDiscount(100); // TypeError: invoice.addDiscount is not a function
```

#### Getters y setters privados

Los métodos de acceso nos permitían declarar, a través de la sintaxis `get nombrePropiedad()` y `set nombrePropiedad()`, métodos en una clase con un comportamiento de propiedad a efectos externos:

```js
class Invoice {
  /* ... */

  get totalInvoice() {
    return (this.cost + this.benefit) * this.tax;
  }

  set tax(value) {
    this.tax = value;
  }
}

const invoice = new Invoice();
invoice.tax = 0.21; // manipularía el valor de la propiedad en la clase
invoice.totalInvoice; // retornaría el sumatorio que proceda
```

La novedad de `ES12` reside en **limitar el acceso a cualquier método accesorio** al prefijarlo con una almohadilla:

```js
class Invoice {
  /* ... */

  get #benefit() {
    return 10;
  }
}

const invoice = new Invoice();
invoice.benefit; // undefined
```

#### WeakRef

`WeakRef` te permite crear una referencia débil a un objeto para no prevenir que se destruya por el Garbage Collector de JavaScript. ¿Por qué? Pues por qué cuando creamos un objeto, especialmente si son grandes, estos no son automáticamente destruidos por el Garbage Collector si existe una referencia a ellos.

Con el método `deref` de `WeakRef`, podemos acceder a la referencia del objeto. Si la referencia al objeto ha sido eliminada, se devuelve `undefined`.

```js
// Al crear un objeto...
let coords = { x: 13, y: 72 };
// Mientras tengas acceso a él directamente,
// el objeto no será liberado de memoria
// por el Garbage Collector

// Ahora podemos crear una referencia débil al objeto
const weakCoords = new WeakRef(coords);

// Recuperamos las propiedades del elemento
const ref = weakCoords.deref();
if (ref) {
  console.log("Todavía tenemos acceso a las coordenadas");
  ref.x; // -> 13
} else {
  // ref es `undefined`
  console.log("La referencia ha sido eliminada");
}
```

Una cosa que debes tener en cuenta con `WeakRef` es que… seguramente es **mejor si no lo usas**. Esta funcionalidad está pensado para casos muy específicos que, en general, acabarán en librerías y frameworks. **Está bien que conozcas su existencia pero los casos de uso son muy limitados.** La recolección de basura en JavaScript puede variar mucho dependiendo del navegador, entorno y especificaciones del sistema.
[Link](https://cosasdigitales.com/articulos-diseno-web/es2021-es12-novedades-de-la-ultima-version-de-javascript/)

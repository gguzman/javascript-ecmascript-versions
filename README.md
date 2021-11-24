# Novedades en JavaScript: Repaso a todas ellas, desde la versión ES5 hasta la ES10

JavaScript es un lenguaje ligero e interpretado, dialecto del estándar ECMAScript, orientado a objetos con funciones de primera clase. Se utiliza principalmente en su forma del lado del cliente, implementando como parte de un navegador web permitiendo mejoras en la interfaz de usuario y páginas web dinámicas.

Actualmente el estándar ECMAScript, se encuentra en la versión ECMAScript 2019. A partir de las versiones ES5 y ES6 agregaron cambios significativos al lenguaje. Veremos algunos de ellos en este tutorial hasta la actual versión ES10.

Versión ES5 y ES6
Función Arrow

Para crear un código más limpio y claro. Veamos un ejemplo:

// ES5
// Imaginemos una variable data que incluye un array de objetos
var data = [{...}, {...}, {...}, ...];
data.forEach(function(elem){
// Tratamos el elemento
console.log(elem)
});
En la versión ES6 se vería de la siguiente manera el código anterior:

//ES6
var data = [{...}, {...}, {...}, ...];
data.forEach(elem => {
console.log(elem);
});
Clases

Ahora JavaScript tendrá clases con todo lo que conlleva, como por ejemplo, la herencia. Son muy parecidas a las funciones constructoras de objetos que realizábamos en el estándar anterior.

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
This

La variable this anteriormente teníamos que cachearla en otra variable ya que solo hace referencia al contexto en el que nos encontremos. Por ejemplo, en el siguiente código si no hacemos var that = this dentro de la función document.addEventListener, this haría referencia a la función que pasamos por Callback y no podríamos llamar a foo().

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
La función Arrow en la versión ES6 es más sencilla y visual:

//ES6
var obj = {
foo : function() {...},
bar : function() {
document.addEventListener("click", (e) => this.foo());
}
}
Let y Const

Ahora podemos declarar variables con let en lugar de var si no queremos que sean accesibles más allá de un ámbito. Por ejemplo:

//ES6
(function() {
if(true) {
let x = "hola mundo";
}
console.log(x);
//Da error, porque "x" ha sido definida dentro del "if"
})();
Template Strings

Con ES6 podemos interpolar Strings de una forma más sencilla que como estábamos haciendo hasta ahora. Por ejemplo:

//ES6
let nombre1 = "JavaScript";
let nombre2 = "awesome";
console.log(‘Sólo quiero decir que ${nombre1} is ${nombre2’);
Destructuring

Tenemos nuevas formas de asignar valores a Arrays y a Objetos. Veamos unos ejemplos:

var [a, b] = ["Buenos", "días"];
console.log(a); // "Buenos"
console.log(b); // "días"

var obj = { nombre: "Pepito", apellido: "Perez" };
var { nombre, apellido } = obj;
console.log(nombre); // "Pepito"
Valores por defecto

Otra de sus novedades es asignar valores por defecto a sus variables, que se pasan por parámetros en las funciones. Antes teníamos que comprobar si la variable ya tenía un valor. Ahora con ES6 se la podremos asignar según creemos la función:

//ES6
function(valor = "foo") {...};
Módulos

A esto lo llamo un browserify nativo. Ahora JavaScript se empieza a parecer a lenguajes como Python o Ruby. Llamamos a las funciones desde los propios Scripts, sin tener que importarlos en el HTML, si usamos JavaScript en el navegador.

//File: lib/person.js
module "person" {
export function hello(nombre) {
return nombre;
}
}
También se pueden exportar de esta manera:

export function hello(nombre) {...};
Y desde otro fichero:

//File: app.js
import { hello } from "person";
var app = {
foo: function() {
hello("Pepe");
}
}
export app;
Versión ES7
Array.prototype.includes(var)

Comprueba si un array contiene el valor pasado por parámetro. Básicamente, funciona igual que la función String.prototype.includes(var) para cadenas de texto (tratada en este post), pero para arrays. Con esta función ya no tendremos que utilizar el indexOf() para comprobar si un determinado valor está en un array.

const array = [1, ‘string’, true, 33];
console.log(array.includes(‘string’)); //true
console.log(array.includes(2)); //false
Operador de exponenciación ()\*\*

Este operador nos permite calcular la potencia de número. Le indicamos el número base y el exponente y nos hará el cálculo elevando el número base al exponente. Anteriormente, esto mismo, se podía hacer con la función Math.pow($base, $exponente), pero ahora no es necesario utilizarla gracias al operador \*\*.

const base = 3;
const exponente = 10;
console.log(base \*\* exponente);
console.log(Math.pow(base, exponente));
Ambos ejemplos de código anteriores se verían de la siguiente forma:

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_1.jpg

Versión ES8
Funciones asíncronas

La novedad más importante de esta versión son las funciones asíncronas, que devuelven promesas y se tienen que declarar con la keyword asinc delante de la declaración de la función. Solamente dentro de estas funciones podemos usar await e indicará que se detenga hasta que no esté resuelta la promesa de la función y cuando lo esté continuará con la ejecución normal. Utilizando async/await, se simplificará todo mucho mucho más pudiendo ejecutar código asíncrono como si fuese síncrono.

const base = 3;
const exponente = 10;
console.log(base \*\* exponente);
console.log(Math.pow(base, exponente));
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_2.jpg

Vamos a usar el paquete node-fetch, el cual nos permitirá usar la función fetch en Node.js, que es el entorno donde estamos ejecutando el código en Repl.it. Si lo estas ejecutando en tu local en un navegador directamente, sin Node.js, no te hará falta instalar el paquete, ya que la función fetch es una función nativa de JS.

Object.entries(obj)

Es un método añadido a Object que recibe como parámetro un objeto y lo que nos devuelve es un array que contiene tantos arrays como propiedades tenga el objeto con la clave y el valor de las propiedades.

const obj = { test: 1, foo: true, string: 'nombre'}
console.log(Object.entries(obj));
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_3.jpg

Object.values(obj)

Este es otro método añadido a Object. Como el anterior, también recibe un objeto como parámetro y lo que nos devuelve son los valores de las propiedades del objeto pasado. Ejemplo:

const obj = { test: 1, foo: true, string: 'nombre'}
console.log(Object.values(obj));
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_4.jpg

string.padStart(num, string)

padStart nos permite rellenar una cadena de texto desde el inicio de ésta hasta la longitud que hayamos indicado con los caracteres que queramos. Ejemplo:

console.log("string".padStart(10));
console.log("string".padStart(10, "abc"));
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_5.jpg

string.padEnd(num, string)

padEnd funciona igual que el anterior, pero en vez de rellenarlos por el principio de la cadena, lo rellena por el final de la cadena (último carácter).

console.log("string".padEnd(10));
// "string "
console.log("string".padEnd(10, "abc"));
// stringabca
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_6.jpg

object.getOwnPropertyDescriptors()

El método Object.getOwnPropertyDescriptors() devuelve la descripción de las propiedades del objeto pasado por parámetro.

const obj = {
test: 1,
foo: true,
string: 'nombre'
}
console.log(Object.getOwnPropertyDescriptors(obj))
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_7.jpg

Versión ES9
rest/spread properties

Es similar a lo que se puede hacer con los parámetros de las funciones y los arrays desde ES6 pero con propiedades de objetos.

const obj = {
name: 'John',
age: '32',
city: 'New York',
address: 'Address...'
}
// Rest
const {name, age, ...rest} = obj;
console.log(name, age, rest); // John 32 { city: 'New York', address: 'Address...' }
// Spread
const newObj = {name, job: 'Developer' , ...rest};
console.log(newObj);
const copyObj = { ...newObj };
console.log(copyObj, newObj);
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_8.jpg

promise: finally()

Es una función introducida en las promesas que se ejecutará siempre al finalizar la promesa, es decir, se ejecutará tanto si la promesa se ejecuta con éxito o es rechazada. Si lo has utilizado alguna vez y lo recuerdas, vendría a ser como él always del Ajax de jQuery.

Por tanto, ahora tendríamos tres posibles funciones callback para las promesas que serían .then(), .catch() y .finally().

const fetch = require('node-fetch');

// Promise: finally()
fetch('https://jsonplaceholder.typicode.com/todos/1')
.then(response => response.json())
.then(json => console.log(json))
.catch(error => console.log(error))
.finally(() => console.log('Esto se mostrará siempre!'));
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_9.jpg

Iteración asíncrona

Se ha introducido el await para bucles for, lo cual permite iterar sobre iterables asíncronos(promesas). Se tiene que utilizar dentro de funciones asíncronas como cualquier await. El bucle quedaría así:

for await (const variable of iterable) {
...
}
Ejemplo:

var asyncIterable = {
[Symbol.asyncIterator]() {
return {
i: 0,
next() {
if (this.i < 3) {
return Promise.resolve({ value: this.i++, done: false });
}

       return Promise.resolve({ done: true });
     }

};
}
};

(async function() {
for await (let num of asyncIterable) {
console.log(num);
}
})();
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_10.jpg

Cambios en RegExp

Se puede dar un nombre a los grupos de captura para referirse a ciertas partes de una cadena y que de esta manera que más claro. Por ejemplo:

let {groups: {one, two}} = /^(?<one>._):(?<two>._)$/u.exec('foo:bar');
console.log(`one: ${one}, two: ${two}`);
https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_11.jpg

Mira detrás de las afirmaciones

Hay dos versiones para mirar detrás de las afirmaciones: positiva y negativa.

Positivo(?<=...)

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_12.jpg

Negativo(?<!...)

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_13.jpg

RegExp Unicode Property Escapes

Ahora podemos buscar caracteres mencionando su propiedad Unicode dentro /p{}

https://www.imaginaformacion.com/tutoriales/tutorial_25_imagen_14.jpg

Versión ES10
Array.flat()

Método crea una nueva matriz con todos los elementos de la submatriz concatenados en ella recursivamente hasta la profundidad específica.

let array1 = [1, 2, [3, 4, ]];
array1.flat();
//[1, 2, 3, 4]

let array2 = [1, 2, [3, 4, [5, 6]]];
array2.flat();
//[1, 2, 3, 4, [5, 6]]

var array3 = [1, 2, [3, 4, [5, 6]]];
array3.flat(2);
//[1, 2, 3, 4, 5, 6]
Array.flatMap()

Método que usando una función de mapeo, mapea cada elemento, y luego aplana el resultado en una nueva matriz.

let array = [1, 2, 3, 4, 5];
array.map(x=> [x, x * 2]);

//[Array(2), Array(2), Array(2)]
//0: (2)[1, 2]
//1: (2)[2, 4]
//2: (2)[3, 6]

arr.flatMap(v => [v, v * 2])
//[1, 2, 2, 4, 3, 6, 4, 8, 5, 10]
Object.fromEntries()

Método transforma una lista de pares clave-valor en un objeto.

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
String.trimStart() & String.trimEnd()

El trimStart() es un método que elimina los espacios en blanco desde el principio de una cadena.

El trimEnd() es un método que elimina los espacios en blanco del final de una cadena.

Puedes pensar por qué otro método nuevo ya tiene dos métodos trimRight() y trimLeft() será un alias de los métodos nuevos.

Enlace de captura opcional

Permitir que los desarrolladores utilicen try/ catch sin crear un enlace no utilizado. Eres libre de seguir adelante haciendo uso del bloque catch sin un parámetro.

try{
throw new Error(“some error”);
} catch {
console.log(“no params for catch”);
}
Function.toString()

Método devuelve una cadena que representa el código fuente de la función. Más espacios blancos, las nuevas líneas y los comentarios se eliminarán cuando lo haga, se conservarán con el código fuente original.

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
Symbol.description

Propiedad de solo lectura es una cadena que devuelve la descripción opcional de los Symbol objetos.

var mySymbol = ‘My Symbol’
var symObj = Symbol(mySymbol)

console.log(symObj) //Symbol(My Symbol)
console.log(String(symObj) === ‘Symbol(${mySymbol})’) //true
console.log(symObj.description) //My Symbol
JSON.Stringify()

Este método convierte un objeto o valor de JavaScript en una cadena de texto JSON, opcionalmente reemplaza valores si se indica una función de reemplazo, o si se especifican las propiedades mediante un array de reemplazo.

console.log(JSON.stringify({ x: 5, y: 6 })); // expected output: "{"x":5,"y":6}" console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)])); // expected output: "[3,"false",false]" console.log(JSON.stringify({ x: [10, undefined, function(){}, Symbol('')] })); // expected output: "{"x":[10,null,null,null]}" console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5))); // expected output: ""2006-01-02T15:04:05.000Z""

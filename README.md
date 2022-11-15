# Ejercicios JavaScript

## Ejercicio 1
Dado un array de objetos, obtener el objeto con el id 3:

```javascript

const arrNames = [
  {id: 1, name: 'Pepe'},
  {id: 2, name: 'Juan'},
  {id: 3, name: 'Alba'},
  {id: 4, name: 'Toby'},
  {id: 5, name: 'Lala'}
] // Initial data

// Answer:

const findObjectById = (id, arr) => arr.find(x => x.id === id)
const result = findObjectById(3, arrNames)

console.log(result)

```

## Ejercicio 2
Dado un array de valores, devolver un array truthy (sin valores nulos, vacíos, no números, indefinidos o falsos)

```javascript

const arrDirty = [NaN, 0, 5, false, -1, '',undefined, 3, null, 'test'] // initial data

// Answer:
const returnTruthyArray = (arr) => arr.filter((x) => !!x);

const truthyArray = returnTruthyArray(arrDirty);

console.log(truthyArray);

```

## Ejercicio 3
Dado un array de ciudades, sacar todas las ciudades de España que no sean capitales

```javascript

const arrCities = [
  {city: 'Logroño', country: 'Spain', capital: false},
  {city: 'Paris', country: 'France', capital: true},
  {city: 'Madrid', country: 'Spain', capital: true},
  {city: 'Rome', country: 'Italy', capital: true},
  {city: 'Oslo', country: 'Norway', capital: true},
  {city: 'Jaén', country: 'Spain', capital: false}
] // Initial data

//Answer

const removeNonCapitalCity = (arr) => arr.filter((x) => x.capital);
console.log(removeNonCapitalCity(arrCities)); // 4 objects

```

## Ejercicio 4
Dado tres arrays de números, sacar en un nuevo array la intersección de estos.

```javascript

// Initial data
const arrNumber1 = [1,2,3];
const arrNumber2 = [1,2,3,4,5];
const arrNumber3 = [1,4,7,2];

// Answer
const findIntersection = (arr1, arr2, arr3) => {
  const newArray = arr1.filter(
    (x) => arr2.some(y => x === y) && arr3.some(y => x === y)
  )
  return newArray
};

console.log(findIntersection(arrNumber1, arrNumber2, arrNumber3));

```
## Ejercicio 5
Dado un array de ciudades, sacar en un nuevo array las ciudades no capitales con unos nuevos parámetros que sean city y isSpain. El valor de isSpain será un booleano indicando si es una ciudad de España.

```javascript
// initial data
const arrCities2 = [
  {city: 'Logroño', country: 'Spain', capital: false},
  {city: 'Bordeaux', country: 'France', capital: false},
  {city: 'Madrid', country: 'Spain', capital: true},
  {city: 'Florence', country: 'Italy', capital: true},
  {city: 'Oslo', country: 'Norway', capital: true},
  {city: 'Jaén', country: 'Spain', capital: false}
]

// answer
const cityIsSpain = (arr) => {
  const notCapital = arr.filter((x) => !x.capital && x.country === "Spain");
  const isSpain = notCapital.map(x => ({country: x.country, isSpain: true}) );

  return isSpain;
};

console.log(cityIsSpain(arrCities2)); // 2 objects
```

## Ejercicio 6
Crea una función que redondee un número float a un número específico de decimales.

La función debe tener dos parámetros: 
- Primer parámetro es un número float con x decimales
- Según parámetro es un int que indique el número de decimales al que redondear
- Evitar usar el método toFixed()

```javascript
const roundTo = (float, numOfDecimals) => {
  let num = "1";
  for (let i = 0; i < numOfDecimals; i++) {
    num += "0";
  }
  return Math.floor(float * Number(num)) / Number(num);
};

console.log(roundTo(5.34335, 2)); // 5.34
```

## Ejercicio 7
Crea una función que retorne los campos de un objeto que equivalgan a un valor “falsy” después de ser ejecutados por una función específica.
La fundación debe tener dos parámetros:
- Primer parámetro es un objeto con x número de campos y valores
- Segundo parametro es una funcion que retorne un booleano, que se tiene que aplicar al objeto del primer parámetro

```javascript
const test = { a: 1, b: "2", c: 3 };

const returnFalsyValues = (obj, fun = (x) => typeof x === "string") => {
  const falsyObject = {};
  for (let key in obj) {
    if (!fun(obj[key])) falsyObject[key] = obj[key]
  }

  return falsyObject
};
console.log(returnFalsyValues(test, x => typeof x === 'number')); // {b: "2"}
```

## Ejercicio 8
Crea una función que convierta un número de bytes en un formato con valores legibles ('B', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB')
La función debe tener 2 parámetros:
- Primer parámetro debe ser el número de bytes
- Segundo parámetro debe ser un número especificando la cantidad de dígitos a los que se debe truncar el resultado (esto se puede hacer con Number.prototype.toPrecision()). Por defecto, este parámetro debe de tener un valor de 3.

```javascript
const fromBytesToFormattedSizeUnits = (bytes, decimals = 3) => {
  const division = 1000;
  const sizes = ["Bytes", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB"];
  const isNegative = bytes.toString()[0] === "-";
  const num = isNegative
    ? Number(bytes.toString().slice(1, bytes.toString().length))
    : bytes;

  const i = Math.floor(Math.log(num) / Math.log(division));

  return `${isNegative ? "-" : ""}${parseFloat(
    (num / Math.pow(division, i)).toPrecision(decimals)
  )} ${sizes[i]}`;
};

// Not especially proud of this one ... Need feedback
```

## Ejercicio 9
Crea una función que a partir de un objeto de entrada, retorne un objeto asegurándose que las claves del objeto estén en lowercase.
La función debe tener un objeto como único parámetro.

```javascript
// Initial data
const myObject = { NamE: 'Charles', ADDress: 'Home Street' };

// Answer
const toLowercaseKeys = (obj) => {
  const lowercaseObject = {}
  for (let key in obj) {
    lowercaseObject[key.toLowerCase()] = obj[key]
  }
  return lowercaseObject
}

console.log(toLowercaseKeys(myObject))

```

## Ejercicio 10
Crea una función que elimine las etiquetas html o xml de un string.
La función debe tener un string como único parámetro.


```javascript
const test = '<div><span>lorem</span> <strong>ipsum</strong></div>';

// Answer(s)
// Solution 1
const removeHTMLTags1 = (str) => {
  const myDiv = document.createElement('div')
  myDiv.innerHTML = str
  return myDiv.textContent
}

console.log(removeHTMLTags1(test)) // lorem ipsum

// Solution 2
const removeHTMLTags2 = (str) => str.replace(/<[^>]*>/g, '')
console.log(removeHTMLTags2(test)) // lorem ipsum
```
## Ejercicio 11
Crea una función que tome un array como parametro y lo divida en arrays nuevos con tantos elementos como sean especificados.
La función debe tener dos parámetros:
- El primer parámetro es el array entero que se quiere dividir.
- El segundo parámetro es el número de elementos que deben tener los arrays en los que se divida el array original del primer parámetro.

```javascript
const testData = [1, 2, 3, 4, 5, 6, 7];

const splitArrayIntoChunks = (arr, numOfChunks) => {
  const finalArr = []
  for (let i = 0; i < arr.length; i += numOfChunks) {
    const chunk = arr.slice(i, i + numOfChunks);
    finalArr.push(chunk)
  }
  return finalArr
}

console.log(splitArrayIntoChunks(testData, 3))
```
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
## Ejercicio 5
## Ejercicio 6
## Ejercicio 7
## Ejercicio 8
## Ejercicio 9
## Ejercicio 10
## Ejercicio 11
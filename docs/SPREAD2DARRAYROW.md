# store.spread2dArrayRow(path, begin, rows, simpleInfilling, count)

| **Param** | **Description** | **type** | **default** |
| --- | --- | --- | --- |
| path  | The [path](https://github.com/Jimmy-YMJ/jsonstore-js#about-the-path-param) of array to spread. | `Array` or `String` or `Number` | `[]` |
| begin  | The begin index of array row. | `Number` | The length of the array referenced by `path`. |
| rows | The rows to fill the array. When the `rows` is an array, all the row of `rows` will be added to target array. When `rows` is a positive number, counts of `rows` `null`s will be added to array. When the `rows` is a negative number, counts of `rows` rows will be removed. | `Array` or `Number` | `undefined` |
| simpleInfilling  | Whether the param `rows` is a simple infilling. When it's true, all items of new added will be filled with `rows`. | `Boolean` | `false` |
| count  | The count of rows to spread when `simpleInfilling` is `true`. | `Number` | `1` |

This method returns the store itself.

## Examples
```javascript
var JSONStore = require('jsonstore-js'),
    storeData = [
        ['a', 'b'],
        ['c', 'd']
    ],
    createStore = function(){
        return new JSONStore({store: storeData});
    };
    
var store = createStore();
store.spread2dArrayRow([], 1, [['e', 'f'], ['g', 'h']]);
console.log(store.get());
/**
* output:
* [
*   ['a', 'b'],
*   ['e', 'f'],
*   ['g', 'h'],
*   ['c', 'd']
* ]
*/

var store = createStore();
store.spread2dArrayRow([], undefined, [['e', 'f'], ['g', 'h']]);
console.log(store.get());
/**
* output:
* [
*   ['a', 'b'],
*   ['c', 'd'],
*   ['e', 'f'],
*   ['g', 'h']
* ]
*/

var store = createStore();
store.spread2dArrayRow([], undefined, 2);
console.log(store.get());
/**
* output:
* [
*   ['a', 'b'],
*   ['c', 'd'],
*   [null, null],
*   [null, null]
* ]
*/

var store = createStore();
store.spread2dArrayRow([], 0, -1);
console.log(store.get());
/**
* output:
* [
*   ['c', 'd']
* ]
*/

var store = createStore();
store.spread2dArrayCol([], 2, 'foo', true, 2);
console.log(store.get());
/**
* output:
* [
*   ['a', 'b'],
*   ['c', 'd'],
*   ['foo', 'foo'],
*   ['foo', 'foo']
* ]
*/
```

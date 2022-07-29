# Javascript

- Scripts can be placed in the <body>, or in the <head> section of an HTML page, or in both.
- Scripts can also be placed in external files
  - JavaScript files have the file extension .js.
  - To use an external script, put the name of the script file in the src (source) attribute of a `<script>` tag:
  - `<script src="myScript.js"></script>`
  -

## JS extension

## Basic

- Array
- Object
- Hash
- Set
- String
- Linked-list
- List

### Array

- new/create  
  - const cars = ["Saab", "TSLA", "BMW"]
  - const cars = new Array("Saab", "TSLA") // no need to use `new Array()`
  - const cars = []
    - cars[0] = "TSLA"
    - cars[1] = "BMW"
  - const points = new Array(40);    // points.length = 40
  - const points = new Array(40, 1); // points = [40, 1]
  - Array.isArray(points);           // true, ES-5 (2009)
  - points instanceof Array;         // true
  -  
  -
- Arrays are Objects
  - `typeof(cars)` // `object`
  - Arrays use numbers to access its "elements", eg: `cars[1]`
  - Array element can be object

- Array Properties
  - `array.length`
    - cars.length       // length property

- Array Methods
  - `sort()`

    ```
    [3, 1, 2].sort()        // [1,2,3]
    ['aa', 'a', 'b'].sort() // ['a', 'aa', 'b']
    [10, 2, 5].sort         // [10,2,5] 

    // Sort with acsending
    points = [10,2,5]
    points.sort(function(a,b){ return a-b });  
    ```

    - `the compare function`
      - function(a, b) {return a-b}
      - sorting based on the returned value (neg, zero, posi)
        - negative: sort `a` before `b` (smaller one first)
        - positive: sort `b` before `a`
        - zero: no change of `a` `b` position

  - max/min value

    ```
    Math.max.apply(null,[1,2,4])    // 4  
    Math.min.apply(null, [1,2,4])   // 1
    ```

  - `reverse()`

    ```
    [1,2,3].reverse()       // [3,2,1]
    ```

  - `toString()`: coverts an array to string of comma separated array values

    ```
    cars = ["Tsla", "BMW", "Ford"]
    cars.toString();   // 'Tsla,BMW,Ford' 
    ```

  - `join()`: join all array elements into a string
    - cars.join()       // 'Tsla,BMW,Ford'
    - cars.join("#")    // 'Tsla#BMW#Ford'
  
  - `pop()` & `push()`
    - x = cars.pop()     // 'Ford`
    - cars.push("XYZ")   // ['Tsla', 'BMW', 'XYZ']
  
  - `shift()` & `unshift()`
    - y = cars.shift      // shift left => "TSLA"
    - cars.unshift("111") // ["111", "BMW", "XYZ"]
  
  - `delete`
    - delete cars[1];      // cars[1] = "undefined"
  
  - `concat()`
    - arr1 = ["A1", "A2"],  arr2 = ["B1", "B2"], arr3 = [31, 32]
    - c1 = arr1.concat(arr2);        // ['A1', 'A2', 'B1', 'B2']
    - c2 = arr1.concat(arr2, arr3);  // ['A1', 'A2', 'B1', 'B2', 31, 32]
  
  - `splice()` & `slice()`

    ```
    arr = [1,2,3,4]
    arr.splice(2, 0, 10, 11);  // add elements [ 1, 2, 10, 11, 3, 4 ], 
    ```
    - 1st param (2) defines the position where new elements should be added
    - 2nd param (0) defines how many elements should be removed
    - The rest of params (10, 11) define the new elements to be added

    - Use `splice()` to remove element

      ```
      arr.splice(0,1);
      ```

    - `slice()`  method slices out a piece of an array into a new array

    ```
    items = [0, 1, 2, 3, 4]
    cut = items.slice(1)   // [1,2,3,4], till the end of the array 
    cut = items.slice(1,3) // [1,2]
    ```

- Array looping/iteration
  - `forEach(), map(), filter(), reduce()`
  - `forEach()`

      ```
      const nums = [4, 9  16, 25];
      let txt = "";
      nums.forEach(myFunction);
      function myFunction(value, index, array){
        txt += value + "<br>;
      } 
      ```
  
    - Note the function takes 3 arguments: value, index, array itself.
    - It can also be written  as

      ```
      function myFunction(value) {
        txt += value + "<br>";
      } 
      ```
  
  - `map()`
    - create a new array by performing a function on each element of the original array
    - does not execute function for array elements without values
    - nums.map(myFunction)
    - `function myFunction(value, index, array) { return value*2}`
  
  - `filter()`
    - create a new array with elements that passes a test
    - eg: filter elements larger than 8

      ```
        const nums = [1, 2, 20, 12];
        const over8 = nums.filter(myFunc);
        function myFunc(value, index, array) {
          return value > 8;
        }
      ```

  - `reduce()`
    - runs a function on each element to produce (reduce it to) a single value.
    - works from left-to-right in the array. See also `reduceRight()`
    - does not reduce the original array
    - eg: sum, the inital valule = 100

    ```
      const nums = [1, 2, 20, 12];
      const total = nums.reduce(sum, 100);
      function sum(total, value, index, array) {
        return total + value; 
      }
    ```

    - the function take `4` arguments
      - The total (the inital value/ previous returned value )
      - The item value
      - The item index
      - The array itself
  
  - `reduceRight()`
    - similar to `reduce()`
    - works from `right-to-left` in the array
  
  - `every()`
    - check if all the elements pass a test
    - eg:

    ```
    const nums = [-2, 2, 4];
    nums.every(function(value, index, array) {value > 0 })
    ```

  - `some()`
    - check if some array pass a test
    -
  - `indexOf()`
    - This method searches an array for an element value and returns its poistion.
    - `[2, 3, 2, 3].indexOf(3)`     // 1
    - `array.indexOf(item, start)`  // start is option  
    - Array.indexOf() returns -1 if the item is not found.
  
  - `lastIndexOf()`
    - Array.lastIndexOf() is the same as Array.indexOf(), but returns the position of the last occurrence of the specified element.
    - `[2,4,2,4].lastIndexOf(4)` // 3

  - `find()`
    - it returns the first value that passes a test, or undefined.
    - `[2,4,2,4].find(function(value, index, array) {return value>=3})` // 4

  - `findIndex()`
    - it returns the index of the first value that passes a test, or -1.
    - `[2,4,2,4].findIndex(function(value, index, array) {return value>=3})` // 1

  - `includes()`
    - `["Banana", "Orange"].includes("Orange")` // true
  
  - Looping using `for`  

    ```
    cars = ["TSLA", "BMW", "FORD"];
    for (i=0; i< cars.length; i++) {
        console.log("car = " + cars[i])
    }
    ```

- Arrays are Not Constants
  - `const` defines a constant reference to an array

  ```
  // You can create a constant array:
  const cars = ["Saab", "Volvo", "BMW"];

  // You can change an element:
  cars[0] = "Toyota";

  // You can add an element:
  cars.push("Audi");
  ```

### Object

- Object use "names" to access its "members"
- eg: `const person = {firstName:"John", lastName:"Doe", age:46};`
- `person.firstName` // `John`

### Keywords

- `var` - Declares a variable
- `let` - Declares a block variable
- `const` - Declares a block constant
- `if` - Marks a block of statements to be executed on a condition
- `switch` - Marks a block of statements to be executed in different cases
- `for` - Marks a block of statements to be executed in a loop
- `function` - Declares a function
- `return` - Exits a function
- `try` - Implements error handling to a block of statements

### Syntax

- Fixed values are called `Literals`
  - numbers, with or without decimals
    - eg: `10.40`, `1001`
  - Strings, text written within single or double quotes
    - eg: `"John"`, `'John'`
- Varaiable values are called `Variables`.
  - used to store data values
  - keywords to declear variables: `var`, `let`, `const`, or `nothing`

-

### - `function`

  ```
    function demo(a, b) {
      return a+b; 
    } 
  ```

### - "functions"

- console.log("hello")
- document.getElementById("demo")
  - document.getElementById("demo").innerHTML = "Hello JavaScript";

- JS can display data in different ways:
  - Writing into an HTML element, using innerHTML.
  - Writing into the HTML output using document.write().
  - Writing into an alert box, using window.alert().
  - Writing into the browser console, using console.log().

## react

## type-script

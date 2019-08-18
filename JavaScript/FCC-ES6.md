# ES6

Not all browsers support ES6 features. If you use ES6 in your own projects, you may need to use a program (transpiler) to convert your ES6 code into ES5 until browsers support ES6.

1. Explore Differences Between the var and let Keywords
    * Variables declared with var can be overrriden.
    * If we use let it will throw an error if already declared variable is being declared again wintin the same block.
    * "use strict" can be used to specify that the code should be executed in strict mode.

    ```javascript
    let catName;
    let quote;
    function catTalk() {
        "use strict";
        catName = "Oliver";
        quote = catName + " says Meow!";

    }
    catTalk();
    ```

1. Compare Scopes of the var and let Keywords
    * let has block level scope whereas var is hoisted to the function start.
    * declaring same variable with let will work for inner blocks and the inner variable scope is that block alone.

    ```javascript
    function checkScope() {
    "use strict";
        let i = "function scope";
        if (true) {
            let i = "block scope";
            console.log("Block scope i is: ", i);
        }
        console.log("Function scope i is: ", i);
        return i;
    }
    ```

1. Declare a Read-Only Variable with the const Keyword

    ```javascript
    function printManyTimes(str) {
        "use strict";

        // change code below this line

        const SENTENCE = str + " is cool!";
        for(let i = 0; i < str.length; i+=2) {
            console.log(SENTENCE);
        }
    }
    printManyTimes("freeCodeCamp");
    ```

1. Mutate an Array Declared with const

    ```javascript
    const s = [5, 7, 2];
    function editInPlace() {
        "use strict";
        // change code below this line
        // s = [2, 5, 7]; <- this is invalid
        s[0] = 2;
        s[1] = 5;
        s[2] = 7;
        // change code above this line
    }
    editInPlace();
    ```

1. Prevent Object Mutation
    * Object.freeze will just ignore any mutation to object without an error.

    ```javascript
    function freezeObj() {
        "use strict";
        const MATH_CONSTANTS = {
            PI: 3.14
        };
        // change code below this line
        Object.freeze(MATH_CONSTANTS)
        // change code above this line
        try {
            MATH_CONSTANTS.PI = 99;
        } catch( ex ) {
            console.log(ex);
        }
        return MATH_CONSTANTS.PI;
    }
    const PI = freezeObj();
    ```

1. Use Arrow Functions to Write Concise Anonymous Functions

    ```javascript
    const magic = () => {
        "use strict";
        return new Date();
    };
    ```

1. Write Arrow Functions with Parameters

    ```javascript
    const myConcat = (arr1, arr2) => {
        "use strict";
        return arr1.concat(arr2);
    };
    // test your code
    console.log(myConcat([1, 2], [3, 4, 5]));
    ```

1. Write Higher Order Arrow Functions
    * filter and map

    ```javascript
    const realNumberArray = [4, 5.6, -9.8, 3.14, 42, 6, 8.34, -2];
    const squareList = (arr) => {
        "use strict";
        // change code below this line
        const squaredIntegers = arr.filter( (value) => Number.isInteger(value) && value >=0).map( (value) => Math.pow(value,2));
        // change code above this line
        return squaredIntegers;
    };
    // test your code
    const squaredIntegers = squareList(realNumberArray);
    console.log(squaredIntegers);
    ```

1. Set Default Parameters for Your Functions

    ```javascript
    const increment = (function() {
        "use strict";
        return function increment(number, value=1) {
            return number + value;
        };
    })();
    console.log(increment(5, 2)); // returns 7
    console.log(increment(5)); // returns 6
    ```

1. Use the Rest Operator with Function Parameters

    ```javascript
    const sum = (function() {
        "use strict";
        return function sum(...args) {
            return args.reduce((a, b) => a + b, 0);
        };
    })();
    console.log(sum(1, 2, 3)); // 6
    ```

1. Use the Spread Operator to Evaluate Arrays In-Place
    * Can be used to avoid loops for creating each argument for a function.
    * Spread operator unpacks all contents of an array into a comma-separated list

    ```javascript
    const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
    let arr2;
    (function() {
        "use strict";
        arr2 = [...arr1]; // change this line
    })();
    console.log(arr2);
    ```

1. Use Destructuring Assignment to Assign Variables from Objects
    * {Source: Destination, Source1: Destination1, ......}

    ```javascript
    const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54
    const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54
    const AVG_TEMPERATURES = {
        today: 77.5,
        tomorrow: 79
    };
    function getTempOfTmrw(avgTemperatures) {
        "use strict";
        // change code below this line
        const {tomorrow:tempOfTomorrow } = avgTemperatures; // change this line
        // change code above this line
        return tempOfTomorrow;
    }
    console.log(getTempOfTmrw(AVG_TEMPERATURES)); // should be 79
    ```

1. Use Destructuring Assignment to Assign Variables from Nested Objects

    ```javascript
    const LOCAL_FORECAST = {
        today: { min: 72, max: 83 },
        tomorrow: { min: 73.3, max: 84.6 }
    };
    function getMaxOfTmrw(forecast) {
        "use strict";
        // change code below this line
        const {tomorrow: { max: maxOfTomorrow } } =forecast ; // change this line
        // change code above this line
        return maxOfTomorrow;
    }
    console.log(getMaxOfTmrw(LOCAL_FORECAST)); // should be 84.6
    ```

1. Use Destructuring Assignment to Assign Variables from Arrays
    * Different from spreading is that we can map one prop to other

    ```javascript
    const [a, b] = [1, 2, 3, 4, 5, 6];
    console.log(a, b); // 1, 2
    const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
    console.log(a, b, c); // 1, 2, 5
    let a = 8, b = 6;
    (() => {
        "use strict";
        // change code below this line
        [a, b] = [b, a];
        // change code above this line
    })();
    console.log(a); // should be 6
    console.log(b); // should be 8
    ```

1. Use Destructuring Assignment with the Rest Operator to Reassign Array Elements

    ```javascript
    const source = [1,2,3,4,5,6,7,8,9,10];
    function removeFirstTwo(list) {
        "use strict";
        // change code below this line
        const [,,...arr] = list; // change this
        // change code above this line
        return arr;
    }
    const arr = removeFirstTwo(source);
    console.log(arr); // should be [3,4,5,6,7,8,9,10]
    console.log(source); // should be [1,2,3,4,5,6,7,8,9,10];
    ```

1. Use Destructuring Assignment to Pass an Object as a Function's Parameters

    ```javascript
    const stats = {
        max: 56.78,
        standard_deviation: 4.34,
        median: 34.54,
        mode: 23.87,
        min: -0.75,
        average: 35.85
    };
    const half = (function() {
    "use strict";
    return function half({ max, min}) {
        // use function argument destructuring
        return (max + min) / 2.0;
    };
    })();
    console.log(stats); // should be object
    console.log(half(stats)); // should be 28.015
    ```

1. Create Strings using Template Literals

    ```javascript
    const result = {
        success: ["max-length", "no-amd", "prefer-arrow-functions"],
        failure: ["no-var", "var-on-top", "linebreak"],
        skipped: ["id-blacklist", "no-dup-keys"]
    };
    function makeList(arr) {
    "use strict";
    // change code below this line
    const resultDisplayArray = [`<li class="text-warning">${arr[0]}</li>`,
                                `<li class="text-warning">${arr[1]}</li>`,
                                `<li class="text-warning">${arr[2]}</li>`];
    // change code above this line
    return resultDisplayArray;
    }
    const resultDisplayArray = makeList(result.failure);
    ```

1. Write Concise Object Literal Declarations Using Simple Fields

    ```javascript
    const createPerson = (name, age, gender) => {
        "use strict";
        // change code below this line
        return { name, age, gender};
        // change code above this line
    };
    console.log(createPerson("Zodiac Hasbro", 56, "male")); // returns a proper object
    ```

1. Write Concise Declarative Functions with ES6

    ```javascript
    // change code below this line
    const bicycle = {
        gear: 2,
        setGear(newGear) {
            "use strict";
            this.gear = newGear;
        }
    };
    // change code above this line
    bicycle.setGear(3);
    console.log(bicycle.gear);
    ```

1. Use class Syntax to Define a Constructor Function

    ```javascript
    function makeClass() {
        "use strict";
        /* Alter code below this line */
        class Vegetable {
            constructor(name){
            this.name = name;
            }
        }
        /* Alter code above this line */
        return Vegetable;
    }
    const Vegetable = makeClass();
    const carrot = new Vegetable('carrot');
    console.log(carrot.name); // => should be 'carrot'
    ```

1. Use getters and setters to Control Access to an Object

    ```javascript
    function makeClass() {
        "use strict";
        /* Alter code below this line */
        class Thermostat {
            constructor(fDegree){
            this._fDegree = fDegree;
            }
            get temperature(){
            return 5/9 * (this._fDegree - 32);
            }
            set temperature(cDegree){
            this._fDegree = cDegree * 9.0 / 5 + 32;
            }
        }
        /* Alter code above this line */
        return Thermostat;
    }
    const Thermostat = makeClass();
    const thermos = new Thermostat(76); // setting in Fahrenheit scale
    let temp = thermos.temperature; // 24.44 in C
    thermos.temperature = 26;
    temp = thermos.temperature; // 26 in C
    ```

1. Understand the Differences Between import and require
    * import isn't supported by browsers.
    * It doesn't import whole file like require() and saves time and memory.

    ```javascript
    import { capitalizeString } from "string_functions"
    "use strict";
    capitalizeString("hello!");
    ```

1. Use export to Reuse a Code Block

    ```javascript
    export { capitalizeString } //How to export functions.
    export const foo = "bar"; //How to export variables.
    export { capitalizeString, foo }
    "use strict";
    export const foo = "bar";
    export const bar = "foo";
    ```

1. Use * to Import Everything from a File

    ```javascript
    import * as stringUtil from "capitalize_strings";
    "use strict";
    ```

1. Create an Export Fallback with export default

    ```javascript
    "use strict";
    export default function subtract(x,y) {return x - y;}
    ```

1. Import a Default Export

    ```javascript
    import subtract from "math_functions"
    "use strict";
    subtract(7,4);
    ```

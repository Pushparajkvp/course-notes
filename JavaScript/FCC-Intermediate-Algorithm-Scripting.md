# Intermediate Algorithm Scripting

1. Sum All Numbers in a Range

    ```javascript
    function sumAll(arr) {
        var min = Math.min(...arr);
        var max = Math.max(...arr);
        var sum = 0;
        for(var i=min; i<=max; i++)
            sum+=i;
        return sum;
    }

    sumAll([1, 4]);
    ```

1. Diff Two Arrays

    ```javascript
    function diffArray(arr1, arr2) {
        return arr1.filter((value)=> arr2.indexOf(value)<0).concat(arr2.filter((value)=> arr1.indexOf(value)<0));
    }

    console.log(diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]));
    ```

1. Seek and Destroy

    ```javascript
    function destroyer(arr, ...arr2) {
        // Remove all the values
        return arr.filter((value) => arr2.indexOf(value)<0);
    }

    destroyer([1, 2, 3, 1, 2, 3], 2, 3);
    ```

1. Wherefore art thou

    ```javascript
    function whatIsInAName(collection, source) {
        // What's in a name?
        var arr = [];
        // Only change code below this line
        arr = collection.filter((obj)=> {
            for(var key in source){
            if(!(key in obj) || obj[key] !== source[key]){
                return false;
            }
            }
            return true;
        });
        // Only change code above this line
        return arr;
    }

    whatIsInAName([{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], { last: "Capulet" });
    ```

1. Spinal Tap Case

    ```javascript
    function spinalCase(str) {
        return str.replace(/([a-z])([A-Z])/g, '$1 $2').toLowerCase().replace(/\s+|_+/g,'-');
    }

    console.log(spinalCase('The_Andy_Griffith_Show'));
    ```

1. Pig Latin

    ```javascript
    function translatePigLatin(str) {
        let vowelRegex = /[aeiou]/g;

        if(str[0].match(vowelRegex)){
            return str + "way";
        }
        if(!str.match(vowelRegex)){
            return str + "ay";
        }
        let firstVowelIndex= str.indexOf(str.match(vowelRegex)[0]);
        return str.substr(firstVowelIndex,str.lenght) + str.substr(0,firstVowelIndex) + "ay";
    }

    console.log(translatePigLatin("glove"));
    ```

1. Search and Replace

    ```javascript
    function myReplace(str, before, after) {
        if(before[0] == before[0].toUpperCase())
            after = after[0].toUpperCase() + after.substr(1);
        else
            after = after[0].toLowerCase() + after.substr(1);
        return str.replace(before, after);
    }

    console.log(myReplace("He is Sleeping on the couch", "Sleeping", "sitting"));
    ```

1. DNA Pairing

    ```javascript
    function pairElement(str) {
        let result = [];
        str.split('').map( (char) => { 
            switch(char.toUpperCase()){
            case 'A': result.push(["A", "T"]); break;
            case 'T': result.push(["T", "A"]); break;
            case 'C': result.push(["C", "G"]); break;
            case 'G': result.push(["G", "C"]); break;
            }
        });
        return result;
    }

    console.log(pairElement("ATCGA"));
    ```

1. Missing letters

    ```javascript
    function fearNotLetter(str) {
        let missingCharacter = undefined;
        for(let i =1 ; i<str.length; i++){
            let prevCode = str[i-1].charCodeAt();
            let currentCode = str[i].charCodeAt();
            if(currentCode - prevCode != 1)
            missingCharacter = String.fromCharCode(currentCode-1);
        }
        return missingCharacter;
    }

    console.log(fearNotLetter("abce"));
    ```

1. Sorted Union

    ```javascript
    function uniteUnique(...arr) {
        let finalArray = [];
        arr.map((innerArray) => {
            innerArray.map((value)=> {
            if(finalArray.indexOf(value) < 0)
                finalArray.push(value)
            });
        });
        return finalArray;
    }

    console.log(uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]));
    ```

1. Convert HTML Entities

    ```javascript
    function convertHTML(str) {
        let characters = str.split('');
        for(let i=0; i<characters.length; i++){
            switch(characters[i]){
            case '&': characters[i]="&amp;"; break;
            case '<': characters[i]="&lt;"; break;
            case '>': characters[i]="&gt;"; break;
            case '"': characters[i]="&quot;"; break;
            case "'": characters[i]="&apos;"; break;
            }
        }
        return characters.join('');
    }

    console.log(convertHTML("Hamburgers < & Pizza < Tacos"));
    ```

1. Sum All Odd Fibonacci Numbers

    ```javascript
    function sumFibs(num) {
        let sum =0;
        let prev = 0;
        let current = 1;
        while(current<=num){
            if(current%2 ==1)
            sum+=current;
            current += prev;
            prev = current - prev;
        }
        return sum;
    }

    console.log(sumFibs(4000000));
    ```

1. Sum All Primes

    ```javascript
    function isPrime(num){
        for(let i=2; i<=num/2; i++){
            if(num%i==0)
            return false;
        }
        return true;
    }
    function sumPrimes(num) {
        let sum =0;
        for(let i=2; i<=num; i++){
            if(isPrime(i))
            sum+=i;
        }
        return sum;
    }

    console.log(sumPrimes(10));
    ```

1. Smallest Common Multiple

    ```javascript
    function gcd(a,b){
        if(b===0)
            return a;
        return gcd(b, a%b);
    }
    function lcm(a,b){
        return (a*b)/gcd(a,b);
    }
    function smallestCommons(arr) {
        let values = [];
        for(let i=Math.max(...arr); i>= Math.min(...arr); i--){
            values.push(i);
        }
        return values.reduce((v1, v2) => {
            return lcm(v1,v2);
        });
    }

    console.log(smallestCommons([1,5]));
    ```

1. Drop it

    ```javascript
    function dropElements(arr, func) {
        let newArr = [];
        for(let i=0; i<arr.length; i++){
            if(func(arr[i])){
            newArr = arr.slice(i);
            break;
            }
        }
        return newArr;
    }

    console.log(dropElements([0, 1, 0, 1], function(n) {return n === 1;}))
    ```

1. Steamroller

    ```javascript
    function flattenArray(arr, flatArray){
        for(let i=0; i<arr.length; i++){
            if(Array.isArray(arr[i])){
            flattenArray(arr[i],flatArray);
            }else{
            flatArray.push(arr[i]);
            }
        }
        }
        function steamrollArray(arr) {
        let flatArray = [];
        flattenArray(arr,flatArray);
        return flatArray;
    }

    console.log(steamrollArray([1, [2], [3, [[4]]]]));
    ```

1. Binary Agents

    ```javascript
    // Or parseInt(biString, 2) // String, base
    function binaryToDecimal(binary){
        let final = 0;
        let digits = binary.split('');
        let power = 0;
        for(let i=digits.length-1; i>=0; i--){
            final += Math.pow(2,power++) * parseInt(digits[i])
        }
        return final;
    }
    function binaryAgent(str) {
        let finalString = '';
        str.split(" ").map((binary) => {
            finalString += String.fromCharCode(binaryToDecimal(binary));
        });
        return finalString;
    }

    console.log(binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111"));
    ```

1. Everything Be True

    ```javascript
    function truthCheck(collection, pre) {
        for(let i=0; i<collection.length; i++){
            if(!collection[i][pre])
            return false;
        }
        return true;
    }

    truthCheck([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy", "sex": "male"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex");
    ```

1. Arguments Optional

    ```javascript
    function addTogether() {
        var checkIfNumber = function(arg){
            if(typeof arg !== 'number')
            return false;
            return true;
        }

        if(arguments.length == 2){
            if(checkIfNumber(arguments[0]), checkIfNumber(arguments[1])){
            return parseInt(arguments[0]) + parseInt(arguments[1]);
            }
            return undefined;
        }else if(arguments.length == 1){
            if(checkIfNumber(arguments[0])){
            let firstArg = arguments[0]
            return function(secondArg){
                if(checkIfNumber(secondArg)){
                return firstArg + secondArg;
                }
                return undefined;
            }
            }
            return undefined;
        }
        return false;
    }

    console.log(addTogether(2)(3));
    ```

1. Make a Person

    ```javascript
    var Person = function(firstAndLast) {
        // Complete the method below and implement the others similarly
        let arr = firstAndLast.split(/\s+/);
        var firstName = arr[0],lastName = arr[1];

        this.setFirstName = function(arg) {
            firstName = arg;
        }
        this.setLastName = function(arg) {
            lastName = arg;
        }
        this.setFullName = function(arg){
            let arr = arg.split(/\s+/);
            firstName = arr[0];
            lastName = arr[1];
        }
        this.getLastName = function() {
            return lastName;
        }

        this.getFirstName = function() {
            return firstName;
        }
        this.getFullName = function() {
            return firstName + " " + lastName;
        };
        return firstAndLast;
    };

    var bob = new Person('Bob Ross');
    bob.getFullName();
    ```

1. Map the Debris

    ```javascript
    function orbitalPeriod(arr) {
        var GM = 398600.4418;
        var earthRadius = 6367.4447;

        arr.map( (obj) => {
            let avgAlt = obj.avgAlt;
            let orbitalPeriod =Math.round(2*Math.PI*Math.sqrt(Math.pow(avgAlt+earthRadius ,3)/GM));
            delete obj.avgAlt;
            obj.orbitalPeriod = orbitalPeriod;
        });
        return arr;
    }

    console.log(orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]));
    ```

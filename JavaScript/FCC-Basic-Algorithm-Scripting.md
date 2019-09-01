# Basic Algorithm Scripting

1. Convert Celsius to Fahrenheit

    ```javascript
    function convertToF(celsius) {
        let fahrenheit= (celsius*9/5) + 32;
        return fahrenheit;
    }

    convertToF(30);
    ```

1. Reverse a String

    ```javascript
    function reverseString(str) {
        return str.split('').reverse().join('');
    }

    reverseString("hello");
    ```

1. Factorialize a Number

    ```javascript
    function factorialize(num) {
        if(num<1)
            return 1;
        return factorialize(num-1)*num;
    }

    factorialize(5);
    ```

1. Find the Longest Word in a String

    ```javascript
    function findLongestWordLength(str) {
        let max=0, words=str.split(' ');
        for(let i=0; i<words.length; i++){
            if(max < words[i].length)
            max = words[i].length;
        }
        return max;
    }

    findLongestWordLength("The quick brown fox jumped over the lazy dog");
    ```

1. Return Largest Numbers in Arrays

    ```javascript
    function largestOfFour(arr) {
        // You can do this!
        let finalArr = [];
        for(let i=0; i<arr.length; i++){
            let max = arr[i][0];
            for(let j=0; j<arr[i].length; j++){
            if(max < arr[i][j])
                max = arr[i][j];
            }
            finalArr.push(max);
        }
        return finalArr;
    }

    largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
    ```

1. Confirm the Ending

    ```javascript
    function confirmEnding(str, target) {
        return str.substring(str.length-target.length, str.length) == target ? true: false;
    }

    confirmEnding("Bastian", "n");
    ```

1. Repeat a String Repeat a String

    ```javascript
    function repeatStringNumTimes(str, num) {
        let final = "";
        while(num > 0 ){
            final += str;
            num--;
        }
        return final;
    }

    repeatStringNumTimes("abc", 3);
    ```

1. Truncate a String

    ```javascript
    function truncateString(str, num) {
    // Clear out that junk in your trunk
        if(str.length > num){
            return str.slice(0, num) + '...';
        }
        return str;
    }

    truncateString("A-tisket a-tasket A green and yellow basket", 8);
    ```

1. Finders Keepers

    ```javascript
    function findElement(arr, func) {
        for(let i=0; i<arr.length; i++){
            if(func(arr[i]))
            return arr[i];
        }
    }

    findElement([1, 2, 3, 4], num => num % 2 === 0);
    ```

1. Boo who

    ```javascript
    function booWho(bool) {
        // What is the new fad diet for ghost developers? The Boolean.
        return typeof(bool) == 'boolean'? true: false;
    }

    booWho(true);
    ```

1. Title Case a Sentence

    ```javascript
    String.prototype.replaceAt = function(index, character) {
        return this.substr(0, index) + character + this.substr(index + 1);
    }
    function titleCase(str) {
        let words = str.split(' ');
        let result = [];
        for(let i=0; i<words.length; i++){
            result.push(words[i].toLowerCase().replaceAt(0, words[i].charAt(0).toUpperCase()));
        }
        return result.join(' ');
    }

    titleCase("I'm a little tea pot");
    ```

1. Slice and Splice

    ```javascript
    function frankenSplice(arr1, arr2, n) {
        // It's alive. It's alive!
        let localArray = arr2.slice();
        localArray.splice(n, 0, ...arr1);
        return localArray;
    }

    console.log(frankenSplice([1, 2, 3], [4, 5, 6], 1));
    ```

1. Falsy Bouncer

    ```javascript
    function bouncer(arr) {
        // Don't show a false ID to this bouncer.
        return arr.filter(Boolean);
    }

    bouncer([7, "ate", "", false, 9]);
    ```

1. Where do I Belong

    ```javascript
    function sortNumber(a, b) {
        return a - b;
    }
    function getIndexToIns(arr, num) {
        // Find my place in this sorted array.
        arr.sort(sortNumber);
        let i=0;
        for(; i<arr.length; i++){
            if(arr[i]>=num)
            break;
        }
        return i;
    }

    getIndexToIns([5, 3, 20, 3], 5);
    ```

1. Mutations

    ```javascript
    function mutation(arr) {
        arr[0]=arr[0].toLowerCase();
        arr[1]=arr[1].toLowerCase();
        for(let i=0; i<arr[1].length; i++){
            console.log(arr[1].charAt(i));
            if(arr[0].indexOf(arr[1].charAt(i))==-1)
            return false;
        }
        return true;
    }

    mutation(["zyxwvutsrqponmlkjihgfedcba", "qrstu"]);
    ```

1. Chunky Monkey

    ```javascript
    function chunkArrayInGroups(arr, size) {
        // Break it up.
        let result = [];
        for(let i=0; i<arr.length;){
            let end = i + size;
            if(end<arr.length){
            result.push(arr.slice(i,end));
            }else{
            result.push(arr.slice(i));
            }
            i+=size;
        }
        return result;
    }

    chunkArrayInGroups(["a", "b", "c", "d"], 2);
    ```

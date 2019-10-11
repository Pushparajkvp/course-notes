# JavaScript Algorithms and Data Structures Projects

1. Palindrome Checker

    ```javascript
    function palindrome(str) {
        let purifiedString = str.toLowerCase().replace(/[^a-z0-9]/g,"");
        let reversePurifiedString = purifiedString.split('').reverse().join('');
        console.log(purifiedString);
        return purifiedString === reversePurifiedString;
    }
    palindrome("1 eye for of 1 eye.");
    ```

1. Roman Numeral Converter

    ```javascript
    ```

1. 
# Debugging

1. Use the JavaScript Console to Check the Value of a Variable

    ```javascript
    let a = 5;
    let b = 1;
    a++;
    // Add your code below this line
    console.log(a);

    let sumAB = a + b;
    console.log(sumAB);
    ```

1. Console.clear()

    ```javascript
    console.clear();
    ```

1. Use typeof to Check the Type of a Variable

    ```javascript
    let seven = 7;
    let three = "3";
    console.log(seven + three);
    // Add your code below this line
    console.log(typeof(seven));
    console.log(typeof(three));
    ```

1. Catch Misspelled Variable and Function Names

    ```javascript
    let receivables = 10;
    let payables = 8;
    let netWorkingCapital = receivables - payables;
    console.log(`Net working capital is: ${netWorkingCapital}`);
    ```

1. Catch Unclosed Parentheses, Brackets, Braces and Quotes

    ```javascript
    let myArray = [1, 2, 3];
    let arraySum = myArray.reduce((previous, current) =>  previous + current);
    console.log(`Sum of array values is: ${arraySum}`);
    ```

1. Catch Mixed Usage of Single and Double Quotes

    ```javascript
    let innerHtml = "<p>Click here to <a href=\"#Home\">return home</a></p>";
    console.log(innerHtml);
    ```

1. Catch Use of Assignment Operator Instead of Equality Operator

    ```javascript
    let x = 7;
    let y = 9;
    let result = "to come";

    if(x == y) {
    result = "Equal!";
    } else {
    result = "Not equal!";
    }

    console.log(result);
    ```

1. Catch Missing Open and Closing Parenthesis After a Function Call

    ```javascript
    function getNine() {
        let x = 6;
        let y = 3;
        return x + y;
    }

    let result = getNine();
    console.log(result);
    ```

1. Catch Arguments Passed in the Wrong Order When Calling a Function

    ```javascript
    function raiseToPower(b, e) {
        return Math.pow(b, e);
    }

    let base = 2;
    let exp = 3;
    let power = raiseToPower(base, exp);
    console.log(power);
    ```

1. Catch Off By One Errors When Using Indexing

    ```javascript
    function countToFive() {
        let firstFive = "12345";
        let len = firstFive.length;
        // Fix the line below
        for (let i = 0; i < len; i++) {
        // Do not alter code below this line
            console.log(firstFive[i]);
        }
    }

    countToFive();
    ```

1. Use Caution When Reinitializing Variables Inside a Loop

    ```javascript
    function zeroArray(m, n) {
        // Creates a 2-D array with m rows and n columns of zeroes
        let newArray = [];
        let row = [];
        for (let i = 0; i < m; i++) {
            // Adds the m-th row into newArray
            row = [];
            for (let j = 0; j < n; j++) {
            // Pushes n zeroes into the current row to create the columns
            row.push(0);
            }
            // Pushes the current row, which now has n zeroes in it, to the array
            newArray.push(row);
        }
        return newArray;
    }

    let matrix = zeroArray(3, 2);
    console.log(matrix);
    ```

1. Prevent Infinite Loops with a Valid Terminal Condition

    ```javascript
    function myFunc() {
        for (let i = 1; i <= 4; i += 2) {
            console.log("Still going!");
        }
    }
    ```

# Basic Javascript

1. Comment Your JavaScript Code

    ```javascript
    //Single line
    /* multi line */
    ```

1. Declare JavaScript Variables

    * undefined, null, boolean, string, symbol, number, and object (7 data types)

    ```javascript
    // Example
    var ourName;

    // Declare myName below this line
    var myName;
    ```

1. Storing Values with the Assignment Operator

    ```javascript
    // Setup
    var a;
    var b = 2;

    // Only change code below this line
    a = 7;
    b = a;
    ```

1. Initializing Variables with the Assignment Operator

    ```javascript
    // Example
    var ourVar = 19;

    // Only change code below this line
    var a = 9;
    ```

1. Understanding Uninitialized Variables
    * Math operation on undefined -> NAN
    * String operation on undefined -> undefined

    ```javascript
    // Initialize these three variables
    var a = 5;
    var b = 10;
    var c = "I am a";

    // Do not change code below this line

    a = a + 1;
    b = b + 5;
    c = c + " String!";
    ```

1. Understanding Case Sensitivity in Variables

    ```javascript
    // Declarations
    var studlyCapVar;
    var properCamelCase;
    var titleCaseOver;

    // Assignments
    studlyCapVar = 10;
    properCamelCase = "A String";
    titleCaseOver = 9000;
    ```

1. Add Two Numbers with JavaScript

    ```javascript
    var sum = 10 + 10;
    ```

1. Subtract One Number from Another with JavaScript

    ```javascript
    var sum = 45 - 33;
    ```

1. Multiply Two Numbers with JavaScript

    ```javascript
    var product = 8 * 10;
    ```

1. Divide One Number by Another with JavaScript

    ```javascript
    var quotient = 66 / 33;
    ```

1. Increment a Number with JavaScript

    ```javascript
    var myVar = 87;
    // Only change code below this line
    myVar++;
    ```

1. Decrement a Number with JavaScript

    ```javascript
    var myVar = 11;

    // Only change code below this line
    --myVar;
    ```

1. Create Decimal Numbers with JavaScript

    ```javascript
    var ourDecimal = 5.7;

    // Only change code below this line
    var myDecimal = 1.2;
    ```

1. Multiply Two Decimals with JavaScript

    ```javascript
    var product = 5.0 * 1.0;
    ```

1. Divide One Decimal by Another with JavaScript

    ```javascript
    var quotient = 4.4 / 2.0; // Fix this line
    ```

1. Finding a Remainder in JavaScript

    ```javascript
    // Only change code below this line

    var remainder = 11%3;
    ```

1. Compound Assignment With Augmented Addition

    ```javascript
    var a = 3;
    var b = 17;
    var c = 12;

    // Only modify code below this line

    a += 12;
    b += 9;
    c += 7;
    ```

1. Compound Assignment With Augmented Subtraction

    ```javascript
    var a = 11;
    var b = 9;
    var c = 3;

    // Only modify code below this line

    a -= 6;
    b -= 15;
    c -= 1;
    ```

1. Compound Assignment With Augmented Multiplication

    ```javascript
    var a = 5;
    var b = 12;
    var c = 4.6;

    // Only modify code below this line

    a *= 5;
    b *= 3;
    c *= 10;
    ```

1. Compound Assignment With Augmented Division

    ```javascript
    var a = 48;
    var b = 108;
    var c = 33;

    // Only modify code below this line

    a /= 12;
    b /= 4;
    c /= 11;
    ```

1. Declare String Variables

    ```javascript
    // Example
    var firstName = "Alan";
    var lastName = "Turing";

    // Only change code below this line
    var myFirstName = firstName;
    var myLastName = lastName;
    ```

1. Escaping Literal Quotes in Strings

    ```javascript
    var myStr = "I am a \"double quoted\" string inside \"double quotes\"."; // Change this line
    ```

1. Quoting Strings with Single Quotes

    ```javascript
    var myStr = '<a href="http://www.example.com" target="_blank">Link</a>';
    ```

1. Escape Sequences in Strings

    ```javascript
    var myStr = "FirstLine\n\t\\SecondLine\nThirdLine"; // Change this line
    ```

1. Concatenating Strings with Plus Operator

    ```javascript
    // Example
    var ourStr = "I come first. " + "I come second.";

    // Only change code below this line

    var myStr = "This is the start. " + "This is the end.";
    ```

1. Concatenating Strings with the Plus Equals Operator

    ```javascript
    // Example
    var ourStr = "I come first. ";
    ourStr += "I come second.";

    // Only change code below this line

    var myStr = "This is the first sentence. ";
    myStr += "This is the second sentence.";
    ```

1. Constructing Strings with Variables

    ```javascript
    // Example
    var ourName = "freeCodeCamp";
    var ourStr = "Hello, our name is " + ourName + ", how are you?";

    // Only change code below this line
    var myName = "private";
    var myStr = "My name is " +myName+ " and I am well!";
    ```

1. Appending Variables to Strings

    ```javascript
    // Example
    var anAdjective = "awesome!";
    var ourStr = "freeCodeCamp is ";
    ourStr += anAdjective;

    // Only change code below this line

    var someAdjective = "test";
    var myStr = "Learning to code is ";
    myStr += someAdjective;
    ```

1. Find the Length of a String

    ```javascript
    // Example
    var firstNameLength = 0;
    var firstName = "Ada";

    firstNameLength = firstName.length;

    // Setup
    var lastNameLength = 0;
    var lastName = "Lovelace";

    // Only change code below this line.

    lastNameLength = lastName.length;
    ```

1. Use Bracket Notation to Find the First Character in a String

    ```javascript
    // Example
    var firstLetterOfFirstName = "";
    var firstName = "Ada";

    firstLetterOfFirstName = firstName[0];

    // Setup
    var firstLetterOfLastName = "";
    var lastName = "Lovelace";

    // Only change code below this line
    firstLetterOfLastName = lastName[0];
    ```

1. Understand String Immutability

    ```javascript
    // Setup
    var myStr = "Jello World";

    // Only change code below this line

    myStr = "Hello World"; // Fix Me
    ```

1. Use Bracket Notation to Find the Nth Character in a String

    ```javascript
    // Example
    var firstName = "Ada";
    var secondLetterOfFirstName = firstName[1];

    // Setup
    var lastName = "Lovelace";

    // Only change code below this line.
    var thirdLetterOfLastName = lastName[2];
    ```

1. Use Bracket Notation to Find the Last Character in a String

    ```javascript
    // Example
    var firstName = "Ada";
    var lastLetterOfFirstName = firstName[firstName.length - 1];

    // Setup
    var lastName = "Lovelace";

    // Only change code below this line.
    var lastLetterOfLastName = lastName[lastName.length - 1];
    ```

1. Use Bracket Notation to Find the Nth-to-Last Character in a String

    ```javascript
    // Example
    var firstName = "Ada";
    var thirdToLastLetterOfFirstName = firstName[firstName.length - 3];

    // Setup
    var lastName = "Lovelace";

    // Only change code below this line
    var secondToLastLetterOfLastName = lastName[lastName.length - 2];
    ```

1. Word Blanks

    ```javascript
    function wordBlanks(myNoun, myAdjective, myVerb, myAdverb) {
    // Your code below this line
    var result = "On seeing a "+ myAdjective+ " "+ myNoun + ", I "+ myVerb + " " + myAdverb;

    // Your code above this line
    return result;
    }

    // Change the words here to test your function
    wordBlanks("dog", "big", "ran", "quickly");
    ```

1. Store Multiple Values in one Variable using JavaScript Arrays

    ```javascript
    // Example
    var ourArray = ["John", 23];

    // Only change code below this line.
    var myArray = ["Test", 123];
    ```

1. Nest one Array within Another Array

    ```javascript
    // Example
    var ourArray = [["the universe", 42], ["everything", 101010]];

    // Only change code below this line.
    var myArray = [["Inner Test", 123], 123];
    ```

1. Access Array Data with Indexes

    ```javascript
    // Example
    var ourArray = [50,60,70];
    var ourData = ourArray[0]; // equals 50

    // Setup
    var myArray = [50,60,70];

    // Only change code below this line.
    var myData = myArray[0];
    ```

1. Modify Array Data With Indexes

    ```javascript
    // Example
    var ourArray = [18,64,99];
    ourArray[1] = 45; // ourArray now equals [18,45,99].

    // Setup
    var myArray = [18,64,99];

    // Only change code below this line.
    myArray[0] = 45;
    ```

1. Access Multi-Dimensional Arrays With Indexes

    ```javascript
    // Setup
    var myArray = [[1,2,3], [4,5,6], [7,8,9], [[10,11,12], 13, 14]];

    // Only change code below this line.
    var myData = myArray[2][1];
    ```

1. Manipulate Arrays With push()

    ```javascript
    // Example
    var ourArray = ["Stimpson", "J", "cat"];
    ourArray.push(["happy", "joy"]);
    // ourArray now equals ["Stimpson", "J", "cat", ["happy", "joy"]]

    // Setup
    var myArray = [["John", 23], ["cat", 2]];

    // Only change code below this line.

    myArray.push(["dog", 3]);
    ```

1. Manipulate Arrays With pop()

    ```javascript
    // Example
    var ourArray = [1,2,3];
    var removedFromOurArray = ourArray.pop(); 
    // removedFromOurArray now equals 3, and ourArray now equals [1,2]

    // Setup
    var myArray = [["John", 23], ["cat", 2]];

    // Only change code below this line.
    var removedFromMyArray = myArray.pop();
    ```

1. Manipulate Arrays With shift()

    ```javascript
    // Example
    var ourArray = ["Stimpson", "J", ["cat"]];
    var removedFromOurArray = ourArray.shift();
    // removedFromOurArray now equals "Stimpson" and ourArray now equals ["J", ["cat"]].

    // Setup
    var myArray = [["John", 23], ["dog", 3]];

    // Only change code below this line.
    var removedFromMyArray = myArray.shift();
    ```

1. Manipulate Arrays With unshift()

    ```javascript
    // Example
    var ourArray = ["Stimpson", "J", "cat"];
    ourArray.shift(); // ourArray now equals ["J", "cat"]
    ourArray.unshift("Happy"); 
    // ourArray now equals ["Happy", "J", "cat"]

    // Setup
    var myArray = [["John", 23], ["dog", 3]];
    myArray.shift();

    // Only change code below this line.

    myArray.unshift(["Paul",35]);
    ```

1. Shopping List

    ```javascript
    var myList = [["Chocolate Bar0", 15],["Chocolate Bar1", 16],["Chocolate Bar2", 17],["Chocolate Bar3", 18],["Chocolate Bar4", 19]];
    ```

1. Write Reusable JavaScript with Functions

    ```javascript
    // Example
    function ourReusableFunction() {
        console.log("Heyya, World");
    }

    ourReusableFunction();

    // Only change code below this line
    function reusableFunction() {
        console.log("Hi World");
    }
    reusableFunction();
    ```

1. Passing Values to Functions with Arguments

    ```javascript
    // Example
    function ourFunctionWithArgs(a, b) {
        console.log(a - b);
    }
    ourFunctionWithArgs(10, 5); // Outputs 5

    // Only change code below this line.

    function functionWithArgs(a, b) {
        console.log(a+b);
    }
    functionWithArgs(1,2);
    ```

1. Global Scope and Functions

    * Declaring without var will have global scope

    ```javascript
    // Declare your variable here
    var myGlobal = 10;

    function fun1() {
        // Assign 5 to oopsGlobal Here
        oopsGlobal = 5;
    }

    // Only change code above this line
    function fun2() {
        var output = "";
        if (typeof myGlobal != "undefined") {
            output += "myGlobal: " + myGlobal;
        }
        if (typeof oopsGlobal != "undefined") {
            output += " oopsGlobal: " + oopsGlobal;
        }
        console.log(output);
    }
    ```

1. Local Scope and Functions

    ```javascript
    function myLocalScope() {
        'use strict'; // you shouldn't need to edit this line
        var myVar = "test";
        console.log(myVar);
    }
    myLocalScope();

    // Run and check the console
    // myVar is not defined outside of myLocalScope
    //console.log(myVar);

    // Now remove the console log line to pass the test
    ```

1. Global vs. Local Scope in Functions

    ```javascript
    // Setup
    var outerWear = "T-Shirt";

    function myOutfit() {
        // Only change code below this line
        var outerWear = "sweater"

        // Only change code above this line
        return outerWear;
    }

    myOutfit();
    ```

1. Return a Value from a Function with Return

    ```javascript
    // Example
    function minusSeven(num) {
        return num - 7;
    }

    // Only change code below this line
    function timesFive(num) {
        return num * 5;
    }


    console.log(minusSeven(10));
    ```

1. Understanding Undefined Value returned from a Function

    ```javascript
    // Example
    var sum = 0;
    function addThree() {
        sum = sum + 3;
    }

    // Only change code below this line
    function addFive() {
        sum += 5;
    }


    // Only change code above this line
    var returnedValue = addFive();
    ```

1. Assignment with a Returned Value

    ```javascript
    // Example
    var changed = 0;

    function change(num) {
        return (num + 5) / 3;
    }

    changed = change(10);

    // Setup
    var processed = 0;

    function processArg(num) {
        return (num + 3) / 5;
    }

    // Only change code below this line
    var processed = processArg(7);
    ```

1. Stand in Line

    ```javascript
    function nextInLine(arr, item) {
        // Your code here
        arr.push(item);
        return arr.shift();  // Change this line
    }

    // Test Setup
    var testArr = [1,2,3,4,5];

    // Display Code
    console.log("Before: " + JSON.stringify(testArr));
    console.log(nextInLine(testArr, 6)); // Modify this line to test
    console.log("After: " + JSON.stringify(testArr));
    ```

1. Understanding Boolean Values

    ```javascript
    function welcomeToBooleans() {
        // Only change code below this line.

        return true; // Change this line

        // Only change code above this line.
    }
    ```

1. Use Conditional Logic with If Statements

    ```javascript
    // Example
    function ourTrueOrFalse(isItTrue) {
        if (isItTrue) { 
            return "Yes, it's true";
        }
        return "No, it's false";
    }

    // Setup
    function trueOrFalse(wasThatTrue) {
        // Only change code below this line.
        if(wasThatTrue)
            return "Yes, that was true";
        return "No, that was false";
        // Only change code above this line.
    }

    // Change this value to test
    trueOrFalse(true);
    ```

1. Comparison with the Equality Operator (Type Coercion)

    ```javascript
    // Setup
    function testEqual(val) {
        if (val == 12) { // Change this line
            return "Equal";
        }
        return "Not Equal";
    }

    // Change this value to test
    testEqual(10);
    ```

1. Comparison with the Strict Equality Operator

    ```javascript
    // Setup
    function testStrict(val) {
        if (val === 7) { // Change this line
            return "Equal";
        }
        return "Not Equal";
    }

    // Change this value to test
    testStrict(10);
    ```

1. Practice comparing different values

    ```javascript
    // Setup
    function compareEquality(a, b) {
        if (a === b) { // Change this line
            return "Equal";
        }
        return "Not Equal";
    }

    // Change this value to test
    compareEquality(10, "10");
    ```

1. Comparison with the Inequality Operator

    ```javascript
    // Setup
    function testNotEqual(val) {
        if (val != 99) { // Change this line
            return "Not Equal";
        }
        return "Equal";
    }

    // Change this value to test
    testNotEqual(10);
    ```

1. Comparison with the Strict Inequality Operator

    ```javascript
    // Setup
    function testStrictNotEqual(val) {
        // Only Change Code Below this Line

        if (val !== 17) {

        // Only Change Code Above this Line

            return "Not Equal";
        }
        return "Equal";
    }

    // Change this value to test
    testStrictNotEqual(10);
    ```

1. Comparison with the Greater Than Operator

    ```javascript
    function testGreaterThan(val) {
        if (val > 100) {  // Change this line
            return "Over 100";
        }

        if (val > 10) {  // Change this line
            return "Over 10";
        }

        return "10 or Under";
    }

    // Change this value to test
    testGreaterThan(10);
    ```

1. Comparison with the Greater Than Or Equal To Operator

    ```javascript
    function testGreaterOrEqual(val) {
        if (val >= 20) {  // Change this line
            return "20 or Over";
        }

        if (val >= 10) {  // Change this line
            return "10 or Over";
        }

        return "Less than 10";
    }

    // Change this value to test
    testGreaterOrEqual(10);
    ```

1. Comparison with the Less Than Operator

    ```javascript
    function testLessThan(val) {
        if (val < 25) {  // Change this line
            return "Under 25";
        }

        if (val < 55) {  // Change this line
            return "Under 55";
        }

        return "55 or Over";
    }

    // Change this value to test
    testLessThan(10);
    ```

1. Comparison with the Less Than Or Equal To Operator

    ```javascript
    function testLessOrEqual(val) {
        if (val <= 12) {  // Change this line
            return "Smaller Than or Equal to 12";
        }

        if (val <= 24) {  // Change this line
            return "Smaller Than or Equal to 24";
        }

        return "More Than 24";
    }

    // Change this value to test
    testLessOrEqual(10);
    ```

1. Comparisons with the Logical And Operator

    ```javascript
    function testLogicalAnd(val) {
        // Only change code below this line

        if (val <=50 && val >= 25) {
            return "Yes";
        }

        // Only change code above this line
        return "No";
    }

    // Change this value to test
    testLogicalAnd(10);
    ```

1. Comparisons with the Logical Or Operator

    ```javascript
    function testLogicalOr(val) {
        // Only change code below this line

        if (val < 10 || val > 20) {
            return "Outside";
        }

        // Only change code above this line
        return "Inside";
    }

    // Change this value to test
    testLogicalOr(15);
    ```

1. Introducing Else Statements

    ```javascript
    function testElse(val) {
        var result = "";
        // Only change code below this line
        if (val > 5) {
            result = "Bigger than 5";
        }else {
            result = "5 or Smaller";
        }
        // Only change code above this line
        return result;
    }
    // Change this value to test
    testElse(4);

    ```

1. Introducing Else If Statements

    ```javascript
    function testElseIf(val) {
        if (val > 10) {
            return "Greater than 10";
        } else if (val < 5 ) {
            return "Smaller than 5";
        } else {
            return "Between 5 and 10";
        }
    }

    // Change this value to test
    testElseIf(7);
    ```

1. Logical Order in If Else Statements

    ```javascript
    function orderMyLogic(val) {
        if (val < 5) {
            return "Less than 5";
        } else if (val < 10) {
            return "Less than 10";
        } else {
            return "Greater than or equal to 10";
        }
    }

    // Change this value to test
    orderMyLogic(7);
    ```

1. Chaining If Else Statements

    ```javascript
    function testSize(num) {
        // Only change code below this line
        if(num < 5)
            return "Tiny";
        else if(num < 10)
            return "Small";
        else if(num < 15)
            return "Medium";
        else if(num < 20)
            return "Large";
        else
            return "Huge";
        // Only change code above this line
    }

    // Change this value to test
    testSize(7);
    ```

1. Golf Code

    ```javascript
    var names = ["Hole-in-one!", "Eagle", "Birdie", "Par", "Bogey", "Double Bogey", "Go Home!"];
    function golfScore(par, strokes) {
        // Only change code below this line
        if(strokes == 1)
            return names[0];
        else if(strokes == par-1)
            return names[2];
        else if(strokes  == par)
            return names[3];
        else if(strokes == par+1)
            return names[4];
        else if(strokes == par+2)
            return names[5];
        else if(strokes <= par-2)
            return names[1];
        else
            return names[6];
        // Only change code above this line
    }

    // Change these values to test
    golfScore(5, 4);
    ```

1. Selecting from Many Options with Switch Statements

    ```javascript
    function caseInSwitch(val) {
        var answer = "";
        // Only change code below this line
        switch(val){
            case 1 : answer = "alpha"; break;
            case 2 : answer = "beta"; break;
            case 3 : answer = "gamma"; break;
            case 4 : answer = "delta"; break;
        }
        // Only change code above this line  
        return answer;  
    }

    // Change this value to test
    caseInSwitch(1);
    ```

1. Adding a Default Option in Switch Statements

    ```javascript
    function switchOfStuff(val) {
        var answer = "";
        // Only change code below this line
        switch(val){
            case "a" : answer = "apple"; break;
            case "b" : answer = "bird"; break;
            case "c" : answer = "cat"; break;
            default : answer = "stuff";
        }
        // Only change code above this line  
    return answer;  
    }

    // Change this value to test
    switchOfStuff(1);
    ```

1. Multiple Identical Options in Switch Statements

    ```javascript
    function sequentialSizes(val) {
        var answer = "";
        // Only change code below this line
        switch(val){
            case 1:
            case 2:
            case 3: answer = "Low"; break;
            case 4:
            case 5:
            case 6: answer = "Mid"; break;
            case 7:
            case 8:
            case 9: answer = "High"; break;
        }
        // Only change code above this line  
        return answer;  
    }
    // Change this value to test
    sequentialSizes(1);
    ```

1. Replacing If Else Chains with Switch

    ```javascript
    function chainToSwitch(val) {
        var answer = "";
        // Only change code below this line
        switch(val){
            case "bob": answer = "Marley"; break;
            case 42: answer = "The Answer"; break;
            case 1: answer = "There is no #1"; break;
            case 99: answer = "Missed me by this much!"; break;
            case 7: answer = "Ate Nine"; break;
        }  
        // Only change code above this line  
        return answer;  
    }

    // Change this value to test
    chainToSwitch(7);

    ```

1. Returning Boolean Values from Functions

    ```javascript
    function isLess(a, b) {
        return a < b;
    }

    // Change these values to test
    isLess(10, 15);
    ```

1. Return Early Pattern for Functions

    ```javascript
    // Setup
    function abTest(a, b) {
        // Only change code below this line
        if( a<0 || b<0)
            return undefined;
        // Only change code above this line
        return Math.round(Math.pow(Math.sqrt(a) + Math.sqrt(b), 2));
    }
    // Change values below to test your code
    abTest(2,2);
    ```

1. Counting Cards

    ```javascript
    var count = 0;
    function cc(card) {
        // Only change code below this line
        switch(card){
            case 2:
            case 3:
            case 4:
            case 5:
            case 6:
            count++; break;
            case 10:
            case 'J':
            case 'Q':
            case 'K':
            case 'A':
            count--; break;
        }
        if(count <= 0)
            return count + " Hold";
        return count + " Bet";
        // Only change code above this line
    }
    // Add/remove calls to test your function.
    // Note: Only the last will display
    cc(2); cc(3); cc(7); cc('K'); cc('A');
    ```

1. Build JavaScript Objects

    ```javascript
    // Example
    var ourDog = {
        "name": "Camper",
        "legs": 4,
        "tails": 1,
        "friends": ["everything!"]
    };
    // Only change code below this line.
    var myDog = {
        "name": "test",
        "legs": 4,
        "tails": 1,
        "friends": ["test", "test2", "test3"]
    };
    ```

1. Accessing Object Properties with Dot Notation

    ```javascript
    // Setup
    var testObj = {
        "hat": "ballcap",
        "shirt": "jersey",
        "shoes": "cleats"
    };
    // Only change code below this line
    var hatValue = testObj.hat;      // Change this line
    var shirtValue = testObj.shirt;    // Change this line
    ```

1. Accessing Object Properties with Bracket Notation
    * For cases when there is a space in the name of the key.

    ```javascript
    // Setup
    var testObj = {
        "an entree": "hamburger",
        "my side": "veggies",
        "the drink": "water"
    };
    // Only change code below this line
    var entreeValue = testObj["an entree"];   // Change this line
    var drinkValue = testObj["the drink"];    // Change this line
    ```

1. Accessing Object Properties with Variables

    ```javascript
    // Setup
    var testObj = {
        12: "Namath",
        16: "Montana",
        19: "Unitas"
    };
    // Only change code below this line;
    var playerNumber = 16;       // Change this Line
    var player = testObj[playerNumber];   // Change this Line
    ```

1. Updating Object Properties

    ```javascript
    // Example
    var ourDog = {
        "name": "Camper",
        "legs": 4,
        "tails": 1,
        "friends": ["everything!"]
    };
    ourDog.name = "Happy Camper";
    // Setup
    var myDog = {
        "name": "Coder",
        "legs": 4,
        "tails": 1,
        "friends": ["freeCodeCamp Campers"]
    };
    // Only change code below this line.
    myDog.name = "Happy Coder";
    ```

1. Add New Properties to a JavaScript Object

    ```javascript
    // Example
    var ourDog = {
        "name": "Camper",
        "legs": 4,
        "tails": 1,
        "friends": ["everything!"]
    };
    ourDog.bark = "bow-wow";
    // Setup
    var myDog = {
        "name": "Happy Coder",
        "legs": 4,
        "tails": 1,
        "friends": ["freeCodeCamp Campers"]
    };
    // Only change code below this line.
    myDog.bark = "woof";
    ```

1. Delete Properties from a JavaScript Object

    ```javascript
    // Example
    var ourDog = {
        "name": "Camper",
        "legs": 4,
        "tails": 1,
        "friends": ["everything!"],
        "bark": "bow-wow"
    };
    delete ourDog.bark;
    // Setup
    var myDog = {
        "name": "Happy Coder",
        "legs": 4,
        "tails": 1,
        "friends": ["freeCodeCamp Campers"],
        "bark": "woof"
    };
    // Only change code below this line.
    delete myDog.tails;
    ```

1. Using Objects for Lookups

    ```javascript
    // Setup
    function phoneticLookup(val) {
        var result = "";
        // Only change code below this line
        var lookup = {
            "alpha" : "Adams",
            "bravo" : "Boston",
            "charlie" : "Chicago",
            "delta" : "Denver",
            "echo" : "Easy",
            "foxtrot" : "Frank"
        }
        result = lookup[val];
        // Only change code above this line
        return result;
    }
    // Change this value to test
    phoneticLookup("charlie");
    ```

1. Testing Objects for Properties

    ```javascript
        // Setup
    var myObj = {
        gift: "pony",
        pet: "kitten",
        bed: "sleigh"
    };
    function checkObj(checkProp) {
        // Your Code Here
        if(myObj.hasOwnProperty(checkProp))
            return myObj[checkProp];
        return "Not Found";
    }
    // Test your code by modifying these values
    checkObj("gift");
    ```

1. Manipulating Complex Objects

    ```javascript
    var myMusic = [
    {
        "artist": "Billy Joel",
        "title": "Piano Man",
        "release_year": 1973,
        "formats": [
            "CD",
            "8T",
            "LP"
        ],
        "gold": true
    },
    {
        "artist": "Billy Joel",
        "title": "Piano Man",
        "release_year": 1973,
        "formats": [
            "CD",
            "8T",
            "LP"
        ],
        "gold": true
    }
    // Add record here
    ];
    ```

1. Accessing Nested Objects

    ```javascript
    // Setup
    var myStorage = {
        "car": {
            "inside": {
            "glove box": "maps",
            "passenger seat": "crumbs"
            },
            "outside": {
            "trunk": "jack"
            }
        }
    };
    var gloveBoxContents = myStorage.car.inside["glove box"]; // Change this line
    ```

1. Accessing Nested Arrays

    ```javascript
    // Setup
    var myPlants = [
    {
        type: "flowers",
        list: [
        "rose",
        "tulip",
        "dandelion"
        ]
    },
    {
        type: "trees",
        list: [
        "fir",
        "pine",
        "birch"
        ]
    }  
    ];
    // Only change code below this line
    var secondTree = myPlants[1].list[1]; // Change this line
    ```

1. Record Collection

    ```javascript
    // Setup
    var collection = {
        "2548": {
        "album": "Slippery When Wet",
        "artist": "Bon Jovi",
        "tracks": [ 
            "Let It Rock", 
            "You Give Love a Bad Name" 
        ]
        },
        "2468": {
        "album": "1999",
        "artist": "Prince",
        "tracks": [ 
            "1999", 
            "Little Red Corvette" 
        ]
        },
        "1245": {
        "artist": "Robert Palmer",
        "tracks": [ ]
        },
        "5439": {
        "album": "ABBA Gold"
        }
    };
    // Keep a copy of the collection for tests
    var collectionCopy = JSON.parse(JSON.stringify(collection));
    // Only change code below this line
    function updateRecords(id, prop, value) {
        if(prop != "tracks" && value != ""){
            collection[id][prop] = value;
            return collection;
        } else if(value == ""){
            delete collection[id][prop];
            return collection;
        }
        if(!collection[id].hasOwnProperty(prop))
            collection[id][prop] = [];
        collection[id][prop].push(value);
        return collection;
    }
    // Alter values below to test your code
    updateRecords(5439, "artist", "ABBA");
    ```

1. Iterate with JavaScript While Loops

    ```javascript
    // Setup
    var myArray = [];

    // Only change code below this line.
    var i =0;
    while(i<=4)
        myArray.push(i++);
    ```

1. Iterate with JavaScript For Loops

    ```javascript
    // Example
    var ourArray = [];
    for (var i = 0; i < 5; i++) {
        ourArray.push(i);
    }
    // Setup
    var myArray = [];
    // Only change code below this line.
    for(var i=1; i<=5; i++)
        myArray.push(i);
    ```

1. Iterate Odd Numbers With a For Loop

    ```javascript
    // Example
    var ourArray = [];
    for (var i = 0; i < 10; i += 2) {
        ourArray.push(i);
    }
    // Setup
    var myArray = [];
    // Only change code below this line.
    for(var i=1; i<=9; i+=2)
        myArray.push(i);
    ```

1. Count Backwards With a For Loop

    ```javascript
    // Example
    var ourArray = [];
    for (var i = 10; i > 0; i -= 2) {
        ourArray.push(i);
    }
    // Setup
    var myArray = [];
    // Only change code below this line.
    for(var i=9; i>=1; i-=2)
        myArray.push(i);
    ```

1. Iterate Through an Array with a For Loop

    ```javascript
    // Example
    var ourArr = [ 9, 10, 11, 12];
    var ourTotal = 0;
    for (var i = 0; i < ourArr.length; i++) {
        ourTotal += ourArr[i];
    }
    // Setup
    var myArr = [ 2, 3, 4, 5, 6];
    // Only change code below this line
    var total =0;
    for(var i=0; i<myArr.length; i++)
        total += myArr[i];
    ```

1. Nesting For Loops

    ```javascript
    function multiplyAll(arr) {
        var product = 1;
        // Only change code below this line
        for(var i=0; i<arr.length; i++){
            for(var j=0; j<arr[i].length; j++){
            product *= arr[i][j];
            }
        }
        // Only change code above this line
        return product;
    }

    // Modify values below to test your code
    multiplyAll([[1,2],[3,4],[5,6,7]]);
    ```

1. Iterate with JavaScript Do...While Loops

    ```javascript
    // Setup
    var myArray = [];
    var i = 10;
    // Only change code below this line.
    do{
        myArray.push(i);
        i++;
    }while(i<=10);
    ```

1. Profile Lookup

    ```javascript
    //Setup
    var contacts = [
        {
            "firstName": "Akira",
            "lastName": "Laine",
            "number": "0543236543",
            "likes": ["Pizza", "Coding", "Brownie Points"]
        },
        {
            "firstName": "Harry",
            "lastName": "Potter",
            "number": "0994372684",
            "likes": ["Hogwarts", "Magic", "Hagrid"]
        },
        {
            "firstName": "Sherlock",
            "lastName": "Holmes",
            "number": "0487345643",
            "likes": ["Intriguing Cases", "Violin"]
        },
        {
            "firstName": "Kristian",
            "lastName": "Vos",
            "number": "unknown",
            "likes": ["JavaScript", "Gaming", "Foxes"]
        }
    ];


    function lookUpProfile(name, prop){
        // Only change code below this line
        for(var i=0; i<contacts.length; i++){
            if(contacts[i].firstName == name){
            if(contacts[i].hasOwnProperty(prop))
                return contacts[i][prop];
            else
                return "No such property";
            }
        }
        return "No such contact";
        // Only change code above this line
    }

    // Change these values to test your function
    lookUpProfile("Akira", "likes");
    ```

1. Generate Random Fractions with JavaScript

    ```javascript
    function randomFraction() {
        // Only change code below this line.
        return Math.random();
        // Only change code above this line.
    }
    ```

1. Generate Random Whole Numbers with JavaScript

    ```javascript
    function randomWholeNum() {
        // Only change code below this line.
        return Math.floor(Math.random()*10);
    }
    ```

1. Generate Random Whole Numbers within a Range

    ```javascript
    function randomRange(myMin, myMax) {
        return Math.floor(Math.random() * (myMax-myMin+1)) + myMin; // Change this line
    }
    ```

1. Use the parseInt Function

    ```javascript
    function convertToInteger(str) {
        return parseInt(str);
    }
    ```

1. Use the parseInt Function with a Radix

    ```javascript
    function convertToInteger(str) {
        return parseInt(str, 2);
    }

    convertToInteger("10011");
    ```

1. Use the Conditional (Ternary) Operator

    ```javascript
    function checkEqual(a, b) {
        return a==b? true: false;
    }
    ```

1. Use Multiple Conditional (Ternary) Operators

    ```javascript
    function checkSign(num) {
        return num > 0 ? "positive" : num == 0? "zero" : "negative";
    }
    ```

1. Replace Loops using Recursion

    ```javascript
    function sum(arr, n) {
        // Only change code below this line
        if(n==0)
            return arr[0];
        return sum(arr, n-1) + arr[n];
        // Only change code above this line
    }
    ```

1. Use Recursion to Create a Range of Numbers

    ```javascript
    function rangeOfNumbers(startNum, endNum) {
        if(startNum == endNum)
            return [startNum];
        var result = rangeOfNumbers(startNum, endNum -1);
        result.push(endNum);
        return result;
    };

    ```

1. Use Recursion to Create a Countdown

    ```javascript
    //Only change code below this line
    function countdown(myArray, n){
        if(n==1)
            return myArray.push(1);
        else if(n<1)
            return myArray;
        myArray.push(n);
        return countdown(myArray,n-1);
    }
    ```

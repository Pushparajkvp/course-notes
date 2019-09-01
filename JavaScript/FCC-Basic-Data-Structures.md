# Basic Data Structures

1. Use an Array to Store a Collection of Data

    ```javascript
    let yourArray = [10, true, "test", 20, false]; // change this line
    ```

1. Access an Array's Contents Using Bracket Notation

    ```javascript
    let myArray = ["a", "b", "c", "d"];
    // change code below this line
    myArray[1] = "e";
    //change code above this line
    console.log(myArray);
    ```

1. Add Items to an Array with push() and unshift()

    ```javascript
    function mixedNumbers(arr) {
        // change code below this line
        arr.unshift('I', 2, 'three');
        arr.push(7, 'VIII', 9);
        // change code above this line
        return arr;
    }

    // do not change code below this line
    console.log(mixedNumbers(['IV', 5, 'six']));
    ```

1. Remove Items from an Array with pop() and shift()

    ```javascript
    function popShift(arr) {
        let popped = arr.pop(); // change this line
        let shifted = arr.shift(); // change this line
        return [shifted, popped];
    }

    // do not change code below this line
    console.log(popShift(['challenge', 'is', 'not', 'complete']));
    ```

1. Remove Items Using splice()

    ```javascript
    function sumOfTen(arr) {
        // change code below this line
        arr.splice(2,2);
        // change code above this line
        return arr.reduce((a, b) => a + b);
    }

    // do not change code below this line
    console.log(sumOfTen([2, 5, 1, 5, 2, 1]));
    ```

1. Add Items Using splice()

    ```javascript
    function htmlColorNames(arr) {
        // change code below this line
        arr.splice(0, 2, 'DarkSalmon', 'BlanchedAlmond');
        // change code above this line
        return arr;
    }
    // do not change code below this line
    console.log(htmlColorNames(['DarkGoldenRod', 'WhiteSmoke', 'LavenderBlush', 'PaleTurqoise', 'FireBrick']));
    ```

1. Copy Array Items Using slice()

    ```javascript
    function forecast(arr) {
        // change code below this line
        return arr.slice(2,4);
    }

    // do not change code below this line
    console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
    ```

1. Copy an Array with the Spread Operator

    ```javascript
    function copyMachine(arr, num) {
        let newArr = [];
        while (num >= 1) {
            // change code below this line
            let tempArr = [...arr];
            newArr.push(tempArr);
            // change code above this line
            num--;
        }
        return newArr;
    }

    // change code here to test different cases:
    console.log(copyMachine([true, false, true], 2));
    ```

1. Combine Arrays with the Spread Operator

    ```javascript
    function spreadOut() {
        let fragment = ['to', 'code'];
        let sentence = ['learning', ...fragment, 'is', 'fun']; // change this line
        return sentence;
    }

    // do not change code below this line
    console.log(spreadOut());
    ```

1. Check For The Presence of an Element With indexOf()

    ```javascript
    function quickCheck(arr, elem) {
        // change code below this line
        return arr.indexOf(elem) == -1 ? false : true;
        // change code above this line
    }

    // change code here to test different cases:
    console.log(quickCheck(['squash', 'onions', 'shallots'], 'mushrooms'));
    ```

1. Iterate Through All an Array's Items Using For Loops

    ```javascript
    function filteredArray(arr, elem) {
        let newArr = [];
        // change code below this line
        for(let i=0; i<arr.length; i++){
            if(arr[i].indexOf(elem) != -1)
            continue;
            newArr.push([...arr[i]]);
        }
        // change code above this line
        return newArr;
    }

    // change code here to test different cases:
    console.log(filteredArray([[3, 2, 3], [1, 6, 3], [3, 13, 26], [19, 3, 9]], 3));
    ```

1. Create complex multi-dimensional arrays

    ```javascript
    let myNestedArray = [
        // change code below this line
        [['deep',['deeper', ['deepest']]]]
        // change code above this line
    ];
    ```

1. Add Key-Value Pairs to JavaScript Objects

    ```javascript
    let foods = {
        apples: 25,
        oranges: 32,
        plums: 28
    };

    // change code below this line
    foods.bananas = 13;
    foods['grapes'] = 35;
    foods['strawberries'] = 27;
    // change code above this line

    console.log(foods);
    ```

1. Modify an Object Nested Within an Object

    ```javascript
    let userActivity = {
        id: 23894201352,
        date: 'January 1, 2017',
        data: {
            totalUsers: 51,
            online: 42
        }
    };

    // change code below this line
    userActivity.data.online = 45;
    // change code above this line

    console.log(userActivity);
    ```

1. Access Property Names with Bracket Notation

    ```javascript
    let foods = {
        apples: 25,
        oranges: 32,
        plums: 28,
        bananas: 13,
        grapes: 35,
        strawberries: 27
    };
    // do not change code above this line

    function checkInventory(scannedItem) {
        // change code below this line
        return foods[scannedItem];
    }

    // change code below this line to test different cases:
    console.log(checkInventory("oranges"));
    ```

1. Use the delete Keyword to Remove Object Properties

    ```javascript
    let foods = {
        apples: 25,
        oranges: 32,
        plums: 28,
        bananas: 13,
        grapes: 35,
        strawberries: 27
    };

    // change code below this line
    delete foods.oranges;
    delete foods.plums;
    delete foods.strawberries;
    // change code above this line

    console.log(foods);
    ```

1. Check if an Object has a Property

    ```javascript
    let users = {
        Alan: {
            age: 27,
            online: true
        },
        Jeff: {
            age: 32,
            online: true
        },
        Sarah: {
            age: 48,
            online: true
        },
        Ryan: {
            age: 19,
            online: true
        }
    };

    function isEveryoneHere(obj) {
        // change code below this line
        if(obj.hasOwnProperty('Alan') && obj.hasOwnProperty('Jeff') && obj.hasOwnProperty('Sarah') && obj.hasOwnProperty('Ryan'))
            return true;
        return false;
        // change code above this line
    }

    console.log(isEveryoneHere(users));
    ```

1. Iterate Through the Keys of an Object with a for...in Statement

    ```javascript
    let users = {
        Alan: {
            age: 27,
            online: false
        },
        Jeff: {
            age: 32,
            online: true
        },
        Sarah: {
            age: 48,
            online: false
        },
        Ryan: {
            age: 19,
            online: true
        }
    };

    function countOnline(obj) {
    // change code below this line
    let count =0;
    for(let user in obj){
        if(obj[user].online)
        count++;
    }
    return count;
    // change code above this line
    }

    console.log(countOnline(users));
    ```

1. Generate an Array of All Object Keys with Object.keys()

    ```javascript
    let users = {
        Alan: {
            age: 27,
            online: false
        },
        Jeff: {
            age: 32,
            online: true
        },
        Sarah: {
            age: 48,
            online: false
        },
        Ryan: {
            age: 19,
            online: true
        }
    };

    function getArrayOfUsers(obj) {
    // change code below this line
    return Object.keys(obj);
    // change code above this line
    }

    console.log(getArrayOfUsers(users));
    ```

1. Modify an Array Stored in an Object

    ```javascript
    let user = {
        name: 'Kenneth',
        age: 28,
        data: {
            username: 'kennethCodesAllDay',
            joinDate: 'March 26, 2016',
            organization: 'freeCodeCamp',
            friends: [
            'Sam',
            'Kira',
            'Tomo'
            ],
            location: {
            city: 'San Francisco',
            state: 'CA',
            country: 'USA'
            }
        }
    };

    function addFriend(userObj, friend) {
    // change code below this line  
    userObj.data.friends.push(friend);
    return userObj.data.friends;
    // change code above this line
    }

    console.log(addFriend(user, 'Pete'));
    ```

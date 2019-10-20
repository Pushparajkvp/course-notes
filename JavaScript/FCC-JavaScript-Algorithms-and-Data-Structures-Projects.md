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
    1. Notations
        1. I -> 1
        1. V -> 5
        1. X -> 10
        1. L -> 50
        1. C -> 100
        1. D -> 500
        1. M -> 1000
    1. VI -> 6 (Add when going from big number to small number)
    1. IV -> 4 (Sub when going from small nuber to big number)

    ```javascript
    function convertToRomanAlt(num) {
        let romanLetters = ["M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"];
        let romanValues = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
        let i=0, result="";
        while(num>0){
            if(num-romanValues[i]>=0){
                result+=romanLetters[i];
                num-=romanValues[i];
            }else{
                i++;
            }
        }
        return result;
    }
    function convertToRoman(num){
        let romanLetters = ["I","V","X","L","C","D","M"];
        let result="",i=0;
        while(num>0){
            let digit = num%10;
            let currentRomanBase10 = romanLetters[i*2];
            let nextRomanBase10 = romanLetters[i*2+1];
            let thirdRomanBase10 = romanLetters[i*2+2];
            switch(digit){
                case 1: result = currentRomanBase10 + result; break;
                case 2: result = currentRomanBase10.repeat(2) + result; break;
                case 3: result = currentRomanBase10.repeat(3) + result; break;
                case 4: result = currentRomanBase10 + nextRomanBase10 + result; break;
                case 5: result = nextRomanBase10 + result; break;
                case 6: result = nextRomanBase10 + currentRomanBase10 + result; break;
                case 7: result = nextRomanBase10 + currentRomanBase10.repeat(2) + result; break;
                case 8: result = nextRomanBase10 + currentRomanBase10.repeat(3) + result; break;
                case 9: result = currentRomanBase10 + thirdRomanBase10 + result; break;
            }
            i++;
            num=parseInt(num/10);
        }
        return result;
    }
    convertToRoman(36);

    ```

1. Caesars Cipher

    ```javascript
    function rot13(str) { // LBH QVQ VG!
        return str.replace(/[A-Z]/g,find=> String.fromCharCode(find.charCodeAt(0)%26 + 65));
    }
    // Change the inputs below to test
    rot13("SERR PBQR PNZC");

    ```

1. Telephone Number Validator

    ```javascript
    function telephoneCheck(str) {
        let regex = /^([+]?1[\s]?)?((?:[(](?:[2-9]1[02-9]|[2-9][02-8][0-9])[)][\s]?)|(?:(?:[2-9]1[02-9]|[2-9][02-8][0-9])[\s.-]?)){1}([2-9]1[02-9]|[2-9][02-9]1|[2-9][02-9]{2}[\s.-]?){1}([0-9]{4}){1}$/;
        return regex.test(str);
    }

    telephoneCheck("555-555-5555");

    ```

1. Cash Register

    ```javascript
    // Create an array of objects which hold the denominations and their values
    var denom = [
    { name: "ONE HUNDRED", val: 100.0 },
    { name: "TWENTY", val: 20.0 },
    { name: "TEN", val: 10.0 },
    { name: "FIVE", val: 5.0 },
    { name: "ONE", val: 1.0 },
    { name: "QUARTER", val: 0.25 },
    { name: "DIME", val: 0.1 },
    { name: "NICKEL", val: 0.05 },
    { name: "PENNY", val: 0.01 }
    ];

    function checkCashRegister(price, cash, cid) {
    var output = { status: null, change: [] };
    var change = cash - price;

    var register = cid.reduce(
        function(acc, curr) {
        acc.total += curr[1];
        acc[curr[0]] = curr[1];
        return acc;
        },
        { total: 0 }
    );
    if (register.total === change) {
        output.status = "CLOSED";
        output.change = cid;
        return output;
    }
    if (register.total < change) {
        output.status = "INSUFFICIENT_FUNDS";
        return output;
    }

    var change_arr = denom.reduce(function(acc, curr) {
        var value = 0;
        while (register[curr.name] > 0 && change >= curr.val) {
        change -= curr.val;
        register[curr.name] -= curr.val;
        value += curr.val;
        change = Math.round(change * 100) / 100;
        }
        if (value > 0) {
        acc.push([curr.name, value]);
        }
        return acc;
    }, []);
    if (change_arr.length < 1 || change > 0) {
        output.status = "INSUFFICIENT_FUNDS";
        return output;
    }
    output.status = "OPEN";
    output.change = change_arr;
    return output;
    }

    // Example cash-in-drawer array:
    // [["PENNY", 1.01],
    // ["NICKEL", 2.05],
    // ["DIME", 3.1],
    // ["QUARTER", 4.25],
    // ["ONE", 90],
    // ["FIVE", 55],
    // ["TEN", 20],
    // ["TWENTY", 60],
    // ["ONE HUNDRED", 100]]

    checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);

    ```

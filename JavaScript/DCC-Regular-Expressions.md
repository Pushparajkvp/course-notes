# Regular Expressions

1. Using the Test Method

    ```javascript
    let myString = "Hello, World!";
    let myRegex = /Hello/;
    let result = myRegex.test(myString); // Change this line
    ```

1. Match Literal Strings

    ```javascript
    let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
    let waldoRegex = /Waldo/; // Change this line
    let result = waldoRegex.test(waldoIsHiding);
    ```

1. Match a Literal String with Different Possibilities

    ```javascript
    let petString = "James has a pet cat.";
    let petRegex = /dog|cat|bird|fish/; // Change this line
    let result = petRegex.test(petString);
    ```

1. Ignore Case While Matching

    ```javascript
    let myString = "freeCodeCamp";
    let fccRegex = /freeCodeCamp/i; // Change this line
    let result = fccRegex.test(myString);
    ```

1. Extract Matches

    ```javascript
    let extractStr = "Extract the word 'coding' from this string.";
    let codingRegex = /coding/; // Change this line
    let result = extractStr.match(codingRegex); // Change this line
    ```

1. Find More Than the First Match

    ```javascript
    let twinkleStar = "Twinkle, twinkle, little star";
    let starRegex = /Twinkle/ig; // Change this line
    let result = twinkleStar.match(starRegex); // Change this line
    ```

1. Match Anything with Wildcard Period

    ```javascript
    let exampleStr = "Let's have fun with regular expressions!";
    let unRegex = /.un/; // Change this line
    let result = unRegex.test(exampleStr);
    ```

1. Match Single Character with Multiple Possibilities

    ```javascript
    let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
    let vowelRegex = /[aeiou]/ig; // Change this line
    let result = quoteSample.match(vowelRegex); // Change this line
    ```

1. Match Letters of the Alphabet

    ```javascript
    let quoteSample = "The quick brown fox jumps over the lazy dog.";
    let alphabetRegex = /[a-zA-Z]/ig; // Change this line
    let result = quoteSample.match(alphabetRegex); // Change this line
    ```

1. Match Numbers and Letters of the Alphabet

    ```javascript
    let quoteSample = "Blueberry 3.141592653s are delicious.";
    let myRegex = /[h-s2-6]/ig; // Change this line
    let result = quoteSample.match(myRegex); // Change this line
    ```

1. Match Single Characters Not Specified

    ```javascript
    let quoteSample = "3 blind mice.";
    let myRegex = /[^0-9aeiou]/ig; // Change this line
    let result = quoteSample.match(myRegex); // Change this line
    ```

1. Match Characters that Occur One or More Times

    ```javascript
    let difficultSpelling = "Mississippi";
    let myRegex = /s+/ig; // Change this line
    let result = difficultSpelling.match(myRegex);
    ```

1. Match Characters that Occur Zero or More Times

    ```javascript
    let chewieQuote = "Aaaaaaaaaaaaaaaarrrgh!";
    let chewieRegex = /Aa*/; // Change this line
    let result = chewieQuote.match(chewieRegex);
    ```

1. Find Characters with Lazy Matching (Default is greedy)

    ```javascript
    let text = "<h1>Winter is coming</h1>";
    let myRegex = /<.*?>/; // Change this line
    let result = text.match(myRegex);
    ```

1. Find One or More Criminals in a Hunt

    ```javascript
    // example crowd gathering
    let crowd = 'P1P2P3P4P5P6CCCP7P8P9';

    let reCriminals = /C+/; // Change this line

    let matchedCriminals = crowd.match(reCriminals);
    console.log(matchedCriminals);
    ```

1. Match Beginning String Patterns

    ```javascript
    let rickyAndCal = "Cal and Ricky both like racing.";
    let calRegex = /^Cal/; // Change this line
    let result = calRegex.test(rickyAndCal);
    ```

1. Match Ending String Patterns

    ```javascript
    let caboose = "The last car on a train is the caboose";
    let lastRegex = /caboose$/; // Change this line
    let result = lastRegex.test(caboose);
    ```

1. Match All Letters and Numbers

    ```javascript
    let quoteSample = "The five boxing wizards jump quickly.";
    let alphabetRegexV2 = /\w/g; // [A-Za-z0-9_]
    let result = quoteSample.match(alphabetRegexV2).length;
    ```

1. Match Everything But Letters and Numbers

    ```javascript
    let quoteSample = "The five boxing wizards jump quickly.";
    let nonAlphabetRegex = /\W/g; // [^A-Za-z0-9_]
    let result = quoteSample.match(nonAlphabetRegex).length;
    ```

1. Match All Numbers

    ```javascript
    let numString = "Your sandwich will be $5.00";
    let numRegex = /\d/g; // [0-9]
    let result = numString.match(numRegex).length;
    ```

1. Match All Non-Numbers

    ```javascript
    let numString = "Your sandwich will be $5.00";
    let noNumRegex = /\D/g; // [^0-9]
    let result = numString.match(noNumRegex).length;
    ```

1. Restrict Possible Usernames

    ```javascript
    let username = "JackOfAllTrades";
    let userCheck = /^[a-z]{2,}[0-9]*$/i; // Change this line
    let result = userCheck.test(username);
    ```

1. Match Whitespace (\s -> [ \r\t\f\n\v])

    ```javascript
    let sample = "Whitespace is important in separating words";
    let countWhiteSpace = /\s/g; // Change this line
    let result = sample.match(countWhiteSpace);
    ```

1. Match Non-Whitespace Characters (\S -> [^ \r\t\f\n\v])

    ```javascript
    let sample = "Whitespace is important in separating words";
    let countNonWhiteSpace = /\S/g; // Change this line
    let result = sample.match(countNonWhiteSpace);
    ```

1. Specify Upper and Lower Number of Matches (quantity specifiers)

    ```javascript
    let ohStr = "Ohhh no";
    let ohRegex = /Oh{3,6}\sno/; // Change this line
    let result = ohRegex.test(ohStr);
    ```

1. Specify Only the Lower Number of Matches

    ```javascript
    let haStr = "Hazzzzah";
    let haRegex = /Haz{4,}ah/; // Change this line
    let result = haRegex.test(haStr);
    ```

1. Specify Exact Number of Matches

    ```javascript
    let timStr = "Timmmmber";
    let timRegex = /Tim{4}ber/; // Change this line
    let result = timRegex.test(timStr);
    ```

1. Check for All or None

    ```javascript
    let favWord = "favorite";
    let favRegex = /favou?rite/; // Change this line
    let result = favRegex.test(favWord);
    ```

1. Positive and Negative Lookahead (My understanding -> check but don't match)

    ```javascript
    let sampleWord = "astronaut";
    let pwRegex = /(?=\w{5,})(?=\D*\d{2,})/; // Change this line
    let result = pwRegex.test(sampleWord);
    ```

1. Reuse Patterns Using Capture Groups

    ```javascript
    let repeatNum = "42 42 42";
    let reRegex = /^(\d+)\s\1\s\1$/; // Change this line
    let result = reRegex.test(repeatNum);
    ```

1. Use Capture Groups to Search and Replace

    ```javascript
    let huhText = "This sandwich is good.";
    let fixRegex = /good/; // Change this line
    let replaceText = "okey-dokey"; // Change this line
    let result = huhText.replace(fixRegex, replaceText);
    ```

1. Remove Whitespace from Start and End

    ```javascript
    let hello = "   Hello, World!  ";
    let wsRegex = /^\s+(.*?)\s+$/; // Change this line
    let result = hello.replace(wsRegex,"$1"); // Change this line
    ```

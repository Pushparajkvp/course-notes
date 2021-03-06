# Functional Programming

1. Learn About Functional Programming

    ```javascript
    /**
    * A long process to prepare tea.
    * @return {string} A cup of tea.
    **/
   const prepareTea = () => 'greenTea';

   /**
    * Get given number of cups of tea.
    * @param {number} numOfCups Number of required cups of tea.
    * @return {Array<string>} Given amount of tea cups.
    **/
   const getTea = (numOfCups) => {
     const teaCups = [];

     for(let cups = 1; cups <= numOfCups; cups += 1) {
       const teaCup = prepareTea();
       teaCups.push(teaCup);
     }

     return teaCups;
   };

   // Add your code below this line

   const tea4TeamFCC = null; // :(

   // Add your code above this line

   console.log(tea4TeamFCC);
    ```

1. Understand Functional Programming Terminology
   1. First Class Function - Functions that can be assigned to a variable, passed into another function, or returned from another function just like any other normal value, are called first classfunctions
   2. Higer Order Functions - The functions that take a function as an argument, or return a function as a return value are called higher orderfunctions.
   3. lambda - When the functions are passed in to another function or returned from another function, then those functions which gets passed in or returned can be called a lambda.

    ```javascript
    /**
    * A long process to prepare green tea.
    * @return {string} A cup of green tea.
    **/
   const prepareGreenTea = () => 'greenTea';

   /**
    * A long process to prepare black tea.
    * @return {string} A cup of black tea.
    **/
   const prepareBlackTea = () => 'blackTea';

   /**
    * Get given number of cups of tea.
    * @param {function():string} prepareTea The type of tea preparing function.
    * @param {number} numOfCups Number of required cups of tea.
    * @return {Array<string>} Given amount of tea cups.
    **/
   const getTea = (prepareTea, numOfCups) => {
     const teaCups = [];

     for(let cups = 1; cups <= numOfCups; cups += 1) {
       const teaCup = prepareTea();
       teaCups.push(teaCup);
     }

     return teaCups;
   };

   // Add your code below this line

   const tea4GreenTeamFCC = getTea(prepareGreenTea,27); // :(
   const tea4BlackTeamFCC = getTea(prepareBlackTea, 13); // :(

   // Add your code above this line

   console.log(
     tea4GreenTeamFCC,
     tea4BlackTeamFCC
   );
    ```

1. Understand the Hazards of Using Imperative Code

    ```javascript
    // tabs is an array of titles of each site open within the window
    var Window = function(tabs) {
    this.tabs = tabs; // we keep a record of the array inside the object
    };

    // When you join two windows into one window
    Window.prototype.join = function (otherWindow) {
    this.tabs = this.tabs.concat(otherWindow.tabs);
    return this;
    };

    // When you open a new tab at the end
    Window.prototype.tabOpen = function (tab) {
    this.tabs.push('new tab'); // let's open a new tab for now
    return this;
    };

    // When you close a tab
    Window.prototype.tabClose = function (index) {
    var tabsBeforeIndex = this.tabs.slice(0, index); // get the tabs before the tab
    var tabsAfterIndex = this.tabs.slice(index); // get the tabs after the tab

    this.tabs = tabsBeforeIndex.concat(tabsAfterIndex); // join them together 
    return this;
    };

    // Let's create three browser windows
    var workWindow = new Window(['GMail', 'Inbox', 'Work mail', 'Docs', 'freeCodeCamp']); // Your mailbox, drive, and other work sites
    var socialWindow = new Window(['FB', 'Gitter', 'Reddit', 'Twitter', 'Medium']); // Social sites
    var videoWindow = new Window(['Netflix', 'YouTube', 'Vimeo', 'Vine']); //  Entertainment sites

    // Now perform the tab opening, closing, and other operations
    var finalTabs = socialWindow
                        .tabOpen() // Open a new tab for cat memes
                        .join(videoWindow.tabClose(2)) // Close third tab in video window, and join
                        .join(workWindow.tabClose(1).tabOpen());

    console.log(finalTabs.tabs);
    ```

1. Avoid Mutations and Side Effects Using Functional Programming
   1. One of the core principle of functional programming is to not change things. Changes lead to bugs. It's easier to prevent bugs knowing that your functions don't change anything, including the function arguments or any global variable.
   2. pure function, meaning that it does not cause any side effects.

    ```javascript
    // the global variable
    var fixedValue = 4;

    function incrementer () {
        return fixedValue + 1;
    }

    var newValue = incrementer(); // Should equal 5
    console.log(fixedValue); // Should print 4
    ```

1. Pass Arguments to Avoid External Dependence in a Function
   1. Always declare your dependencies explicitly. This means if a function depends on a variable or object being present, then pass that variable or object directly into the function as an argument.
   2. The function is easier to test, you know exactly what input it takes, and it won't depend on anything else in your program.

    ```javascript
    // the global variable
    var fixedValue = 4;
    function incrementer (fixedValue) {
        return fixedValue+1;
    }
    var newValue = incrementer(fixedValue); // Should equal 5
    console.log(fixedValue); // Should print 4
    ```

1. Refactor Global Variables Out of Functions

    ```javascript
    // the global variable
    var bookList = ["The Hound of the Baskervilles", "On The Electrodynamics of Moving Bodies", "Philosophiæ Naturalis Principia Mathematica", "Disquisitiones Arithmeticae"];

    /* This function should add a book to the list and return the list */
    // New parameters should come before the bookName one

    // Add your code below this line
    function add (bookList,bookName) {
        return [...bookList, bookName];
        // Add your code above this line
    }

    /* This function should remove a book from the list and return the list */
    // New parameters should come before the bookName one

    // Add your code below this line
    function remove (bookList,bookName) {
    if (bookList.indexOf(bookName) >= 0) {
        return bookList.slice(0, bookList.indexOf(bookName)).concat(bookList.slice(bookList.indexOf(bookName)+1));
        // Add your code above this line
        }
    }

    var newBookList = add(bookList, 'A Brief History of Time');
    var newerBookList = remove(bookList, 'On The Electrodynamics of Moving Bodies');
    var newestBookList = remove(add(bookList, 'A Brief History of Time'), 'On The Electrodynamics of Moving Bodies');

    console.log(bookList);
    //["The Hound of the Baskervilles", "Philosophiæ Naturalis Principia Mathematica", "Disquisitiones Arithmeticae"]
    ```

1. Use the map Method to Extract Data from an Array

    ```javascript
    // the global variable
    var watchList = [
                    {  
                    "Title": "Inception",
                    "Year": "2010",
                    "Rated": "PG-13",
                    "Released": "16 Jul 2010",
                    "Runtime": "148 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Christopher Nolan",
                    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Ellen Page, Tom Hardy",
                    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
                    "Language": "English, Japanese, French",
                    "Country": "USA, UK",
                    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.8",
                    "imdbVotes": "1,446,708",
                    "imdbID": "tt1375666",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Interstellar",
                    "Year": "2014",
                    "Rated": "PG-13",
                    "Released": "07 Nov 2014",
                    "Runtime": "169 min",
                    "Genre": "Adventure, Drama, Sci-Fi",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan, Christopher Nolan",
                    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
                    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
                    "Language": "English",
                    "Country": "USA, UK",
                    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.6",
                    "imdbVotes": "910,366",
                    "imdbID": "tt0816692",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "The Dark Knight",
                    "Year": "2008",
                    "Rated": "PG-13",
                    "Released": "18 Jul 2008",
                    "Runtime": "152 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
                    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
                    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
                    "Language": "English, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
                    "Metascore": "82",
                    "imdbRating": "9.0",
                    "imdbVotes": "1,652,832",
                    "imdbID": "tt0468569",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Batman Begins",
                    "Year": "2005",
                    "Rated": "PG-13",
                    "Released": "15 Jun 2005",
                    "Runtime": "140 min",
                    "Genre": "Action, Adventure",
                    "Director": "Christopher Nolan",
                    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
                    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
                    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
                    "Language": "English, Urdu, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
                    "Metascore": "70",
                    "imdbRating": "8.3",
                    "imdbVotes": "972,584",
                    "imdbID": "tt0372784",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "Avatar",
                    "Year": "2009",
                    "Rated": "PG-13",
                    "Released": "18 Dec 2009",
                    "Runtime": "162 min",
                    "Genre": "Action, Adventure, Fantasy",
                    "Director": "James Cameron",
                    "Writer": "James Cameron",
                    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
                    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
                    "Language": "English, Spanish",
                    "Country": "USA, UK",
                    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
                    "Metascore": "83",
                    "imdbRating": "7.9",
                    "imdbVotes": "876,575",
                    "imdbID": "tt0499549",
                    "Type": "movie",
                    "Response": "True"
                    }
    ];

    // Add your code below this line

    var rating = watchList.map((obj) => { return {title: obj.Title, rating: obj.imdbRating}});
    // Add your code above this line

    console.log(rating);
    ```

1. Implement map on a Prototype

    ```javascript
    // the global Array
    var s = [23, 65, 98, 5];

    Array.prototype.myMap = function(callback){
        var newArray = [];
        // Add your code below this line
        this.forEach((item)=> newArray.push(callback(item)));
        // Add your code above this line
        return newArray;

    };

    var new_s = s.myMap(function(item){
    return item * 2;
    });
    ```

1. Use the filter Method to Extract Data from an Array

    ```javascript
    // the global variable
    var watchList = [
                    {  
                    "Title": "Inception",
                    "Year": "2010",
                    "Rated": "PG-13",
                    "Released": "16 Jul 2010",
                    "Runtime": "148 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Christopher Nolan",
                    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Ellen Page, Tom Hardy",
                    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
                    "Language": "English, Japanese, French",
                    "Country": "USA, UK",
                    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.8",
                    "imdbVotes": "1,446,708",
                    "imdbID": "tt1375666",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Interstellar",
                    "Year": "2014",
                    "Rated": "PG-13",
                    "Released": "07 Nov 2014",
                    "Runtime": "169 min",
                    "Genre": "Adventure, Drama, Sci-Fi",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan, Christopher Nolan",
                    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
                    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
                    "Language": "English",
                    "Country": "USA, UK",
                    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.6",
                    "imdbVotes": "910,366",
                    "imdbID": "tt0816692",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "The Dark Knight",
                    "Year": "2008",
                    "Rated": "PG-13",
                    "Released": "18 Jul 2008",
                    "Runtime": "152 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
                    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
                    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
                    "Language": "English, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
                    "Metascore": "82",
                    "imdbRating": "9.0",
                    "imdbVotes": "1,652,832",
                    "imdbID": "tt0468569",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Batman Begins",
                    "Year": "2005",
                    "Rated": "PG-13",
                    "Released": "15 Jun 2005",
                    "Runtime": "140 min",
                    "Genre": "Action, Adventure",
                    "Director": "Christopher Nolan",
                    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
                    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
                    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
                    "Language": "English, Urdu, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
                    "Metascore": "70",
                    "imdbRating": "8.3",
                    "imdbVotes": "972,584",
                    "imdbID": "tt0372784",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "Avatar",
                    "Year": "2009",
                    "Rated": "PG-13",
                    "Released": "18 Dec 2009",
                    "Runtime": "162 min",
                    "Genre": "Action, Adventure, Fantasy",
                    "Director": "James Cameron",
                    "Writer": "James Cameron",
                    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
                    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
                    "Language": "English, Spanish",
                    "Country": "USA, UK",
                    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
                    "Metascore": "83",
                    "imdbRating": "7.9",
                    "imdbVotes": "876,575",
                    "imdbID": "tt0499549",
                    "Type": "movie",
                    "Response": "True"
                    }
    ];

    // Add your code below this line

    var filteredList = watchList.map( (obj)=> { return {title: obj.Title, rating: obj.imdbRating}}).filter((obj) => obj.rating >= 8.0);

    // Add your code above this line

    console.log(filteredList);
    ```

1. Implement the filter Method on a Prototype

    ```javascript
    // the global Array
    var s = [23, 65, 98, 5];

    Array.prototype.myFilter = function(callback){
        var newArray = [];
        // Add your code below this line
        this.forEach((item) => {if(callback(item)) newArray.push(item)});
        // Add your code above this line
        return newArray;

    };

    var new_s = s.myFilter(function(item){
        return item % 2 === 1;
    });
    ```

1. Return Part of an Array Using the slice Method

    ```javascript
    function sliceArray(anim, beginSlice, endSlice) {
        // Add your code below this line

        return anim.slice(beginSlice, endSlice);
        // Add your code above this line
    }
    var inputAnim = ["Cat", "Dog", "Tiger", "Zebra", "Ant"];
    sliceArray(inputAnim, 1, 3);
    ```

1. Remove Elements from an Array Using slice Instead of splice

    ```javascript
    function nonMutatingSplice(cities) {
        // Add your code below this line
        return cities.slice(0,3);
        // Add your code above this line
    }
    var inputCities = ["Chicago", "Delhi", "Islamabad", "London", "Berlin"];
    nonMutatingSplice(inputCities);
    ```

1. Combine Two Arrays Using the concat Method

    ```javascript
    function nonMutatingConcat(original, attach) {
        // Add your code below this line
        return original.concat(attach);
        // Add your code above this line
    }
    var first = [1, 2, 3];
    var second = [4, 5];
    nonMutatingConcat(first, second);
    ```

1. Add Elements to the End of an Array Using concat Instead of push

    ```javascript
    function nonMutatingPush(original, newItem) {
        // Add your code below this line
        return original.concat(newItem);

        // Add your code above this line
    }
    var first = [1, 2, 3];
    var second = [4, 5];
    nonMutatingPush(first, second);
    ```

1. Use the reduce Method to Analyze Data

    ```javascript
    // the global variable
    var watchList = [
                    {  
                    "Title": "Inception",
                    "Year": "2010",
                    "Rated": "PG-13",
                    "Released": "16 Jul 2010",
                    "Runtime": "148 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Christopher Nolan",
                    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Ellen Page, Tom Hardy",
                    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
                    "Language": "English, Japanese, French",
                    "Country": "USA, UK",
                    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.8",
                    "imdbVotes": "1,446,708",
                    "imdbID": "tt1375666",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Interstellar",
                    "Year": "2014",
                    "Rated": "PG-13",
                    "Released": "07 Nov 2014",
                    "Runtime": "169 min",
                    "Genre": "Adventure, Drama, Sci-Fi",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan, Christopher Nolan",
                    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
                    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
                    "Language": "English",
                    "Country": "USA, UK",
                    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
                    "Metascore": "74",
                    "imdbRating": "8.6",
                    "imdbVotes": "910,366",
                    "imdbID": "tt0816692",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "The Dark Knight",
                    "Year": "2008",
                    "Rated": "PG-13",
                    "Released": "18 Jul 2008",
                    "Runtime": "152 min",
                    "Genre": "Action, Adventure, Crime",
                    "Director": "Christopher Nolan",
                    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
                    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
                    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
                    "Language": "English, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
                    "Metascore": "82",
                    "imdbRating": "9.0",
                    "imdbVotes": "1,652,832",
                    "imdbID": "tt0468569",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {  
                    "Title": "Batman Begins",
                    "Year": "2005",
                    "Rated": "PG-13",
                    "Released": "15 Jun 2005",
                    "Runtime": "140 min",
                    "Genre": "Action, Adventure",
                    "Director": "Christopher Nolan",
                    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
                    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
                    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
                    "Language": "English, Urdu, Mandarin",
                    "Country": "USA, UK",
                    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
                    "Metascore": "70",
                    "imdbRating": "8.3",
                    "imdbVotes": "972,584",
                    "imdbID": "tt0372784",
                    "Type": "movie",
                    "Response": "True"
                    },
                    {
                    "Title": "Avatar",
                    "Year": "2009",
                    "Rated": "PG-13",
                    "Released": "18 Dec 2009",
                    "Runtime": "162 min",
                    "Genre": "Action, Adventure, Fantasy",
                    "Director": "James Cameron",
                    "Writer": "James Cameron",
                    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
                    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
                    "Language": "English, Spanish",
                    "Country": "USA, UK",
                    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
                    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
                    "Metascore": "83",
                    "imdbRating": "7.9",
                    "imdbVotes": "876,575",
                    "imdbID": "tt0499549",
                    "Type": "movie",
                    "Response": "True"
                    }
    ];

    // Add your code below this line

    var averageRating = watchList.filter(obj => obj.Director === 'Christopher Nolan').map(obj => Number(obj.imdbRating)).reduce((v1, v2) => v1+v2)/ watchList.filter(obj => obj.Director === 'Christopher Nolan').length;

    // Add your code above this line

    console.log(averageRating);
    ```

1. Sort an Array Alphabetically using the sort Method
    1. Default sort function sorts using unicodes.

    ```javascript
    function alphabeticalOrder(arr) {
        // Add your code below this line
        return arr.sort();
        // Add your code above this line
    }
    alphabeticalOrder(["a", "d", "c", "a", "z", "g"]);
    ```

1. Return a Sorted Array Without Changing the Original Array

    ```javascript
    var globalArray = [5, 6, 3, 2, 9];
    function nonMutatingSort(arr) {
        // Add your code below this line
        return [].concat(arr).sort();
        // Add your code above this line
    }
    nonMutatingSort(globalArray);
    ```

1. Split a String into an Array Using the split Method

    ```javascript
    function splitify(str) {
        // Add your code below this line
        return str.split(/[^a-zA-Z]/);
        // Add your code above this line
    }
    console.log(splitify("Hello World,I-am code"));
    ```

1. Combine an Array into a String Using the join Method

    ```javascript
    function sentensify(str) {
        // Add your code below this line
        return str.split(/[^a-zA-Z]/).join(" ");
        // Add your code above this line
    }
    sentensify("May-the-force-be-with-you");
    ```

1. Apply Functional Programming to Convert Strings to URL Slugs

    ```javascript
    // the global variable
    var globalTitle = "Winter Is Coming";

    // Add your code below this line
    function urlSlug(title) {
        return title.split(/[^a-zA-Z]/).filter((obj)=> obj !== " " && obj !== "").map( value => value.toLowerCase()).join("-"); 
    }
    // Add your code above this line

    var winterComing = urlSlug(globalTitle); // Should be "winter-is-coming"
    ```

1. Use the every Method to Check that Every Element in an Array Meets a Criteria

    ```javascript
    function checkPositive(arr) {
        // Add your code below this line
        return arr.every((value) => { return value>=0});
        // Add your code above this line
    }
    checkPositive([1, 2, 3, -4, 5]);
    ```

1. Use the some Method to Check that Any Elements in an Array Meet a Criteria

    ```javascript
    function checkPositive(arr) {
        // Add your code below this line
        return arr.some((value) => value>=0);
        // Add your code above this line
    }
    checkPositive([1, 2, 3, -4, 5]);
    ```

1. Introduction to Currying and Partial Application
    1. The arityof a function is the number of arguments it requires. Curryinga function means to convert a function of N arityinto N functions of arity1.
    1. Similarly, partial applicationcan be described as applying a few arguments to a function at a time and returning another function that is applied to more arguments.

    ```javascript
    function add(x) {
        // Add your code below this line
        return function(y){
            return function(z){
            return x+y+z;
            }
        }
        // Add your code above this line
    }
    add(10)(20)(30);
    ```

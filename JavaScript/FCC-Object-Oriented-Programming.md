# Object Oriented Programming

1. Create a Basic JavaScript Object

    ```javascript
    let dog = {
        name: "test",
        numLegs: 1
    };
    ```

1. Use Dot Notation to Access the Properties of an Object

    ```javascript
    let dog = {
        name: "Spot",
        numLegs: 4
    };
    // Add your code below this line
    console.log(dog.name);
    console.log(dog.numLegs);
    ```

1. Make Code More Reusable with the this Keyword

    ```javascript
    let dog = {
        name: "Spot",
        numLegs: 4,
        sayLegs: function() {return "This dog has " + this.numLegs + " legs.";}
    };

    dog.sayLegs();
    ```

1. Define a Constructor Function

    ```javascript
    function Dog(){
        this.name = "test",
        this.color = "blue",
        this.numLegs = 2
    }
    ```

1. Use a Constructor to Create Objects

    ```javascript
    function Dog() {
        this.name = "Rupert";
        this.color = "brown";
        this.numLegs = 4;
    }
    // Add your code below this line
    let hound = new Dog();
    ```

1. Extend Constructors to Receive Arguments

    ```javascript
    function Dog(name, color) {
        this.numLegs= 4;
        this.name= name;
        this.color= color;
    }
    let terrier = new Dog("test", "blue");

    ```

1. Verify an Object's Constructor with instanceof

    ```javascript
    /* jshint expr: true */

    function House(numBedrooms) {
        this.numBedrooms = numBedrooms;
    }

    // Add your code below this line
    let myHouse = new House(2);
    myHouse instanceof House;

    ```

1. Understand Own Properties

    ```javascript
    function Bird(name) {
        this.name = name;
        this.numLegs = 2;
    }

    let canary = new Bird("Tweety");
    let ownProps = [];
    // Add your code below this line

    for(let property in canary){
        ownProps.push(property);
    }
    ```

1. Use Prototype Properties to Reduce Duplicate Code

    ```javascript
    function Dog(name) {
        this.name = name;
    }
    // Add your code above this line
    let beagle = new Dog("Snoopy");
    Dog.prototype.numLegs = 3;
    ```

1. Iterate Over All Properties

    ```javascript
    function Dog(name) {
        this.name = name;
    }
    Dog.prototype.numLegs = 4;
    let beagle = new Dog("Snoopy");
    let ownProps = [];
    let prototypeProps = [];
    for(let prop in beagle){
        if(beagle.hasOwnProperty(prop)){
            ownProps.push(prop);
        }else{
            prototypeProps.push(prop);
        }
    }
    ```

1. Understand the Constructor Property

    ```javascript
    function Dog(name) {
        this.name = name;
    }
    // Add your code below this line
    function joinDogFraternity(candidate) {
    if(candidate.constructor == Dog)
            return true;
        return false;
    }

    ```

1. Change the Prototype to a New Object

    ```javascript
    function Dog(name) {
        this.name = name;
    }
    Dog.prototype = {
        numLegs: 2,
        eat: function(){
            console.log("eat");
        },
        describe: function(){
            console.log("describe");
        }
    };
    ```

1. Remember to Set the Constructor Property when Changing the Prototype

    ```javascript
    function Dog(name) {
        this.name = name;
    }

    // Modify the code below this line
    Dog.prototype = {
        constructor: Dog,
        numLegs: 2,
        eat: function() {
            console.log("nom nom nom");
        },
        describe: function() {
            console.log("My name is " + this.name);
        }
    };
    ```

1. Understand Where an Object’s Prototype Comes From

    ```javascript
    function Dog(name) {
        this.name = name;
    }
    let beagle = new Dog("Snoopy");
    console.log(Dog.prototype.isPrototypeOf(beagle));
    ```

1. Understand the Prototype Chain
    1. prototypeof Bird.prototypeis Object.prototype
    2. The hasOwnPropertymethod is defined in Object.prototype

        ```javascript
        function Dog(name) {
            this.name = name;
        }

        let beagle = new Dog("Snoopy");

        Dog.prototype.isPrototypeOf(beagle);  // => true

        // Fix the code below so that it evaluates to true
        Object.prototype.isPrototypeOf(Dog.prototype);
        ```

1. Use Inheritance So You Don't Repeat Yourself

    ```javascript
    function Cat(name) {
        this.name = name;
    }
    Cat.prototype = {
        constructor: Cat
    };
    function Bear(name) {
        this.name = name;
    }
    Bear.prototype = {
        constructor: Bear
    };
    function Animal() { }
        Animal.prototype = {
        constructor: Animal,
        eat: function() {
            console.log("nom nom nom");
        }
    };
    ```

1. Inherit Behaviors from a Supertype

    ```javascript
    function Animal() { }
    Animal.prototype = {
        constructor: Animal,
        eat: function() {
            console.log("nom nom nom");
        }
    };
    let duck = Object.create(Animal.prototype); // Change this line
    let beagle = Object.create(Animal.prototype); // Change this line
    duck.eat(); // Should print "nom nom nom"
    beagle.eat(); // Should print "nom nom nom" 
    ```

1. Set the Child's Prototype to an Instance of the Parent

    ```javascript
    function Animal() { }
    Animal.prototype = {
        constructor: Animal,
        eat: function() {
            console.log("nom nom nom");
        }
    };
    function Dog() { }
    // Add your code below this line
    Dog.prototype = Object.create(Animal.prototype);
    let beagle = new Dog();
    beagle.eat();  // Should print "nom nom nom"
    ```

1. Reset an Inherited Constructor Property

    ```javascript
    function Animal() { }
    function Bird() { }
    function Dog() { }

    Bird.prototype = Object.create(Animal.prototype);
    Dog.prototype = Object.create(Animal.prototype);

    // Add your code below this line
    Bird.prototype.constructor = Bird;
    Dog.prototype.constructor = Dog;

    let duck = new Bird();
    let beagle = new Dog();
    ```

1. Add Methods After Inheritance

    ```javascript
    function Animal() { }
    Animal.prototype.eat = function() { console.log("nom nom nom"); };

    function Dog() { }

    // Add your code below this line
    Dog.prototype = Object.create(Animal.prototype);
    Dog.prototype.bark = function(){console.log("Woof!")}
    Dog.prototype.constructor = Dog;

    // Add your code above this line

    let beagle = new Dog();

    beagle.eat(); // Should print "nom nom nom"
    beagle.bark(); // Should print "Woof!"
    ```

1. Override Inherited Methods

    ```javascript
    function Bird() { }

    Bird.prototype.fly = function() { return "I am flying!"; };

    function Penguin() { }
    Penguin.prototype = Object.create(Bird.prototype);
    Penguin.prototype.constructor = Penguin;

    // Add your code below this line
    Penguin.prototype.fly = function(){return "Alas, this is a flightless bird.";};


    // Add your code above this line

    let penguin = new Penguin();
    console.log(penguin.fly());
    ```

1. Use a Mixin to Add Common Behavior Between Unrelated Objects

    ```javascript
    let bird = {
        name: "Donald",
        numLegs: 2
    };

    let boat = {
        name: "Warrior",
        type: "race-boat"
    };

    // Add your code below this line
    let glideMixin = function(obj){
        obj.glide = function(){
            console.log("gliding");
        }
    }
    glideMixin(bird);
    glideMixin(boat);
    ```

1. Use Closure to Protect Properties Within an Object from Being Modified Externally

    ```javascript
    function Bird() {
        let weight = 15;
        this.getWeight = function(){
            return weight;
        }
    }
    ```

1. Understand the Immediately Invoked Function Expression (IIFE)

    ```javascript
    (function() {
        console.log("A cozy nest is ready");
    })();
    ```

1. Use an IIFE to Create a Module

    ```javascript
    let funModule = (function(){
        return {
            isCuteMixin: function(obj) {
                obj.isCute = function() {
                    return true;
                };
            },
            singMixin: function(obj) {
                obj.sing = function() {
                    console.log("Singing to an awesome tune");
                };
            }
        }
    })();
    ```

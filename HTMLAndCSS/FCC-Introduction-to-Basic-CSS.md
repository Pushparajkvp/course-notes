# Basic CSS

1. Change the Color of Text

    ```html
    <h2 style="color:red;">CatPhotoApp</h2>
    ```

1. Use CSS Selectors to Style Elements

    ```html
    <style>
        h2{
            color:blue;
        }
    </style>
    ```

1. Use a CSS Class to Style an Element

    ```html
    <style>
        .red-text{
            color: red;
        }
    </style>
    ```

1. Change the Font Size of an Element

    ```html
    <style>
        p {
            font-size: 16px;
        }
    </style>
    ```

1. Set the Font Family of an Element

    ```html
    <style>
        p {
            font-size: 16px;
            font-family: monospace;
        }
    </style>
    ```

1. Import a Google Font

    ```html
    <link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
    <style>
        h2{
            font-family: Lobster;
        }
    </style>
    ```

1. Specify How Fonts Should Degrade

    ```html
    <style>
        h2 {
            font-family: Lobster, monospace;
        }
    </style>
    ```

1. Size Your Images

    ```html
    <style>
        .smaller-image{
            width: 100px;
        }
    </style>
    ```

1. Add Borders Around Your Elements

    ```html
    // Can use two classes and both styles will be applied
    <style>
        .smaller-image {
            width: 100px;
        }

        .thick-green-border {
            border-style: solid;
            border-color: green;
            border-width: 10px;
        }
    </style>
    <img class="smaller-image thick-green-border" src="https://bit.ly/fcc-relaxing-cat" alt="A cute orange cat lying on its back.">
    ```

1. Add Rounded Corners with border-radius

    ```html
    <style>
            .smaller-image {
            width: 100px;
            border-radius: 10px;
        }
    </style>
    ```

1. Make Circular Images with a border-radius

    ```html
    <style>
        .thick-green-border {
            border-color: green;
            border-width: 10px;
            border-style: solid;
            border-radius: 50%;
        }
    </style>
    ```

1. Give a Background Color to a div Element

    ```html
    <style>
        .silver-background {
            background-color: silver;
        }
    </style>
    ```

1. Use an id Attribute to Style an Element

    ```html
    <style>
        #cat-photo-form {
            background-color: green;
        }
    </style>
    ```

1. Clockwise notation

    ```html
    // Top->Right->Bottom->Left
    <style>
        p {
            padding: 40x 20px 40px 20px;
        }
    </style>
    ```

1. Use Attribute Selectors to Style Elements

    ```html
    <style>
        [type='radio'] {
            margin-top: 10px;
            margin-bottom: 15px;
        }
    </style>
    ```

1. Understand Absolute versus Relative Units

    ```html
    <style>
        .red-box {
            background-color: red;
            margin: 20px 40px 20px 40px;
            padding: 1.5em;
        }
    </style>
    ```

1. Override Class Declarations by Styling ID Attributes

    ```html
    // ID has more precedence than class
    <style>
        .pink-text {
            color: pink;
        }
        .blue-text {
            color: blue;
        }
        #orange-text {
            color: orange;
        }
    </style>
    <h1 class="pink-text blue-text" id="orange-text">Hello World!</h1>
    ```

1. Override Class Declarations with Inline Styles

    ```html
    // Inline style has more precedence than class and id
    <style>
        #orange-text {
            color: orange;
        }
        .pink-text {
            color: pink;
        }
        .blue-text {
            color: blue;
        }
    </style>
    <h1 style="color:green" id="orange-text" class="pink-text blue-text">Hello World!</h1>
    ```

1. Override All Other Styles by using Important

    ```html
    // Important overrides inline, id and class
    <style>
        #orange-text {
            color: orange;
        }
        .pink-text {
            color: pink !important;
        }
        .blue-text {
            color: blue;
        }
    </style>
    <h1 id="orange-text" class="pink-text blue-text" style="color: white">Hello World!</h1>
    ```

1. Use CSS Variables to change several elements at once

    ```html
    <style>
        .penguin {
            /* change code below */
            --penguin-skin: gray;
            --penguin-belly: white;
            --penguin-beak: orange;
            /* change code above */
            position: relative;
            margin: auto;
            display: block;
            margin-top: 5%;
            width: 300px;
            height: 300px;
        }
        .penguin-top {
            top: 10%;
            left: 25%;
            background: var(--penguin-skin, gray);
            width: 50%;
            height: 45%;
            border-radius: 70% 70% 60% 60%;
        }
        .penguin-bottom {
            top: 40%;
            left: 23.5%;
            background: var(--penguin-skin, gray);
            width: 53%;
            height: 45%;
            border-radius: 70% 70% 100% 100%;
        }
        .right-hand {
            top: 0%;
            left: -5%;
            background: var(--penguin-skin, gray);
            width: 30%;
            height: 60%;
            border-radius: 30% 30% 120% 30%;
            transform: rotate(45deg);
            z-index: -1;
        }
        .left-hand {
            top: 0%;
            left: 75%;
            background: var(--penguin-skin, gray);
            width: 30%;
            height: 60%;
            border-radius: 30% 30% 30% 120%;
            transform: rotate(-45deg);
            z-index: -1;
        }
        .right-cheek {
            top: 15%;
            left: 35%;
            background: var(--penguin-belly, white);
            width: 60%;
            height: 70%;
            border-radius: 70% 70% 60% 60%;
        }
        .left-cheek {
            top: 15%;
            left: 5%;
            background: var(--penguin-belly, white);
            width: 60%;
            height: 70%;
            border-radius: 70% 70% 60% 60%;
        }
        .belly {
            top: 60%;
            left: 2.5%;
            background: var(--penguin-belly, white);
            width: 95%;
            height: 100%;
            border-radius: 120% 120% 100% 100%;
        }
        .right-feet {
            top: 85%;
            left: 60%;
            background: var(--penguin-beak, orange);
            width: 15%;
            height: 30%;
            border-radius: 50% 50% 50% 50%;
            transform: rotate(-80deg);
            z-index: -2222;  
        }
        .left-feet {
            top: 85%;
            left: 25%;
            background: var(--penguin-beak, orange);
            width: 15%;
            height: 30%;
            border-radius: 50% 50% 50% 50%;
            transform: rotate(80deg);
            z-index: -2222;  
        }
        .right-eye {
            top: 45%;
            left: 60%;
            background: black;
            width: 15%;
            height: 17%;
            border-radius: 50%;
        }
        .left-eye {
            top: 45%;
            left: 25%;
            background: black;
            width: 15%;
            height: 17%;
            border-radius: 50%;  
        }
        .sparkle {
            top: 25%;
            left: 15%;
            background: white;
            width: 35%;
            height: 35%;
            border-radius: 50%;  
        }
        .blush-right {
            top: 65%;
            left: 15%;
            background: pink;
            width: 15%;
            height: 10%;
            border-radius: 50%;  
        }
        .blush-left {
            top: 65%;
            left: 70%;
            background: pink;
            width: 15%;
            height: 10%;
            border-radius: 50%;  
        }
        .beak-top {
            top: 60%;
            left: 40%;
            background: var(--penguin-beak, orange);
            width: 20%;
            height: 10%;
            border-radius: 50%;  
        }
        .beak-bottom {
            top: 65%;
            left: 42%;
            background: var(--penguin-beak, orange);
            width: 16%;
            height: 10%;
            border-radius: 50%;  
        }
        body {
            background:#c6faf1;
        }
        .penguin * {
            position: absolute;
        }
        </style>
        <div class="penguin">
        <div class="penguin-bottom">
            <div class="right-hand"></div>
            <div class="left-hand"></div>
            <div class="right-feet"></div>
            <div class="left-feet"></div>
        </div>
        <div class="penguin-top">
            <div class="right-cheek"></div>
            <div class="left-cheek"></div>
            <div class="belly"></div>
            <div class="right-eye">
            <div class="sparkle"></div>
            </div>
            <div class="left-eye">
            <div class="sparkle"></div>
            </div>
            <div class="blush-right"></div>
            <div class="blush-left"></div>
            <div class="beak-top"></div>
            <div class="beak-bottom"></div>
        </div>
    </div>
    ```

1. Improve Compatibility with Browser Fallbacks

    ```html
    <style>
        .red-box {
            background: red;
            background: var(--red-color);
            height: 200px;
            width:200px;
        }
    </style>
    ```

1. Cascading CSS variables

    ```html
    <style>
        /*You can think of the :root element as a container for your entire HTML document, in the same way that an html element is a container for the body element.*/
        :root {
            --penguin-belly: pink;
        }
    </style>
    ```

1. Use a media query to change a variable

    ```html
    <style>
        :root {
            --penguin-size: 300px;
            --penguin-skin: gray;
            --penguin-belly: white;
            --penguin-beak: orange;
        }
        @media (max-width: 350px) {
            :root {
                --penguin-skin: black;
                --penguin-size: 200px;
            }
        }
    </style>
    ```
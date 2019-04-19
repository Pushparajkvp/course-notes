# Applied Accessibility

1. Add a Text Alternative to Images for Visually Impaired Accessibility

    ```html
    <img src="doingKarateWow.jpeg" alt="camper cat doing karate">
    ```

1. Know When Alt Text Should be Left Blank

    ```html
    <img src="deviderImage.jpeg" alt="">
    ```

1. Use Headings to Show Hierarchical Relationships of Content
    * Only one h1 tag.
    * use css for size not header tags
    * use sequential heading tags

        ```html
        <h1>How to Become a Ninja</h1>
        <main>
        <h2>Learn the Art of Moving Stealthily</h2>
        <h3>How to Hide in Plain Sight</h3>
        <h3>How to Climb a Wall</h3>

        <h2>Learn the Art of Battle</h2>
        <h3>How to Strengthen your Body</h3>
        <h3>How to Fight like a Ninja</h3>

        <h2>Learn the Art of Living with Honor</h2>
        <h3>How to Breathe Properly</h3>
        <h3>How to Simplify your Life</h3>
        </main>
        ```

1. Wrap Content in the article Element (Does not depend on any other data in the website. eg: blogs, news articles etc)
    * &lt;div&gt; - groups content
    * &lt;section&gt; - groups related content
    * &lt;article&gt; - groups independent, self-contained content

    ```html
    <article>
        <h2>The Garfield Files: Lasagna as Training Fuel?</h2>
        <p>The internet is littered with varying opinions on nutritional paradigms, from catnip paleo to hairball cleanses. But let's turn our attention to an often overlooked fitness fuel, and examine the protein-carb-NOM trifecta that is lasagna...</p>
    </article>
    ```

1. Make Screen Reader Navigation Easier with the header Landmark

    ```html
    <header>
        <h1>Training with Camper Cat</h1>
    </header>
    ```

1. Make Screen Reader Navigation Easier with the nav Landmark

    ```html
    <nav>
      <ul>
        <li><a href="#stealth">Stealth &amp; Agility</a></li>
        <li><a href="#combat">Combat</a></li>
        <li><a href="#weapons">Weapons</a></li>
      </ul>
    </nav>
    ```

1. Make Screen Reader Navigation Easier with the footer Landmark

    ```html
    <footer>&copy; 2018 Camper Cat</footer>
    ```

1. Improve Accessibility of Audio Content with the audio Element

    ```html
    <audio controls>
      <source src="https://s3.amazonaws.com/freecodecamp/screen-reader.mp3" type="audio/mpeg"/>
    </audio>
    ```

1. Improve Chart Accessibility with the figure Element

    ```html
    <figure>
        <!-- Stacked bar chart will go here -->
        <br>
        <figcaption>Breakdown per week of time to spend training in stealth, combat, and weapons.</figcaption>
    </figure>
    ```

1. Improve Form Field Accessibility with the label Element

    ```html
    <label for="email">Email:</label>
    <input type="text" id="email" name="email">
    ```

1. Wrap Radio Buttons in a fieldset Element for Better Accessibility

    ```html
    <fieldset>
        <legend>What level ninja are you?</legend>
        <input id="newbie" type="radio" name="levels" value="newbie">
        <label for="newbie">Newbie Kitten</label><br>
        <input id="intermediate" type="radio" name="levels" value="intermediate">
        <label for="intermediate">Developing Student</label><br>
        <input id="master" type="radio" name="levels" value="master">
        <label for="master">Master</label>
    </fieldset>
    ```

1. Add an Accessible Date Picker

    ```html
    <label for="pickdate"> Pick Date: </label>
    <input type="date" id="pickdate" name="date">
    ```

1. Standardize Times with the HTML5 datetime Attribute

    ```html
    <p>Thank you to everyone for responding to Master Camper Cat's survey. The best day to host the vaunted Mortal Kombat tournament is <time datetime="2016-09-15">Thursday, September 15<sup>th</sup></time>. May the best ninja win!</p>
    ```

1. Make Elements Only Visible to a Screen Reader by Using Custom CSS

    * **display: none;** and **visibility: hidden;** will remove for both screen readers and visual users.
    * **width: 0px;** or **height: 0px;** will remove the element.

    ```html
    <style>
        .sr-only {
            position: absolute;
            left: -10000px;
            width: 1px;
            height: 1px;
            top: auto;
            overflow: hidden;
        }
    </style>
    ```

1. Make Links Navigatable with HTML Access Keys

    ```html
    <h2><a id="first" accesskey="g" href="">The Garfield Files: Lasagna as Training Fuel?</a></h2>
    ```

1. Use tabindex to Add Keyboard Focus to an Element

    ```html
    <input type="search" name="search" id="search" tabindex="1">
    <input type="submit" name="submit" value="Submit" id="submit" tabindex="2">
    ```

1. 

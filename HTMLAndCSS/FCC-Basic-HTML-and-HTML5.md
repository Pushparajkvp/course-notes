# Basic HTML and HTML5

1. Say Hello to HTML Elements

    ```html
    <h1>Hello World</h1>
    ```

1. Headline with the h2 Element

    ```html
    <h2>CatPhotoApp</h2>
    ```

1. Inform with the Paragraph Element

    ```html
    <p>Hello Paragraph</p>
    ```

1. Add Images to Your Website

    ```html
    <img src="https://bit.ly/fcc-relaxing-cat" alt="cat">
    ```

1. Link to External Pages with Anchor Elements

    ```html
    <a href="http://freecatphotoapp.com">cat photos</a>
    ```

1. Link to Internal Sections of a Page with Anchor Elements
    1. Remove the target="_blank" attribute from the anchor tag since this causes the linked document to open in a new window tab.

    1. ```html
        <a href="#footer" target="_blank">jump to bottom</a>
        ```

1. Nest an Anchor Element within a Paragraph

    ```html
    <p>View more <a href="http://freecatphotoapp.com" target="_blank">cat photos</a></p>
    ```

1. Make Dead Links Using the Hash Symbol

    ```html
    <p>Click here to view more <a href="#" target="_blank">cat photos</a>.</p>
    ```

1. Turn an Image into a Link

    ```html
    <a href="#"><img src="https://bit.ly/fcc-relaxing-cat" alt="A cute orange cat lying on its back."></a>
    ```

1. Create a Bulleted Unordered List

    ```html
    <ul>
        <li>item1</li>
        <li>item2</li>
        <li>item3</li>
    </ul>
    ```

1. Create an Ordered List

    ```html
    <ol>
        <li>cat nip</li>
        <li>laser pointers</li>
        <li>lasagna</li>
    </ol>
    ```

1. Create a Text Field

    ```html
    <input type="text">
    ```

1. Add Placeholder Text to a Text Field

    ```html
    <input type="text" placeholder="cat photo URL">
    ```

1. Create a Form Element

    ```html
    <form action="/submit-cat-photo">
        <input type="text" placeholder="cat photo URL">
    </form>
    ```

1. Add a Submit Button to a Form

    ```html
     <button type="submit">Submit</button>
    ```

1. Use HTML5 to Require a Field

    ```html
    <input type="text" required placeholder="cat photo URL">
    ```

1. Create a Set of Radio Buttons

    ```html
    <label>
      <input type="radio" name="indoor-outdoor">indoor 
    </label>
    ```

1. Create a Set of Checkboxes

    ```html
    <label>
      <input type="checkbox" name="personality">test2
    </label>
    ```

1. Check Radio Buttons and Checkboxes by Default

    ```html
    <label><input type="radio" name="indoor-outdoor" checked> Indoor</label>
    <label><input type="checkbox" name="personality" checked> Loving</label>
    ```

1. Declare the Doctype of an HTML Document

    ```html
    <!DOCTYPE html>
    <html>
        <h1>Hello World</h1>
    </html>
    ```

1. Define the Head and Body of an HTML Document

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>The best page ever</title>
    </head>
    <body>
        <h1>The best page ever</h1>
        <p>Cat ipsum dolor sit amet, jump launch to pounce upon little yarn mouse, bare fangs at toy run hide in litter box until treats are fed. Go into a room to decide you didn't want to be in there anyway. I like big cats and i can not lie kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff. Meow i could pee on this if i had the energy for slap owner's face at 5am until human fills food dish yet scamper. Knock dish off table head butt cant eat out of my own dish scratch the furniture. Make meme, make cute face. Sleep in the bathroom sink chase laser but pee in the shoe. Paw at your fat belly licks your face and eat grass, throw it back up kitty ipsum dolor sit amet, shed everywhere shed everywhere stretching attack your ankles chase the red dot, hairball run catnip eat the grass sniff.</p>
    </body>
    </html>  
    ```
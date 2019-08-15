# Responsive Web Design Principles

1. Create a Media Query

    ```html
    <style>
        p {
            font-size: 20px;
        }
        @media (max-height: 800px){
            p {
            font-size: 10px;
            }
        }
    </style>
    ```

1. Make an Image Responsive

    ```html
    <style>
        img {
            max-width: 100%;
            display: block;
            height: auto;
        }
    </style>
    ```

1. Use a Retina Image for Higher Resolution Displays

    ```html
    <style>
        /* Half the original size*/
        img {
            height: 100px;
            width: 100px;
        }
    </style>
    ```

1. Make Typography Responsive
    * vw: 10vw would be 10% of the viewport's width.
    * vh: 3vh would be 3% of the viewport's height.
    * vmin: 70vmin would be 70% of the viewport's smaller dimension (height vs. width).
    * vmax: 100vmax would be 100% of the viewport's bigger dimension (height vs. width).

    ```html
    <style>
        h2 {
            width: 80vw;
        }
        p {
            width: 75vmin;
        }
    </style>
    ```

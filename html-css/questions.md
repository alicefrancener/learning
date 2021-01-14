# Questions

- What is like the basic HTML page structure?
  ```html
    <!DOCTYPE html>
    <html lang="pt-br">
      <head></head>
      <body></body>
    </html>
  ```

- How to add a favicon to your website with HTML?
  ```html
  <head>
    <link rel="shortcut icon" type="image/jpg" href="Favicon_Image_Location"/>
  </head>
  ```

- How to set colors in CSS?
  ```css
    {
      /* Keywords */
      color: red;

      /* Hehadecimal (full or abbreviate) */
      color: #FF0000; 
      color: #F00;
      
      /* RGB and RGBA values
        Range RGB (red-green-blue): 0 to 255 => same range as hexadecimal (16^2 = 256)
        Range Alpha: 0 (transparente) to 1 (opaco) */
      color: color: rgb(255, 165, 0);
      background-color: rgba(255, 0, 0, 0.3);      
    }
  ```

- How to add an icon in HTML?
  - The `<i>` and `<span>` elements are widely used to add icons

  ```html
    <head>
      <script src="https://kit.fontawesome.com/yourcode.js"></script>
      <!--Get your code at fontawesome.com-->
    </head>

    <body>
      <i class="fas fa-band-aid fa-3x"></i>
    </body>
  ```

- How to add an YouTube video in HTML?
  - Define an `<iframe>` element in your web page
  - Let the `src` attribute point to the video URL
  - Use the `width` and `height` attributes to specify the dimension of the player
  
  ```html
  <iframe width="420" height="315"
    src="https://www.youtube.com/embed/tgbNymZ7vqY">
  </iframe>
  ```
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


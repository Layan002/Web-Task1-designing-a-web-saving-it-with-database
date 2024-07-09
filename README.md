# Apps we need to install

- We need to have a Visual Studio Code: [VS Code](https://code.visualstudio.com/)
this is the program we relies on to to program, it supports so many programming language, such as what we will need to complete this task: HTML, CSS, and PHP.

- We need to install [Xampp](https://www.apachefriends.org/). XAMPP stands for: X (cross-platform), A (Apache HTTP Server), 
M (MariaDB), P (PHP), and P (Perl). it is a local server environment to test their web applications. It's widely used for developing and testing web pages and websites on a local computer before deploying them to a live server.

- We will need also to use myPHP website to initialize the database that will store all the data that will be send from the localhost website.

# Steps
## XAMPP
- Open the xampp after you install it, click on start for both apache and mysql.
- save a folder that is named "robot-web" in the path of XAMPP, it is usually in C:\xampp\htdocs\

## VS code
- open VS code in the top tap open select file --> open folder --> robot-web
- Now create the following files:
'index.html', 'styles.css', 'send_movement.php'

### HTML File
inside the 'index.htm', copy-paste the following code. 
``` HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="keywords" content="HTML, CSS" />
    <meta name="description" content="Controlling the movements of the robot" />
    <title>Controlling the robot movement</title>
    <link rel="stylesheet" href="styles.css" />
    <script>
      function sendMovement(direction, element) {
        var xhr = new XMLHttpRequest();
        xhr.open("POST", "send_movement.php", true);
        xhr.setRequestHeader(
          "Content-Type",
          "application/x-www-form-urlencoded"
        );
        xhr.onreadystatechange = function () {
          if (xhr.readyState === 4 && xhr.status === 200) {
            var response = JSON.parse(xhr.responseText);
            if (response.status === "success") {
              // Update last movement display
              document.getElementById("last-movement").innerText =
                "Last Movement: " + direction;
            } else {
              console.error("Error:", response.message);
            }
          }
        };
        xhr.send("direction=" + direction);

        element.classList.add("active");
        setTimeout(function () {
          element.classList.remove("active");
        }, 200);
      }
    </script>
  </head>
  <body>
    <div class="container">
      <div class="rectangle up" onclick="sendMovement('up', this)">Up</div>
      <div class="middle">
        <div class="rectangle left" onclick="sendMovement('left', this)">
          Left
        </div>
        <div class="rectangle center" onclick="sendMovement('stop', this)">
          Stop
        </div>
        <div class="rectangle right" onclick="sendMovement('right', this)">
          Right
        </div>
      </div>
      <div class="rectangle down" onclick="sendMovement('down', this)">
        Down
      </div>
    </div>
    <div id="last-movement" class="last-movement">Last Movement: None</div>
  </body>
</html>
```
> [!NOTE]
> Inside the html file there is a JavaScript code between   <script> </script>. it is used with HTML to create dynamic and interactive web pages.

  





  

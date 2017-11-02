## Website Performance Optimization portfolio project

### About

Fourth project from the Front-End Web Developer Nanodegree in [Udacity](https://www.udacity.com/):

optimized index.html to achieve a score of 90 in PageSpeed, and optimized main.js to achieve 60 fps in pizza.html.

#### Part 1: Optimize PageSpeed Insights

- Minify CSS and JS files with Grunt in the production version /dist/
- Optimize images with Grunt which resizes and minifies images at different size
- Eliminate render-block CSS and JavaScript in above -the fold content:
  - Style.css inlined in index.html
  - Print.css add the media=print tag
  - Load asyncronoulsy the perfmatters.js script in the header
  - Put the Google Analytics script to the footer of the page

#### Part 2: Optimize Frames per Second

- Optimizations made in views/index.html
  - Apply optimizations for PageSpeed: minify css and js, optimize images, inline css, configure the viewport.
  - Changes images tag's photo to the minify version.
- Optimizations made in views/js/main.js:
  - Change querySelector and querySelectorAll to getElementById and getElementByClassName to make it faster (Learn more <a href="https://discussions.udacity.com/t/project-4-how-do-i-optimize-the-background-pizzas-for-loop/36302">Udacity forum</a>)
  - Delete the function determineDx, since we change the pizza size inside the changePizzaSizes. Also optimize the loop in changePizzaSizes to put the new width in each .randomPizzaContainer.
  - Create all the variables outside of loops as possible.
  - In updatePositions, phase only have 5 different values, because it changes for each (i % 5). So we create an array where we put the 5 values. We also put the phase variable outside the for loop, to separate the manipulation of the DOM from the methods that query the state. And finally we optimize the loop.
  - Dynamically calculated the number of pizzas needed to fill the background
- Optimizations made in views/css/style.css
  - Put will-change:transform;transform:translateZ(0);backface-visibility:hidden; in the .mover class. This way we will create diferent layouts for each pizza and the main layout will not be repainted every time we create a pizza.

### Folders structure

- /dist/ folder, there is the production code, with the minified css, js and optimized images.
- /dev/ folder, there is the development code.
- / folder, there is the root folder which has grunt and package.json.

### How to run the application locally

Some useful tips to help you get started:

1. Clone the repository to your computer( run on terminal )

2. ```
   git clone https://github.com/EvanFung/FEND-project-4-optimization.git
   ```

3. Install dependencies with npm

4. ```
   npm install
   ```

5. Run grunt (Learn more about <a href="https://gruntjs.com/">Grunt</a>)

6. ```
   grunt
   ```

7. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8000
  ```

8. Open a browser and visit localhost:8000

9. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8000
  ```

10. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

### Udacity's instructions

You will optimize a provided website with a number of optimization- and performance-related issues so that it achieves a target PageSpeed score and runs at 60 frames per second.

1. Review our course on Website Performance Optimization using Google PageSpeed.
2. Download the required project assets.
3. Use Chrome Developer Tools to review the current state of various pages within the application and identify areas for improvement.
4. Review the code powering the website and identify areas where you believe modifications are warranted.
5. Iteratively make changes and test those changes using the tools available to you to determine if they are a performance gain or loss.

### License

The project is licensed under the [MIT license](license.txt).

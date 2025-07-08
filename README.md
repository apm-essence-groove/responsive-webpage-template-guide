# Responsive Webpage Template Guide
By Eeshvar Das

## Responsive Webpage Template Repository
I created a [Responsive Website Teamplate](https://github.com/apm-essence-groove/responsive-webpage-template) for you to get started quickly with making a website that is full stasck.

### Website Anatomy: A Beginner's Guide to Front End and Back End

Understanding how a website works involves two main parts: the Front End and the Back End. Think of a website like a restaurant.

---

### The Front End (The Client-Side)

The **Front End** is everything you see and interact with directly in your web browser. It's the visual part of the website, like the dining area of a restaurant. Its main goal is to create a positive and easy-to-use experience for you, the visitor. This includes all the colors, fonts, menus, buttons, and forms.

Our simple homepage application uses three core front-end technologies:

1.  **HTML (HyperText Markup Language): The Skeleton**
    *   **What it is:** HTML provides the basic structure and content of a webpage. It's like the skeleton of a building, defining where everything goes, such as headings, paragraphs, images, and links.
    *   **How it works in our app:** Our website's main structure is defined in `express/public/index.html`. This file includes elements like the navigation logo ("MyWebsite"), parts of the hamburger menu (span elements with class "bar"), and a "Get Started" button. This `index.html` file sits inside the `public` folder.

2.  **CSS (Cascading Style Sheets): The Styling**
    *   **What it is:** CSS is responsible for the visual presentation of your webpage. It controls how the HTML elements look, including colors, fonts, layout, and overall design. It also handles "responsive design," which means the website adjusts its appearance to look good on different screen sizes, like mobile phones or large monitors.
    *   **How it works in our app:** The styling for our homepage is defined in `express/public/style.css`. This CSS file sets general body styles, defines the appearance of the header and navigation bar, styles the "hamburger" menu for mobile devices, designs the "hero" section (the large introductory area with an image), and formats the main content and footer. For instance, it specifies the font family, background colors, and how elements like navigation links change color when you hover over them. It also includes media queries that hide the hamburger menu on larger screens and display it for smaller ones, transforming it when active. This `style.css` file is also within the `public` folder.

3.  **JavaScript: The Interactivity**
    *   **What it is:** JavaScript adds interactivity to a webpage. It handles dynamic elements, such as animations, form validations, and updating content without needing to reload the entire page.
    *   **How it works in our app:** The interactive elements of our homepage are managed by `express/public/script.js`. This script provides the functionality for the mobile navigation menu (the "hamburger" menu), allowing it to toggle between active and inactive states when clicked. It also ensures that the navigation menu closes when a link inside it is clicked. Additionally, it adds an event listener to the "Get Started" button (with `id="hero-button"`) which, when clicked, triggers a simple pop-up alert saying "Thanks for getting started!". Like HTML and CSS, `script.js` is located in the `public` folder.

---

### The Back End (The Server-Side)

The **Back End** is the part of the website that you don't see; it's the "behind-the-scenes" engine that powers the front end. In our restaurant analogy, the back end is the kitchen where the food is prepared, ingredients are stored, and orders are processed. Its goal is to handle data, security, and the core functionality of the site.

Our application's back end is built using **Node.js** and the **Express** framework.

The back end consists of three main parts:

1.  **A Server-Side Language (Node.js with Express)**
    *   **What it is:** This is the programming language and framework that runs on the server to handle requests from the front end. It's responsible for tasks like processing form submissions, interacting with databases, or retrieving user data. Node.js allows JavaScript to be used on the server side.
    *   **How it works in our app:** Our main back-end logic is defined in `express/server.js`. This file imports the Express library to create an Express application instance. It's configured to serve static files (our HTML, CSS, and JavaScript) from the `public` directory. This means when someone visits the website, Express knows to look in the `public` folder for `index.html` and other assets to display. The `server.js` also includes middleware to parse incoming data, such as JSON or URL-encoded data from forms. It defines a simple API endpoint (`/api/contact`) that handles form submissions, logging the received data to the console and sending back a "Thank you for your message!" response.

2.  **A Server**
    *   **What it is:** This is the computer that runs the back-end code and serves the website to visitors. It listens for requests from browsers and sends back responses.
    *   **How it works in our app:** Our `server.js` file sets up the Express application to listen on a specific port (e.g., `process.env.PORT` or `3000`). When the server starts, it prints a message like ```Server running at http://localhost:3000``` to indicate it's ready to receive requests. For deployment, the application is set up to be run by Heroku, which identifies it as a Node.js application and uses a `Procfile` to know what command to execute to start the web server. Our `Procfile` specifies `web: node server.js`. Our simple homepage has been successfully deployed and is now live.

3.  **A Database**
    *   **What it is:** This is where all the application's data is stored and organized. Examples include user accounts, blog posts, or product information.
    *   **How it works in our app:** While our current simple homepage backend doesn't connect to a database, the `server.js` file notes that in a real application, the received form data would typically be saved to a database.

Our back-end also includes a `package.json` file. This file manages the project's details and dependencies (other necessary tools). It defines the project's name, version, and a `start` script (`"start": "node server.js"`) which is the command to run the server. It also lists `express` as a dependency, meaning the application needs the Express library to run. The `package.json` also specifies the Node.js version to use (`"node": "20.x"`) for deployment environments like Heroku.

---

### How They Communicate

The front end and back end constantly communicate with each other using **HTTP requests**. This is a continuous request-response cycle.

Here's how it generally works:
1.  **Request from Front End:** The front end (your browser) sends a request to the back end. For example, if you fill out a contact form on our homepage and click "Submit," your browser sends a request containing your message data to the server's `/api/contact` endpoint.
2.  **Processing by Back End:** The back end (our Node.js Express server) receives this request. It processes the data (in our case, it just logs it to the console).
3.  **Response to Front End:** The back end then sends a response back to the front end. For the contact form, it sends a JSON response `{ message: 'Thank you for your message!' }`.
4.  **Update by Front End:** The front end receives this response and can update the page accordingly, perhaps by showing a confirmation message to the user.

This communication is often managed through an **API (Application Programming Interface)**, which is a set of rules defining how the front end and back end should talk to each other.

***

This setup forms the foundation of a "full-stack" application, where the front end is the visual part you interact with, and the back end is the powerful engine working behind the scenes. Our simple homepage is a great example of this fundamental architecture.

_There is plenty of information on the internet that goes into more detail. You are welcome to make a specific issue on thie repository and I will respond directly to the issue._

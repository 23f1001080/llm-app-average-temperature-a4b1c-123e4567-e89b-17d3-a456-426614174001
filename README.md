# Temperature Report Advanced Web App

## 1. Project Title and Description
This single-page web application is designed to fetch weather data from an attached `weather.csv` file. It computes and displays the average, highest, and lowest temperatures from the 'temperature' column. The average temperature is rounded to two decimal places. The application leverages Bootstrap 5 for modern styling and presents the calculated results within visually appealing cards. The browser tab title is dynamically set to 'Temperature Report Advanced 2025-10-22'.

## 2. Setup Instructions
To run this application locally, a simple HTTP server is required because modern web browsers restrict `fetch` requests to local files (using the `file://` protocol) due to security policies. Below are a couple of straightforward methods to set up a local server:

### Using Python's built-in HTTP server:
1.  Ensure Python is installed on your system.
2.  Navigate to the project's root directory (where `index.html` and `weather.csv` are located) in your terminal.
3.  Execute the following command:
    ```bash
    python -m http.server 8000
    ```
4.  Open your web browser and go to `http://localhost:8000`.

### Using Node.js `http-server` (if Node.js is installed):
1.  If you don't have `http-server` installed globally, install it:
    ```bash
    npm install -g http-server
    ```
2.  Navigate to the project directory in your terminal.
3.  Run the server:
    ```bash
    http-server
    ```
4.  Open your web browser and visit the address displayed in the terminal (e.g., `http://127.0.0.1:8080`).

## 3. Usage Guide
1.  Once the local server is running, open your web browser and navigate to the server's address (e.g., `http://localhost:8000`).
2.  The browser tab's title will immediately update to 'Temperature Report Advanced 2025-10-22'.
3.  The application will automatically fetch and parse the `weather.csv` file.
4.  It will then calculate the average, highest, and lowest temperatures from the 'temperature' column and display these statistics prominently within distinct Bootstrap cards on the page. The average will be rounded to two decimal places, while the highest and lowest will be displayed as whole numbers.

## 4. Code Explanation

*   **`index.html`**: This is the core and sole HTML file of the application. It includes:
    *   Standard HTML5 boilerplate and essential meta tags.
    *   A link to **Bootstrap 5 CSS** hosted on `jsdelivr` for modern, responsive, and aesthetically pleasing styling.
    *   Three `div` elements, thoughtfully structured as Bootstrap cards and arranged within a `row`, with `id="avg-temp"`, `id="high-temp"`, and `id="low-temp"`. These serve as dynamic placeholders where the computed average, highest, and lowest temperatures will be displayed.
    *   An embedded JavaScript `<script>` block that executes once the Document Object Model (DOM) is fully loaded:
        *   It programmatically sets the `document.title` to the required 'Temperature Report Advanced 2025-10-22'.
        *   It utilizes the browser's native `fetch` API to retrieve the `weather.csv` file.
        *   Upon successful retrieval, it parses the CSV content:
            *   The content is split into individual rows, and the header row is used to identify the 'temperature' column.
            *   It then iterates through each data row, extracts the numerical temperature values, accumulates their sum, counts the valid entries, and continuously tracks the minimum and maximum temperatures encountered.
            *   The average temperature is computed and then rounded to two decimal places using `toFixed(2)`.
            *   Finally, it updates the `textContent` of the `#avg-temp`, `#high-temp`, and `#low-temp` HTML elements with the calculated average, highest (rounded to a whole number using `toFixed(0)`), and lowest (rounded to a whole number using `toFixed(0)`) temperatures respectively.
            *   Basic error handling is implemented to gracefully manage potential network issues or problems during CSV parsing.
        *   A link to the **Bootstrap 5 JS bundle** from `jsdelivr` is included at the end of the `<body>` for any interactive Bootstrap components, though primarily the CSS is utilized for this application.

*   **`weather.csv`**: This file contains the raw weather data in a Comma Separated Values (CSV) format. It includes columns such as `city` and `temperature`, which the JavaScript code specifically targets to perform the required statistical computations.

## 5. License Information
This project is released under the MIT License. For complete details, please refer to the accompanying `LICENSE` file.

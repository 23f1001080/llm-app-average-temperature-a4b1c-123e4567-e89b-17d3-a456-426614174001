# Temperature Report Web App

## 1. Project Title and Description
This is a single-page web application designed to fetch weather data from a CSV file, calculate the average temperature, and display it prominently on the page. The application uses Bootstrap 5 for styling and sets a specific title for the browser tab.

## 2. Setup Instructions
To run this application locally, you will need a simple HTTP server because modern browsers restrict `fetch` requests to local files (`file://` protocol) for security reasons. 

Here are a few ways to set up a local server:

### Using Python's built-in HTTP server:
1.  Ensure you have Python installed.
2.  Navigate to the directory containing `index.html` and `weather.csv` in your terminal.
3.  Run the following command:
    ```bash
    python -m http.server 8000
    ```
4.  Open your web browser and go to `http://localhost:8000`.

### Using Node.js `http-server` (if you have Node.js installed):
1.  Install `http-server` globally:
    ```bash
    npm install -g http-server
    ```
2.  Navigate to the project directory in your terminal.
3.  Run:
    ```bash
    http-server
    ```
4.  Open your web browser and go to the address displayed in the terminal (e.g., `http://127.0.0.1:8080`).

## 3. Usage Guide
1.  Once the local server is running, open your web browser and navigate to the server's address (e.g., `http://localhost:8000`).
2.  The browser tab title will automatically update to 'Temperature Report 2025-10-22'.
3.  The application will fetch `weather.csv`, calculate the average of the 'temperature' column, and display the result, rounded to two decimal places, within the "Overall Average" section.

## 4. Code Explanation

*   **`index.html`**: This is the main and only HTML file. It includes:
    *   Standard HTML5 boilerplate and meta tags.
    *   A link to **Bootstrap 5 CSS** from `jsdelivr` for responsive and modern styling.
    *   A `div` with `id="avg-temp"` serves as the placeholder where the calculated average temperature will be displayed.
    *   An embedded JavaScript `<script>` block that executes once the DOM is loaded:
        *   It sets the `document.title` to the required 'Temperature Report 2025-10-22'.
        *   It uses the `fetch` API to retrieve `weather.csv`.
        *   Upon successful fetching, it parses the CSV content:
            *   Splits the content into rows and then headers.
            *   Identifies the 'temperature' column.
            *   Iterates through each data row, extracts temperature values, and calculates their sum and count.
            *   Computes the average temperature, rounding it to two decimal places using `toFixed(2)`.
            *   Updates the `textContent` of the `#avg-temp` element with the calculated average.
        *   Includes basic error handling for network issues or CSV parsing problems.
    *   A link to **Bootstrap 5 JS bundle** from `jsdelivr` for Bootstrap's interactive components (though not strictly used in this simple app, it's good practice for a full Bootstrap setup).

*   **`weather.csv`**: This file contains the raw weather data in CSV (Comma Separated Values) format. It includes columns for `city` and `temperature`, which the JavaScript code parses to compute the average.

## 5. License Information
This project is licensed under the MIT License. See the LICENSE file (if explicitly provided, otherwise assume standard MIT terms as per common practice) for more details.

### Project Structure
```
/C:/Users/HP/Desktop/hub code/
    ├── login.html
    └── weberadmin.html
```

### 1. Create `login.html`
This file will serve as the login page.

```html
<!-- filepath: /C:/Users/HP/Desktop/hub code/login.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f8f9fa;
        }
        .login-container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        h2 {
            text-align: center;
            margin-bottom: 20px;
        }
        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .login-btn {
            width: 100%;
            padding: 10px;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .login-btn:hover {
            background-color: #2980b9;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <h2>Login</h2>
        <input type="text" id="username" placeholder="Username" required>
        <input type="password" id="password" placeholder="Password" required>
        <button class="login-btn" onclick="login()">Login</button>
        <p id="error-message" style="color: red; text-align: center;"></p>
    </div>

    <script>
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            // Simple authentication (for demonstration purposes)
            if (username === 'admin' && password === 'password') {
                // Redirect to the admin dashboard
                window.location.href = 'weberadmin.html';
            } else {
                document.getElementById('error-message').textContent = 'Invalid username or password';
            }
        }
    </script>
</body>
</html>
```

### 2. Modify `weberadmin.html`
We will add a check to ensure that the user is logged in before accessing the admin dashboard. If not logged in, they will be redirected to the login page.

```html
<!-- filepath: /C:/Users/HP/Desktop/hub code/weberadmin.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Dashboard</title>
    <script src="https://unpkg.com/xlsx/dist/xlsx.full.min.js"></script>
    <style>
        /* Existing styles remain unchanged */
        * {
            font-family: 'Roboto', sans-serif;
            font-size: 11px;
        }
        /* ... (rest of your existing styles) ... */
    </style>
</head>
<body>
    <script>
        // Check if user is logged in
        if (!sessionStorage.getItem('loggedIn')) {
            window.location.href = 'login.html';
        }
    </script>

    <div class="header-container">
        <img src="EiEWG_nigeria_logo.ico" alt="Education Sector Logo" class="logo">
        <h1>Education Sector Submitted Response Data (5Ws)</h1>
    </div>
    
    <div class="filter-section">
        <label for="monthFilter">Filter by Month:</label>
        <input type="month" id="monthFilter" name="monthFilter">
        <div class="button-group">
            <button class="download-btn" onclick="downloadFilteredData()">Download Filtered Data</button>
            <button class="download-btn" onclick="downloadAllData()">Download All Data</button>
        </div>
    </div>

    <div id="submissions-table"></div>
     
    <script>
        // Store login status in sessionStorage
        sessionStorage.setItem('loggedIn', true);

        // Existing JavaScript functions remain unchanged
        function downloadAllData() {
            // ... (existing code) ...
        }

        function displaySubmissions() {
            // ... (existing code) ...
        }

        // Initialize table on page load
        document.addEventListener('DOMContentLoaded', displaySubmissions);
        // Refresh table every 30 seconds
        setInterval(displaySubmissions, 30000);

        function downloadFilteredData() {
            // ... (existing code) ...
        }
    </script>
    
</body>
</html>
```

### Summary
- **Login Page (`login.html`)**: A simple login form that checks for hardcoded credentials (username: `admin`, password: `password`). If the credentials are correct, it redirects to the admin dashboard.
- **Admin Dashboard (`weberadmin.html`)**: Checks if the user is logged in by looking for a `loggedIn` flag in `sessionStorage`. If not found, it redirects to the login page.

This setup is basic and should be enhanced with proper authentication and security measures for a production environment.
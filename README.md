<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Form</title>
    <link rel="stylesheet" href="/styles.css">
</head>
<body>
    <div class="container">
        <h1>Login Form</h1>
        <form action="/register" method="post">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
            </div>
            <button type="submit">Submit</button>
        </form>
        <!-- <form id="myForm">
          <label for="name">Name:</label>
          <input type="text" id="name" name="name" required>
          <label for="email">Email:</label>
          <input type="email" id="email" name="email" required>
          <button type="submit">Submit</button>
        </form>
       -->

    </div>
    <script>
        // Step 2: Add a submit event listener to the form
        document.getElementById('myForm').addEventListener('submit', function(event) {
          event.preventDefault(); // Prevent the default form submission
    
          // Collect form data
          const formData = {
            name: document.getElementById('name').value,
            email: document.getElementById('email').value,
            password: document.getElementById('password').value
          };
    
          // Step 3: Use fetch to submit the form data via a POST request
          fetch('https://didactic-dollop-v6p5vx4pr9wvhp6q7-3000.app.github.dev/', {
            method: 'POST', // Specify the method
            headers: {
              'Content-Type': 'application/json' // Specify the content type
            },
            body: JSON.stringify(formData) // Convert the data to a JSON string
          })
          .then(response => {
            if (!response.ok) {
              throw new Error('Network response was not ok');
            }
            return response.json(); // Parse the JSON response
          })
          .then(data => {
            // Handle the response data
            console.log('Response:', data);
            alert('Form submitted successfully!');
          })
          .catch(error => {
            // Handle errors
            console.error('Error:', error);
            alert('An error occurred. Please try again.');
          });
        });
      </script>
</body>
</html>

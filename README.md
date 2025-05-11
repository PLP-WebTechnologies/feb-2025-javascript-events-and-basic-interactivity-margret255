# feb-2025-avasjcript-events-and-basic-interactivity



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Interactive JS Demo</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2rem;
      background-color: #f9f9f9;
      color: #333;
      transition: background 0.3s, color 0.3s;
    }
    .dark-mode {
      background-color: #1e1e1e;
      color: #f0f0f0;
    }
    form {
      max-width: 400px;
      margin: auto;
      border: 1px solid #ccc;
      padding: 1.5rem;
      border-radius: 8px;
      background: white;
    }
    input, textarea, button {
      width: 100%;
      padding: 0.5rem;
      margin-top: 0.5rem;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    .char-count {
      font-size: 0.9rem;
      color: gray;
      text-align: right;
    }
    .error {
      color: red;
      font-size: 0.9rem;
    }
    .success {
      color: green;
      font-size: 1rem;
      text-align: center;
      margin-top: 1rem;
    }
    #toggle-dark {
      margin-top: 1.5rem;
      display: block;
      text-align: center;
    }
  </style>
</head>
<body>

  <h2>Contact Us</h2>
  <form id="contactForm">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    <div id="nameError" class="error"></div>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    <div id="emailError" class="error"></div>

    <label for="message">Message:</label>
    <textarea id="message" name="message" maxlength="200" rows="5"></textarea>
    <div class="char-count" id="charCount">0 / 200</div>

    <button type="submit">Send Message</button>
    <div class="success" id="successMsg"></div>
  </form>

  <button id="toggle-dark">Toggle Dark Mode 🌙</button>

  <script>
    const form = document.getElementById('contactForm');
    const nameInput = document.getElementById('name');
    const emailInput = document.getElementById('email');
    const messageInput = document.getElementById('message');
    const charCount = document.getElementById('charCount');
    const nameError = document.getElementById('nameError');
    const emailError = document.getElementById('emailError');
    const successMsg = document.getElementById('successMsg');
    const darkToggle = document.getElementById('toggle-dark');

    // Character counter
    messageInput.addEventListener('input', () => {
      charCount.textContent = `${messageInput.value.length} / 200`;
    });

    // Toggle dark mode
    darkToggle.addEventListener('click', () => {
      document.body.classList.toggle('dark-mode');
    });

    // Form validation and submission
    form.addEventListener('submit', function(e) {
      e.preventDefault();
      let valid = true;
      nameError.textContent = '';
      emailError.textContent = '';
      successMsg.textContent = '';

      if (nameInput.value.trim() === '') {
        nameError.textContent = 'Name is required.';
        valid = false;
      }

      if (!validateEmail(emailInput.value)) {
        emailError.textContent = 'Enter a valid email.';
        valid = false;
      }

      if (valid) {
        successMsg.textContent = 'Message sent successfully!';
        form.reset();
        charCount.textContent = '0 / 200';
      }
    });

    // Email validation helper
    function validateEmail(email) {
      const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return regex.test(email);
    }
  </script>

</body>
</html>

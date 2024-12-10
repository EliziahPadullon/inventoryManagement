<script>
    import { goto } from '$app/navigation'; // Import the `goto` function
  
    let email = "";
    let password = "";
  
    function handleLogin() {
      // Here you can validate credentials (e.g., make an API call)
      if (email && password) {
        // Navigate to the dashboard page after successful login
        goto('/dashboard'); // Replace `/dashboard` with your actual route
      } else {
        alert('Please fill out the fields correctly.');
      }
    }
  </script>
  
  <style>
    .container {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100%;
      background-color: #f8f9fa;
    }
  
    .card {
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 400px;
      text-align: center;
    }
  
    .card h2 {
      margin-bottom: 20px;
      font-size: 24px;
      font-weight: bold;
      color: #333;
    }
  
    .form-group {
      margin-bottom: 20px;
      text-align: left;
    }
  
    .form-group label {
      display: block;
      font-size: 14px;
      color: #333;
      margin-bottom: 5px;
    }
  
    .form-group input {
      width: 100%;
      padding: 10px 15px;
      font-size: 14px;
      border: 1px solid #ddd;
      border-radius: 8px;
      outline: none;
      transition: border-color 0.3s;
    }
  
    .form-group input:focus {
      border-color: #6c757d;
    }
  
    .button {
      width: 100%;
      padding: 10px 15px;
      background-color: #7A985F;
      color: white;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
  
    .button:hover {
      background-color: #5c714a;
    }
  
    .footer {
      margin-top: 20px;
      font-size: 14px;
      color: #666;
    }
  
    .footer a {
      color: #34C4C9;
      text-decoration: none;
    }
  
    .footer a:hover {
      text-decoration: underline;
    }
  </style>

  <div class="container">
    <div class="card">
      <h2>Sign in</h2>
      <form on:submit|preventDefault={handleLogin}>
        <div class="form-group">
          <label for="email">Email Address</label>
          <input
            id="email"
            type="email"
            bind:value={email}
            placeholder="example@gmail.com"
            required
          />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input
            id="password"
            type="password"
            bind:value={password}
            placeholder="********"
            required
          />
        </div>
        <button class="button" type="submit">Sign in</button>
      </form>
      <div class="footer">
        Don't have an account? <a href="/signup">Register now!</a>
      </div>
    </div>
  </div>
  
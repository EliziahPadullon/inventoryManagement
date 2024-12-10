<script lang="ts">

  import { goto } from '$app/navigation';

  let name = "";
  let email = "";
  let password = "";
  let confirmPassword = "";
  let errorMessage = "";

  async function handleSignUp(event: Event) {
    event.preventDefault();

    // Validate password and confirm password match
    if (password !== confirmPassword) {
      errorMessage = "Passwords do not match!";
      return;
    }

    try {
      const response = await fetch('/signup.php', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ name, email, password }),
      });


      const result = await response.json();
      console.log(result);

      if (result.success) {
        alert("Registration successful!");
        // Redirect to the login page
        goto('/login');
      } else {
        errorMessage = result.message || "An error occurred during registration.";
      }
    } catch (error) {
      console.error("Error:", error);
      errorMessage = "Unable to connect to the server. Please try again.";
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

  .error {
    color: red;
    font-size: 14px;
    margin-top: -10px;
    margin-bottom: 10px;
    text-align: left;
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
    <h2>Sign up</h2>
    <form on:submit={handleSignUp}>
      <div class="form-group">
        <label for="name">Name</label>
        <input
          id="name"
          type="text"
          bind:value={name}
          placeholder="Enter your full name"
          required
        />
      </div>
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
      <div class="form-group">
        <label for="confirm-password">Confirm Password</label>
        <input
          id="confirm-password"
          type="password"
          bind:value={confirmPassword}
          placeholder="********"
          required
        />
      </div>
      {#if errorMessage}
        <div class="error">{errorMessage}</div>
      {/if}
      <button class="button" type="submit">Submit</button>
    </form>
    <div class="footer">
      Already have an account? <a href="/login">Sign in now!</a>
    </div>
  </div>
</div>

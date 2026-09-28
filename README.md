# Login.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mifibot | Login / Create Account</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    }

    body {
      background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      color: #e2e8f0;
    }

    .container {
      background: #1e293b;
      border-radius: 20px;
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
      width: 100%;
      max-width: 440px;
      overflow: hidden;
      border: 1px solid #334155;
    }

    .header {
      background: linear-gradient(90deg, #0ea5e9, #0284c7);
      padding: 28px 24px;
      text-align: center;
    }

    .logo {
      font-size: 28px;
      font-weight: 800;
      letter-spacing: -0.5px;
      color: white;
      margin-bottom: 6px;
    }

    .tagline {
      font-size: 13px;
      color: #bae6fd;
      font-weight: 500;
      line-height: 1.4;
    }

    .tabs {
      display: flex;
      background: #0f172a;
    }

    .tab {
      flex: 1;
      padding: 16px;
      text-align: center;
      cursor: pointer;
      font-weight: 600;
      font-size: 15px;
      color: #94a3b8;
      transition: all 0.25s;
      border-bottom: 3px solid transparent;
    }

    .tab.active {
      color: #38bdf8;
      border-bottom-color: #0ea5e9;
      background: #1e293b;
    }

    .form-container {
      padding: 32px 28px;
    }

    .form {
      display: none;
    }

    .form.active {
      display: block;
    }

    h2 {
      text-align: center;
      margin-bottom: 24px;
      font-size: 22px;
      color: #f1f5f9;
    }

    .input-group {
      margin-bottom: 18px;
    }

    label {
      display: block;
      margin-bottom: 6px;
      font-size: 13px;
      color: #94a3b8;
      font-weight: 500;
    }

    input {
      width: 100%;
      padding: 13px 16px;
      background: #0f172a;
      border: 1px solid #334155;
      border-radius: 10px;
      font-size: 15px;
      color: #f1f5f9;
      transition: all 0.2s;
    }

    input:focus {
      outline: none;
      border-color: #0ea5e9;
      box-shadow: 0 0 0 3px rgba(14, 165, 233, 0.2);
    }

    input::placeholder {
      color: #64748b;
    }

    button {
      width: 100%;
      padding: 14px;
      background: linear-gradient(90deg, #0ea5e9, #0284c7);
      color: white;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
      margin-top: 8px;
    }

    button:hover {
      background: linear-gradient(90deg, #0284c7, #0369a1);
      transform: translateY(-1px);
    }

    .message {
      margin-top: 16px;
      padding: 12px;
      border-radius: 8px;
      text-align: center;
      font-size: 14px;
      display: none;
    }

    .message.success {
      background: rgba(34, 197, 94, 0.15);
      color: #4ade80;
      border: 1px solid rgba(34, 197, 94, 0.3);
      display: block;
    }

    .message.error {
      background: rgba(239, 68, 68, 0.15);
      color: #f87171;
      border: 1px solid rgba(239, 68, 68, 0.3);
      display: block;
    }

    .switch-text {
      text-align: center;
      margin-top: 22px;
      font-size: 14px;
      color: #94a3b8;
    }

    .switch-text a {
      color: #38bdf8;
      text-decoration: none;
      font-weight: 600;
      cursor: pointer;
    }

    .switch-text a:hover {
      text-decoration: underline;
    }

    .footer {
      text-align: center;
      padding: 16px;
      font-size: 12px;
      color: #64748b;
      border-top: 1px solid #334155;
    }
  </style>
</head>
<body>
  <div class="container">
    <!-- Header -->
    <div class="header">
      <div class="logo">Mifibot</div>
      <div class="tagline">A Miniature Mobile Robot for Extinguishing in Confined Areas</div>
    </div>

    <!-- Tabs -->
    <div class="tabs">
      <div class="tab active" onclick="switchTab('login')">Login</div>
      <div class="tab" onclick="switchTab('signup')">Create Account</div>
    </div>

    <div class="form-container">
      <!-- Login Form -->
      <div id="loginForm" class="form active">
        <h2>Welcome Back</h2>
        <form onsubmit="handleLogin(event)">
          <div class="input-group">
            <label>Email</label>
            <input type="email" id="loginEmail" required placeholder="you@company.com">
          </div>
          <div class="input-group">
            <label>Password</label>
            <input type="password" id="loginPassword" required placeholder="••••••••">
          </div>
          <button type="submit">Log In to Mifibot</button>
          <div id="loginMessage" class="message"></div>
        </form>
        <div class="switch-text">
          Don't have an account? <a onclick="switchTab('signup')">Create one</a>
        </div>
      </div>

      <!-- Sign Up Form -->
      <div id="signupForm" class="form">
        <h2>Create Account</h2>
        <form onsubmit="handleSignup(event)">
          <div class="input-group">
            <label>Full Name</label>
            <input type="text" id="signupName" required placeholder="John Doe">
          </div>
          <div class="input-group">
            <label>Email</label>
            <input type="email" id="signupEmail" required placeholder="you@company.com">
          </div>
          <div class="input-group">
            <label>Password</label>
            <input type="password" id="signupPassword" required placeholder="••••••••" minlength="6">
          </div>
          <div class="input-group">
            <label>Confirm Password</label>
            <input type="password" id="signupConfirm" required placeholder="••••••••">
          </div>
          <button type="submit">Create Mifibot Account</button>
          <div id="signupMessage" class="message"></div>
        </form>
        <div class="switch-text">
          Already have an account? <a onclick="switchTab('login')">Log in</a>
        </div>
      </div>
    </div>

    <div class="footer">
      © 2026 Mifibot — Miniature Fire-Extinguishing Robot
    </div>
  </div>

  <script>
    function switchTab(tab) {
      document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
      document.querySelectorAll('.form').forEach(f => f.classList.remove('active'));

      if (tab === 'login') {
        document.querySelectorAll('.tab')[0].classList.add('active');
        document.getElementById('loginForm').classList.add('active');
      } else {
        document.querySelectorAll('.tab')[1].classList.add('active');
        document.getElementById('signupForm').classList.add('active');
      }

      // Clear messages
      document.getElementById('loginMessage').className = 'message';
      document.getElementById('signupMessage').className = 'message';
    }

    function handleSignup(e) {
      e.preventDefault();

      const name = document.getElementById('signupName').value.trim();
      const email = document.getElementById('signupEmail').value.trim().toLowerCase();
      const password = document.getElementById('signupPassword').value;
      const confirm = document.getElementById('signupConfirm').value;
      const messageEl = document.getElementById('signupMessage');

      if (password !== confirm) {
        showMessage(messageEl, 'Passwords do not match', 'error');
        return;
      }

      let users = JSON.parse(localStorage.getItem('mifibot_users') || '[]');

      if (users.find(u => u.email === email)) {
        showMessage(messageEl, 'This email is already registered', 'error');
        return;
      }

      users.push({ name, email, password });
      localStorage.setItem('mifibot_users', JSON.stringify(users));

      showMessage(messageEl, 'Account created successfully! You can now log in.', 'success');
      e.target.reset();
    }

    function handleLogin(e) {
      e.preventDefault();

      const email = document.getElementById('loginEmail').value.trim().toLowerCase();
      const password = document.getElementById('loginPassword').value;
      const messageEl = document.getElementById('loginMessage');

      let users = JSON.parse(localStorage.getItem('mifibot_users') || '[]');
      const user = users.find(u => u.email === email && u.password === password);

      if (user) {
        localStorage.setItem('mifibot_currentUser', JSON.stringify(user));
        showMessage(messageEl, `Welcome back, ${user.name}!`, 'success');
        
        // Optional: Redirect after successful login
        // setTimeout(() => {
        //   window.location.href = 'dashboard.html';
        // }, 1500);
      } else {
        showMessage(messageEl, 'Invalid email or password', 'error');
      }
    }

    function showMessage(el, text, type) {
      el.textContent = text;
      el.className = `message ${type}`;
    }
  </script>
</body>
</html>

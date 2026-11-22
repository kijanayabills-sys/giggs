<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GIGGS | Discover. Work. Earn.</title>
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

:root {
  --navy: #14213d;
  --blue: #2563eb;
  --light: #f3f6fc;
  --green: #16834a;
  --red: #b42318;
}

body {
  background: var(--light);
  color: #253047;
  line-height: 1.6;
}

header {
  background: var(--navy);
  color: white;
  padding: 16px 5%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
}

.logo {
  font-size: 26px;
  font-weight: bold;
}

.logo span {
  color: #60a5fa;
}

nav {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

button {
  border: 0;
  border-radius: 7px;
  padding: 11px 16px;
  cursor: pointer;
  font-size: 14px;
}

.primary {
  background: var(--blue);
  color: white;
}

.secondary {
  background: white;
  color: var(--navy);
}

.nav-btn {
  background: transparent;
  color: white;
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.hero {
  background: linear-gradient(120deg, #14213d, #2563eb);
  color: white;
  text-align: center;
  padding: 65px 20px;
}

.hero h1 {
  font-size: 38px;
  margin-bottom: 12px;
}

.hero p {
  max-width: 650px;
  margin: 0 auto 22px;
}

.container {
  width: 92%;
  max-width: 1100px;
  margin: 30px auto;
}

h1, h2, h3 {
  color: var(--navy);
  margin-bottom: 14px;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
  margin: 20px 0;
}

.card, .panel, form {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 3px 12px #0000000d;
  margin-bottom: 18px;
}

form {
  max-width: 500px;
  margin: 25px auto;
}

label {
  display: block;
  margin-top: 12px;
  font-weight: bold;
}

input, textarea, select {
  width: 100%;
  padding: 12px;
  margin: 7px 0 12px;
  border: 1px solid #ccd5e4;
  border-radius: 7px;
  font-size: 15px;
}

textarea {
  min-height: 100px;
  resize: vertical;
}

form button {
  width: 100%;
  margin-top: 8px;
}

.page {
  display: none;
}

.page.active {
  display: block;
}

.message {
  margin-top: 12px;
  overflow-wrap: anywhere;
}

.success {
  color: var(--green);
}

.error {
  color: var(--red);
}

.notice {
  background: #fff6dc;
  border-left: 4px solid #e5b43c;
  padding: 14px;
  margin: 18px 0;
}

.small {
  font-size: 13px;
  color: #68758a;
}

.item {
  background: white;
  border: 1px solid #e1e7f0;
  border-radius: 9px;
  padding: 16px;
  margin: 12px 0;
}

.item button {
  margin: 6px 4px 0 0;
}

footer {
  background: var(--navy);
  color: white;
  text-align: center;
  padding: 25px;
  margin-top: 45px;
}

footer p {
  color: white;
}

@media(max-width: 650px) {
  header {
    justify-content: center;
  }

  nav {
    justify-content: center;
  }

  .hero h1 {
    font-size: 30px;
  }
}
</style>
</head>
<body>
<header>
  <div class="logo">GIG<span>GS</span></div>
  <nav>
    <button class="nav-btn" type="button" onclick="showPage('home')">Home</button>
    <button class="nav-btn" type="button" onclick="showPage('tasks')">Explore Gigs</button>
    <button class="nav-btn" type="button" onclick="showPage('login')">Login</button>
    <button class="primary" type="button" onclick="showPage('register')">Join Now</button>
  </nav>
</header>

<main>

<section id="home" class="page active">
  <div class="hero">
    <h1>Discover. Work. Earn.</h1>
    <p>Discover opportunities, complete tasks and grow your digital skills with GIGGS.</p>
    <button class="primary" onclick="showPage('tasks')">Explore Gigs</button>
    <button class="secondary" onclick="showPage('register')">Create Account</button>
  </div>

  <div class="container">
    <h2>How GIGGS Works</h2>
    <div class="cards">
      <div class="card">
        <h3>01. Discover</h3>
        <p>Explore opportunities published by administrators.</p>
      </div>
      <div class="card">
        <h3>02. Apply</h3>
        <p>Choose an opportunity and follow its instructions.</p>
      </div>
      <div class="card">
        <h3>03. Submit</h3>
        <p>Send your completed work for review.</p>
      </div>
    </div>
  </div>
</section>

<section id="register" class="page">
  <form id="registerForm">
    <h2>Create GIGGS Account</h2>

    <label>Full Name</label>
    <input id="regName" type="text" required>

    <label>Email Address</label>
    <input id="regEmail" type="email" required>

    <label>Password</label>
    <input id="regPassword" type="password" minlength="6" required>

    <button class="primary" id="registerButton">Create Account</button>
    <p id="registerMessage" class="message"></p>

    <p>Already registered?
      <a href="#" onclick="showPage('login');return false;">Login here</a>
    </p>
  </form>
</section>

<section id="login" class="page">
  <form id="loginForm">
    <h2>Login to GIGGS</h2>

    <label>Email Address</label>
    <input id="loginEmail" type="email" required>

    <label>Password</label>
    <input id="loginPassword" type="password" required>

    <button class="primary" id="loginButton">Login</button>
    <p id="loginMessage" class="message"></p>

    <p>Don't have an account?
      <a href="#" onclick="showPage('register');return false;">Register here</a>
    </p>
  </form>
</section>

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

    body {
      background: #f4f7fc;
      color: #172b4d;
    }

    header {
      background: #102a56;
      color: white;
      padding: 18px 6%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 15px;
    }

    header h2 {
      font-size: 25px;
      letter-spacing: 1px;
    }

    nav {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
      align-items: center;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-size: 14px;
      cursor: pointer;
    }

    .hero {
      background: linear-gradient(120deg, #102a56, #2563eb);
      color: white;
      text-align: center;
      padding: 75px 20px;
    }

    .hero h1 {
      font-size: 38px;
      margin-bottom: 15px;
    }

    .hero p {
      font-size: 17px;
      margin-bottom: 25px;
    }

    .container {
      width: 90%;
      max-width: 900px;
      margin: 35px auto;
    }

    .panel {
      background: white;
      padding: 28px;
      border-radius: 12px;
      box-shadow: 0 3px 15px rgba(0,0,0,0.07);
      margin-bottom: 25px;
    }

    h2, h3 {
      margin-bottom: 15px;
    }

    input {
      width: 100%;
      padding: 13px;
      margin: 9px 0 15px;
      border: 1px solid #ccd5e2;
      border-radius: 7px;
      font-size: 15px;
    }

    button {
      background: #2563eb;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 7px;
      cursor: pointer;
      font-size: 15px;
    }

    button:hover {
      background: #1749b1;
    }

    button:disabled {
      opacity: 0.6;
      cursor: not-allowed;
    }

    .secondary {
      background: #102a56;
    }

    .message {
      margin-top: 14px;
      font-size: 14px;
      line-height: 1.5;
      overflow-wrap: anywhere;
    }

    .success {
      color: #087443;
    }

    .error {
      color: #c62828;
    }

    .muted {
      color: #65748b;
      font-size: 14px;
      line-height: 1.5;
    }

    .gig {
      border: 1px solid #e0e6ef;
      padding: 18px;
      border-radius: 9px;
      margin-top: 15px;
    }

    .gig p {
      margin: 8px 0 14px;
      color: #65748b;
    }

    .hidden {
      display: none;
    }

    footer {
      background: #102a56;
      color: white;
      text-align: center;
      padding: 25px;
      margin-top: 50px;
      font-size: 14px;
    }

    @media (max-width: 600px) {
      .hero h1 {
        font-size: 29px;
      }

      header {
        flex-direction: column;
      }
    }
  </style>
</head>

<body>

<header>
  <h2>GIGGS</h2>
  <nav>
    <a href="#home">Home</a>
    <a href="#gigs">Explore Gigs</a>
    <a href="#login" id="loginNav">Login</a>
    <a href="#register" id="joinNav">Join Now</a>
    <a href="#account" id="accountNav" class="hidden">My Account</a>
    <a href="#" id="logoutNav" class="hidden">Logout</a>
  </nav>
</header>

<section class="hero" id="home">
  <h1>Discover. Work. Earn.</h1>
  <p>Discover opportunities, explore gigs and build your skills with GIGGS.</p>
  <button onclick="showSection('register')">Get Started</button>
  <button class="secondary" onclick="showSection('gigs')">Explore Gigs</button>
</section>

<main class="container">

  <section id="register" class="panel hidden">
    <h2>Create Your GIGGS Account</h2>
    <p class="muted">Register with your email address to get started.</p>

    <form id="registerForm">
      <label for="fullName">Full Name</label>
      <input type="text" id="fullName" placeholder="Enter your full name" required>

      <label for="regEmail">Email Address</label>
      <input type="email" id="regEmail" placeholder="Enter your email" required>

      <label for="regPassword">Password</label>
      <input type="password" id="regPassword" placeholder="Create a password" minlength="8" required>

      <button type="submit" id="registerButton">Create Account</button>
    </form>

    <p id="registerMessage" class="message"></p>

    <p class="muted">
      Already have an account?
      <a href="#login" onclick="showSection('login')">Login here</a>
    </p>
  </section>

  <section id="login" class="panel hidden">
    <h2>Login to GIGGS</h2>
    <p class="muted">Enter your registered email and password.</p>

    <form id="loginForm">
      <label for="loginEmail">Email Address</label>
      <input type="email" id="loginEmail" placeholder="Enter your email" required>

      <label for="loginPassword">Password</label>
      <input type="password" id="loginPassword" placeholder="Enter your password" required>

      <button type="submit" id="loginButton">Login</button>
    </form>

    <p id="loginMessage" class="message"></p>

    <p class="muted">
      Don't have an account?
      <a href="#register" onclick="showSection('register')">Join now</a>
    </p>
  </section>

  <section id="account" class="panel hidden">
    <h2>My GIGGS Account</h2>
    <p id="accountEmail"></p>
    <p class="muted">You are signed in.</p>
    <button onclick="showSection('gigs')">Explore Gigs</button>
  </section>

  <section id="gigs" class="panel">
    <h2>Explore Gigs</h2>
    <p class="muted">
      Browse sample opportunities. These listings are demonstrations;
      real gig applications and rewards are not active yet.
    </p>

    <div class="gig">
      <h3>Online Research Assistant</h3>
      <p>Help organize information and carry out basic research tasks.</p>
      <button onclick="demoApply()">View Opportunity</button>
    </div>

    <div class="gig">
      <h3>Content Writing</h3>
      <p>Practice writing short articles and simple online content.</p>
      <button onclick="demoApply()">View Opportunity</button>
    </div>

    <div class="gig">
      <h3>Data Organization</h3>
      <p>Help arrange information into organized digital records.</p>
      <button onclick="demoApply()">View Opportunity</button>
    </div>
  </section>

  <section class="panel">
    <h2>About GIGGS</h2>
    <p>
      GIGGS is designed to connect users with opportunities to discover
      gigs, develop skills and complete tasks. Gig posting is reserved
      for administrators.
    </p>
  </section>

</main>

<footer>
  <h3>GIGGS</h3>
  <p>Discover. Work. Earn.</p>
  <p>© 2026 GIGGS. All rights reserved.</p>
</footer>

<script>
  const SUPABASE_URL = "https://fvmqjqjojfbeiiltauxm.supabase.co";

  const SUPABASE_KEY = "sb_publishable_ugLuC8Q3J6-mh5rSqqrD0Q_-GoHc3yS";

  const supabaseClient = window.supabase.createClient(
    SUPABASE_URL,
    SUPABASE_KEY
  );

  function showSection(sectionId) {
    const sections = ["register", "login", "account"];

    sections.forEach(function(id) {
      document.getElementById(id).classList.add("hidden");
    });

    if (sections.includes(sectionId)) {
      document.getElementById(sectionId).classList.remove("hidden");
    }

    if (sectionId === "gigs") {
      document.getElementById("gigs").scrollIntoView({
        behavior: "smooth"
      });
    } else {
      window.scrollTo({
        top: 0,
        behavior: "smooth"
      });
    }
  }

  function showMessage(elementId, message, type) {
    const element = document.getElementById(elementId);
    element.textContent = message;
    element.className = "message " + type;
  }

  function updateNavigation(user) {
    document.getElementById("loginNav").classList.toggle("hidden", !!user);
    document.getElementById("joinNav").classList.toggle("hidden", !!user);
    document.getElementById("accountNav").classList.toggle("hidden", !user);
    document.getElementById("logoutNav").classList.toggle("hidden", !user);

    if (user) {
      document.getElementById("accountEmail").textContent =
        "Signed in as: " + user.email;
    }
  }

  document.getElementById("registerForm").addEventListener("submit", async function(event) {
    event.preventDefault();

    const button = document.getElementById("registerButton");
    const fullName = document.getElementById("fullName").value.trim();
    const email = document.getElementById("regEmail").value.trim();
    const password = document.getElementById("regPassword").value;

    button.disabled = true;
    button.textContent = "Creating account...";

    showMessage("registerMessage", "Please wait...", "");

    try {
      const { data, error } = await supabaseClient.auth.signUp({
        email: email,
        password: password,
        options: {
          data: {
            full_name: fullName
          },
          emailRedirectTo: "https://kijanayabills-sys.github.io/giggs/"
        }
      });

      if (error) {
        throw error;
      }

      if (data.session) {
        showMessage(
          "registerMessage",
          "Registration successful. Your account is ready.",
          "success"
        );
        updateNavigation(data.user);
        showSection("account");
      } else {
        showMessage(
          "registerMessage",
          "Registration submitted successfully. Please check your email and confirm your account before logging in.",
          "success"
        );
      }

      document.getElementById("registerForm").reset();

    } catch (error) {
      showMessage("registerMessage", error.message, "error");
    } finally {
      button.disabled = false;
      button.textContent = "Create Account";
    }
  });

  document.getElementById("loginForm").addEventListener("submit", async function(event) {
    event.preventDefault();

    const button = document.getElementById("loginButton");
    const email = document.getElementById("loginEmail").value.trim();
    const password = document.getElementById("loginPassword").value;

    button.disabled = true;
    button.textContent = "Logging in...";

    showMessage("loginMessage", "Please wait...", "");

    try {
      const { data, error } = await supabaseClient.auth.signInWithPassword({
        email: email,
        password: password
      });

      if (error) {
        throw error;
      }

      updateNavigation(data.user);
      document.getElementById("loginForm").reset();
      showSection("account");

    } catch (error) {
      showMessage("loginMessage", error.message, "error");
    } finally {
      button.disabled = false;
      button.textContent = "Login";
    }
  });

  document.getElementById("logoutNav").addEventListener("click", async function(event) {
    event.preventDefault();

    const { error } = await supabaseClient.auth.signOut();

    if (error) {
      alert(error.message);
      return;
    }

    updateNavigation(null);
    showSection("login");
    showMessage("loginMessage", "You have logged out successfully.", "success");
  });

  async function checkSession() {
    const { data, error } = await supabaseClient.auth.getSession();

    if (error) {
      console.error(error.message);
      return;
    }

    updateNavigation(data.session ? data.session.user : null);
  }

  supabaseClient.auth.onAuthStateChange(function(event, session) {
    updateNavigation(session ? session.user : null);
  });

  function demoApply() {
    alert(
      "This is a sample GIGGS opportunity. Real applications will be available after the gig database and application system are connected."
    );
  }

  checkSession();

  const initialSection = window.location.hash.replace("#", "");

  if (["register", "login", "account"].includes(initialSection)) {
    showSection(initialSection);
  } else {
    showSection("gigs");
  }
</script>

</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GIGGS | Discover. Work. Earn.</title>
<style>
:root {
  --navy:#102b65;
  --blue:#1677e8;
  --light:#f3f6fc;
  --green:#087b4b;
}
* { box-sizing:border-box; margin:0; padding:0; font-family:Arial,sans-serif; }
body { background:var(--light); color:#24344d; }
header {
  background:var(--navy); color:white; padding:18px;
  display:flex; justify-content:space-between;
  align-items:center; flex-wrap:wrap; gap:12px;
}
.logo { font-size:27px; font-weight:bold; letter-spacing:2px; }
.logo span { color:#48c6ef; }
nav { display:flex; gap:7px; flex-wrap:wrap; }
button {
  padding:12px 16px; border:0; border-radius:7px;
  cursor:pointer; font-weight:bold;
}
button:disabled { opacity:.6; cursor:not-allowed; }
.primary { background:var(--blue); color:white; }
.secondary { background:#e8effb; color:var(--navy); }
.nav-btn { background:transparent; color:white; }
.page { display:none; }
.page.active { display:block; }
.hero {
  background:linear-gradient(120deg,var(--navy),var(--blue));
  color:white; text-align:center; padding:65px 20px;
}
.hero h1 { font-size:38px; margin-bottom:15px; color:white; }
.hero p { line-height:1.7; margin-bottom:22px; }
.hero button { margin:5px; }
.container { width:92%; max-width:1100px; margin:30px auto; }
h1,h2 { color:var(--navy); margin-bottom:15px; }
.cards {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(190px,1fr));
  gap:17px; margin:22px 0;
}
.card,.panel,form {
  background:white; padding:22px; border-radius:11px;
  box-shadow:0 3px 12px #0000000d;
}
.card h3 { color:var(--navy); margin-bottom:12px; }
.card p { line-height:1.5; margin-bottom:12px; }
.amount { font-size:25px; font-weight:bold; color:var(--navy); }
form { max-width:480px; margin:30px auto; }
form h2 { margin-bottom:20px; }
label { display:block; margin-top:12px; }
input {
  width:100%; padding:13px; margin:8px 0 14px;
  border:1px solid #ccd5e4; border-radius:7px; font-size:15px;
}
form button { width:100%; margin-top:8px; }
.message { margin-top:14px; line-height:1.5; overflow-wrap:anywhere; }
.success { color:var(--green); }
.error { color:#b42318; }
.notice {
  background:#fff6dc; border-left:4px solid #e5b43c;
  padding:14px; margin:18px 0; line-height:1.5;
}
.small { font-size:13px; color:#68758a; line-height:1.5; }
footer {
  background:var(--navy); color:white; text-align:center;
  padding:25px; margin-top:50px;
}
a { color:var(--blue); }
@media(max-width:650px) {
  header { justify-content:center; }
  nav { justify-content:center; }
  .hero h1 { font-size:30px; }
  .container { width:94%; }
}
</style>
</head>

<body>

<header>
  <div class="logo">GIG<span>GS</span></div>
  <nav>
    <button class="nav-btn" onclick="showPage('home')">Home</button>
    <button class="nav-btn" onclick="showPage('tasks')">Explore Gigs</button>
    <button class="nav-btn" onclick="showPage('login')">Login</button>
    <button class="primary" onclick="showPage('register')">Join Now</button>
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
        <p>Explore opportunities published by GIGGS administrators.</p>
      </div>
      <div class="card">
        <h3>02. Apply</h3>
        <p>Choose an opportunity and follow its instructions.</p>
      </div>
      <div class="card">
        <h3>03. Complete</h3>
        <p>Complete the task and submit your work for review.</p>
      </div>
    </div>
  </div>
</section>

<section id="register" class="page">
  <form id="registerForm">
    <h2>Create Your GIGGS Account</h2>

    <label for="regName">Full Name</label>
    <input type="text" id="regName" autocomplete="name"
      required placeholder="Enter your full name">

    <label for="regEmail">Email Address</label>
    <input type="email" id="regEmail" autocomplete="email"
      required placeholder="Enter your email">

    <label for="regPassword">Password</label>
    <input type="password" id="regPassword"
      autocomplete="new-password" minlength="6"
      required placeholder="Create a password">

    <button class="primary" id="registerButton" type="submit">
      Create Account
    </button>

    <p id="registerMessage" class="message" role="status" aria-live="polite"></p>

    <p class="small">Use an email address you can access. Never share your password.</p>
    <p>Already registered?
      <a href="#" onclick="showPage('login');return false">Login</a>
    </p>
  </form>
</section>

<section id="login" class="page">
  <form id="loginForm">
    <h2>Login to GIGGS</h2>

    <label for="loginEmail">Email Address</label>
    <input type="email" id="loginEmail" autocomplete="email"
      required placeholder="Enter your email">

    <label for="loginPassword">Password</label>
    <input type="password" id="loginPassword"
      autocomplete="current-password" required
      placeholder="Enter your password">

    <button class="primary" id="loginButton" type="submit">Login</button>

    <p id="loginMessage" class="message" role="status" aria-live="polite"></p>

    <p>New to GIGGS?
      <a href="#" onclick="showPage('register');return false">Create Account</a>
    </p>
  </form>
</section>

<section id="dashboard" class="page">
  <div class="container">
    <h1>User Dashboard</h1>
    <p id="welcomeName">Welcome to GIGGS.</p>

    <div class="notice">
      Your account is connected to Supabase.
      Earnings and rewards are not yet active.
    </div>

    <div class="cards">
      <div class="card">
        <h3>Total Earnings</h3>
        <div class="amount">KSh 0.00</div>
      </div>
      <div class="card">
        <h3>Available Rewards</h3>
        <div class="amount">0</div>
      </div>
      <div class="card">
        <h3>Completed Tasks</h3>
        <div class="amount">0</div>
      </div>
      <div class="card">
        <h3>Total Referrals</h3>
        <div class="amount">0</div>
      </div>
    </div>

    <div class="panel">
      <h2>Getting Started</h2>
      <p>Explore available opportunities on GIGGS.</p>
      <button class="primary" onclick="showPage('tasks')">Explore Gigs</button>
    </div>

    <br>
    <button class="secondary" onclick="logout()">Logout</button>
  </div>
</section>

<section id="tasks" class="page">
  <div class="container">
    <h1>Available Gigs</h1>
    <div class="notice">
      These are sample opportunities, not active paid assignments.
    </div>
    <div class="cards">
      <div class="card">
        <h3>Content Writing</h3>
        <p>Practice creating an original short article.</p>
        <button class="primary" onclick="applyTask()">View Gig</button>
      </div>
      <div class="card">
        <h3>Data Entry</h3>
        <p>Practice organizing information in a spreadsheet.</p>
        <button class="primary" onclick="applyTask()">View Gig</button>
      </div>
      <div class="card">
        <h3>Graphic Design</h3>
        <p>Practice creating an original promotional design.</p>
        <button class="primary" onclick="applyTask()">View Gig</button>
      </div>
    </div>
  </div>
</section>

</main>

<footer>
  <h3>GIGGS</h3>
  <p>Discover. Work. Earn.</p>
  <p class="small">© 2026 GIGGS. All rights reserved.</p>
</footer>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<script>
"use strict";

// GIGGS SUPABASE CONFIGURATION
const SUPABASE_URL = "https://fvmqjqjojfbeiiltauxm.supabase.co";
const SUPABASE_KEY = "sb_publishable_ugLuC8Q3J6-mh5rSqqrD0Q_-GoHc3yS";

let supabaseClient = null;
let currentUser = null;

function setMessage(elementId, message, type) {
  const element = document.getElementById(elementId);
  element.className = "message" + (type ? " " + type : "");
  element.textContent = message;
}

function initSupabase() {
  if (!window.supabase ||
      typeof window.supabase.createClient !== "function") {
    setMessage("registerMessage",
      "Supabase library did not load. Check your internet connection.",
      "error");
    setMessage("loginMessage",
      "Supabase library did not load. Check your internet connection.",
      "error");
    return false;
  }

  try {
    supabaseClient = window.supabase.createClient(
      SUPABASE_URL,
      SUPABASE_KEY,
      {
        auth: {
          autoRefreshToken: true,
          persistSession: true,
          detectSessionInUrl: true
        }
      }
    );
    return true;
  } catch (error) {
    console.error("Supabase initialization failed:", error);
    setMessage("registerMessage",
      "Supabase initialization failed. Please refresh the page.",
      "error");
    return false;
  }
}

function showPage(pageId) {
  const page = document.getElementById(pageId);
  if (!page) return;

  const privatePages = ["dashboard"];

  if (privatePages.includes(pageId) && !currentUser) {
    showPage("login");
    return;
  }

  document.querySelectorAll(".page").forEach(item => {
    item.classList.remove("active");
  });

  page.classList.add("active");

  if (currentUser) updateAccountDisplay();

  window.scrollTo(0, 0);
}

function updateAccountDisplay() {
  if (!currentUser) return;

  const name = currentUser.user_metadata?.full_name || "GIGGS User";

  document.getElementById("welcomeName").textContent =
    "Welcome, " + name;
}

// REGISTRATION
document.getElementById("registerForm").addEventListener(
  "submit", async function(event) {
    event.preventDefault();

    if (!supabaseClient) {
      setMessage("registerMessage",
        "Supabase is not connected. Refresh and try again.", "error");
      return;
    }

    const name = document.getElementById("regName").value.trim();
    const email = document.getElementById("regEmail").value.trim();
    const password = document.getElementById("regPassword").value;

    const button = document.getElementById("registerButton");
    button.disabled = true;
    button.textContent = "Creating account...";

    setMessage("registerMessage", "Connecting to Supabase...", "");

    try {
      const { data, error } = await supabaseClient.auth.signUp({
        email: email,
        password: password,
        options: {
          data: { full_name: name },
          emailRedirectTo: "https://kijanayabills-sys.github.io/giggs/"
        }
      });

      if (error) throw error;

      if (data.user && data.session) {
        currentUser = data.user;
        this.reset();

        setMessage("registerMessage",
          "Account created successfully.", "success");

        showPage("dashboard");

      } else if (data.user) {
        this.reset();

        setMessage("registerMessage",
          "Registration accepted! Check your email inbox and spam folder for a confirmation message. Confirm your email before logging in.",
          "success");

      } else {
        setMessage("registerMessage",
          "Supabase returned no user record. Please try again.",
          "error");
      }

    } catch (error) {
      console.error("Registration error:", error);

      setMessage("registerMessage",
        "Registration failed: " + error.message, "error");

    } finally {
      button.disabled = false;
      button.textContent = "Create Account";
    }
  }
);

// LOGIN
document.getElementById("loginForm").addEventListener(
  "submit", async function(event) {
    event.preventDefault();

    if (!supabaseClient) {
      setMessage("loginMessage",
        "Supabase is not connected. Refresh and try again.", "error");
      return;
    }

    const email = document.getElementById("loginEmail").value.trim();
    const password = document.getElementById("loginPassword").value;

    const button = document.getElementById("loginButton");
    button.disabled = true;
    button.textContent = "Signing in...";

    setMessage("loginMessage", "Checking your account...", "");

    try {
      const { data, error } =
        await supabaseClient.auth.signInWithPassword({
          email: email,
          password: password
        });

      if (error) throw error;

      currentUser = data.user;
      this.reset();

      setMessage("loginMessage", "Login successful.", "success");
      showPage("dashboard");

    } catch (error) {
      console.error("Login error:", error);

      setMessage("loginMessage",
        "Login failed: " + error.message, "error");

    } finally {
      button.disabled = false;
      button.textContent = "Login";
    }
  }
);

// LOGOUT
async function logout() {
  if (!supabaseClient) return;

  const { error } = await supabaseClient.auth.signOut();

  if (error) {
    alert("Logout failed: " + error.message);
    return;
  }

  currentUser = null;
  showPage("home");
}

// SAMPLE GIG ACTION
function applyTask() {
  if (!currentUser) {
    showPage("login");
    return;
  }

  alert("This is a sample gig. Real applications and submissions will be implemented later.");
}

// RESTORE EXISTING SESSION
async function checkSession() {
  if (!supabaseClient) return;

  const { data, error } = await supabaseClient.auth.getSession();

  if (error) {
    console.error("Session check failed:", error.message);
    return;
  }

  currentUser = data.session?.user || null;

  if (currentUser) {
    updateAccountDisplay();

    if (window.location.hash.includes("access_token") ||
        window.location.search.includes("code=")) {
      showPage("dashboard");
    }
  }
}

// START SUPABASE
if (initSupabase()) {
  checkSession();

  supabaseClient.auth.onAuthStateChange((event, session) => {
    currentUser = session?.user || null;

    if (currentUser) {
      updateAccountDisplay();
    }
  });
}
</script>

</body>
</html>

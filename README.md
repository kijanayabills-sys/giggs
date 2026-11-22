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

<!-- I
<section id="dashboard" class="page">
  <div class="container">
    <h1 id="welcomeName">Welcome to GIGGS</h1>
    
<section id="tasks" class="page">
  <div class="container">
    <h1>Explore Available Gigs</h1>

    <div class="notice">
      Browse opportunities published by GIGGS administrators.
      Rewards shown are indicative only.
    </div>

    <div id="gigsList">Loading gigs...</div>

    <button class="secondary" onclick="showPage('dashboard')">
      Back to Dashboard
    </button>
  </div>
</section>


    <div class="notice">
      Your account dashboard. Track your applications and submissions here.
    </div>

    <div class="cards">
      <div class="card">
        <h3>My Applications</h3>
        <p id="applicationCount">0</p>
      </div>
      <div class="card">
        <h3>My Submissions</h3>
        <p id="submissionCount">0</p>
      </div>
      <div class="card">
        <h3>Account Role</h3>
        <p id="accountRole">User</p>
      </div>
    </div>

    <p id="profileLoadMessage" class="message"></p>

    <h2>My Applications</h2>
    <div id="myApplications">Loading applications...</div>

    <button class="primary" onclick="showPage('tasks')">
      Explore Gigs
    </button>
    <button class="secondary" onclick="showPage('profile')">
      My Profile
    </button>
    <button class="secondary" onclick="logout()">Logout</button>
  </div>
</section>

<section id="admin" class="page">

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
<section id="admin" class="page">
  <div class="container">
    <h1>GIGGS Admin Dashboard</h1>

    <div class="notice">
      Administrator access is controlled by Supabase database permissions.
    </div>

    <div class="cards">
      <div class="card">
        <h3>Total Gigs</h3>
        <p id="adminGigCount">0</p>
      </div>
      <div class="card">
        <h3>Applications</h3>
        <p id="adminApplicationCount">0</p>
      </div>
      <div class="card">
        <h3>Submissions</h3>
        <p id="adminSubmissionCount">0</p>
      </div>
      <div class="card">
        <h3>Registered Profiles</h3>
        <p id="adminUserCount">0</p>
      </div>
    </div>

    <div class="panel">
      <h2 id="gigFormHeading">Publish a New Gig</h2>

      <form id="gigForm">
        <input type="hidden" id="gigId">

        <label>Gig Title</label>
        <input id="gigTitle" type="text" required>

        <label>Description and Instructions</label>
        <textarea id="gigDescription" required></textarea>

        <label>Indicative Reward</label>
        <input id="gigReward" type="number" min="0" step="0.01" required>

        <label>Status</label>
        <select id="gigStatus">
          <option value="open">Open</option>
          <option value="closed">Closed</option>
        </select>

        <button class="primary" id="gigSaveButton">Publish Gig</button>
        <button class="secondary" type="button" onclick="resetGigForm()">Clear Form</button>

        <p id="gigMessage" class="message"></p>
      </form>
    </div>

    <h2>Manage Gigs</h2>
    <div id="adminGigsList">Loading gigs...</div>

    <h2>Review Applications</h2>
    <div id="adminApplicationsList">Loading applications...</div>

    <h2>Review Submissions</h2>
    <div id="adminSubmissionsList">Loading submissions...</div>

    <button class="secondary" onclick="logout()">Logout</button>
  </div>
</section>

</main>

<footer>
  <h3>GIGGS</h3>
  <p>Discover. Work. Earn.</p>
  <p class="small">© 2026 GIGGS. All rights reserved.</p>
</footer>
<script>
"use strict";

// GIGGS Supabase configuration
const SUPABASE_URL = "https://fvmqjqjojfbeiiltauxm.supabase.co";
const SUPABASE_KEY = "sb_publishable_ugLuC8Q3J6-mh5rSqqrD0Q_-GoHc3yS";

let supabaseClient = null;
let currentUser = null;
let currentProfile = null;
let allGigs = [];

const el = id => document.getElementById(id);

function escapeHTML(value) {
  return String(value ?? "").replace(/[&<>"']/g, char => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#039;"
  })[char]);
}

function setMessage(id, message, type = "") {
  const element = el(id);
  if (!element) return;
  element.className = "message " + type;
  element.textContent = message;
}

function initSupabase() {
  if (!window.supabase) {
    setMessage("loginMessage", "Supabase library failed to load. Refresh the page.");
    return false;
  }

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
}

function showPage(pageId) {
  const page = el(pageId);
  if (!page) return;

  if (["dashboard", "profile", "submitWork", "admin"].includes(pageId)
      && !currentUser) {
    showPage("login");
    return;
  }

  if (pageId === "admin" &&
      currentProfile?.role !== "admin") {
    alert("Administrator access only.");
    showPage("dashboard");
    return;
  }

  document.querySelectorAll(".page").forEach(section => {
    section.classList.remove("active");
  });

  page.classList.add("active");
  window.scrollTo(0, 0);

  if (currentUser && pageId === "dashboard") {
    loadDashboard();
  }

  if (pageId === "tasks") {
    loadGigs();
  }

  if (pageId === "admin" && currentProfile?.role === "admin") {
    loadAdminDashboard();
  }
}

async function loadProfile() {
  if (!currentUser) return false;

  const { data, error } = await supabaseClient
    .from("profiles")
    .select("id,full_name,email,role")
    .eq("id", currentUser.id)
    .maybeSingle();

  if (error) {
    setMessage("profileLoadMessage",
      "Profile loading failed: " + error.message, "error");
    return false;
  }

  if (!data) {
    setMessage("profileLoadMessage",
      "No profile was found for this account.", "error");
    return false;
  }

  currentProfile = data;

  const name = data.full_name ||
    currentUser.user_metadata?.full_name ||
    "GIGGS User";

  el("welcomeName").textContent = "Welcome, " + name;
  el("profileName").textContent = "Name: " + name;
  el("profileEmail").textContent = "Email: " + (data.email || currentUser.email || "");
  el("profileRole").textContent = "Role: " + (data.role || "user");
  el("accountRole").textContent = data.role || "user";

  setMessage("profileLoadMessage",
    "Profile loaded successfully.", "success");

  return true;
}

async function loadGigs() {
  el("gigsList").textContent = "Loading gigs...";

  const { data, error } = await supabaseClient
    .from("gigs")
    .select("id,title,description,reward,status")
    .eq("status", "open");

  if (error) {
    el("gigsList").textContent = "Could not load gigs: " + error.message;
    return;
  }

  allGigs = data || [];

  if (!allGigs.length) {
    el("gigsList").innerHTML = "<p>No open gigs available yet.</p>";
    return;
  }

  el("gigsList").innerHTML = allGigs.map(gig => `
    <div class="item">
      <h3>${escapeHTML(gig.title)}</h3>
      <p>${escapeHTML(gig.description)}</p>
      <p><strong>Indicative reward:</strong>
        ${escapeHTML(gig.reward)}</p>
      <button class="primary"
        onclick="applyToGig('${gig.id}')">Apply</button>
    </div>
  `).join("");
}

async function applyToGig(gigId) {
  if (!currentUser) {
    showPage("login");
    return;
  }

  const { error } = await supabaseClient
    .from("applications")
    .insert({
      gig_id: gigId,
      user_id: currentUser.id,
      status: "pending"
    });

  if (error) {
    alert("Application could not be saved: " + error.message);
    return;
  }

  alert("Application submitted successfully.");
  loadDashboard();
}

async function loadDashboard() {
  if (!currentUser) return;

  const { data: applications, error: appError } =
    await supabaseClient
      .from("applications")
      .select("id,gig_id,status,created_at")
      .eq("user_id", currentUser.id);

  if (appError) {
    el("myApplications").textContent =
      "Could not load applications: " + appError.message;
    return;
  }

  const myApps = applications || [];
  el("applicationCount").textContent = myApps.length;

  const { data: submissions, error: subError } =
    await supabaseClient
      .from("submissions")
      .select("id,application_id,status")
      .in("application_id",
        myApps.length ? myApps.map(a => a.id) : ["00000000-0000-0000-0000-000000000000"]);

  if (subError) {
    el("submissionCount").textContent = "Unavailable";
  } else {
    el("submissionCount").textContent = (submissions || []).length;
  }

  if (!myApps.length) {
    el("myApplications").innerHTML =
      "<p>No applications yet. Explore available gigs to get started.</p>";
    return;
  }

  const { data: gigs } = await supabaseClient
    .from("gigs")
    .select("id,title");

  const gigMap = {};
  (gigs || []).forEach(gig => {
    gigMap[gig.id] = gig.title;
  });

  el("myApplications").innerHTML = myApps.map(app => `
    <div class="item">
      <h3>${escapeHTML(gigMap[app.gig_id] || "Gig")}</h3>
      <p>Status: ${escapeHTML(app.status)}</p>
      ${app.status === "approved" ? `
        <button class="primary"
          onclick="openSubmission('${app.id}')">
          Submit Work
        </button>
      ` : ""}
    </div>
  `).join("");
}

function openSubmission(applicationId) {
  el("submissionApplicationId").value = applicationId;
  el("submissionText").value = "";
  setMessage("submissionMessage", "");
  showPage("submitWork");
}

el("submissionForm").addEventListener("submit", async function(e) {
  e.preventDefault();

  if (!currentUser) return;

  const applicationId = el("submissionApplicationId").value;
  const submissionText = el("submissionText").value.trim();

  if (!submissionText) return;

  const button = el("submissionButton");
  button.disabled = true;

  const { error } = await supabaseClient
    .from("submissions")
    .insert({
      application_id: applicationId,
      submission_text: submissionText,
      status: "pending"
    });

  button.disabled = false;

  if (error) {
    setMessage("submissionMessage",
      "Submission failed: " + error.message, "error");
    return;
  }

  setMessage("submissionMessage",
    "Your submission has been sent for review.", "success");

  this.reset();
  loadDashboard();
});

function resetGigForm() {
  el("gigForm").reset();
  el("gigId").value = "";
  el("gigFormHeading").textContent = "Publish a New Gig";
  el("gigSaveButton").textContent = "Publish Gig";
  setMessage("gigMessage", "");
}

el("gigForm").addEventListener("submit", async function(e) {
  e.preventDefault();

  if (currentProfile?.role !== "admin") {
    setMessage("gigMessage", "Administrator access required.", "error");
    return;
  }

  const id = el("gigId").value;

  const gig = {
    title: el("gigTitle").value.trim(),
    description: el("gigDescription").value.trim(),
    reward: Number(el("gigReward").value),
    status: el("gigStatus").value
  };

  const button = el("gigSaveButton");
  button.disabled = true;

  let result;

  if (id) {
    result = await supabaseClient
      .from("gigs")
      .update(gig)
      .eq("id", id);
  } else {
    result = await supabaseClient
      .from("gigs")
      .insert(gig);
  }

  button.disabled = false;

  if (result.error) {
    setMessage("gigMessage",
      "Could not save gig: " + result.error.message, "error");
    return;
  }

  setMessage("gigMessage",
    id ? "Gig updated successfully." : "Gig published successfully.",
    "success");

  resetGigForm();
  loadAdminDashboard();
  loadGigs();
});

async function editGig(gigId) {
  const { data, error } = await supabaseClient
    .from("gigs")
    .select("id,title,description,reward,status")
    .eq("id", gigId)
    .single();

  if (error) {
    alert("Could not open gig: " + error.message);
    return;
  }

  el("gigId").value = data.id;
  el("gigTitle").value = data.title;
  el("gigDescription").value = data.description;
  el("gigReward").value = data.reward;
  el("gigStatus").value = data.status;

  el("gigFormHeading").textContent = "Edit Gig";
  el("gigSaveButton").textContent = "Update Gig";

  el("gigForm").scrollIntoView({ behavior: "smooth" });
}

async function deleteGig(gigId) {
  if (!confirm("Delete this gig?")) return;

  const { error } = await supabaseClient
    .from("gigs")
    .delete()
    .eq("id", gigId);

  if (error) {
    alert("Could not delete gig: " + error.message);
    return;
  }

  alert("Gig deleted.");
  loadAdminDashboard();
}

async function reviewApplication(id, status) {
  const { error } = await supabaseClient
    .from("applications")
    .update({ status })
    .eq("id", id);

  if (error) {
    alert("Could not update application: " + error.message);
    return;
  }

  loadAdminDashboard();
}

async function reviewSubmission(id, status) {
  const { error } = await supabaseClient
    .from("submissions")
    .update({ status })
    .eq("id", id);

  if (error) {
    alert("Could not update submission: " + error.message);
    return;
  }

  loadAdminDashboard();
}

async function loadAdminDashboard() {
  if (currentProfile?.role !== "admin") return;

  el("adminGigsList").textContent = "Loading...";
  el("adminApplicationsList").textContent = "Loading...";
  el("adminSubmissionsList").textContent = "Loading...";

  const [gigResult, appResult, subResult, profileResult] =
    await Promise.all([
      supabaseClient.from("gigs")
        .select("id,title,description,reward,status"),
      supabaseClient.from("applications")
        .select("id,gig_id,user_id,status,created_at"),
      supabaseClient.from("submissions")
        .select("id,application_id,submission_text,status,created_at"),
      supabaseClient.from("profiles").select("id")
    ]);

  if (gigResult.error) {
    el("adminGigsList").textContent = gigResult.error.message;
    return;
  }

  const gigs = gigResult.data || [];
  const applications = appResult.data || [];
  const submissions = subResult.data || [];

  el("adminGigCount").textContent = gigs.length;
  el("adminApplicationCount").textContent = applications.length;
  el("adminSubmissionCount").textContent = submissions.length;
  el("adminUserCount").textContent =
    profileResult.error ? "Unavailable" : (profileResult.data || []).length;

  el("adminGigsList").innerHTML = gigs.length
    ? gigs.map(gig => `
      <div class="item">
        <h3>${escapeHTML(gig.title)}</h3>
        <p>${escapeHTML(gig.description)}</p>
        <p>Reward: ${escapeHTML(gig.reward)}</p>
        <p>Status: ${escapeHTML(gig.status)}</p>
        <button class="primary"
          onclick="editGig('${gig.id}')">Edit</button>
        <button class="secondary"
          onclick="deleteGig('${gig.id}')">Delete</button>
      </div>
    `).join("")
    : "<p>No gigs have been created.</p>";

  const gigMap = {};
  gigs.forEach(gig => gigMap[gig.id] = gig.title);

  const appMap = {};
  applications.forEach(app => appMap[app.id] = app);

  el("adminApplicationsList").innerHTML = applications.length
    ? applications.map(app => `
      <div class="item">
        <h3>${escapeHTML(gigMap[app.gig_id] || "Gig")}</h3>
        <p>Application ID: ${escapeHTML(app.id)}</p>
        <p>User ID: ${escapeHTML(app.user_id)}</p>
        <p>Status: ${escapeHTML(app.status)}</p>
        <button class="primary"
          onclick="reviewApplication('${app.id}','approved')">
          Approve
        </button>
        <button class="secondary"
          onclick="reviewApplication('${app.id}','rejected')">
          Reject
        </button>
      </div>
    `).join("")
    : "<p>No applications received.</p>";

  el("adminSubmissionsList").innerHTML = submissions.length
    ? submissions.map(sub => {
        const app = appMap[sub.application_id];
        const gigTitle = app ? gigMap[app.gig_id] : "Gig";

        return `
          <div class="item">
            <h3>${escapeHTML(gigTitle || "Gig")}</h3>
            <p>${escapeHTML(sub.submission_text)}</p>
            <p>Status: ${escapeHTML(sub.status)}</p>
            <button class="primary"
              onclick="reviewSubmission('${sub.id}','approved')">
              Approve
            </button>
            <button class="secondary"
              onclick="reviewSubmission('${sub.id}','rejected')">
              Reject
            </button>
          </div>
        `;
      }).join("")
    : "<p>No submissions received.</p>";
}

async function logout() {
  const { error } = await supabaseClient.auth.signOut();

  if (error) {
    alert("Logout failed: " + error.message);
    return;
  }

  currentUser = null;
  currentProfile = null;
  showPage("home");
}

async function handleSession(session) {
  currentUser = session?.user || null;
  currentProfile = null;

  if (!currentUser) {
    showPage("home");
    return;
  }

  const loaded = await loadProfile();

  if (loaded) {
    showPage("dashboard");
    loadDashboard();
  } else {
    showPage("login");
  }
}

el("registerForm").addEventListener("submit", async function(e) {
  e.preventDefault();

  const button = el("registerButton");
  button.disabled = true;

  const name = el("regName").value.trim();
  const email = el("regEmail").value.trim();
  const password = el("regPassword").value;

  const { data, error } = await supabaseClient.auth.signUp({
    email,
    password,
    options: {
      data: { full_name: name },
      emailRedirectTo: "https://kijanayabills-sys.github.io/giggs/"
    }
  });

  button.disabled = false;

  if (error) {
    setMessage("registerMessage", error.message, "error");
    return;
  }

  if (data.session) {
    await handleSession(data.session);
  } else {
    setMessage("registerMessage",
      "Registration received. Check your email to confirm your account before logging in.",
      "success");
    this.reset();
  }
});

el("loginForm").addEventListener("submit", async function(e) {
  e.preventDefault();

  const button = el("loginButton");
  button.disabled = true;
  setMessage("loginMessage", "Checking your account...");

  const email = el("loginEmail").value.trim();
  const password = el("loginPassword").value;

  const { data, error } = await supabaseClient.auth.signInWithPassword({
    email,
    password
  });

  button.disabled = false;

  if (error) {
    setMessage("loginMessage", error.message, "error");
    return;
  }

  this.reset();
  await handleSession(data.session);
});

async function startGIGGS() {
  const { data, error } = await supabaseClient.auth.getSession();

  if (error) {
    setMessage("loginMessage", error.message, "error");
    return;
  }

  await handleSession(data.session);

  supabaseClient.auth.onAuthStateChange((event, session) => {
    if (event === "SIGNED_OUT") {
      currentUser = null;
      currentProfile = null;
      showPage("home");
    }
  });
}

if (initSupabase()) {
  startGIGGS();
}
</script>
</body>
</html>

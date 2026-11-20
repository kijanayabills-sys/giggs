# giggs
sales and marketing

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gigs Pesa | Dashboard</title>

<style>
:root {
  --navy: #071b3a;
  --gold: #d9aa35;
  --light: #f4f6fa;
  --white: #ffffff;
  --text: #24344d;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: var(--light);
  color: var(--text);
}

header {
  background: var(--navy);
  color: white;
  padding: 18px 25px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  color: var(--gold);
  font-size: 23px;
  font-weight: bold;
}

header span {
  font-size: 13px;
}

.container {
  display: flex;
  min-height: calc(100vh - 65px);
}

.sidebar {
  width: 230px;
  background: var(--navy);
  padding: 20px 12px;
}

.sidebar button {
  display: block;
  width: 100%;
  padding: 14px;
  margin-bottom: 8px;
  background: transparent;
  color: white;
  border: none;
  text-align: left;
  border-radius: 7px;
  cursor: pointer;
  font-size: 15px;
}

.sidebar button:hover,
.sidebar button.active {
  background: var(--gold);
  color: var(--navy);
  font-weight: bold;
}

main {
  flex: 1;
  padding: 25px;
  min-width: 0;
}

.page {
  display: none;
}

.page.active {
  display: block;
}

h1, h2 {
  color: var(--navy);
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 18px;
  margin: 25px 0;
}

.card {
  background: white;
  padding: 22px;
  border-radius: 10px;
  box-shadow: 0 2px 9px #0000000d;
}

.card h3 {
  font-size: 14px;
  color: #68758a;
  margin-top: 0;
}

.amount {
  font-size: 25px;
  color: var(--navy);
  font-weight: bold;
}

.gold {
  color: #b1841c;
}

.panel {
  background: white;
  padding: 22px;
  border-radius: 10px;
  margin-top: 20px;
}

.action {
  background: var(--gold);
  color: var(--navy);
  padding: 11px 17px;
  border: none;
  border-radius: 6px;
  font-weight: bold;
  cursor: pointer;
}

.action:hover {
  opacity: .85;
}

input {
  padding: 12px;
  width: 100%;
  max-width: 400px;
  border: 1px solid #ccc;
  border-radius: 6px;
  margin: 8px 0 15px;
}

table {
  width: 100%;
  border-collapse: collapse;
  background: white;
}

th, td {
  padding: 13px;
  text-align: left;
  border-bottom: 1px solid #eee;
}

th {
  background: #edf1f7;
}

.notice {
  background: #fff6dc;
  border-left: 4px solid var(--gold);
  padding: 13px;
  border-radius: 5px;
  font-size: 13px;
}

footer {
  text-align: center;
  padding: 18px;
  color: #777;
}

@media(max-width: 700px) {
  .container {
    display: block;
  }

  .sidebar {
    width: 100%;
    display: flex;
    overflow-x: auto;
    padding: 8px;
  }

  .sidebar button {
    min-width: 115px;
    text-align: center;
    font-size: 12px;
    padding: 12px 7px;
  }

  main {
    padding: 16px;
  }

  header {
    padding: 16px;
  }

  table {
    font-size: 12px;
  }
}
</style>
</head>

<body>

<header>
  <div class="logo">GIGS PESA</div>
  <span>Earn, Connect and Grow</span>
</header>

<div class="container">

<nav class="sidebar">
  <button class="active" data-page="overview">Dashboard</button>
  <button data-page="tasks">Available Tasks</button>
  <button data-page="rewards">My Rewards</button>
  <button data-page="referrals">Referrals</button>
  <button data-page="transactions">Transactions</button>
  <button data-page="profile">My Profile</button>
</nav>

<main>

<section id="overview" class="page active">
  <h1>Welcome to Gigs Pesa!</h1>
  <p>Your personal earning opportunities dashboard.</p>

  <div class="notice">
    DEMO MODE: All figures and activities shown here are examples.
    No real payments or earnings are being processed.
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
    <p>Explore available opportunities and learn how Gigs Pesa works.</p>
    <button class="action" onclick="showPage('tasks')">
      Explore Tasks
    </button>
  </div>
</section>

<section id="tasks" class="page">
  <h1>Available Tasks</h1>
  <p>Explore sample opportunities.</p>

  <div class="card">
    <h3>Sample Task 01</h3>
    <p>Learn how online task platforms work.</p>
    <button class="action" onclick="demoMessage()">
      View Task
    </button>
  </div>

  <div class="card" style="margin-top:15px">
    <h3>Sample Task 02</h3>
    <p>Explore digital skills and online opportunities.</p>
    <button class="action" onclick="demoMessage()">
      View Task
    </button>
  </div>
</section>

<section id="rewards" class="page">
  <h1>My Rewards</h1>
  <div class="card">
    <h3>Demo Reward Balance</h3>
    <div class="amount gold">0 Points</div>
    <p>Reward information will appear here.</p>
  </div>
</section>

<section id="referrals" class="page">
  <h1>Referral Centre</h1>
  <div class="card">
    <h3>Your Referral Code</h3>
    <p>Not generated yet</p>
    <button class="action" onclick="demoMessage()">
      Generate Demo Code
    </button>
  </div>
  <p>Referral tracking will be connected to Supabase later.</p>
</section>

<section id="transactions" class="page">
  <h1>Transactions</h1>
  <div class="panel">
    <p>No transaction records available.</p>
    <p>Transaction history will appear here when connected to the backend.</p>
  </div>
</section>

<section id="profile" class="page">
  <h1>My Profile</h1>
  <div class="panel">
    <label>Full Name</label><br>
    <input type="text" placeholder="Enter your name"><br>

    <label>Email Address</label><br>
    <input type="email" placeholder="Enter your email"><br>

    <button class="action" onclick="demoMessage()">
      Save Demo Profile
    </button>
  </div>
</section>

</main>
</div>

<footer>
  © 2026 Gigs Pesa. All rights reserved.
</footer>

<script>
function showPage(pageId) {
  document.querySelectorAll('.page').forEach(page => {
    page.classList.remove('active');
  });

  document.querySelectorAll('.sidebar button').forEach(button => {
    button.classList.remove('active');
  });

  document.getElementById(pageId).classList.add('active');

  document.querySelector(
    '[data-page="' + pageId + '"]'
  ).classList.add('active');
}

document.querySelectorAll('.sidebar button').forEach(button => {
  button.addEventListener('click', () => {
    showPage(button.dataset.page);
  });
});

function demoMessage() {
  alert('This is a Gigs Pesa demo feature. Backend integration is coming next.');
}
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>

</body>
</html>

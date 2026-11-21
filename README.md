
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GIGGS | Discover. Work. Earn.</title>
<style>
:root{--navy:#102b65;--blue:#1677e8;--light:#f3f6fc;--white:#fff;--text:#24344d;--green:#087b4b;--red:#b42318}
*{box-sizing:border-box;margin:0;padding:0;font-family:Arial,sans-serif}
body{background:var(--light);color:var(--text)}
header{background:var(--navy);color:white;padding:16px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
.logo{font-size:27px;font-weight:bold;letter-spacing:2px}.logo span{color:#48c6ef}
nav{display:flex;gap:6px;flex-wrap:wrap}
button{padding:11px 14px;border:0;border-radius:7px;cursor:pointer;font-weight:bold;margin:3px}
button:disabled{opacity:.5;cursor:not-allowed}
.primary{background:var(--blue);color:white}.secondary{background:#e8effb;color:var(--navy)}
.nav-btn{background:transparent;color:white}.danger{background:#fee4e2;color:var(--red)}
.page{display:none}.page.active{display:block}
.hero{background:linear-gradient(120deg,var(--navy),var(--blue));color:white;text-align:center;padding:65px 20px}
.hero h1{color:white;font-size:38px;margin-bottom:15px}.hero p{line-height:1.7;margin-bottom:20px}
.container{width:94%;max-width:1100px;margin:28px auto}
h1,h2{color:var(--navy);margin-bottom:15px}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:15px;margin:20px 0}
.card,.panel,form{background:white;padding:20px;border-radius:10px;box-shadow:0 3px 12px #0000000d;margin-bottom:15px}
.card h3{color:var(--navy);margin-bottom:10px}.card p,.panel p{line-height:1.6;margin:8px 0}
.amount{font-size:25px;font-weight:bold;color:var(--navy)}
form{max-width:500px;margin:25px auto}
label{display:block;margin-top:12px;font-weight:bold}
input,textarea,select{width:100%;padding:12px;margin:7px 0 12px;border:1px solid #ccd5e4;border-radius:7px;font-size:15px}
textarea{min-height:100px;resize:vertical}
form button{width:100%;margin-top:8px}
.message{margin:12px 0;line-height:1.5;overflow-wrap:anywhere}
.success{color:var(--green)}.error{color:var(--red)}
.notice{background:#fff6dc;border-left:4px solid #e5b43c;padding:13px;margin:15px 0;line-height:1.5}
.small{font-size:13px;color:#68758a;line-height:1.5}
table{width:100%;border-collapse:collapse;margin:12px 0;background:white}
th,td{padding:10px;border:1px solid #dce3ed;text-align:left;font-size:14px}
th{background:#e8effb;color:var(--navy)}
.table-wrap{overflow-x:auto;margin:15px 0}
.section-title{margin-top:28px}
footer{background:var(--navy);color:white;text-align:center;padding:25px;margin-top:40px}
footer p{margin-top:8px}
@media(max-width:650px){header{justify-content:center}nav{justify-content:center}.hero h1{font-size:30px}th,td{font-size:12px;padding:7px}}
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
<div class="card"><h3>01. Discover</h3><p>Explore opportunities published by administrators.</p></div>
<div class="card"><h3>02. Apply</h3><p>Choose an opportunity and submit an application.</p></div>
<div class="card"><h3>03. Complete</h3><p>Submit your work for administrator review.</p></div>
</div>
</div>
</section>

<section id="register" class="page">
<form id="registerForm">
<h2>Create Your Account</h2>
<label>Full Name</label>
<input id="regName" required maxlength="100" autocomplete="name">
<label>Email Address</label>
<input id="regEmail" type="email" required autocomplete="email">
<label>Password</label>
<input id="regPassword" type="password" minlength="6" required autocomplete="new-password">
<button class="primary" id="registerButton">Create Account</button>
<p id="registerMessage" class="message" role="status"></p>
<p>Already registered? <a href="#" onclick="showPage('login');return false">Login</a></p>
</form>
</section>

<section id="login" class="page">
<form id="loginForm">
<h2>Login to GIGGS</h2>
<label>Email Address</label>
<input id="loginEmail" type="email" required autocomplete="email">
<label>Password</label>
<input id="loginPassword" type="password" required autocomplete="current-password">
<button class="primary" id="loginButton">Login</button>
<p id="loginMessage" class="message" role="status"></p>
<p>New to GIGGS? <a href="#" onclick="showPage('register');return false">Create Account</a></p>
</form>
</section>

<section id="dashboard" class="page">
<div class="container">
<h1>User Dashboard</h1>
<p id="welcomeName">Welcome to GIGGS.</p>
<p id="profileLoadMessage" class="message" role="status"></p>
<div class="notice">GIGGS is currently in testing. Displayed rewards are indicative only. Payments and withdrawals are not active.</div>
<div class="cards">
<div class="card"><h3>My Applications</h3><div class="amount" id="myApplicationCount">0</div></div>
<div class="card"><h3>My Submissions</h3><div class="amount" id="mySubmissionCount">0</div></div>
<div class="card"><h3>Account Role</h3><div class="amount" id="myRole">Loading...</div></div>
</div>
<button class="primary" onclick="showPage('tasks')">Explore Gigs</button>
<button class="secondary" onclick="loadMyActivity()">Refresh Activity</button>
<button class="secondary" onclick="showPage('profile')">My Profile</button>
<button class="secondary" onclick="logout()">Logout</button>
<div class="panel section-title"><h2>My Applications</h2><div id="myApplications">Loading...</div></div>
<div class="panel"><h2>My Submissions</h2><div id="mySubmissions">Loading...</div></div>
</div>
</section>

<section id="tasks" class="page">
<div class="container">
<h1>Available Gigs</h1>
<p>Explore opportunities currently marked as open.</p>
<div id="gigList">Loading gigs...</div>
</div>
</section>

<section id="admin" class="page">
<div class="container">
<h1>GIGGS Admin Dashboard</h1>
<p id="adminWelcome">Administrator area</p>
<div class="notice">Admin tools are available only to accounts whose database profile role is admin.</div>
<div class="cards">
<div class="card"><h3>Total Gigs</h3><div class="amount" id="statGigs">0</div></div>
<div class="card"><h3>Applications</h3><div class="amount" id="statApplications">0</div></div>
<div class="card"><h3>Submissions</h3><div class="amount" id="statSubmissions">0</div></div>
</div>
<div class="panel">
<h2 id="gigFormHeading">Create a Gig</h2>
<form id="gigForm">
<input type="hidden" id="gigId">
<label>Gig Title</label><input id="gigTitle" maxlength="150" required>
<label>Description</label><textarea id="gigDescription" maxlength="5000" required></textarea>
<label>Indicative Reward (KSh)</label><input id="gigReward" type="number" min="0" step="0.01" required>
<label>Status</label>
<select id="gigStatus"><option value="open">Open</option><option value="closed">Closed</option></select>
<button class="primary" id="saveGigButton">Save Gig</button>
<button class="secondary" type="button" onclick="resetGigForm()">Clear Form</button>
<p id="gigMessage" class="message" role="status"></p>
</form>
</div>
<div class="panel"><h2>Manage Gigs</h2><div id="adminGigs">Loading...</div></div>
<div class="panel"><h2>Manage Applications</h2><div id="adminApplications">Loading...</div></div>
<div class="panel"><h2>Review Submissions</h2><div id="adminSubmissions">Loading...</div></div>
<button class="secondary" onclick="loadAdminDashboard()">Refresh Dashboard</button>
<button class="secondary" onclick="logout()">Logout</button>
</div>
</section>

<section id="profile" class="page">
<div class="container">
<h1>My Profile</h1>
<div class="card">
<p id="profileName">Name:</p>
<p id="profileEmail">Email:</p>
<p id="profileRole">Role:</p>
</div>
<button class="secondary" onclick="showPage('dashboard')">Back to Dashboard</button>
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

const SUPABASE_URL="https://fvmqjqjojfbeiiltauxm.supabase.co";
const SUPABASE_KEY="sb_publishable_ugLuC8Q3J6-mh5rSqqrD0Q_-GoHc3yS";

let db=null;
let currentUser=null;
let currentProfile=null;

function el(id){return document.getElementById(id)}

function escapeHTML(value){
return String(value??"").replace(/[&<>"']/g,c=>({
"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"
}[c]));
}

function message(id,text,type=""){
el(id).className="message "+type;
el(id).textContent=text;
}

function showPage(id){
const privatePages=["dashboard","admin","profile"];
if(privatePages.includes(id)&&!currentUser){id="login"}
if(id==="admin"&&currentProfile?.role!=="admin"){
alert("Administrator access only.");
id="dashboard";
}
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
el(id).classList.add("active");
window.scrollTo(0,0);
}

async function loadProfile(){
if(!currentUser)throw new Error("No authenticated user.");
const {data,error}=await db.from("profiles")
.select("id,full_name,email,role")
.eq("id",currentUser.id).maybeSingle();

if(error)throw error;
if(!data)throw new Error("Your profile was not found. Contact the administrator.");
currentProfile=data;
return data;
}

function updateAccountDisplay(){
if(!currentUser||!currentProfile)return;
const name=currentProfile.full_name||currentUser.email||"GIGGS User";
el("welcomeName").textContent="Welcome, "+name;
el("profileName").textContent="Name: "+name;
el("profileEmail").textContent="Email: "+(currentUser.email||"");
el("profileRole").textContent="Role: "+currentProfile.role;
el("myRole").textContent=currentProfile.role;
el("adminWelcome").textContent="Welcome, "+name;
}

async function refreshUserState(){
if(!currentUser)return;
try{
message("profileLoadMessage","Loading your account...");
await loadProfile();
updateAccountDisplay();
message("profileLoadMessage","Profile loaded successfully.","success");
if(el("dashboard").classList.contains("active"))await loadMyActivity();
if(el("tasks").classList.contains("active"))await loadGigs();
}catch(err){
console.error("Profile loading error:",err);
currentProfile=null;
el("myRole").textContent="Unavailable";
message("profileLoadMessage","Could not load your profile: "+err.message,"error");
}
}

async function loadGigs(){
el("gigList").textContent="Loading gigs...";
const {data,error}=await db.from("gigs")
.select("id,title,description,reward,status")
.eq("status","open").order("title");
if(error){el("gigList").textContent="Could not load gigs: "+error.message;return}
if(!data.length){el("gigList").textContent="There are no open gigs at the moment.";return}
el("gigList").innerHTML=data.map(g=>`
<div class="card">
<h3>${escapeHTML(g.title)}</h3>
<p>${escapeHTML(g.description)}</p>
<p><strong>Indicative reward:</strong> KSh ${Number(g.reward||0).toFixed(2)}</p>
<button class="primary" onclick="applyForGig('${g.id}')">Apply</button>
</div>`).join("");
}

async function applyForGig(gigId){
if(!currentUser){showPage("login");return}
const {error}=await db.from("applications").insert({
gig_id:gigId,user_id:currentUser.id,status:"pending"
});
if(error){
alert(error.code==="23505"?"You have already applied for this gig.":"Application failed: "+error.message);
return;
}
alert("Application submitted successfully.");
await loadMyActivity();
}

async function loadMyActivity(){
if(!currentUser)return;
const [appsResult,subsResult]=await Promise.all([
db.from("applications").select("id,gig_id,status,created_at")
.eq("user_id",currentUser.id).order("created_at",{ascending:false}),
db.from("submissions").select("id,application_id,submission_text,status,created_at")
.order("created_at",{ascending:false})
]);
if(appsResult.error){el("myApplications").textContent=appsResult.error.message;return}
if(subsResult.error){el("mySubmissions").textContent=subsResult.error.message;return}
const apps=appsResult.data||[];
const subs=(subsResult.data||[]).filter(s=>apps.some(a=>a.id===s.application_id));
el("myApplicationCount").textContent=apps.length;
el("mySubmissionCount").textContent=subs.length;
const gigsResult=await db.from("gigs").select("id,title");
const gigMap=Object.fromEntries((gigsResult.data||[]).map(g=>[g.id,g.title]));

el("myApplications").innerHTML=apps.length?apps.map(a=>`
<div class="card">
<h3>${escapeHTML(gigMap[a.gig_id]||"Gig")}</h3>
<p>Status: <strong>${escapeHTML(a.status)}</strong></p>
${a.status==="approved"?`
<label for="submission-${a.id}">Submit your work</label>
<textarea id="submission-${a.id}" maxlength="10000" placeholder="Describe your completed work"></textarea>
<button class="primary" onclick="submitWork('${a.id}')">Submit Work</button>`:""}
</div>`).join(""):"You have not applied for any gigs yet.";

el("mySubmissions").innerHTML=subs.length?subs.map(s=>`
<div class="card">
<p>${escapeHTML(s.submission_text)}</p>
<p>Status: <strong>${escapeHTML(s.status)}</strong></p>
</div>`).join(""):"You have no submissions yet.";
}

async function submitWork(applicationId){
const input=el("submission-"+applicationId);
const content=input.value.trim();
if(!content){alert("Please enter your work before submitting.");return}
const {error}=await db.from("submissions").insert({
application_id:applicationId,submission_text:content,status:"pending"
});
if(error){alert("Submission failed: "+error.message);return}
alert("Your work has been submitted for review.");
await loadMyActivity();
}

async function loadAdminDashboard(){
if(currentProfile?.role!=="admin"){
alert("Administrator access only.");
showPage("dashboard");return;
}
const [gigsR,appsR,subsR,profilesR]=await Promise.all([
db.from("gigs").select("*").order("title"),
db.from("applications").select("*").order("created_at",{ascending:false}),
db.from("submissions").select("*").order("created_at",{ascending:false}),
db.from("profiles").select("id,full_name,email")
]);
for(const r of [gigsR,appsR,subsR,profilesR]){
if(r.error){alert("Could not load admin data: "+r.error.message);return}
}
const gigs=gigsR.data||[];
const apps=appsR.data||[];
const subs=subsR.data||[];
const profiles=profilesR.data||[];
const gigMap=Object.fromEntries(gigs.map(g=>[g.id,g]));
const profileMap=Object.fromEntries(profiles.map(p=>[p.id,p]));

el("statGigs").textContent=gigs.length;
el("statApplications").textContent=apps.length;
el("statSubmissions").textContent=subs.length;

el("adminGigs").innerHTML=gigs.length?gigs.map(g=>`
<div class="card">
<h3>${escapeHTML(g.title)}</h3>
<p>${escapeHTML(g.description)}</p>
<p>Indicative reward: KSh ${Number(g.reward||0).toFixed(2)}</p>
<p>Status: ${escapeHTML(g.status)}</p>
<button class="secondary" onclick="editGig('${g.id}')">Edit</button>
<button class="danger" onclick="deleteGig('${g.id}')">Delete</button>
</div>`).join(""):"No gigs have been created.";

el("adminApplications").innerHTML=apps.length?apps.map(a=>{
const p=profileMap[a.user_id]||{};
const g=gigMap[a.gig_id]||{};
return `<div class="card">
<h3>${escapeHTML(g.title||"Gig")}</h3>
<p>Applicant: ${escapeHTML(p.full_name||"Unknown")}</p>
<p>Email: ${escapeHTML(p.email||"")}</p>
<p>Status: <strong>${escapeHTML(a.status)}</strong></p>
<button class="primary" onclick="updateApplication('${a.id}','approved')">Approve</button>
<button class="danger" onclick="updateApplication('${a.id}','rejected')">Reject</button>
</div>`;
}).join(""):"No applications yet.";

el("adminSubmissions").innerHTML=subs.length?subs.map(s=>{
const app=apps.find(a=>a.id===s.application_id)||{};
const p=profileMap[app.user_id]||{};
const g=gigMap[app.gig_id]||{};
return `<div class="card">
<h3>${escapeHTML(g.title||"Gig submission")}</h3>
<p>Submitted by: ${escapeHTML(p.full_name||"Unknown")}</p>
<p>${escapeHTML(s.submission_text)}</p>
<p>Status: <strong>${escapeHTML(s.status)}</strong></p>
<button class="primary" onclick="updateSubmission('${s.id}','approved')">Approve</button>
<button class="danger" onclick="updateSubmission('${s.id}','rejected')">Reject</button>
</div>`;
}).join(""):"No submissions to review.";
}

async function updateApplication(id,status){
const {error}=await db.from("applications").update({status}).eq("id",id);
if(error){alert("Could not update application: "+error.message);return}
await loadAdminDashboard();
}

async function updateSubmission(id,status){
const {error}=await db.from("submissions").update({status}).eq("id",id);
if(error){alert("Could not update submission: "+error.message);return}
await loadAdminDashboard();
}

function resetGigForm(){
el("gigForm").reset();
el("gigId").value="";
el("gigFormHeading").textContent="Create a Gig";
el("saveGigButton").textContent="Save Gig";
message("gigMessage","");
}

async function editGig(id){
const {data,error}=await db.from("gigs").select("*").eq("id",id).single();
if(error){alert(error.message);return}
el("gigId").value=data.id;
el("gigTitle").value=data.title;
el("gigDescription").value=data.description;
el("gigReward").value=data.reward;
el("gigStatus").value=data.status;
el("gigFormHeading").textContent="Edit Gig";
el("saveGigButton").textContent="Update Gig";
window.scrollTo(0,0);
}

async function deleteGig(id){
if(!confirm("Delete this gig? Existing applications may prevent deletion."))return;
const {error}=await db.from("gigs").delete().eq("id",id);
if(error){alert("Could not delete gig: "+error.message);return}
alert("Gig deleted.");
await loadAdminDashboard();
}

el("gigForm").addEventListener("submit",async function(e){
e.preventDefault();
if(currentProfile?.role!=="admin"){message("gigMessage","Administrator access only.","error");return}
const id=el("gigId").value;
const gig={
title:el("gigTitle").value.trim(),
description:el("gigDescription").value.trim(),
reward:Number(el("gigReward").value),
status:el("gigStatus").value
};
if(!gig.title||!gig.description||!Number.isFinite(gig.reward)||gig.reward<0){
message("gigMessage","Please enter valid gig details.","error");return;
}
el("saveGigButton").disabled=true;
const result=id
?await db.from("gigs").update(gig).eq("id",id)
:await db.from("gigs").insert(gig);
el("saveGigButton").disabled=false;
if(result.error){message("gigMessage","Could not save gig: "+result.error.message,"error");return}
message("gigMessage",id?"Gig updated successfully.":"Gig created successfully.","success");
resetGigForm();
await loadAdminDashboard();
});

el("registerForm").addEventListener("submit",async function(e){
e.preventDefault();
if(!db){message("registerMessage","Connection is not ready.","error");return}
const name=el("regName").value.trim();
const email=el("regEmail").value.trim();
const password=el("regPassword").value;
el("registerButton").disabled=true;
message("registerMessage","Creating your account...");
try{
const {data,error}=await db.auth.signUp({
email,password,
options:{
data:{full_name:name},
emailRedirectTo:"https://kijanayabills-sys.github.io/giggs/"
}
});
if(error)throw error;
if(data.session){
currentUser=data.session.user;
await refreshUserState();
if(currentProfile){
showPage("dashboard");
}else{
message("registerMessage","Account created, but your profile could not be loaded. Please contact the administrator.","error");
}
}else{
message("registerMessage","Account created. Check your email to confirm your address, then log in.","success");
}
}catch(err){
message("registerMessage",err.message,"error");
}finally{
el("registerButton").disabled=false;
}
});

el("lo

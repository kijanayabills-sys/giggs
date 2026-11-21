
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GIGGS | Discover. Work. Earn.</title>
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{box-sizing:border-box;margin:0;padding:0;font-family:Arial,sans-serif}
body{background:#f4f7fc;color:#172b4d}
header{background:#102a56;color:white;padding:17px 5%;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
nav{display:flex;gap:15px;flex-wrap:wrap}
nav a{color:white;text-decoration:none;cursor:pointer;font-size:14px}
.hero{background:linear-gradient(120deg,#102a56,#2563eb);color:white;text-align:center;padding:55px 15px}
.hero h1{font-size:36px;margin-bottom:12px}
.container{width:92%;max-width:1000px;margin:28px auto}
.panel{background:white;padding:23px;border-radius:12px;box-shadow:0 3px 14px #0000000d;margin-bottom:22px}
h2,h3{margin-bottom:14px}
input,textarea,select{width:100%;padding:12px;margin:8px 0 14px;border:1px solid #ccd5e2;border-radius:7px;font-size:15px}
textarea{min-height:90px;resize:vertical}
button{background:#2563eb;color:white;border:0;padding:11px 16px;border-radius:7px;cursor:pointer;margin:4px 3px 4px 0}
button:hover{background:#1749b1}
button:disabled{opacity:.6;cursor:not-allowed}
.danger{background:#c62828}
.dark{background:#102a56}
.secondary{background:#64748b}
.hidden{display:none!important}
.message{font-size:14px;margin-top:12px;line-height:1.5;overflow-wrap:anywhere}
.success{color:#087443}
.error{color:#c62828}
.muted{color:#64748b;font-size:14px;line-height:1.5}
.item{border:1px solid #e0e6ef;padding:16px;border-radius:9px;margin:13px 0}
.item p{margin:8px 0;line-height:1.5}
.tag{display:inline-block;background:#e8efff;color:#1749b1;padding:5px 9px;border-radius:5px;font-size:12px;margin:5px 0}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}
footer{background:#102a56;color:white;text-align:center;padding:24px;margin-top:40px}
hr{border:0;border-top:1px solid #e5eaf1;margin:18px 0}
</style>
</head>

<body>

<header>
<h2>GIGGS</h2>
<nav>
<a href="#home">Home</a>
<a href="#gigs" onclick="showPage('gigs')">Explore Gigs</a>
<a href="#login" id="loginLink" onclick="showPage('login')">Login</a>
<a href="#register" id="joinLink" onclick="showPage('register')">Join Now</a>
<a href="#account" id="accountLink" class="hidden" onclick="showPage('account')">My Account</a>
<a href="#admin" id="adminLink" class="hidden" onclick="showPage('admin')">Admin Dashboard</a>
<a href="#" id="logoutLink" class="hidden" onclick="logout()">Logout</a>
</nav>
</header>

<section class="hero" id="home">
<h1>Discover. Work. Earn.</h1>
<p>Discover opportunities and build your skills with GIGGS.</p>
<br>
<button onclick="showPage('register')">Get Started</button>
<button class="dark" onclick="showPage('gigs')">Explore Gigs</button>
</section>

<main class="container">

<section id="register" class="panel hidden">
<h2>Create Your Account</h2>
<form id="registerForm">
<label>Full Name</label>
<input id="fullName" required>
<label>Email Address</label>
<input id="regEmail" type="email" required>
<label>Password</label>
<input id="regPassword" type="password" minlength="8" required>
<button id="registerButton" type="submit">Create Account</button>
</form>
<p id="registerMessage" class="message"></p>
</section>

<section id="login" class="panel hidden">
<h2>Login to GIGGS</h2>
<form id="loginForm">
<label>Email Address</label>
<input id="loginEmail" type="email" required>
<label>Password</label>
<input id="loginPassword" type="password" required>
<button id="loginButton" type="submit">Login</button>
</form>
<p id="loginMessage" class="message"></p>
</section>

<section id="account" class="panel hidden">
<h2>My Account</h2>
<p id="accountName"></p>
<p id="accountEmail" class="muted"></p>
<p id="accountRole" class="tag"></p>
<hr>
<button onclick="showPage('gigs')">Explore Gigs</button>
</section>

<section id="gigs" class="panel">
<h2>Available Gigs</h2>
<p class="muted">Browse opportunities published by GIGGS administrators.</p>
<div id="publicGigs">Loading gigs...</div>
</section>

<section id="admin" class="hidden">

<div class="panel">
<h2>GIGGS Administrator Dashboard</h2>
<p id="adminWelcome" class="muted">Administrator area</p>
<p class="tag">Administrator access</p>
<p id="adminMessage" class="message"></p>
</div>

<div class="panel">
<h3>Post a New Gig</h3>
<form id="gigForm">
<input type="hidden" id="gigId">
<label>Gig Title</label>
<input id="gigTitle" placeholder="Enter gig title" required>
<label>Description</label>
<textarea id="gigDescription" placeholder="Describe the gig" required></textarea>
<label>Reward amount (KSh)</label>
<input id="gigReward" type="number" min="0" step="0.01" required>
<button id="saveGigButton" type="submit">Publish Gig</button>
<button type="button" class="secondary" onclick="resetGigForm()">Clear Form</button>
</form>
<p id="gigMessage" class="message"></p>
</div>

<div class="panel">
<h3>Manage Gigs</h3>
<div id="adminGigs">Loading...</div>
</div>

<div class="panel">
<h3>Registered Users</h3>
<div id="adminUsers">Loading...</div>
</div>

<div class="panel">
<h3>Gig Applications</h3>
<div id="adminApplications">Loading...</div>
</div>

<div class="panel">
<h3>Task Submissions</h3>
<div id="adminSubmissions">Loading...</div>
</div>

</section>

<section class="panel">
<h2>About GIGGS</h2>
<p>GIGGS connects users with opportunities to discover gigs, develop skills and complete tasks. Only authorized administrators can post gigs.</p>
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

const db = window.supabase.createClient(SUPABASE_URL, SUPABASE_KEY);

let currentUser = null;
let currentProfile = null;

function message(id,text,type="") {
  const el=document.getElementById(id);
  if(el){el.textContent=text;el.className="message "+type;}
}

function showPage(id) {
  ["register","login","account","admin"].forEach(page=>{
    document.getElementById(page).classList.add("hidden");
  });

  if(["register","login","account","admin"].includes(id)){
    document.getElementById(id).classList.remove("hidden");
  }

  if(id==="gigs"){
    document.getElementById("gigs").scrollIntoView({behavior:"smooth"});
  } else {
    window.scrollTo({top:0,behavior:"smooth"});
  }

  if(id==="admin" && currentProfile?.role==="admin"){
    loadAdminDashboard();
  }
}

function updateNavigation() {
  const loggedIn=!!currentUser;
  const isAdmin=currentProfile?.role==="admin";

  document.getElementById("loginLink").classList.toggle("hidden",loggedIn);
  document.getElementById("joinLink").classList.toggle("hidden",loggedIn);
  document.getElementById("accountLink").classList.toggle("hidden",!loggedIn);
  document.getElementById("logoutLink").classList.toggle("hidden",!loggedIn);
  document.getElementById("adminLink").classList.toggle("hidden",!isAdmin);

  if(loggedIn){
    document.getElementById("accountName").textContent=
      "Name: "+(currentProfile?.full_name||"GIGGS User");
    document.getElementById("accountEmail").textContent=
      "Email: "+currentUser.email;
    document.getElementById("accountRole").textContent=
      "Account role: "+(currentProfile?.role||"user");
  }
}

async function loadProfile() {
  if(!currentUser){
    currentProfile=null;
    updateNavigation();
    return;
  }

  const {data,error}=await db
    .from("profiles")
    .select("id,full_name,email,role")
    .eq("id",currentUser.id)
    .single();

  if(error){
    console.error("Profile loading error:",error.message);
    currentProfile=null;
  }else{
    currentProfile=data;
  }

  updateNavigation();
}

document.getElementById("registerForm").addEventListener("submit",async e=>{
  e.preventDefault();

  const button=document.getElementById("registerButton");
  button.disabled=true;
  button.textContent="Creating account...";

  try{
    const {data,error}=await db.auth.signUp({
      email:document.getElementById("regEmail").value.trim(),
      password:document.getElementById("regPassword").value,
      options:{
        data:{
          full_name:document.getElementById("fullName").value.trim()
        },
        emailRedirectTo:"https://kijanayabills-sys.github.io/giggs/"
      }
    });

    if(error) throw error;

    message("registerMessage",
      data.session
      ?"Registration successful."
      :"Registration submitted. Check your email to confirm your account.",
      "success"
    );

    document.getElementById("registerForm").reset();

  }catch(error){
    message("registerMessage",error.message,"error");
  }finally{
    button.disabled=false;
    button.textContent="Create Account";
  }
});

document.getElementById("loginForm").addEventListener("submit",async e=>{
  e.preventDefault();

  const button=document.getElementById("loginButton");
  button.disabled=true;
  button.textContent="Logging in...";

  try{
    const {data,error}=await db.auth.signInWithPassword({
      email:document.getElementById("loginEmail").value.trim(),
      password:document.getElementById("loginPassword").value
    });

    if(error) throw error;

    currentUser=data.user;
    await loadProfile();

    document.getElementById("loginForm").reset();

    if(currentProfile?.role==="admin"){
      showPage("admin");
    }else{
      showPage("account");
    }

  }catch(error){
    message("loginMessage",error.message,"error");
  }finally{
    button.disabled=false;
    button.textContent="Login";
  }
});

async function logout(){
  const {error}=await db.auth.signOut();

  if(error){
    alert(error.message);
    return;
  }

  currentUser=null;
  currentProfile=null;
  updateNavigation();
  showPage("login");
  message("loginMessage","You have logged out.","success");
}

async function loadPublicGigs(){
  const container=document.getElementById("publicGigs");

  const {data,error}=await db
    .from("gigs")
    .select("*")
    .eq("status","open")
    .order("created_at",{ascending:false});

  if(error){
    container.textContent="Unable to load gigs: "+error.message;
    return;
  }

  if(!data.length){
    container.textContent="No open gigs are currently available.";
    return;
  }

  container.innerHTML="";

  data.forEach(gig=>{
    const item=document.createElement("div");
    item.className="item";

    const title=document.createElement("h3");
    title.textContent=gig.title;

    const description=document.createElement("p");
    description.textContent=gig.description;

    const reward=document.createElement("p");
    reward.textContent="Reward: KSh "+Number(gig.reward).toLocaleString();

    const button=document.createElement("button");
    button.textContent="Apply for Gig";
    button.onclick=()=>applyForGig(gig.id);

    item.append(title,description,reward,button);
    container.appendChild(item);
  });
}

async function applyForGig(gigId){
  if(!currentUser){
    alert("Please log in before applying.");
    showPage("login");
    return;
  }

  const {error}=await db.from("applications").insert({
    gig_id:gigId,
    user_id:currentUser.id
  });

  if(error){
    alert(error.message);
  }else{
    alert("Your application has been submitted.");
  }
}

function resetGigForm(){
  document.getElementById("gigForm").reset();
  document.getElementById("gigId").value="";
  document.getElementById("saveGigButton").textContent="Publish Gig";
}

document.getElementById("gigForm").addEventListener("submit",async e=>{
  e.preventDefault();

  if(currentProfile?.role!=="admin"){
    message("gigMessage","Administrator access required.","error");
    return;
  }

  const button=document.getElementById("saveGigButton");
  button.disabled=true;

  const id=document.getElementById("gigId").value;
  const gig={
    title:document.getElementById("gigTitle").value.trim(),
    description:document.getElementById("gigDescription").value.trim(),
    reward:Number(document.getElementById("gigReward").value),
    status:"open"
  };

  try{
    let result;

    if(id){
      result=await db.from("gigs").update(gig).eq("id",id);
    }else{
      gig.created_by=currentUser.id;
      result=await db.from("gigs").insert(gig);
    }

    if(result.error) throw result.error;

    message("gigMessage",id?"Gig updated successfully.":"Gig published successfully.","success");
    resetGigForm();
    await loadAdminDashboard();
    await loadPublicGigs();

  }catch(error){
    message("gigMessage",error.message,"error");
  }finally{
    button.disabled=false;
  }
});

async function editGig(id){
  const {data,error}=await db.from("gigs").select("*").eq("id",id).single();

  if(error){
    alert(error.message);
    return;
  }

  document.getElementById("gigId").value=data.id;
  document.getElementById("gigTitle").value=data.title;
  document.getElementById("gigDescription").value=data.description;
  document.getElementById("gigReward").value=data.reward;
  document.getElementById("saveGigButton").textContent="Save Changes";

  document.getElementById("gigForm").scrollIntoView({behavior:"smooth"});
}

async function closeGig(id){
  if(!confirm("Close this gig?")) return;

  const {error}=await db.from("gigs")
    .update({status:"closed"}).eq("id",id);

  if(error) alert(error.message);
  else{
    await loadAdminDashboard();
    await loadPublicGigs();
  }
}

async function deleteGig(id){
  if(!confirm("Delete this gig and its related applications?")) return;

  const {error}=await db.from("gigs").delete().eq("id",id);

  if(error) alert(error.message);
  else{
    await loadAdminDashboard();
    await loadPublicGigs();
  }
}

async function loadAdminDashboard(){
  if(currentProfile?.role!=="admin"){
    showPage("account");
    return;
  }

  document.getElementById("adminWelcome").textContent=
    "Signed in as administrator: "+currentUser.email;

  await Promise.all([
    loadAdminGigs(),
    loadAdminUsers(),
    loadAdminApplications(),
    loadAdminSubmissions()
  ]);
}

async function loadAdminGigs(){
  const box=document.getElementById("adminGigs");
  const {data,error}=await db.from("gigs")
    .select("*").order("created_at",{ascending:false});

  if(error){box.textContent=error.message;return;}
  if(!data.length){box.textContent="No gigs posted yet.";return;}

  box.innerHTML="";

  data.forEach(gig=>{
    const item=document.createElement("div");
    item.className="item";

    const title=document.createElement("h3");
    title.textContent=gig.title;

    const description=document.createElement("p");
    description.textContent=gig.description;

    const details=document.createElement("p");
    details.textContent="KSh "+gig.reward+" | Status: "+gig.status;

    const edit=document.createElement("button");
    edit.textContent="Edit";
    edit.onclick=()=>editGig(gig.id);

    const close=document.createElement("button");
    close.textContent="Close Gig";
    close.className="secondary";
    close.disabled=gig.status==="closed";
    close.onclick=()=>closeGig(gig.id);

    const remove=document.createElement("button");
    remove.textContent="Delete";
    remove.className="danger";
    remove.onclick=()=>deleteGig(gig.id);

    item.append(title,description,details,edit,close,remove);
    box.appendChild(item);
  });
}

async function loadAdminUsers(){
  const box=document.getElementById("adminUsers");
  const {data,error}=await db.from("profiles")
    .select("id,full_name,email,role,created_at")
    .order("created_at",{ascending:false});

  if(error){box.textContent=error.message;return;}
  if(!data.length){box.textContent="No profiles found.";return;}

  box.innerHTML="";

  data.forEach(user=>{
    const item=document.createElement("div");
    item.className="item";

    const name=document.createElement("p");
    name.textContent="Name: "+(user.full_name||"Not provided");

    const email=document.createElement("p");
    email.textContent="Email: "+user.email;

    const role=document.createElement("p");
    role.textContent="Role: "+user.role;

    item.append(name,email,role);
    box.appendChild(item);
  });
}

async function loadAdminApplications(){
  const box=document.getElementById("adminApplications");

  const {data,error}=await db.from("applications")
    .select("id,gig_id,user_id,status,created_at")
    .order("created_at",{ascending:false});

  if(error){box.textContent=error.message;return;}
  if(!data.length){box.textContent="No applications yet.";return;}

  box.innerHTML="";

  for(const app of data){
    const [gigResult,userResult]=await Promise.all([
      db.from("gigs").select("title").eq("id",app.gig_id).maybeSingle(),
      db.from("profiles").select("full_name,email").eq("id",app.user_id).maybeSingle()
    ]);

    const item=document.createElement("div");
    item.className="item";

    const heading=document.createElement("h3");
    heading.textContent=gigResult.data?.title||"Gig";

    const applicant=document.createElement("p");
    applicant.textContent="Applicant: "+(userResult.data?.full_name||userResult.data?.email||app.user_id);

    const status=document.createElement("p");
    status.textContent="Status: "+app.status;

    item.append(heading,applicant,status);

    if(app.status==="pending"){
      const approve=document.createElement("button");
      approve.textContent="Approve";
      approve.onclick=()=>updateApplication(app.id,"approved");

      const reject=document.createElement("button");
      reject.textContent="Reject";
      reject.className="danger";
      reject.onclick=()=>updateApplication(app.id,"rejected");

      item.append(approve,reject);
    }

    box.appendChild(item);
  }
}

async function updateApplication(id,status){
  const {error}=await db.from("applications")
    .update({status}).eq("id",id);

  if(error) alert(error.message);
  else await loadAdminApplications();
}

async function loadAdminSubmissions(){
  const box=document.getElementById("adminSubmissions");

  const {data,error}=await db.from("submissions")
    .select("*").order("created_at",{ascending:false});

  if(error){box.textContent=error.message;return;}
  if(!data.length){box.textContent="No task submissions yet.";return;}

  box.innerHTML="";

  for(const submission of data){
    const item=document.createElement("div");
    item.className="item";

    const appResult=await db.from("applications")
      .select("user_id,gig_id")
      .eq("id",submission.application_id)
      .maybeSingle();

    const userResult=appResult.data
      ? await db.from("profiles").select("full_name,email")
          .eq("id",appResult.data.user_id).maybeSingle()
      : {data:null};

    const title=document.createElement("h3");
    title.textContent="Task Submission";

    const content=document.createElement("p");
    content.textContent=submission.submission_text||"No submission text provided.";

    const applicant=document.createElement("p");
    applicant.textContent="User: "+(userResult.data?.full_name||userResult.data?.email||"Unknown");

    const status=document.createElement("p");
    status.textContent="Status: "+submission.status;

    item.append(title,content,applicant,status);

    if(submission.status==="pending"){
      const approve=document.createElement("button");
      approve.textContent="Approve";
      approve.onclick=()=>updateSubmission(submission.id,"approved");

      const reject=document.createElement("button");
      reject.textContent="Reject";
      reject.className="danger";
      reject.onclick=()=>updateSubmission(submission.id,"rejected");

      item.append(approve,reject);
    }

    box.appendChild(item);
  }
}

async function updateSubmission(id,status){
  const {error}=await db.from("submissions")
    .update({status}).eq("id",id);

  if(error) alert(error.message);
  else await loadAdminSubmis

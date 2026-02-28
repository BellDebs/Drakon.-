# Papi
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Drakon System</title>

<style>

body{
margin:0;
background:black;
color:#00ffcc;
font-family:monospace;
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
text-align:center;
}

/* glowing card */
.panel{
width:90%;
max-width:650px;
padding:30px;
border:1px solid #00ffcc;
box-shadow:0 0 25px #00ffcc;
background:rgba(0,0,0,0.85);
border-radius:12px;
}

.hidden{display:none;}

h1{
letter-spacing:3px;
}

button{
padding:12px 20px;
background:#00ffcc;
border:none;
color:black;
font-weight:bold;
margin-top:20px;
cursor:pointer;
border-radius:6px;
}

input{
padding:12px;
width:80%;
font-size:18px;
text-align:center;
border:none;
border-radius:6px;
}

#text{
white-space:pre-line;
line-height:1.8;
}

.stat{
color:#ffd700;
font-size:18px;
margin-top:8px;
}

</style>
</head>

<body>

<audio id="music" loop>
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8a73467.mp3?filename=calm-background-ambient-110624.mp3">
</audio>

<!-- BOOT -->
<div id="boot" class="panel">
<h1 id="bootText"></h1>
</div>

<!-- PASSWORD -->
<div id="login" class="panel hidden">
<h2>HOST IDENTIFIED</h2>

<p id="names"></p>

<p>Enter Access Key</p>
<input id="pass">
<br>
<button onclick="unlock()">ACCESS</button>

<p id="error"></p>
</div>

<!-- GREETING -->
<div id="greet" class="panel hidden">
<div id="text"></div>
<button onclick="showReward()">ACCEPT SYSTEM REWARD</button>
</div>

<!-- REWARD -->
<div id="reward" class="panel hidden">
<h2>===== SYSTEM STATUS =====</h2>

<p>Name: Drakon</p>
<p>Race: Human</p>

<div id="stats"></div>

<h3 style="margin-top:20px;">System Blessing Installed ✔</h3>
<p>I hope you like it.</p>

</div>

<script>

/* ---------------- BOOT ---------------- */

const bootMsg=
"SYSTEM INITIALIZING...\n"+
"REBOOTING CORE...\n"+
"LOADING LIFE PARAMETERS...\n"+
"HOST SEARCHING...\n"+
"CONNECTION ESTABLISHED...\n";

let i=0;
function boot(){
if(i<bootMsg.length){
document.getElementById("bootText").innerHTML+=bootMsg.charAt(i);
i++;
setTimeout(boot,30);
}else{
setTimeout(()=>{
document.getElementById("boot").classList.add("hidden");
document.getElementById("login").classList.remove("hidden");
showNames();
},1000);
}
}
boot();

/* ---------------- NAMES ---------------- */

const nameText=
"Emmanuel\nSunbola\nPraise";

let n=0;
function showNames(){
if(n<nameText.length){
document.getElementById("names").innerHTML+=nameText.charAt(n);
n++;
setTimeout(showNames,60);
}
}

/* ---------------- PASSWORD ---------------- */

function unlock(){
let pass=document.getElementById("pass").value.trim().toLowerCase();

if(pass==="drakon"){

let music=document.getElementById("music");
music.volume=0;
music.play();

/* fade music */
let vol=0;
let fade=setInterval(()=>{
if(vol<1){
vol+=0.05;
music.volume=vol;
}else clearInterval(fade);
},200);

document.getElementById("login").classList.add("hidden");
document.getElementById("greet").classList.remove("hidden");

typeGreeting();

}else{
document.getElementById("error").innerText=
"ACCESS DENIED";
}
}

/* ---------------- GREETING ---------------- */

const greetMsg=`Today marks more than a birthday.

It marks growth.
Resilience.
Dreams refusing to fade.

Emmanuel.
Sunbola.
Praise.

May your life be filled with joy,
success,
peace,
and unstoppable happiness.

May inspiration follow your path.
May motivation never abandon you.
May your career rise beyond expectations.

In the nearest future,
you shall live the life you truly desire.

Keep rising.

Happy Birthday, Drakon.`;

let g=0;
function typeGreeting(){
if(g<greetMsg.length){
document.getElementById("text")
.innerHTML+=greetMsg.charAt(g);
g++;
setTimeout(typeGreeting,25);
}
}

/* ---------------- REWARD ---------------- */

function showReward(){

document.getElementById("greet").classList.add("hidden");
document.getElementById("reward").classList.remove("hidden");

const stats=[
"Wealth +100",
"Health +100",
"Happiness +100"
];

let s=0;

function loadStats(){
if(s<stats.length){
let div=document.createElement("div");
div.className="stat";
div.innerText=stats[s];
document.getElementById("stats").appendChild(div);
s++;
setTimeout(loadStats,700);
}
}

loadStats();
}

</script>

</body>
</html>

<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Mint Exclusive Toggle UI</title>

<style>
body{
  margin:0;
  background:#0f0f12;
  font-family:Arial, sans-serif;
  color:#eaeaea;
}

/* BUTTON STYLE */
.btn{
  width:26px;
  height:26px;

  border:1px solid #2ef2c2;
  border-radius:6px;
  background:transparent;

  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  gap:2px;

  cursor:pointer;

  box-shadow:0 0 6px #2ef2c2, 0 0 12px rgba(46,242,194,0.5);
  transition:0.2s ease;
  z-index:1000;
}

.btn span{
  width:12px;
  height:2px;
  background:#2ef2c2;
  border-radius:2px;
  box-shadow:0 0 4px #2ef2c2;
}

.btn:hover{
  transform:scale(1.05);
}

/* POSITIONS */
.left{ position:fixed; top:10px; left:10px; }
.center{ position:fixed; top:10px; left:50%; transform:translateX(-50%); }
.right{ position:fixed; top:10px; right:10px; }

/* PANEL */
.panel{
  position:fixed;
  top:45px;

  width:320px;

  background:rgba(15,15,18,0.97);
  border-radius:10px;

  padding:0 10px;

  max-height:0;
  overflow:hidden;

  transition:0.25s ease;
  box-shadow:0 0 14px rgba(0,0,0,0.4);

  z-index:999;
}

.panel.open{
  max-height:1200px;
  padding:10px;
}

.leftP{ left:10px; }
.centerP{ left:50%; transform:translateX(-50%); }
.rightP{ right:10px; }

/* TEXT */
.title{
  color:#2ef2c2;
  font-weight:bold;
  font-size:13px;
  margin-bottom:8px;
}

.text{
  font-size:12px;
  line-height:1.4;
  margin:6px 0;
}

.section-title{
  font-size:12px;
  font-weight:bold;
  margin-top:10px;
}

/* ROW */
.row{
  display:flex;
  align-items:center;
  gap:6px;
  margin:5px 0;
}

/* BOXES */
.win, .loss{
  width:14px;
  height:14px;
  border-radius:3px;

  display:flex;
  align-items:center;
  justify-content:center;

  font-size:10px;
  font-weight:bold;
  color:#111;
}

.win{
  background:#2ef2c2;
  box-shadow:0 0 5px rgba(46,242,194,0.5);
}

.loss{
  background:#ff3b3b;
  box-shadow:0 0 5px rgba(255,59,59,0.5);
}
</style>
</head>

<body>

<!-- BUTTONS -->
<div class="btn left" onclick="toggle('left')">
  <span></span><span></span><span></span>
</div>

<div class="btn center" onclick="toggle('center')">
  <span></span><span></span><span></span>
</div>

<div class="btn right" onclick="toggle('right')">
  <span></span><span></span><span></span>
</div>

<!-- LEFT PANEL -->
<div id="left" class="panel leftP">
  <div class="title">🔁 Patronen herkennen</div>

  <div class="text">
    De app volgt voorspellingsreeksen om herhaalbare structuren te detecteren.
  </div>

  <div class="section-title">VOORBEELD VAN EEN PATROON</div>

  <div class="row"><div class="loss">L</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="loss">L</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>

  <div class="text">
    Na elk verlies volgen drie opeenvolgende winsten. Instappen na resetmomenten.
  </div>
</div>

<!-- CENTER PANEL -->
<div id="center" class="panel centerP">
  <div class="title">🔥 Sterke patroonherkenning</div>

  <div class="text">
    Zoek naar reeksen met lage verliesfrequentie tussen winsten.
  </div>

  <div class="section-title">HETE REEKS</div>

  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="loss">L</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>

  <div class="text">
    Sterk momentum bij consistente winststructuren.
  </div>
</div>

<!-- RIGHT PANEL -->
<div id="right" class="panel rightP">
  <div class="title">📉 Patroonverzwakking herkennen</div>

  <div class="text">
    Wanneer winstreeksen korter worden of verliezen toenemen.
  </div>

  <div class="section-title">VERZWAKKERING</div>

  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="loss">L</div></div>
  <div class="row"><div class="win">W</div></div>
  <div class="row"><div class="loss">L</div></div>

  <div class="text">
    Reeks verliest structuur → wachten op reset.
  </div>
</div>

<script>
function toggle(id){
  const panels = ["left","center","right"];

  panels.forEach(p=>{
    if(p !== id){
      document.getElementById(p).classList.remove("open");
    }
  });

  document.getElementById(id).classList.toggle("open");
}
</script>

</body>
</html>

<p style="color: Yellow;">🇮🇩🇺🇸RT🇸🇷🇳🇱</p>

<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Week Schema</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background:#050505;
    font-family:Arial,sans-serif;
    padding:8px;
    color:white;
}

/* CONTAINER */

.container{
    width:100%;
    max-width:420px;
    margin:auto;
    background:#101010;
    border-radius:16px;
    padding:12px;

    box-shadow:
        0 0 15px #00ffae55,
        0 0 30px #00ffae22;
}

/* TITLE */

.title{
    text-align:center;
    font-size:20px;
    margin-bottom:10px;
    color:white;

    text-shadow:
        0 0 5px #fff,
        0 0 10px #00ffae,
        0 0 20px #00ffae;
}

/* GRID */

.header,
.row{
    display:grid;
    grid-template-columns:
        45px
        1fr
        1fr
        1fr;

    gap:5px;
    align-items:center;
}

.header{
    margin-bottom:6px;
    font-size:11px;
    font-weight:bold;
    text-align:center;

    color:white;

    text-shadow:
        0 0 6px #00ffae;
}

.row{
    margin-bottom:6px;
}

/* BOX */

.box{
    width:100%;
    border:none;
    border-radius:8px;
    padding:8px 4px;

    background:#1a1a1a;
    color:white;

    text-align:center;
    font-size:11px;

    outline:none;

    text-shadow:
        0 0 5px #00ffae;

    box-shadow:
        0 0 6px #00ffae33,
        0 0 12px #00ffae11;
}

.day{
    font-weight:bold;
}

.result{
    background:#0d0d0d;
    font-weight:bold;
}

/* NETTO */

.nettoBox{
    margin-top:10px;
    padding:10px;

    border-radius:12px;
    background:#0d0d0d;

    text-align:center;

    box-shadow:
        0 0 10px #00ffae55,
        0 0 20px #00ffae22;
}

.nettoTitle{
    font-size:12px;
    margin-bottom:4px;

    text-shadow:
        0 0 6px #00ffae;
}

.nettoValue{
    font-size:22px;
    font-weight:bold;

    text-shadow:
        0 0 5px #fff,
        0 0 15px #00ffae;
}

/* BUTTONS */

.buttons{
    display:flex;
    gap:6px;
    margin-top:10px;
}

button{
    flex:1;

    border:none;
    border-radius:10px;

    padding:10px;

    font-size:12px;
    font-weight:bold;

    cursor:pointer;

    transition:0.2s;
}

/* SAVE */

.saveBtn{
    background:#00ffae;
    color:white;

    text-shadow:
        0 0 6px #000;

    box-shadow:
        0 0 10px #00ffae88,
        0 0 20px #00ffae33;
}

/* RESET */

.resetBtn{
    background:#bfffe9;
    color:white;

    text-shadow:
        0 0 6px #000;

    box-shadow:
        0 0 10px #bfffe988,
        0 0 20px #bfffe933;
}

button:hover{
    transform:scale(1.02);
}

/* PLACEHOLDER */

input::placeholder{
    color:#888;
}

</style>

<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Glow Informatie</title>

<style>
body {
    background-color: #0a0a0a;
    color: white;
    font-family: Arial, sans-serif;
    padding: 40px;
}

/* Glowing titel */
h1 {
    text-align: center;
    font-size: 50px;
    color: #ffffff;
    text-shadow:
        0 0 5px #00ffff,
        0 0 10px #00ffff,
        0 0 20px #00ffff,
        0 0 40px #00ffff;
}

/* Glowing tekst blok */
.info {
    max-width: 700px;
    margin: auto;
    font-size: 18px;
    line-height: 1.6;
    padding: 20px;
    border: 1px solid #00ffff;
    border-radius: 10px;
    box-shadow:
        0 0 10px #00ffff,
        0 0 20px #00ffff;
}

/* Knop met glow */
button {
    display: block;
    margin: 30px auto;
    padding: 12px 25px;
    font-size: 16px;
    color: white;
    background: black;
    border: 1px solid #ff00ff;
    cursor: pointer;
    box-shadow:
        0 0 10px #ff00ff,
        0 0 20px #ff00ff;
    transition: 0.3s;
}

button:hover {
    box-shadow:
        0 0 20px #ff00ff,
        0 0 40px #ff00ff;
}
</style>

</head>
<body>

</body>
</html>

<html lang="nl">
<head>
<meta charset="UTF-8">
<title>GRS TOOL</title>

<style>
body {
  font-family: Arial;
  text-align: center;
  background: #050505;
  color: white;
}

/* STATIC glow casino background */
body::before {
  content: "";
  position: fixed;
  inset: 0;
  background:
    radial-gradient(circle at 20% 25%, rgba(0,255,200,0.15), transparent 40%),
    radial-gradient(circle at 80% 20%, rgba(255,215,0,0.12), transparent 40%),
    radial-gradient(circle at 40% 70%, rgba(0,150,255,0.10), transparent 45%),
    radial-gradient(circle at 70% 60%, rgba(255,0,150,0.08), transparent 45%);
  pointer-events: none;
}

/* title */
h2 {
  margin-top: 20px;
  text-shadow: 0 0 10px #00f2ff;
}

.grid {
  display: grid;
  grid-template-columns: repeat(6, 60px);
  gap: 10px;
  justify-content: center;
  margin-top: 20px;
}

.cell {
  width: 60px;
  height: 60px;
  background: #111;
  border: 1px solid #00f2ff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  font-weight: bold;
  user-select: none;
  box-shadow: 0 0 8px #00f2ff;
  color: white;
}

.cell:hover {
  box-shadow: 0 0 15px #00ffcc;
}

#output {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
  padding: 10px;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  background: #111;
  border-radius: 10px;
  box-shadow: 0 0 12px #00f2ff;
}

button {
  margin-top: 10px;
  padding: 8px 12px;
  border: none;
  cursor: pointer;
  font-weight: bold;
  background: #00f2ff;
  border-radius: 6px;
}

button:hover {
  box-shadow: 0 0 15px #8a2be2;
}
</style>
</head>

<body>



<div id="output">Choose the following number</div>

<div class="grid" id="grid"></div>

<script>
const grid = document.getElementById("grid");
const output = document.getElementById("output");

let data = JSON.parse(localStorage.getItem("outcomes")) || {};

function save() {
  localStorage.setItem("outcomes", JSON.stringify(data));
}

for (let i = 0; i <= 36; i++) {
  const cell = document.createElement("div");
  cell.className = "cell";
  cell.textContent = i;

  // klik = tonen
  cell.addEventListener("click", () => {
    if (!data[i]) {
      output.textContent = "Nummer " + i + " heeft nog geen uitkomst ingesteld.";
    } else {
      output.textContent = "🎯 Nummer " + i + " → " + data[i];
    }
  });

  // dubbelklik = instellen
  cell.addEventListener("dblclick", () => {
    let nieuw = prompt("Geef jouw uitkomst voor nummer " + i + ":", data[i] || "");
    if (nieuw && nieuw.trim() !== "") {
      data[i] = nieuw;
      save();
      output.textContent = "✔ Uitkomst opgeslagen voor nummer " + i;
    }
  });

  grid.appendChild(cell);
}

function resetAll() {
  if (confirm("Alles resetten?")) {
    localStorage.removeItem("outcomes");
    location.reload();
  }
}
</script>

</body>
</html>

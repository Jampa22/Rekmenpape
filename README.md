<style>
/* FIXED GUIDE */
#miniGuideShort{
    position:fixed;
    top:6px;
    left:6px;
    z-index:999999999;
    font-family:Arial,sans-serif;
}

/* BUTTON */
#miniGuideShortBtn{
    width:24px;
    height:24px;

    border:none;
    border-radius:7px;

    background:
        linear-gradient(145deg,#050505,#111);

    color:#baffea;
    font-size:11px;
    cursor:pointer;

    display:flex;
    align-items:center;
    justify-content:center;

    box-shadow:
        0 0 8px #9fffe3,
        0 0 18px rgba(159,255,227,.35),
        inset 0 0 5px rgba(255,255,255,.05);

    transition:.15s ease;
}

#miniGuideShortBtn:hover{
    transform:scale(1.05);

    box-shadow:
        0 0 12px #baffea,
        0 0 24px rgba(159,255,227,.55);
}

/* POPUP */
#miniGuideShortBox{
    position:absolute;
    top:32px;
    left:0;

    width:205px;
    padding:9px;

    border-radius:12px;

    background:
        linear-gradient(
            180deg,
            rgba(10,10,10,.98),
            rgba(5,5,5,.99)
        );

    border:1px solid rgba(186,255,234,.14);

    display:none;

    color:#fff;

    box-shadow:
        0 0 20px rgba(159,255,227,.18),
        inset 0 0 10px rgba(255,255,255,.03);
}

/* ITEM */
.shortItem{
    margin-bottom:7px;
    padding:6px 7px;

    border-radius:8px;

    background:rgba(255,255,255,.02);

    color:#d8d8d8;
    font-size:10px;
    line-height:1.35;
}

.shortItem:last-child{
    margin-bottom:0;
}

/* TITLE */
.shortTitle{
    color:#baffea;
    font-weight:bold;
    margin-bottom:2px;
    font-size:10px;
}
</style>

<!-- GUIDE -->
<div id="miniGuideShort">

    <!-- BUTTON -->
    <button id="miniGuideShortBtn">☰</button>

    <!-- POPUP -->
    <div id="miniGuideShortBox">

        <div class="shortItem">
            <div class="shortTitle">🎯 Predictions</div>
            Predicts next trends.
        </div>

        <div class="shortItem">
            <div class="shortTitle">📈 Patterns</div>
            Detects repeating behavior.
        </div>

        <div class="shortItem">
            <div class="shortTitle">📊 Data</div>
            Uses live table statistics.
        </div>

        <div class="shortItem">
            <div class="shortTitle">📉 Exit signals</div>
            Stop on repeated loss pattern.
        </div>

        <div class="shortItem">
            <div class="shortTitle">⭐️ Optimize</div>
            Improves calculation stability.
        </div>

        <div class="shortItem">
            <div class="shortTitle">🔥 Hot tables</div>
            Shows strong active tables.
        </div>

    </div>

</div>

<script>
const miniGuideShortBtn =
document.getElementById("miniGuideShortBtn");

const miniGuideShortBox =
document.getElementById("miniGuideShortBox");

miniGuideShortBtn.onclick = () => {

    miniGuideShortBox.style.display =
        miniGuideShortBox.style.display === "block"
        ? "none"
        : "block";

};
</script>

<style>
/* FIXED RIGHT GUIDE */
#rightMiniGuide{
    position:fixed;
    top:6px;
    right:6px;
    z-index:999999999;
    font-family:Arial,sans-serif;
}

/* MINI BUTTON */
#rightMiniGuideBtn{
    width:24px;
    height:24px;

    border:none;
    border-radius:7px;

    background:
        linear-gradient(145deg,#050505,#111);

    color:#baffea;
    font-size:11px;
    cursor:pointer;

    display:flex;
    align-items:center;
    justify-content:center;

    box-shadow:
        0 0 8px #9fffe3,
        0 0 18px rgba(159,255,227,.35),
        inset 0 0 5px rgba(255,255,255,.05);

    transition:.15s ease;
}

#rightMiniGuideBtn:hover{
    transform:scale(1.05);

    box-shadow:
        0 0 12px #baffea,
        0 0 24px rgba(159,255,227,.55);
}

/* POPUP */
#rightMiniGuideBox{
    position:absolute;
    top:32px;
    right:0;

    width:240px;
    padding:10px;

    border-radius:12px;

    background:
        linear-gradient(
            180deg,
            rgba(10,10,10,.98),
            rgba(5,5,5,.99)
        );

    border:1px solid rgba(186,255,234,.14);

    display:none;

    color:#fff;

    box-shadow:
        0 0 20px rgba(159,255,227,.18),
        inset 0 0 10px rgba(255,255,255,.03);
}

/* TITLE */
.rightGuideTitle{
    color:#baffea;
    font-size:10px;
    font-weight:bold;
    margin-bottom:7px;
    text-transform:uppercase;
    letter-spacing:.5px;
}

/* TEXT */
.rightGuideText{
    color:#d8d8d8;
    font-size:10px;
    line-height:1.45;
}
</style>

<!-- RIGHT GUIDE -->
<div id="rightMiniGuide">

    <!-- BUTTON -->
    <button id="rightMiniGuideBtn">☰</button>

    <!-- POPUP -->
    <div id="rightMiniGuideBox">

        <div class="rightGuideTitle">
            Exit Signal Info
        </div>

        <div class="rightGuideText">
            If the table previously changed calculation type after a certain
            number of confirmed spins (causing a loss), stop when that same
            count is reached again.
        </div>

    </div>

</div>

<script>
const rightMiniGuideBtn =
document.getElementById("rightMiniGuideBtn");

const rightMiniGuideBox =
document.getElementById("rightMiniGuideBox");

rightMiniGuideBtn.onclick = () => {

    rightMiniGuideBox.style.display =
        rightMiniGuideBox.style.display === "block"
        ? "none"
        : "block";

};
</script>

<span style="color: green;">
The Most Powerfull Prediction Tool
</span>

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
</head>
<body>

<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mint Glow Ultra Compact</title>

<style>
body{
    margin:0;
    background:#000;
    font-family:Arial,sans-serif;
}

/* ===== FIXED GUIDE BUTTON ===== */
#guideUI{
    position:fixed;
    top:6px;
    left:50%;
    transform:translateX(-50%);
    z-index:999999;
}

#guideBtn{
    width:26px;
    height:26px;
    border:none;
    border-radius:7px;

    background:#050505;
    color:#baffea;
    cursor:pointer;

    display:flex;
    align-items:center;
    justify-content:center;

    box-shadow:0 0 10px #7fffd4;
    font-size:12px;
}

/* PANEL */
#panel{
    position:absolute;
    top:34px;
    left:50%;
    transform:translateX(-50%);

    width:230px;
    padding:8px;

    background:#050505;
    border:1px solid rgba(127,255,212,.25);
    border-radius:10px;

    display:none;

    box-shadow:0 0 18px rgba(127,255,212,.25);
    color:#fff;
}

/* WEEK CHECKLIST */
.week{
    display:flex;
    flex-direction:column;
    gap:3px;
    margin-bottom:8px;
}

.day{
    display:flex;
    align-items:center;
    justify-content:space-between;

    padding:3px;
    border-radius:6px;

    background:rgba(255,255,255,0.03);
    box-shadow:0 0 6px rgba(127,255,212,.12);
}

.day span{
    width:24px;
    font-size:8px;
    color:#baffea;
}

/* CHECKBOX */
.day input[type="checkbox"]{
    transform:scale(0.8);
    accent-color:#7fffd4;
}

/* INPUTS */
.row{
    display:flex;
    gap:6px;
}

.box{
    flex:1;
}

.label{
    font-size:9px;
    color:#baffea;
    margin-bottom:3px;
}

.box input{
    width:100%;
    padding:6px;

    border:none;
    border-radius:6px;

    background:#0b0b0b;
    color:#fff;
    font-size:10px;
    text-align:center;

    box-shadow:0 0 8px rgba(127,255,212,.2);
}

/* NETTO */
#netto{
    margin-top:8px;
    padding:6px;

    text-align:center;
    border-radius:6px;

    background:rgba(255,255,255,0.03);
    color:#baffea;

    font-size:10px;
    font-weight:bold;

    box-shadow:0 0 10px rgba(127,255,212,.2);
}

/* BUTTONS */
.buttons{
    display:flex;
    gap:6px;
    margin-top:8px;
}

/* GREEN SAVE */
.saveBtn{
    flex:1;
    padding:6px;
    border:none;
    border-radius:6px;

    background:#0f3;
    color:#fff;

    font-size:9px;
    cursor:pointer;
}

/* MINT RESET */
.resetBtn{
    flex:1;
    padding:6px;
    border:none;
    border-radius:6px;

    background:#111;
    color:#baffea;

    font-size:9px;
    cursor:pointer;

    box-shadow:0 0 10px rgba(127,255,212,.15);
}

.resetBtn:hover{
    box-shadow:0 0 14px rgba(127,255,212,.3);
}
</style>
</head>

<body>

<!-- GUIDE -->
<div id="guideUI">

    <button id="guideBtn">☰</button>

    <div id="panel">

        <!-- WEEK -->
        <div class="week">
            <div class="day"><span>Ma</span><input type="checkbox"></div>
            <div class="day"><span>Di</span><input type="checkbox"></div>
            <div class="day"><span>Wo</span><input type="checkbox"></div>
            <div class="day"><span>Do</span><input type="checkbox"></div>
            <div class="day"><span>Vr</span><input type="checkbox"></div>
            <div class="day"><span>Za</span><input type="checkbox"></div>
            <div class="day"><span>Zo</span><input type="checkbox"></div>
        </div>

        <!-- INPUTS -->
        <div class="row">
            <div class="box">
                <div class="label">Inzet</div>
                <input id="bet" type="number" oninput="calc()">
            </div>

            <div class="box">
                <div class="label">Winst</div>
                <input id="win" type="number" oninput="calc()">
            </div>
        </div>

        <!-- NETTO -->
        <div id="netto">Netto: €0</div>

        <!-- BUTTONS -->
        <div class="buttons">
            <button class="saveBtn" onclick="save()">Opslaan</button>
            <button class="resetBtn" onclick="reset()">Opnieuw</button>
        </div>

    </div>

</div>

<script>

/* TOGGLE */
const btn = document.getElementById("guideBtn");
const panel = document.getElementById("panel");

btn.onclick = () => {
    panel.style.display =
        panel.style.display === "block"
        ? "none"
        : "block";
};

/* CALC */
function calc(){
    let w = parseFloat(document.getElementById("win").value)||0;
    let b = parseFloat(document.getElementById("bet").value)||0;

    document.getElementById("netto").innerText =
        "Netto: €" + (w - b).toFixed(2);
}

/* SAVE */
function save(){
    localStorage.setItem("mintUltraV8", JSON.stringify({
        bet: document.getElementById("bet").value,
        win: document.getElementById("win").value
    }));
}

/* LOAD */
window.onload = () => {
    let d = JSON.parse(localStorage.getItem("mintUltraV8"));
    if(!d) return;

    document.getElementById("bet").value = d.bet;
    document.getElementById("win").value = d.win;
    calc();
};

/* RESET */
function reset(){
    localStorage.removeItem("mintUltraV8");
    location.reload();
}

</script>

</body>
</html>

</body>
</html>

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



<div id="output">Choose following number</div>

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

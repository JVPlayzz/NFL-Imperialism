<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NFL Imperialism</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #0f172a;
  color: white;
  text-align: center;
}

h1 {
  margin-top: 30px;
  font-size: 36px;
}

button {
  width: 85%;
  max-width: 320px;
  padding: 18px;
  margin: 12px auto;
  font-size: 20px;
  border: none;
  border-radius: 14px;
  cursor: pointer;
  background: #38bdf8;
  display: block;
}

button:hover {
  background: #0ea5e9;
}

.page {
  display: none;
}

.active {
  display: block;
}

.spinner {
  margin: 25px auto;
  padding: 25px;
  background: #1e293b;
  width: 85%;
  max-width: 320px;
  border-radius: 16px;
}

.spinner img {
  width: 160px;
}

footer {
  margin-top: 60px;
  opacity: 0.7;
  font-size: 14px;
}
</style>
</head>

<body>

<!-- HOME -->
<div id="home" class="page active">
  <h1>NFL Imperialism</h1>
  <button onclick="goTo('nfl')">Wheel of NFL</button>
  <button onclick="goTo('arrow')">Arrow</button>
  <footer>made by JV</footer>
</div>

<!-- NFL WHEEL -->
<div id="nfl" class="page">
  <h1>Wheel of NFL</h1>
  <div class="spinner" id="teamResult">
    Tap spin to get a team
  </div>
  <button onclick="spinTeam()">SPIN</button>
  <button onclick="goTo('arrow')">NEXT →</button>
</div>

<!-- ARROW -->
<div id="arrow" class="page">
  <h1>Arrow</h1>
  <div class="spinner" id="directionResult">
    Tap spin to get direction
  </div>
  <button onclick="spinDirection()">SPIN</button>
  <button onclick="goTo('finish')">FINISH</button>
</div>

<!-- FINAL -->
<div id="finish" class="page">
  <h1>Final Result</h1>
  <div class="spinner">
    <div id="finalTeam"></div>
    <p id="finalDirection" style="font-size:24px;"></p>
  </div>
  <button onclick="goTo('home')">BACK HOME</button>
</div>

<script>
const teams = [
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/ari.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/atl.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/bal.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/buf.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/car.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/chi.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/cin.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/cle.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/dal.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/den.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/det.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/gb.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/hou.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/ind.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/jax.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/kc.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/lv.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/lac.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/lar.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/mia.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/min.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/ne.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/no.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/nyg.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/nyj.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/phi.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/pit.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/sf.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/sea.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/tb.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/ten.png" },
  { logo:"https://a.espncdn.com/i/teamlogos/nfl/500/wsh.png" }
];

const directions = ["⬆️ North","⬇️ South","➡️ East","⬅️ West","↗️ NE","↖️ NW","↘️ SE","↙️ SW"];

let selectedTeam = null;
let selectedDirection = "";

function goTo(page) {
  document.querySelectorAll(".page").forEach(p => p.classList.remove("active"));
  document.getElementById(page).classList.add("active");
}

function spinTeam() {
  selectedTeam = teams[Math.floor(Math.random() * teams.length)];
  document.getElementById("teamResult").innerHTML =
    `<img src="${selectedTeam.logo}">`;
}

function spinDirection() {
  selectedDirection = directions[Math.floor(Math.random() * directions.length)];
  document.getElementById("directionResult").innerText = selectedDirection;
  document.getElementById("finalTeam").innerHTML =
    `<img src="${selectedTeam.logo}">`;
  document.getElementById("finalDirection").innerText = selectedDirection;
}
</script>

</body>
</html>

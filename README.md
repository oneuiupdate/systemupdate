<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>System Integrity</title>

<style>
body{
  margin:0;
  background:black;
  color:white;
  font-family:monospace;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  overflow:hidden;
  flex-direction:column;
}

#hiddenText{
  opacity:0;
  transition:opacity 2s;
  text-align:center;
}

.red{
  color:red;
}

@keyframes flash{
  0%{background:black;}
  50%{background:red;}
  100%{background:black;}
}

.flash{
  animation:flash 0.2s 6;
}

@keyframes glitch{
  0%{transform:translate(0);}
  20%{transform:translate(-4px,4px);}
  40%{transform:translate(4px,-4px);}
  60%{transform:translate(-4px,-4px);}
  80%{transform:translate(4px,4px);}
  100%{transform:translate(0);}
}

.glitch{
  animation:glitch 0.15s infinite;
}
</style>
</head>

<body onclick="document.documentElement.requestFullscreen()">

<div id="hiddenText">
<h2>Scanning system...</h2>
</div>

<audio id="beep">
<source src="https://actions.google.com/sounds/v1/alarms/beep_short.ogg">
</audio>

<script>
let text = document.getElementById("hiddenText");
let beep = document.getElementById("beep");

// 3 sekonda ekran i zi
setTimeout(()=>{
  text.style.opacity = "1";
},3000);

// Pas 6 sekondash fillon tensioni
setTimeout(()=>{
  text.innerHTML = "<h2 class='red'>Unauthorized access detected...</h2>";
  beep.play();
},6000);

// Pas 9 sekondash red flash + glitch
setTimeout(()=>{
  document.body.classList.add("flash");
  document.body.innerHTML = `
  <h1 class="red glitch">⚠ SYSTEM BREACH ⚠</h1>
  <h2 class="red glitch">Device compromised.</h2>
  `;
  beep.play();
},9000);

// Pas 14 sekondash zbulohet prank
setTimeout(()=>{
  document.body.classList.remove("flash");
  document.body.innerHTML = `
  <h1 style="color:white;">Relax 😈</h1>
  <h2 style="color:white;">It’s just a prank 😂</h2>
  `;
},14000);

</script>

</body>
</html>

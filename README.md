<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>System Integrity Check</title>

<style>
body{
  margin:0;
  background:black;
  color:#00ff00;
  font-family:monospace;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  overflow:hidden;
  flex-direction:column;
}

#screen{
  text-align:center;
}

.red{
  color:red;
}

@keyframes glitch{
  0%{transform:translate(0);}
  20%{transform:translate(-5px,5px);}
  40%{transform:translate(5px,-5px);}
  60%{transform:translate(-5px,-5px);}
  80%{transform:translate(5px,5px);}
  100%{transform:translate(0);}
}

.glitch{
  animation:glitch 0.2s infinite;
}
</style>
</head>

<body onclick="document.documentElement.requestFullscreen()">

<div id="screen">
<h2>Running security scan...</h2>
<div id="log"></div>
</div>

<script>
let log = document.getElementById("log");

let lines = [
"Connecting to system core...",
"Scanning memory blocks...",
"Unauthorized access detected...",
"Bypassing firewall...",
"Extracting private data...",
"Encrypting storage..."
];

let i = 0;

let interval = setInterval(()=>{
  if(i < lines.length){
    log.innerHTML += lines[i] + "<br>";
    i++;
  } else {
    clearInterval(interval);
    setTimeout(()=>{
      document.body.innerHTML = `
      <h1 class="red glitch">⚠ SYSTEM BREACH ⚠</h1>
      <h2 class="red glitch">Device compromised.</h2>
      `;
      setTimeout(()=>{
        document.body.innerHTML = `
        <h1 style="color:white;">Relax 😈</h1>
        <h2 style="color:white;">It’s just a prank 😂</h2>
        `;
      },3000);
    },1000);
  }
},700);
</script>

</body>
</html>

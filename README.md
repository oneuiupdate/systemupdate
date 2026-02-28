<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>System Update</title>

<style>
body{
  margin:0;
  background:#0c1b2e;
  color:white;
  font-family:Arial, sans-serif;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  flex-direction:column;
}

h1{
  font-weight:500;
  margin-bottom:30px;
}

#progress{
  width:80%;
  height:8px;
  background:#1f3554;
  border-radius:4px;
  overflow:hidden;
}

#bar{
  height:100%;
  width:0%;
  background:#4da6ff;
  transition:width 0.3s;
}

#percent{
  margin-top:15px;
  font-size:18px;
}
</style>
</head>

<body onclick="document.documentElement.requestFullscreen()">

<h1>Installing System Update</h1>

<div id="progress">
  <div id="bar"></div>
</div>

<div id="percent">0%</div>

<script>
let percent = 0;
let bar = document.getElementById("bar");
let percentText = document.getElementById("percent");

let interval = setInterval(()=>{
  percent += Math.floor(Math.random()*6)+3;
  if(percent > 100) percent = 100;

  bar.style.width = percent + "%";
  percentText.innerText = percent + "%";

  if(percent === 100){
    clearInterval(interval);
    setTimeout(()=>{
      document.body.innerHTML = `
      <h1 style="color:red;">⚠ SYSTEM FAILURE ⚠</h1>
      <h2 style="color:red;">Update corrupted.</h2>
      <h3>Just kidding 😂</h3>
      `;
    },1000);
  }

},400);
</script>

</body>
</html>

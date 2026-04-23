<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Living God Music Pro</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Poppins',sans-serif;background:linear-gradient(135deg,#020617,#0f172a);color:#fff;}
header{padding:20px;text-align:center;font-size:26px;font-weight:600;background:rgba(0,0,0,0.4);backdrop-filter:blur(10px);border-bottom:1px solid rgba(255,255,255,0.1);}
.container{display:flex;height:100vh;}
.sidebar{width:30%;padding:15px;overflow-y:auto;border-right:1px solid rgba(255,255,255,0.1);}
.content{width:70%;padding:25px;display:flex;flex-direction:column;gap:15px;}
.song{padding:12px;margin-bottom:10px;border-radius:10px;background:rgba(255,255,255,0.05);cursor:pointer;transition:0.3s;}
.song:hover{background:rgba(255,255,255,0.1);transform:scale(1.02);}
.song.active{background:#38bdf8;color:#000;font-weight:600;}
iframe{width:100%;height:350px;border:none;border-radius:12px;box-shadow:0 0 20px rgba(0,0,0,0.5);}
.controls{display:flex;gap:10px;margin-top:10px;}
button{padding:10px 14px;border:none;border-radius:8px;cursor:pointer;font-weight:500;background:#38bdf8;color:#000;}
button:hover{background:#0ea5e9;color:#fff;}
.title{font-size:20px;font-weight:500;}
.footer{text-align:center;font-size:12px;opacity:0.7;margin-top:auto;}
</style>
</head>

<body>

<header>🎵 Living God Music Pro</header>

<div class="container">
  <div class="sidebar" id="list"></div>

  <div class="content">
    <div class="title" id="title">Select a song</div>

    <iframe id="player"></iframe>

    <div class="controls">
      <button onclick="prevSong()">⏮ Prev</button>
      <button onclick="nextSong()">⏭ Next</button>
    </div>

    <div class="footer">© Living God Music | Worship & Faith</div>
  </div>
</div>

<script>
const songs=[
{title:"At The Cross I Am Found",id:"rzwQsdnFLXA"},
{title:"Thank You Lord",id:"_jdcTk6Ja6I"},
{title:"You Heal Me",id:"pZ6myLUja_o"},
{title:"Jesus Is My Strength",id:"NhcB0GEZJZ0"},
{title:"Jesus Is My Strength Vol.2",id:"3tMV-GBaNn4"},
{title:"Jesus, Make Me Whole",id:"rOwbReZrYkk"},
{title:"God of Mercy",id:"Lt6YKq0uYf0"},
{title:"Come On and Praise the Lord",id:"Am8h1P27eMk"},
{title:"Spirit & Truth Worship",id:"YDNeCboAalw"},  // ✅ comma added
{title:"When the Devil Speaks",id:"wsxcxuGGhGw"}
];

let current=0;
const list=document.getElementById("list");
const player=document.getElementById("player");
const title=document.getElementById("title");

function render(){
list.innerHTML="";
songs.forEach((s,i)=>{
const div=document.createElement("div");
div.className="song"+(i===current?" active":"");
div.innerText=s.title;
div.onclick=()=>play(i);
list.appendChild(div);
});
}

function play(i){
current=i;
const s=songs[i];
title.innerText=s.title;
player.src=`https://www.youtube.com/embed/${s.id}?autoplay=1`;
render();
}

function nextSong(){
current=(current+1)%songs.length;
play(current);
}

function prevSong(){
current=(current-1+songs.length)%songs.length;
play(current);
}

render();
</script>

</body>
</html>

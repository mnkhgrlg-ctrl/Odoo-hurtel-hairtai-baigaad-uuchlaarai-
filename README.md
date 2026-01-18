# hairtai bld 3 jil boljee
<!Mnkhgrl ees html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You ❤️</title>
<style>
*{box-sizing:border-box;}
body{
  margin:0;
  height:100vh;
  overflow:hidden;
  font-family:-apple-system,BlinkMacSystemFont,sans-serif;
  background:radial-gradient(circle at top,#1a0033,#000);
  color:white;
}

/* ===== BACKGROUND STARS ===== */
.star{
  position:fixed;
  width:2px;
  height:2px;
  background:white;
  border-radius:50%;
  animation:twinkle linear infinite;
}
@keyframes twinkle{50%{opacity:.2}}

/* ===== CENTERED LAYOUT ===== */
.center{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
  z-index:1;
}

/* ===== LOCK (PASSWORD) ===== */
#lock{
  display:flex;
  flex-direction:column;
  gap:14px;
  align-items:center;
  animation:fadeIn 1s;
  z-index:2;
}
.hint{font-size:14px;color:#ff9ecf;opacity:.9;}
#lock input{
  padding:12px;font-size:20px;border:none;border-radius:10px;outline:none;
  text-align:center;background:#00000080;color:white;letter-spacing:3px;width:180px;
}
#lock button{
  padding:10px 26px;border:none;border-radius:12px;font-size:16px;
  cursor:pointer;background:linear-gradient(45deg,#ff0055,#ff5cab);
  color:white;box-shadow:0 0 20px #ff3b7f;transition:.3s;
}
#lock button:hover{transform:scale(1.05);}

/* ===== RECTANGLE BOX ===== */
#gift{
  display:none;
  width:250px;
  height:170px;
  background:#c8002d;
  border-radius:14px;
  position:relative;
  cursor:pointer;
  box-shadow:0 25px 70px rgba(255,0,80,.7);
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  z-index:2;
}
#giftText{
  color:#ffd1ea;
  font-size:26px;
  font-weight:900;
  text-shadow:0 0 20px hotpink;
  text-align:center;
}

/* ===== MAIN MESSAGE ===== */
#mainMsg{
  display:none;
  font-size:38px;
  font-weight:900;
  color:#ffd1ea;
  text-shadow:0 0 40px hotpink;
  margin-bottom:20px;
  z-index:2;
}

/* ===== LOVE WORD SCROLL ===== */
#loveBox{
  display:none;
  position:fixed;
  left:50%;
  bottom:10px;
  transform:translateX(-50%);
  height:auto;width:90vw;
  max-width:900px;
  overflow:hidden;
  font-size:22px;font-weight:700;
  color:#ffd1ea;text-shadow:0 0 20px pink;
  z-index:2;
}
.scroll{
  display:inline-block;
  white-space:nowrap;
  animation:scrollLeft 32s linear infinite;
}
@keyframes scrollLeft{
  0%{transform:translateX(100%);}
  100%{transform:translateX(-100%);}
}

/* ===== FIREWORK ===== */
.boom{
  position:fixed;font-size:40px;pointer-events:none;
  animation:blast 4s ease-out forwards;
}
@keyframes blast{
  to{transform:translate(calc(-500px + 1000px * var(--x)), calc(-500px + 1000px * var(--y))) scale(.3); opacity:0;}
}

/* ===== MOBILE ===== */
@media(max-width:600px){
  #mainMsg{font-size:30px}
  #loveBox{font-size:18px}
  #gift{width:190px;height:130px}
  #giftText{font-size:22px}
}
</style>
</head>
<body>

<div class="center">

<!-- PASSWORD -->
<div id="lock" class="glass">
  <div style="font-size:22px">🔐 Нууц үг оруул</div>
  <div class="hint">Hint: Tiim ❤️</div>
  <input id="code" placeholder="Энд бич">
  <button onclick="unlock()">Нээх 💖</button>
</div>

<!-- RECTANGLE GIFT BOX -->
<div id="gift">
  <div id="giftText">💗 Надтай үерхээч 💗</div>
</div>

<!-- MAIN MESSAGE -->
<div id="mainMsg">💖 Би чамд хайртай! 💖</div>

<!-- LOVE WORD SCROLL -->
<div id="loveBox">
  <div class="scroll" id="loveText"></div>
</div>

</div>

<script>

/* ===== STARS (BACKGROUND) ===== */
for(let i=0;i<150;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  s.style.animationDuration=2+Math.random()*4+"s";
  document.body.appendChild(s);
}

/* ===== PASSWORD CHECK ===== */
function unlock(){
  if(code.value==="Tiim"){
    lock.style.display="none";
    gift.style.display="flex"; 
  } else {
    navigator.vibrate?.(200);
    alert("💔 Буруу нууц үг");
  }
}

/* ===== GIFT CLICK ===== */
let opened=false;
gift.onclick = ()=>{
  if(opened) return;
  opened=true;

  // FIREWORK BIG
  for(let i=0;i<60;i++){ explode("❤️"); explode("✨"); }

  // SHOW MAIN MESSAGE
  setTimeout(()=>{ mainMsg.style.display="block"; },500);

  // SHOW SCROLL TEXT
  setTimeout(()=>{ loveBox.style.display="block"; },1500);

  setTimeout(()=>{ gift.style.display="none"; },800);
}

/* ===== FIREWORK ===== */
function explode(t){
  const e=document.createElement("div");
  e.className="boom";
  e.innerHTML=t;
  e.style.left=innerWidth/2+"px";
  e.style.top=innerHeight/2+"px";
  e.style.setProperty("--x",Math.random());
  e.style.setProperty("--y",Math.random());
  document.body.appendChild(e);
  setTimeout(()=>e.remove(),4000);
}

/* ===== INTERNATIONAL “I LOVE YOU” SCROLL ===== */
const words=[
 "I love you ❤️","Je t'aime 💖","Te amo 💕","Ich liebe dich 💘",
 "Te quiero 😘","愛してる 💞","사랑해 💗","Я тебя люблю 💝",
 "Ik hou van jou 💖","Eu te amo 💕","Mahal kita 💖","Jeg elsker dig 💗",
 "Te dua 💘","Te iubesc 💞","Szeretlek 💖","Ana 'oho 💞",
 "Я тебя люблю 💗","Te amo 💘","Ik hou van jou 💗"
];

let textHTML="";
for(let i=0;i<words.length;i++){
  textHTML+=words[i]+"   ";
}
loveText.innerHTML=textHTML;

</script>

</body>
</html>

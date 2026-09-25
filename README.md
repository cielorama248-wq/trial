# rams
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Love You</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Great+Vibes&display=swap" rel="stylesheet">
<style>
:root{color-scheme:dark;}
*{box-sizing:border-box;}
html,body{height:100%;margin:0;background:#000;overflow:hidden;
  padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);}
body{font-family:'Press Start 2P','Courier New',monospace;position:relative;}

/* ---------- scene 1: dialog ---------- */
#dialogScreen{
  position:absolute;inset:0;display:flex;align-items:center;justify-content:center;
  background:radial-gradient(ellipse at 50% 40%,#170014 0%,#000 70%);z-index:10;transition:opacity .6s ease;
}
.scan{position:absolute;inset:0;pointer-events:none;
  background:repeating-linear-gradient(0deg,rgba(255,255,255,0.035) 0px,rgba(255,255,255,0.035) 1px,transparent 2px,transparent 3px);
  mix-blend-mode:overlay;}
.box{
  position:relative;width:min(88vw,340px);background:#0a0508;
  border:3px solid #ff5fae;box-shadow:0 0 0 3px #000,0 0 24px 4px rgba(255,60,150,.55);
  animation:borderPulse 2.4s ease-in-out infinite;
}
@keyframes borderPulse{0%,100%{box-shadow:0 0 0 3px #000,0 0 18px 2px rgba(255,60,150,.4);}50%{box-shadow:0 0 0 3px #000,0 0 30px 7px rgba(255,60,150,.75);}}
.titlebar{background:linear-gradient(90deg,#ff5fae,#ff8fc7);color:#1a0010;font-size:10px;padding:6px 8px;display:flex;gap:5px;align-items:center;}
.titlebar span{width:7px;height:7px;border:1px solid #1a0010;display:inline-block;border-radius:1px;}
.body{padding:30px 18px 32px;text-align:center;}
.body p{color:#ffeaf5;font-size:clamp(12px,3.6vw,15px);line-height:2;margin:0 0 30px;text-shadow:0 0 8px rgba(255,120,190,.6);}
.btnrow{display:flex;justify-content:center;gap:22px;position:relative;height:44px;}
.pixbtn{
  border:2px solid #ffeaf5;color:#ffeaf5;background:#1a0a14;padding:10px 20px;font-size:11px;
  font-family:inherit;cursor:pointer;transition:transform .25s ease,background .2s;
}
#yesBtn{box-shadow:0 0 10px rgba(255,140,200,.5);animation:yesGlow 1.6s ease-in-out infinite;}
@keyframes yesGlow{0%,100%{box-shadow:0 0 8px rgba(255,140,200,.4);}50%{box-shadow:0 0 18px rgba(255,140,200,.85);}}
.pixbtn:active{background:#3a1428;}
#noBtn{position:fixed;transition:left .2s ease,top .2s ease,transform .2s ease;z-index:20;}

/* ---------- scene 2: matrix + heart ---------- */
#loveScreen{position:absolute;inset:0;opacity:0;pointer-events:none;transition:opacity 1s ease;z-index:5;}
#loveScreen.show{opacity:1;pointer-events:auto;}
#matrix{position:absolute;inset:0;}
.vignette{position:absolute;inset:0;pointer-events:none;
  background:radial-gradient(ellipse at 50% 40%,transparent 30%,rgba(0,0,0,.75) 100%);}
#glow{
  position:absolute;top:20%;left:50%;transform:translate(-50%,0);width:420px;height:420px;max-width:110vw;
  background:radial-gradient(circle,rgba(255,50,140,.35) 0%,rgba(255,50,140,0) 70%);
  opacity:0;animation:showTitle 1.2s ease 1.3s forwards,heartbeat 1.8s ease-in-out 2.6s infinite;
}
#loveTitle{
  position:absolute;top:15%;left:50%;transform:translate(-50%,0) scale(.8);
  color:#fff;font-weight:800;font-size:clamp(26px,8vw,46px);letter-spacing:9px;font-family:'Press Start 2P',monospace;
  text-shadow:0 0 8px #ff2f92,0 0 24px #ff2f92,0 0 46px #ff2f92;
  opacity:0;animation:titlePop 1s ease 1.6s forwards;
}
@keyframes titlePop{to{opacity:1;transform:translate(-50%,0) scale(1);}}
@keyframes showTitle{to{opacity:1;}}
@keyframes heartbeat{0%,100%{transform:translate(-50%,0) scale(1);}25%{transform:translate(-50%,0) scale(1.07);}40%{transform:translate(-50%,0) scale(1);}55%{transform:translate(-50%,0) scale(1.05);}}
#heartWrap{position:absolute;top:24%;left:50%;transform:translate(-50%,0);width:360px;height:320px;max-width:96vw;
  opacity:0;animation:showTitle 1s ease .9s forwards,heartbeat 1.8s ease-in-out 2.6s infinite;}
#heartSvg{width:100%;height:100%;overflow:visible;}
#heartPath{
  fill:url(#heartGrad);stroke:#ffd0e6;stroke-width:2;filter:url(#glowFilter);
  stroke-dasharray:1400;stroke-dashoffset:1400;animation:drawHeart 1.6s ease .5s forwards;
}
@keyframes drawHeart{to{stroke-dashoffset:0;}}
.spark{position:absolute;border-radius:50%;background:#fff;opacity:0;
  animation:sparkIn .6s ease forwards,twinkle 2.4s ease-in-out infinite;}
@keyframes sparkIn{to{opacity:1;}}
@keyframes twinkle{0%,100%{opacity:.3;}50%{opacity:1;}}
#heartName{
  position:absolute;top:40%;left:50%;transform:translate(-50%,-50%);
  color:#fff;font-family:'Great Vibes',cursive;font-weight:400;
  font-size:clamp(30px,10vw,46px);letter-spacing:1px;white-space:nowrap;
  text-shadow:-1px -1px 0 #7a0033,1px -1px 0 #7a0033,-1px 1px 0 #7a0033,1px 1px 0 #7a0033,
    0 0 10px #fff,0 0 24px #ff3d92,0 0 44px #ff3d92;
  opacity:0;animation:nameIn 1s cubic-bezier(.2,1.4,.4,1) 2.1s forwards;z-index:3;
}
@keyframes nameIn{0%{opacity:0;transform:translate(-50%,-50%) scale(.6);}100%{opacity:1;transform:translate(-50%,-50%) scale(1);}}
.floatheart{position:absolute;bottom:-8%;pointer-events:none;opacity:0;animation:rise linear forwards;color:#ff8fc7;
  text-shadow:0 0 8px #ff3d92;}
@keyframes rise{0%{opacity:0;transform:translateY(0);}10%{opacity:.85;}90%{opacity:.85;}100%{opacity:0;transform:translateY(-100vh);}}
</style>
</head>
<body>

<div id="dialogScreen">
  <div class="scan"></div>
  <div class="box">
    <div class="titlebar"><span></span><span></span><span></span></div>
    <div class="body">
      <p>Do you love me babyyy<br>❤❤❤❤</p>
      <div class="btnrow">
        <button class="pixbtn" id="yesBtn" onclick="showLove()">Yes</button>
        <button class="pixbtn" id="noBtn">No</button>
      </div>
    </div>
  </div>
</div>

<div id="loveScreen">
  <canvas id="matrix"></canvas>
  <div class="vignette"></div>
  <div id="glow"></div>
  <div id="loveTitle">LOVE YOU</div>
  <div id="heartWrap">
    <svg id="heartSvg" viewBox="0 0 360 320">
      <defs>
        <radialGradient id="heartGrad" cx="50%" cy="35%" r="75%">
          <stop offset="0%" stop-color="#ffd7ea"/>
          <stop offset="45%" stop-color="#ff4f9c"/>
          <stop offset="100%" stop-color="#b3116a"/>
        </radialGradient>
        <filter id="glowFilter" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="5" result="blur"/>
          <feMerge>
            <feMergeNode in="blur"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
      </defs>
      <path id="heartPath" d=""></path>
    </svg>
    <div id="heartName">Mia</div>
  </div>
</div>

<script>
/* ---- dodging No button (runs anywhere on screen) ---- */
const noBtn=document.getElementById('noBtn');
const yesBtn=document.getElementById('yesBtn');
const box=document.querySelector('.box');
let scale=1, dodges=0;
function placeInitial(){
  const r=box.getBoundingClientRect();
  const br=document.querySelector('.btnrow').getBoundingClientRect();
  noBtn.style.left=(br.left+br.width/2+30)+'px';
  noBtn.style.top=(br.top)+'px';
}
function dodge(){
  dodges=Math.min(dodges+1,8);
  scale=Math.max(0.55,1-dodges*0.05);
  noBtn.style.transform=`scale(${scale})`;
  yesBtn.style.transform=`scale(${Math.min(1.5,1+dodges*0.045)})`;
  const bw=90*scale, bh=40*scale, margin=16;
  const maxX=window.innerWidth-bw-margin, maxY=window.innerHeight-bh-margin;
  const x=margin+Math.random()*(maxX-margin);
  const y=margin+Math.random()*(maxY-margin);
  noBtn.style.left=x+'px';
  noBtn.style.top=y+'px';
}
noBtn.addEventListener('mouseenter',dodge);
noBtn.addEventListener('touchstart',e=>{e.preventDefault();dodge();},{passive:false});
noBtn.addEventListener('click',e=>{e.preventDefault();dodge();});
window.addEventListener('resize',placeInitial);
placeInitial();

/* ---- matrix rain ---- */
const canvas=document.getElementById('matrix');
const ctx=canvas.getContext('2d');
let W,H,cols,drops;
const chars="アイウエオカキクケコサシスセソタチツテト0123456789LOVE❤";
function resize(){
  W=canvas.width=window.innerWidth;
  H=canvas.height=window.innerHeight;
  cols=Math.floor(W/18);
  drops=new Array(cols).fill(0).map(()=>Math.random()*-50);
}
resize(); window.addEventListener('resize',resize);
function drawMatrix(){
  ctx.fillStyle='rgba(0,0,0,0.14)';
  ctx.fillRect(0,0,W,H);
  ctx.font='16px monospace';
  for(let i=0;i<cols;i++){
    const ch=chars[Math.floor(Math.random()*chars.length)];
    const isHead=Math.random()<0.08;
    ctx.fillStyle=isHead?'#ffd7ea':'rgba(255,60,140,0.4)';
    ctx.fillText(ch,i*18,drops[i]*18);
    if(drops[i]*18>H && Math.random()>0.975) drops[i]=0;
    drops[i]++;
  }
  requestAnimationFrame(drawMatrix);
}
let matrixStarted=false;

/* ---- heart path (parametric heart curve -> smooth SVG path) ---- */
function buildHeartPath(){
  const cx=180, cy=130, scale=9, N=200;
  let d='';
  for(let i=0;i<=N;i++){
    const t=(i/N)*Math.PI*2;
    const x=16*Math.pow(Math.sin(t),3);
    const y=13*Math.cos(t)-5*Math.cos(2*t)-2*Math.cos(3*t)-Math.cos(4*t);
    const px=(cx+x*scale).toFixed(1), py=(cy-y*scale).toFixed(1);
    d+= (i===0?'M':'L')+px+' '+py+' ';
  }
  d+='Z';
  document.getElementById('heartPath').setAttribute('d',d);

  // sparkles around the outline
  const wrap=document.getElementById('heartWrap');
  for(let i=0;i<16;i++){
    const t=Math.random()*Math.PI*2;
    const rr=1.08+Math.random()*0.12;
    const x=16*Math.pow(Math.sin(t),3)*rr;
    const y=(13*Math.cos(t)-5*Math.cos(2*t)-2*Math.cos(3*t)-Math.cos(4*t))*rr;
    const px=cx+x*scale, py=cy-y*scale;
    const s=document.createElement('div');
    s.className='spark';
    const size=2+Math.random()*3;
    s.style.width=size+'px';s.style.height=size+'px';
    s.style.left=px+'px';s.style.top=py+'px';
    s.style.animationDelay=(1.8+Math.random()*1.2)+'s, '+(2+Math.random()*2)+'s';
    wrap.appendChild(s);
  }
}
buildHeartPath();

function startHearts(){
  const icons=['💗','✨','💫'];
  function spawn(){
    const h=document.createElement('div');
    h.className='floatheart';
    h.textContent=icons[Math.floor(Math.random()*icons.length)];
    h.style.left=Math.random()*100+'vw';
    h.style.fontSize=(14+Math.random()*16)+'px';
    const dur=8+Math.random()*5;
    h.style.animationDuration=dur+'s';
    document.body.appendChild(h);
    setTimeout(()=>h.remove(),dur*1000+300);
  }
  for(let i=0;i<4;i++) setTimeout(spawn,i*700);
  setInterval(spawn,1600);
}

function showLove(){
  document.getElementById('dialogScreen').style.opacity='0';
  setTimeout(()=>document.getElementById('dialogScreen').style.pointerEvents='none',600);
  document.getElementById('loveScreen').classList.add('show');
  if(!matrixStarted){matrixStarted=true; drawMatrix(); startHearts();}
}
</script>
</body>
</html>


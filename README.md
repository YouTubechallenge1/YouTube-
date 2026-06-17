   <!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Shorts Donation Game</title>
<style>
body{font-family:Arial,sans-serif;background:#0f172a;color:white;margin:0}
.hero{text-align:center;padding:30px}
.crypto-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:10px;padding:20px}
.crypto-btn{background:#1e293b;border:1px solid #334155;border-radius:12px;padding:12px;color:white;cursor:pointer}
.crypto-btn:hover{transform:scale(1.03)}
.toast{position:fixed;bottom:20px;right:20px;background:#22c55e;padding:10px 16px;border-radius:8px;display:none}
.level{background:#1e293b;margin:10px;border-radius:10px;padding:12px}
</style>
</head>
<body>
<div class="hero">
<h1>THE SHORTS DONATION GAME</h1>
<p>Tap a crypto button to copy donation address.</p>
</div>

<div class="crypto-grid">
<button class="crypto-btn" onclick="copyAddr('bc1q5gxpm2frv49drn05ejcxg7um048hhjwgkahl0k','BTC')">₿ BTC</button>
<button class="crypto-btn" onclick="copyAddr('0x2002F217A5991521fc8Aac74b522295693C18e36','ETH')">◆ ETH</button>
<button class="crypto-btn" onclick="copyAddr('7wFK8mBC9qNQ15VpX9PhCzABTLA5omAsVzx8Lud5MvN','SOL')">SOL</button>
<button class="crypto-btn" onclick="copyAddr('UQCEdaxRbzLGUgihFx-51Au7mc2DhV5FlcPNRKuiiaJlIDJW','TON')">TON</button>
</div>

<div id="levels"></div>
<div id="toast" class="toast"></div>

<script>
function copyAddr(addr,name){
 navigator.clipboard.writeText(addr);
 let t=document.getElementById('toast');
 t.innerText='✓ '+name+' address copied';
 t.style.display='block';
 setTimeout(()=>t.style.display='none',2000);
}
const levels=[];
for(let i=1;i<=100;i++){
 levels.push({id:i,price:Math.min(1000,Math.round(4+(i-1)*10.06))});
}
const box=document.getElementById('levels');
levels.forEach(l=>{
 box.innerHTML += `<div class="level">LEVEL ${l.id} - $${l.price}</div>`;
});
</script>
</body>
</html>
             

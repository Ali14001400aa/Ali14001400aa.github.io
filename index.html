<!doctype html>
<html lang="fa" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>BSC Wallet Viewer</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Tahoma,Arial,sans-serif;background:#07111f;color:#eef6ff;min-height:100vh}
.bg{position:fixed;inset:0;overflow:hidden;z-index:-1;background:radial-gradient(circle at 20% 10%,#15335a 0,transparent 35%),radial-gradient(circle at 85% 80%,#193d31 0,transparent 35%),#07111f}
.wrap{width:min(1050px,92%);margin:42px auto}.hero{text-align:center;margin-bottom:28px}.logo{width:64px;height:64px;margin:auto;border-radius:20px;display:grid;place-items:center;background:linear-gradient(135deg,#f0b90b,#ff8a00);font-size:30px;box-shadow:0 12px 40px #f0b90b33}
h1{margin:16px 0 8px;font-size:32px}.sub{color:#9db0c7}.card{background:#0d1b2dce;border:1px solid #ffffff12;border-radius:24px;padding:22px;box-shadow:0 20px 60px #0005;backdrop-filter:blur(16px)}
.form{display:flex;gap:10px}.form input{flex:1;min-width:0;background:#07111f;border:1px solid #263b55;color:#fff;padding:16px;border-radius:14px;font-size:15px;direction:ltr;text-align:left}.btn{border:0;border-radius:14px;padding:0 24px;background:#f0b90b;color:#111;font-weight:800;cursor:pointer}.btn:disabled{opacity:.5;cursor:wait}
.api{margin-top:12px;color:#8fa5bd;font-size:12px}.api input{background:#07111f;border:1px solid #263b55;color:#fff;border-radius:10px;padding:9px;width:300px;direction:ltr}
.hidden{display:none}.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-top:16px}.stat{padding:20px;border-radius:18px;background:#102239;border:1px solid #ffffff0d}.label{color:#8fa5bd;font-size:13px}.value{font-size:24px;font-weight:800;margin-top:9px;direction:ltr;text-align:right}.green{color:#55e6a5}.yellow{color:#f0b90b}
.section{margin-top:16px}.section h2{font-size:18px}.table{overflow:auto;border-radius:16px;border:1px solid #ffffff10}.row{display:grid;grid-template-columns:150px 1fr 130px 120px;gap:12px;min-width:700px;padding:14px 16px;border-bottom:1px solid #ffffff09;align-items:center}.row.head{color:#8fa5bd;background:#0a1728;font-size:12px}.row:last-child{border:0}.addr{font-family:monospace;font-size:12px;direction:ltr;text-align:left;overflow:hidden;text-overflow:ellipsis}.pill{padding:5px 9px;border-radius:999px;background:#173f31;color:#55e6a5;font-size:11px;display:inline-block}.muted{color:#8fa5bd}.err{color:#ff7d8d;margin-top:12px}.loader{display:inline-block;width:17px;height:17px;border:2px solid #ffffff33;border-top-color:#111;border-radius:50%;animation:spin .7s linear infinite;vertical-align:middle}@keyframes spin{to{transform:rotate(360deg)}}footer{text-align:center;color:#71859d;font-size:12px;margin:22px}
@media(max-width:700px){.form{flex-direction:column}.btn{height:52px}.grid{grid-template-columns:1fr}h1{font-size:26px}.api input{width:100%;margin-top:7px}}
</style>
</head>
<body>
<div class="bg"></div>
<main class="wrap">
<section class="hero">
<div class="logo">₿</div>
<h1>BSC Wallet Viewer</h1>
<div class="sub">موجودی و تراکنش‌های کیف پول روی BNB Smart Chain</div>
</section>

<div class="card">
<div class="form">
<input id="address" placeholder="مثال: 0xccE2Ee92FB3EdE02cfb9e587dA275172E86604fA">
<button id="search" class="btn">بررسی کیف پول</button>
</div>
<div class="api">
کلید API سایت BscScan برای نمایش تاریخچه تراکنش‌ها لازم است.
<input id="apiKey" placeholder="BscScan API Key" autocomplete="off">
</div>
<div id="error" class="err"></div>
</div>

<section id="result" class="hidden">
<div class="grid">
<div class="stat"><div class="label">ارزش تقریبی کل</div><div id="total" class="value">$0.00</div></div>
<div class="stat"><div class="label">USDT (BEP-20)</div><div id="usdt" class="value green">0.00</div></div>
<div class="stat"><div class="label">BNB</div><div id="bnb" class="value yellow">0.000000</div></div>
</div>
<div class="card section">
<h2>آخرین واریزهای USDT</h2>
<div id="txs" class="table"><div class="muted" style="padding:18px">هنوز اطلاعاتی دریافت نشده است.</div></div>
</div>
</section>
<footer>شبکه: BNB Smart Chain • USDT: BEP-20</footer>
</main>

<script>
const USDT='0x55d398326f99059fF775485246999027B3197955';
const RPC='https://bsc-dataseed.binance.org/';
const $=id=>document.getElementById(id);
const short=a=>a.slice(0,8)+'…'+a.slice(-6);
const fmtDate=ts=>new Date(Number(ts)*1000).toLocaleString('fa-IR',{dateStyle:'medium',timeStyle:'short'});
const valid=a=>/^0x[a-fA-F0-9]{40}$/.test(a);

async function rpc(method,params){
 const r=await fetch(RPC,{method:'POST',headers:{'content-type':'application/json'},body:JSON.stringify({jsonrpc:'2.0',id:1,method,params})});
 const j=await r.json(); if(j.error) throw Error(j.error.message); return j.result;
}
async function balanceOf(address){
 const data='0x70a08231'+address.slice(2).padStart(64,'0');
 const hex=await rpc('eth_call',[{to:USDT,data},'latest']);
 return Number(BigInt(hex))/1e18;
}
async function bnbBalance(address){
 const hex=await rpc('eth_getBalance',[address,'latest']);
 return Number(BigInt(hex))/1e18;
}
async function bnbPrice(){
 try{
   const r=await fetch('https://api.coingecko.com/api/v3/simple/price?ids=binancecoin&vs_currencies=usd');
   const j=await r.json(); return j.binancecoin.usd||0;
 }catch{return 0}
}
async function txHistory(address,key){
 if(!key) return [];
 const url=`https://api.bscscan.com/api?chainid=56&module=account&action=tokentx&contractaddress=${USDT}&address=${address}&page=1&offset=20&sort=desc&apikey=${encodeURIComponent(key)}`;
 const r=await fetch(url); const j=await r.json();
 if(j.status!=='1' && j.message!=='No transactions found') throw Error(j.result||j.message||'خطا در BscScan');
 return (j.result||[]).filter(x=>x.to.toLowerCase()===address.toLowerCase());
}
function renderTxs(txs,address){
 if(!txs.length){$('txs').innerHTML='<div class="muted" style="padding:18px">واریز USDT پیدا نشد یا API Key وارد نشده است.</div>';return}
 $('txs').innerHTML='<div class="row head"><div>زمان</div><div>فرستنده</div><div>مقدار</div><div>وضعیت</div></div>'+
 txs.map(x=>`<div class="row"><div>${fmtDate(x.timeStamp)}</div><div class="addr" title="${x.from}">${short(x.from)}</div><div class="green">${(Number(x.value)/1e18).toLocaleString('en-US',{maximumFractionDigits:4})} USDT</div><div><span class="pill">واریز</span></div></div>`).join('');
}
async function run(){
 const address=$('address').value.trim(); $('error').textContent='';
 if(!valid(address)){ $('error').textContent='آدرس BSC معتبر نیست.'; return }
 $('search').disabled=true; $('search').innerHTML='<span class="loader"></span> در حال بررسی';
 try{
  const [usdt,bnb,price]=await Promise.all([balanceOf(address),bnbBalance(address),bnbPrice()]);
  $('usdt').textContent=usdt.toLocaleString('en-US',{maximumFractionDigits:4});
  $('bnb').textContent=bnb.toLocaleString('en-US',{maximumFractionDigits:6});
  $('total').textContent='$'+(usdt+bnb*price).toLocaleString('en-US',{maximumFractionDigits:2});
  $('result').classList.remove('hidden');
  try{renderTxs(await txHistory(address,$('apiKey').value.trim()),address)}
  catch(e){$('txs').innerHTML='<div class="err" style="padding:18px">تاریخچه تراکنش‌ها: '+e.message+'</div>'}
 }catch(e){$('error').textContent='خطا: '+e.message}
 finally{$('search').disabled=false;$('search').textContent='بررسی کیف پول'}
}
$('search').onclick=run;
$('address').onkeydown=e=>{if(e.key==='Enter')run()};
</script>
</body>
</html>

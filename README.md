<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>مركز أوراق للبحوث والدراسات</title>
<link href="https://fonts.googleapis.com/css2?family=Amiri:wght@700&family=Tajawal:wght@400;700;800&display=swap" rel="stylesheet">
<style>
:root{--paper:#fdfbf5;--ink:#1e1e1e;--gold:#b8963e;--dark:#14201d;--line:#ece3d3}
*{box-sizing:border-box}body{margin:0;background:var(--paper);color:var(--ink);font-family:'Tajawal',sans-serif;line-height:1.9}
header{padding:18px 22px;display:flex;justify-content:space-between;align-items:center;max-width:1200px;margin:auto}
.logo{font-family:'Amiri',serif;font-size:28px;color:var(--dark);line-height:.9}.logo span{display:block;font-family:'Tajawal';font-size:10px;letter-spacing:4px;color:var(--gold);margin-top:4px}
.hero{max-width:1200px;margin:0 auto;padding:60px 22px 20px;display:grid;grid-template-columns:1.1fr .9fr;gap:30px}
@media(max-width:800px){.hero{grid-template-columns:1fr}}
.hero h1{font-family:'Amiri',serif;font-size:46px;line-height:1.2;margin:0;color:var(--dark)}.hero h1 b{color:var(--gold)}
.sec{max-width:1200px;margin:30px auto;padding:0 22px;display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
@media(max-width:800px){.sec{grid-template-columns:1fr}}
.box{background:#fff;border:1px solid var(--line);border-radius:16px;padding:20px}
.box h3{font-family:'Amiri',serif;margin:0 0 8px;color:var(--dark);border-right:3px solid var(--gold);padding-right:10px}
.box p{margin:0;opacity:.75;font-size:14px}
.divider{max-width:1200px;margin:20px auto;padding:0 22px;display:flex;align-items:center;gap:12px}
.divider i{height:1px;background:var(--line);flex:1}.divider b{font-family:'Amiri';color:var(--gold)}
.grid{max-width:1200px;margin:0 auto 50px;padding:0 22px;display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:16px}
.card{background:#fff;border:1px solid var(--line);border-radius:14px;overflow:hidden}
.card img{width:100%;height:190px;object-fit:cover}
.card .bd{padding:14px}.badge{font-size:11px;font-weight:800;color:var(--gold);border:1px solid var(--line);padding:3px 10px;border-radius:20px}
footer{text-align:center;padding:30px;opacity:.4;font-size:12px;border-top:1px solid var(--line)}
</style>
</head>
<body>
<header><div class="logo">أوراق<span>AWRAQ RESEARCH CENTER</span></div></header>

<div class="hero">
<div><h1>مركز <b>أوراق</b> للبحوث والدراسات</h1><p id="t_intro" style="opacity:.7;margin-top:12px"></p></div>
<div class="box" style="background:var(--dark);color:#fff;border-color:var(--dark)"><h3 style="color:#fff;border-color:var(--gold)">لماذا أوراق؟</h3><p style="color:rgba(255,255,255,.7)">نقدم معرفة رصينة بأدوات بحثية معاصرة، تجمع بين الأصالة والتحليل العلمي العميق.</p></div>
</div>

<div class="sec">
<div class="box"><h3>تعريف المركز</h3><p id="t_tareef"></p></div>
<div class="box"><h3>رسالتنا</h3><p id="t_resala"></p></div>
<div class="box"><h3>رؤيتنا</h3><p id="t_roaya"></p></div>
</div>

<div class="divider"><i></i><b>إصدارات وبحوث المركز</b><i></i></div>
<div class="grid" id="grid"></div>
<footer>مركز أوراق للبحوث والدراسات © 2026</footer>

<script>
function getInfo(){
 return JSON.parse(localStorage.getItem("awraq_info")) || {
  intro:"مركز متخصص في البحوث الاستراتيجية والدراسات التاريخية المعمقة، وبحوث في كافة المجالات الإسلامية والحياتية.",
  tareef:"مركز أوراق هو مؤسسة بحثية مستقلة تُعنى بإنتاج المعرفة الرصينة وتوثيقها، وتهتم بتحليل الظواهر السياسية والتاريخية والاجتماعية بمنهج علمي موضوعي.",
  resala:"تقديم دراسات وتقارير استراتيجية تخدم الباحث وصانع القرار، وتسهم في فهم الواقع واستشراف المستقبل برؤية إسلامية أصيلة ومعاصرة.",
  roaya:"أن نكون مرجعاً علمياً رصيناً في مجال البحوث الاستراتيجية والتاريخية على مستوى العراق والعالم الإسلامي."
 }
}
function getPosts(){return JSON.parse(localStorage.getItem("aurak_posts"))||[]}
let info=getInfo();
document.getElementById('t_intro').innerText=info.intro;
document.getElementById('t_tareef').innerText=info.tareef;
document.getElementById('t_resala').innerText=info.resala;
document.getElementById('t_roaya').innerText=info.roaya;

let grid=document.getElementById('grid');let posts=getPosts();
if(posts.length==0){grid.innerHTML="<p style='grid-column:1/-1;text-align:center;opacity:.4;padding:30px'>سيتم نشر البحوث قريباً</p>"}else{
 grid.innerHTML=posts.map(p=>`
 <div class="card">${p.media? (p.media.includes('youtu')? `<iframe width="100%" height="190" src="${p.media.replace('watch?v=','embed/')}" frameborder="0" allowfullscreen></iframe>`:`<img src="${p.media}">`):`<img src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=600">`}
 <div class="bd"><span class="badge">${p.category}</span><h3 style="font-family:'Amiri';margin:8px 0;font-size:19px">${p.title}</h3><p style="opacity:.65;font-size:13px">${p.content.substring(0,110)}...</p><small style="opacity:.4">${p.date}</small></div></div>`).join('');
}
</script>
</body>
</html>

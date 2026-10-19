<!DOCTYPE html>
<html lang="vi"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>GaraPro — Quản lý gara ô tô</title>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#f3f5f7;--sf:#fff;--tx:#17212b;--mu:#5d6b79;--ln:#dde3e9;--nv:#102a43;--tl:#0e8f84;--tl2:#e2f4f2;--or:#e8742a;--rd:#c8382f;--gn:#238a4f;--bl:#2a6fb0;--ye:#b8860b;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme=light]){--bg:#0e1620;--sf:#16212d;--tx:#e6ecf2;--mu:#93a1af;--ln:#2a3947;--nv:#0a1a2b;--tl:#2cc0b2;--tl2:#143a3a}}
*{box-sizing:border-box}html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;font:14px/1.5 'Be Vietnam Pro',system-ui,Arial,sans-serif;background:var(--bg);color:var(--tx);display:flex;min-height:100vh}
aside{width:224px;background:var(--nv);color:#cfd9e3;padding:16px 10px;flex-shrink:0;position:sticky;top:0;height:100vh;overflow:auto}
.logo{font-weight:700;font-size:18px;color:#fff;padding:4px 10px 18px}.logo b{color:#4fd6c8}
aside a{display:flex;gap:10px;align-items:center;padding:9px 10px;border-radius:6px;color:inherit;text-decoration:none;margin-bottom:2px;cursor:pointer}
aside a:hover{background:#1b3a58}aside a.on{background:var(--tl);color:#fff;font-weight:600}
aside i{width:18px;text-align:center;font-style:normal}
main{flex:1;min-width:0}
header{display:flex;gap:12px;align-items:center;padding:12px 24px;background:var(--sf);border-bottom:1px solid var(--ln);position:sticky;top:0;z-index:5}
header h1{font-size:17px;margin:0;flex:1}
input,select,textarea{font:inherit;padding:7px 10px;border:1px solid var(--ln);border-radius:6px;background:var(--sf);color:var(--tx);min-height:36px}
button{font:inherit;padding:7px 14px;border-radius:6px;border:1px solid var(--ln);background:var(--sf);color:var(--tx);cursor:pointer;min-height:36px}
button:hover{border-color:var(--tl)}button.p{background:var(--or);border-color:var(--or);color:#fff;font-weight:600}button.t{background:var(--tl);border-color:var(--tl);color:#fff}
:focus-visible{outline:2px solid var(--tl);outline-offset:2px}
.menu{display:none}
.pg{padding:20px 24px;max-width:1400px}
.bar{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:14px;align-items:center}.bar .sp{flex:1}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:12px;margin-bottom:16px}
.k{background:var(--sf);border:1px solid var(--ln);border-radius:8px;padding:12px 14px}.k small{color:var(--mu)}.k b{display:block;font-size:24px;margin-top:2px}
.k.w b{color:var(--or)}
.two{display:grid;grid-template-columns:3fr 2fr;gap:14px;margin-bottom:14px}
.box{background:var(--sf);border:1px solid var(--ln);border-radius:8px;padding:14px;min-width:0}.box h3{margin:0 0 10px;font-size:14px}
.tw{overflow-x:auto;background:var(--sf);border:1px solid var(--ln);border-radius:8px}
table{border-collapse:collapse;width:100%;min-width:720px}th,td{text-align:left;padding:9px 12px;border-bottom:1px solid var(--ln);white-space:nowrap}
th{font-size:12px;color:var(--mu);text-transform:uppercase;letter-spacing:.03em;cursor:pointer;background:var(--bg)}tr:last-child td{border-bottom:0}
tbody tr:hover{background:var(--tl2)}
.tag{display:inline-block;padding:1px 9px;border-radius:99px;font-size:12px;font-weight:500;background:var(--tl2);color:var(--tl)}
.s0,.s1{background:#e8eef5;color:#40566e}.s2{background:#fff1d6;color:var(--ye)}.s3{background:#dcebfa;color:var(--bl)}.s4{background:#fde5d3;color:#b85410}.s5{background:#e9e2f7;color:#6446a8}.s6,.s7,.ok{background:#dcf2e5;color:var(--gn)}.bad{background:#fbe0dd;color:var(--rd)}.warn{background:#fde5d3;color:#b85410}
.kb{display:flex;gap:10px;overflow-x:auto;padding-bottom:10px;align-items:flex-start}
.col{flex:0 0 232px;background:#e6ebf0;border-radius:8px;padding:8px;min-height:140px}
@media(prefers-color-scheme:dark){:root:not([data-theme=light]) .col{background:#101a25}}
.col h4{margin:2px 4px 8px;font-size:12.5px;display:flex;justify-content:space-between}
.col.over{outline:2px dashed var(--tl);background:var(--tl2)}
.card{background:var(--sf);border:1px solid var(--ln);border-radius:6px;padding:9px 10px;margin-bottom:8px;cursor:grab;font-size:13px}
.card.drag{opacity:.4;transform:rotate(2deg)}.card b{font-size:13px}.card small{color:var(--mu);display:block}
.pr{border-left:3px solid var(--ln)}.pr.cao{border-left-color:var(--rd)}.pr.tb{border-left-color:var(--or)}
.mod{position:fixed;inset:0;background:rgba(10,20,30,.55);display:flex;align-items:center;justify-content:center;z-index:20;padding:12px}
.dlg{background:var(--sf);border-radius:10px;padding:20px;width:640px;max-width:100%;max-height:92vh;overflow:auto}
.dlg h2{margin:0 0 4px;font-size:18px}.row{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:12px 0}.row div small{color:var(--mu);display:block}
label{display:block;margin-bottom:10px;font-weight:500}label input,label select{width:100%;margin-top:3px}.err{color:var(--rd);font-size:12px;font-weight:400}
.toast{position:fixed;right:20px;bottom:20px;padding:10px 16px;border-radius:6px;color:#fff;z-index:30;max-width:340px}
.empty{padding:30px;text-align:center;color:var(--mu)}
.seg button{border-radius:0}.seg button.on{background:var(--tl);color:#fff;border-color:var(--tl)}
.bars{display:flex;align-items:flex-end;gap:10px;height:150px}.bars div{flex:1;text-align:center;font-size:11px;color:var(--mu)}.bars span{display:block;background:var(--tl);border-radius:4px 4px 0 0;margin-bottom:4px}
ul.l{list-style:none;padding:0;margin:0}ul.l li{padding:7px 0;border-bottom:1px solid var(--ln);display:flex;justify-content:space-between;gap:8px}
.hub{background:#1b3a58;border-radius:6px;padding:8px 10px;margin:0 0 12px;font-size:12px}.hub b{display:block;color:#fff;font-size:13px}.dot{display:inline-block;width:9px;height:9px;border-radius:50%;margin-right:6px}.dot.gn{background:var(--gn)}.dot.am{background:var(--or)}.dot.rd{background:var(--rd)}.me{margin-top:18px;padding:10px;border-top:1px solid #1b3a58;font-size:12px}.prog{height:8px;background:var(--ln);border-radius:4px;overflow:hidden;margin:8px 0 4px}.prog i{display:block;height:100%;background:var(--tl)}.chip{padding:3px 10px;border-radius:99px;background:var(--tl2);color:var(--tl);font-weight:600;font-size:12px;white-space:nowrap}
@media(max-width:900px){aside{position:fixed;z-index:15;left:-240px;transition:left .2s}aside.open{left:0}.menu{display:inline-block}.two{grid-template-columns:1fr}.pg{padding:14px}header{padding:10px 14px}#q{width:110px}.row{grid-template-columns:1fr}}
</style></head><body>
<aside id="sb"><div class="logo">Gara<b>Pro</b></div><div class="hub"><b>Chi nhánh Trung tâm</b>Dữ liệu minh họa · chưa kết nối máy chủ</div><nav id="nav"></nav><div class="me"><b style="color:#fff">Điều phối trưởng</b><br>Chấm công, nhân sự trực: chưa triển khai</div></aside>
<main><header><button class="menu" onclick="sb.classList.toggle('open')" aria-label="Mở menu">☰ Menu</button><h1 id="ttl"></h1><span class="chip" id="bay"></span><input id="q" placeholder="Tìm biển số, phiếu, khách (Ctrl+K)" aria-label="Tìm kiếm"><span title="Thông báo" id="bell" style="cursor:pointer">🔔</span><span class="tag">Chủ gara · Demo</span></header>
<div class="pg" id="pg"></div></main><div id="mo"></div>
<script>
const $=s=>document.querySelector(s),vnd=n=>n.toLocaleString('vi-VN')+' ₫';
const ST=['Mới tiếp nhận','Chờ kiểm tra','Chờ báo giá/xác nhận','Đang sửa chữa','Chờ phụ tùng','Chờ kiểm tra hoàn tất','Hoàn thành','Đã bàn giao'];
const tag=i=>`<span class="tag s${i}">${ST[i]}</span>`;
let O=[
['PSC-0412','51H-284.17','Nguyễn Văn Thành','Thay má phanh trước','Hùng','cao','Hôm nay',3,2850000],
['PSC-0413','30G-559.02','Trần Thị Lan','Bảo dưỡng 40.000 km','Tuấn','tb','Hôm nay',3,3400000],
['PSC-0414','59A-118.76','Lê Quốc Bảo','Kiểm tra tiếng ồn gầm','Long','tb','Ngày mai',1,0],
['PSC-0415','51K-902.33','Phạm Minh Châu','Thay bơm nước','Hùng','cao','Ngày mai',4,4200000],
['PSC-0416','60A-731.45','Võ Hoàng Nam','Sơn dặm cản sau','Phúc','th','21/10',2,5600000],
['PSC-0417','51F-377.80','Đặng Thu Hà','Thay lọc gió, lọc dầu','Tuấn','th','Hôm nay',5,980000],
['PSC-0418','61A-246.19','Bùi Gia Huy','Cân chỉnh góc đặt bánh','Phúc','th','Hôm nay',6,650000],
['PSC-0419','51H-675.04','Ngô Thanh Tùng','Thay ắc quy','Long','tb','Hôm qua',7,2300000],
['PSC-0420','50A-413.58','Huỳnh Mai Anh','Thay dầu hộp số','Hùng','th','Hôm qua',7,1750000],
['PSC-0421','51G-820.66','Đỗ Văn Khoa','Chẩn đoán đèn check engine','Long','cao','Hôm nay',0,0]
].map(a=>({id:a[0],plate:a[1],cust:a[2],task:a[3],tech:a[4],pr:a[5],due:a[6],st:a[7],cost:a[8]}));
const V=[['51H-284.17','Toyota','Camry',2019,'Nguyễn Văn Thành','0903 114 227','05/07/2026'],['30G-559.02','Honda','CR-V',2021,'Trần Thị Lan','0912 880 345','20/04/2026'],['59A-118.76','Hyundai','Accent',2018,'Lê Quốc Bảo','0977 301 662','12/01/2026'],['51K-902.33','Mazda','CX-5',2020,'Phạm Minh Châu','0938 556 019','03/08/2026'],['60A-731.45','Kia','Seltos',2022,'Võ Hoàng Nam','0868 245 790','28/09/2026'],['51F-377.80','Ford','Ranger',2017,'Đặng Thu Hà','0944 702 118','15/06/2026']];
const P=[['PT-001','Má phanh trước Camry','Phanh','bộ',3,4,680000,'A1-02'],['PT-002','Lọc dầu động cơ','Lọc','cái',24,10,85000,'B2-01'],['PT-003','Dầu nhớt 5W-30 (4L)','Dầu nhớt','can',11,8,420000,'C1-04'],['PT-004','Bơm nước Mazda CX-5','Làm mát','cái',1,2,1450000,'A3-05'],['PT-005','Ắc quy 12V 70Ah','Điện','cái',6,3,1800000,'D1-01'],['PT-006','Lọc gió động cơ','Lọc','cái',15,6,160000,'B2-03']];
const I=[['HD-2031','PSC-0419','Ngô Thanh Tùng',0,2300000,2300000],['HD-2032','PSC-0420','Huỳnh Mai Anh',1,1750000,1750000],['HD-2033','PSC-0418','Bùi Gia Huy',1,650000,300000],['HD-2034','PSC-0417','Đặng Thu Hà',3,980000,980000]];
const DAYS=['T2','T3','T4','T5','T6','T7','CN'],BAYS=8,TARGET=30000000;
const bayUse=()=>O.filter(o=>o.st>=3&&o.st<=5).length;
const tl=o=>o.st>=6?'gn':(o.st==4||(o.pr=='cao'&&o.st<3))?'rd':'am';
const A=[['08:30','Trần Thị Lan','30G-559.02','Bảo dưỡng định kỳ','Đã xác nhận'],['10:00','Lê Quốc Bảo','59A-118.76','Kiểm tra gầm','Chưa xác nhận'],['14:00','Phạm Minh Châu','51K-902.33','Nhận xe sau sửa','Đã xác nhận'],['15:30','Mai Văn Đức','72A-005.91','Thay lốp','Chưa xác nhận']];
const NAV=[['dash','▦','Tổng quan'],['veh','🚗','Xe và khách hàng'],['ord','🔧','Phiếu sửa chữa'],['apt','📅','Lịch hẹn'],['inv','📦','Kho phụ tùng'],['stf','👥','Nhân viên'],['bil','🧾','Hóa đơn và thanh toán'],['rep','📊','Báo cáo thống kê'],['set','⚙','Cài đặt']];
let view='ord',mode='kb',sort={},q='';
function toast(m,bad){const t=document.createElement('div');t.className='toast';t.style.background=bad?'var(--rd)':'var(--gn)';t.textContent=m;document.body.append(t);setTimeout(()=>t.remove(),3200)}
function go(v){view=v;sb.classList.remove('open');render()}
function nav(){$('#nav').innerHTML=NAV.map(n=>`<a class="${n[0]==view?'on':''}" tabindex=0 onclick="go('${n[0]}')" onkeydown="if(event.key=='Enter')go('${n[0]}')"><i>${n[1]}</i>${n[2]}</a>`).join('')}
function table(h,rows,cols){if(!rows.length)return'<div class="empty">Không tìm thấy dữ liệu phù hợp.</div>';
 return`<div class="tw"><table><thead><tr>${h.map((x,i)=>`<th onclick="doSort(${i})">${x}${sort.i==i?(sort.d>0?' ▲':' ▼'):''}</th>`).join('')}</tr></thead><tbody>${rows.join('')}</tbody></table></div>`}
function doSort(i){sort={i,d:sort.i==i?-sort.d:1};render()}
function srt(rows){if(sort.i==null)return rows;return[...rows].sort((a,b)=>String(a[sort.i]).localeCompare(String(b[sort.i]),'vi',{numeric:true})*sort.d)}
const match=(...s)=>!q||s.join(' ').toLowerCase().includes(q.toLowerCase());
function render(){nav();$('#bay').textContent='Khoang: '+bayUse()+'/'+BAYS+' ('+Math.round(bayUse()/BAYS*100)+'%)';const t=NAV.find(n=>n[0]==view)[2];$('#ttl').textContent=t;$('#pg').innerHTML=pages[view]()}
const revByDay=DAYS.map((d,i)=>I.filter(x=>x[3]==i).reduce((s,x)=>s+x[5],0));
const pages={
dash(){const act=O.filter(o=>o.st==3).length,wait=O.filter(o=>o.st<3).length,open=O.filter(o=>o.st<6).length,low=P.filter(p=>p[4]<=p[5]).length,rev=I.reduce((s,x)=>s+x[5],0),mx=Math.max(...revByDay,1);
const d=new Date().toLocaleDateString('vi-VN',{weekday:'long',day:'2-digit',month:'2-digit',year:'numeric'});
return`<div class="bar"><div><b style="font-size:16px">Xin chào, anh/chị quản lý</b><br><small style="color:var(--mu)">${d} · Dữ liệu minh họa</small></div><span class="sp"></span><select><option>7 ngày qua</option></select><button class="p" onclick="newOrder()">+ Tiếp nhận xe</button></div>
<div class="grid"><div class="k"><small>Xe đang sửa chữa</small><b>${act}</b></div><div class="k"><small>Xe chờ tiếp nhận/xử lý</small><b>${wait}</b></div><div class="k"><small>Lịch hẹn hôm nay</small><b>${A.length}</b></div><div class="k"><small>Doanh thu đã thu (7 ngày)</small><b style="font-size:19px;padding-top:5px">${vnd(rev)}</b></div><div class="k"><small>Phiếu chưa hoàn thành</small><b>${open}</b></div><div class="k ${low?'w':''}"><small>Phụ tùng sắp hết</small><b>${low}</b></div></div>
<div class="two"><div class="box"><h3>Doanh thu so với mục tiêu tuần</h3><b style="font-size:20px">${vnd(rev)}</b> / ${vnd(TARGET)}<div class="prog"><i style="width:${Math.min(100,rev/TARGET*100)}%"></i></div><small style="color:var(--mu)">Đạt ${Math.round(rev/TARGET*100)}% · mục tiêu là số minh họa</small></div><div class="box"><h3>Khoang sửa chữa &amp; phụ tùng nguy cấp</h3>Khoang đang dùng: <b>${bayUse()}/${BAYS}</b><div class="prog"><i style="width:${bayUse()/BAYS*100}%"></i></div><span class="dot rd"></span>Phiếu chờ phụ tùng: <b>${O.filter(o=>o.st==4).length}</b> · Phụ tùng sắp hết: <b>${low}</b> <a href="#" onclick="go('inv');return false">Xem kho</a></div></div>
<div class="two"><div class="box"><h3>Doanh thu đã thu theo ngày</h3><div class="bars">${revByDay.map((v,i)=>`<div><span style="height:${v/mx*110}px" title="${vnd(v)}"></span>${DAYS[i]}</div>`).join('')}</div></div>
<div class="box"><h3>Phân bố trạng thái phiếu</h3>${ST.map((s,i)=>({s,i,n:O.filter(o=>o.st==i).length})).filter(x=>x.n).map(x=>`<div style="display:flex;justify-content:space-between;padding:4px 0">${tag(x.i)}<b>${x.n}</b></div>`).join('')}</div></div>
<div class="two"><div class="box"><h3>Xe đang sửa chữa</h3><ul class="l">${O.filter(o=>o.st==3||o.st==4).map(o=>`<li><span><b>${o.plate}</b> · ${o.task}</span><span>${o.tech}</span></li>`).join('')}</ul></div>
<div class="box"><h3>Lịch hẹn sắp tới</h3><ul class="l">${A.map(a=>`<li><span>${a[0]} · ${a[1]}</span><span class="tag ${a[4]=='Đã xác nhận'?'ok':'warn'}">${a[4]}</span></li>`).join('')}</ul><h3 style="margin-top:14px">Cảnh báo tồn kho thấp</h3><ul class="l">${P.filter(p=>p[4]<=p[5]).map(p=>`<li><span>${p[1]}</span><span class="tag bad">${p[4]}/${p[5]}</span></li>`).join('')||'<li>Không có cảnh báo</li>'}</ul></div></div>`},
veh(){const r=srt(V).filter(v=>match(...v));return`<div class="bar"><button class="t" onclick="toast('Biểu mẫu thêm khách hàng: chưa triển khai trong bản demo',1)">+ Thêm khách hàng</button><button onclick="toast('Biểu mẫu thêm phương tiện: chưa triển khai trong bản demo',1)">+ Thêm phương tiện</button><span class="sp"></span><small style="color:var(--mu)">Nhấn tiêu đề cột để sắp xếp</small></div>`+table(['Biển số','Hãng','Dòng xe','Năm SX','Chủ xe','Điện thoại','Bảo dưỡng gần nhất','Trạng thái'],r.map(v=>{const o=O.find(o=>o.plate==v[0]);return`<tr><td><b>${v[0]}</b></td><td>${v[1]}</td><td>${v[2]}</td><td>${v[3]}</td><td>${v[4]}</td><td>${v[5]}</td><td>${v[6]}</td><td>${o?tag(o.st):'<span class="tag">Không có phiếu</span>'}</td></tr>`}))},
ord(){const r=O.filter(o=>match(o.id,o.plate,o.cust,o.task));
const seg=`<div class="bar"><div class="seg"><button class="${mode=='kb'?'on':''}" onclick="mode='kb';render()">Kanban</button><button class="${mode=='tb'?'on':''}" onclick="mode='tb';render()">Bảng</button></div><span class="sp"></span><small style="color:var(--mu)">Kéo thả thẻ để đổi trạng thái, hoặc mở phiếu để chọn trạng thái bằng bàn phím</small><button class="p" onclick="newOrder()">+ Tiếp nhận xe</button></div>`;
if(mode=='tb')return seg+table(['Mã phiếu','Biển số','Khách hàng','Hạng mục','KTV','Dự kiến xong','Chi phí dự kiến','Trạng thái',''],r.map(o=>`<tr><td><b>${o.id}</b></td><td>${o.plate}</td><td>${o.cust}</td><td>${o.task}</td><td>${o.tech}</td><td>${o.due}</td><td>${vnd(o.cost)}</td><td>${tag(o.st)}</td><td><button onclick="openO('${o.id}')">Xem</button></td></tr>`));
return seg+`<div class="kb">${ST.map((s,i)=>`<div class="col" data-i="${i}" ondragover="event.preventDefault();this.classList.add('over')" ondragleave="this.classList.remove('over')" ondrop="drop(event,${i})"><h4>${s}<span>${r.filter(o=>o.st==i).length}</span></h4>${r.filter(o=>o.st==i).map(o=>`<div class="card pr ${o.pr}" draggable="true" tabindex=0 ondragstart="event.dataTransfer.setData('t','${o.id}');this.classList.add('drag')" ondragend="this.classList.remove('drag')" onclick="openO('${o.id}')" onkeydown="if(event.key=='Enter')openO('${o.id}')"><b><span class="dot ${tl(o)}" title="Xanh: xong · Cam: đang xử lý · Đỏ: cần chú ý"></span>${o.id} · ${o.plate}</b><small>${o.cust}</small>${o.task}<small>KTV ${o.tech} · Hạn: ${o.due}${o.pr=='cao'?' · <span style="color:var(--rd)">Ưu tiên cao</span>':''}</small></div>`).join('')}</div>`).join('')}</div>`},
apt(){return`<div class="bar"><button class="t" onclick="toast('Tạo lịch hẹn: chưa triển khai trong bản demo',1)">+ Tạo lịch hẹn</button></div>`+table(['Giờ','Khách hàng','Biển số','Nhu cầu','Trạng thái'],A.filter(a=>match(...a)).map(a=>`<tr><td>${a[0]}</td><td>${a[1]}</td><td>${a[2]}</td><td>${a[3]}</td><td><span class="tag ${a[4]=='Đã xác nhận'?'ok':'warn'}">${a[4]}</span></td></tr>`))},
inv(){return`<div class="bar"><small style="color:var(--mu)">Số lượng tồn chỉ thay đổi khi ghi nhận nhập/xuất kho có xác nhận.</small></div>`+table(['Mã','Tên phụ tùng','Danh mục','ĐVT','Tồn','Tối thiểu','Giá nhập','Vị trí','Trạng thái'],P.filter(p=>match(...p)).map(p=>`<tr><td>${p[0]}</td><td><b>${p[1]}</b></td><td>${p[2]}</td><td>${p[3]}</td><td>${p[4]}</td><td>${p[5]}</td><td>${vnd(p[6])}</td><td>${p[7]}</td><td><span class="tag ${p[4]<=p[5]?'bad':'ok'}">${p[4]<=p[5]?'Sắp hết':'Đủ hàng'}</span></td></tr>`))},
stf(){const S=[['NV01','Hùng','Kỹ thuật viên','Máy gầm'],['NV02','Tuấn','Kỹ thuật viên','Bảo dưỡng'],['NV03','Long','Kỹ thuật viên','Điện – chẩn đoán'],['NV04','Phúc','Kỹ thuật viên','Đồng sơn'],['NV05','Thảo','Cố vấn dịch vụ','Tiếp nhận']];
return table(['Mã NV','Họ tên','Vai trò','Chuyên môn','Phiếu đang phụ trách'],S.map(s=>`<tr><td>${s[0]}</td><td><b>${s[1]}</b></td><td>${s[2]}</td><td>${s[3]}</td><td>${O.filter(o=>o.tech==s[1]&&o.st<7).length}</td></tr>`))+`<p style="color:var(--mu)">Lưu ý: phân quyền thực sự phải được kiểm soát ở máy chủ khi triển khai.</p>`},
bil(){return table(['Mã HĐ','Mã phiếu','Khách hàng','Tổng tiền','Đã thanh toán','Còn lại','Trạng thái'],I.filter(x=>match(...x)).map(x=>{const c=x[4]-x[5];return`<tr><td><b>${x[0]}</b></td><td>${x[1]}</td><td>${x[2]}</td><td>${vnd(x[4])}</td><td>${vnd(x[5])}</td><td>${vnd(c)}</td><td><span class="tag ${c?'warn':'ok'}">${c?'Còn nợ':'Đã thanh toán'}</span></td></tr>`}))},
rep(){const rev=I.reduce((s,x)=>s+x[5],0),debt=I.reduce((s,x)=>s+x[4]-x[5],0);return`<div class="grid"><div class="k"><small>Tổng thu 7 ngày</small><b style="font-size:19px">${vnd(rev)}</b></div><div class="k"><small>Công nợ chưa thu</small><b style="font-size:19px">${vnd(debt)}</b></div><div class="k"><small>Phiếu đã hoàn thành/bàn giao</small><b>${O.filter(o=>o.st>=6).length}/${O.length}</b></div></div><div class="box"><h3>Doanh thu theo ngày</h3><div class="bars">${revByDay.map((v,i)=>`<div><span style="height:${v/Math.max(...revByDay,1)*110}px"></span>${DAYS[i]}<br>${(v/1e6).toFixed(2)}tr</div>`).join('')}</div></div>`},
set(){return`<div class="box empty">Phần Cài đặt (thông tin gara, danh mục, vai trò, thông báo) chưa được triển khai trong bản demo này.</div>`}};
function drop(e,to){e.preventDefault();document.querySelectorAll('.col').forEach(c=>c.classList.remove('over'));move(e.dataTransfer.getData('t'),to)}
function move(id,to){const o=O.find(x=>x.id==id);if(o.st==to)return true;
 if(to==7&&o.st!=6){toast('Không thể bàn giao: phiếu '+id+' chưa ở trạng thái Hoàn thành.',1);return false}
 if(o.st==7){toast('Phiếu đã bàn giao, không thể đổi trạng thái.',1);return false}
 const f=ST[o.st];o.st=to;toast(`${id}: ${f} → ${ST[to]}`);render();return true}
function openO(id){const o=O.find(x=>x.id==id),v=V.find(x=>x[0]==o.plate);
$('#mo').innerHTML=`<div class="mod" onclick="if(event.target==this)closeM()"><div class="dlg" role="dialog" aria-modal="true"><h2>${o.id} ${tag(o.st)}</h2><div class="row"><div><small>Khách hàng</small>${o.cust}</div><div><small>Phương tiện</small>${o.plate}${v?' · '+v[1]+' '+v[2]:''}</div><div><small>Hạng mục</small>${o.task}</div><div><small>Kỹ thuật viên</small>${o.tech}</div><div><small>Dự kiến xong</small>${o.due}</div><div><small>Chi phí dự kiến</small>${vnd(o.cost)}</div></div>
<label>Cập nhật trạng thái<select id="ns">${ST.map((s,i)=>`<option value="${i}" ${i==o.st?'selected':''}>${s}</option>`).join('')}</select></label>
<div class="bar"><button class="t" onclick="if(move('${o.id}',+$('#ns').value))closeM()">Lưu trạng thái</button>${o.st==6?`<button class="p" onclick="if(move('${o.id}',7))closeM()">Ghi nhận bàn giao</button>`:o.st<6?`<button onclick="if(move('${o.id}',6))closeM()">Đánh dấu hoàn thành</button>`:''}<span class="sp"></span><button onclick="closeM()">Đóng</button></div></div></div>`;$('#ns').focus()}
function closeM(){$('#mo').innerHTML=''}
function newOrder(){$('#mo').innerHTML=`<div class="mod" onclick="if(event.target==this)closeM()"><div class="dlg"><h2>Tiếp nhận xe</h2><label>Biển số xe *<input id="f1" placeholder="VD: 51H-123.45"><span class="err" id="e1"></span></label><label>Tên khách hàng *<input id="f2"><span class="err" id="e2"></span></label><label>Hạng mục / mô tả lỗi *<input id="f3"></label><div class="bar"><button class="t" onclick="saveO()">Tạo phiếu</button><button onclick="closeM()">Hủy</button></div></div></div>`;$('#f1').focus()}
function saveO(){const p=$('#f1').value.trim().toUpperCase(),c=$('#f2').value.trim(),t=$('#f3').value.trim();let ok=1;
 $('#e1').textContent=/^\d{2}[A-Z]-?\d{3}\.?\d{2}$/.test(p)?'':(ok=0,'Biển số chưa đúng định dạng.');
 $('#e2').textContent=c?'':(ok=0,'Vui lòng nhập tên khách hàng.');if(!t)ok=0;if(!ok)return;
 O.unshift({id:'PSC-0'+(422+O.length-9),plate:p,cust:c,task:t,tech:'Chưa phân công',pr:'th',due:'Chưa có',st:0,cost:0});closeM();toast('Đã tạo phiếu mới.');go('ord')}
$('#q').oninput=e=>{q=e.target.value;if(view=='dash'){go('ord')}else render()};
$('#bell').onclick=()=>toast('Có '+P.filter(p=>p[4]<=p[5]).length+' phụ tùng sắp hết hàng.');
document.addEventListener('keydown',e=>{if((e.ctrlKey||e.metaKey)&&e.key=='k'){e.preventDefault();$('#q').focus()}if(e.key=='Escape')closeM()});
render();
</script></body></html>

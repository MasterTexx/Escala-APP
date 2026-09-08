[escala-pwa.html](https://github.com/user-attachments/files/31948651/escala-pwa.html)
<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Escalas">
<meta name="theme-color" content="#1F4E79">
<title>Gestão de Escalas</title>
<link rel="apple-touch-icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='20' fill='%231F4E79'/><text y='72' x='50' font-size='60' text-anchor='middle'>📋</text></svg>">
<style>
:root{--navy:#1F4E79;--blue:#2E75B6;--lbl:#D6E4F7;--sun:#FFCCCC;--hol:#FF9999;--man:#FFF9C4;--lck:#E8F0FB;--emp:#FFF3E0;--grn:#E8F5E9;--gdk:#2e7d32;--red:#FFEBEE;--rdk:#c62828;--ylw:#FFF8E1;--org:#e65100;--gry:#F8F9FA}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{height:100%;overflow:hidden;font-family:-apple-system,BlinkMacSystemFont,'SF Pro Text','Helvetica Neue',Arial,sans-serif;font-size:14px;background:#f0f4f8;color:#1a1a1a}
#app{display:flex;flex-direction:column;height:100%;height:100dvh}
/* HEADER */
.hdr{background:var(--navy);color:white;padding:env(safe-area-inset-top,0px) 16px 10px;display:flex;align-items:flex-end;justify-content:space-between;min-height:calc(52px + env(safe-area-inset-top,0px));flex-shrink:0}
.hdr h1{font-size:17px;font-weight:600;letter-spacing:-.3px}
.hdr .sub{font-size:11px;opacity:.75;margin-top:1px}
.hdr-right{display:flex;align-items:center;gap:6px}
/* BOTTOM NAV (iOS style) */
.bnav{display:flex;background:white;border-top:0.5px solid #ddd;padding-bottom:env(safe-area-inset-bottom,0px);flex-shrink:0;box-shadow:0 -1px 0 rgba(0,0,0,.1)}
.bnav button{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:8px 4px 6px;background:none;border:none;cursor:pointer;font-size:10px;color:#8e8e93;gap:3px;min-height:50px;transition:color .15s}
.bnav button.on{color:var(--blue)}
.bnav button .icon{font-size:22px;line-height:1}
/* CONTENT */
.pg{flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;padding:14px 14px calc(8px + env(safe-area-inset-bottom,0px));overscroll-behavior:contain}
/* CARDS */
.card{background:white;border-radius:12px;padding:14px;margin-bottom:12px;box-shadow:0 1px 3px rgba(0,0,0,.1)}
.card h3{font-size:15px;font-weight:600;margin-bottom:10px;color:var(--navy)}
/* BUTTONS */
button.pri{background:var(--blue);color:white;border:none;padding:10px 18px;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;min-height:44px}
button.sec{background:#E8F0FB;color:var(--blue);border:none;padding:10px 18px;border-radius:10px;font-size:14px;cursor:pointer;min-height:44px}
button.sml{background:#f0f0f5;color:#1a1a1a;border:none;padding:7px 14px;border-radius:8px;font-size:13px;cursor:pointer;min-height:36px}
button.dng{background:#FFEBEE;color:var(--rdk);border:none;padding:7px 14px;border-radius:8px;font-size:13px;cursor:pointer}
button:active{opacity:.7}
button:disabled{opacity:.35;cursor:default}
/* INPUTS */
select,input{font-family:inherit;font-size:16px;padding:10px 12px;border:1px solid #ddd;border-radius:10px;background:white;color:#1a1a1a;width:100%;min-height:44px;-webkit-appearance:none;appearance:none}
/* TABLE */
.tbl-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch;border-radius:10px;box-shadow:0 1px 3px rgba(0,0,0,.1)}
table{border-collapse:collapse;width:100%;font-size:12px;min-width:340px;background:white}
th{background:var(--navy);color:white;padding:9px 8px;font-size:11px;font-weight:500;text-align:left;white-space:nowrap}
td{padding:8px 8px;border-bottom:0.5px solid #f0f0f0;vertical-align:middle}
tr:last-child td{border-bottom:none}
/* ALERTS */
.al{border-radius:10px;padding:10px 13px;font-size:13px;margin-bottom:10px;line-height:1.5;white-space:pre-wrap}
.al.e{background:#FFEBEE;color:#c62828}
.al.ok{background:#E8F5E9;color:#2e7d32}
.al.w{background:#FFF8E1;color:#e65100}
.al.i{background:#E3F2FD;color:#1565C0}
/* TAGS */
.tg{display:inline-block;font-size:10px;padding:2px 7px;border-radius:10px;font-weight:500}
.tg.ok{background:#E8F5E9;color:#2e7d32}
.tg.e{background:#FFEBEE;color:#c62828}
.tg.w{background:#FFF8E1;color:#e65100}
.tg.i{background:#E3F2FD;color:#1565C0}
/* STAT */
.stats{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;-webkit-overflow-scrolling:touch}
.stat{background:white;border-radius:10px;padding:12px 14px;text-align:center;min-width:70px;box-shadow:0 1px 3px rgba(0,0,0,.1);flex-shrink:0}
.stat .v{font-size:22px;font-weight:600;line-height:1}
.stat .l{font-size:10px;color:#8e8e93;margin-top:3px}
/* ROW */
.row{display:flex;gap:8px;flex-wrap:wrap;align-items:center}
/* OVERLAY */
.ov{position:fixed;inset:0;background:rgba(0,0,0,.5);display:flex;align-items:flex-end;justify-content:center;z-index:200;-webkit-backdrop-filter:blur(4px);backdrop-filter:blur(4px)}
.sheet{background:white;border-radius:20px 20px 0 0;padding:20px 20px calc(20px + env(safe-area-inset-bottom,0px));width:100%;max-height:85vh;overflow-y:auto}
.sheet-handle{width:36px;height:4px;background:#e0e0e0;border-radius:2px;margin:0 auto 16px}
/* MONTH NAV */
.mnav{display:flex;align-items:center;gap:8px}
.mnav button{background:#E8F0FB;color:var(--blue);border:none;width:36px;height:36px;border-radius:10px;font-size:18px;display:flex;align-items:center;justify-content:center;cursor:pointer}
.mnav span{font-size:15px;font-weight:600;color:var(--navy);min-width:130px;text-align:center}
/* CALENDAR GRID */
.mcal{display:grid;grid-template-columns:repeat(7,1fr);gap:3px;margin-bottom:10px}
.mcal .dh{text-align:center;font-size:10px;color:#8e8e93;font-weight:500;padding:3px 0}
.mcal .dc{aspect-ratio:1;display:flex;align-items:center;justify-content:center;border-radius:8px;font-size:13px;cursor:pointer;border:1px solid transparent}
.mcal .dc.vac{background:#FFEBEE;color:#c62828;font-weight:500}
.mcal .dc.ud{background:#FFF8E1;color:#e65100}
.mcal .dc.we{background:#f5f5f5;color:#c7c7cc}
.mcal .dc.hol{background:#FFEBEE;color:#c62828;border-color:#c62828}
/* TABLE CELLS */
.cemp{background:var(--emp)!important}
.clk{background:var(--lck)!important}
.cman{background:var(--man)!important}
.csat{background:var(--lbl)!important}
.csun{background:var(--sun)!important}
.chol{background:var(--hol)!important}
.chl{background:#FFF9C4!important}
/* PERSON PICKER */
.ppick{display:flex;flex-direction:column;gap:6px;max-height:55vh;overflow-y:auto}
.ppick button{text-align:left;padding:12px 14px;background:#f8f8f8;border:none;border-radius:10px;cursor:pointer;font-size:14px;display:flex;justify-content:space-between;align-items:center;min-height:48px}
.ppick button:active{background:#E8F0FB}
/* SEARCH */
.search{width:100%;padding:10px 12px;border:1px solid #ddd;border-radius:10px;font-size:16px;margin-bottom:10px;background:#f8f8f8}
/* VIABILITY BAR */
.vbar{background:white;border-radius:10px;padding:11px 13px;margin-bottom:10px;display:flex;align-items:center;gap:10px;box-shadow:0 1px 3px rgba(0,0,0,.08)}
.vbar .dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}
.vbar .dot.ok{background:#34c759}
.vbar .dot.err{background:#ff3b30}
/* SECTION TABS */
.stabs{display:flex;background:#f0f4f8;border-radius:10px;padding:3px;margin-bottom:12px;gap:2px}
.stabs button{flex:1;padding:7px 4px;background:none;border:none;border-radius:8px;font-size:12px;color:#8e8e93;cursor:pointer;font-weight:500}
.stabs button.on{background:white;color:var(--navy);box-shadow:0 1px 3px rgba(0,0,0,.15)}
/* IOS ACTION BUTTON */
.fab{position:fixed;right:16px;bottom:calc(70px + env(safe-area-inset-bottom,0px));width:56px;height:56px;border-radius:28px;background:var(--blue);color:white;border:none;font-size:24px;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 16px rgba(46,117,182,.4);cursor:pointer;z-index:10}
</style>
</head>
<body>
<div id="app"></div>
<script>
// ══ CONSTANTES ══
const SHK=['morning','midday','afternoon'];
const SHN={morning:'Manhã',midday:'Intermédio',afternoon:'Tarde'};
const SHT={morning:'09:00–13:00',midday:'13:00–16:00',afternoon:'16:00–19:00'};
const MNS=['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto','Setembro','Outubro','Novembro','Dezembro'];
const WDS=['D','S','T','Q','Q','S','S'];
const WDF=['Domingo','Segunda-feira','Terça-feira','Quarta-feira','Quinta-feira','Sexta-feira','Sábado'];
const SAVE='escala_ios_v1';

// ══ CALENDÁRIO ══
const dim=(y,m)=>new Date(y,m,0).getDate();
const dwd=d=>{const[y,mo,dd]=d.split('-').map(Number);return new Date(y,mo-1,dd).getDay();};
const fpt=d=>{if(!d)return'';const[y,m,dd]=d.split('-');return`${dd}/${m}`;};
const fptFull=d=>{if(!d)return'';const[y,m,dd]=d.split('-');return`${dd}/${m}/${y}`;};
const mk=(y,m)=>`${y}-${String(m).padStart(2,'0')}`;
const mds=(y,m)=>Array.from({length:dim(y,m)},(_,i)=>`${y}-${String(m).padStart(2,'0')}-${String(i+1).padStart(2,'0')}`);
const wdays=(y,m,h)=>mds(y,m).filter(d=>{const w=dwd(d);return w>=1&&w<=5&&!h.includes(d);});
const satsOf=(y,m)=>mds(y,m).filter(d=>dwd(d)===6);
const dst=(d,h)=>{const w=dwd(d);return w===0?'sun':w===6?h.includes(d)?'hol':'sat':h.includes(d)?'hol':'work';};
const wom=(d,y,m)=>{const dt=new Date(d+'T12:00:00'),f=new Date(y,m-1,1),fw=f.getDay(),off=fw===0?1:fw===1?0:-(fw-1),fm=new Date(y,m-1,1+off);return Math.floor((dt-fm)/86400000/7)+1;};
const consec=(a,b)=>Math.abs(new Date(a+'T12:00:00')-new Date(b+'T12:00:00'))/86400000===1;
const d2ms=d=>{const[y,m,dd]=d.split('-').map(Number);return new Date(y,m-1,dd).getTime();};
const defHols=(y,m)=>[`${y}-01-01`,`${y}-04-25`,`${y}-05-01`,`${y}-06-10`,`${y}-08-15`,`${y}-10-05`,`${y}-11-01`,`${y}-12-01`,`${y}-12-08`,`${y}-12-25`].filter(d=>parseInt(d.slice(5,7))===m);

// ══ ENGINE ══
const effQ=(p,c)=>p.active?(c.qov[p.id]??p.quota):0;
const unavail=(p,d,h)=>!p.active||(p.vac||[]).includes(d)||(p.ud||[]).includes(d)||(p.uwd||[]).includes(dwd(d));

function feasi(people,cfg){
  const wd=wdays(cfg.y,cfg.m,cfg.h),total=wd.length*3;
  const ac=people.filter(p=>p.active&&effQ(p,cfg)>0);
  const tq=ac.reduce((s,p)=>s+effQ(p,cfg),0),sur=tq-total;
  const msgs=[];
  if(sur!==0)msgs.push(sur>0?`Quotas totalizam ${tq} mas existem apenas ${total} vagas.\nReduz as quotas em ${sur}.`:`Quotas somam apenas ${tq} mas existem ${total} vagas.\nAumenta as quotas em ${Math.abs(sur)}.`);
  for(const p of ac){const q=effQ(p,cfg),av=wd.filter(d=>!unavail(p,d,cfg.h));if(av.length<q)msgs.push(`${p.name}: quota ${q} mas só ${av.length} dias disponíveis.`);}
  return{ok:sur===0&&msgs.length===0,wd:wd.length,total,tq,sur,msgs};
}

function gSlots(y,m,h){const r=[];wdays(y,m,h).forEach((d,i)=>{const w=dwd(d),wo=wom(d,y,m);SHK.forEach(sh=>r.push({date:d,shift:sh,dow:w,wom:wo}));});return r;}
const mulb=s=>{let t=s>>>0;return()=>{t+=0x6d2b79f5;let r=Math.imul(t^(t>>>15),t|1);r^=r+Math.imul(r^(r>>>7),r|61);return((r^(r>>>14))>>>0)/4294967296;};};
const shuf=(a,rng)=>{const r=[...a];for(let i=r.length-1;i>0;i--){const j=Math.floor(rng()*(i+1));[r[i],r[j]]=[r[j],r[i]];}return r;};

function solve(people,cfg,opts={}){
  const t0=Date.now(),rng=mulb(opts.alt?(opts.seed??cfg.seed)+999983:(opts.seed??cfg.seed));
  const maxIt=opts.alt?60000:500000,stopSc=opts.alt?3000:1000;
  const ac=people.filter(p=>p.active&&effQ(p,cfg)>0);
  const allS=gSlots(cfg.y,cfg.m,cfg.h);
  const locked=(opts.locked||[]).filter(a=>a.locked);
  const lkK=new Set(locked.map(a=>`${a.date}::${a.shift}`));
  const open=allS.filter(s=>!lkK.has(`${s.date}::${s.shift}`));
  const rq=new Map(ac.map(p=>[p.id,effQ(p,cfg)]));
  const ams=new Map(ac.map(p=>[p.id,new Set()]));
  const ad=new Map(ac.map(p=>[p.id,[]]));
  const sbd=new Map(),wu=new Map(ac.map(p=>[p.id,new Set()])),wdu=new Map(ac.map(p=>[p.id,[]])),ag=new Map();
  for(const lk of locked){const sl=allS.find(s=>s.date===lk.date&&s.shift===lk.shift);if(!sl||!rq.has(lk.personId))continue;ag.set(`${lk.date}::${lk.shift}`,lk.personId);rq.set(lk.personId,rq.get(lk.personId)-1);ams.get(lk.personId).add(d2ms(lk.date));const da=ad.get(lk.personId);const i=da.findIndex(x=>x>lk.date);if(i<0)da.push(lk.date);else da.splice(i,0,lk.date);sbd.set(`${lk.personId}::${lk.date}`,lk.shift);wu.get(lk.personId).add(sl.wom);wdu.get(lk.personId).push(sl.dow);}
  const valid=(p,sl)=>{const pid=p.id;if((rq.get(pid)??0)<=0)return false;if(unavail(p,sl.date,cfg.h))return false;if((p.fs||[]).includes(sl.shift))return false;const ms=d2ms(sl.date),am=ams.get(pid);if(am.has(ms)||am.has(ms-86400000)||am.has(ms+86400000))return false;const dates=ad.get(pid);if(dates.length>0){let last=null,next=null;for(const d of dates){if(d<sl.date)last=d;else if(d>sl.date&&!next)next=d;}if(last&&!dates.some(d=>d>last&&d<sl.date)&&sbd.get(`${pid}::${last}`)===sl.shift)return false;if(next&&!dates.some(d=>d>sl.date&&d<next)&&sbd.get(`${pid}::${next}`)===sl.shift)return false;}return true;};
  const cst=(p,sl)=>{let c=0;if(wu.get(p.id).has(sl.wom))c+=2000;c+=wdu.get(p.id).filter(w=>w===sl.dow).length*200;c+=rng()*5;return c;};
  const aply=(pid,sl)=>{ag.set(`${sl.date}::${sl.shift}`,pid);rq.set(pid,rq.get(pid)-1);ams.get(pid).add(d2ms(sl.date));const da=ad.get(pid);const i=da.findIndex(x=>x>sl.date);if(i<0)da.push(sl.date);else da.splice(i,0,sl.date);sbd.set(`${pid}::${sl.date}`,sl.shift);wu.get(pid).add(sl.wom);wdu.get(pid).push(sl.dow);};
  const undo=(pid,sl)=>{ag.delete(`${sl.date}::${sl.shift}`);rq.set(pid,rq.get(pid)+1);ams.get(pid).delete(d2ms(sl.date));const da=ad.get(pid);da.splice(da.indexOf(sl.date),1);sbd.delete(`${pid}::${sl.date}`);const ws=wu.get(pid);ws.delete(sl.wom);for(const d of da)if(wom(d,cfg.y,cfg.m)===sl.wom){ws.add(sl.wom);break;}const wa=wdu.get(pid);wa.splice(wa.lastIndexOf(sl.dow),1);};
  const fchk=rem=>{for(const p of ac){const r=rq.get(p.id)??0;if(r===0)continue;if(r>rem.length)return false;if(r<=1&&rem.length>=3)continue;let c=0;for(const s of rem){if(valid(p,s)){c++;if(c>=r)break;}}if(c<r)return false;}return true;};
  const score=()=>{let s=0;const wm=new Map();for(const[k,pid]of ag){const[date,shift]=k.split('::');const sl=allS.find(x=>x.date===date&&x.shift===shift);if(!sl)continue;if(!wm.has(pid))wm.set(pid,new Map());const w=wm.get(pid);w.set(sl.wom,(w.get(sl.wom)??0)+1);}for(const[,w]of wm)for(const[,c]of w)if(c>1)s+=(c-1)*1000;return s;};
  const ord=[...open].sort((a,b)=>{const da=ac.filter(p=>valid(p,a)).length,db=ac.filter(p=>valid(p,b)).length;return da!==db?da-db:a.date.localeCompare(b.date);});
  let best=null,bestSc=Infinity,iters=0,aborted=false;
  const bt=idx=>{if(++iters>maxIt){aborted=true;return false;}if(idx===ord.length){const s=score();if(s<bestSc){bestSc=s;best=new Map(ag);}return bestSc<=stopSc;}const sl=ord[idx];const cands=shuf(ac.filter(p=>valid(p,sl)),rng).sort((a,b)=>cst(a,sl)-cst(b,sl));for(const p of cands){aply(p.id,sl);if(fchk(ord.slice(idx+1))){if(bt(idx+1))return true;if(aborted){undo(p.id,sl);return false;}}undo(p.id,sl);}return false;};
  bt(0);
  if(!best)return{ok:false,asgns:[],msg:'Não foi encontrada solução. Verifique restrições e quotas.',ms:Date.now()-t0};
  const res=[...locked];for(const[k,pid]of best){const[date,shift]=k.split('::');res.push({id:`${date}-${shift}`,date,shift,personId:pid,locked:false,manual:false});}
  return{ok:true,asgns:res,sc:bestSc,viol:aborted?['Limite de iterações']:[], ms:Date.now()-t0};
}

function valAll(people,cfg,asgns,satA){
  const errs=[],warns=[],pm=new Map(people.map(p=>[p.id,p]));
  const wd=wdays(cfg.y,cfg.m,cfg.h);
  for(const d of wd)for(const sh of SHK){const f=asgns.find(a=>a.date===d&&a.shift===sh);if(!f)errs.push({code:'EMPTY',msg:`Vaga vazia: ${fptFull(d)} — ${SHN[sh]}`});}
  const bd=new Map();for(const a of asgns){if(!bd.has(a.date))bd.set(a.date,[]);bd.get(a.date).push(a);}
  for(const[d,da]of bd){const seen=new Set();for(const a of da){if(seen.has(a.personId))errs.push({code:'DUP',msg:`${pm.get(a.personId)?.name??a.personId} duplicado em ${fptFull(d)}`});seen.add(a.personId);}}
  const bp=new Map();for(const a of asgns){if(!bp.has(a.personId))bp.set(a.personId,[]);bp.get(a.personId).push(a);}
  for(const[pid,pa]of bp){const p=pm.get(pid),dates=pa.map(a=>a.date).sort();
  for(let i=0;i<dates.length-1;i++)if(consec(dates[i],dates[i+1]))errs.push({code:'CONSEC',msg:`${p?.name??pid}: dias consecutivos`});
  const sorted=[...pa].sort((a,b)=>a.date.localeCompare(b.date));
  for(let i=0;i<sorted.length-1;i++)if(sorted[i].shift===sorted[i+1].shift)errs.push({code:'SAME_SH',msg:`${p?.name??pid}: turno ${SHN[sorted[i].shift]} repetido`});}
  for(const p of people){if(!p.active)continue;const q=effQ(p,cfg),n=asgns.filter(a=>a.personId===p.id).length;if(n!==q)errs.push({code:'QUOTA',msg:`${p.name}: quota ${q}, atribuído ${n}`});}
  for(const[pid,pa]of bp){const p=pm.get(pid),wm=new Map();for(const a of pa){const w=wom(a.date,cfg.y,cfg.m);wm.set(w,(wm.get(w)??0)+1);}for(const[w,c]of wm)if(c>1)warns.push({code:'WREP',msg:`${p?.name??pid}: ${c}× semana ${w}`});}
  return{valid:errs.length===0,errs,warns};
}

// ══ DADOS DEMO ══
const DEMO=[
  {id:'p1',name:'Ana Macias',active:true,quota:3},{id:'p2',name:'Cristina Cascais',active:true,quota:3},
  {id:'p3',name:'Diana Justino',active:true,quota:4},{id:'p4',name:'Elsa Torres Pereira',active:true,quota:4},
  {id:'p5',name:'Fátima Pessanha',active:true,quota:3},{id:'p6',name:'Fernando Cabral',active:true,quota:3},
  {id:'p7',name:'João Monteiro',active:true,quota:5},{id:'p8',name:'João Montenegro',active:true,quota:4},
  {id:'p9',name:'José Miranda',active:true,quota:4},{id:'p10',name:'José Pedreira',active:true,quota:4},
  {id:'p11',name:'Luís Gaspar',active:true,quota:3},{id:'p12',name:'Luís Parra',active:true,quota:4},
  {id:'p13',name:'Luís Santos',active:true,quota:3},{id:'p14',name:'Margarida Ramos',active:true,quota:3},
  {id:'p15',name:'Rosa Volcarte',active:true,quota:4},{id:'p16',name:'Rui Ferreira',active:true,quota:3},
  {id:'p17',name:'Vita Lains',active:true,quota:3},{id:'p18',name:'Maria Morbey Mesquita',active:true,quota:3},
].map(p=>({...p,vac:[],ud:[],uwd:[],fs:[],notes:''}));

// ══ ESTADO ══
const sst=()=>{try{localStorage.setItem(SAVE,JSON.stringify({people:S.people,months:S.months,y:S.y,m:S.m}));}catch(e){}};
const lst=()=>{try{const d=JSON.parse(localStorage.getItem(SAVE)||'null');if(d?.people){S.people=d.people;S.months=d.months||{};S.y=d.y||S.y;S.m=d.m||S.m;return true;}}catch(e){}return false;};
const now=new Date();
let S={people:JSON.parse(JSON.stringify(DEMO)),y:now.getFullYear(),m:now.getMonth()+1,admin:false,tab:'schedule',months:{},modal:null,editSlot:null,editErrs:[],genBusy:false,genStatus:null,myPerson:'',cfgSec:'people',_selP:'',satWarn:{},search:''};
lst();

function gmd(){
  const k=mk(S.y,S.m);
  if(!S.months[k]){const qov={};S.people.forEach(p=>qov[p.id]=p.quota);S.months[k]={cfg:{y:S.y,m:S.m,seed:S.y*100+S.m,h:defHols(S.y,S.m),satQ:false,qov},asgns:[],satA:satsOf(S.y,S.m).map(d=>({id:'s'+d,date:d,personId:null,locked:false})),hist:[]};}
  return S.months[mk(S.y,S.m)];
}
const gcfg=()=>gmd().cfg;
const addH=(desc,action='edit')=>{const md=gmd();md.hist.push({id:String(Date.now()),ts:new Date().toISOString(),action,desc});sst();};

// ══ RENDER ══
function R(){
  const app=document.getElementById('app');if(!app)return;
  const md=gmd(),cfg=md.cfg,mn=MNS[S.m-1];
  const v=md.asgns.length?valAll(S.people,cfg,md.asgns,md.satA):{valid:null,errs:[],warns:[]};

  app.innerHTML=`
  <div class="hdr">
    <div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:20px">📋</span><div><div><b>Gestão de Escalas</b></div><div class="sub">${mn} ${S.y}</div></div></div></div>
    <div class="hdr-right">
      ${S.admin?`<button onclick="S.admin=false;R()" style="background:rgba(255,255,255,.2);color:white;border:none;padding:6px 10px;border-radius:8px;font-size:11px">Sair Admin</button>`:`<button onclick="showLogin()" style="background:rgba(255,255,255,.2);color:white;border:none;padding:6px 10px;border-radius:8px;font-size:12px">🔒</button>`}
    </div>
  </div>
  <div class="pg" id="PG">
    ${S.tab==='schedule'?tSched(md,cfg):S.tab==='my'?tMy(md,cfg):S.tab==='summary'?tSum(md,cfg):S.tab==='config'?tCfg(md,cfg):S.tab==='saturdays'?tSats(md,cfg):tVal(md,cfg,v)}
  </div>
  <nav class="bnav">
    ${[['schedule','📅','Escala'],['saturdays','🗓','Sábados'],['my','👤','A Minha'],['summary','📊','Resumo'],['validation','✅','Validação'],['config','⚙️','Config']].map(([id,ic,lb])=>`<button class="${S.tab===id?'on':''}" onclick="sTab('${id}')"><span class="icon">${ic}</span>${lb}</button>`).join('')}
  </nav>
  ${S.modal?rModal():''}`;
}

// ══ ESCALA ══
function tSched(md,cfg){
  const f=feasi(S.people,cfg),pm=new Map(S.people.map(p=>[p.id,p]));
  let h=`<div class="mnav" style="margin-bottom:12px">
    <button onclick="pM()">◀</button>
    <span>${MNS[cfg.m-1]} ${cfg.y}</span>
    <button onclick="nM()">▶</button>
  </div>`;

  h+=`<div class="vbar"><div class="dot ${f.ok?'ok':'err'}"></div><div style="font-size:12px"><b>${f.ok?'Configuração viável':'Configuração inviável'}</b> — ${f.wd}×3=<b>${f.total}</b> vagas | Quotas: <b>${f.tq}</b>${f.sur!==0?` (${f.sur>0?'+':''}${f.sur})`:''}</div></div>`;
  if(!f.ok&&f.msgs.length)h+=`<div class="al e" style="margin-bottom:10px">${f.msgs.join('\n')}</div>`;
  if(S.genStatus)h+=`<div class="al ${S.genStatus.t}" style="margin-bottom:8px">${S.genStatus.msg}</div>`;

  h+=`<div class="row" style="margin-bottom:12px;gap:8px">
    <button class="pri" onclick="doGen(false)" ${S.genBusy?'disabled':''} style="flex:1">⚡ ${S.genBusy?'A gerar…':'Gerar'}</button>
    <button class="sec" onclick="doGen(true)" ${S.genBusy||!md.asgns.length?'disabled':''} style="flex:1">🔄 Alternativa</button>
  </div>
  <div class="row" style="margin-bottom:12px;gap:8px">
    <button class="sml" onclick="doPrint()" ${!md.asgns.length?'disabled':''}>🖨 Imprimir</button>
    <button class="sml" onclick="doExportJSON()">💾 Backup</button>
    <button class="sml" onclick="doImportJSON()">📥 Restaurar</button>
  </div>`;

  if(S.editSlot){
    h+=`<div class="al i" style="margin-bottom:8px">A editar: <b>${fptFull(S.editSlot.date)}</b> — ${SHN[S.editSlot.shift]}<br><button class="sml" onclick="S.editSlot=null;S.editErrs=[];R()" style="margin-top:6px">Cancelar</button></div>`;
    if(S.editErrs.length)h+=`<div class="al e" style="margin-bottom:8px">${S.editErrs.join('<br>')}</div>`;
    const acP=S.people.filter(p=>p.active&&effQ(p,gcfg())>0).sort((a,b)=>a.name.localeCompare(b.name));
    h+=`<div class="ppick">`;
    for(const p of acP){const q=effQ(p,gcfg()),n=md.asgns.filter(a=>a.personId===p.id).length;h+=`<button onclick="cEd('${p.id}')">${p.name}<span class="tg ${n>=q?'e':'ok'}">${n}/${q}</span></button>`;}
    h+=`</div>`;
    return h;
  }

  // Tabela compacta para mobile
  h+=`<div class="tbl-wrap"><table><tr><th>Data</th><th>Manhã</th><th>Interm.</th><th>Tarde</th></tr>`;
  for(const date of mds(cfg.y,cfg.m)){
    const st=dst(date,cfg.h),w=dwd(date);
    if(st==='sun'){h+=`<tr class="csun"><td style="font-size:11px">${fpt(date)} <span style="color:#c62828">Dom</span></td><td colspan="3" style="color:#c62828;font-size:11px;font-style:italic">Domingo</td></tr>`;continue;}
    if(st==='hol'){h+=`<tr class="chol"><td style="font-size:11px">${fpt(date)}</td><td colspan="3" style="color:#c62828;font-size:11px;font-style:italic">Feriado</td></tr>`;continue;}
    if(st==='sat'){h+=`<tr class="csat"><td style="font-size:11px">${fpt(date)} <span style="color:var(--blue);font-size:10px">sáb.</span></td><td colspan="3" style="color:var(--blue);font-size:11px;font-style:italic">→ Sábados</td></tr>`;continue;}
    h+=`<tr><td style="font-size:11px;font-weight:500">${fpt(date)}<br><span style="color:#8e8e93;font-weight:400;font-size:9px">${['','Seg','Ter','Qua','Qui','Sex',''][w]}</span></td>`;
    for(const sh of SHK){
      const a=md.asgns.find(x=>x.date===date&&x.shift===sh),p=a?pm.get(a.personId):null;
      const isEd=S.editSlot?.date===date&&S.editSlot?.shift===sh;
      let cls='',cont='';
      if(!a){cls='cemp';cont='<span style="color:#e65100;font-size:10px">vazio</span>';}
      else if(a.locked){cls='clk';cont=`<span style="font-size:10px">${p?.name?.split(' ')[0]||'?'} 🔒</span>`;}
      else if(a.manual){cls='cman';cont=`<span style="font-size:10px">${p?.name?.split(' ')[0]||'?'} ✏</span>`;}
      else{cont=`<span style="font-size:11px">${p?.name?.split(' ')[0]||'?'}</span>`;}
      const click=S.admin&&!a?.locked?`eSl('${date}','${sh}')`:null;
      h+=`<td class="${cls}" onclick="${click||''}" style="${click?'cursor:pointer':''}">${cont}</td>`;
    }
    h+=`</tr>`;
  }
  h+=`</table></div>`;
  return h;
}

// ══ SÁBADOS ══
function tSats(md,cfg){
  const ss=satsOf(cfg.y,cfg.m),pm=new Map(S.people.map(p=>[p.id,p]));
  const ac=S.people.filter(p=>p.active).sort((a,b)=>a.name.localeCompare(b.name));
  let h=`<div class="mnav" style="margin-bottom:12px"><button onclick="pM()">◀</button><span>Sábados ${MNS[cfg.m-1]}</span><button onclick="nM()">▶</button></div>`;
  h+=`<div class="tbl-wrap"><table><tr><th>Data</th><th>Nome</th><th>Estado</th></tr>`;
  for(const date of ss){
    const isH=cfg.h.includes(date),sa=(md.satA||[]).find(x=>x.date===date),person=sa?.personId?pm.get(sa.personId):null;
    h+=`<tr class="${isH?'chol':'csat'}"><td style="font-size:12px;font-weight:500">${fptFull(date)}</td><td>`;
    if(isH)h+=`<span style="color:#c62828;font-size:12px">FERIADO</span>`;
    else h+=`<select onchange="asgSat('${date}',this.value)" style="font-size:12px;min-height:36px"><option value="">—</option>${ac.map(p=>`<option value="${p.id}" ${sa?.personId===p.id?'selected':''}>${p.name}</option>`).join('')}</select>`;
    h+=`</td><td>${isH?`<span class="tg e">Feriado</span>`:person?`<span class="tg ok">✅</span>`:`<span class="tg w">⚠</span>`}</td></tr>`;
    if((S.satWarn||{})[date])h+=`<tr><td colspan="3" style="background:#FFEBEE;color:#c62828;font-size:11px;padding:5px 8px">${S.satWarn[date].join(' · ')}</td></tr>`;
  }
  h+=`</table></div>`;
  return h;
}

// ══ A MINHA ESCALA ══
function tMy(md,cfg){
  const ac=S.people.filter(p=>p.active).sort((a,b)=>a.name.localeCompare(b.name));
  const p=S.myPerson?S.people.find(x=>x.id===S.myPerson):null;
  const myA=p?md.asgns.filter(a=>a.personId===p.id).sort((a,b)=>a.date.localeCompare(b.date)):[];
  const mySat=p?(md.satA||[]).filter(s=>s.personId===p.id).sort((a,b)=>a.date.localeCompare(b.date)):[];
  const q=p?(cfg.qov[p.id]??p.quota):0,def=q-myA.length;
  let h=`<div style="font-size:16px;font-weight:600;margin-bottom:12px;color:var(--navy)">A Minha Escala</div>
  <div class="card">
    <label style="font-size:13px;font-weight:500;display:block;margin-bottom:8px">Seleciona o teu nome:</label>
    <select onchange="S.myPerson=this.value;R()" style="font-size:15px">
      <option value="">— Seleciona —</option>
      ${ac.map(p=>`<option value="${p.id}" ${p.id===S.myPerson?'selected':''}>${p.name}</option>`).join('')}
    </select>
  </div>`;
  if(p){
    h+=`<div class="stats" style="margin-bottom:12px">`;
    [{l:'Quota',v:q},{l:'Atribuído',v:myA.length},{l:'Sábados',v:mySat.length},{l:'Manhãs',v:myA.filter(a=>a.shift==='morning').length},{l:'Interm.',v:myA.filter(a=>a.shift==='midday').length},{l:'Tardes',v:myA.filter(a=>a.shift==='afternoon').length}].forEach(({l,v})=>h+=`<div class="stat"><div class="v">${v}</div><div class="l">${l}</div></div>`);
    h+=`</div>`;
    if(!myA.length&&!mySat.length){h+=`<div class="al w">${p.name} não tem escalas em ${MNS[cfg.m-1]} ${cfg.y}.</div>`;}
    else{
      // Próxima escala em destaque
      const all=[...myA,...mySat.map(sa=>({...sa,shift:'sat'}))].filter(a=>a.date>=new Date().toISOString().slice(0,10)).sort((a,b)=>a.date.localeCompare(b.date));
      if(all.length){const next=all[0];h+=`<div class="card" style="background:linear-gradient(135deg,#1F4E79,#2E75B6);color:white;margin-bottom:12px"><div style="font-size:11px;opacity:.8;margin-bottom:4px">Próxima escala</div><div style="font-size:20px;font-weight:600">${fptFull(next.date)}</div><div style="font-size:14px;margin-top:4px">${next.shift==='sat'?'Sábado 09:00–13:00':SHN[next.shift]+' · '+SHT[next.shift]}</div></div>`;}
      if(myA.length){
        h+=`<div class="card"><div style="font-weight:600;font-size:14px;margin-bottom:10px">Dias úteis (${myA.length})</div>`;
        const sc={morning:'#E3F2FD',midday:'#F3E5F5',afternoon:'#FFF3E0'};
        for(const a of myA)h+=`<div style="display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:0.5px solid #f0f0f0"><div><div style="font-weight:500;font-size:14px">${fptFull(a.date)}</div><div style="font-size:12px;color:#8e8e93">${WDF[dwd(a.date)]}</div></div><div style="background:${sc[a.shift]};padding:6px 12px;border-radius:8px;font-size:13px;font-weight:500">${SHN[a.shift]}<br><span style="font-size:11px;font-weight:400">${SHT[a.shift]}</span></div></div>`;
        h+=`</div>`;
      }
      if(mySat.length){
        h+=`<div class="card"><div style="font-weight:600;font-size:14px;margin-bottom:10px">Sábados (${mySat.length})</div>`;
        for(const sa of mySat)h+=`<div style="display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:0.5px solid #f0f0f0"><div style="font-weight:500;font-size:14px">${fptFull(sa.date)}</div><div style="background:#D6E4F7;padding:6px 12px;border-radius:8px;font-size:13px;font-weight:500">09:00–13:00</div></div>`;
        h+=`</div>`;
      }
    }
    h+=`<button class="sml" onclick="printIndividual('${p.id}')" style="width:100%;margin-top:4px">🖨 Imprimir a minha escala</button>`;
  }
  return h;
}

// ══ RESUMO ══
function tSum(md,cfg){
  const stats=S.people.filter(p=>p.active).map(p=>{
    const q=effQ(p,cfg),pa=md.asgns.filter(a=>a.personId===p.id),n=pa.length,def=q-n;
    const ss=(md.satA||[]).filter(s=>s.personId===p.id).length;
    return{id:p.id,name:p.name,q,n,def,ss,st:def!==0?'e':'ok'};
  }).sort((a,b)=>a.name.localeCompare(b.name));
  const tq=stats.reduce((s,p)=>s+p.q,0),ta=stats.reduce((s,p)=>s+p.n,0);
  let h=`<div style="font-size:16px;font-weight:600;margin-bottom:12px;color:var(--navy)">Resumo — ${MNS[cfg.m-1]} ${cfg.y}</div>
  <div class="stats" style="margin-bottom:12px">`;
  [{l:'Total quotas',v:tq},{l:'Atribuído',v:ta},{l:'Erros',v:stats.filter(p=>p.st==='e').length}].forEach(({l,v})=>h+=`<div class="stat"><div class="v">${v}</div><div class="l">${l}</div></div>`);
  h+=`</div>`;
  for(const s of stats){
    const ds=s.def===0?'✓':s.def>0?`−${s.def}`:`+${Math.abs(s.def)}`;
    h+=`<div class="card" style="padding:12px 14px;${s.st==='e'?'border-left:3px solid #c62828':'border-left:3px solid #34c759'}">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <div style="font-weight:600;font-size:14px">${s.name}</div>
        <span class="tg ${s.st==='ok'?'ok':'e'}">${ds}</span>
      </div>
      <div class="row" style="margin-top:6px;gap:8px;font-size:12px;color:#8e8e93">
        <span>Quota: ${s.q}</span><span>Atribuído: ${s.n}</span><span>Sábados: ${s.ss}</span>
      </div>
    </div>`;
  }
  return h;
}

// ══ VALIDAÇÃO ══
function tVal(md,cfg,v){
  let h=`<div style="font-size:16px;font-weight:600;margin-bottom:12px;color:var(--navy)">Validação</div>`;
  if(!md.asgns.length)return h+`<div class="al w">Escala ainda não gerada.</div>`;
  h+=`<div class="card" style="background:${v.valid?'#E8F5E9':'#FFEBEE'};border:none;margin-bottom:12px"><div style="font-size:18px;font-weight:600;color:${v.valid?'#2e7d32':'#c62828'}">${v.valid?'✅ Escala válida':'❌ Escala inválida'}</div><div style="font-size:13px;margin-top:4px">${v.errs.length} erro(s) · ${v.warns.length} aviso(s)</div></div>`;
  v.errs.forEach(e=>h+=`<div class="al e" style="margin-bottom:6px"><b>${e.code}</b> ${e.msg}</div>`);
  v.warns.forEach(e=>h+=`<div class="al w" style="margin-bottom:6px"><b>${e.code}</b> ${e.msg}</div>`);
  if(v.valid&&!v.warns.length)h+=`<div style="text-align:center;padding:24px;color:#2e7d32;font-size:16px">🎉 Tudo em ordem!</div>`;
  return h;
}

// ══ CONFIGURAÇÃO ══
function tCfg(md,cfg){
  if(!S.admin)return`<div class="al w">Clique em 🔒 no cabeçalho para entrar em modo admin.</div>`;
  const sec=S.cfgSec||'people';
  const f=feasi(S.people,cfg);
  const ac=S.people.filter(p=>p.active).sort((a,b)=>a.name.localeCompare(b.name));
  let h=`<div style="font-size:16px;font-weight:600;margin-bottom:12px;color:var(--navy)">Configuração</div>
  <div class="vbar" style="margin-bottom:10px"><div class="dot ${f.ok?'ok':'err'}"></div><div style="font-size:12px"><b>${f.ok?'Viável':'Inviável'}</b> — ${f.wd}×3=${f.total} vagas | Quotas: <b>${f.tq}</b>${f.sur!==0?` (${f.sur>0?'+':''}${f.sur})`:''}</div></div>
  <div class="stabs">
    ${[['people','👥'],['quotas','📊'],['holidays','🏖'],['unavail','🚫'],['export','📂']].map(([id,ic])=>`<button class="${sec===id?'on':''}" onclick="S.cfgSec='${id}';R()">${ic}</button>`).join('')}
  </div>`;

  if(sec==='people'){
    h+=`<div class="row" style="justify-content:space-between;margin-bottom:10px"><span style="font-weight:600">Pessoas (${S.people.length})</span><button class="sml" onclick="openAddP()">+ Adicionar</button></div>`;
    const q2=S.search||'';
    h+=`<input class="search" type="search" placeholder="Pesquisar…" value="${q2}" oninput="S.search=this.value;R()">`;
    for(const p of [...S.people].sort((a,b)=>a.name.localeCompare(b.name)).filter(p=>!q2||p.name.toLowerCase().includes(q2.toLowerCase()))){
      h+=`<div class="card" style="padding:12px 14px;margin-bottom:8px"><div style="display:flex;justify-content:space-between;align-items:center">
        <div><div style="font-weight:600;font-size:14px;color:${p.active?'var(--navy)':'#8e8e93'}">${p.name}</div><div style="font-size:12px;color:#8e8e93">Quota ${p.quota} · ${(p.vac||[]).length} férias</div></div>
        <div class="row" style="gap:5px">
          <button onclick="togAct('${p.id}')" style="font-size:11px;padding:5px 9px;background:${p.active?'#E8F5E9':'#FFEBEE'};color:${p.active?'#2e7d32':'#c62828'};border:none;border-radius:8px">${p.active?'✅':'❌'}</button>
          <button onclick="openEditP('${p.id}')" class="sml">✏️</button>
        </div>
      </div></div>`;
    }
  }

  if(sec==='quotas'){
    h+=`<div style="font-weight:600;margin-bottom:10px">Quotas de ${MNS[cfg.m-1]} ${cfg.y}</div>`;
    for(const p of ac){const q=cfg.qov[p.id]??p.quota,n=md.asgns.filter(a=>a.personId===p.id).length;
      h+=`<div class="card" style="padding:10px 14px;margin-bottom:8px;display:flex;align-items:center;justify-content:space-between">
        <div><div style="font-size:14px;font-weight:500">${p.name}</div><div style="font-size:11px;color:#8e8e93">${n}/${q} atribuídos</div></div>
        <div style="display:flex;align-items:center;gap:10px">
          <button onclick="updQ('${p.id}',${q-1})" style="width:36px;height:36px;border-radius:50%;background:#f0f0f5;border:none;font-size:20px;display:flex;align-items:center;justify-content:center;cursor:pointer">−</button>
          <span style="font-size:20px;font-weight:600;min-width:24px;text-align:center">${q}</span>
          <button onclick="updQ('${p.id}',${q+1})" style="width:36px;height:36px;border-radius:50%;background:#f0f0f5;border:none;font-size:20px;display:flex;align-items:center;justify-content:center;cursor:pointer">+</button>
        </div>
      </div>`;
    }
    const tq=ac.reduce((s,p)=>s+(cfg.qov[p.id]??p.quota),0);
    h+=`<div class="al ${f.ok?'ok':'e'}">Total: <b>${tq}</b> | Vagas: <b>${f.total}</b> | ${f.sur===0?'✅ Equilibrado':`❌ ${f.sur>0?'Excesso':'Défice'}: ${Math.abs(f.sur)}`}</div>`;
  }

  if(sec==='holidays'){
    const allDts=mds(cfg.y,cfg.m);
    h+=`<div style="font-weight:600;margin-bottom:8px">Feriados — ${MNS[cfg.m-1]} ${cfg.y}</div>
    <p style="font-size:12px;color:#8e8e93;margin-bottom:10px">Toque numa data para marcar/desmarcar.</p>
    <div class="mcal">
    ${['S','T','Q','Q','S','S','D'].map(d=>`<div class="dh">${d}</div>`).join('')}`;
    const fd=allDts[0],fdw=dwd(fd),off=fdw===0?6:fdw-1;
    for(let i=0;i<off;i++)h+=`<div></div>`;
    for(const d of allDts){const isH=cfg.h.includes(d),w=dwd(d),isWe=w===0||w===6,day=parseInt(d.slice(8));h+=`<div class="dc ${isH?'hol':isWe?'we':''}" onclick="${!isWe?`togHol('${d}')`:''}">${day}${isH?'🏖':''}</div>`;}
    h+=`</div>`;
    if(cfg.h.length)h+=`<div class="al e">${cfg.h.sort().map(d=>`${fptFull(d)} <button onclick="togHol('${d}')" style="background:none;border:none;cursor:pointer;color:inherit">✕</button>`).join(' · ')}</div>`;
  }

  if(sec==='unavail'){
    h+=`<div style="font-weight:600;margin-bottom:8px">Indisponibilidades</div>
    <select onchange="S._selP=this.value;R()" style="margin-bottom:10px">
      <option value="">— Seleccionar pessoa —</option>
      ${S.people.sort((a,b)=>a.name.localeCompare(b.name)).map(p=>`<option value="${p.id}" ${S._selP===p.id?'selected':''}>${p.name}</option>`).join('')}
    </select>`;
    const sel=S._selP?S.people.find(p=>p.id===S._selP):null;
    if(sel){
      const allDts=mds(cfg.y,cfg.m);
      h+=`<div class="card"><div style="font-weight:500;margin-bottom:6px">${sel.name} — Calendário</div>
      <div style="font-size:11px;color:#8e8e93;margin-bottom:8px">🔴 Férias · 🟡 Indisponível · Toque para alternar</div>
      <div class="mcal">
      ${['S','T','Q','Q','S','S','D'].map(d=>`<div class="dh">${d}</div>`).join('')}`;
      const fd=allDts[0],off=dwd(fd)===0?6:dwd(fd)-1;
      for(let i=0;i<off;i++)h+=`<div></div>`;
      for(const d of allDts){const isV=(sel.vac||[]).includes(d),isU=(sel.ud||[]).includes(d),w=dwd(d),day=parseInt(d.slice(8));h+=`<div class="dc ${isV?'vac':isU?'ud':w===0||w===6?'we':''}" onclick="togVac('${sel.id}','${d}')">${day}</div>`;}
      h+=`</div><div style="font-size:11px;color:#8e8e93;margin-top:6px">${(sel.vac||[]).length} férias · ${(sel.ud||[]).length} indisponível</div>`;
      h+=`<div class="sep" style="height:0.5px;background:#f0f0f0;margin:10px 0"></div>`;
      h+=`<div style="font-weight:500;margin-bottom:6px">Turnos proibidos</div>
      <div style="display:flex;gap:10px;flex-wrap:wrap">
      ${SHK.map(sh=>`<label style="display:flex;align-items:center;gap:5px;font-size:13px;cursor:pointer"><input type="checkbox" ${(sel.fs||[]).includes(sh)?'checked':''} onchange="togFS('${sel.id}','${sh}',this.checked)" style="width:18px;height:18px"> ${SHN[sh]}</label>`).join('')}
      </div></div>`;
    }
  }

  if(sec==='export'){
    h+=`<div style="font-weight:600;margin-bottom:10px">Exportar / Importar</div>
    <div class="card"><div style="font-weight:500;margin-bottom:5px">💾 Backup completo</div>
    <p style="font-size:12px;color:#8e8e93;margin-bottom:8px">Guarda todos os dados num ficheiro JSON.</p>
    <div class="row"><button class="pri" onclick="doExportJSON()" style="flex:1">Exportar JSON</button><button class="sec" onclick="doImportJSON()" style="flex:1">Importar JSON</button></div></div>
    <div class="card"><div style="font-weight:500;margin-bottom:5px">🖨 Imprimir</div>
    <button class="sec" onclick="doPrint()" ${!md.asgns.length?'disabled':''} style="width:100%">Imprimir A4</button></div>
    <div class="card"><div style="font-weight:500;margin-bottom:5px">📋 Copiar para mês seguinte</div>
    <button class="sec" onclick="doCopy()" style="width:100%">Copiar configuração</button></div>
    <div class="card"><div style="font-weight:500;margin-bottom:5px">🗑 Limpar dados</div>
    <button class="dng" onclick="if(confirm('Apagar tudo?')){localStorage.removeItem('${SAVE}');location.reload();}" style="width:100%">Limpar todos os dados</button></div>`;
  }
  return h;
}

// ══ MODAL ══
function rModal(){
  const m=S.modal;
  if(m.type==='login')return`<div class="ov" onclick="if(event.target===this){S.modal=null;R()}"><div class="sheet"><div class="sheet-handle"></div>
  <div style="font-size:18px;font-weight:600;margin-bottom:4px">Modo Administrador</div>
  <p style="font-size:13px;color:#8e8e93;margin-bottom:16px">Senha: admin123</p>
  <input type="password" id="pwI" placeholder="Senha" style="margin-bottom:12px" onkeydown="if(event.key==='Enter')doLogin()">
  <div class="row"><button class="pri" onclick="doLogin()" style="flex:1">Entrar</button><button onclick="S.modal=null;R()" style="flex:1">Cancelar</button></div></div></div>`;

  if(m.type==='person'){const p=m.p;
  return`<div class="ov" onclick="if(event.target===this){S.modal=null;R()}"><div class="sheet"><div class="sheet-handle"></div>
  <div style="font-size:18px;font-weight:600;margin-bottom:16px">${m.isNew?'➕ Adicionar':'✏️ Editar'} Pessoa</div>
  <label style="display:block;font-size:13px;font-weight:500;margin-bottom:5px">Nome *</label>
  <input type="text" id="pN" value="${p.name}" placeholder="Nome completo" style="margin-bottom:12px">
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:12px">
    <div><label style="display:block;font-size:13px;font-weight:500;margin-bottom:5px">Quota</label>
    <input type="number" id="pQ" value="${p.quota}" min="0" style="font-size:16px"></div>
    <div style="padding-top:22px"><label style="display:flex;align-items:center;gap:8px;cursor:pointer;font-size:14px"><input type="checkbox" id="pA" ${p.active?'checked':''} style="width:20px;height:20px"> Activa</label></div>
  </div>
  <label style="display:block;font-size:13px;font-weight:500;margin-bottom:8px">Turnos proibidos</label>
  <div style="display:flex;gap:12px;margin-bottom:16px">
  ${SHK.map(s=>`<label style="display:flex;align-items:center;gap:5px;font-size:13px;cursor:pointer"><input type="checkbox" id="fs_${s}" ${(p.fs||[]).includes(s)?'checked':''} style="width:18px;height:18px"> ${SHN[s]}</label>`).join('')}
  </div>
  <div class="row"><button class="pri" onclick="saveP()" style="flex:1">Guardar</button>${!m.isNew?`<button class="dng" onclick="delP('${p.id}')" style="flex:1">Apagar</button>`:''}
  <button onclick="S.modal=null;R()" style="flex:1">Cancelar</button></div></div></div>`;}
  return'';
}

// ══ ACÇÕES ══
window.pM=()=>{let y=S.y,m=S.m-1;if(m<1){m=12;y--;}S.y=y;S.m=m;S.genStatus=null;S.editSlot=null;R();};
window.nM=()=>{let y=S.y,m=S.m+1;if(m>12){m=1;y++;}S.y=y;S.m=m;S.genStatus=null;S.editSlot=null;R();};
window.sTab=t=>{if(t==='config'&&!S.admin){showLogin();return;}S.tab=t;S.editSlot=null;R();};
window.showLogin=()=>{S.modal={type:'login'};R();};
window.doLogin=()=>{const pw=document.getElementById('pwI')?.value;if(pw===''||pw==='admin123'){S.admin=true;S.tab='config';S.modal=null;R();}else{alert('Senha incorrecta.');}};
window.eSl=(date,shift)=>{S.editSlot={date,shift};S.editErrs=[];R();};
window.cEd=pid=>{
  if(!S.editSlot)return;const p=S.people.find(x=>x.id===pid),md=gmd();if(!p)return;
  const without=md.asgns.filter(a=>!(a.date===S.editSlot.date&&a.shift===S.editSlot.shift));
  // Validação básica
  const errs=[];
  if(without.find(a=>a.date===S.editSlot.date&&a.personId===pid))errs.push('Já tem escala neste dia.');
  for(const d of without.filter(a=>a.personId===pid).map(a=>a.date))if(consec(d,S.editSlot.date))errs.push(`Dia consecutivo a ${fptFull(d)}.`);
  if(errs.length){S.editErrs=errs;R();return;}
  const newA={id:`${S.editSlot.date}-${S.editSlot.shift}`,date:S.editSlot.date,shift:S.editSlot.shift,personId:pid,locked:false,manual:true};
  if(without.length<md.asgns.length)md.asgns=md.asgns.map(a=>a.date===S.editSlot.date&&a.shift===S.editSlot.shift?newA:a);else md.asgns.push(newA);
  addH(`✏️ ${fptFull(S.editSlot.date)} ${SHN[S.editSlot.shift]} → ${p.name}`);
  S.editSlot=null;S.editErrs=[];R();
};
window.asgSat=(date,pid)=>{
  const md=gmd(),cfg=gcfg();if(cfg.h.includes(date))return;
  S.satWarn=S.satWarn||{};
  if(pid){const p=S.people.find(x=>x.id===pid),errs=[];
    if(!p.active)errs.push(`${p.name} inactiva.`);
    if(unavail(p,date,cfg.h))errs.push('Indisponível.');
    const f=new Date(date+'T12:00:00');f.setDate(f.getDate()-1);const fs=f.toISOString().slice(0,10);
    if(md.asgns.find(a=>a.date===fs&&a.personId===pid))errs.push('Tem escala na sexta-feira anterior.');
    if(errs.length){S.satWarn[date]=errs;R();return;}
  }
  delete S.satWarn[date];
  const sa=(md.satA||[]).find(x=>x.date===date);
  if(sa)sa.personId=pid||null;else{md.satA=md.satA||[];md.satA.push({id:'s'+date,date,personId:pid||null,locked:false});}
  addH(`🗓 Sáb ${fptFull(date)}: ${pid?S.people.find(p=>p.id===pid)?.name:'removido'}`);R();
};
window.togAct=id=>{const p=S.people.find(x=>x.id===id);if(p){p.active=!p.active;sst();}R();};
window.openAddP=()=>{S.modal={type:'person',isNew:true,p:{id:'p'+Date.now(),name:'',active:true,quota:0,vac:[],ud:[],uwd:[],fs:[],notes:''}};R();};
window.openEditP=id=>{const p=S.people.find(x=>x.id===id);if(p)S.modal={type:'person',isNew:false,p:{...p,vac:[...(p.vac||[])],ud:[...(p.ud||[])],uwd:[...(p.uwd||[])],fs:[...(p.fs||[])]}};R();};
window.saveP=()=>{
  const m=S.modal?.p;if(!m)return;
  const name=document.getElementById('pN')?.value?.trim();if(!name){alert('Nome obrigatório.');return;}
  m.name=name;m.quota=parseInt(document.getElementById('pQ')?.value)||0;m.active=document.getElementById('pA')?.checked??true;
  m.fs=SHK.filter(s=>document.getElementById('fs_'+s)?.checked);
  const ex=S.people.find(p=>p.id===m.id);if(ex)S.people=S.people.map(p=>p.id===m.id?{...m}:p);else S.people.push({...m});
  gcfg().qov[m.id]=m.quota;S.modal=null;sst();R();
};
window.delP=id=>{if(confirm('Eliminar?')){S.people=S.people.filter(p=>p.id!==id);S.modal=null;sst();}R();};
window.updQ=(id,q)=>{gcfg().qov[id]=Math.max(0,q);sst();R();};
window.togHol=date=>{const cfg=gcfg();const i=cfg.h.indexOf(date);if(i>=0)cfg.h.splice(i,1);else{cfg.h.push(date);cfg.h.sort();}sst();R();};
window.togVac=(pid,date)=>{const p=S.people.find(x=>x.id===pid);if(!p)return;p.vac=p.vac||[];p.ud=p.ud||[];if(p.vac.includes(date)){p.vac.splice(p.vac.indexOf(date),1);p.ud.push(date);}else if(p.ud.includes(date)){p.ud.splice(p.ud.indexOf(date),1);}else{p.vac.push(date);}sst();R();};
window.togFS=(pid,sh,on)=>{const p=S.people.find(x=>x.id===pid);if(!p)return;p.fs=p.fs||[];if(on&&!p.fs.includes(sh))p.fs.push(sh);else p.fs=p.fs.filter(s=>s!==sh);sst();R();};

window.doGen=async(alt)=>{
  const md=gmd(),cfg=gcfg();
  const f=feasi(S.people,cfg);
  if(!f.ok){S.genStatus={t:'e',msg:f.msgs.join('\n')};R();return;}
  S.genBusy=true;S.genStatus={t:'i',msg:'⚙️ A gerar…'};R();
  await new Promise(r=>setTimeout(r,40));
  try{
    const r=solve(S.people,cfg,{seed:cfg.seed,alt,locked:md.asgns.filter(a=>a.locked)});
    if(!r.ok){S.genStatus={t:'e',msg:'❌ '+r.msg};return;}
    md.asgns=r.asgns;
    addH(`⚡ Escala ${alt?'alt ':''}gerada (${r.ms}ms)`,'generate');
    S.genStatus={t:'ok',msg:`✅ Gerada em ${r.ms}ms · Score: ${r.sc}`};sst();
  }finally{S.genBusy=false;R();}
};

window.doPrint=()=>{
  const md=gmd(),cfg=gcfg(),pm=new Map(S.people.map(p=>[p.id,p])),mn=MNS[cfg.m-1];
  let rows='';
  for(const date of mds(cfg.y,cfg.m)){
    const st=dst(date,cfg.h),w=dwd(date);
    if(st==='sun'){rows+=`<tr style="background:#ffcccc"><td>${WDS[w]}</td><td>${fptFull(date)}</td><td colspan="3" style="font-style:italic;color:#c00">Domingo</td></tr>`;continue;}
    if(st==='hol'){rows+=`<tr style="background:#ff9999"><td>F</td><td>${fptFull(date)}</td><td colspan="3" style="font-style:italic;color:#c00">Feriado</td></tr>`;continue;}
    if(st==='sat'){rows+=`<tr style="background:#d6e4f7"><td>${WDS[w]}</td><td>${fptFull(date)}</td><td colspan="3" style="font-style:italic">Sábado</td></tr>`;continue;}
    const cells=SHK.map(sh=>{const a=md.asgns.find(x=>x.date===date&&x.shift===sh);return`<td>${pm.get(a?.personId)?.name||''}</td>`;}).join('');
    rows+=`<tr><td>${WDS[w]}</td><td>${fptFull(date)}</td>${cells}</tr>`;
  }
  const win=window.open('','_blank');
  win.document.write(`<!DOCTYPE html><html><head><meta charset="UTF-8"><title>Escala ${mn} ${cfg.y}</title><style>body{font-family:Arial;font-size:10px;margin:10px}table{border-collapse:collapse;width:100%}th{background:#1F4E79;color:white;padding:4px 6px;text-align:left}td{padding:3px 6px;border:0.5px solid #ccc}@media print{@page{size:A4 landscape;margin:.5cm}}</style></head><body><h2 style="margin:0 0 5px">ESCALA ${mn.toUpperCase()} ${cfg.y}</h2><table><tr><th>D</th><th>Data</th><th>Manhã 09–13h</th><th>Interm. 13–16h</th><th>Tarde 16–19h</th></tr>${rows}</table><script>window.onload=()=>window.print()<\/script></body></html>`);
  win.document.close();
};

window.printIndividual=pid=>{
  const p=S.people.find(x=>x.id===pid);if(!p)return;
  const md=gmd(),cfg=gcfg(),mn=MNS[cfg.m-1];
  const myA=md.asgns.filter(a=>a.personId===pid).sort((a,b)=>a.date.localeCompare(b.date));
  const mySat=(md.satA||[]).filter(s=>s.personId===pid).sort((a,b)=>a.date.localeCompare(b.date));
  const all=[...myA,...mySat.map(sa=>({...sa,shift:'sat'}))].sort((a,b)=>a.date.localeCompare(b.date));
  let rows=all.map(a=>`<tr><td>${fptFull(a.date)}</td><td>${WDF[dwd(a.date)]}</td><td><b>${a.shift==='sat'?'Sábado':SHN[a.shift]}</b></td><td>${a.shift==='sat'?'09:00–13:00':SHT[a.shift]}</td></tr>`).join('');
  const win=window.open('','_blank');
  win.document.write(`<!DOCTYPE html><html><head><meta charset="UTF-8"><title>${p.name} — ${mn} ${cfg.y}</title><style>body{font-family:Arial;font-size:12px;margin:20px;max-width:500px}h1{color:#1F4E79;font-size:20px;margin:0 0 4px}h2{font-size:12px;color:#666;margin:0 0 16px}table{border-collapse:collapse;width:100%}th{background:#1F4E79;color:white;padding:6px 8px;text-align:left}td{padding:7px 8px;border:0.5px solid #ddd}@media print{@page{size:A4 portrait;margin:1.5cm}}</style></head><body><h1>${p.name}</h1><h2>Escala de ${mn} ${cfg.y}</h2><table><tr><th>Data</th><th>Dia</th><th>Turno</th><th>Horário</th></tr>${rows}</table><script>window.onload=()=>window.print()<\/script></body></html>`);
  win.document.close();
};

window.doExportJSON=()=>{
  const data={version:1,exportedAt:new Date().toISOString(),people:S.people,months:S.months};
  const blob=new Blob([JSON.stringify(data,null,2)],{type:'application/json'});
  const url=URL.createObjectURL(blob),a=document.createElement('a');
  a.href=url;a.download=`escala-backup-${new Date().toISOString().slice(0,10)}.json`;
  document.body.appendChild(a);a.click();document.body.removeChild(a);URL.revokeObjectURL(url);
};
window.doImportJSON=()=>{
  const inp=document.createElement('input');inp.type='file';inp.accept='.json';
  inp.onchange=async e=>{
    const file=e.target.files[0];if(!file)return;
    try{const d=JSON.parse(await file.text());if(!d.people)throw new Error('Inválido');
    if(!confirm(`Importar ${d.people.length} pessoas?`))return;
    S.people=d.people;S.months=d.months||{};sst();R();}
    catch(err){alert('Erro: '+err.message);}
  };inp.click();
};
window.doCopy=()=>{
  const cfg=gcfg();let ny=S.y,nm=S.m+1;if(nm>12){nm=1;ny++;}
  if(!confirm(`Copiar para ${MNS[nm-1]} ${ny}?`))return;
  const nk=mk(ny,nm);const qov={...cfg.qov};
  S.months[nk]={cfg:{y:ny,m:nm,seed:ny*100+nm,h:defHols(ny,nm),satQ:cfg.satQ,qov},asgns:[],satA:satsOf(ny,nm).map(d=>({id:'s'+d,date:d,personId:null,locked:false})),hist:[]};
  sst();S.genStatus={t:'ok',msg:`✅ Copiado para ${MNS[nm-1]} ${ny}.`};R();
};

R();
</script>
</body>
</html>

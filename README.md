<!DOCTYPE html>
<html lang="da">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Research Budget Builder</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.44.0/tabler-icons.min.css" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg:#ffffff;--bg2:#f5f5f3;--bg3:#eeede9;
    --text:#1a1a1a;--text2:#555;--text3:#999;
    --border:rgba(0,0,0,0.12);--border2:rgba(0,0,0,0.22);
    --info-bg:#e6f1fb;--info-text:#0c447c;--info-border:#85b7eb;
    --success-bg:#eaf3de;--success-text:#27500a;--success-border:#97c459;
    --radius:8px;--radius-lg:12px;
  }
  @media(prefers-color-scheme:dark){:root{
    --bg:#1e1e1e;--bg2:#2a2a2a;--bg3:#333;
    --text:#f0f0f0;--text2:#aaa;--text3:#666;
    --border:rgba(255,255,255,0.12);--border2:rgba(255,255,255,0.22);
    --info-bg:#0c2a42;--info-text:#85b7eb;--info-border:#185fa5;
    --success-bg:#172a08;--success-text:#97c459;--success-border:#3b6d11;
  }}
  body{font-family:system-ui,-apple-system,sans-serif;background:var(--bg3);color:var(--text);min-height:100vh;}
  .page{max-width:980px;margin:0 auto;padding:2rem 1rem 4rem;}
  .top-bar{display:flex;align-items:center;gap:10px;margin-bottom:1.25rem;flex-wrap:wrap;}
  .top-bar h1{font-size:22px;font-weight:500;flex:1;min-width:140px;}
  .pill-group{display:flex;gap:3px;}
  .pill{padding:5px 11px;font-size:12px;cursor:pointer;border:0.5px solid var(--border2);border-radius:var(--radius);background:transparent;color:var(--text2);white-space:nowrap;transition:background .12s,color .12s;}
  .pill.active{background:var(--info-bg);color:var(--info-text);border-color:var(--info-border);font-weight:500;}
  .currency-toggle{display:flex;border:0.5px solid var(--border2);border-radius:var(--radius);overflow:hidden;}
  .cur-btn{padding:5px 13px;font-size:12px;font-weight:500;cursor:pointer;border:none;background:transparent;color:var(--text2);}
  .cur-btn.active{background:var(--text);color:var(--bg);}
  .icon-btn{display:flex;align-items:center;gap:5px;padding:5px 12px;font-size:12px;cursor:pointer;border:0.5px solid var(--border2);border-radius:var(--radius);background:transparent;color:var(--text);white-space:nowrap;}
  .icon-btn:hover{background:var(--bg2);}
  .icon-btn:disabled{opacity:.5;cursor:not-allowed;}
  .rate-bar{display:flex;align-items:center;gap:8px;flex-wrap:wrap;padding:8px 12px;background:var(--bg2);border:0.5px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;font-size:12px;color:var(--text2);}
  .rate-bar input{font-size:13px;padding:3px 7px;border:0.5px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);width:80px;}
  .panel{border:0.5px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;overflow:hidden;background:var(--bg);}
  .panel-header{display:flex;align-items:center;justify-content:space-between;padding:9px 14px;background:var(--bg2);cursor:pointer;}
  .panel-title{font-size:13px;font-weight:500;display:flex;align-items:center;gap:7px;}
  .chevron{font-size:14px;color:var(--text3);transition:transform .18s;display:inline-block;}
  .chevron.open{transform:rotate(180deg);}
  .rates-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:8px;padding:12px 14px;}
  .rate-row{display:flex;flex-direction:column;gap:3px;}
  .rate-label{font-size:11px;color:var(--text2);}
  .rate-inp{font-size:13px;padding:4px 7px;border:0.5px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);width:100%;}
  .summary-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(115px,1fr));gap:10px;margin-bottom:1.25rem;}
  .metric{background:var(--bg2);border-radius:var(--radius);padding:10px 12px;}
  .metric-label{font-size:11px;color:var(--text2);margin:0 0 3px;}
  .metric-value{font-size:15px;font-weight:500;}
  .section{margin-bottom:1rem;border:0.5px solid var(--border);border-radius:var(--radius-lg);overflow:hidden;background:var(--bg);}
  .section-header{display:flex;align-items:center;justify-content:space-between;padding:9px 14px;background:var(--bg2);cursor:pointer;user-select:none;}
  .section-title{font-size:13px;font-weight:500;display:flex;align-items:center;gap:7px;}
  .section-total{font-size:13px;font-weight:500;}
  .section-body{border-top:0.5px solid var(--border);}
  .tbl-wrap{overflow-x:auto;}
  table{width:100%;border-collapse:collapse;table-layout:fixed;min-width:480px;}
  th{font-size:11px;font-weight:500;color:var(--text2);text-align:left;padding:6px 8px;border-bottom:0.5px solid var(--border);background:var(--bg);}
  td{font-size:12px;padding:5px 8px;border-bottom:0.5px solid var(--border);vertical-align:middle;}
  tr:last-child td{border-bottom:none;}
  tr.hidden-row{display:none;}
  tr:not(.hidden-row):hover td{background:var(--bg2);}
  .inst-badge{font-size:10px;padding:1px 5px;border-radius:var(--radius);background:var(--bg2);color:var(--text2);white-space:nowrap;}
  .num-inp{width:100%;font-size:12px;padding:3px 5px;border:0.5px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);text-align:right;}
  .num-inp:focus{outline:none;box-shadow:0 0 0 2px var(--info-border);}
  .row-total{font-weight:500;text-align:right;font-size:12px;}
  .section-foot{display:flex;justify-content:space-between;align-items:center;padding:7px 14px;border-top:0.5px solid var(--border);background:var(--bg2);}
  .section-foot-label{font-size:11px;color:var(--text2);}
  .section-foot-val{font-size:13px;font-weight:500;}
  .grand-foot{display:flex;justify-content:space-between;align-items:center;padding:12px 16px;border:0.5px solid var(--border2);border-radius:var(--radius-lg);margin-top:1rem;background:var(--bg);}
  .grand-label{font-size:13px;color:var(--text2);}
  .grand-val{font-size:20px;font-weight:500;}
  #dl-area{margin-bottom:10px;}
  #dl-link{display:inline-flex;align-items:center;gap:6px;padding:7px 16px;font-size:13px;font-weight:500;border:0.5px solid var(--success-border);border-radius:var(--radius);background:var(--success-bg);color:var(--success-text);text-decoration:none;}
</style>
</head>
<body>
<div class="page">
  <div class="top-bar">
    <h1>Research budget</h1>
    <div style="display:flex;align-items:center;gap:6px;flex-wrap:wrap;">
      <span style="font-size:12px;color:var(--text2)">Years:</span>
      <div class="pill-group" id="year-btns">
        <button class="pill active" data-y="1">1</button>
        <button class="pill" data-y="2">2</button>
        <button class="pill" data-y="3">3</button>
        <button class="pill" data-y="4">4</button>
        <button class="pill" data-y="5">5</button>
      </div>
      <span style="font-size:12px;color:var(--text2);margin-left:4px">Institution:</span>
      <div class="pill-group" id="inst-btns">
        <button class="pill active" data-inst="all">All</button>
        <button class="pill" data-inst="Rigshospitalet">Rigshospitalet</button>
        <button class="pill" data-inst="DTU">DTU</button>
      </div>
      <div class="currency-toggle" style="margin-left:4px">
        <button class="cur-btn active" id="btn-dkk">DKK</button>
        <button class="cur-btn" id="btn-eur">EUR</button>
      </div>
      <button class="icon-btn" id="export-btn"><i class="ti ti-download"></i> Export Excel</button>
    </div>
  </div>

  <div id="dl-area"></div>

  <div class="rate-bar">
    <i class="ti ti-arrows-exchange" style="font-size:15px"></i>
    <span>1 EUR =</span>
    <input type="number" id="rate-inp" value="7.4728" step="0.0001" />
    <span>DKK</span>
    <span style="color:var(--text3);font-size:11px">(bruges til EUR-visning og Excel-export — kurs pr. 6. maj 2026)</span>
  </div>

  <div class="panel">
    <div class="panel-header" id="rates-toggle">
      <span class="panel-title"><i class="ti ti-coin" style="font-size:15px"></i> Lønsatser (DKK / år ved 1,0 FTE)</span>
      <i class="ti ti-chevron-down chevron open" id="rates-chev"></i>
    </div>
    <div id="rates-body">
      <div class="rates-grid" id="rates-grid"></div>
      <p style="padding:0 14px 10px;font-size:11px;color:var(--text3)">Budget = FTE × lønsats. Ret budgetfeltet manuelt for at låse det.</p>
    </div>
  </div>

  <div class="summary-grid" id="summary-grid"></div>
  <div id="sections-container"></div>

  <div class="grand-foot">
    <span class="grand-label">Samlet total (alle år)</span>
    <span class="grand-val" id="grand-total">DKK 0</span>
  </div>
</div>

<script>
let eurRate=7.4728, displayCurrency='DKK';
function toDisplay(d){return displayCurrency==='EUR'?d/eurRate:d;}
function fmtDisplay(d){const v=Math.round(toDisplay(d));return displayCurrency==='EUR'?'€ '+v.toLocaleString('da-DK'):'DKK '+v.toLocaleString('da-DK');}

const SALARY_ROWS=[
  {sub:'Consultant',inst:'Rigshospitalet',rateKey:'consultant_rh'},
  {sub:'Pre-graduate scholar',inst:'Rigshospitalet',rateKey:'pregrad_rh'},
  {sub:'Scientist / researcher',inst:'Rigshospitalet',rateKey:'scientist_rh'},
  {sub:'PhD student',inst:'Rigshospitalet',rateKey:'phd_rh'},
  {sub:'Research technician / nurse',inst:'Rigshospitalet',rateKey:'tech_rh'},
  {sub:'Project employees at admin. institution',inst:'Rigshospitalet',rateKey:'projempl_rh'},
  {sub:'Project employees',inst:'DTU',rateKey:'projempl_dtu'},
  {sub:'PhD student',inst:'DTU',rateKey:'phd_dtu'},
  {sub:'Postdoc',inst:'DTU',rateKey:'postdoc_dtu'},
  {sub:'Pre-graduate scholar',inst:'DTU',rateKey:'pregrad_dtu'},
];
const CATEGORIES=[
  {id:'salary',label:'Salary',color:'#E6F1FB',tcolor:'#185FA5',hasFte:true,rows:SALARY_ROWS},
  {id:'operation',label:'Operation',color:'#E1F5EE',tcolor:'#0F6E56',hasFte:false,rows:[
    {sub:'Data management',inst:'DTU'},{sub:'Subcontractor costs',inst:'Rigshospitalet'},
    {sub:'Bench fee',inst:'Rigshospitalet'},{sub:'Infrastructure',inst:'DTU'},
    {sub:'Project specific costs',inst:'Rigshospitalet'},{sub:'Operating expenses',inst:'Rigshospitalet'},
    {sub:'Equipment',inst:'DTU'},{sub:'Equipment',inst:'Rigshospitalet'},
  ]},
  {id:'dissemination',label:'Dissemination, training & education',color:'#FAEEDA',tcolor:'#854F0B',hasFte:false,rows:[
    {sub:'Travel',inst:'Rigshospitalet'},{sub:'Training',inst:'Rigshospitalet'},
    {sub:'Conference participation',inst:'Rigshospitalet'},{sub:'Conference participation',inst:'DTU'},
    {sub:'Collaborative activities',inst:'Rigshospitalet'},{sub:'Collaborative activities',inst:'DTU'},
    {sub:'Publication costs',inst:'Rigshospitalet'},
  ]},
  {id:'admin',label:'Administration',color:'#F1EFE8',tcolor:'#5F5E5A',hasFte:false,rows:[
    {sub:'Direct administrative expenses',inst:'Rigshospitalet'},
  ]},
  {id:'supplement',label:'Project supplement',color:'#EEEDFE',tcolor:'#534AB7',hasFte:false,rows:[
    {sub:'Project supplement',inst:'DTU'},
  ]},
];
const RATE_DEFS=[
  {key:'consultant_rh',label:'Consultant (RH)',default:1080000},
  {key:'pregrad_rh',label:'Pre-graduate scholar (RH)',default:150000},
  {key:'scientist_rh',label:'Scientist / researcher (RH)',default:624000},
  {key:'phd_rh',label:'PhD student (RH)',default:624000},
  {key:'tech_rh',label:'Research technician / nurse (RH)',default:504000},
  {key:'projempl_rh',label:'Project employees (RH)',default:550000},
  {key:'projempl_dtu',label:'Project employees (DTU)',default:550000},
  {key:'phd_dtu',label:'PhD student (DTU)',default:530000},
  {key:'postdoc_dtu',label:'Postdoc (DTU)',default:650000},
  {key:'pregrad_dtu',label:'Pre-graduate scholar (DTU)',default:150000},
];

let numYears=1,instFilter='all',state={},rates={},collapsed={};
RATE_DEFS.forEach(r=>{rates[r.key]=r.default;});

function sk(c,r,y,f){return c+'_'+r+'_y'+y+'_'+f;}
function getVal(c,r,y,f){return state[sk(c,r,y,f)]||0;}
function setVal(c,r,y,f,v){state[sk(c,r,y,f)]=parseFloat(v)||0;}
function catTotal(catId){
  const cat=CATEGORIES.find(c=>c.id===catId);let t=0;
  cat.rows.forEach((row,ri)=>{
    if(instFilter!=='all'&&row.inst!==instFilter)return;
    for(let y=1;y<=numYears;y++)t+=getVal(catId,ri,y,'budget');
  });return t;
}
function yearTotal(y){
  let t=0;
  CATEGORIES.forEach(cat=>cat.rows.forEach((row,ri)=>{
    if(instFilter!=='all'&&row.inst!==instFilter)return;
    t+=getVal(cat.id,ri,y,'budget');
  }));return t;
}
function grandTotal(){let t=0;for(let y=1;y<=numYears;y++)t+=yearTotal(y);return t;}

function updateTotals(){
  document.getElementById('grand-total').textContent=fmtDisplay(grandTotal());
  const sg=document.getElementById('summary-grid');sg.innerHTML='';
  for(let y=1;y<=numYears;y++){
    const m=document.createElement('div');m.className='metric';
    m.innerHTML='<p class="metric-label">År '+y+' total</p><p class="metric-value">'+fmtDisplay(yearTotal(y))+'</p>';
    sg.appendChild(m);
  }
  CATEGORIES.forEach(cat=>{
    const ct=catTotal(cat.id);
    const el=document.getElementById('sec-total-'+cat.id);if(el)el.textContent=fmtDisplay(ct);
    const fl=document.getElementById('sec-foot-'+cat.id);if(fl)fl.textContent=fmtDisplay(ct);
    cat.rows.forEach((_,ri)=>{
      let rowT=0;for(let y=1;y<=numYears;y++)rowT+=getVal(cat.id,ri,y,'budget');
      const rt=document.getElementById('rt_'+cat.id+'_'+ri);if(rt)rt.textContent=fmtDisplay(rowT);
    });
  });
  document.querySelectorAll('.budget-th').forEach(th=>{
    th.textContent='År '+th.dataset.y+' budget ('+(displayCurrency==='EUR'?'EUR':'DKK')+')';
  });
}
function applyInstFilter(){
  CATEGORIES.forEach(cat=>cat.rows.forEach((row,ri)=>{
    const tr=document.getElementById('tr_'+cat.id+'_'+ri);
    if(tr)tr.classList.toggle('hidden-row',instFilter!=='all'&&row.inst!==instFilter);
  }));updateTotals();
}
function buildRatesPanel(){
  const grid=document.getElementById('rates-grid');grid.innerHTML='';
  RATE_DEFS.forEach(r=>{
    const div=document.createElement('div');div.className='rate-row';
    div.innerHTML='<span class="rate-label">'+r.label+'</span><input class="rate-inp" type="number" min="0" step="1000" value="'+rates[r.key]+'" data-key="'+r.key+'" />';
    grid.appendChild(div);
  });
  grid.addEventListener('input',e=>{
    const el=e.target;if(!el.dataset.key)return;
    rates[el.dataset.key]=parseFloat(el.value)||0;
    SALARY_ROWS.forEach((row,ri)=>{
      if(row.rateKey!==el.dataset.key)return;
      for(let y=1;y<=numYears;y++){
        if(state[sk('salary',ri,y,'budget_manual')]!==undefined)return;
        const auto=Math.round(getVal('salary',ri,y,'fte')*rates[row.rateKey]);
        setVal('salary',ri,y,'budget',auto);
        const inp=document.getElementById('bi_salary_'+ri+'_'+y);if(inp)inp.value=auto||'';
      }
    });updateTotals();
  });
}
function buildTable(cat){
  const years=Array.from({length:numYears},(_,i)=>i+1);
  let cols='<col style="width:150px"><col style="width:78px">';
  if(cat.hasFte)years.forEach(()=>{cols+='<col style="width:55px">';});
  years.forEach(()=>{cols+='<col style="width:105px">';});
  cols+='<col style="width:95px">';
  let thead='<thead><tr><th>Subcategory</th><th>Institution</th>';
  if(cat.hasFte)years.forEach(y=>{thead+='<th style="text-align:center">Y'+y+' FTE</th>';});
  years.forEach(y=>{thead+='<th class="budget-th" data-y="'+y+'" style="text-align:right">År '+y+' budget ('+(displayCurrency==='EUR'?'EUR':'DKK')+')</th>';});
  thead+='<th style="text-align:right">Total</th></tr></thead>';
  let tbody='<tbody>';
  cat.rows.forEach((row,ri)=>{
    const hide=instFilter!=='all'&&row.inst!==instFilter;
    tbody+='<tr id="tr_'+cat.id+'_'+ri+'"'+(hide?' class="hidden-row"':'')+'>'+
      '<td style="font-size:11px">'+row.sub+'</td>'+
      '<td><span class="inst-badge">'+row.inst+'</span></td>';
    if(cat.hasFte)years.forEach(y=>{
      const v=getVal(cat.id,ri,y,'fte')||'';
      tbody+='<td style="text-align:center"><input id="fi_'+cat.id+'_'+ri+'_'+y+'" class="num-inp" type="number" min="0" max="1" step="0.1" placeholder="0" value="'+v+'" style="width:50px;text-align:center" data-cat="'+cat.id+'" data-ri="'+ri+'" data-y="'+y+'" data-field="fte" /></td>';
    });
    years.forEach(y=>{
      const v=getVal(cat.id,ri,y,'budget')||'';
      tbody+='<td><input id="bi_'+cat.id+'_'+ri+'_'+y+'" class="num-inp" type="number" min="0" step="1000" placeholder="0" value="'+v+'" data-cat="'+cat.id+'" data-ri="'+ri+'" data-y="'+y+'" data-field="budget" /></td>';
    });
    let rowT=0;for(let y=1;y<=numYears;y++)rowT+=getVal(cat.id,ri,y,'budget');
    tbody+='<td class="row-total" id="rt_'+cat.id+'_'+ri+'">'+fmtDisplay(rowT)+'</td></tr>';
  });
  tbody+='</tbody>';
  return '<div class="tbl-wrap"><table><colgroup>'+cols+'</colgroup>'+thead+tbody+'</table></div>';
}
function render(){
  const container=document.getElementById('sections-container');container.innerHTML='';
  CATEGORIES.forEach(cat=>{
    const isOpen=collapsed[cat.id]!==true,ct=catTotal(cat.id);
    const sec=document.createElement('div');sec.className='section';
    sec.innerHTML=
      '<div class="section-header" id="sh-'+cat.id+'">'+
        '<span class="section-title">'+
          '<span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:'+cat.color+';border:1px solid '+cat.tcolor+'66"></span>'+
          cat.label+'</span>'+
        '<span style="display:flex;align-items:center;gap:10px">'+
          '<span class="section-total" id="sec-total-'+cat.id+'">'+fmtDisplay(ct)+'</span>'+
          '<i class="ti ti-chevron-down chevron'+(isOpen?' open':'')+'" ></i>'+
        '</span>'+
      '</div>'+
      '<div class="section-body" id="sb-'+cat.id+'" style="display:'+(isOpen?'block':'none')+'">'+
        buildTable(cat)+
        '<div class="section-foot">'+
          '<span class="section-foot-label">Subtotal — '+cat.label+'</span>'+
          '<span class="section-foot-val" id="sec-foot-'+cat.id+'">'+fmtDisplay(ct)+'</span>'+
        '</div>'+
      '</div>';
    container.appendChild(sec);
    sec.querySelector('#sh-'+cat.id).addEventListener('click',()=>{
      const cur=collapsed[cat.id]!==true;
      collapsed[cat.id]=cur;
      sec.querySelector('#sb-'+cat.id).style.display=cur?'none':'block';
      sec.querySelector('.chevron').classList.toggle('open',!cur);
    });
  });
  container.addEventListener('input',e=>{
    const el=e.target;if(!el.dataset.cat)return;
    const catId=el.dataset.cat,riN=parseInt(el.dataset.ri),yN=parseInt(el.dataset.y),field=el.dataset.field;
    if(field==='fte'){
      setVal(catId,riN,yN,'fte',el.value);
      const row=SALARY_ROWS[riN];
      if(row){
        const auto=Math.round((parseFloat(el.value)||0)*(rates[row.rateKey]||0));
        if(state[sk(catId,riN,yN,'budget_manual')]===undefined){
          setVal(catId,riN,yN,'budget',auto);
          const bi=document.getElementById('bi_'+catId+'_'+riN+'_'+yN);if(bi)bi.value=auto||'';
        }
      }
    } else if(field==='budget'){
      const v=parseFloat(el.value)||0;
      if(catId==='salary'){
        const row=SALARY_ROWS[riN];
        const auto=row?Math.round(getVal(catId,riN,yN,'fte')*(rates[row.rateKey]||0)):0;
        if(v!==auto)state[sk(catId,riN,yN,'budget_manual')]=v;
        else delete state[sk(catId,riN,yN,'budget_manual')];
      }
      setVal(catId,riN,yN,'budget',v);
    }
    updateTotals();
  });
  updateTotals();
}

// ── EXCEL EXPORT with styling ──
function exportExcel(){
  const btn=document.getElementById('export-btn');
  btn.disabled=true;btn.innerHTML='<i class="ti ti-loader"></i> Bygger Excel...';
  setTimeout(()=>{
    try{
      const years=Array.from({length:numYears},(_,i)=>i+1);
      const wb=XLSX.utils.book_new();

      // Build worksheet as array-of-arrays first
      const aoa=[];
      // Header
      const hdr=['Category','Subcategory','Institution'];
      years.forEach(y=>{hdr.push('Year '+y+' Budget (DKK)');hdr.push('Year '+y+' FTE');});
      hdr.push('Total (DKK)');
      aoa.push(hdr);

      const catMeta=[]; // track row indices for styling

      CATEGORIES.forEach(cat=>{
        const visRows=cat.rows.filter((row,ri)=>{
          if(instFilter!=='all'&&row.inst!==instFilter)return false;
          return years.some(y=>getVal(cat.id,ri,y,'budget')>0||getVal(cat.id,ri,y,'fte')>0);
        });
        if(!visRows.length)return;

        const dataStartRow=aoa.length; // 0-based
        visRows.forEach((row,i)=>{
          const ri=cat.rows.indexOf(row);
          const dr=[i===0?cat.label:'', row.sub, row.inst];
          let rowT=0;
          years.forEach(y=>{
            const bud=getVal(cat.id,ri,y,'budget');
            const fte=cat.hasFte?getVal(cat.id,ri,y,'fte'):'';
            dr.push(bud||0);dr.push(fte||'');rowT+=bud;
          });
          dr.push(rowT);
          aoa.push(dr);
        });

        // Subtotal row
        const sub=[cat.label+' — Total','',''];
        let subT=0;
        years.forEach(y=>{
          let yt=0;
          cat.rows.forEach((row,ri)=>{
            if(instFilter!=='all'&&row.inst!==instFilter)return;
            yt+=getVal(cat.id,ri,y,'budget');
          });
          sub.push(yt);sub.push('');subT+=yt;
        });
        sub.push(subT);
        const subtotalRow=aoa.length;
        aoa.push(sub);
        catMeta.push({dataStartRow,subtotalRow,label:cat.label});

        aoa.push([]); // spacer
      });

      // Grand total
      const gt=['GRAND TOTAL','',''];
      let grand=0;
      years.forEach(y=>{const yt=yearTotal(y);gt.push(yt);gt.push('');grand+=yt;});
      gt.push(grand);
      const grandRow=aoa.length;
      aoa.push(gt);

      const ws=XLSX.utils.aoa_to_sheet(aoa);

      // Column widths
      const colW=[{wch:22},{wch:36},{wch:18}];
      years.forEach(()=>{colW.push({wch:18});colW.push({wch:9});});
      colW.push({wch:18});
      ws['!cols']=colW;

      // ── Styling via !rows and cell styles ──
      const RED='C0392B', BLUE='D6E4F7', WHITE='FFFFFF';
      const totalCols=3+numYears*2+1;

      function styleCell(ws,r,c,opts){
        const addr=XLSX.utils.encode_cell({r,c});
        if(!ws[addr])ws[addr]={t:'z',v:''};
        ws[addr].s={
          font:{name:'Arial',bold:!!opts.bold,color:{rgb:opts.fontColor||'000000'},sz:opts.sz||10},
          fill:{patternType:'solid',fgColor:{rgb:opts.bg||WHITE}},
          alignment:{horizontal:c>=3?'right':'left',vertical:'center',wrapText:false,indent:opts.indent||0},
          border:{
            top:{style:'thin',color:{rgb:'CCCCCC'}},
            bottom:{style:'thin',color:{rgb:'CCCCCC'}},
            left:{style:'thin',color:{rgb:'CCCCCC'}},
            right:{style:'thin',color:{rgb:'CCCCCC'}},
          },
          numFmt:c>=3&&c<totalCols-1?'#,##0':'#,##0'
        };
      }

      // Style header row (row 0)
      for(let c=0;c<totalCols;c++){
        styleCell(ws,0,c,{bold:true,fontColor:'FFFFFF',bg:RED,sz:11});
        const addr=XLSX.utils.encode_cell({r:0,c});
        if(ws[addr])ws[addr].s.alignment={horizontal:c<3?'left':'right',vertical:'center',wrapText:true};
      }

      // Style data rows
      aoa.forEach((row,r)=>{
        if(r===0)return; // already done
        const isMeta=catMeta.find(m=>m.subtotalRow===r);
        const isGrand=r===grandRow;
        const isBlue=isMeta||isGrand;
        const isSpacer=row.every(v=>v===''||v===undefined);
        if(isSpacer)return;
        for(let c=0;c<totalCols;c++){
          styleCell(ws,r,c,{
            bold:isBlue,
            bg:isBlue?BLUE:WHITE,
            indent:c===1&&!isBlue?1:0
          });
        }
      });

      XLSX.utils.book_append_sheet(wb,ws,'Budget');

      // Assumptions sheet
      const assump=[['Lønsatser',''],['Rolle','DKK/år ved 1,0 FTE']];
      RATE_DEFS.forEach(r=>assump.push([r.label,rates[r.key]]));
      assump.push([]);assump.push(['EUR/DKK kurs',eurRate]);
      const aws=XLSX.utils.aoa_to_sheet(assump);
      aws['!cols']=[{wch:36},{wch:20}];
      XLSX.utils.book_append_sheet(wb,aws,'Forudsætninger');

      const wbout=XLSX.write(wb,{bookType:'xlsx',type:'base64',cellStyles:true});
      document.getElementById('dl-area').innerHTML='<a id="dl-link" href="data:application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;base64,'+wbout+'" download="Research_Budget.xlsx"><i class="ti ti-file-spreadsheet"></i> Download Research_Budget.xlsx</a>';
    }catch(err){
      document.getElementById('dl-area').innerHTML='<span style="font-size:12px;color:red">Fejl: '+err.message+'</span>';
    }
    btn.disabled=false;btn.innerHTML='<i class="ti ti-download"></i> Export Excel';
  },50);
}

document.getElementById('btn-dkk').addEventListener('click',()=>{
  displayCurrency='DKK';
  document.getElementById('btn-dkk').classList.add('active');
  document.getElementById('btn-eur').classList.remove('active');
  updateTotals();
});
document.getElementById('btn-eur').addEventListener('click',()=>{
  displayCurrency='EUR';
  document.getElementById('btn-eur').classList.add('active');
  document.getElementById('btn-dkk').classList.remove('active');
  updateTotals();
});
document.getElementById('year-btns').addEventListener('click',e=>{
  const btn=e.target.closest('.pill');if(!btn||!btn.dataset.y)return;
  numYears=parseInt(btn.dataset.y);
  document.querySelectorAll('#year-btns .pill').forEach(b=>b.classList.toggle('active',b.dataset.y==numYears));
  render();
});
document.getElementById('inst-btns').addEventListener('click',e=>{
  const btn=e.target.closest('.pill');if(!btn||!btn.dataset.inst)return;
  instFilter=btn.dataset.inst;
  document.querySelectorAll('#inst-btns .pill').forEach(b=>b.classList.toggle('active',b.dataset.inst===instFilter));
  applyInstFilter();
});
document.getElementById('rates-toggle').addEventListener('click',()=>{
  const body=document.getElementById('rates-body'),chev=document.getElementById('rates-chev');
  const open=body.style.display!=='none';
  body.style.display=open?'none':'block';chev.classList.toggle('open',!open);
});
document.getElementById('export-btn').addEventListener('click',exportExcel);
document.getElementById('rate-inp').addEventListener('input',e=>{
  eurRate=parseFloat(e.target.value)||7.4728;updateTotals();
});

buildRatesPanel();render();
</script>
</body>
</html>

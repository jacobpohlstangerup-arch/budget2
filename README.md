<!DOCTYPE html>
<html lang="da">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Forskningsbudget</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.44.0/tabler-icons.min.css"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Sortable/1.15.2/Sortable.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.8.2/jspdf.plugin.autotable.min.js"></script>
<style>
:root{
  --bg:#F7F6F3;--surface:#FFFFFF;--surface2:#F0EFE9;--surface3:#E8E6DE;
  --text:#1C1B18;--text2:#6B6860;--text3:#A8A69E;
  --accent:#C0392B;--accent-light:#FDECEA;
  --blue:#1A56B0;--blue-light:#EBF2FD;--blue-total:#D6E4F7;
  --green:#1A7A4A;--green-light:#E6F5ED;
  --border:#E2E0D8;--border2:#C8C6BC;
  --radius:8px;--radius-lg:12px;--radius-xl:16px;
  --shadow:0 1px 3px rgba(0,0,0,.08),0 1px 2px rgba(0,0,0,.06);
  font-family:'DM Sans',sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
body{background:var(--bg);color:var(--text);min-height:100vh;font-size:14px;line-height:1.5;}
.app{max-width:1120px;margin:0 auto;padding:2rem 1.25rem 5rem;}
.app-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.75rem;flex-wrap:wrap;gap:12px;}
.app-title{font-size:20px;font-weight:600;letter-spacing:-.3px;}
.app-title small{font-size:13px;font-weight:400;color:var(--text3);display:block;margin-top:1px;}
.header-controls{display:flex;align-items:center;gap:8px;flex-wrap:wrap;}
.pill-group{display:flex;gap:2px;background:var(--surface2);border-radius:var(--radius);padding:3px;}
.pill{padding:4px 11px;font-size:12px;font-weight:500;cursor:pointer;border:none;border-radius:6px;background:transparent;color:var(--text2);transition:all .15s;font-family:inherit;}
.pill.active{background:var(--surface);color:var(--text);box-shadow:var(--shadow);}
.lang-toggle{display:flex;border:1px solid var(--border2);border-radius:var(--radius);overflow:hidden;}
.lang-btn{padding:5px 10px;cursor:pointer;border:none;background:transparent;color:var(--text2);font-family:inherit;font-weight:600;font-size:12px;transition:all .15s;}
.lang-btn.active{background:var(--text);color:var(--bg);}
.icon-btn{display:inline-flex;align-items:center;gap:5px;padding:6px 13px;font-size:12px;font-weight:500;cursor:pointer;border:1px solid var(--border2);border-radius:var(--radius);background:var(--surface);color:var(--text);font-family:inherit;transition:all .15s;white-space:nowrap;}
.icon-btn:hover{background:var(--surface2);}
.icon-btn:disabled{opacity:.4;cursor:not-allowed;}
.icon-btn.primary{background:var(--accent);color:#fff;border-color:var(--accent);}
.icon-btn.primary:hover{background:#a93226;}
.icon-btn.success{background:var(--green);color:#fff;border-color:var(--green);}
.icon-btn.danger{color:var(--accent);border-color:transparent;background:transparent;}
.icon-btn.danger:hover{background:var(--accent-light);}
.icon-btn.ghost{border-color:transparent;background:transparent;color:var(--text2);}
.icon-btn.ghost:hover{background:var(--surface2);color:var(--text);}

/* Config bars */
.config-bar{display:flex;align-items:center;gap:10px;flex-wrap:wrap;padding:10px 14px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1rem;font-size:12px;color:var(--text2);}
.config-bar label{font-weight:500;white-space:nowrap;}
.config-bar input{font-size:12px;padding:4px 8px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;text-align:right;}
.config-sep{width:1px;height:20px;background:var(--border2);flex-shrink:0;}

/* Summary */
.summary-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:10px;margin-bottom:1.5rem;}
.metric{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:14px 16px;}
.metric-label{font-size:10px;color:var(--text3);text-transform:uppercase;letter-spacing:.6px;margin-bottom:4px;font-weight:600;}
.metric-value{font-size:15px;font-weight:600;font-family:'DM Mono',monospace;}

/* Panel (salary rates) */
.panel{border:1px solid var(--border);border-radius:var(--radius-lg);margin-bottom:1.25rem;overflow:hidden;background:var(--surface);}
.panel-header{display:flex;align-items:center;justify-content:space-between;padding:10px 16px;background:var(--surface2);cursor:pointer;user-select:none;}
.panel-title{font-size:12px;font-weight:600;text-transform:uppercase;letter-spacing:.4px;display:flex;align-items:center;gap:7px;color:var(--text2);}
.chevron{font-size:14px;color:var(--text3);transition:transform .2s;display:inline-block;}
.chevron.open{transform:rotate(180deg);}
.rates-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:8px;padding:14px 16px;}
.rate-row{display:flex;flex-direction:column;gap:3px;}
.rate-label{font-size:11px;color:var(--text2);font-weight:500;}
.rate-inp{font-size:12px;padding:4px 8px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;text-align:right;}
.rate-inp:focus{outline:none;box-shadow:0 0 0 2px var(--blue-light);border-color:var(--blue);}

/* Sections */
.sections-wrap{display:flex;flex-direction:column;gap:10px;margin-bottom:12px;}
.section{border:1px solid var(--border);border-radius:var(--radius-xl);overflow:hidden;background:var(--surface);}
.section-header{display:flex;align-items:center;gap:8px;padding:10px 14px;background:var(--surface2);cursor:pointer;user-select:none;}
.section-drag-handle{color:var(--text3);cursor:grab;font-size:16px;flex-shrink:0;}
.section-drag-handle:active{cursor:grabbing;}
.section-dot{width:10px;height:10px;border-radius:3px;flex-shrink:0;}
.section-name-wrap{flex:1;min-width:0;}
.section-name-inp{font-size:13px;font-weight:600;border:none;background:transparent;color:var(--text);font-family:'DM Sans',sans-serif;width:100%;outline:none;}
.section-name-inp:focus{background:var(--surface);border-radius:4px;padding:2px 6px;}
.section-controls{display:flex;align-items:center;gap:4px;flex-shrink:0;}
.section-total-badge{font-size:13px;font-weight:600;font-family:'DM Mono',monospace;white-space:nowrap;margin-right:6px;}
.section-body{border-top:1px solid var(--border);}
.section-desc-row{padding:8px 16px;border-bottom:1px solid var(--border);background:var(--bg);}

/* Table */
.tbl-wrap{overflow-x:auto;}
table{width:100%;border-collapse:collapse;font-size:12px;}
th{font-size:10px;font-weight:700;color:var(--text3);text-align:left;padding:7px 10px;border-bottom:1px solid var(--border);background:var(--surface2);white-space:nowrap;text-transform:uppercase;letter-spacing:.5px;}
th.r{text-align:right;}
td{padding:6px 10px;border-bottom:1px solid var(--border);vertical-align:top;color:var(--text);}
tr:last-child td{border-bottom:none;}
tr.data-row:hover td{background:#FAFAF8;}
tr.hidden-row{display:none;}
.drag-handle-cell{color:var(--text3);cursor:grab;width:20px;font-size:14px;}
.drag-handle-cell:active{cursor:grabbing;}

/* Inputs */
.num-inp{width:100%;font-size:12px;padding:3px 6px;border:1px solid transparent;border-radius:5px;background:transparent;color:var(--text);text-align:right;font-family:'DM Mono',monospace;}
.num-inp:hover{border-color:var(--border2);background:var(--bg);}
.num-inp:focus{outline:none;border-color:var(--blue);background:var(--surface);}
.text-inp{width:100%;font-size:12px;padding:3px 6px;border:1px solid transparent;border-radius:5px;background:transparent;color:var(--text);font-family:'DM Sans',sans-serif;}
.text-inp:hover{border-color:var(--border2);background:var(--bg);}
.text-inp:focus{outline:none;border-color:var(--blue);background:var(--surface);}
.desc-inp{font-size:11px;color:var(--text3);font-style:italic;}
.desc-inp::placeholder{color:var(--text3);}
.row-desc-cell{font-size:11px;color:var(--text3);font-style:italic;min-width:140px;}
.row-total{font-weight:600;text-align:right;font-family:'DM Mono',monospace;white-space:nowrap;}
.inst-badge{font-size:10px;padding:2px 6px;border-radius:4px;background:var(--surface2);color:var(--text3);font-weight:500;}

/* Subtotal / total rows */
.subtotal-row td{background:var(--blue-total)!important;font-weight:700;border-top:1px solid var(--border2);}
.subtotal-row td:first-child{font-family:'DM Sans',sans-serif;font-size:12px;font-weight:700;}
.subtotal-row .mono-cell{font-family:'DM Mono',monospace;}
.overhead-row td{background:#EBF5FF!important;font-size:11px;color:var(--blue);}
.overhead-row .mono-cell{font-family:'DM Mono',monospace;}
.grandtotal-row td{background:var(--blue-total)!important;font-weight:700;font-size:13px;border-top:2px solid var(--border2);}
.grandtotal-row .mono-cell{font-family:'DM Mono',monospace;}

/* Section footer */
.section-foot{display:flex;align-items:center;gap:8px;padding:8px 14px;border-top:1px solid var(--border);background:var(--surface2);}

/* Grand footer */
.grand-footer{display:flex;align-items:center;justify-content:space-between;padding:16px 20px;background:var(--surface);border:1px solid var(--border2);border-radius:var(--radius-xl);margin-top:1.25rem;}
.grand-label{font-size:14px;font-weight:600;color:var(--text2);}
.grand-val{font-size:22px;font-weight:700;font-family:'DM Mono',monospace;text-align:right;}
.grand-sub{font-size:12px;color:var(--text3);font-family:'DM Mono',monospace;text-align:right;margin-top:2px;}

/* Add section */
.add-section-btn{display:flex;align-items:center;justify-content:center;gap:8px;padding:12px;border:2px dashed var(--border2);border-radius:var(--radius-xl);background:transparent;color:var(--text3);font-size:13px;font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .15s;width:100%;margin-bottom:1.25rem;}
.add-section-btn:hover{border-color:var(--blue);color:var(--blue);background:var(--blue-light);}

/* DL area */
#dl-area{margin-bottom:10px;min-height:10px;}
#dl-link{display:inline-flex;align-items:center;gap:6px;padding:7px 16px;font-size:12px;font-weight:600;border:1px solid var(--green);border-radius:var(--radius);background:var(--green-light);color:var(--green);text-decoration:none;}

/* Modal */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);display:flex;align-items:center;justify-content:center;z-index:1000;padding:1rem;}
.modal{background:var(--surface);border-radius:var(--radius-xl);padding:24px;max-width:420px;width:100%;box-shadow:0 8px 32px rgba(0,0,0,.18);}
.modal h3{font-size:15px;font-weight:700;margin-bottom:16px;}
.modal label{font-size:11px;color:var(--text2);font-weight:600;text-transform:uppercase;letter-spacing:.4px;display:block;margin-bottom:4px;}
.modal input,.modal textarea,.modal select{width:100%;font-size:13px;padding:8px 10px;border:1px solid var(--border2);border-radius:var(--radius);background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;margin-bottom:12px;}
.modal textarea{height:70px;resize:vertical;}
.modal-actions{display:flex;gap:8px;justify-content:flex-end;margin-top:4px;}
.color-grid{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:12px;}
.color-swatch{width:26px;height:26px;border-radius:6px;cursor:pointer;border:3px solid transparent;transition:transform .1s;}
.color-swatch:hover{transform:scale(1.15);}
.color-swatch.selected{border-color:#000;}
</style>
</head>
<body>
<div class="app">

  <div class="app-header">
    <div>
      <div class="app-title">Forskningsbudget <span id="proj-title-display"></span></div>
      <small id="header-sub" style="font-size:12px;color:var(--text3);margin-top:2px;display:block">Budgetværktøj til fondsansøgninger</small>
    </div>
    <div class="header-controls">
      <div class="lang-toggle">
        <button class="lang-btn active" id="btn-da" onclick="setLang('da')">DA</button>
        <button class="lang-btn" id="btn-en" onclick="setLang('en')">EN</button>
      </div>
      <div class="pill-group" id="year-btns">
        <button class="pill active" data-y="1">1</button>
        <button class="pill" data-y="2">2</button>
        <button class="pill" data-y="3">3</button>
        <button class="pill" data-y="4">4</button>
        <button class="pill" data-y="5">5</button>
      </div>
      <div class="pill-group" id="inst-btns">
        <button class="pill active" data-inst="all" id="inst-all">Alle</button>
        <button class="pill" data-inst="Rigshospitalet">Rigshospitalet</button>
        <button class="pill" data-inst="DTU">DTU</button>
      </div>
      <div class="pill-group">
        <button class="pill active" id="btn-dkk" onclick="setCurrency('DKK')">DKK</button>
        <button class="pill" id="btn-eur" onclick="setCurrency('EUR')">EUR</button>
      </div>
      <button class="icon-btn success" onclick="exportPDF()"><i class="ti ti-file-type-pdf"></i> <span id="lbl-pdf">PDF-eksport</span></button>
      <button class="icon-btn" onclick="exportExcel()"><i class="ti ti-file-spreadsheet"></i> <span id="lbl-excel">Excel</span></button>
    </div>
  </div>

  <div id="dl-area"></div>

  <!-- Config row -->
  <div class="config-bar">
    <label id="lbl-project">Projekttitel</label>
    <input type="text" id="proj-title" placeholder="Indtast projekttitel…" style="width:220px;" oninput="document.getElementById('proj-title-display').textContent=this.value?'— '+this.value:''"/>
    <div class="config-sep"></div>
    <label id="lbl-eurrate">1 EUR =</label>
    <input type="number" id="rate-inp" value="7.4728" step="0.0001" style="width:80px"/>
    <span style="font-size:11px;color:var(--text3)">DKK</span>
    <div class="config-sep"></div>
    <label id="lbl-overhead">Overhead (%)</label>
    <input type="number" id="overhead-inp" value="0" min="0" max="100" step="0.5" style="width:60px"/>
    <span id="overhead-result" style="font-size:12px;font-weight:600;color:var(--blue);font-family:'DM Mono',monospace;display:none;"></span>
  </div>

  <!-- Salary rates -->
  <div class="panel" id="rates-panel">
    <div class="panel-header" onclick="togglePanel('rates')">
      <span class="panel-title"><i class="ti ti-coin"></i> <span id="lbl-ratesTitle">Lønsatser — DKK pr. år ved 1,0 FTE</span></span>
      <i class="ti ti-chevron-down chevron open" id="rates-chev"></i>
    </div>
    <div id="rates-body">
      <div class="rates-grid" id="rates-grid"></div>
      <div style="padding:0 16px 12px;font-size:11px;color:var(--text3)" id="lbl-ratesHint">Budget beregnes automatisk som FTE × lønsats. Budgetfeltet kan redigeres manuelt for at tilsidesætte.</div>
    </div>
  </div>

  <!-- Summary -->
  <div class="summary-grid" id="summary-grid"></div>

  <!-- Sections -->
  <div class="sections-wrap" id="sections-wrap"></div>

  <button class="add-section-btn" onclick="addSection()">
    <i class="ti ti-plus"></i> <span id="lbl-addCat">Tilføj kategori</span>
  </button>

  <!-- Grand total -->
  <div class="grand-footer">
    <span class="grand-label" id="lbl-grandTotal">Samlet total (alle år)</span>
    <div>
      <div class="grand-val" id="grand-val">0 kr.</div>
      <div class="grand-sub" id="grand-eur" style="display:none"></div>
      <div class="grand-sub" id="grand-oh" style="display:none"></div>
    </div>
  </div>
</div>

<script>
// ═══════════════════════════════════════════════════
//  TRANSLATIONS
// ═══════════════════════════════════════════════════
const T = {
  da: {
    appSub:'Budgetværktøj til fondsansøgninger',
    project:'Projekttitel', eurRate:'1 EUR =', overhead:'Overhead (%)',
    ratesTitle:'Lønsatser — DKK pr. år ved 1,0 FTE',
    ratesHint:'Budget beregnes automatisk som FTE × lønsats. Budgetfeltet kan redigeres manuelt for at tilsidesætte.',
    addCat:'Tilføj kategori', grandTotal:'Samlet total (alle år)',
    instAll:'Alle',
    sub:'Underkategori', inst:'Institution', fte:'FTE',
    budget:'Budget', total:'Total', desc:'Beskrivelse',
    subtotal:'Subtotal', addPerson:'+ Tilføj person', addRow:'+ Tilføj post',
    overheadRow:'Overhead', inclOverhead:'Inkl. overhead',
    save:'Gem', cancel:'Annuller', editCat:'Rediger kategori',
    catName:'Kategorinavn', catDesc:'Beskrivelse (valgfri)', catColor:'Farve',
    hasFte:'Lønkategori (FTE-baseret)',
    pdfExport:'PDF-eksport', excelExport:'Excel',
    delCatConfirm:'Slet denne kategori og alle dens poster?',
    yr: y=>`År ${y}`,
    salCats:{
      consultant_rh:'Speciallæge (RH)', pregrad_rh:'Prægraduat stipendiat (RH)',
      scientist_rh:'Forsker (RH)', phd_rh:'Ph.d.-studerende (RH)',
      tech_rh:'Forskningssygeplejerske (RH)', projempl_rh:'Projektansatte (RH)',
      projempl_dtu:'Projektansatte (DTU)', phd_dtu:'Ph.d.-studerende (DTU)',
      postdoc_dtu:'Postdoc (DTU)', pregrad_dtu:'Prægraduat stipendiat (DTU)',
    },
    catLabels:{
      salary:'Løn', operation:'Drift',
      dissemination:'Formidling, uddannelse og træning',
      admin:'Administration', supplement:'Projekttillæg',
    },
    rowLabels:{
      data_mgmt:'Datahåndtering', subcontractor:'Underleverandøromkostninger',
      bench_fee:'Bench fee', infrastructure:'Infrastruktur',
      proj_specific:'Projektspecifikke omkostninger', operating:'Driftsomkostninger',
      equipment_dtu:'Udstyr (DTU)', equipment_rh:'Udstyr (RH)',
      travel:'Rejseudgifter', training:'Uddannelse og kurser',
      conf_rh:'Konferencedeltagelse (RH)', conf_dtu:'Konferencedeltagelse (DTU)',
      collab_rh:'Samarbejdsaktiviteter (RH)', collab_dtu:'Samarbejdsaktiviteter (DTU)',
      publication:'Publikationsomkostninger',
      admin_direct:'Direkte administrative udgifter',
      supplement:'Projekttillæg',
    },
  },
  en: {
    appSub:'Budget tool for grant applications',
    project:'Project title', eurRate:'1 EUR =', overhead:'Overhead (%)',
    ratesTitle:'Salary rates — DKK per year at 1.0 FTE',
    ratesHint:'Budget is auto-calculated as FTE × salary rate. Edit the budget field manually to override.',
    addCat:'Add category', grandTotal:'Grand total (all years)',
    instAll:'All',
    sub:'Subcategory', inst:'Institution', fte:'FTE',
    budget:'Budget', total:'Total', desc:'Description',
    subtotal:'Subtotal', addPerson:'+ Add person', addRow:'+ Add line',
    overheadRow:'Overhead', inclOverhead:'Incl. overhead',
    save:'Save', cancel:'Cancel', editCat:'Edit category',
    catName:'Category name', catDesc:'Description (optional)', catColor:'Colour',
    hasFte:'Salary category (FTE-based)',
    pdfExport:'Export PDF', excelExport:'Excel',
    delCatConfirm:'Delete this category and all its lines?',
    yr: y=>`Year ${y}`,
    salCats:{
      consultant_rh:'Consultant, MD (RH)', pregrad_rh:'Pre-graduate scholar (RH)',
      scientist_rh:'Scientist / researcher (RH)', phd_rh:'PhD student (RH)',
      tech_rh:'Research nurse (RH)', projempl_rh:'Project employees (RH)',
      projempl_dtu:'Project employees (DTU)', phd_dtu:'PhD student (DTU)',
      postdoc_dtu:'Postdoc (DTU)', pregrad_dtu:'Pre-graduate scholar (DTU)',
    },
    catLabels:{
      salary:'Salary', operation:'Operation',
      dissemination:'Dissemination, training & education',
      admin:'Administration', supplement:'Project supplement',
    },
    rowLabels:{
      data_mgmt:'Data management', subcontractor:'Subcontractor costs',
      bench_fee:'Bench fee', infrastructure:'Infrastructure',
      proj_specific:'Project-specific costs', operating:'Operating expenses',
      equipment_dtu:'Equipment (DTU)', equipment_rh:'Equipment (RH)',
      travel:'Travel expenses', training:'Training & courses',
      conf_rh:'Conference participation (RH)', conf_dtu:'Conference participation (DTU)',
      collab_rh:'Collaborative activities (RH)', collab_dtu:'Collaborative activities (DTU)',
      publication:'Publication costs',
      admin_direct:'Direct administrative expenses',
      supplement:'Project supplement',
    },
  }
};

// ═══════════════════════════════════════════════════
//  STATE
// ═══════════════════════════════════════════════════
let lang='da', currency='DKK', eurRate=7.4728, numYears=1, instFilter='all', overheadPct=0;

const RATE_DEFS=[
  {key:'consultant_rh',default:1080000},{key:'pregrad_rh',default:150000},
  {key:'scientist_rh',default:624000},{key:'phd_rh',default:624000},
  {key:'tech_rh',default:504000},{key:'projempl_rh',default:550000},
  {key:'projempl_dtu',default:550000},{key:'phd_dtu',default:530000},
  {key:'postdoc_dtu',default:650000},{key:'pregrad_dtu',default:150000},
];
let rates={};
RATE_DEFS.forEach(r=>{rates[r.key]=r.default;});

const CAT_COLORS=['#185FA5','#0F6E56','#854F0B','#5F5E5A','#534AB7','#7B2D8B','#C0392B','#1A7A4A','#B7791F','#2B6CB0'];

function uid(){return Math.random().toString(36).slice(2,9);}
function mkRow(labelKey,label,inst,rateKey=''){
  return {id:uid(),labelKey,label,inst,rateKey,fte:{},budget:{},budgetManual:{},desc:''};
}

let categories=[
  {id:'salary',labelKey:'salary',label:'Løn',color:'#185FA5',hasFte:true,desc:'',rows:[
    mkRow('consultant_rh','Speciallæge (RH)','Rigshospitalet','consultant_rh'),
    mkRow('pregrad_rh','Prægraduat stipendiat (RH)','Rigshospitalet','pregrad_rh'),
    mkRow('scientist_rh','Forsker (RH)','Rigshospitalet','scientist_rh'),
    mkRow('phd_rh','Ph.d.-studerende (RH)','Rigshospitalet','phd_rh'),
    mkRow('tech_rh','Forskningssygeplejerske (RH)','Rigshospitalet','tech_rh'),
    mkRow('projempl_rh','Projektansatte (RH)','Rigshospitalet','projempl_rh'),
    mkRow('projempl_dtu','Projektansatte (DTU)','DTU','projempl_dtu'),
    mkRow('phd_dtu','Ph.d.-studerende (DTU)','DTU','phd_dtu'),
    mkRow('postdoc_dtu','Postdoc (DTU)','DTU','postdoc_dtu'),
    mkRow('pregrad_dtu','Prægraduat stipendiat (DTU)','DTU','pregrad_dtu'),
  ]},
  {id:'operation',labelKey:'operation',label:'Drift',color:'#0F6E56',hasFte:false,desc:'',rows:[
    mkRow('data_mgmt','Datahåndtering','DTU'),
    mkRow('subcontractor','Underleverandøromkostninger','Rigshospitalet'),
    mkRow('bench_fee','Bench fee','Rigshospitalet'),
    mkRow('infrastructure','Infrastruktur','DTU'),
    mkRow('proj_specific','Projektspecifikke omkostninger','Rigshospitalet'),
    mkRow('operating','Driftsomkostninger','Rigshospitalet'),
    mkRow('equipment_dtu','Udstyr (DTU)','DTU'),
    mkRow('equipment_rh','Udstyr (RH)','Rigshospitalet'),
  ]},
  {id:'dissemination',labelKey:'dissemination',label:'Formidling, uddannelse og træning',color:'#854F0B',hasFte:false,desc:'',rows:[
    mkRow('travel','Rejseudgifter','Rigshospitalet'),
    mkRow('training','Uddannelse og kurser','Rigshospitalet'),
    mkRow('conf_rh','Konferencedeltagelse (RH)','Rigshospitalet'),
    mkRow('conf_dtu','Konferencedeltagelse (DTU)','DTU'),
    mkRow('collab_rh','Samarbejdsaktiviteter (RH)','Rigshospitalet'),
    mkRow('collab_dtu','Samarbejdsaktiviteter (DTU)','DTU'),
    mkRow('publication','Publikationsomkostninger','Rigshospitalet'),
  ]},
  {id:'admin',labelKey:'admin',label:'Administration',color:'#5F5E5A',hasFte:false,desc:'',rows:[
    mkRow('admin_direct','Direkte administrative udgifter','Rigshospitalet'),
  ]},
  {id:'supplement',labelKey:'supplement',label:'Projekttillæg',color:'#534AB7',hasFte:false,desc:'',rows:[
    mkRow('supplement','Projekttillæg','DTU'),
  ]},
];
let collapsed={};

// ═══════════════════════════════════════════════════
//  FORMAT
// ═══════════════════════════════════════════════════
function fmtCur(n){
  let v=Math.round(n);
  if(currency==='EUR') v=Math.round(n/eurRate);
  const s=Math.abs(v).toLocaleString('da-DK');
  return currency==='EUR'?`€ ${s}`:`${s} kr.`;
}
function fmtDKK(n){ return Math.round(n).toLocaleString('da-DK')+' kr.'; }
function yrs(){return Array.from({length:numYears},(_,i)=>i+1);}

// ═══════════════════════════════════════════════════
//  LABEL RESOLUTION
// ═══════════════════════════════════════════════════
function rowLabel(row){
  if(row.rateKey && T[lang].salCats[row.rateKey]){
    const da=T.da.salCats[row.rateKey], en=T.en.salCats[row.rateKey];
    if(row.label===da||row.label===en) return T[lang].salCats[row.rateKey];
  }
  if(row.labelKey && T[lang].rowLabels[row.labelKey]){
    const da=T.da.rowLabels[row.labelKey], en=T.en.rowLabels[row.labelKey];
    if(row.label===da||row.label===en) return T[lang].rowLabels[row.labelKey];
  }
  return row.label;
}
function catLabel(cat){
  if(cat.labelKey && T[lang].catLabels[cat.labelKey]){
    const da=T.da.catLabels[cat.labelKey], en=T.en.catLabels[cat.labelKey];
    if(cat.label===da||cat.label===en) return T[lang].catLabels[cat.labelKey];
  }
  return cat.label;
}

// ═══════════════════════════════════════════════════
//  TOTALS
// ═══════════════════════════════════════════════════
function rowBudget(row,y){return row.budget[y]||0;}
function catTotal(cat){
  let t=0;
  cat.rows.forEach(row=>{
    if(instFilter!=='all'&&row.inst!==instFilter)return;
    yrs().forEach(y=>{t+=rowBudget(row,y);});
  });
  return t;
}
function yearGrand(y){
  let t=0;
  categories.forEach(cat=>cat.rows.forEach(row=>{
    if(instFilter!=='all'&&row.inst!==instFilter)return;
    t+=rowBudget(row,y);
  }));
  return t;
}
function grandTotal(){let t=0;yrs().forEach(y=>{t+=yearGrand(y);});return t;}

// ═══════════════════════════════════════════════════
//  UPDATE TOTALS (no re-render)
// ═══════════════════════════════════════════════════
function updateTotals(){
  const gt=grandTotal();
  const oh=overheadPct>0?Math.round(gt*overheadPct/100):0;

  // Grand footer
  document.getElementById('grand-val').textContent=fmtCur(gt);
  const eurEl=document.getElementById('grand-eur');
  eurEl.style.display=currency==='DKK'&&eurRate>0?'block':'none';
  if(currency==='DKK') eurEl.textContent='≈ € '+Math.round(gt/eurRate).toLocaleString('da-DK');
  const ohEl=document.getElementById('grand-oh');
  if(overheadPct>0){
    ohEl.style.display='block';
    ohEl.textContent=T[lang].inclOverhead+': '+fmtCur(gt+oh);
    document.getElementById('overhead-result').style.display='inline';
    document.getElementById('overhead-result').textContent=T[lang].overheadRow+': '+fmtCur(oh);
  } else {
    ohEl.style.display='none';
    document.getElementById('overhead-result').style.display='none';
  }

  // Summary cards
  const sg=document.getElementById('summary-grid');sg.innerHTML='';
  yrs().forEach(y=>{
    const yt=yearGrand(y);
    const m=document.createElement('div');m.className='metric';
    m.innerHTML=`<div class="metric-label">${T[lang].yr(y)}</div><div class="metric-value">${fmtCur(yt)}</div>`;
    sg.appendChild(m);
  });

  // Per-category
  categories.forEach(cat=>{
    const ct=catTotal(cat);
    const el=document.getElementById('sec-total-'+cat.id);
    if(el) el.textContent=fmtCur(ct);

    cat.rows.forEach(row=>{
      let rowT=0;yrs().forEach(y=>{rowT+=rowBudget(row,y);});
      const rt=document.getElementById('rt_'+row.id);
      if(rt) rt.textContent=fmtCur(rowT);
    });

    // Subtotal row cells
    yrs().forEach(y=>{
      let yt=0;
      cat.rows.forEach(row=>{
        if(instFilter!=='all'&&row.inst!==instFilter)return;
        yt+=rowBudget(row,y);
      });
      const sc=document.getElementById(`sc_${cat.id}_${y}`);
      if(sc) sc.textContent=fmtCur(yt);
      const oc=document.getElementById(`oc_${cat.id}_${y}`);
      if(oc&&overheadPct>0) oc.textContent=fmtCur(Math.round(yt*overheadPct/100));
    });
    const stot=document.getElementById('sc_'+cat.id+'_total');
    if(stot) stot.textContent=fmtCur(ct);
    const otot=document.getElementById('oc_'+cat.id+'_total');
    if(otot) otot.textContent=fmtCur(Math.round(ct*overheadPct/100));

    // Overhead row visibility
    const ohRow=document.getElementById('oh_'+cat.id);
    if(ohRow) ohRow.style.display=overheadPct>0?'':'none';
  });

  // Column headers
  document.querySelectorAll('.budget-th').forEach(th=>{
    const y=th.dataset.y;
    th.textContent=`${T[lang].yr(y)} ${T[lang].budget} (${currency})`;
  });
}

// ═══════════════════════════════════════════════════
//  LANGUAGE
// ═══════════════════════════════════════════════════
function setLang(l){
  lang=l;
  document.getElementById('btn-da').classList.toggle('active',l==='da');
  document.getElementById('btn-en').classList.toggle('active',l==='en');
  // Update static labels
  const lblMap={
    'lbl-pdf':'pdfExport','lbl-excel':'excelExport',
    'lbl-project':'project','lbl-eurrate':'eurRate','lbl-overhead':'overhead',
    'lbl-ratesTitle':'ratesTitle','lbl-ratesHint':'ratesHint',
    'lbl-addCat':'addCat','lbl-grandTotal':'grandTotal',
    'header-sub':'appSub',
  };
  Object.entries(lblMap).forEach(([id,k])=>{
    const el=document.getElementById(id);
    if(el&&T[lang][k]) el.textContent=T[lang][k];
  });
  document.getElementById('inst-all').textContent=T[lang].instAll;
  document.title=l==='da'?'Forskningsbudget':'Research Budget';
  buildRatesPanel();
  renderAll();
}

// ═══════════════════════════════════════════════════
//  CURRENCY
// ═══════════════════════════════════════════════════
function setCurrency(c){
  currency=c;
  document.getElementById('btn-dkk').classList.toggle('active',c==='DKK');
  document.getElementById('btn-eur').classList.toggle('active',c==='EUR');
  updateTotals();
}

// ═══════════════════════════════════════════════════
//  PANELS
// ═══════════════════════════════════════════════════
function togglePanel(id){
  const body=document.getElementById(id+'-body');
  const chev=document.getElementById(id+'-chev');
  if(!body)return;
  const open=body.style.display!=='none';
  body.style.display=open?'none':'block';
  chev.classList.toggle('open',!open);
}

// ═══════════════════════════════════════════════════
//  SALARY RATES PANEL
// ═══════════════════════════════════════════════════
function buildRatesPanel(){
  const grid=document.getElementById('rates-grid');grid.innerHTML='';
  RATE_DEFS.forEach(r=>{
    const lbl=T[lang].salCats[r.key]||r.key;
    const div=document.createElement('div');div.className='rate-row';
    div.innerHTML=`<span class="rate-label">${lbl}</span><input class="rate-inp" type="number" min="0" step="1000" value="${rates[r.key]}" data-key="${r.key}"/>`;
    grid.appendChild(div);
  });
}
document.getElementById('rates-grid').addEventListener('input',e=>{
  const el=e.target;if(!el.dataset.key)return;
  rates[el.dataset.key]=parseFloat(el.value)||0;
  recalcSalary(el.dataset.key);
  updateTotals();
});
function recalcSalary(rateKey){
  categories.forEach(cat=>{
    if(!cat.hasFte)return;
    cat.rows.forEach(row=>{
      if(row.rateKey!==rateKey)return;
      yrs().forEach(y=>{
        if(row.budgetManual[y])return;
        row.budget[y]=Math.round((row.fte[y]||0)*(rates[rateKey]||0));
        const inp=document.getElementById(`bi_${row.id}_${y}`);
        if(inp)inp.value=row.budget[y]||'';
      });
    });
  });
}

// ═══════════════════════════════════════════════════
//  RENDER ALL
// ═══════════════════════════════════════════════════
function renderAll(){
  const wrap=document.getElementById('sections-wrap');
  wrap.innerHTML='';
  categories.forEach(cat=>wrap.appendChild(buildSection(cat)));
  initSortableSections();
  updateTotals();
}

// ═══════════════════════════════════════════════════
//  BUILD SECTION
// ═══════════════════════════════════════════════════
function esc(s){return (s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/"/g,'&quot;');}

function buildSection(cat){
  const isOpen=collapsed[cat.id]!==true;
  const sec=document.createElement('div');
  sec.className='section';sec.dataset.catId=cat.id;

  // Header
  const hdr=document.createElement('div');hdr.className='section-header';
  hdr.innerHTML=`
    <i class="ti ti-grip-vertical section-drag-handle"></i>
    <div class="section-dot" style="background:${cat.color}"></div>
    <div class="section-name-wrap">
      <input class="section-name-inp" type="text" value="${esc(catLabel(cat))}"
        onclick="event.stopPropagation()"
        onchange="renameCat('${cat.id}',this.value)"/>
    </div>
    <div class="section-controls">
      <span class="section-total-badge" id="sec-total-${cat.id}">${fmtCur(catTotal(cat))}</span>
      <button class="icon-btn ghost" onclick="event.stopPropagation();editSection('${cat.id}')" title="${T[lang].editCat}"><i class="ti ti-settings-2"></i></button>
      <button class="icon-btn danger" onclick="event.stopPropagation();delSection('${cat.id}')" title="Slet"><i class="ti ti-trash"></i></button>
      <i class="ti ti-chevron-down chevron ${isOpen?'open':''}" id="chev-${cat.id}"></i>
    </div>`;
  hdr.addEventListener('click',()=>toggleSec(cat.id));
  sec.appendChild(hdr);

  // Body
  const body=document.createElement('div');
  body.className='section-body';body.id='sb-'+cat.id;
  body.style.display=isOpen?'block':'none';

  // Category description
  const descRow=document.createElement('div');descRow.className='section-desc-row';
  descRow.innerHTML=`<input class="text-inp desc-inp" type="text" placeholder="${T[lang].catDesc}" value="${esc(cat.desc)}" style="width:100%"/>`;
  descRow.querySelector('input').addEventListener('change',e=>{cat.desc=e.target.value;});
  body.appendChild(descRow);

  body.appendChild(buildTable(cat));

  // Footer
  const foot=document.createElement('div');foot.className='section-foot';
  if(cat.hasFte){
    foot.innerHTML+=`<button class="icon-btn ghost" onclick="addPersonRow('${cat.id}')"><i class="ti ti-user-plus"></i> ${T[lang].addPerson}</button>`;
  }
  foot.innerHTML+=`<button class="icon-btn ghost" onclick="addRow('${cat.id}')"><i class="ti ti-plus"></i> ${T[lang].addRow}</button>`;
  body.appendChild(foot);
  sec.appendChild(body);
  return sec;
}

function toggleSec(catId){
  const isOpen=collapsed[catId]!==true;
  collapsed[catId]=isOpen;
  const body=document.getElementById('sb-'+catId);
  const chev=document.getElementById('chev-'+catId);
  if(body)body.style.display=isOpen?'none':'block';
  if(chev)chev.classList.toggle('open',!isOpen);
}

// ═══════════════════════════════════════════════════
//  BUILD TABLE
// ═══════════════════════════════════════════════════
function buildTable(cat){
  const wrap=document.createElement('div');wrap.className='tbl-wrap';
  const yr=yrs();

  let h=`<table><thead><tr>
    <th style="width:20px"></th>
    <th style="min-width:160px">${T[lang].sub}</th>
    <th style="min-width:140px">${T[lang].desc}</th>
    <th style="width:85px">${T[lang].inst}</th>`;
  if(cat.hasFte) yr.forEach(y=>{h+=`<th class="r" style="width:62px">${T[lang].yr(y)} ${T[lang].fte}</th>`;});
  yr.forEach(y=>{h+=`<th class="r budget-th" data-y="${y}" style="min-width:115px">${T[lang].yr(y)} ${T[lang].budget} (${currency})</th>`;});
  h+=`<th class="r" style="width:110px">${T[lang].total}</th></tr></thead>`;
  h+=`<tbody id="tbody-${cat.id}">`;

  cat.rows.forEach(row=>{h+=buildRowHTML(cat,row);});

  // Subtotal
  h+=`<tr class="subtotal-row"><td></td><td colspan="2" style="font-weight:700">${T[lang].subtotal} — ${catLabel(cat)}</td><td></td>`;
  if(cat.hasFte) yr.forEach(()=>{h+=`<td></td>`;});
  yr.forEach(y=>{h+=`<td class="r mono-cell" id="sc_${cat.id}_${y}"></td>`;});
  h+=`<td class="r mono-cell" id="sc_${cat.id}_total"></td></tr>`;

  // Overhead
  h+=`<tr class="overhead-row" id="oh_${cat.id}" style="${overheadPct>0?'':'display:none'}">
    <td></td><td colspan="2">${T[lang].overheadRow} (${overheadPct}%)</td><td></td>`;
  if(cat.hasFte) yr.forEach(()=>{h+=`<td></td>`;});
  yr.forEach(y=>{h+=`<td class="r mono-cell" id="oc_${cat.id}_${y}"></td>`;});
  h+=`<td class="r mono-cell" id="oc_${cat.id}_total"></td></tr>`;

  h+=`</tbody></table>`;
  wrap.innerHTML=h;

  // Sortable rows
  const tbody=wrap.querySelector('#tbody-'+cat.id);
  if(tbody){
    Sortable.create(tbody,{
      handle:'.drag-handle-cell',animation:120,
      onEnd(){
        const ids=[...tbody.querySelectorAll('tr.data-row')].map(tr=>tr.dataset.rowId);
        cat.rows.sort((a,b)=>ids.indexOf(a.id)-ids.indexOf(b.id));
        updateTotals();
      }
    });
  }
  return wrap;
}

function buildRowHTML(cat,row){
  const yr=yrs();
  const hide=instFilter!=='all'&&row.inst!==instFilter;
  let h=`<tr class="data-row${hide?' hidden-row':''}" data-row-id="${row.id}">
    <td class="drag-handle-cell"><i class="ti ti-grip-horizontal"></i></td>
    <td><input class="text-inp" type="text" value="${esc(rowLabel(row))}" onchange="renameRow('${cat.id}','${row.id}',this.value)"/></td>
    <td><input class="text-inp desc-inp" type="text" placeholder="${T[lang].desc}…" value="${esc(row.desc)}" onchange="onRowDesc('${cat.id}','${row.id}',this.value)"/></td>
    <td><span class="inst-badge">${row.inst}</span></td>`;
  if(cat.hasFte) yr.forEach(y=>{
    h+=`<td><input id="fi_${row.id}_${y}" class="num-inp" type="number" min="0" max="10" step="0.1" placeholder="0" value="${row.fte[y]||''}" style="width:56px;text-align:center" onchange="onFte('${cat.id}','${row.id}',${y},this.value)"/></td>`;
  });
  yr.forEach(y=>{
    h+=`<td><input id="bi_${row.id}_${y}" class="num-inp" type="number" min="0" step="1000" placeholder="0" value="${row.budget[y]||''}" onchange="onBudget('${cat.id}','${row.id}',${y},this.value)"/></td>`;
  });
  let rowT=0;yr.forEach(y=>{rowT+=rowBudget(row,y);});
  h+=`<td class="row-total" id="rt_${row.id}">${fmtCur(rowT)}</td></tr>`;
  return h;
}

// ═══════════════════════════════════════════════════
//  INPUT HANDLERS
// ═══════════════════════════════════════════════════
window.onFte=function(catId,rowId,y,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  row.fte[y]=parseFloat(val)||0;
  if(!row.budgetManual[y]){
    row.budget[y]=Math.round(row.fte[y]*(rates[row.rateKey]||0));
    const bi=document.getElementById(`bi_${rowId}_${y}`);
    if(bi)bi.value=row.budget[y]||'';
  }
  updateTotals();
};
window.onBudget=function(catId,rowId,y,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  const v=parseFloat(val)||0;
  if(cat.hasFte){
    const auto=Math.round((row.fte[y]||0)*(rates[row.rateKey]||0));
    row.budgetManual[y]=v!==auto;
  }
  row.budget[y]=v;
  updateTotals();
};
window.onRowDesc=function(catId,rowId,val){
  const cat=categories.find(c=>c.id===catId);
  const row=cat.rows.find(r=>r.id===rowId);
  row.desc=val;
};
window.renameRow=function(catId,rowId,val){
  categories.find(c=>c.id===catId).rows.find(r=>r.id===rowId).label=val;
};
window.renameCat=function(catId,val){
  categories.find(c=>c.id===catId).label=val;
  const sub=document.querySelector(`#tbody-${catId} .subtotal-row td:nth-child(2)`);
  if(sub) sub.textContent=T[lang].subtotal+' — '+val;
  updateTotals();
};

// ═══════════════════════════════════════════════════
//  SECTION ACTIONS
// ═══════════════════════════════════════════════════
window.addPersonRow=function(catId){
  const cat=categories.find(c=>c.id===catId);
  const tmpl=cat.rows[0]||{};
  const row=mkRow(tmpl.labelKey||'',rowLabel(tmpl)||'Ny person',tmpl.inst||'Rigshospitalet',tmpl.rateKey||'');
  cat.rows.push(row);renderAll();
};
window.addRow=function(catId){
  const cat=categories.find(c=>c.id===catId);
  cat.rows.push(mkRow('',lang==='da'?'Ny post':'New line','Rigshospitalet'));
  renderAll();
};
window.delSection=function(catId){
  if(!confirm(T[lang].delCatConfirm))return;
  categories=categories.filter(c=>c.id!==catId);renderAll();
};
window.addSection=function(){
  const color=CAT_COLORS[categories.length%CAT_COLORS.length];
  categories.push({id:uid(),labelKey:'',label:lang==='da'?'Ny kategori':'New category',
    color,hasFte:false,desc:'',rows:[mkRow('',lang==='da'?'Ny post':'New line','Rigshospitalet')]});
  renderAll();
};

// ═══════════════════════════════════════════════════
//  EDIT SECTION MODAL
// ═══════════════════════════════════════════════════
window.editSection=function(catId){
  const cat=categories.find(c=>c.id===catId);
  const overlay=document.createElement('div');overlay.className='modal-overlay';
  overlay.innerHTML=`<div class="modal">
    <h3>${T[lang].editCat}</h3>
    <label>${T[lang].catName}</label><input id="m-name" value="${esc(catLabel(cat))}"/>
    <label>${T[lang].catDesc}</label><textarea id="m-desc">${esc(cat.desc)}</textarea>
    <label>${T[lang].catColor}</label>
    <div class="color-grid">${CAT_COLORS.map(c=>`<div class="color-swatch${c===cat.color?' selected':''}" style="background:${c}" data-c="${c}" onclick="pickColor(this)"></div>`).join('')}</div>
    <label><input id="m-fte" type="checkbox" ${cat.hasFte?'checked':''} style="width:auto;margin-right:6px;margin-bottom:0"/>${T[lang].hasFte}</label>
    <div style="margin-bottom:12px"></div>
    <div class="modal-actions">
      <button class="icon-btn" onclick="this.closest('.modal-overlay').remove()">${T[lang].cancel}</button>
      <button class="icon-btn primary" onclick="saveSection('${catId}',this)">${T[lang].save}</button>
    </div>
  </div>`;
  document.body.appendChild(overlay);
  overlay.addEventListener('click',e=>{if(e.target===overlay)overlay.remove();});
};
window.pickColor=function(el){
  el.closest('.color-grid').querySelectorAll('.color-swatch').forEach(s=>s.classList.remove('selected'));
  el.classList.add('selected');
};
window.saveSection=function(catId,btn){
  const ov=btn.closest('.modal-overlay');
  const cat=categories.find(c=>c.id===catId);
  cat.label=ov.querySelector('#m-name').value;
  cat.labelKey=''; // custom label, no auto-translate
  cat.desc=ov.querySelector('#m-desc').value;
  cat.hasFte=ov.querySelector('#m-fte').checked;
  const sel=ov.querySelector('.color-swatch.selected');
  if(sel)cat.color=sel.dataset.c;
  ov.remove();renderAll();
};

// ═══════════════════════════════════════════════════
//  SORTABLE SECTIONS
// ═══════════════════════════════════════════════════
function initSortableSections(){
  const wrap=document.getElementById('sections-wrap');
  Sortable.create(wrap,{handle:'.section-drag-handle',animation:150,
    onEnd(){
      const ids=[...wrap.querySelectorAll('.section')].map(el=>el.dataset.catId);
      categories.sort((a,b)=>ids.indexOf(a.id)-ids.indexOf(b.id));
    }
  });
}

// ═══════════════════════════════════════════════════
//  INST FILTER
// ═══════════════════════════════════════════════════
function applyInstFilter(){
  categories.forEach(cat=>cat.rows.forEach(row=>{
    const tr=document.querySelector(`tr[data-row-id="${row.id}"]`);
    if(tr)tr.classList.toggle('hidden-row',instFilter!=='all'&&row.inst!==instFilter);
  }));
  updateTotals();
}

// ═══════════════════════════════════════════════════
//  OVERHEAD
// ═══════════════════════════════════════════════════
document.getElementById('overhead-inp').addEventListener('input',e=>{
  overheadPct=parseFloat(e.target.value)||0;
  // Update overhead row labels
  document.querySelectorAll('.overhead-row td:nth-child(2)').forEach(td=>{
    td.textContent=T[lang].overheadRow+(overheadPct>0?` (${overheadPct}%)`:'');
  });
  updateTotals();
});

// ═══════════════════════════════════════════════════
//  PDF EXPORT — professional jsPDF
// ═══════════════════════════════════════════════════
window.exportPDF=function(){
  const {jsPDF}=window.jspdf;
  const doc=new jsPDF({orientation:'landscape',unit:'mm',format:'a4'});
  const yr=yrs();
  const projTitle=document.getElementById('proj-title').value||'';
  const gt=grandTotal();
  const oh=overheadPct>0?Math.round(gt*overheadPct/100):0;
  const dateStr=new Date().toLocaleDateString(lang==='da'?'da-DK':'en-GB');

  // ── Fonts & colors ──
  const RED=[192,57,43], BLUE_HEADER=[26,86,176], BLUE_TOTAL=[214,228,247];
  const DARK=[28,27,24], GREY=[107,104,96], LIGHT_GREY=[240,239,233];

  // ── Header block ──
  doc.setFillColor(...RED);
  doc.rect(0,0,297,18,'F');
  doc.setTextColor(255,255,255);
  doc.setFontSize(13);doc.setFont(undefined,'bold');
  doc.text(lang==='da'?'Forskningsbudget':'Research Budget',10,11);
  if(projTitle){doc.setFontSize(10);doc.setFont(undefined,'normal');doc.text(projTitle,10,16);}
  doc.setFontSize(9);doc.text(dateStr,280,11,{align:'right'});

  let yPos=24;

  // ── For each category with data ──
  categories.forEach(cat=>{
    // Filter rows
    const visRows=cat.rows.filter(row=>{
      if(instFilter!=='all'&&row.inst!==instFilter)return false;
      return yr.some(y=>rowBudget(row,y)>0||(cat.hasFte&&(row.fte[y]||0)>0));
    });
    if(!visRows.length)return;

    // Page break check
    const estimatedHeight=12+(visRows.length+2)*8;
    if(yPos+estimatedHeight>190){doc.addPage();yPos=10;}

    // Category title bar
    doc.setFillColor(...hexToRgb(cat.color));
    doc.rect(8,yPos,281,7,'F');
    doc.setTextColor(255,255,255);
    doc.setFontSize(9);doc.setFont(undefined,'bold');
    doc.text(catLabel(cat).toUpperCase(),11,yPos+5);
    yPos+=7;

    // Category description
    if(cat.desc){
      doc.setTextColor(...GREY);doc.setFontSize(8);doc.setFont(undefined,'italic');
      doc.text(cat.desc,11,yPos+4);yPos+=6;
    }

    // Build table data
    // Columns: Subcategory | Description | Institution | [FTE y1..] | Budget y1.. | Total
    const head=[];
    const headRow=[T[lang].sub,T[lang].desc,T[lang].inst];
    if(cat.hasFte) yr.forEach(y=>{headRow.push(T[lang].yr(y)+'\n'+T[lang].fte);});
    yr.forEach(y=>{headRow.push(T[lang].yr(y)+'\n'+T[lang].budget);});
    headRow.push(T[lang].total);
    head.push(headRow);

    const body=[];
    visRows.forEach(row=>{
      const r=[rowLabel(row),row.desc||'',row.inst];
      if(cat.hasFte) yr.forEach(y=>{r.push((row.fte[y]||0)>0?(row.fte[y]||0).toLocaleString('da-DK'):'-');});
      yr.forEach(y=>{const b=rowBudget(row,y);r.push(b>0?fmtDKK(b):'-');});
      let rowT=0;yr.forEach(y=>{rowT+=rowBudget(row,y);});
      r.push(rowT>0?fmtDKK(rowT):'-');
      body.push(r);
    });

    // Subtotal row
    const subRow=[{content:T[lang].subtotal+' — '+catLabel(cat),colSpan:cat.hasFte?3+yr.length:3,styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,textColor:DARK}}];
    yr.forEach(y=>{
      let yt=0;visRows.forEach(row=>{yt+=rowBudget(row,y);});
      subRow.push({content:fmtDKK(yt),styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,halign:'right',textColor:DARK}});
    });
    let catT=0;visRows.forEach(row=>{yr.forEach(y=>{catT+=rowBudget(row,y);});});
    subRow.push({content:fmtDKK(catT),styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,halign:'right',textColor:DARK}});
    body.push(subRow);

    // Overhead row for this category
    if(overheadPct>0){
      const ohVal=Math.round(catT*overheadPct/100);
      const ohRow=[{content:`${T[lang].overheadRow} (${overheadPct}%)`,colSpan:cat.hasFte?3+yr.length:3,styles:{fontSize:8,textColor:BLUE_HEADER,fillColor:[235,245,255]}}];
      yr.forEach(y=>{
        let yt=0;visRows.forEach(row=>{yt+=rowBudget(row,y);});
        ohRow.push({content:fmtDKK(Math.round(yt*overheadPct/100)),styles:{fontSize:8,halign:'right',textColor:BLUE_HEADER,fillColor:[235,245,255]}});
      });
      ohRow.push({content:fmtDKK(ohVal),styles:{fontSize:8,halign:'right',textColor:BLUE_HEADER,fillColor:[235,245,255]}});
      body.push(ohRow);
    }

    // Determine column widths
    const nYrCols=yr.length*(cat.hasFte?2:1);
    const totalW=281;
    const subW=60,descW=55,instW=22,totW=30;
    const remW=totalW-subW-descW-instW-totW;
    const yrColW=Math.floor(remW/nYrCols);

    const colStyles={};
    let ci=0;
    colStyles[ci++]={cellWidth:subW,halign:'left'};
    colStyles[ci++]={cellWidth:descW,halign:'left',fontSize:7,fontStyle:'italic',textColor:GREY};
    colStyles[ci++]={cellWidth:instW,halign:'center',fontSize:7};
    if(cat.hasFte) yr.forEach(()=>{colStyles[ci++]={cellWidth:yrColW,halign:'right'};});
    yr.forEach(()=>{colStyles[ci++]={cellWidth:yrColW,halign:'right'};});
    colStyles[ci++]={cellWidth:totW,halign:'right',fontStyle:'bold'};

    doc.autoTable({
      head,body,
      startY:yPos,
      margin:{left:8,right:8},
      tableWidth:totalW,
      styles:{fontSize:8,cellPadding:2,lineColor:[226,224,216],lineWidth:0.2,textColor:DARK,font:'helvetica'},
      headStyles:{fillColor:BLUE_HEADER,textColor:[255,255,255],fontStyle:'bold',fontSize:7.5,halign:'center'},
      columnStyles:colStyles,
      didParseCell(data){
        if(data.row.index>0&&data.row.raw[0]&&typeof data.row.raw[0]==='object') return;
        // Alternate row shading
        if(data.section==='body'&&data.row.index%2===1&&!data.row.raw[0]?.styles){
          data.cell.styles.fillColor=[250,250,248];
        }
      },
    });
    yPos=doc.lastAutoTable.finalY+5;
  });

  // ── Grand total block ──
  if(yPos>185){doc.addPage();yPos=10;}
  yPos+=3;
  const gtCols=yr.length;
  const gtBody=[];
  const gtRow=[{content:lang==='da'?'SAMLET TOTAL (ALLE ÅR)':'GRAND TOTAL (ALL YEARS)',colSpan:3,styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,textColor:DARK,fontSize:9}}];
  yr.forEach(y=>{gtRow.push({content:fmtDKK(yearGrand(y)),styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,halign:'right',textColor:DARK,fontSize:9}});});
  gtRow.push({content:fmtDKK(gt),styles:{fontStyle:'bold',fillColor:BLUE_TOTAL,halign:'right',textColor:DARK,fontSize:10}});
  gtBody.push(gtRow);
  if(overheadPct>0){
    const ohRow=[{content:T[lang].inclOverhead+' ('+overheadPct+'%)',colSpan:3,styles:{fontStyle:'bold',fillColor:[214,234,248],textColor:BLUE_HEADER,fontSize:9}}];
    yr.forEach(y=>{ohRow.push({content:fmtDKK(Math.round(yearGrand(y)*overheadPct/100)+yearGrand(y)),styles:{fontStyle:'bold',fillColor:[214,234,248],halign:'right',textColor:BLUE_HEADER,fontSize:9}});});
    ohRow.push({content:fmtDKK(gt+oh),styles:{fontStyle:'bold',fillColor:[214,234,248],halign:'right',textColor:BLUE_HEADER,fontSize:10}});
    gtBody.push(ohRow);
  }
  doc.autoTable({
    body:gtBody,startY:yPos,margin:{left:8,right:8},tableWidth:281,
    styles:{lineColor:[192,57,43],lineWidth:0.3},
  });

  // ── Footer on all pages ──
  const pageCount=doc.internal.getNumberOfPages();
  for(let i=1;i<=pageCount;i++){
    doc.setPage(i);
    doc.setFontSize(7);doc.setTextColor(...GREY);doc.setFont(undefined,'normal');
    doc.text(`${lang==='da'?'Side':'Page'} ${i} / ${pageCount}`,289,205,{align:'right'});
    doc.text(lang==='da'?'Fortroligt — til intern brug':'Confidential — for internal use',8,205);
  }

  const fname=projTitle?`Budget_${projTitle.replace(/[^a-zA-Z0-9]/g,'_')}.pdf`:'Forskningsbudget.pdf';
  doc.save(fname);
};

function hexToRgb(hex){
  const r=parseInt(hex.slice(1,3),16);
  const g=parseInt(hex.slice(3,5),16);
  const b=parseInt(hex.slice(5,7),16);
  return [r,g,b];
}

// ═══════════════════════════════════════════════════
//  EXCEL EXPORT (via sendPrompt)
// ═══════════════════════════════════════════════════
window.exportExcel=function(){
  const payload=buildPayload();
  const msg='EXCEL_EXPORT_REQUEST:'+JSON.stringify(payload);
  document.getElementById('dl-area').innerHTML='<div style="font-size:12px;color:var(--text2);padding:6px 0">⏳ Sender budgetdata — Excel genereres…</div>';
  if(typeof sendPrompt==='function'){sendPrompt(msg);}
  else{navigator.clipboard.writeText(msg).then(()=>{document.getElementById('dl-area').innerHTML='<div style="font-size:12px;color:var(--text2)">📋 Kopieret til udklipsholder.</div>';});}
};

function buildPayload(){
  const yr=yrs();
  const payload={numYears,eurRate,currency,lang,overheadPct,
    projTitle:document.getElementById('proj-title').value,
    categories:[],rateDefs:RATE_DEFS.map(r=>({label:T[lang].salCats[r.key]||r.key,rate:rates[r.key]}))};
  categories.forEach(cat=>{
    const visRows=cat.rows.filter(row=>{
      if(instFilter!=='all'&&row.inst!==instFilter)return false;
      return yr.some(y=>rowBudget(row,y)>0||(cat.hasFte&&(row.fte[y]||0)>0));
    }).map(row=>({label:rowLabel(row),inst:row.inst,desc:row.desc,
      years:yr.map(y=>({budget:rowBudget(row,y),fte:cat.hasFte?(row.fte[y]||0):null}))}));
    if(visRows.length) payload.categories.push({label:catLabel(cat),hasFte:cat.hasFte,desc:cat.desc,rows:visRows});
  });
  return payload;
}

// ═══════════════════════════════════════════════════
//  EVENTS
// ═══════════════════════════════════════════════════
document.getElementById('year-btns').addEventListener('click',e=>{
  const b=e.target.closest('.pill');if(!b||!b.dataset.y)return;
  numYears=parseInt(b.dataset.y);
  document.querySelectorAll('#year-btns .pill').forEach(p=>p.classList.toggle('active',p.dataset.y==numYears));
  renderAll();
});
document.getElementById('inst-btns').addEventListener('click',e=>{
  const b=e.target.closest('.pill');if(!b||!b.dataset.inst)return;
  instFilter=b.dataset.inst;
  document.querySelectorAll('#inst-btns .pill').forEach(p=>p.classList.toggle('active',p.dataset.inst===instFilter));
  applyInstFilter();
});
document.getElementById('rate-inp').addEventListener('input',e=>{eurRate=parseFloat(e.target.value)||7.4728;updateTotals();});

// ═══════════════════════════════════════════════════
//  INIT
// ═══════════════════════════════════════════════════
buildRatesPanel();
renderAll();
</script>
</body>
</html>

[OMS_ONE_MILLION_SERVICE (2).html](https://github.com/user-attachments/files/27461538/OMS_ONE_MILLION_SERVICE.2.html)
<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>ONE MILLION SERVICE</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap');
:root{
  --navy:#0f1e35;--navy2:#1a2d4f;--navy3:#243d63;
  --red:#c0272d;--red2:#e03035;
  --silver:#8a9bb0;--silverL:#b8c8d8;
  --bg:#07111f;--card:#0c1827;--card2:#101e30;
  --border:#1a2e4a;--text:#dce8f5;--muted:#5a7a9a;
  --gold:#d4a820;--green:#1eb87a;--orange:#e07830;--blue:#4a9eff;
}
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;}
h1,h2,h3,.serif{font-family:'Playfair Display',serif;}
input,select,textarea,button{font-family:'DM Sans',sans-serif;}
::-webkit-scrollbar{width:5px;height:5px;}
::-webkit-scrollbar-track{background:var(--navy);}
::-webkit-scrollbar-thumb{background:var(--navy3);border-radius:3px;}

#app-shell{display:flex;min-height:100vh;}
#sidebar{width:235px;background:var(--navy);border-right:1px solid var(--border);display:flex;flex-direction:column;transition:width .25s;flex-shrink:0;overflow:hidden;}
#sidebar.collapsed{width:58px;}
#main-area{flex:1;display:flex;flex-direction:column;min-width:0;}
#topbar{background:var(--navy);border-bottom:1px solid var(--border);padding:11px 22px;display:flex;justify-content:space-between;align-items:center;flex-shrink:0;position:sticky;top:0;z-index:50;}
#page-content{flex:1;padding:20px 22px;overflow-y:auto;}

/* LOGIN */
#login-wrap{min-height:100vh;background:var(--bg);display:flex;align-items:center;justify-content:center;padding:16px;position:relative;}
.login-bg{position:fixed;inset:0;pointer-events:none;background:radial-gradient(ellipse at 15% 50%,rgba(26,45,79,.6),transparent 55%),radial-gradient(ellipse at 85% 15%,rgba(192,39,45,.18),transparent 50%),radial-gradient(ellipse at 50% 90%,rgba(15,30,53,.8),transparent 60%);}
.login-card{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:38px;width:100%;max-width:430px;box-shadow:0 28px 70px rgba(0,0,0,.7);position:relative;z-index:1;}
.login-logo{text-align:center;margin-bottom:28px;}

/* SIDEBAR */
.sb-head{padding:14px 13px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;min-height:62px;}
.sb-logo{display:flex;align-items:center;gap:9px;overflow:hidden;flex:1;}
.globe{width:34px;height:34px;background:linear-gradient(135deg,var(--navy2),var(--navy3));border-radius:50%;display:flex;align-items:center;justify-content:center;border:2.5px solid var(--red);font-size:16px;flex-shrink:0;}
.logo-txt b{color:#fff;font-family:'Playfair Display',serif;font-size:12px;display:block;line-height:1.2;white-space:nowrap;}
.logo-txt small{color:var(--silver);font-size:10px;letter-spacing:1.5px;}
.toggle-btn{background:none;border:none;color:var(--muted);cursor:pointer;padding:5px;border-radius:6px;flex-shrink:0;}
.sb-nav{flex:1;padding:8px 7px;overflow-y:auto;}
.grp-lbl{color:var(--muted);font-size:10px;text-transform:uppercase;letter-spacing:1.5px;padding:2px 10px;margin:10px 0 3px;white-space:nowrap;}
.nb{width:100%;display:flex;align-items:center;gap:9px;padding:9px 11px;border-radius:8px;border:none;cursor:pointer;font-size:13px;font-family:'DM Sans',sans-serif;background:transparent;color:var(--muted);font-weight:400;border-left:3px solid transparent;transition:all .15s;text-align:left;}
.nb.active{background:rgba(192,39,45,.16);color:#fff;font-weight:600;border-left-color:var(--red);}
.nb:hover:not(.active){background:rgba(255,255,255,.04);color:var(--silverL);}
.nb svg{flex-shrink:0;color:inherit;}
.nb.active svg{color:var(--red);}
#sidebar.collapsed .nb{justify-content:center;padding:9px;}
#sidebar.collapsed .grp-lbl,#sidebar.collapsed .nb-lbl{display:none;}
.sb-foot{padding:11px 13px;border-top:1px solid var(--border);}
.logout-btn{width:100%;display:flex;align-items:center;gap:8px;background:rgba(192,39,45,.1);border:1px solid rgba(192,39,45,.28);border-radius:8px;color:var(--red);padding:9px 12px;cursor:pointer;font-size:13px;font-family:'DM Sans',sans-serif;font-weight:600;}
#sidebar.collapsed .sb-foot{padding:8px;}
#sidebar.collapsed .logout-btn{justify-content:center;}
#sidebar.collapsed .logout-btn span{display:none;}

/* TOPBAR */
.tb-right{display:flex;align-items:center;gap:9px;}
.user-chip{display:flex;align-items:center;gap:8px;background:var(--card2);border:1px solid var(--border);border-radius:8px;padding:6px 12px;cursor:default;}
.u-av{width:28px;height:28px;background:linear-gradient(135deg,var(--red),var(--red2));border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;color:#fff;}
.u-name{font-size:12px;font-weight:600;line-height:1.2;}
.u-role{font-size:10px;color:var(--gold);text-transform:uppercase;letter-spacing:.7px;}

/* BUTTONS */
.btn{display:inline-flex;align-items:center;gap:6px;border:none;border-radius:8px;cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600;transition:all .15s;white-space:nowrap;font-size:13px;}
.btn-p{background:linear-gradient(135deg,var(--red),var(--red2));color:#fff;padding:9px 17px;box-shadow:0 3px 12px rgba(192,39,45,.3);}
.btn-p:hover{transform:translateY(-1px);box-shadow:0 5px 16px rgba(192,39,45,.4);}
.btn-n{background:transparent;color:var(--muted);border:1px solid var(--border);padding:9px 15px;}
.btn-n:hover{border-color:var(--silver);color:var(--silverL);}
.btn-g{background:#152a1a;color:var(--green);border:1px solid rgba(30,184,122,.2);padding:8px 14px;font-weight:600;}
.btn-g:hover{background:#1a3520;}
.btn-b{background:rgba(74,158,255,.12);color:var(--blue);border:1px solid rgba(74,158,255,.25);padding:8px 14px;font-weight:600;}
.btn-sm{padding:6px 10px;font-size:12px;}
.btn-xs{padding:4px 8px;font-size:11px;}
.btn-ico{padding:6px 8px;}
.btn:disabled{opacity:.5;cursor:not-allowed;}

/* CARDS */
.card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:18px;}
.card-hover:hover{border-color:var(--navy3);}

/* BADGES */
.bdg{display:inline-flex;align-items:center;font-size:10px;font-weight:700;padding:3px 9px;border-radius:20px;text-transform:uppercase;letter-spacing:.7px;white-space:nowrap;}

/* INPUTS */
.inp{width:100%;background:var(--navy);border:1px solid var(--border);border-radius:8px;color:var(--text);padding:9px 13px;font-size:13px;outline:none;transition:border-color .15s;}
.inp:focus{border-color:var(--red);}
.inp[readonly]{opacity:.7;cursor:not-allowed;}
.lbl{color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:1px;margin-bottom:5px;display:block;}
.fg{margin-bottom:13px;}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:13px;}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;}
.cs2{grid-column:1/-1;}

/* MODAL */
.ov{position:fixed;inset:0;background:rgba(0,5,18,.93);z-index:300;display:flex;align-items:center;justify-content:center;padding:14px;backdrop-filter:blur(5px);}
.mb{background:var(--card);border:1px solid var(--border);border-radius:16px;width:100%;max-width:580px;max-height:95vh;overflow-y:auto;box-shadow:0 30px 80px rgba(0,0,0,.8);}
.mb.wide{max-width:860px;}
.mb.xl{max-width:1100px;}
.mh{display:flex;justify-content:space-between;align-items:center;padding:15px 22px;border-bottom:1px solid var(--border);background:var(--navy);border-radius:16px 16px 0 0;position:sticky;top:0;z-index:2;}
.mt{display:flex;align-items:center;gap:8px;color:var(--text);font-family:'Playfair Display',serif;font-size:15px;}
.mt::before{content:'';width:3px;height:17px;background:var(--red);border-radius:2px;display:inline-block;}
.mbody{padding:20px 22px;}
.mfoot{display:flex;gap:10px;justify-content:flex-end;margin-top:16px;}

/* KPI */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(170px,1fr));gap:12px;margin-bottom:18px;}
.kpi{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:15px;border-left-width:3px;border-left-style:solid;}
.kpi-l{color:var(--muted);font-size:10px;text-transform:uppercase;letter-spacing:1px;margin-bottom:7px;}
.kpi-v{font-size:21px;font-weight:800;margin-bottom:2px;}
.kpi-s{color:var(--muted);font-size:11px;}

/* TABLE */
.tbl{width:100%;border-collapse:collapse;font-size:13px;}
.tbl th{padding:9px 12px;text-align:left;font-size:11px;text-transform:uppercase;letter-spacing:.9px;color:var(--muted);border-bottom:1px solid var(--border);background:var(--navy);font-weight:600;}
.tbl td{padding:9px 12px;border-bottom:1px solid var(--border);}
.tbl tr:last-child td{border-bottom:none;}
.tbl tr:hover td{background:rgba(255,255,255,.018);}

/* PROGRESS */
.pt{background:var(--border);border-radius:99px;height:5px;overflow:hidden;}
.pf{height:100%;border-radius:99px;transition:width .4s;}

/* ALERTS */
.alert-w{background:#1a1000;border:1px solid rgba(212,168,32,.35);border-radius:10px;padding:12px 15px;margin-bottom:12px;}
.alert-r{background:#180808;border:1px solid rgba(192,39,45,.35);border-radius:10px;padding:12px 15px;margin-bottom:12px;}
.alert-g{background:#081510;border:1px solid rgba(30,184,122,.3);border-radius:10px;padding:12px 15px;margin-bottom:12px;}

/* PAGE HEADER */
.ph{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:18px;flex-wrap:wrap;gap:12px;}
.ph-title{font-family:'Playfair Display',serif;font-size:21px;color:var(--text);}
.ph-sub{color:var(--muted);font-size:13px;margin-top:3px;}
.ph-actions{display:flex;gap:8px;flex-wrap:wrap;}

/* TABS */
.tabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:16px;}
.tab{padding:7px 14px;border-radius:8px;border:1px solid var(--border);background:transparent;color:var(--muted);cursor:pointer;font-size:12px;font-weight:600;font-family:'DM Sans',sans-serif;transition:all .15s;}
.tab.active{border-color:var(--red);background:rgba(192,39,45,.18);color:var(--red);}
.tab:hover:not(.active){border-color:var(--silver);color:var(--silverL);}

/* SEARCH */
.sw{position:relative;margin-bottom:13px;}
.sw .si{position:absolute;left:12px;top:50%;transform:translateY(-50%);color:var(--muted);}
.sw input{padding-left:40px;}

/* DIVIDER */
hr.dv{border:none;border-top:1px solid var(--border);margin:14px 0;}

/* ITEM ROW TABLE */
.ir-grid{display:grid;grid-template-columns:3fr 1fr 1fr 1.4fr 1.2fr 28px;gap:6px;align-items:center;}
.ir-grid.hdr div{color:var(--muted);font-size:11px;text-transform:uppercase;margin-bottom:5px;}

/* PDF */
.pdf-wrap{background:#fff;color:#111;border-radius:8px;padding:32px;font-family:'DM Sans',sans-serif;font-size:13px;line-height:1.5;}
.pdf-hdr{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;padding-bottom:18px;border-bottom:3px solid #c0272d;}
.pdf-co{font-weight:800;font-size:18px;color:#1a2d4f;}
.pdf-badge{background:#c0272d;color:#fff;padding:5px 15px;border-radius:5px;font-weight:700;font-size:14px;display:inline-block;margin-bottom:4px;}
.pdf-tbl{width:100%;border-collapse:collapse;margin:14px 0;}
.pdf-tbl th{background:#1a2d4f;color:#fff;padding:8px 11px;font-size:11px;text-align:left;}
.pdf-tbl th:not(:first-child){text-align:right;}
.pdf-tbl td{padding:8px 11px;border-bottom:1px solid #eee;font-size:12px;}
.pdf-tbl td:not(:first-child){text-align:right;}
.pdf-tbl tr:nth-child(even) td{background:#f8f9fa;}
.pdf-total{background:#1a2d4f;color:#fff;border-radius:8px;padding:14px 18px;max-width:250px;margin-left:auto;margin-top:10px;}
.pdf-pay{background:#f0f4f8;border-radius:8px;padding:14px 16px;margin-top:14px;font-size:12px;}

/* STATUS COLORS */
.s-pendente{color:#8a9bb0;background:rgba(138,155,176,.15);}
.s-enviado{color:#4a9eff;background:rgba(74,158,255,.15);}
.s-aprovado{color:#1eb87a;background:rgba(30,184,122,.15);}
.s-rejeitado{color:#c0272d;background:rgba(192,39,45,.15);}
.s-pago{color:#1eb87a;background:rgba(30,184,122,.15);}
.s-parcial{color:#d4a820;background:rgba(212,168,32,.15);}
.s-ativo{color:#1eb87a;background:rgba(30,184,122,.15);}
.s-inativo{color:#c0272d;background:rgba(192,39,45,.15);}
.s-andamento{color:#d4a820;background:rgba(212,168,32,.15);}
.s-concluido{color:#1eb87a;background:rgba(30,184,122,.15);}
.s-ferias{color:#4a9eff;background:rgba(74,158,255,.15);}
.s-licenca{color:#e07830;background:rgba(224,120,48,.15);}

/* RESPONSIVE */
@media(max-width:700px){
  #sidebar{position:fixed;left:0;top:0;height:100vh;z-index:200;transform:translateX(-100%);transition:transform .25s;}
  #sidebar.mob-open{transform:translateX(0);}
  .g2,.g3,.g4{grid-template-columns:1fr;}
  .mb{max-width:100%;margin:8px;}
  #page-content{padding:14px;}
  .kpi-grid{grid-template-columns:1fr 1fr;}
}

/* PRINT */
@media print{
  #app-shell,#login-wrap{display:none!important;}
  #print-area{display:block!important;}
}
#print-area{display:none;}
</style>
</head>
<body>

<!-- ══════════ LOGIN ══════════ -->
<div id="login-wrap">
  <div class="login-bg"></div>
  <div style="width:100%;max-width:430px;position:relative;z-index:1;">
    <div class="login-logo" id="ll-area">
      <div style="display:inline-flex;align-items:center;gap:13px;margin-bottom:10px;">
        <div class="globe" style="width:54px;height:54px;font-size:22px;">🌐</div>
        <div style="text-align:left;">
          <div style="color:#fff;font-family:'Playfair Display',serif;font-weight:700;font-size:19px;">ONE MILLION</div>
          <div style="color:var(--silver);font-size:12px;letter-spacing:2px;">SERVICE</div>
        </div>
      </div>
      <div style="color:var(--muted);font-size:12px;">Moçambique · Sistema de Gestão Empresarial</div>
    </div>
    <div class="login-card">
      <div style="display:flex;align-items:center;gap:8px;margin-bottom:20px;">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--red)" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
        <span style="font-size:16px;font-weight:700;">Acesso ao Sistema</span>
      </div>
      <div class="fg"><label class="lbl">Utilizador</label>
        <input id="l-user" class="inp" placeholder="admin / vendas / financeiro / rh" onkeydown="if(event.key==='Enter')doLogin()"/></div>
      <div class="fg"><label class="lbl">Senha</label>
        <div style="position:relative;">
          <input id="l-pass" class="inp" type="password" placeholder="••••••••" style="padding-right:42px;" onkeydown="if(event.key==='Enter')doLogin()"/>
          <button onclick="togglePass()" style="position:absolute;right:11px;top:50%;transform:translateY(-50%);background:none;border:none;color:var(--muted);cursor:pointer;font-size:15px;">👁</button>
        </div>
      </div>
      <div id="l-err" style="display:none;" class="alert-r" style="font-size:13px;">⚠️ Utilizador ou senha incorretos.</div>
      <button class="btn btn-p" style="width:100%;justify-content:center;padding:12px;font-size:14px;" onclick="doLogin()">Entrar no Sistema</button>
      <hr class="dv"/>
      <div style="color:var(--muted);font-size:11px;text-align:center;">
        <b style="color:var(--silverL);">admin</b> / <b style="color:var(--silverL);">vendas</b> / <b style="color:var(--silverL);">financeiro</b> / <b style="color:var(--silverL);">rh</b><br/>
        Senha: [utilizador]123
      </div>
    </div>
    <div style="text-align:center;margin-top:16px;color:var(--muted);font-size:11px;">ONE MILLION SERVICE · v3.0 · Moçambique</div>
  </div>
</div>

<!-- ══════════ APP ══════════ -->
<div id="app-shell" style="display:none;">
  <div id="sidebar">
    <div class="sb-head">
      <div class="sb-logo" id="sb-logo">
        <div class="globe">🌐</div>
        <div class="logo-txt"><b>ONE MILLION</b><small>SERVICE</small></div>
      </div>
      <button class="toggle-btn" onclick="toggleNav()">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="18" x2="21" y2="18"/></svg>
      </button>
    </div>
    <nav class="sb-nav" id="sb-nav"></nav>
    <div class="sb-foot">
      <button class="logout-btn" onclick="doLogout()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"/><polyline points="16 17 21 12 16 7"/><line x1="21" y1="12" x2="9" y2="12"/></svg>
        <span>Terminar Sessão</span>
      </button>
    </div>
  </div>
  <div id="main-area">
    <div id="topbar">
      <span style="color:var(--muted);font-size:13px;" id="tb-title">Dashboard</span>
      <div class="tb-right">
        <button class="btn btn-g btn-sm" onclick="goTo('cotacoes')">+ Cotação</button>
        <button class="btn btn-p btn-sm" onclick="goTo('vendas-nova')">+ Venda</button>
        <div class="user-chip">
          <div class="u-av" id="tb-av">A</div>
          <div><div class="u-name" id="tb-name">Admin</div><div class="u-role" id="tb-role">ADMIN</div></div>
        </div>
      </div>
    </div>
    <div id="page-content"></div>
  </div>
</div>
<div id="modal-ov" class="ov" style="display:none;" onclick="if(event.target===this)closeModal()">
  <div id="modal-box" class="mb">
    <div class="mh"><div class="mt" id="m-title">Título</div>
      <button onclick="closeModal()" style="background:rgba(255,255,255,.05);border:none;color:var(--muted);cursor:pointer;padding:7px;border-radius:7px;display:flex;">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
      </button>
    </div>
    <div class="mbody" id="m-body"></div>
  </div>
</div>
<div id="print-area"></div>

<script>

// ════════════════════════════════════════════════════════════
// CONSTANTES E CONFIGURAÇÃO
// ════════════════════════════════════════════════════════════
const USERS_LIST=[
  {id:1,nome:"Administrador",user:"admin",pass:"admin123",nivel:"admin",av:"A"},
  {id:2,nome:"Agente de Vendas",user:"vendas",pass:"vendas123",nivel:"vendas",av:"V"},
  {id:3,nome:"Gestor Financeiro",user:"financeiro",pass:"fin123",nivel:"financeiro",av:"F"},
  {id:4,nome:"Gestor de RH",user:"rh",pass:"rh123",nivel:"rh",av:"R"},
];
const PERMS={
  admin:["dash","clientes","cotacoes","vendas","vendas-nova","estoque","obras","financeiro","rh-mod","relatorios","config"],
  vendas:["dash","clientes","cotacoes","vendas","vendas-nova","estoque"],
  financeiro:["dash","vendas","financeiro","relatorios"],
  rh:["dash","rh-mod","relatorios"],
};
const DEFAULT_CFG={
  empresa:"ONE MILLION SERVICE",slogan:"Construção · Móveis · Design · Paletes",
  pais:"Moçambique",cidade:"Maputo",end:"Av. Julius Nyerere, 1234",
  tel:"+258 84 000 0000",email:"geral@onemillion.co.mz",website:"www.onemillion.co.mz",
  nuit:"100123456",moeda:"MZN",iva:16,logo:null,
  termos:"1. Os preços são válidos pelo período indicado.\n2. Pagamento conforme condições acordadas.\n3. Prazo de entrega a confirmar após aprovação.\n4. A ONE MILLION SERVICE reserva-se o direito de ajustar preços em caso de variação cambial.",
  rodape:"Obrigado pela sua confiança! · ONE MILLION SERVICE",
  msg_wa:"Prezado(a) {cliente},\n\nAdjunto segue a nossa {tipo} nº {numero}.\nValor total: {total}\n\nAgradecemos a sua preferência!\n\nAtenciosamente,\n{empresa}\n{tel}",
  pagamentos:[
    {id:1,tipo:"banco",nome:"BIM - Millennium Bim",conta:"1234 5678 9012 3456",titular:"ONE MILLION SERVICE LDA",ativo:true},
    {id:2,tipo:"banco",nome:"BCI",conta:"9876 5432 1098 7654",titular:"ONE MILLION SERVICE LDA",ativo:true},
    {id:3,tipo:"mpesa",nome:"M-Pesa",numero:"+258 84 000 0000",titular:"ONE MILLION SERVICE",ativo:true},
    {id:4,tipo:"emola",nome:"e-Mola",numero:"+258 86 000 0000",titular:"ONE MILLION SERVICE",ativo:true},
    {id:5,tipo:"numerario",nome:"Numerário / Dinheiro",conta:"",titular:"",ativo:true},
  ],
};

// ════════════════════════════════════════════════════════════
// BASE DE DADOS
// ════════════════════════════════════════════════════════════
function loadDB(){
  try{const r=localStorage.getItem("oms4_db");if(r)return JSON.parse(r);}catch(e){}
  const d=initDB();saveDB(d);return d;
}
function saveDB(d){localStorage.setItem("oms4_db",JSON.stringify(d));}
function initDB(){
  return{
    cfg:{...DEFAULT_CFG},
    cotSeq:4,vendSeq:2,fatSeq:1,
    clientes:[
      {id:1,nome:"Armando Muianga",tel:"+258 84 123 4567",email:"armando@email.co.mz",tipo:"empresa",nuit:"123456789",end:"Av. Julius Nyerere, 1234, Maputo",status:"ativo",obs:""},
      {id:2,nome:"Fátima Cossa",tel:"+258 82 987 6543",email:"fatima@email.co.mz",tipo:"particular",nuit:"",end:"Beira, Sofala",status:"ativo",obs:""},
      {id:3,nome:"Construtora Nhongo Lda",tel:"+258 86 456 7890",email:"geral@nhongo.co.mz",tipo:"empresa",nuit:"987654321",end:"Nampula, Av. Trabalho",status:"ativo",obs:""},
    ],
    cotacoes:[
      {id:1,num:"COT-2026-001",cliId:1,cliNome:"Armando Muianga",data:"2026-04-15",val:"2026-04-30",
       itens:[{desc:"Cozinha em MDF lacado branco",qty:1,un:"un",preco:185000,desc_obs:""},{desc:"Dobradiças Blum cx 20un",qty:3,un:"cx",preco:4500,desc_obs:""}],
       subtotal:198500,iva:0,ivaPct:0,desconto:0,total:198500,status:"aprovado",notas:"Inclui instalação e acabamentos.",moeda:"MZN"},
      {id:2,num:"COT-2026-002",cliId:2,cliNome:"Fátima Cossa",data:"2026-04-20",val:"2026-05-05",
       itens:[{desc:"Roupeiro embutido 3 portas",qty:1,un:"un",preco:95000,desc_obs:""}],
       subtotal:95000,iva:0,ivaPct:0,desconto:0,total:95000,status:"enviado",notas:"",moeda:"MZN"},
    ],
    vendas:[
      {id:1,cliId:1,cliNome:"Armando Muianga",cotId:1,num:"VND-2026-001",fatNum:"FAT-2026-001",data:"2026-04-16",
       itens:[{desc:"Cozinha em MDF lacado",qty:1,un:"un",preco:185000,desc_obs:""},{desc:"Dobradiças Blum",qty:3,un:"cx",preco:4500}],
       subtotal:198500,desconto:0,iva:0,ivaPct:0,total:198500,pago:100000,status:"parcial",
       pagamentos:[{tipo:"banco",nome:"BIM",valor:100000,data:"2026-04-16"}],notas:""},
    ],
    produtos:[
      {id:1,nome:"MDF 15mm 2750×1830",cat:"Chapas",preco:2800,custo:1600,estoque:15,min:5,un:"ch"},
      {id:2,nome:"Dobradiça 35mm Blum",cat:"Ferragens",preco:85,custo:40,estoque:200,min:50,un:"un"},
      {id:3,nome:"Palete 1200×800mm",cat:"Paletes",preco:450,custo:220,estoque:80,min:20,un:"un"},
      {id:4,nome:"Cimento CEM II 42.5",cat:"Construção",preco:650,custo:400,estoque:120,min:30,un:"saco"},
      {id:5,nome:"Puxador Inox 160mm",cat:"Ferragens",preco:180,custo:80,estoque:5,min:25,un:"un"},
      {id:6,nome:"Serviço Instalação Marcenaria",cat:"Serviços",preco:15000,custo:0,estoque:999,min:0,un:"un"},
    ],
    financeiro:{
      receitas:[{id:1,desc:"Entrada Cozinha - Armando",valor:100000,data:"2026-04-16",cat:"Serviços",status:"recebido",ref:"VND-2026-001"}],
      despesas:[
        {id:1,desc:"Folha Salarial Abril",valor:127000,data:"2026-04-30",cat:"RH",status:"pago",ref:""},
        {id:2,desc:"Compra MDF - JL Madeiras",valor:38400,data:"2026-04-18",cat:"Estoque",status:"pago",ref:""},
        {id:3,desc:"Renda Galpão",valor:45000,data:"2026-04-05",cat:"Infraestrutura",status:"pago",ref:""},
      ],
    },
    obras:[
      {id:1,nome:"Moradia T3 - Sommerschield",cliId:1,cliNome:"Armando Muianga",valor:850000,inicio:"2026-03-01",fim:"2026-08-30",prog:42,status:"andamento",resp:"Eng. Salomão",notas:""},
    ],
    rh:{
      funcionarios:[
        {id:1,nome:"Carlos Sitoe",bi:"123456789A",nasc:"1988-03-15",tel:"+258 84 111 2222",email:"carlos@onemillion.co.mz",cargo:"Encarregado de Obra",dep:"Obras",tipo_contrato:"efectivo",salario_base:35000,inss_pct:3,irps_pct:10,bonus:0,comissoes:0,data_admissao:"2023-06-01",status:"ativo",banco:"BIM",conta_banco:"1234567890",mpesa:"",notas:""},
        {id:2,nome:"Esperança Bila",bi:"987654321B",nasc:"1992-07-22",tel:"+258 82 333 4444",email:"esperanca@onemillion.co.mz",cargo:"Designer de Interiores",dep:"Design",tipo_contrato:"efectivo",salario_base:42000,inss_pct:3,irps_pct:12,bonus:5000,comissoes:0,data_admissao:"2024-01-15",status:"ativo",banco:"BCI",conta_banco:"9876543210",mpesa:"",notas:""},
        {id:3,nome:"Tomás Nhantumbo",bi:"456789123C",nasc:"1985-11-08",tel:"+258 86 555 6666",email:"tomas@onemillion.co.mz",cargo:"Marceneiro Sénior",dep:"Produção",tipo_contrato:"efectivo",salario_base:28000,inss_pct:3,irps_pct:8,bonus:0,comissoes:0,data_admissao:"2022-09-01",status:"ativo",banco:"BIM",conta_banco:"1122334455",mpesa:"+258 86 555 6666",notas:""},
      ],
      presencas:[
        {id:1,funcId:1,data:"2026-04-28",entrada:"08:00",saida:"17:00",tipo:"normal",obs:""},
        {id:2,funcId:2,data:"2026-04-28",entrada:"08:30",saida:"17:30",tipo:"normal",obs:""},
        {id:3,funcId:3,data:"2026-04-28",entrada:"",saida:"",tipo:"falta",obs:"Justificada"},
      ],
      ferias:[
        {id:1,funcId:1,funcNome:"Carlos Sitoe",inicio:"2026-07-01",fim:"2026-07-20",dias:20,status:"aprovado",obs:""},
      ],
      avaliacoes:[
        {id:1,funcId:1,funcNome:"Carlos Sitoe",data:"2026-03-31",periodo:"Q1 2026",nota:4,comentario:"Bom desempenho, pontual e eficiente.",avaliador:"Admin",status:"concluida"},
      ],
      folhas:[],
      vagas:[],
    },
    logs:[{id:1,user:"sistema",acao:"Base de dados iniciada",data:nowStr()}],
  };
}

// ════════════════════════════════════════════════════════════
// UTILITÁRIOS
// ════════════════════════════════════════════════════════════
function nowStr(){return new Date().toLocaleString("pt-MZ");}
function hoje(){return new Date().toISOString().split("T")[0];}
function mzn(v,m){m=m||DB.cfg.moeda;return Number(v||0).toLocaleString("pt-MZ",{minimumFractionDigits:2,maximumFractionDigits:2})+" "+(m||"MZN");}
function pad(n,p,y){p=p||"COT";y=y||(new Date().getFullYear());return `${p}-${y}-${String(n).padStart(3,"0")}`;}
function esc(s){return String(s||"").replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/"/g,"&quot;");}
function addLog(acao){if(CU)DB.logs.push({id:Date.now(),user:CU.user,acao,data:nowStr()});saveDB(DB);}
function SI(s){return{pendente:{l:"Pendente",c:"#8a9bb0"},enviado:{l:"Enviado",c:"#4a9eff"},aprovado:{l:"Aprovado",c:"#1eb87a"},rejeitado:{l:"Rejeitado",c:"#c0272d"},pago:{l:"Pago",c:"#1eb87a"},parcial:{l:"Parcial",c:"#d4a820"},ativo:{l:"Ativo",c:"#1eb87a"},inativo:{l:"Inativo",c:"#c0272d"},andamento:{l:"Em Andamento",c:"#d4a820"},concluido:{l:"Concluído",c:"#1eb87a"},normal:{l:"Presente",c:"#1eb87a"},falta:{l:"Falta",c:"#c0272d"},atraso:{l:"Atraso",c:"#d4a820"},ferias:{l:"Férias",c:"#4a9eff"},aprovado:{l:"Aprovado",c:"#1eb87a"},recebido:{l:"Recebido",c:"#1eb87a"}}[s]||{l:s,c:"#8a9bb0"};}
function bdg(s){const si=SI(s);return`<span class="bdg" style="background:${si.c}22;color:${si.c};">${esc(si.l)}</span>`;}
function bdgC(l,c){return`<span class="bdg" style="background:${c}22;color:${c};">${esc(l)}</span>`;}
function pb(v,c){return`<div class="pt"><div class="pf" style="width:${Math.min(v||0,100)}%;background:${c||"var(--red)"};"></div></div>`;}

function ico(paths,s){
  s=s||16;
  const segs=paths.split("|").map(d=>`<path d="${d}"/>`).join("");
  return`<svg width="${s}" height="${s}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">${segs}</svg>`;
}
const ICOS={
  dash:"M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z|M9 22V12h6v10",
  cli:"M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2|M9 7a4 4 0 1 0 0-8 4 4 0 0 0 0 8|M23 21v-2a4 4 0 0 0-3-3.87|M16 3.13a4 4 0 0 1 0 7.75",
  cot:"M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z|M14 2v6h6|M16 13H8|M16 17H8|M10 9H8",
  cart:"M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z|M3 6h18|M16 10a4 4 0 0 1-8 0",
  box:"M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z",
  build:"M2 20h20|M4 20V10l8-8 8 8v10|M12 20v-8",
  money:"M12 2v20|M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6",
  rh:"M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2|M9 7a4 4 0 1 0 0-8 4 4 0 0 0 0 8|M22 21v-2a4 4 0 0 0-3-3.87|M16 3.13a4 4 0 0 1 0 7.75",
  chart:"M18 20V10|M12 20V4|M6 20v-6",
  cfg:"M12 15a3 3 0 1 0 0-6 3 3 0 0 0 0 6z|M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 2.83-2.83l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z",
  plus:"M12 5v14|M5 12h14",x:"M18 6 6 18|M6 6l12 12",check:"M20 6 9 17l-5-5",
  edit:"M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7|M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z",
  trash:"M3 6h18|M8 6V4h8v2|M19 6l-1 14a2 2 0 0 1-2 2H8a2 2 0 0 1-2-2L5 6",
  search:"M11 19a8 8 0 1 0 0-16 8 8 0 0 0 0 16z|M21 21l-4.35-4.35",
  wa:"M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z",
  print:"M6 9V2h12v7|M6 18H4a2 2 0 0 1-2-2v-5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v5a2 2 0 0 1-2 2h-2|M6 14h12v8H6z",
  arrow:"M5 12h14|M12 5l7 7-7 7",
  logout:"M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4|M16 17l5-5-5-5|M21 12H9",
  prod:"M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z",
  cal:"M16 2v4|M8 2v4|M3 10h18|M21 8v13a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2v2",
  star:"M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z",
  alert:"M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z|M12 9v4|M12 17h.01",
};

// ════════════════════════════════════════════════════════════
// ESTADO GLOBAL
// ════════════════════════════════════════════════════════════
let DB=loadDB();
let CU=null; // currentUser
let CP="dash"; // currentPage
let navCol=false;

// ════════════════════════════════════════════════════════════
// AUTH
// ════════════════════════════════════════════════════════════
function togglePass(){const i=document.getElementById("l-pass");i.type=i.type==="password"?"text":"password";}
function doLogin(){
  const u=document.getElementById("l-user").value.trim();
  const p=document.getElementById("l-pass").value;
  const found=USERS_LIST.find(x=>x.user===u&&x.pass===p);
  if(!found){document.getElementById("l-err").style.display="block";return;}
  document.getElementById("l-err").style.display="none";
  CU=found; DB=loadDB();
  addLog("Login no sistema");
  document.getElementById("login-wrap").style.display="none";
  document.getElementById("app-shell").style.display="flex";
  document.getElementById("tb-av").textContent=found.av;
  document.getElementById("tb-name").textContent=found.nome.split(" ")[0];
  document.getElementById("tb-role").textContent=found.nivel.toUpperCase();
  buildNav(); updateLogo(); goTo("dash");
}
function doLogout(){addLog("Logout");CU=null;document.getElementById("app-shell").style.display="none";document.getElementById("login-wrap").style.display="flex";}

// ════════════════════════════════════════════════════════════
// NAV
// ════════════════════════════════════════════════════════════
const NAV=[
  {id:"dash",lbl:"Dashboard",grp:"Geral",i:"dash"},
  {id:"clientes",lbl:"Clientes / CRM",grp:"Comercial",i:"cli"},
  {id:"cotacoes",lbl:"Cotações",grp:"Comercial",i:"cot"},
  {id:"vendas",lbl:"Vendas",grp:"Comercial",i:"cart"},
  {id:"vendas-nova",lbl:"Nova Venda",grp:"Comercial",i:"plus"},
  {id:"estoque",lbl:"Estoque",grp:"Operacional",i:"box"},
  {id:"obras",lbl:"Obras",grp:"Operacional",i:"build"},
  {id:"financeiro",lbl:"Financeiro",grp:"Gestão",i:"money"},
  {id:"rh-mod",lbl:"RH",grp:"Gestão",i:"rh"},
  {id:"relatorios",lbl:"Relatórios",grp:"Gestão",i:"chart"},
  {id:"config",lbl:"Configurações",grp:"Sistema",i:"cfg"},
];
function buildNav(){
  const ps=PERMS[CU.nivel]||[];
  const its=NAV.filter(n=>ps.includes(n.id));
  const grps=[...new Set(its.map(n=>n.grp))];
  let h="";
  grps.forEach(g=>{
    h+=`<div class="grp-lbl">${g}</div>`;
    its.filter(n=>n.grp===g).forEach(n=>{
      h+=`<button class="nb${n.id===CP?" active":""}" id="nb-${n.id}" onclick="goTo('${n.id}')" title="${n.lbl}">
        ${ico(ICOS[n.i],15)}<span class="nb-lbl">${n.lbl}</span></button>`;
    });
  });
  document.getElementById("sb-nav").innerHTML=h;
}
function goTo(p){
  CP=p;
  document.querySelectorAll(".nb").forEach(b=>b.classList.remove("active"));
  const nb=document.getElementById("nb-"+p);if(nb)nb.classList.add("active");
  const navItem=NAV.find(n=>n.id===p);
  document.getElementById("tb-title").textContent=navItem?.lbl||p;
  render(p);
}
function toggleNav(){navCol=!navCol;document.getElementById("sidebar").classList.toggle("collapsed",navCol);}
function updateLogo(){
  const sb=document.getElementById("sb-logo");
  const lg=DB.cfg.logo;
  if(lg)sb.innerHTML=`<img src="${lg}" style="max-height:36px;max-width:140px;object-fit:contain;" alt="Logo"/>`;
  else sb.innerHTML=`<div class="globe">🌐</div><div class="logo-txt"><b>${esc(DB.cfg.empresa)}</b><small>SERVICE</small></div>`;
  const ll=document.getElementById("ll-area");
  if(ll&&lg)ll.innerHTML=`<img src="${lg}" style="max-height:70px;margin-bottom:10px;" alt="Logo"/><div style="color:var(--muted);font-size:12px;">Moçambique · Sistema de Gestão Empresarial</div>`;
}

// ════════════════════════════════════════════════════════════
// MODAL
// ════════════════════════════════════════════════════════════
function openModal(t,b,sz){
  document.getElementById("m-title").textContent=t;
  document.getElementById("m-body").innerHTML=b;
  const mb=document.getElementById("modal-box");
  mb.className="mb"+(sz==="wide"?" wide":sz==="xl"?" xl":"");
  document.getElementById("modal-ov").style.display="flex";
}
function closeModal(){document.getElementById("modal-ov").style.display="none";}

// ════════════════════════════════════════════════════════════
// RENDER ROUTER
// ════════════════════════════════════════════════════════════
function render(p){
  DB=loadDB();
  const fns={dash:rDash,clientes:rClientes,cotacoes:rCotacoes,vendas:rVendas,"vendas-nova":rNovaVenda,
    estoque:rEstoque,obras:rObras,financeiro:rFinanceiro,"rh-mod":rRH,relatorios:rRelatorios,config:rConfig};
  const fn=fns[p];
  document.getElementById("page-content").innerHTML=fn?fn():`<div class="alert-w">Módulo em desenvolvimento.</div>`;
}

// ════════════════════════════════════════════════════════════
// DASHBOARD
// ════════════════════════════════════════════════════════════
function rDash(){
  const tV=DB.vendas.reduce((s,v)=>s+v.total,0);
  const tC=DB.cotacoes.length,cA=DB.cotacoes.filter(c=>c.status==="aprovado").length;
  const taxa=tC>0?Math.round((cA/tC)*100):0;
  const tR=DB.financeiro.receitas.reduce((s,r)=>s+r.valor,0);
  const tD=DB.financeiro.despesas.reduce((s,d)=>s+d.valor,0);
  const crit=DB.produtos.filter(p=>p.estoque<=p.min);
  const stC={pendente:"#8a9bb0",enviado:"#4a9eff",aprovado:"#1eb87a",rejeitado:"#c0272d"};
  let funnel=["pendente","enviado","aprovado","rejeitado"].map(st=>{
    const cnt=DB.cotacoes.filter(c=>c.status===st).length;
    const tot=DB.cotacoes.filter(c=>c.status===st).reduce((s,c)=>s+c.total,0);
    const pct=tC>0?Math.round((cnt/tC)*100):0;
    const si=SI(st);
    return`<div style="margin-bottom:12px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:5px;">
        <span style="color:${si.c};font-size:13px;font-weight:600;">${si.l}</span>
        <div style="display:flex;gap:12px;"><span style="color:var(--muted);font-size:12px;">${cnt}</span><span style="color:var(--gold);font-size:13px;font-weight:700;">${mzn(tot)}</span><span style="color:${si.c};font-size:12px;font-weight:700;">${pct}%</span></div>
      </div>${pb(pct,si.c)}</div>`;
  }).join("");
  let lastCots=[...DB.cotacoes].reverse().slice(0,5).map(c=>`<tr>
    <td style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(c.num)}</td>
    <td style="font-weight:600;">${esc(c.cliNome)}</td>
    <td style="color:var(--gold);font-weight:700;">${mzn(c.total)}</td>
    <td>${bdg(c.status)}</td>
    <td><button class="btn btn-n btn-xs" onclick="goTo('cotacoes')">Ver</button></td></tr>`).join("");
  let critHtml="";
  if(crit.length)critHtml=`<div class="alert-r" style="margin-top:14px;"><div style="color:var(--red);font-weight:700;margin-bottom:6px;">${ico(ICOS.alert,14)} ${crit.length} produto(s) com estoque crítico</div>${crit.map(p=>`<div style="color:#e09090;font-size:13px;">${esc(p.nome)} — ${p.estoque} ${p.un} (mín: ${p.min})</div>`).join("")}</div>`;
  return`<div style="background:linear-gradient(135deg,var(--navy),#0a1828);border:1px solid var(--border);border-radius:14px;padding:20px 24px;margin-bottom:18px;position:relative;overflow:hidden;">
    <div style="position:absolute;top:-50px;right:-50px;width:220px;height:220px;background:radial-gradient(circle,rgba(192,39,45,.12),transparent 70%);border-radius:50%;pointer-events:none;"></div>
    <div style="color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:2px;margin-bottom:4px;">${new Date().toLocaleDateString("pt-MZ",{weekday:"long",day:"numeric",month:"long",year:"numeric"})}</div>
    <h1 style="color:#fff;font-size:20px;margin-bottom:2px;">Bem-vindo, ${esc(CU.nome.split(" ")[0])}!</h1>
    <div style="color:var(--silverL);font-size:13px;">Acesso: <b style="color:var(--gold);">${CU.nivel.toUpperCase()}</b> · ONE MILLION SERVICE</div>
  </div>
  <div class="kpi-grid">
    <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Faturamento Total</div><div class="kpi-v" style="color:var(--red);">${mzn(tV)}</div><div class="kpi-s">${DB.vendas.length} vendas realizadas</div></div>
    <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Cotações Emitidas</div><div class="kpi-v" style="color:var(--blue);">${tC}</div><div class="kpi-s">${cA} aprovadas · ${DB.cotacoes.filter(c=>c.status==="pendente").length} pendentes</div></div>
    <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Taxa de Conversão</div><div class="kpi-v" style="color:var(--green);">${taxa}%</div><div class="kpi-s">Cotações convertidas em vendas</div></div>
    <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Saldo do Período</div><div class="kpi-v" style="color:${tR-tD>=0?"var(--gold)":"var(--red)"};">${mzn(tR-tD)}</div><div class="kpi-s">Receitas ${mzn(tR)} · Despesas ${mzn(tD)}</div></div>
  </div>
  <div style="display:grid;grid-template-columns:3fr 2fr;gap:14px;">
    <div class="card"><h3 class="serif" style="font-size:14px;margin-bottom:14px;">Últimas Cotações</h3>
      <table class="tbl"><thead><tr><th>Nº</th><th>Cliente</th><th>Total</th><th>Status</th><th></th></tr></thead><tbody>${lastCots}</tbody></table></div>
    <div class="card"><h3 class="serif" style="font-size:14px;margin-bottom:12px;">Funil de Cotações</h3>${funnel}</div>
  </div>${critHtml}`;
}

// ════════════════════════════════════════════════════════════
// CLIENTES
// ════════════════════════════════════════════════════════════
function rClientes(){
  let cards=DB.clientes.map(c=>{
    const nc=DB.cotacoes.filter(x=>x.cliId===c.id).length;
    return`<div class="card card-hover" onclick="verCli(${c.id})" style="cursor:pointer;">
      <div style="display:flex;gap:10px;align-items:center;margin-bottom:10px;">
        <div style="width:40px;height:40px;background:linear-gradient(135deg,var(--navy2),var(--navy3));border-radius:50%;display:flex;align-items:center;justify-content:center;border:2px solid var(--border);color:var(--red);font-weight:800;font-size:16px;flex-shrink:0;">${c.nome[0]}</div>
        <div style="flex:1;min-width:0;"><div style="color:var(--text);font-weight:700;font-size:14px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;">${esc(c.nome)}</div>
          <div style="color:var(--muted);font-size:11px;">${c.tipo==="empresa"?"🏢 Empresa":"👤 Particular"}</div></div>
        ${bdg(c.status)}
      </div>
      <div style="font-size:12px;color:var(--muted);display:flex;flex-direction:column;gap:3px;margin-bottom:10px;">
        <div>📞 ${esc(c.tel)}</div>${c.email?`<div>✉️ ${esc(c.email)}</div>`:""}${c.end?`<div>📍 ${esc(c.end)}</div>`:""}
      </div>
      <div style="display:flex;justify-content:space-between;align-items:center;" onclick="event.stopPropagation()">
        <span style="color:var(--muted);font-size:11px;">${nc} cotação(ões)</span>
        <div style="display:flex;gap:4px;">
          <a href="https://wa.me/${(c.tel||"").replace(/\D/g,"")}" target="_blank" class="btn btn-g btn-xs">💬</a>
          <button class="btn btn-n btn-xs" onclick="editCli(${c.id})">✏️</button>
          <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delCli(${c.id})">🗑️</button>
        </div>
      </div></div>`;
  }).join("");
  return`<div class="ph"><div><div class="ph-title">CRM — Clientes</div><div class="ph-sub">${DB.clientes.length} clientes cadastrados</div></div>
    <div class="ph-actions"><button class="btn btn-p" onclick="novoCli()">${ico(ICOS.plus,14)} Novo Cliente</button></div></div>
  <div class="sw"><span class="si">${ico(ICOS.search,14)}</span><input class="inp" id="bq-cli" placeholder="Pesquisar cliente..." oninput="filtCli()"/></div>
  <div id="cli-grid" style="display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:11px;">${cards}</div>`;
}
function filtCli(){
  const q=document.getElementById("bq-cli").value.toLowerCase();
  document.querySelectorAll("#cli-grid .card").forEach((el,i)=>{
    const c=DB.clientes[i];if(!c)return;
    el.style.display=(!q||c.nome.toLowerCase().includes(q)||c.email?.toLowerCase().includes(q)||c.tel?.includes(q))?"":"none";
  });
}
function verCli(id){
  const c=DB.clientes.find(x=>x.id===id);if(!c)return;
  const cots=DB.cotacoes.filter(x=>x.cliId===id);
  const vs=DB.vendas.filter(x=>x.cliId===id);
  const tg=vs.reduce((s,v)=>s+v.total,0);
  let cotRows=cots.map(co=>`<tr><td style="font-family:monospace;font-size:11px;">${esc(co.num)}</td><td>${esc(co.data)}</td><td style="color:var(--gold);font-weight:700;">${mzn(co.total)}</td><td>${bdg(co.status)}</td></tr>`).join("");
  openModal(`Histórico — ${c.nome}`,`
    <div class="g2" style="margin-bottom:14px;">
      ${[["📞 Tel",c.tel],["✉️ Email",c.email||"—"],["📍 End.",c.end||"—"],["NUIT",c.nuit||"—"]].map(([l,v])=>`<div style="background:var(--navy);border-radius:8px;padding:11px;"><div style="color:var(--muted);font-size:11px;margin-bottom:3px;">${l}</div><div style="font-size:13px;">${esc(v)}</div></div>`).join("")}
    </div>
    <div class="g3" style="margin-bottom:14px;">
      ${[["Cotações",cots.length,"var(--blue)"],["Vendas",vs.length,"var(--green)"],["Total Gasto",mzn(tg),"var(--gold)"]].map(([l,v,col])=>`<div style="background:var(--navy);border-radius:8px;padding:11px;text-align:center;"><div style="color:${col};font-size:18px;font-weight:800;">${v}</div><div style="color:var(--muted);font-size:11px;">${l}</div></div>`).join("")}
    </div>
    <h4 style="font-size:13px;margin-bottom:8px;">Histórico de Cotações</h4>
    ${cotRows?`<table class="tbl"><thead><tr><th>Nº</th><th>Data</th><th>Total</th><th>Status</th></tr></thead><tbody>${cotRows}</tbody></table>`:"<p style='color:var(--muted);font-size:13px;'>Sem cotações.</p>"}
    <div class="mfoot"><a href="https://wa.me/${(c.tel||"").replace(/\D/g,"")}" target="_blank" class="btn btn-g">💬 WhatsApp</a><button class="btn btn-n" onclick="closeModal()">Fechar</button></div>`,"wide");
}
function novoCli(){_fCli(null);}
function editCli(id){_fCli(DB.clientes.find(c=>c.id===id));}
function _fCli(c){
  openModal(c?"Editar Cliente":"Novo Cliente",`
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome / Empresa</label><input class="inp" id="cf-n" value="${esc(c?.nome||"")}"/></div>
      <div class="fg"><label class="lbl">Telefone/WhatsApp</label><input class="inp" id="cf-t" value="${esc(c?.tel||"")}" placeholder="+258 84 000 0000"/></div>
      <div class="fg"><label class="lbl">Email</label><input class="inp" id="cf-e" value="${esc(c?.email||"")}"/></div>
      <div class="fg"><label class="lbl">Tipo</label><select class="inp" id="cf-tp"><option value="particular" ${c?.tipo==="particular"?"selected":""}>Particular</option><option value="empresa" ${c?.tipo==="empresa"?"selected":""}>Empresa</option></select></div>
      <div class="fg"><label class="lbl">NUIT</label><input class="inp" id="cf-nu" value="${esc(c?.nuit||"")}"/></div>
      <div class="fg cs2"><label class="lbl">Endereço</label><input class="inp" id="cf-en" value="${esc(c?.end||"")}"/></div>
      <div class="fg cs2"><label class="lbl">Observações</label><textarea class="inp" id="cf-ob" style="height:55px;resize:vertical;">${esc(c?.obs||"")}</textarea></div>
    </div>
    <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveCli(${c?.id||0})">${ico(ICOS.check,14)} Guardar</button></div>`);
}
function saveCli(id){
  const n=document.getElementById("cf-n").value.trim();if(!n)return alert("Nome obrigatório!");
  const o={id:id||Date.now(),nome:n,tel:v("cf-t"),email:v("cf-e"),tipo:v("cf-tp"),nuit:v("cf-nu"),end:v("cf-en"),obs:v("cf-ob"),status:"ativo"};
  if(id)DB.clientes=DB.clientes.map(c=>c.id===id?o:c);else DB.clientes.push(o);
  addLog((id?"Editou":"Criou")+" cliente: "+n);saveDB(DB);closeModal();render("clientes");
}
function delCli(id){if(!confirm("Eliminar cliente?"))return;DB.clientes=DB.clientes.filter(c=>c.id!==id);saveDB(DB);render("clientes");}
function v(id){const el=document.getElementById(id);return el?el.value:"";}


// ════════════════════════════════════════════════════════════
// COTAÇÕES — completo com IVA, desconto, pagamentos, PDF
// ════════════════════════════════════════════════════════════
let _ci=[{desc:"",qty:1,un:"un",preco:0,desc_obs:""}];
let _cFiltro="todos";

function rCotacoes(){
  const stC={pendente:"#8a9bb0",enviado:"#4a9eff",aprovado:"#1eb87a",rejeitado:"#c0272d"};
  let ftabs=["todos","pendente","enviado","aprovado","rejeitado"].map(f=>`<button class="tab${_cFiltro===f?" active":""}" onclick="_setCF('${f}')">${f==="todos"?"Todas":SI(f).l}</button>`).join("");
  let its=DB.cotacoes.filter(c=>_cFiltro==="todos"||c.status===_cFiltro);
  let cards=[...its].reverse().map(c=>{
    const si=SI(c.status);
    const iC=c.itens.slice(0,2).map(i=>esc(i.desc)).join(" · ")+(c.itens.length>2?` +${c.itens.length-2} mais`:"");
    const apr=["pendente","enviado"].includes(c.status)?`<div style="display:flex;gap:4px;margin-top:5px;justify-content:flex-end;">
      <button class="btn btn-xs" style="background:rgba(30,184,122,.15);color:var(--green);border:none;" onclick="stCot(${c.id},'aprovado')">✓ Aprovar</button>
      <button class="btn btn-xs" style="background:rgba(192,39,45,.15);color:var(--red);border:none;" onclick="stCot(${c.id},'rejeitado')">✗ Rejeitar</button></div>`:"";
    const cvt=c.status!=="aprovado"&&c.status!=="rejeitado"?`<button class="btn btn-b btn-xs" onclick="cvtCot(${c.id})">${ico(ICOS.arrow,12)} Converter</button>`:"";
    return`<div class="card" style="margin-bottom:9px;">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;">
        <div style="flex:1;">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;flex-wrap:wrap;">
            <span style="color:var(--muted);font-family:monospace;font-size:11px;">${esc(c.num)}</span>
            <span style="font-weight:700;font-size:15px;">${esc(c.cliNome)}</span>${bdg(c.status)}</div>
          <div style="color:var(--muted);font-size:12px;margin-bottom:4px;">📅 ${c.data} · Válida: ${c.val} · ${c.itens.length} item(ns)</div>
          <div style="color:var(--silverL);font-size:12px;">${iC}</div>
        </div>
        <div style="text-align:right;">
          <div style="color:var(--gold);font-size:20px;font-weight:800;margin-bottom:7px;">${mzn(c.total)}</div>
          <div style="display:flex;gap:4px;flex-wrap:wrap;justify-content:flex-end;">
            <button class="btn btn-n btn-xs" onclick="pdfDoc(${c.id},'cot')">📄 PDF</button>
            <button class="btn btn-g btn-xs" onclick="sendWA(${c.id},'cot')">💬 WA</button>
            ${cvt}
            <button class="btn btn-n btn-xs" onclick="editCot(${c.id})">✏️</button>
            <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delCot(${c.id})">🗑️</button>
          </div>${apr}
        </div>
      </div></div>`;
  }).join("");
  const tPip=DB.cotacoes.reduce((s,c)=>s+c.total,0);
  return`<div class="ph"><div><div class="ph-title">Cotações / Orçamentos</div><div class="ph-sub">${DB.cotacoes.length} cotações · ${mzn(tPip)} em pipeline</div></div>
    <button class="btn btn-p" onclick="novaCot()">${ico(ICOS.plus,14)} Nova Cotação</button></div>
  <div class="tabs">${ftabs}</div>
  ${cards||'<div class="alert-w">Nenhuma cotação encontrada.</div>'}`;
}
function _setCF(f){_cFiltro=f;render("cotacoes");}
function stCot(id,st){DB.cotacoes=DB.cotacoes.map(c=>c.id===id?{...c,status:st}:c);addLog(`Cotação ${DB.cotacoes.find(c=>c.id===id)?.num} → ${st}`);saveDB(DB);render("cotacoes");}
function delCot(id){if(!confirm("Eliminar cotação?"))return;DB.cotacoes=DB.cotacoes.filter(c=>c.id!==id);saveDB(DB);render("cotacoes");}
function cvtCot(id){
  const c=DB.cotacoes.find(x=>x.id===id);if(!c)return;
  if(!confirm(`Converter ${c.num} em venda?`))return;
  const num=pad(DB.vendSeq,"VND");const fn=pad(DB.fatSeq,"FAT");
  const v={id:Date.now(),cliId:c.cliId,cliNome:c.cliNome,cotId:c.id,num,fatNum:fn,data:hoje(),
    itens:c.itens,subtotal:c.subtotal,desconto:c.desconto,iva:c.iva,ivaPct:c.ivaPct,total:c.total,
    pago:0,status:"pendente",pagamentos:[],notas:c.notas,moeda:c.moeda||DB.cfg.moeda};
  DB.vendas.push(v);DB.cotacoes=DB.cotacoes.map(x=>x.id===id?{...x,status:"aprovado"}:x);
  DB.vendSeq++;DB.fatSeq++;addLog(`Converteu ${c.num} → ${num}`);saveDB(DB);render("cotacoes");
}

function novaCot(){_ci=[{desc:"",qty:1,un:"un",preco:0,desc_obs:""}];_abrirFCot(null);}
function editCot(id){const c=DB.cotacoes.find(x=>x.id===id);_ci=JSON.parse(JSON.stringify(c.itens));_abrirFCot(c);}

function _abrirFCot(c){
  const cliOpts=DB.clientes.map(x=>`<option value="${x.id}" ${x.id===(c?.cliId)?"selected":""}>${esc(x.nome)}</option>`).join("");
  openModal(c?"Editar Cotação":"Nova Cotação",`
    <div class="g2" style="margin-bottom:13px;">
      <div class="fg cs2"><label class="lbl">Cliente</label><select class="inp" id="cf2-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="cf2-d" value="${c?.data||hoje()}"/></div>
      <div class="fg"><label class="lbl">Válida Até</label><input class="inp" type="date" id="cf2-v" value="${c?.val||""}"/></div>
      <div class="fg"><label class="lbl">IVA %</label><input class="inp" type="number" id="cf2-iva" value="${c?.ivaPct??DB.cfg.iva}" min="0" max="100" oninput="_calcCot()"/></div>
      <div class="fg"><label class="lbl">Desconto (${DB.cfg.moeda})</label><input class="inp" type="number" id="cf2-desc" value="${c?.desconto||0}" min="0" oninput="_calcCot()"/></div>
    </div>
    <div style="margin-bottom:13px;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
        <label class="lbl" style="margin:0;">Itens / Serviços</label>
        <button class="btn btn-n btn-xs" onclick="_addCI()">+ Adicionar Item</button>
      </div>
      <div style="background:var(--navy);border-radius:10px;padding:11px;">
        <div class="ir-grid hdr"><div>Descrição</div><div>Un.</div><div>Qty</div><div>Preço Unit.</div><div>Total</div><div></div></div>
        <div id="ci-cont"></div>
        <div style="display:flex;justify-content:flex-end;padding-top:9px;border-top:1px solid var(--border);margin-top:6px;">
          <div style="text-align:right;font-size:13px;">
            <div style="color:var(--muted);">Subtotal: <span id="ci-sub">0</span></div>
            <div style="color:var(--muted);">IVA: <span id="ci-iva">0</span></div>
            <div style="color:var(--muted);">Desconto: -<span id="ci-dsc">0</span></div>
            <div style="color:var(--gold);font-weight:800;font-size:17px;">TOTAL: <span id="ci-tot">0</span></div>
          </div>
        </div>
      </div>
    </div>
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Observações / Notas</label><textarea class="inp" id="cf2-obs" style="height:60px;resize:vertical;">${esc(c?.notas||"")}</textarea></div>
    </div>
    <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveCot(${c?.id||0})">${ico(ICOS.check,14)} ${c?"Guardar":"Criar Cotação"}</button></div>`,"wide");
  _renderCI();
}
function _addCI(){_ci.push({desc:"",qty:1,un:"un",preco:0,desc_obs:""});_renderCI();}
function _remCI(i){if(_ci.length===1)return;_ci.splice(i,1);_renderCI();}
function _updCI(i,k,val){_ci[i][k]=["qty","preco"].includes(k)?Number(val):val;_calcCot();}
function _renderCI(){
  const cont=document.getElementById("ci-cont");if(!cont)return;
  cont.innerHTML=_ci.map((it,i)=>`<div class="ir-grid" style="margin-bottom:5px;">
    <input class="inp" style="padding:7px 8px;font-size:12px;" placeholder="Descrição" value="${esc(it.desc)}" oninput="_updCI(${i},'desc',this.value)"/>
    <input class="inp" style="padding:7px 8px;font-size:12px;" placeholder="un" value="${esc(it.un)}" oninput="_updCI(${i},'un',this.value)"/>
    <input class="inp" type="number" style="padding:7px 8px;font-size:12px;" value="${it.qty}" oninput="_updCI(${i},'qty',this.value)" min="1"/>
    <input class="inp" type="number" style="padding:7px 8px;font-size:12px;" value="${it.preco}" oninput="_updCI(${i},'preco',this.value)" min="0"/>
    <div style="color:var(--gold);font-size:12px;font-weight:700;display:flex;align-items:center;">${mzn(it.qty*it.preco)}</div>
    <button onclick="_remCI(${i})" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:16px;">×</button></div>`).join("");
  _calcCot();
}
function _calcCot(){
  const sub=_ci.reduce((s,it)=>s+it.qty*it.preco,0);
  const ivaPct=Number(document.getElementById("cf2-iva")?.value||0);
  const dsc=Number(document.getElementById("cf2-desc")?.value||0);
  const iva=sub*(ivaPct/100);
  const tot=Math.max(0,sub+iva-dsc);
  const f=el=>{const e=document.getElementById(el);if(e)e.textContent=mzn(["ci-sub","ci-iva","ci-dsc","ci-tot"].includes(el)?[sub,iva,dsc,tot][["ci-sub","ci-iva","ci-dsc","ci-tot"].indexOf(el)]:0);};
  ["ci-sub","ci-iva","ci-dsc","ci-tot"].forEach((id,i)=>{const e=document.getElementById(id);if(e)e.textContent=mzn([sub,iva,dsc,tot][i]);});
}
function saveCot(id){
  const cliId=Number(document.getElementById("cf2-cli").value);
  if(!cliId||!_ci[0].desc)return alert("Cliente e pelo menos 1 item são obrigatórios!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  const sub=_ci.reduce((s,it)=>s+it.qty*it.preco,0);
  const ivaPct=Number(document.getElementById("cf2-iva").value||0);
  const dsc=Number(document.getElementById("cf2-desc").value||0);
  const iva=sub*(ivaPct/100);
  const tot=Math.max(0,sub+iva-dsc);
  const num=id?(DB.cotacoes.find(c=>c.id===id)?.num||pad(DB.cotSeq)):pad(DB.cotSeq);
  const obj={id:id||Date.now(),num,cliId,cliNome:cli.nome,data:v("cf2-d"),val:v("cf2-v"),
    itens:_ci.map(it=>({...it,qty:Number(it.qty),preco:Number(it.preco)})),
    subtotal:sub,ivaPct,iva,desconto:dsc,total:tot,
    status:id?(DB.cotacoes.find(c=>c.id===id)?.status||"pendente"):"pendente",
    notas:v("cf2-obs"),moeda:DB.cfg.moeda};
  if(id)DB.cotacoes=DB.cotacoes.map(c=>c.id===id?obj:c);
  else{DB.cotacoes.push(obj);DB.cotSeq++;}
  addLog((id?"Editou":"Criou")+" cotação "+num);saveDB(DB);closeModal();render("cotacoes");
}

// PDF / FATURA UNIVERSAL
function pdfDoc(id,tipo){
  const doc=tipo==="cot"?DB.cotacoes.find(x=>x.id===id):DB.vendas.find(x=>x.id===id);
  if(!doc)return;
  const cfg=DB.cfg;
  const cli=DB.clientes.find(x=>x.id===doc.cliId)||{};
  const isVenda=tipo==="vnd";
  const docNum=isVenda?(doc.fatNum||doc.num):doc.num;
  const docTipo=isVenda?"FATURA":"COTAÇÃO";
  const pgAtivos=cfg.pagamentos.filter(p=>p.ativo);
  const logoH=cfg.logo?`<img src="${cfg.logo}" style="max-height:55px;max-width:170px;object-fit:contain;" alt="Logo"/>`:"";
  const rows=doc.itens.map((it,i)=>`<tr>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;">${i+1}</td>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;">${esc(it.desc)}${it.desc_obs?`<br/><small style="color:#888;">${esc(it.desc_obs)}</small>`:""}</td>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;text-align:center;">${esc(it.un)}</td>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;text-align:right;">${it.qty}</td>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;text-align:right;">${mzn(it.preco,doc.moeda)}</td>
    <td style="padding:7px 10px;border-bottom:1px solid #eee;text-align:right;font-weight:700;">${mzn(it.qty*it.preco,doc.moeda)}</td></tr>`).join("");
  const pgRows=pgAtivos.length?`<div class="pdf-pay"><div style="font-weight:700;margin-bottom:8px;color:#1a2d4f;">Formas de Pagamento Aceites:</div>${pgAtivos.map(p=>`<div style="margin-bottom:5px;">
    <span style="font-weight:600;color:#1a2d4f;">${esc(p.nome)}:</span>
    ${p.tipo==="numerario"?"Dinheiro em mão":`${p.conta||p.numero||""} ${p.titular?`· Tit: ${esc(p.titular)}`:""}`}
  </div>`).join("")}</div>`:"";
  const termosH=cfg.termos?`<div style="margin-top:12px;border-top:1px solid #eee;padding-top:10px;font-size:11px;color:#777;"><b>Termos e Condições:</b><br/>${esc(cfg.termos).replace(/\n/g,"<br/>")}</div>`:"";
  openModal(`${docTipo} — ${docNum}`,`
    <div class="pdf-wrap" id="pdf-content">
      <div class="pdf-hdr">
        <div>${logoH?logoH+`<br/>`:""}
          <div class="pdf-co">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan)}</div>
          <div style="color:#777;font-size:11px;margin-top:3px;">
            ${esc(cfg.end)}<br/>${esc(cfg.cidade)}, ${esc(cfg.pais)}<br/>
            ${esc(cfg.tel)} · ${esc(cfg.email)}<br/>
            ${cfg.nuit?`NUIT: ${esc(cfg.nuit)}`:""}${cfg.website?` · ${esc(cfg.website)}`:""}
          </div>
        </div>
        <div style="text-align:right;">
          <div class="pdf-badge">${docTipo}</div>
          <div style="font-weight:800;font-size:14px;color:#1a2d4f;margin-top:4px;">${esc(docNum)}</div>
          <div style="color:#777;font-size:11px;">Data: ${doc.data}</div>
          ${!isVenda&&doc.val?`<div style="color:#c0272d;font-size:11px;font-weight:600;">Válida até: ${doc.val}</div>`:""}
          ${isVenda?`<div style="color:#1eb87a;font-size:11px;font-weight:600;">Pago: ${mzn(doc.pago||0,doc.moeda)}</div>`:""}
        </div>
      </div>
      <div style="background:#f5f7fa;border-radius:8px;padding:12px 14px;margin-bottom:18px;">
        <div style="color:#888;font-size:10px;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px;">Cliente</div>
        <div style="font-weight:700;font-size:15px;">${esc(doc.cliNome)}</div>
        <div style="color:#555;font-size:11px;">${esc(cli.tel||"")}${cli.email?` · ${esc(cli.email)}`:""}</div>
        ${cli.end?`<div style="color:#555;font-size:11px;">${esc(cli.end)}</div>`:""}
        ${cli.nuit?`<div style="color:#555;font-size:11px;">NUIT: ${esc(cli.nuit)}</div>`:""}
      </div>
      <table class="pdf-tbl">
        <thead><tr><th>#</th><th style="text-align:left;">Descrição</th><th>Un.</th><th>Qty</th><th>Preço Unit.</th><th>Total</th></tr></thead>
        <tbody>${rows}</tbody>
      </table>
      <div class="pdf-total">
        <div style="display:flex;justify-content:space-between;margin-bottom:5px;font-size:12px;"><span>Subtotal</span><span>${mzn(doc.subtotal,doc.moeda)}</span></div>
        ${doc.ivaPct>0?`<div style="display:flex;justify-content:space-between;margin-bottom:5px;font-size:12px;"><span>IVA (${doc.ivaPct}%)</span><span>${mzn(doc.iva,doc.moeda)}</span></div>`:""}
        ${doc.desconto>0?`<div style="display:flex;justify-content:space-between;margin-bottom:5px;font-size:12px;"><span>Desconto</span><span>-${mzn(doc.desconto,doc.moeda)}</span></div>`:""}
        <div style="border-top:1px solid rgba(255,255,255,.2);padding-top:9px;display:flex;justify-content:space-between;font-size:16px;font-weight:800;"><span>TOTAL</span><span style="color:#d4a820;">${mzn(doc.total,doc.moeda)}</span></div>
        ${isVenda?`<div style="display:flex;justify-content:space-between;margin-top:5px;font-size:12px;color:rgba(255,255,255,.7);"><span>Valor Pago</span><span style="color:#1eb87a;">${mzn(doc.pago||0,doc.moeda)}</span></div>
        <div style="display:flex;justify-content:space-between;font-size:12px;color:rgba(255,255,255,.7);"><span>Saldo</span><span style="color:#ff9090;">${mzn(Math.max(0,doc.total-(doc.pago||0)),doc.moeda)}</span></div>`:""}
      </div>
      ${pgRows}
      ${doc.notas?`<div style="background:#fffbea;border:1px solid #ffe070;border-radius:8px;padding:10px 13px;margin-top:12px;font-size:12px;"><b>Observações:</b> ${esc(doc.notas)}</div>`:""}
      ${termosH}
      <div style="border-top:2px solid #eee;padding-top:12px;margin-top:14px;text-align:center;font-size:10px;color:#999;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:9px;margin-top:14px;justify-content:flex-end;flex-wrap:wrap;">
      <button class="btn btn-g" onclick="sendWA(${id},'${tipo}')">💬 WhatsApp</button>
      <button class="btn btn-p" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"xl");
}

function printDoc(){
  const c=document.getElementById("pdf-content");
  if(!c)return;
  const pa=document.getElementById("print-area");
  pa.innerHTML=c.outerHTML;
  pa.style.display="block";
  window.print();
  setTimeout(()=>{pa.style.display="none";pa.innerHTML="";},1000);
}

function sendWA(id,tipo){
  const doc=tipo==="cot"?DB.cotacoes.find(x=>x.id===id):DB.vendas.find(x=>x.id===id);
  if(!doc)return;
  const cli=DB.clientes.find(x=>x.id===doc.cliId);
  if(!cli?.tel)return alert("Cliente sem telefone!");
  const itens=doc.itens.map(i=>`  • ${i.desc}: ${i.qty}×${mzn(i.preco)} = ${mzn(i.qty*i.preco)}`).join("\n");
  const tp=tipo==="cot"?"COTAÇÃO":"FATURA";
  const num=tipo==="cot"?doc.num:(doc.fatNum||doc.num);
  let msg=DB.cfg.msg_wa
    .replace("{cliente}",doc.cliNome)
    .replace("{tipo}",tp)
    .replace("{numero}",num)
    .replace("{total}",mzn(doc.total))
    .replace("{empresa}",DB.cfg.empresa)
    .replace("{tel}",DB.cfg.tel);
  msg+=`\n\n*${tp} Nº ${num}*\nData: ${doc.data}\n\n*Itens:*\n${itens}\n\nSubtotal: ${mzn(doc.subtotal)}${doc.iva>0?`\nIVA (${doc.ivaPct}%): ${mzn(doc.iva)}`:""}\n*TOTAL: ${mzn(doc.total)}*`;
  if(tipo==="cot")stCot(id,"enviado");
  window.open(`https://wa.me/${cli.tel.replace(/\D/g,"")}?text=${encodeURIComponent(msg)}`,"_blank");
}

// ════════════════════════════════════════════════════════════
// VENDAS — lista
// ════════════════════════════════════════════════════════════
function rVendas(){
  const tV=DB.vendas.reduce((s,v)=>s+v.total,0);
  const tP=DB.vendas.reduce((s,v)=>s+(v.pago||0),0);
  let rows=DB.vendas.map(v=>{
    const cot=DB.cotacoes.find(c=>c.id===v.cotId);
    return`<tr>
      <td style="font-family:monospace;font-size:11px;">${esc(v.fatNum||v.num)}<br/><span style="color:var(--muted);font-size:10px;">${esc(v.num)}</span></td>
      <td style="font-weight:600;">${esc(v.cliNome)}</td>
      <td style="color:var(--muted);font-size:11px;">${v.data}</td>
      <td style="color:var(--gold);font-weight:700;">${mzn(v.total)}</td>
      <td style="color:var(--green);">${mzn(v.pago||0)}</td>
      <td>${bdg(v.status)}</td>
      <td style="text-align:right;">
        <div style="display:flex;gap:4px;justify-content:flex-end;">
          <button class="btn btn-n btn-xs" onclick="pdfDoc(${v.id},'vnd')">📄 FAT</button>
          <button class="btn btn-g btn-xs" onclick="sendWA(${v.id},'vnd')">💬</button>
          <button class="btn btn-b btn-xs" onclick="regPag(${v.id})">💰 Pag.</button>
          <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delVenda(${v.id})">🗑️</button>
        </div>
      </td></tr>`;
  }).reverse().join("");
  return`<div class="ph"><div><div class="ph-title">Vendas & Faturas</div><div class="ph-sub">${DB.vendas.length} vendas · Faturado ${mzn(tV)} · Recebido ${mzn(tP)}</div></div>
    <button class="btn btn-p" onclick="goTo('vendas-nova')">${ico(ICOS.plus,14)} Nova Venda</button></div>
  <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:11px;margin-bottom:16px;">
    <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Total Faturado</div><div class="kpi-v" style="color:var(--gold);">${mzn(tV)}</div></div>
    <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Total Recebido</div><div class="kpi-v" style="color:var(--green);">${mzn(tP)}</div></div>
    <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">A Receber</div><div class="kpi-v" style="color:var(--red);">${mzn(tV-tP)}</div></div>
  </div>
  <div class="card"><table class="tbl"><thead><tr><th>Nº FAT / VND</th><th>Cliente</th><th>Data</th><th>Total</th><th>Recebido</th><th>Status</th><th></th></tr></thead><tbody>${rows||`<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:20px;">Sem vendas. <a onclick="goTo('vendas-nova')" style="color:var(--red);cursor:pointer;">Criar nova venda</a></td></tr>`}</tbody></table></div>`;
}
function delVenda(id){if(!confirm("Eliminar venda?"))return;DB.vendas=DB.vendas.filter(v=>v.id!==id);saveDB(DB);render("vendas");}

function regPag(id){
  const vd=DB.vendas.find(x=>x.id===id);if(!vd)return;
  const saldo=vd.total-(vd.pago||0);
  const pgOpts=DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  openModal(`Registar Pagamento — ${vd.fatNum||vd.num}`,`
    <div style="background:var(--navy);border-radius:8px;padding:12px;margin-bottom:13px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Total da Venda</span><span style="font-weight:700;">${mzn(vd.total)}</span></div>
      <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Já Pago</span><span style="color:var(--green);font-weight:700;">${mzn(vd.pago||0)}</span></div>
      <div style="display:flex;justify-content:space-between;"><span style="color:var(--muted);">Saldo Pendente</span><span style="color:var(--red);font-weight:700;">${mzn(saldo)}</span></div>
    </div>
    <div class="g2">
      <div class="fg"><label class="lbl">Valor a Pagar (MZN)</label><input class="inp" type="number" id="pg-val" value="${saldo}" min="0" max="${saldo}"/></div>
      <div class="fg"><label class="lbl">Forma de Pagamento</label><select class="inp" id="pg-tp">${pgOpts}</select></div>
      <div class="fg"><label class="lbl">Data do Pagamento</label><input class="inp" type="date" id="pg-dt" value="${hoje()}"/></div>
      <div class="fg"><label class="lbl">Referência / Comprovativo</label><input class="inp" id="pg-ref" placeholder="Nº transação, referência..."/></div>
    </div>
    <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="savePag(${id})">${ico(ICOS.check,14)} Registar Pagamento</button></div>`);
}
function savePag(id){
  const val=Number(document.getElementById("pg-val").value);
  if(!val||val<=0)return alert("Valor inválido!");
  DB.vendas=DB.vendas.map(v=>{
    if(v.id!==id)return v;
    const novoPago=Math.min((v.pago||0)+val,v.total);
    const novoPags=[...(v.pagamentos||[]),{tipo:v("pg-tp"),nome:v("pg-tp"),valor:val,data:v("pg-dt"),ref:v("pg-ref")}];
    const st=novoPago>=v.total?"pago":novoPago>0?"parcial":"pendente";
    return{...v,pago:novoPago,pagamentos:novoPags,status:st};
  });
  DB.financeiro.receitas.push({id:Date.now(),desc:`Pagamento ${DB.vendas.find(x=>x.id===id)?.fatNum||""} - ${DB.vendas.find(x=>x.id===id)?.cliNome}`,valor:val,data:v("pg-dt"),cat:"Vendas",status:"recebido",ref:v("pg-ref")});
  addLog(`Pagamento registado: ${mzn(val)}`);saveDB(DB);closeModal();render("vendas");
}

// ════════════════════════════════════════════════════════════
// NOVA VENDA DIRECTA (com desconto, IVA, formas pagamento)
// ════════════════════════════════════════════════════════════
let _vi=[{desc:"",qty:1,un:"un",preco:0,desc_obs:""}];

function rNovaVenda(){
  const cliOpts=DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  const prodOpts=DB.produtos.map(p=>`<option value="${p.id}" data-preco="${p.preco}" data-un="${esc(p.un)}">${esc(p.nome)} — ${mzn(p.preco)}</option>`).join("");
  const pgOpts=DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  _vi=[{desc:"",qty:1,un:"un",preco:0,desc_obs:""}];
  // Will call nv_renderItens after DOM is ready
  setTimeout(()=>{nv_renderItens();nv_calc();},50);
  return`<div class="ph"><div><div class="ph-title">Nova Venda Directa</div><div class="ph-sub">Registe uma venda e gere fatura automaticamente</div></div></div>
  <div style="display:grid;grid-template-columns:2fr 1fr;gap:16px;">
    <div>
      <div class="card" style="margin-bottom:13px;">
        <h3 class="serif" style="font-size:14px;margin-bottom:12px;">1. Cliente</h3>
        <div class="g2">
          <div class="fg cs2"><label class="lbl">Selecionar Cliente</label>
            <select class="inp" id="nv-cli" onchange="nv_fillCli(this)">
              <option value="">Selecionar cliente...</option>${cliOpts}
            </select>
          </div>
          <div class="fg"><label class="lbl">Data da Venda</label><input class="inp" type="date" id="nv-data" value="${hoje()}"/></div>
          <div class="fg"><label class="lbl">Notas</label><input class="inp" id="nv-notas" placeholder="Observações..."/></div>
        </div>
      </div>
      <div class="card" style="margin-bottom:13px;">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:11px;">
          <h3 class="serif" style="font-size:14px;">2. Produtos / Serviços</h3>
          <div style="display:flex;gap:6px;">
            <select id="nv-prod-sel" class="inp" style="width:auto;font-size:12px;padding:5px 8px;" onchange="nv_addProd(this)">
              <option value="">+ Adicionar produto...</option>${prodOpts}
            </select>
            <button class="btn btn-n btn-xs" onclick="nv_addItem()">+ Item manual</button>
          </div>
        </div>
        <div style="background:var(--navy);border-radius:9px;padding:11px;">
          <div class="ir-grid hdr"><div>Descrição</div><div>Un.</div><div>Qty</div><div>Preço Unit.</div><div>Total</div><div></div></div>
          <div id="nv-itens"></div>
          <div style="padding-top:9px;border-top:1px solid var(--border);margin-top:6px;display:flex;justify-content:flex-end;">
            <div style="text-align:right;font-size:13px;min-width:220px;">
              <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Subtotal</span><span id="nv-sub">0 MZN</span></div>
              <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">IVA (<span id="nv-iva-pct-disp">${DB.cfg.iva}</span>%)</span><span id="nv-iva">0 MZN</span></div>
              <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Desconto</span><span id="nv-dsc-disp">0 MZN</span></div>
              <div style="display:flex;justify-content:space-between;font-size:17px;font-weight:800;color:var(--gold);"><span>TOTAL</span><span id="nv-tot">0 MZN</span></div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div>
      <div class="card" style="margin-bottom:13px;">
        <h3 class="serif" style="font-size:14px;margin-bottom:12px;">3. Impostos & Desconto</h3>
        <div class="fg"><label class="lbl">IVA %</label><input class="inp" type="number" id="nv-iva-pct" value="${DB.cfg.iva}" min="0" max="100" oninput="nv_calc()"/></div>
        <div class="fg"><label class="lbl">Desconto (${DB.cfg.moeda})</label><input class="inp" type="number" id="nv-dsc" value="0" min="0" oninput="nv_calc()"/></div>
      </div>
      <div class="card" style="margin-bottom:13px;">
        <h3 class="serif" style="font-size:14px;margin-bottom:12px;">4. Pagamento</h3>
        <div class="fg"><label class="lbl">Forma de Pagamento</label><select class="inp" id="nv-pgtp">${pgOpts}</select></div>
        <div class="fg"><label class="lbl">Valor Pago Agora (${DB.cfg.moeda})</label><input class="inp" type="number" id="nv-pago" value="0" min="0" oninput="nv_calc()"/></div>
        <div class="fg"><label class="lbl">Referência</label><input class="inp" id="nv-ref" placeholder="Nº transação, referência..."/></div>
        <div id="nv-saldo-info" style="background:var(--navy);border-radius:8px;padding:10px;font-size:12px;margin-top:5px;">
          <div style="display:flex;justify-content:space-between;margin-bottom:3px;"><span style="color:var(--muted);">Total da Venda</span><span id="nv-tot2">0 MZN</span></div>
          <div style="display:flex;justify-content:space-between;"><span style="color:var(--muted);">Saldo a Pagar</span><span id="nv-sld" style="color:var(--red);font-weight:700;">0 MZN</span></div>
        </div>
      </div>
      <button class="btn btn-p" style="width:100%;justify-content:center;padding:13px;font-size:14px;" onclick="finalizarVenda()">
        ${ico(ICOS.check,16)} Finalizar Venda & Gerar Fatura</button>
      <button class="btn btn-n" style="width:100%;justify-content:center;margin-top:8px;" onclick="nv_salvarCot()">
        ${ico(ICOS.cot,14)} Guardar como Cotação</button>
    </div>
  </div>`;
}
function nv_fillCli(sel){}
function nv_addProd(sel){
  const opt=sel.options[sel.selectedIndex];if(!opt.value)return;
  const preco=Number(opt.dataset.preco||0);const un=opt.dataset.un||"un";
  _vi.push({desc:opt.text.split(" — ")[0],qty:1,un,preco,desc_obs:""});
  sel.value="";nv_renderItens();
}
function nv_addItem(){_vi.push({desc:"",qty:1,un:"un",preco:0,desc_obs:""});nv_renderItens();}
function nv_remItem(i){if(_vi.length===1)return;_vi.splice(i,1);nv_renderItens();}
function nv_updItem(i,k,val){_vi[i][k]=["qty","preco"].includes(k)?Number(val):val;nv_calc();}
function nv_renderItens(){
  const cont=document.getElementById("nv-itens");if(!cont)return;
  cont.innerHTML=_vi.map((it,i)=>`<div class="ir-grid" style="margin-bottom:5px;">
    <input class="inp" style="padding:7px 8px;font-size:12px;" placeholder="Descrição" value="${esc(it.desc)}" oninput="nv_updItem(${i},'desc',this.value)"/>
    <input class="inp" style="padding:7px 8px;font-size:12px;" placeholder="un" value="${esc(it.un)}" oninput="nv_updItem(${i},'un',this.value)"/>
    <input class="inp" type="number" style="padding:7px 8px;font-size:12px;" value="${it.qty}" oninput="nv_updItem(${i},'qty',this.value)" min="1"/>
    <input class="inp" type="number" style="padding:7px 8px;font-size:12px;" value="${it.preco}" oninput="nv_updItem(${i},'preco',this.value)" min="0"/>
    <div style="color:var(--gold);font-size:12px;font-weight:700;display:flex;align-items:center;">${mzn(it.qty*it.preco)}</div>
    <button onclick="nv_remItem(${i})" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:16px;">×</button></div>`).join("");
  nv_calc();
}
function nv_calc(){
  const sub=_vi.reduce((s,it)=>s+it.qty*it.preco,0);
  const ivaPct=Number(document.getElementById("nv-iva-pct")?.value||0);
  const dsc=Number(document.getElementById("nv-dsc")?.value||0);
  const pago=Number(document.getElementById("nv-pago")?.value||0);
  const iva=sub*(ivaPct/100);const tot=Math.max(0,sub+iva-dsc);const sld=Math.max(0,tot-pago);
  const upd=(id,v)=>{const e=document.getElementById(id);if(e)e.textContent=v;};
  upd("nv-sub",mzn(sub));upd("nv-iva",mzn(iva));upd("nv-dsc-disp",mzn(dsc));
  upd("nv-tot",mzn(tot));upd("nv-tot2",mzn(tot));upd("nv-sld",mzn(sld));
  const pp=document.getElementById("nv-iva-pct-disp");if(pp)pp.textContent=ivaPct;
}
function finalizarVenda(){
  const cliId=Number(document.getElementById("nv-cli")?.value);
  if(!cliId||!_vi[0].desc)return alert("Selecione cliente e adicione pelo menos 1 item!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  const sub=_vi.reduce((s,it)=>s+it.qty*it.preco,0);
  const ivaPct=Number(document.getElementById("nv-iva-pct").value||0);
  const dsc=Number(document.getElementById("nv-dsc").value||0);
  const iva=sub*(ivaPct/100);const tot=Math.max(0,sub+iva-dsc);
  const pago=Math.min(Number(document.getElementById("nv-pago").value||0),tot);
  const num=pad(DB.vendSeq,"VND");const fn=pad(DB.fatSeq,"FAT");
  const st=pago>=tot?"pago":pago>0?"parcial":"pendente";
  const vd={id:Date.now(),cliId,cliNome:cli.nome,cotId:null,num,fatNum:fn,data:v("nv-data")||hoje(),
    itens:_vi.map(it=>({...it,qty:Number(it.qty),preco:Number(it.preco)})),
    subtotal:sub,desconto:dsc,ivaPct,iva,total:tot,pago,status:st,
    pagamentos:pago>0?[{tipo:v("nv-pgtp"),nome:v("nv-pgtp"),valor:pago,data:v("nv-data")||hoje(),ref:v("nv-ref")}]:[],
    notas:v("nv-notas"),moeda:DB.cfg.moeda};
  DB.vendas.push(vd);DB.vendSeq++;DB.fatSeq++;
  if(pago>0)DB.financeiro.receitas.push({id:Date.now(),desc:`${fn} - ${cli.nome}`,valor:pago,data:vd.data,cat:"Vendas",status:"recebido",ref:v("nv-ref")});
  addLog(`Nova venda ${num} / ${fn} — ${cli.nome} — ${mzn(tot)}`);saveDB(DB);
  if(confirm(`Venda ${fn} criada com sucesso!\nDeseja visualizar a fatura?`)){render("vendas");setTimeout(()=>pdfDoc(vd.id,"vnd"),300);}
  else{render("vendas");}
}
function nv_salvarCot(){
  const cliId=Number(document.getElementById("nv-cli")?.value);
  if(!cliId||!_vi[0].desc)return alert("Selecione cliente e adicione pelo menos 1 item!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  const sub=_vi.reduce((s,it)=>s+it.qty*it.preco,0);
  const ivaPct=Number(document.getElementById("nv-iva-pct").value||0);
  const dsc=Number(document.getElementById("nv-dsc").value||0);
  const iva=sub*(ivaPct/100);const tot=Math.max(0,sub+iva-dsc);
  const num=pad(DB.cotSeq);
  DB.cotacoes.push({id:Date.now(),num,cliId,cliNome:cli.nome,data:v("nv-data")||hoje(),val:"",
    itens:_vi.map(it=>({...it})),subtotal:sub,ivaPct,iva,desconto:dsc,total:tot,
    status:"pendente",notas:v("nv-notas"),moeda:DB.cfg.moeda});
  DB.cotSeq++;addLog(`Cotação ${num} criada a partir de venda`);saveDB(DB);
  alert(`Cotação ${num} guardada!`);goTo("cotacoes");
}

// ════════════════════════════════════════════════════════════
// ESTOQUE
// ════════════════════════════════════════════════════════════
function rEstoque(){
  const crit=DB.produtos.filter(p=>p.estoque<=p.min);
  let rows=DB.produtos.map(p=>{
    const baixo=p.estoque<=p.min;
    const mg=p.preco>0?Math.round(((p.preco-p.custo)/p.preco)*100):0;
    const pc=Math.min((p.estoque/(Math.max(p.min,1)*3))*100,100);
    return`<div class="card" style="margin-bottom:8px;border-left:4px solid ${baixo?"var(--red)":"var(--green)"};">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
        <div style="flex:1;">
          <div style="display:flex;gap:8px;align-items:center;margin-bottom:5px;flex-wrap:wrap;">
            <span style="font-weight:700;font-size:14px;">${esc(p.nome)}</span>
            ${bdgC(p.cat,"var(--navy3)")}
            ${baixo?bdgC("CRÍTICO","var(--red)"):""}
          </div>
          <div style="color:var(--muted);font-size:12px;margin-bottom:7px;">Venda: ${mzn(p.preco)} · Custo: ${mzn(p.custo)} · Margem: ${mg}%</div>
          ${pb(pc,baixo?"var(--red)":"var(--green)")}
        </div>
        <div style="display:flex;align-items:center;gap:12px;">
          <div style="text-align:right;">
            <div style="color:${baixo?"var(--red)":"var(--green)"};font-size:24px;font-weight:800;">${p.estoque}</div>
            <div style="color:var(--muted);font-size:11px;">${esc(p.un)} (mín: ${p.min})</div>
          </div>
          <div style="display:flex;gap:4px;">
            <button class="btn btn-n btn-xs" onclick="editEst(${p.id})">✏️</button>
            <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delEst(${p.id})">🗑️</button>
          </div>
        </div>
      </div></div>`;
  }).join("");
  return`<div class="ph"><div><div class="ph-title">Controlo de Estoque</div><div class="ph-sub">${DB.produtos.length} produtos · ${crit.length} críticos</div></div>
    <button class="btn btn-p" onclick="novoEst()">${ico(ICOS.plus,14)} Novo Produto</button></div>
  ${crit.length?`<div class="alert-r"><b>⚠️ ${crit.length} produto(s) com estoque crítico:</b> ${crit.map(p=>esc(p.nome)).join(", ")}</div>`:""}
  ${rows}`;
}
function novoEst(){_fEst(null);}
function editEst(id){_fEst(DB.produtos.find(p=>p.id===id));}
function _fEst(p){
  openModal(p?"Editar Produto":"Novo Produto",`
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome do Produto / Serviço</label><input class="inp" id="ef-n" value="${esc(p?.nome||"")}" placeholder="Nome completo"/></div>
      <div class="fg"><label class="lbl">Categoria</label><input class="inp" id="ef-c" value="${esc(p?.cat||"")}"/></div>
      <div class="fg"><label class="lbl">Unidade</label><input class="inp" id="ef-u" value="${esc(p?.un||"un")}" placeholder="un, m, kg, ch, saco..."/></div>
      <div class="fg"><label class="lbl">Preço de Venda (${DB.cfg.moeda})</label><input class="inp" type="number" id="ef-pv" value="${p?.preco||0}" min="0"/></div>
      <div class="fg"><label class="lbl">Custo (${DB.cfg.moeda})</label><input class="inp" type="number" id="ef-pc" value="${p?.custo||0}" min="0"/></div>
      <div class="fg"><label class="lbl">Estoque Actual</label><input class="inp" type="number" id="ef-es" value="${p?.estoque||0}" min="0"/></div>
      <div class="fg"><label class="lbl">Estoque Mínimo (Alerta)</label><input class="inp" type="number" id="ef-em" value="${p?.min||0}" min="0"/></div>
    </div>
    <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveEst(${p?.id||0})">${ico(ICOS.check,14)} Guardar</button></div>`);
}
function saveEst(id){
  const n=document.getElementById("ef-n").value.trim();if(!n)return alert("Nome obrigatório!");
  const o={id:id||Date.now(),nome:n,cat:v("ef-c"),un:v("ef-u"),preco:Number(v("ef-pv")),custo:Number(v("ef-pc")),estoque:Number(v("ef-es")),min:Number(v("ef-em"))};
  if(id)DB.produtos=DB.produtos.map(p=>p.id===id?o:p);else DB.produtos.push(o);
  addLog((id?"Editou":"Adicionou")+" produto: "+n);saveDB(DB);closeModal();render("estoque");
}
function delEst(id){if(!confirm("Eliminar produto?"))return;DB.produtos=DB.produtos.filter(p=>p.id!==id);saveDB(DB);render("estoque");}

// ════════════════════════════════════════════════════════════
// OBRAS
// ════════════════════════════════════════════════════════════
function rObras(){
  let cards=DB.obras.map(o=>`<div class="card" style="margin-bottom:11px;border-left:4px solid var(--blue);">
    <div style="display:flex;justify-content:space-between;margin-bottom:11px;flex-wrap:wrap;gap:8px;">
      <div><div style="font-weight:700;font-size:16px;">${esc(o.nome)}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:3px;">👤 ${esc(o.cliNome)} · 👷 ${esc(o.resp)}</div>
        <div style="color:var(--muted);font-size:12px;">📅 ${o.inicio} → ${o.fim}</div>
      </div>
      <div style="text-align:right;"><div style="color:var(--blue);font-size:18px;font-weight:800;">${mzn(o.valor)}</div>${bdg(o.status)}</div>
    </div>
    <div style="margin-bottom:7px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:5px;"><span style="color:var(--muted);font-size:12px;">Progresso</span><span style="color:var(--blue);font-weight:700;">${o.prog}%</span></div>
      ${pb(o.prog,"var(--blue)")}
    </div>
    <div style="display:flex;align-items:center;gap:8px;margin-top:7px;">
      <input type="range" min="0" max="100" value="${o.prog}" oninput="updObra(${o.id},this.value)" style="flex:1;accent-color:var(--blue);"/>
      <button class="btn btn-n btn-xs" onclick="delObra(${o.id})" style="color:var(--red);">🗑️</button>
    </div></div>`).join("");
  return`<div class="ph"><div><div class="ph-title">Gestão de Obras</div><div class="ph-sub">${DB.obras.length} obra(s)</div></div>
    <button class="btn btn-p" onclick="novaObra()">${ico(ICOS.plus,14)} Nova Obra</button></div>${cards||'<div class="alert-w">Sem obras registadas.</div>'}`;
}
function updObra(id,v2){DB.obras=DB.obras.map(o=>o.id===id?{...o,prog:Number(v2)}:o);saveDB(DB);}
function delObra(id){if(!confirm("Eliminar obra?"))return;DB.obras=DB.obras.filter(o=>o.id!==id);saveDB(DB);render("obras");}
function novaObra(){
  const co=DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  openModal("Nova Obra",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Nome da Obra</label><input class="inp" id="ob-n" placeholder="Ex: Moradia T3 - Bairro X"/></div>
    <div class="fg cs2"><label class="lbl">Cliente</label><select class="inp" id="ob-c"><option value="">Selecionar...</option>${co}</select></div>
    <div class="fg"><label class="lbl">Valor Total (${DB.cfg.moeda})</label><input class="inp" type="number" id="ob-v"/></div>
    <div class="fg"><label class="lbl">Responsável</label><input class="inp" id="ob-r"/></div>
    <div class="fg"><label class="lbl">Início</label><input class="inp" type="date" id="ob-i" value="${hoje()}"/></div>
    <div class="fg"><label class="lbl">Conclusão Prevista</label><input class="inp" type="date" id="ob-f"/></div>
    <div class="fg cs2"><label class="lbl">Notas</label><textarea class="inp" id="ob-no" style="height:55px;resize:vertical;"></textarea></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveObra()">${ico(ICOS.check,14)} Guardar</button></div>`);
}
function saveObra(){
  const n=v("ob-n");const cliId=Number(v("ob-c"));if(!n||!cliId)return alert("Nome e cliente obrigatórios!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  DB.obras.push({id:Date.now(),nome:n,cliId,cliNome:cli.nome,valor:Number(v("ob-v")),inicio:v("ob-i"),fim:v("ob-f"),prog:0,status:"andamento",resp:v("ob-r"),notas:v("ob-no")});
  addLog("Nova obra: "+n);saveDB(DB);closeModal();render("obras");
}

// ════════════════════════════════════════════════════════════
// FINANCEIRO
// ════════════════════════════════════════════════════════════
let _fAba="receitas";
function rFinanceiro(){
  const tR=DB.financeiro.receitas.reduce((s,r)=>s+r.valor,0);
  const tD=DB.financeiro.despesas.reduce((s,d)=>s+d.valor,0);
  const sl=tR-tD;
  const lista=_fAba==="receitas"?DB.financeiro.receitas:DB.financeiro.despesas;
  let rows=[...lista].reverse().map(it=>`<div class="card" style="margin-bottom:8px;">
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
      <div><div style="font-weight:600;font-size:14px;">${esc(it.desc)}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:3px;">${it.data} · ${esc(it.cat)}${it.ref?` · Ref: ${esc(it.ref)}`:""}</div></div>
      <div style="display:flex;align-items:center;gap:10px;">
        <div style="color:${_fAba==="receitas"?"var(--green)":"var(--red)"};font-size:18px;font-weight:800;">${mzn(it.valor)}</div>
        ${bdg(it.status)}
      </div>
    </div></div>`).join("");
  return`<div class="ph"><h2 class="ph-title">Controlo Financeiro</h2></div>
  <div class="g3" style="margin-bottom:16px;">
    <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Receitas</div><div class="kpi-v" style="color:var(--green);">${mzn(tR)}</div></div>
    <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Despesas</div><div class="kpi-v" style="color:var(--red);">${mzn(tD)}</div></div>
    <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Saldo Líquido</div><div class="kpi-v" style="color:${sl>=0?"var(--gold)":"var(--red)"};">${mzn(sl)}</div></div>
  </div>
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:13px;flex-wrap:wrap;gap:8px;">
    <div class="tabs" style="margin:0;">
      <button class="tab${_fAba==="receitas"?" active":""}" onclick="_setFA('receitas')">Receitas</button>
      <button class="tab${_fAba==="despesas"?" active":""}" onclick="_setFA('despesas')">Despesas</button>
    </div>
    <button class="btn btn-p" onclick="novoLanc()">${ico(ICOS.plus,14)} Novo Lançamento</button>
  </div>${rows||'<div class="alert-w">Sem lançamentos.</div>'}`;
}
function _setFA(a){_fAba=a;render("financeiro");}
function novoLanc(){
  const cats_r=["Serviços","Produtos","Obras","Vendas","Outros"];
  const cats_d=["RH","Estoque","Infraestrutura","Marketing","Fornecedores","Impostos","Outros"];
  openModal(`Novo Lançamento — ${_fAba}`,`<div class="g2">
    <div class="fg cs2"><label class="lbl">Descrição</label><input class="inp" id="fl-d" placeholder="Descrição detalhada"/></div>
    <div class="fg"><label class="lbl">Valor (${DB.cfg.moeda})</label><input class="inp" type="number" id="fl-v" min="0"/></div>
    <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="fl-dt" value="${hoje()}"/></div>
    <div class="fg"><label class="lbl">Categoria</label><select class="inp" id="fl-c">${(_fAba==="receitas"?cats_r:cats_d).map(c=>`<option>${c}</option>`).join("")}</select></div>
    <div class="fg"><label class="lbl">Status</label><select class="inp" id="fl-s">${_fAba==="receitas"?'<option value="pendente">Pendente</option><option value="recebido">Recebido</option>':'<option value="pendente">Pendente</option><option value="pago">Pago</option>'}</select></div>
    <div class="fg"><label class="lbl">Referência</label><input class="inp" id="fl-r" placeholder="Nº doc, referência..."/></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveLanc()">${ico(ICOS.check,14)} Guardar</button></div>`);
}
function saveLanc(){
  const d=v("fl-d");const vl=Number(v("fl-v"));if(!d||!vl)return alert("Preencha descrição e valor!");
  DB.financeiro[_fAba].push({id:Date.now(),desc:d,valor:vl,data:v("fl-dt"),cat:v("fl-c"),status:v("fl-s"),ref:v("fl-r")});
  addLog(`Lançamento ${_fAba}: ${d}`);saveDB(DB);closeModal();render("financeiro");
}

// ════════════════════════════════════════════════════════════
// RH — RECURSOS HUMANOS COMPLETO
// ════════════════════════════════════════════════════════════
let _rhAba="funcionarios";
function rRH(){
  const abas=[["funcionarios","👥 Funcionários"],["presencas","📋 Presenças"],["folha","💰 Folha Salarial"],["ferias","🏖️ Férias"],["avaliacoes","⭐ Avaliações"]];
  let tabHtml=abas.map(([id,l])=>`<button class="tab${_rhAba===id?" active":""}" onclick="_setRH('${id}')">${l}</button>`).join("");
  let content="";
  const rh=DB.rh;
  if(_rhAba==="funcionarios"){
    let cards=rh.funcionarios.map(f=>{
      const salLiq=f.salario_base-(f.salario_base*(f.inss_pct||3)/100)-(f.salario_base*(f.irps_pct||0)/100)+(f.bonus||0)+(f.comissoes||0);
      return`<div class="card" style="margin-bottom:10px;">
        <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:10px;">
          <div style="display:flex;gap:12px;align-items:center;">
            <div style="width:46px;height:46px;background:linear-gradient(135deg,var(--red),var(--red2));border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800;font-size:18px;flex-shrink:0;">${f.nome[0]}</div>
            <div>
              <div style="font-weight:700;font-size:15px;">${esc(f.nome)}</div>
              <div style="color:var(--muted);font-size:12px;">${esc(f.cargo)} · ${esc(f.dep)}</div>
              <div style="color:var(--muted);font-size:12px;">📞 ${esc(f.tel||"")} · Admissão: ${f.data_admissao}</div>
            </div>
          </div>
          <div style="text-align:right;">
            <div style="color:var(--gold);font-weight:800;font-size:16px;">${mzn(f.salario_base)}/mês</div>
            <div style="color:var(--green);font-size:12px;">Líquido: ${mzn(salLiq)}</div>
            ${bdg(f.status)}
          </div>
        </div>
        <hr class="dv" style="margin:10px 0;"/>
        <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;font-size:12px;">
          <div><div style="color:var(--muted);">INSS</div><div style="color:var(--red);">${f.inss_pct||3}% = ${mzn(f.salario_base*(f.inss_pct||3)/100)}</div></div>
          <div><div style="color:var(--muted);">IRPS</div><div style="color:var(--orange);">${f.irps_pct||0}% = ${mzn(f.salario_base*(f.irps_pct||0)/100)}</div></div>
          <div><div style="color:var(--muted);">Bónus</div><div style="color:var(--green);">${mzn(f.bonus||0)}</div></div>
          <div><div style="color:var(--muted);">Contrato</div><div>${esc(f.tipo_contrato||"")}</div></div>
        </div>
        <div style="display:flex;gap:6px;margin-top:10px;">
          <button class="btn btn-n btn-xs" onclick="editFunc(${f.id})">✏️ Editar</button>
          <button class="btn btn-g btn-xs" onclick="gerarRecibo(${f.id})">📄 Recibo</button>
          ${f.mpesa?`<button class="btn btn-xs" style="background:rgba(30,184,122,.15);color:var(--green);border:none;" onclick="pgMpesa(${f.id})">📱 M-Pesa</button>`:""}
          ${f.banco?`<button class="btn btn-xs" style="background:rgba(74,158,255,.15);color:var(--blue);border:none;" onclick="pgBanco(${f.id})">🏦 Banco</button>`:""}
          <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delFunc(${f.id})">🗑️</button>
        </div>
      </div>`;
    }).join("");
    const totalFolha=rh.funcionarios.reduce((s,f)=>s+f.salario_base,0);
    content=`<div style="display:grid;grid-template-columns:repeat(3,1fr);gap:11px;margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Total Folha Bruta</div><div class="kpi-v" style="color:var(--gold);">${mzn(totalFolha)}</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Funcionários Activos</div><div class="kpi-v" style="color:var(--blue);">${rh.funcionarios.filter(f=>f.status==="ativo").length}</div></div>
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Departamentos</div><div class="kpi-v" style="color:var(--green);">${[...new Set(rh.funcionarios.map(f=>f.dep))].length}</div></div>
    </div>
    <div style="display:flex;justify-content:flex-end;margin-bottom:12px;">
      <button class="btn btn-p" onclick="novoFunc()">+ Novo Funcionário</button>
    </div>${cards||'<div class="alert-w">Sem funcionários cadastrados.</div>'}`;
  } else if(_rhAba==="presencas"){
    const hoje2=hoje();
    let rows=rh.funcionarios.map(f=>{
      const pr=rh.presencas.find(p=>p.funcId===f.id&&p.data===hoje2)||{tipo:"falta",entrada:"",saida:""};
      const si=SI(pr.tipo||"falta");
      return`<tr>
        <td style="font-weight:600;">${esc(f.nome)}</td>
        <td style="color:var(--muted);font-size:12px;">${esc(f.dep)}</td>
        <td><input type="time" class="inp" style="padding:5px 8px;width:100px;font-size:12px;" value="${pr.entrada||""}" onchange="regPresenca(${f.id},'entrada',this.value,'${hoje2}')"/></td>
        <td><input type="time" class="inp" style="padding:5px 8px;width:100px;font-size:12px;" value="${pr.saida||""}" onchange="regPresenca(${f.id},'saida',this.value,'${hoje2}')"/></td>
        <td><select class="inp" style="padding:5px 8px;width:110px;font-size:12px;" onchange="regPresenca(${f.id},'tipo',this.value,'${hoje2}')">
          <option value="normal" ${pr.tipo==="normal"?"selected":""}>✅ Presente</option>
          <option value="falta" ${pr.tipo==="falta"?"selected":""}>❌ Falta</option>
          <option value="atraso" ${pr.tipo==="atraso"?"selected":""}>⏰ Atraso</option>
          <option value="ferias" ${pr.tipo==="ferias"?"selected":""}>🏖️ Férias</option>
        </select></td>
        <td>${bdgC(si.l,si.c)}</td>
      </tr>`;
    }).join("");
    content=`<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;flex-wrap:wrap;gap:8px;">
      <div style="color:var(--text);font-weight:600;">Presenças — ${hoje2}</div>
      <button class="btn btn-p btn-sm" onclick="render('rh-mod')">🔄 Actualizar</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Funcionário</th><th>Dep.</th><th>Entrada</th><th>Saída</th><th>Tipo</th><th>Status</th></tr></thead><tbody>${rows}</tbody></table></div>`;
  } else if(_rhAba==="folha"){
    const mes=hoje().substring(0,7);
    let rows=rh.funcionarios.map(f=>{
      const bruto=f.salario_base+(f.bonus||0)+(f.comissoes||0);
      const inss=f.salario_base*(f.inss_pct||3)/100;
      const irps=f.salario_base*(f.irps_pct||0)/100;
      const liq=bruto-inss-irps;
      return`<tr>
        <td style="font-weight:600;">${esc(f.nome)}</td>
        <td style="color:var(--muted);font-size:12px;">${esc(f.dep)}</td>
        <td>${mzn(f.salario_base)}</td>
        <td style="color:var(--green);">+${mzn((f.bonus||0)+(f.comissoes||0))}</td>
        <td style="color:var(--red);">-${mzn(inss)}</td>
        <td style="color:var(--orange);">-${mzn(irps)}</td>
        <td style="color:var(--gold);font-weight:700;">${mzn(liq)}</td>
        <td>
          <div style="display:flex;gap:4px;">
            <button class="btn btn-g btn-xs" onclick="gerarRecibo(${f.id})">📄 Recibo</button>
            <button class="btn btn-b btn-xs" onclick="pagarFunc(${f.id})">💸 Pagar</button>
          </div>
        </td>
      </tr>`;
    }).join("");
    const totBruto=rh.funcionarios.reduce((s,f)=>s+(f.salario_base+(f.bonus||0)+(f.comissoes||0)),0);
    const totLiq=rh.funcionarios.reduce((s,f)=>{
      const b=f.salario_base+(f.bonus||0)+(f.comissoes||0);
      const desc=f.salario_base*(f.inss_pct||3)/100+f.salario_base*(f.irps_pct||0)/100;
      return s+b-desc;
    },0);
    content=`<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:11px;margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Total Bruto</div><div class="kpi-v" style="color:var(--blue);">${mzn(totBruto)}</div></div>
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Descontos (INSS+IRPS)</div><div class="kpi-v" style="color:var(--red);">${mzn(totBruto-totLiq)}</div></div>
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Total Líquido a Pagar</div><div class="kpi-v" style="color:var(--gold);">${mzn(totLiq)}</div></div>
    </div>
    <div style="display:flex;justify-content:flex-end;margin-bottom:10px;gap:8px;">
      <button class="btn btn-p btn-sm" onclick="pagarTodos()">💸 Processar Folha Completa</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Funcionário</th><th>Dep.</th><th>Salário Base</th><th>Bónus</th><th>INSS</th><th>IRPS</th><th>Líquido</th><th></th></tr></thead><tbody>${rows}</tbody></table></div>`;
  } else if(_rhAba==="ferias"){
    let rows=rh.ferias.map(f=>`<tr>
      <td style="font-weight:600;">${esc(f.funcNome)}</td>
      <td>${f.inicio}</td><td>${f.fim}</td><td>${f.dias} dias</td>
      <td>${bdg(f.status)}</td>
      <td>${esc(f.obs||"")}</td>
      <td><div style="display:flex;gap:4px;">
        ${f.status==="pendente"?`<button class="btn btn-g btn-xs" onclick="aprFerias(${f.id})">✓ Aprovar</button>`:""}
        <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delFerias(${f.id})">🗑️</button>
      </div></td>
    </tr>`).join("");
    content=`<div style="display:flex;justify-content:flex-end;margin-bottom:12px;">
      <button class="btn btn-p" onclick="novasFerias()">+ Solicitar Férias</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Funcionário</th><th>Início</th><th>Fim</th><th>Dias</th><th>Status</th><th>Obs.</th><th></th></tr></thead><tbody>${rows||'<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:20px;">Sem registos de férias.</td></tr>'}</tbody></table></div>`;
  } else if(_rhAba==="avaliacoes"){
    let rows=rh.avaliacoes.map(a=>{
      const stars="⭐".repeat(a.nota||0)+"☆".repeat(5-(a.nota||0));
      return`<tr>
        <td style="font-weight:600;">${esc(a.funcNome)}</td>
        <td>${a.data}</td><td>${esc(a.periodo)}</td>
        <td>${stars} (${a.nota}/5)</td>
        <td style="color:var(--muted);font-size:12px;">${esc(a.comentario||"")}</td>
        <td>${esc(a.avaliador)}</td>
      </tr>`;
    }).join("");
    content=`<div style="display:flex;justify-content:flex-end;margin-bottom:12px;">
      <button class="btn btn-p" onclick="novaAval()">+ Nova Avaliação</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Funcionário</th><th>Data</th><th>Período</th><th>Nota</th><th>Comentário</th><th>Avaliador</th></tr></thead><tbody>${rows||'<tr><td colspan="6" style="text-align:center;color:var(--muted);padding:20px;">Sem avaliações.</td></tr>'}</tbody></table></div>`;
  }
  return`<div class="ph"><div class="ph-title">Recursos Humanos</div></div>
  <div class="tabs">${tabHtml}</div>${content}`;
}
function _setRH(a){_rhAba=a;render("rh-mod");}

function novoFunc(){
  const pgOpts=DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  openModal("Novo Funcionário",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Nome Completo</label><input class="inp" id="rf-n" placeholder="Nome completo"/></div>
    <div class="fg"><label class="lbl">BI / Passaporte</label><input class="inp" id="rf-bi"/></div>
    <div class="fg"><label class="lbl">Data Nascimento</label><input class="inp" type="date" id="rf-nasc"/></div>
    <div class="fg"><label class="lbl">Telefone</label><input class="inp" id="rf-tel" placeholder="+258 8X XXX XXXX"/></div>
    <div class="fg"><label class="lbl">Email</label><input class="inp" id="rf-email"/></div>
    <div class="fg"><label class="lbl">Cargo / Função</label><input class="inp" id="rf-cargo"/></div>
    <div class="fg"><label class="lbl">Departamento</label>
      <select class="inp" id="rf-dep"><option>Obras</option><option>Produção</option><option>Design</option><option>Administrativo</option><option>Vendas</option><option>Financeiro</option><option>RH</option><option>Outros</option></select></div>
    <div class="fg"><label class="lbl">Tipo de Contrato</label>
      <select class="inp" id="rf-cont"><option value="efectivo">Efectivo</option><option value="prazo">A Prazo</option><option value="freelance">Freelance</option></select></div>
    <div class="fg"><label class="lbl">Data de Admissão</label><input class="inp" type="date" id="rf-adm" value="${hoje()}"/></div>
    <div class="fg"><label class="lbl">Salário Base (${DB.cfg.moeda})</label><input class="inp" type="number" id="rf-sal" min="0"/></div>
    <div class="fg"><label class="lbl">INSS %</label><input class="inp" type="number" id="rf-inss" value="3" min="0" max="100"/></div>
    <div class="fg"><label class="lbl">IRPS %</label><input class="inp" type="number" id="rf-irps" value="0" min="0" max="100"/></div>
    <div class="fg"><label class="lbl">Bónus Mensal</label><input class="inp" type="number" id="rf-bonus" value="0" min="0"/></div>
    <div class="fg"><label class="lbl">Banco</label><input class="inp" id="rf-banco" placeholder="BIM, BCI, FNB..."/></div>
    <div class="fg"><label class="lbl">Nº Conta Bancária</label><input class="inp" id="rf-conta"/></div>
    <div class="fg"><label class="lbl">M-Pesa / e-Mola</label><input class="inp" id="rf-mpesa" placeholder="+258 8X XXX XXXX"/></div>
    <div class="fg cs2"><label class="lbl">Notas</label><textarea class="inp" id="rf-notas" style="height:50px;resize:vertical;"></textarea></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveFunc(0)">${ico(ICOS.check,14)} Guardar</button></div>`,"wide");
}

function editFunc(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  openModal("Editar Funcionário",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Nome</label><input class="inp" id="rf-n" value="${esc(f.nome)}"/></div>
    <div class="fg"><label class="lbl">BI</label><input class="inp" id="rf-bi" value="${esc(f.bi||"")}"/></div>
    <div class="fg"><label class="lbl">Nascimento</label><input class="inp" type="date" id="rf-nasc" value="${f.nasc||""}"/></div>
    <div class="fg"><label class="lbl">Telefone</label><input class="inp" id="rf-tel" value="${esc(f.tel||"")}"/></div>
    <div class="fg"><label class="lbl">Email</label><input class="inp" id="rf-email" value="${esc(f.email||"")}"/></div>
    <div class="fg"><label class="lbl">Cargo</label><input class="inp" id="rf-cargo" value="${esc(f.cargo)}"/></div>
    <div class="fg"><label class="lbl">Departamento</label>
      <select class="inp" id="rf-dep"><option ${f.dep==="Obras"?"selected":""}>Obras</option><option ${f.dep==="Produção"?"selected":""}>Produção</option><option ${f.dep==="Design"?"selected":""}>Design</option><option ${f.dep==="Administrativo"?"selected":""}>Administrativo</option><option ${f.dep==="Vendas"?"selected":""}>Vendas</option><option ${f.dep==="Financeiro"?"selected":""}>Financeiro</option><option ${f.dep==="RH"?"selected":""}>RH</option></select></div>
    <div class="fg"><label class="lbl">Contrato</label>
      <select class="inp" id="rf-cont"><option value="efectivo" ${f.tipo_contrato==="efectivo"?"selected":""}>Efectivo</option><option value="prazo" ${f.tipo_contrato==="prazo"?"selected":""}>A Prazo</option><option value="freelance" ${f.tipo_contrato==="freelance"?"selected":""}>Freelance</option></select></div>
    <div class="fg"><label class="lbl">Admissão</label><input class="inp" type="date" id="rf-adm" value="${f.data_admissao||""}"/></div>
    <div class="fg"><label class="lbl">Salário Base</label><input class="inp" type="number" id="rf-sal" value="${f.salario_base}"/></div>
    <div class="fg"><label class="lbl">INSS %</label><input class="inp" type="number" id="rf-inss" value="${f.inss_pct||3}"/></div>
    <div class="fg"><label class="lbl">IRPS %</label><input class="inp" type="number" id="rf-irps" value="${f.irps_pct||0}"/></div>
    <div class="fg"><label class="lbl">Bónus</label><input class="inp" type="number" id="rf-bonus" value="${f.bonus||0}"/></div>
    <div class="fg"><label class="lbl">Banco</label><input class="inp" id="rf-banco" value="${esc(f.banco||"")}"/></div>
    <div class="fg"><label class="lbl">Nº Conta</label><input class="inp" id="rf-conta" value="${esc(f.conta_banco||"")}"/></div>
    <div class="fg"><label class="lbl">M-Pesa</label><input class="inp" id="rf-mpesa" value="${esc(f.mpesa||"")}"/></div>
    <div class="fg cs2"><label class="lbl">Notas</label><textarea class="inp" id="rf-notas" style="height:50px;resize:vertical;">${esc(f.notas||"")}</textarea></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveFunc(${id})">${ico(ICOS.check,14)} Guardar</button></div>`,"wide");
}

function saveFunc(id){
  const n=v("rf-n");if(!n)return alert("Nome obrigatório!");
  const obj={id:id||Date.now(),nome:n,bi:v("rf-bi"),nasc:v("rf-nasc"),tel:v("rf-tel"),email:v("rf-email"),cargo:v("rf-cargo"),dep:v("rf-dep"),tipo_contrato:v("rf-cont"),data_admissao:v("rf-adm"),
    salario_base:Number(v("rf-sal")),inss_pct:Number(v("rf-inss")||3),irps_pct:Number(v("rf-irps")||0),bonus:Number(v("rf-bonus")||0),comissoes:0,
    banco:v("rf-banco"),conta_banco:v("rf-conta"),mpesa:v("rf-mpesa"),notas:v("rf-notas"),status:"ativo"};
  if(id)DB.rh.funcionarios=DB.rh.funcionarios.map(f=>f.id===id?obj:f);
  else DB.rh.funcionarios.push(obj);
  addLog((id?"Editou":"Adicionou")+" funcionário: "+n);saveDB(DB);closeModal();render("rh-mod");
}
function delFunc(id){if(!confirm("Eliminar?"))return;DB.rh.funcionarios=DB.rh.funcionarios.filter(f=>f.id!==id);saveDB(DB);render("rh-mod");}

function regPresenca(funcId,campo,valor,data){
  let pr=DB.rh.presencas.find(p=>p.funcId===funcId&&p.data===data);
  if(!pr){pr={id:Date.now(),funcId,data,entrada:"",saida:"",tipo:"normal",obs:""};DB.rh.presencas.push(pr);}
  pr[campo]=valor;saveDB(DB);
}

function gerarRecibo(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  const cfg=DB.cfg;
  const bruto=f.salario_base+(f.bonus||0)+(f.comissoes||0);
  const inss=f.salario_base*(f.inss_pct||3)/100;
  const irps=f.salario_base*(f.irps_pct||0)/100;
  const liq=bruto-inss-irps;
  const mesAno=new Date().toLocaleDateString("pt-MZ",{month:"long",year:"numeric"});
  const logoH=cfg.logo?`<img src="${cfg.logo}" style="max-height:50px;object-fit:contain;" alt="Logo"/>`:"";
  openModal(`Recibo Salarial — ${f.nome}`,`
    <div class="pdf-wrap">
      <div class="pdf-hdr">
        <div>${logoH}${logoH?`<br/>`:""}
          <div class="pdf-co">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan)}<br/>${esc(cfg.cidade)}, ${esc(cfg.pais)}<br/>NUIT: ${esc(cfg.nuit||"")}</div>
        </div>
        <div style="text-align:right;">
          <div class="pdf-badge">RECIBO SALARIAL</div>
          <div style="font-size:13px;font-weight:700;margin-top:4px;">${mesAno}</div>
        </div>
      </div>
      <div style="background:#f5f7fa;border-radius:8px;padding:12px 14px;margin-bottom:16px;">
        <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Funcionário</div>
        <div style="font-weight:700;font-size:15px;">${esc(f.nome)}</div>
        <div style="color:#555;font-size:12px;">${esc(f.cargo)} · ${esc(f.dep)} · Admissão: ${f.data_admissao||""}</div>
        ${f.bi?`<div style="color:#555;font-size:12px;">BI: ${esc(f.bi)}</div>`:""}
      </div>
      <table style="width:100%;border-collapse:collapse;margin-bottom:14px;">
        <thead><tr style="background:#1a2d4f;color:#fff;"><th style="padding:8px 12px;text-align:left;">Descrição</th><th style="padding:8px 12px;text-align:right;">Valor (${cfg.moeda})</th></tr></thead>
        <tbody>
          <tr style="border-bottom:1px solid #eee;"><td style="padding:8px 12px;">Salário Base</td><td style="padding:8px 12px;text-align:right;font-weight:700;">${mzn(f.salario_base)}</td></tr>
          ${f.bonus>0?`<tr style="border-bottom:1px solid #eee;background:#f9fff9;"><td style="padding:8px 12px;color:#1eb87a;">Bónus</td><td style="padding:8px 12px;text-align:right;color:#1eb87a;">+${mzn(f.bonus)}</td></tr>`:""}
          ${f.comissoes>0?`<tr style="border-bottom:1px solid #eee;background:#f9fff9;"><td style="padding:8px 12px;color:#1eb87a;">Comissões</td><td style="padding:8px 12px;text-align:right;color:#1eb87a;">+${mzn(f.comissoes)}</td></tr>`:""}
          <tr style="border-bottom:1px solid #eee;"><td style="padding:8px 12px;font-weight:600;">Vencimento Bruto</td><td style="padding:8px 12px;text-align:right;font-weight:700;">${mzn(bruto)}</td></tr>
          <tr style="border-bottom:1px solid #eee;background:#fff5f5;"><td style="padding:8px 12px;color:#c0272d;">(-) INSS (${f.inss_pct||3}%)</td><td style="padding:8px 12px;text-align:right;color:#c0272d;">-${mzn(inss)}</td></tr>
          ${irps>0?`<tr style="border-bottom:1px solid #eee;background:#fff5f5;"><td style="padding:8px 12px;color:#e07830;">(-) IRPS (${f.irps_pct}%)</td><td style="padding:8px 12px;text-align:right;color:#e07830;">-${mzn(irps)}</td></tr>`:""}
        </tbody>
      </table>
      <div style="background:#1a2d4f;color:#fff;border-radius:8px;padding:14px 18px;display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;">
        <span style="font-weight:700;font-size:16px;">SALÁRIO LÍQUIDO</span>
        <span style="color:#d4a820;font-weight:800;font-size:22px;">${mzn(liq)}</span>
      </div>
      ${f.banco||f.mpesa?`<div style="background:#f0f4f8;border-radius:8px;padding:12px 14px;font-size:12px;margin-bottom:14px;">
        <div style="font-weight:700;margin-bottom:6px;color:#1a2d4f;">Dados de Pagamento:</div>
        ${f.banco?`<div>🏦 <b>${esc(f.banco)}</b>: ${esc(f.conta_banco||"")}</div>`:""}
        ${f.mpesa?`<div>📱 <b>M-Pesa/e-Mola</b>: ${esc(f.mpesa)}</div>`:""}
      </div>`:""}
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:30px;margin-top:20px;border-top:2px solid #eee;padding-top:16px;">
        <div style="text-align:center;"><div style="border-top:1px solid #999;padding-top:8px;margin-top:30px;font-size:11px;color:#888;">Assinatura do Funcionário</div></div>
        <div style="text-align:center;"><div style="border-top:1px solid #999;padding-top:8px;margin-top:30px;font-size:11px;color:#888;">Assinatura do Responsável</div></div>
      </div>
      <div style="text-align:center;font-size:10px;color:#aaa;margin-top:12px;">${esc(cfg.empresa)} · ${esc(cfg.email)} · ${esc(cfg.tel)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn btn-p" onclick="printDoc()">🖨️ Imprimir</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"wide");
}

function pagarFunc(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  const bruto=f.salario_base+(f.bonus||0)+(f.comissoes||0);
  const inss=f.salario_base*(f.inss_pct||3)/100;
  const irps=f.salario_base*(f.irps_pct||0)/100;
  const liq=bruto-inss-irps;
  const pgOpts=DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  openModal(`Processar Pagamento — ${f.nome}`,`
    <div style="background:var(--navy);border-radius:8px;padding:12px;margin-bottom:13px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Salário Líquido</span><span style="color:var(--gold);font-weight:700;">${mzn(liq)}</span></div>
      ${f.banco?`<div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">🏦 ${esc(f.banco)}</span><span style="color:var(--blue);">${esc(f.conta_banco||"—")}</span></div>`:""}
      ${f.mpesa?`<div style="display:flex;justify-content:space-between;"><span style="color:var(--muted);">📱 M-Pesa</span><span style="color:var(--green);">${esc(f.mpesa)}</span></div>`:""}
    </div>
    <div class="g2">
      <div class="fg"><label class="lbl">Forma de Pagamento</label>
        <select class="inp" id="pf-tp" onchange="autoFillPgFunc(${id},this.value)">
          ${f.banco?`<option value="banco_func">🏦 ${esc(f.banco)} (conta do funcionário)</option>`:""}
          ${f.mpesa?`<option value="mpesa_func">📱 M-Pesa (${esc(f.mpesa)})</option>`:""}
          ${pgOpts}
        </select>
      </div>
      <div class="fg"><label class="lbl">Valor (${DB.cfg.moeda})</label><input class="inp" type="number" id="pf-val" value="${liq.toFixed(2)}" min="0"/></div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="pf-dt" value="${hoje()}"/></div>
      <div class="fg"><label class="lbl">Referência</label><input class="inp" id="pf-ref" placeholder="Nº transação..."/></div>
      <div class="fg cs2" id="pf-dest-info" style="background:var(--navy);border-radius:8px;padding:10px;font-size:12px;color:var(--muted);">
        Selecione a forma de pagamento acima
      </div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="confirmarPagFunc(${id})">💸 Confirmar Pagamento</button>
    </div>`);
  if(f.banco)setTimeout(()=>autoFillPgFunc(id,"banco_func"),100);
}

function autoFillPgFunc(funcId,tipo){
  const f=DB.rh.funcionarios.find(x=>x.id===funcId);if(!f)return;
  const info=document.getElementById("pf-dest-info");if(!info)return;
  if(tipo==="banco_func"&&f.banco){
    info.innerHTML=`🏦 <b>${esc(f.banco)}</b><br/>Conta: <b>${esc(f.conta_banco||"—")}</b><br/>Titular: ${esc(f.nome)}`;
  } else if(tipo==="mpesa_func"&&f.mpesa){
    info.innerHTML=`📱 <b>M-Pesa/e-Mola</b><br/>Número: <b>${esc(f.mpesa)}</b><br/>Titular: ${esc(f.nome)}`;
  } else {
    const pg=DB.cfg.pagamentos.find(p=>p.nome===tipo);
    if(pg)info.innerHTML=`${pg.tipo==="banco"?"🏦":"📱"} <b>${esc(pg.nome)}</b><br/>${pg.conta||pg.numero||""}<br/>${pg.titular?`Titular: ${esc(pg.titular)}`:""}`;
  }
}

function confirmarPagFunc(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  const val=Number(v("pf-val"));if(!val)return alert("Valor inválido!");
  DB.financeiro.despesas.push({id:Date.now(),desc:`Salário ${f.nome} — ${new Date().toLocaleDateString("pt-MZ",{month:"long",year:"numeric"})}`,
    valor:val,data:v("pf-dt"),cat:"RH",status:"pago",ref:v("pf-ref")});
  addLog(`Pagamento salário: ${f.nome} — ${mzn(val)}`);saveDB(DB);closeModal();
  alert(`✅ Pagamento de ${mzn(val)} registado para ${f.nome}!\nForma: ${v("pf-tp")}\nRef: ${v("pf-ref")||"—"}`);
  render("rh-mod");
}

function pagarTodos(){
  if(!confirm("Processar folha completa para todos os funcionários?"))return;
  const mes=new Date().toLocaleDateString("pt-MZ",{month:"long",year:"numeric"});
  let total=0;
  DB.rh.funcionarios.filter(f=>f.status==="ativo").forEach(f=>{
    const bruto=f.salario_base+(f.bonus||0)+(f.comissoes||0);
    const inss=f.salario_base*(f.inss_pct||3)/100;
    const irps=f.salario_base*(f.irps_pct||0)/100;
    const liq=bruto-inss-irps;
    DB.financeiro.despesas.push({id:Date.now()+f.id,desc:`Salário ${f.nome} — ${mes}`,valor:liq,data:hoje(),cat:"RH",status:"pago",ref:`FOLHA-${mes}`});
    total+=liq;
  });
  addLog(`Folha processada: ${mzn(total)}`);saveDB(DB);
  alert(`✅ Folha processada!\nTotal pago: ${mzn(total)}\nLançado em Despesas → RH`);
  render("rh-mod");
}

function novasFerias(){
  const opts=DB.rh.funcionarios.map(f=>`<option value="${f.id}">${esc(f.nome)}</option>`).join("");
  openModal("Solicitar Férias",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Funcionário</label><select class="inp" id="fv-f">${opts}</select></div>
    <div class="fg"><label class="lbl">Data Início</label><input class="inp" type="date" id="fv-i" value="${hoje()}"/></div>
    <div class="fg"><label class="lbl">Data Fim</label><input class="inp" type="date" id="fv-f2"/></div>
    <div class="fg cs2"><label class="lbl">Observações</label><input class="inp" id="fv-o"/></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveFerias()">Guardar</button></div>`);
}
function saveFerias(){
  const fid=Number(v("fv-f"));const ini=v("fv-i");const fim=v("fv-f2");
  if(!fid||!ini||!fim)return alert("Preencha todos os campos!");
  const f=DB.rh.funcionarios.find(x=>x.id===fid);
  const dias=Math.round((new Date(fim)-new Date(ini))/(1000*60*60*24))+1;
  DB.rh.ferias.push({id:Date.now(),funcId:fid,funcNome:f.nome,inicio:ini,fim:fim,dias,status:"pendente",obs:v("fv-o")});
  addLog(`Férias solicitadas: ${f.nome}`);saveDB(DB);closeModal();render("rh-mod");
}
function aprFerias(id){DB.rh.ferias=DB.rh.ferias.map(f=>f.id===id?{...f,status:"aprovado"}:f);saveDB(DB);render("rh-mod");}
function delFerias(id){if(!confirm("Eliminar?"))return;DB.rh.ferias=DB.rh.ferias.filter(f=>f.id!==id);saveDB(DB);render("rh-mod");}

function novaAval(){
  const opts=DB.rh.funcionarios.map(f=>`<option value="${f.id}">${esc(f.nome)}</option>`).join("");
  openModal("Nova Avaliação",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Funcionário</label><select class="inp" id="av-f">${opts}</select></div>
    <div class="fg"><label class="lbl">Período</label><input class="inp" id="av-p" placeholder="Q1 2026, Jan 2026..."/></div>
    <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="av-d" value="${hoje()}"/></div>
    <div class="fg"><label class="lbl">Nota (1-5)</label><input class="inp" type="number" id="av-n" min="1" max="5" value="3"/></div>
    <div class="fg cs2"><label class="lbl">Comentário</label><textarea class="inp" id="av-c" style="height:60px;resize:vertical;"></textarea></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveAval()">Guardar</button></div>`);
}
function saveAval(){
  const fid=Number(v("av-f"));const f=DB.rh.funcionarios.find(x=>x.id===fid);
  DB.rh.avaliacoes.push({id:Date.now(),funcId:fid,funcNome:f.nome,data:v("av-d"),periodo:v("av-p"),nota:Number(v("av-n")),comentario:v("av-c"),avaliador:CU.nome,status:"concluida"});
  addLog(`Avaliação: ${f.nome}`);saveDB(DB);closeModal();render("rh-mod");
}

function pgMpesa(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  const liq=f.salario_base*(1-(f.inss_pct||3)/100-(f.irps_pct||0)/100)+(f.bonus||0);
  const msg=`Pagamento de salário ${new Date().toLocaleDateString("pt-MZ",{month:"long",year:"numeric"})} — ${mzn(liq)} — ${DB.cfg.empresa}`;
  alert(`📱 M-Pesa / e-Mola\n\nNúmero: ${f.mpesa}\nNome: ${f.nome}\nValor: ${mzn(liq)}\n\nMensagem:\n"${msg}"\n\nEnvie o pagamento através da sua aplicação M-Pesa/e-Mola para o número indicado.`);
}
function pgBanco(id){
  const f=DB.rh.funcionarios.find(x=>x.id===id);if(!f)return;
  const liq=f.salario_base*(1-(f.inss_pct||3)/100-(f.irps_pct||0)/100)+(f.bonus||0);
  alert(`🏦 Transferência Bancária\n\nBanco: ${f.banco}\nConta: ${f.conta_banco||"—"}\nTitular: ${f.nome}\nValor: ${mzn(liq)}\n\nEfectue a transferência através do seu banco para os dados acima.`);
}

// ════════════════════════════════════════════════════════════
// MÓDULO DE PROJETOS INTELIGENTES — MARCENARIA + CONSTRUÇÃO
// ════════════════════════════════════════════════════════════
let _projAba="marcenaria";
function rProjetos(){
  const abas=[["marcenaria","🪵 Marcenaria"],["construcao","🏗️ Construção Civil"],["historico","📋 Histórico"]];
  let tabHtml=abas.map(([id,l])=>`<button class="tab${_projAba===id?" active":""}" onclick="_setPrj('${id}')">${l}</button>`).join("");
  let content="";
  if(_projAba==="marcenaria"){content=_marcenaria();}
  else if(_projAba==="construcao"){content=_construcao();}
  else{content=_historicoPrj();}
  return`<div class="ph"><div class="ph-title">🛠️ Projetos Inteligentes</div><div class="ph-sub">Calcule materiais automaticamente por medidas</div></div>
  <div class="tabs">${tabHtml}</div>${content}`;
}
function _setPrj(a){_projAba=a;render("projetos");}

function _marcenaria(){
  return`<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;">
    <div class="card">
      <h3 class="serif" style="font-size:15px;margin-bottom:14px;">🪵 Calculadora de Marcenaria</h3>
      <div class="fg"><label class="lbl">Tipo de Móvel</label>
        <select class="inp" id="mc-tipo" onchange="mc_changeTipo()">
          <option value="cozinha">Cozinha Completa</option>
          <option value="guarda-fato">Guarda-Fato / Roupeiro</option>
          <option value="comoda">Cómoda / Commode</option>
          <option value="armario">Armário Simples</option>
          <option value="rack">Rack / Painel TV</option>
          <option value="mesa">Mesa / Bancada</option>
          <option value="estante">Estante / Prateleiras</option>
          <option value="cama">Cabeceira / Cama</option>
          <option value="personalizado">Personalizado</option>
        </select>
      </div>
      <div id="mc-desc-area" style="background:var(--navy);border-radius:8px;padding:11px;margin-bottom:13px;font-size:13px;color:var(--silverL);">
        Selecione o tipo de móvel para ver as dimensões necessárias.
      </div>
      <div class="fg"><label class="lbl">Nome do Projeto</label><input class="inp" id="mc-nome" placeholder="Ex: Cozinha Sr. Armando"/></div>
      <div class="g3" style="margin-bottom:10px;">
        <div class="fg"><label class="lbl">Largura (cm)</label><input class="inp" type="number" id="mc-L" placeholder="ex: 300" min="0"/></div>
        <div class="fg"><label class="lbl">Altura (cm)</label><input class="inp" type="number" id="mc-A" placeholder="ex: 220" min="0"/></div>
        <div class="fg"><label class="lbl">Profundidade (cm)</label><input class="inp" type="number" id="mc-P" placeholder="ex: 60" min="0"/></div>
      </div>
      <div class="g2" style="margin-bottom:10px;">
        <div class="fg"><label class="lbl">Material</label>
          <select class="inp" id="mc-mat">
            <option value="MDF 15mm">MDF 15mm</option>
            <option value="MDF 18mm">MDF 18mm</option>
            <option value="MDF 25mm">MDF 25mm</option>
            <option value="Melamina 15mm">Melamina 15mm</option>
            <option value="Melamina 18mm">Melamina 18mm</option>
            <option value="Madeira Pinho">Madeira Pinho</option>
            <option value="Madeira Carvalho">Madeira Carvalho</option>
          </select>
        </div>
        <div class="fg"><label class="lbl">Cor / Acabamento</label>
          <select class="inp" id="mc-cor">
            <option>Branco Brilhante</option><option>Branco Mate</option><option>Carvalho Natural</option>
            <option>Cinza Cimento</option><option>Preto Mate</option><option>Madeira Natural</option><option>Personalizado</option>
          </select>
        </div>
        <div class="fg"><label class="lbl">Nº de Portas</label><input class="inp" type="number" id="mc-portas" value="2" min="0"/></div>
        <div class="fg"><label class="lbl">Nº de Gavetas</label><input class="inp" type="number" id="mc-gavetas" value="0" min="0"/></div>
      </div>
      <div class="fg"><label class="lbl">Preço Chapa 2750×1830mm (${DB.cfg.moeda})</label><input class="inp" type="number" id="mc-pchapa" value="${(DB.produtos.find(p=>p.cat==="Chapas")?.preco)||2800}" min="0"/></div>
      <div class="fg"><label class="lbl">Custo Mão de Obra (${DB.cfg.moeda})</label><input class="inp" type="number" id="mc-mo" value="15000" min="0"/></div>
      <div class="fg"><label class="lbl">Transporte (${DB.cfg.moeda})</label><input class="inp" type="number" id="mc-transp" value="2000" min="0"/></div>
      <button class="btn btn-p" style="width:100%;justify-content:center;margin-top:4px;" onclick="mc_calcular()">⚙️ Calcular Materiais & Custo</button>
    </div>
    <div id="mc-resultado" style="display:flex;align-items:center;justify-content:center;">
      <div style="text-align:center;color:var(--muted);">
        <div style="font-size:40px;margin-bottom:10px;">🪵</div>
        <div>Insira as medidas e clique em Calcular</div>
      </div>
    </div>
  </div>`;
}

function mc_changeTipo(){
  const t=v("mc-tipo");
  const descs={
    "cozinha":"Informe: Largura total da parede (cm) · Altura até o teto (cm) · Profundidade dos armários inferiores (60cm padrão) · Nº de portas e gavetas",
    "guarda-fato":"Informe: Largura total (cm) · Altura total (cm) · Profundidade (60cm padrão) · Nº de portas",
    "comoda":"Informe: Largura (cm) · Altura (cm) · Profundidade (cm) · Nº de gavetas",
    "armario":"Informe: Largura (cm) · Altura (cm) · Profundidade (cm) · Nº de portas e prateleiras",
    "rack":"Informe: Largura (cm) · Altura (cm) · Profundidade (cm) · Nº de compartimentos",
    "mesa":"Informe: Comprimento (cm) · Largura (cm) · Altura (cm) · Tipo de tampo",
    "estante":"Informe: Largura (cm) · Altura (cm) · Profundidade (cm) · Nº de prateleiras",
    "cama":"Informe: Tamanho (solteiro/casal/queen/king) · Largura (cm) · Altura da cabeceira (cm)",
    "personalizado":"Insira as medidas conforme o seu projeto personalizado.",
  };
  const desc=document.getElementById("mc-desc-area");
  if(desc)desc.innerHTML=descs[t]||"Insira as medidas do seu projeto.";
}

function mc_calcular(){
  const tipo=v("mc-tipo");const nome=v("mc-nome")||tipo;
  const L=Number(v("mc-L"));const A=Number(v("mc-A"));const P=Number(v("mc-P"));
  if(!L||!A)return alert("Insira largura e altura!");
  const mat=v("mc-mat");const cor=v("mc-cor");
  const nPortas=Number(v("mc-portas")||0);const nGav=Number(v("mc-gavetas")||0);
  const pChapa=Number(v("mc-pchapa")||2800);const mo=Number(v("mc-mo")||0);const transp=Number(v("mc-transp")||0);

  // Área de chapa 2750x1830 = 5.0325 m²
  const areaChapa=2.75*1.83;
  let pecas=[];let totalArea=0;

  if(tipo==="cozinha"){
    const profInf=P||60;const profSup=35;const altInf=90;const altSup=A-altInf-10;
    pecas=[
      {desc:"Tampo bancada",q:1,l:L,a:profInf,obs:"com aba frontal"},
      {desc:"Lateral inferior esq.",q:1,l:profInf,a:altInf},
      {desc:"Lateral inferior dir.",q:1,l:profInf,a:altInf},
      {desc:"Divisórias inferiores",q:Math.ceil(L/80)-1,l:profInf,a:altInf-4},
      {desc:"Fundo inferior",q:1,l:L,a:altInf,obs:"6mm ou 8mm"},
      {desc:"Prateleira inferior",q:Math.ceil(L/80),l:Math.min(L/Math.ceil(L/80)-3,77),a:profInf-4},
      {desc:"Lateral superior esq.",q:1,l:profSup,a:altSup},
      {desc:"Lateral superior dir.",q:1,l:profSup,a:altSup},
      {desc:"Divisórias superiores",q:Math.ceil(L/60)-1,l:profSup,a:altSup-4},
      {desc:"Prateleira superior",q:Math.ceil(L/60)*2,l:Math.min(L/Math.ceil(L/60)-3,57),a:profSup-4},
      {desc:"Portas superiores",q:nPortas||Math.ceil(L/60)*2,l:L/Math.ceil(nPortas||2)-(nPortas?2:2),a:altSup-4},
      {desc:"Portas inferiores",q:nPortas||Math.ceil(L/80)*2,l:L/Math.ceil(nPortas||2)-(nPortas?2:2),a:altInf-50-(nGav>0?nGav*18:0)},
    ];
    if(nGav>0){for(let g=0;g<nGav;g++)pecas.push({desc:`Frente gaveta ${g+1}`,q:1,l:L/3-3,a:18});}
  } else if(tipo==="guarda-fato"){
    const profF=P||60;
    pecas=[
      {desc:"Lateral esquerda",q:1,l:profF,a:A},
      {desc:"Lateral direita",q:1,l:profF,a:A},
      {desc:"Topo",q:1,l:L-36,a:profF},
      {desc:"Base",q:1,l:L-36,a:profF},
      {desc:"Divisória central",q:Math.ceil(L/120)-1,l:profF,a:A-36},
      {desc:"Prateleiras",q:Math.ceil(L/60)*2,l:Math.min(L/Math.ceil(L/60)-3,117),a:profF-4},
      {desc:"Fundo",q:1,l:L,a:A,obs:"6mm"},
      {desc:`Portas (${nPortas||Math.ceil(L/60)*2}un)`,q:nPortas||Math.ceil(L/60)*2,l:L/(nPortas||Math.ceil(L/60)*2)-3,a:A-4},
    ];
    if(nGav>0){for(let g=0;g<nGav;g++)pecas.push({desc:`Gaveta ${g+1}`,q:1,l:L/2-36,a:18});}
  } else if(tipo==="comoda"){
    const profC=P||50;
    pecas=[
      {desc:"Lateral esquerda",q:1,l:profC,a:A},
      {desc:"Lateral direita",q:1,l:profC,a:A},
      {desc:"Topo",q:1,l:L-36,a:profC},
      {desc:"Base",q:1,l:L-36,a:profC},
      {desc:"Fundo",q:1,l:L,a:A,obs:"6mm"},
      {desc:`Frontes gavetas (${nGav||4}un)`,q:nGav||4,l:L-6,a:(A-20)/(nGav||4)-4},
      {desc:`Fundos gavetas`,q:nGav||4,l:L-40,a:profC-120},
      {desc:`Laterais gavetas (2 por gav.)`,q:(nGav||4)*2,l:profC-120,a:(A-20)/(nGav||4)-4},
    ];
  } else {
    // Genérico
    const prof=P||40;
    pecas=[
      {desc:"Lateral esquerda",q:1,l:prof,a:A},
      {desc:"Lateral direita",q:1,l:prof,a:A},
      {desc:"Topo",q:1,l:L-36,a:prof},
      {desc:"Base",q:1,l:L-36,a:prof},
      {desc:"Fundo",q:1,l:L,a:A,obs:"6mm"},
      {desc:"Prateleiras",q:3,l:L-36,a:prof-4},
      {desc:"Portas",q:nPortas||2,l:(L-6)/(nPortas||2),a:A-4},
    ];
  }

  // Calcular área total
  pecas.forEach(p=>{const a=(p.l/100)*(p.a/100)*p.q;totalArea+=a;});
  const nChapas=Math.ceil(totalArea/areaChapa*1.15); // 15% desperdício
  const custoChapas=nChapas*pChapa;

  // Fita de borda: perímetro exposto × quantidade
  const fitaM=pecas.reduce((s,p)=>s+(2*(p.l+p.a)/100)*p.q,0)*1.1;
  const custoFita=fitaM*80; // 80 MZN/metro estimado

  // Ferragens
  const nDob=nPortas?nPortas*2:4;const cDob=nDob*85;
  const nPux=nPortas||4;const cPux=nPux*180;
  const nCorr=nGav;const cCorr=nCorr*280;
  const custoFerr=cDob+cPux+cCorr;

  const subtotal=custoChapas+custoFita+custoFerr+mo+transp;
  const iva=subtotal*(DB.cfg.iva/100);
  const total=subtotal+iva;

  let pecasHTML=pecas.map((p,i)=>`<tr>
    <td style="font-size:12px;">${i+1}</td>
    <td style="font-size:12px;font-weight:600;">${esc(p.desc)}</td>
    <td style="font-size:12px;text-align:center;">${p.q}</td>
    <td style="font-size:12px;text-align:right;">${p.l}×${p.a}mm</td>
    <td style="font-size:12px;text-align:right;">${((p.l/100)*(p.a/100)*p.q).toFixed(3)}m²</td>
    ${p.obs?`<td style="font-size:11px;color:var(--muted);">${p.obs}</td>`:"<td></td>"}
  </tr>`).join("");

  document.getElementById("mc-resultado").innerHTML=`<div style="width:100%;">
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:12px;">
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Chapas ${mat}</div><div class="kpi-v" style="color:var(--red);font-size:18px;">${nChapas}</div><div class="kpi-s">${totalArea.toFixed(2)}m² + 15%</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Fita de Bordo</div><div class="kpi-v" style="color:var(--blue);font-size:18px;">${fitaM.toFixed(1)}m</div></div>
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Custo Total</div><div class="kpi-v" style="color:var(--gold);font-size:15px;">${mzn(total)}</div></div>
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Material</div><div class="kpi-v" style="color:var(--green);font-size:13px;">${esc(mat)}<br/><small>${esc(cor)}</small></div></div>
    </div>
    <div class="card" style="margin-bottom:10px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:8px;"><span class="serif" style="font-size:14px;">Lista de Corte — ${esc(nome)}</span><span style="color:var(--muted);font-size:12px;">${pecas.length} peças</span></div>
      <div style="max-height:240px;overflow-y:auto;">
        <table class="tbl"><thead><tr><th>#</th><th>Peça</th><th>Qtd</th><th>Dimensões</th><th>Área</th><th>Obs.</th></tr></thead><tbody>${pecasHTML}</tbody></table>
      </div>
    </div>
    <div class="card" style="margin-bottom:10px;">
      <div class="serif" style="font-size:14px;margin-bottom:10px;">Resumo de Custos</div>
      <table class="tbl">
        <tbody>
          <tr><td>${nChapas} chapas ${mat}</td><td style="text-align:right;font-weight:700;">${mzn(custoChapas)}</td></tr>
          <tr><td>Fita de bordo (${fitaM.toFixed(1)}m)</td><td style="text-align:right;">${mzn(custoFita)}</td></tr>
          <tr><td>Ferragens (dobradiças, puxadores, corrediças)</td><td style="text-align:right;">${mzn(custoFerr)}</td></tr>
          <tr><td>Mão de obra</td><td style="text-align:right;">${mzn(mo)}</td></tr>
          <tr><td>Transporte</td><td style="text-align:right;">${mzn(transp)}</td></tr>
          <tr style="border-top:2px solid var(--border);"><td style="font-weight:700;">Subtotal</td><td style="text-align:right;font-weight:700;">${mzn(subtotal)}</td></tr>
          <tr><td>IVA (${DB.cfg.iva}%)</td><td style="text-align:right;">${mzn(iva)}</td></tr>
          <tr style="background:rgba(212,168,32,.1);"><td style="font-weight:800;font-size:15px;color:var(--gold);">TOTAL</td><td style="text-align:right;font-weight:800;font-size:17px;color:var(--gold);">${mzn(total)}</td></tr>
        </tbody>
      </table>
    </div>
    <div style="display:flex;gap:8px;">
      <button class="btn btn-p" onclick="mc_gerarCot('${esc(nome)}',${subtotal},${iva},${total})">📄 Gerar Cotação</button>
      <button class="btn btn-g" onclick="mc_gerarVenda('${esc(nome)}',${subtotal},${iva},${total})">💰 Gerar Venda</button>
    </div>
  </div>`;
}

function mc_gerarCot(nome,sub,ivaV,tot){
  const cliOpts=DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  openModal("Gerar Cotação do Projeto",`
    <div class="fg"><label class="lbl">Cliente</label><select class="inp" id="gq-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
    <div class="fg"><label class="lbl">Validade</label><input class="inp" type="date" id="gq-val"/></div>
    <div class="fg"><label class="lbl">Notas</label><textarea class="inp" id="gq-obs" style="height:60px;resize:vertical;" placeholder="Prazo de entrega, condições..."></textarea></div>
    <div style="background:var(--navy);border-radius:8px;padding:11px;margin-top:10px;font-size:13px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">Subtotal</span><span>${mzn(sub)}</span></div>
      <div style="display:flex;justify-content:space-between;margin-bottom:4px;"><span style="color:var(--muted);">IVA (${DB.cfg.iva}%)</span><span>${mzn(ivaV)}</span></div>
      <div style="display:flex;justify-content:space-between;font-weight:800;color:var(--gold);"><span>TOTAL</span><span>${mzn(tot)}</span></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="mc_saveCot('${nome}',${sub},${ivaV},${tot})">📄 Criar Cotação</button>
    </div>`);
}
function mc_saveCot(nome,sub,ivaV,tot){
  const cliId=Number(v("gq-cli"));if(!cliId)return alert("Selecione um cliente!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  const num=pad(DB.cotSeq);
  DB.cotacoes.push({id:Date.now(),num,cliId,cliNome:cli.nome,data:hoje(),val:v("gq-val"),
    itens:[{desc:`Projecto de Marcenaria — ${nome}`,qty:1,un:"un",preco:sub,desc_obs:"Inclui materiais, mão de obra e transporte"}],
    subtotal:sub,ivaPct:DB.cfg.iva,iva:ivaV,desconto:0,total:tot,status:"pendente",notas:v("gq-obs"),moeda:DB.cfg.moeda});
  DB.cotSeq++;addLog(`Cotação gerada de projecto: ${nome}`);saveDB(DB);closeModal();
  alert(`✅ Cotação ${num} criada com sucesso!`);goTo("cotacoes");
}
function mc_gerarVenda(nome,sub,ivaV,tot){
  const cliOpts=DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  openModal("Gerar Venda do Projeto",`
    <div class="fg"><label class="lbl">Cliente</label><select class="inp" id="gv-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
    <div class="fg"><label class="lbl">Valor Pago Agora</label><input class="inp" type="number" id="gv-pg" value="0" min="0"/></div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="mc_saveVenda('${nome}',${sub},${ivaV},${tot})">💰 Criar Venda</button>
    </div>`);
}
function mc_saveVenda(nome,sub,ivaV,tot){
  const cliId=Number(v("gv-cli"));if(!cliId)return alert("Selecione um cliente!");
  const cli=DB.clientes.find(c=>c.id===cliId);
  const pago=Math.min(Number(v("gv-pg")||0),tot);
  const num=pad(DB.vendSeq,"VND");const fn=pad(DB.fatSeq,"FAT");
  DB.vendas.push({id:Date.now(),cliId,cliNome:cli.nome,cotId:null,num,fatNum:fn,data:hoje(),
    itens:[{desc:`Projecto de Marcenaria — ${nome}`,qty:1,un:"un",preco:sub}],
    subtotal:sub,desconto:0,ivaPct:DB.cfg.iva,iva:ivaV,total:tot,pago,
    status:pago>=tot?"pago":pago>0?"parcial":"pendente",pagamentos:[],notas:"",moeda:DB.cfg.moeda});
  DB.vendSeq++;DB.fatSeq++;addLog(`Venda gerada de projecto: ${nome}`);saveDB(DB);closeModal();
  alert(`✅ Venda ${fn} criada!`);goTo("vendas");
}

function _construcao(){
  return`<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;">
    <div class="card">
      <h3 class="serif" style="font-size:15px;margin-bottom:14px;">🏗️ Calculadora de Construção Civil</h3>
      <div class="fg"><label class="lbl">Tipo de Cálculo</label>
        <select class="inp" id="cc-tipo">
          <option value="parede">Parede (Blocos de Cimento)</option>
          <option value="piso">Piso / Pavimento (Cerâmica)</option>
          <option value="reboco">Reboco / Estuque</option>
          <option value="pintura">Pintura</option>
          <option value="casa">Casa Completa (Estimativa)</option>
          <option value="laje">Laje / Cobertura</option>
        </select>
      </div>
      <div class="fg"><label class="lbl">Nome do Projeto</label><input class="inp" id="cc-nome" placeholder="Ex: Parede sala principal"/></div>
      <div class="g2" style="margin-bottom:10px;">
        <div class="fg"><label class="lbl">Comprimento / Largura (m)</label><input class="inp" type="number" id="cc-C" placeholder="ex: 5.5" step="0.1" min="0"/></div>
        <div class="fg"><label class="lbl">Altura / Profundidade (m)</label><input class="inp" type="number" id="cc-A" placeholder="ex: 2.8" step="0.1" min="0"/></div>
      </div>
      <div class="g2" style="margin-bottom:10px;">
        <div class="fg"><label class="lbl">Nº de Aberturas (portas/janelas)</label><input class="inp" type="number" id="cc-aber" value="0" min="0"/></div>
        <div class="fg"><label class="lbl">Preço Bloco / Cerâmica (${DB.cfg.moeda})</label><input class="inp" type="number" id="cc-pmat" value="35" min="0"/></div>
      </div>
      <div class="g2" style="margin-bottom:10px;">
        <div class="fg"><label class="lbl">Preço Saco Cimento (${DB.cfg.moeda})</label><input class="inp" type="number" id="cc-pcim" value="${(DB.produtos.find(p=>p.cat==="Construção")?.preco)||650}" min="0"/></div>
        <div class="fg"><label class="lbl">Custo Mão de Obra (${DB.cfg.moeda})</label><input class="inp" type="number" id="cc-mo" value="20000" min="0"/></div>
      </div>
      <button class="btn btn-p" style="width:100%;justify-content:center;" onclick="cc_calcular()">🧮 Calcular Materiais</button>
    </div>
    <div id="cc-resultado" style="display:flex;align-items:center;justify-content:center;">
      <div style="text-align:center;color:var(--muted);">
        <div style="font-size:40px;margin-bottom:10px;">🏗️</div>
        <div>Insira as medidas e clique em Calcular</div>
      </div>
    </div>
  </div>`;
}

function cc_calcular(){
  const tipo=v("cc-tipo");const nome=v("cc-nome")||tipo;
  const C=Number(v("cc-C"));const A=Number(v("cc-A"));
  if(!C||!A)return alert("Insira comprimento e altura/profundidade!");
  const aber=Number(v("cc-aber")||0);const pMat=Number(v("cc-pmat")||35);
  const pCim=Number(v("cc-pcim")||650);const mo=Number(v("cc-mo")||0);
  const area=C*A-(aber*1.8*0.9); // área útil (descontando aberturas médias)
  let materiais=[];let subtotal=0;

  if(tipo==="parede"){
    const blocos=Math.ceil(area/0.04*1.05); // bloco 20x40cm, 5% perda
    const sacosCim=Math.ceil(area*0.3); // ~1 saco por 3.3m² de parede
    const m3Areia=sacosCim*0.15;
    const m3Brita=sacosCim*0.1;
    materiais=[
      {desc:`Blocos de cimento 20×40cm`,qty:blocos,un:"un",preco:pMat},
      {desc:`Sacos de cimento 50kg`,qty:sacosCim,un:"saco",preco:pCim},
      {desc:`Areia (m³)`,qty:Math.ceil(m3Areia),un:"m³",preco:1800},
      {desc:`Mão de obra (pedreiro + servente)`,qty:1,un:"un",preco:mo},
    ];
  } else if(tipo==="piso"){
    const ceramicas=Math.ceil(area*1.1); // 10% quebra
    const sacosCim=Math.ceil(area*0.2);
    const cola=Math.ceil(area/5); // ~1 saco cola por 5m²
    materiais=[
      {desc:`Cerâmica/Porcelânico (m²)`,qty:Math.ceil(area*1.1),un:"m²",preco:pMat},
      {desc:`Sacos cimento cola`,qty:cola,un:"saco",preco:280},
      {desc:`Rejunte`,qty:Math.ceil(area/10),un:"un",preco:120},
      {desc:`Mão de obra (ladrilhador)`,qty:1,un:"un",preco:mo},
    ];
  } else if(tipo==="pintura"){
    const litros=Math.ceil(area/6); // ~1L por 6m²
    const primarios=Math.ceil(area/10);
    materiais=[
      {desc:`Tinta (litros)`,qty:litros*2,un:"L",preco:pMat*2},
      {desc:`Primário / Selador`,qty:primarios,un:"L",preco:pMat*1.2},
      {desc:`Material aplicação (rolos, pincéis, fita)`,qty:1,un:"kit",preco:500},
      {desc:`Mão de obra (pintor)`,qty:1,un:"un",preco:mo},
    ];
  } else if(tipo==="reboco"){
    const sacosCim=Math.ceil(area*0.4);
    const areia=sacosCim*0.2;
    materiais=[
      {desc:`Sacos cimento`,qty:sacosCim,un:"saco",preco:pCim},
      {desc:`Areia (m³)`,qty:Math.ceil(areia),un:"m³",preco:1800},
      {desc:`Mão de obra`,qty:1,un:"un",preco:mo},
    ];
  } else if(tipo==="laje"){
    const m3Beton=area*0.12; // espessura ~12cm
    const ferroBetao=area*12; // kg/m²
    materiais=[
      {desc:`Betão (m³)`,qty:Math.ceil(m3Beton),un:"m³",preco:12000},
      {desc:`Ferro betão (kg)`,qty:Math.ceil(ferroBetao),un:"kg",preco:85},
      {desc:`Cofragem (m²)`,qty:Math.ceil(area),un:"m²",preco:200},
      {desc:`Mão de obra especializada`,qty:1,un:"un",preco:mo},
    ];
  } else {
    // Casa completa estimativa
    const perim=C*2+A*2;
    materiais=[
      {desc:`Blocos de cimento (estimativa)`,qty:Math.ceil(perim*2.8/0.04*1.1),un:"un",preco:pMat},
      {desc:`Cimento (estimativa)`,qty:Math.ceil(area*0.5),un:"saco",preco:pCim},
      {desc:`Areia (m³)`,qty:Math.ceil(area*0.1),un:"m³",preco:1800},
      {desc:`Brita (m³)`,qty:Math.ceil(area*0.05),un:"m³",preco:2200},
      {desc:`Ferro betão (kg)`,qty:Math.ceil(area*8),un:"kg",preco:85},
      {desc:`Mão de obra + Empreitada`,qty:1,un:"un",preco:mo},
    ];
  }

  materiais.forEach(m=>{subtotal+=m.qty*m.preco;});
  const iva=subtotal*(DB.cfg.iva/100);const tot=subtotal+iva;

  let matHTML=materiais.map((m,i)=>`<tr>
    <td style="font-size:12px;">${i+1}</td>
    <td style="font-size:12px;font-weight:600;">${esc(m.desc)}</td>
    <td style="font-size:12px;text-align:center;">${m.qty} ${m.un}</td>
    <td style="font-size:12px;text-align:right;">${mzn(m.preco)}</td>
    <td style="font-size:12px;text-align:right;font-weight:700;">${mzn(m.qty*m.preco)}</td>
  </tr>`).join("");

  document.getElementById("cc-resultado").innerHTML=`<div style="width:100%;">
    <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:12px;">
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Área Total</div><div class="kpi-v" style="color:var(--red);font-size:18px;">${area.toFixed(2)}m²</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Materiais</div><div class="kpi-v" style="color:var(--blue);font-size:18px;">${materiais.length}</div></div>
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Custo Total</div><div class="kpi-v" style="color:var(--gold);font-size:15px;">${mzn(tot)}</div></div>
    </div>
    <div class="card" style="margin-bottom:10px;">
      <div class="serif" style="font-size:14px;margin-bottom:10px;">Lista de Materiais — ${esc(nome)}</div>
      <table class="tbl"><thead><tr><th>#</th><th>Material</th><th>Quantidade</th><th>Preço Unit.</th><th>Total</th></tr></thead>
      <tbody>${matHTML}</tbody>
      <tfoot><tr style="background:rgba(212,168,32,.1);border-top:2px solid var(--border);">
        <td colspan="4" style="padding:9px 12px;font-weight:800;color:var(--gold);">TOTAL c/ IVA (${DB.cfg.iva}%)</td>
        <td style="padding:9px 12px;font-weight:800;color:var(--gold);font-size:16px;">${mzn(tot)}</td>
      </tr></tfoot></table>
    </div>
    <div style="display:flex;gap:8px;">
      <button class="btn btn-p" onclick="cc_gerarCot('${esc(nome)}',${subtotal},${iva},${tot})">📄 Gerar Cotação</button>
      <button class="btn btn-g" onclick="mc_gerarVenda('${esc(nome)}',${subtotal},${iva},${tot})">💰 Gerar Venda</button>
    </div>
  </div>`;
}
function cc_gerarCot(nome,sub,ivaV,tot){mc_gerarCot(nome,sub,ivaV,tot);}

function _historicoPrj(){
  const cots=DB.cotacoes.filter(c=>c.itens[0]?.desc?.includes("Projecto"));
  const vs=DB.vendas.filter(v=>v.itens[0]?.desc?.includes("Projecto"));
  return`<div class="card">
    <div class="serif" style="font-size:15px;margin-bottom:14px;">Cotações e Vendas de Projetos</div>
    ${cots.length===0&&vs.length===0?'<div style="color:var(--muted);text-align:center;padding:20px;">Sem projetos gerados ainda.</div>':""}
    ${cots.map(c=>`<div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--border);">
      <div><div style="font-weight:600;">${esc(c.itens[0]?.desc||"")}</div><div style="color:var(--muted);font-size:12px;">${c.num} · ${c.cliNome}</div></div>
      <div style="text-align:right;"><div style="color:var(--gold);font-weight:700;">${mzn(c.total)}</div>${bdg(c.status)}</div>
    </div>`).join("")}
    ${vs.map(vv=>`<div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--border);">
      <div><div style="font-weight:600;">${esc(vv.itens[0]?.desc||"")}</div><div style="color:var(--muted);font-size:12px;">${vv.fatNum||vv.num} · ${vv.cliNome}</div></div>
      <div style="text-align:right;"><div style="color:var(--blue);font-weight:700;">${mzn(vv.total)}</div>${bdg(vv.status)}</div>
    </div>`).join("")}
  </div>`;
}

// ════════════════════════════════════════════════════════════
// RELATÓRIOS
// ════════════════════════════════════════════════════════════
let _relAba="geral";
function rRelatorios(){
  const abas=[["geral","📊 Geral"],["vendas","💰 Vendas"],["estoque","📦 Estoque"],["financeiro","💳 Financeiro"],["rh","👥 RH"],["backup","💾 Backup"]];
  let tabHtml=abas.map(([id,l])=>`<button class="tab${_relAba===id?" active":""}" onclick="_setRel('${id}')">${l}</button>`).join("");
  let content="";
  if(_relAba==="geral"){
    const tV=DB.vendas.reduce((s,v)=>s+v.total,0);
    const tR=DB.financeiro.receitas.reduce((s,r)=>s+r.valor,0);
    const tD=DB.financeiro.despesas.reduce((s,d)=>s+d.valor,0);
    const cA=DB.cotacoes.filter(c=>c.status==="aprovado").length;
    const taxa=DB.cotacoes.length>0?Math.round((cA/DB.cotacoes.length)*100):0;
    const lucro=tR-tD;
    // Top produtos
    const prodMap={};
    DB.vendas.forEach(vv=>vv.itens.forEach(it=>{if(it.desc)prodMap[it.desc]=(prodMap[it.desc]||0)+it.qty*it.preco;}));
    const topProd=Object.entries(prodMap).sort((a,b)=>b[1]-a[1]).slice(0,5);
    content=`<div class="g4" style="margin-bottom:16px;">
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Faturamento Total</div><div class="kpi-v" style="color:var(--red);">${mzn(tV)}</div></div>
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Receitas</div><div class="kpi-v" style="color:var(--green);">${mzn(tR)}</div></div>
      <div class="kpi" style="border-left-color:${lucro>=0?"var(--gold)":"var(--red)"};"><div class="kpi-l">Lucro Líquido</div><div class="kpi-v" style="color:${lucro>=0?"var(--gold)":"var(--red)"};">${mzn(lucro)}</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Taxa Conversão</div><div class="kpi-v" style="color:var(--blue);">${taxa}%</div></div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;">
      <div class="card"><div class="serif" style="font-size:14px;margin-bottom:12px;">🏆 Top 5 Produtos/Serviços</div>
        ${topProd.length?topProd.map(([desc,val],i)=>`<div style="display:flex;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border);">
          <span style="color:var(--text);font-size:13px;">${i+1}. ${esc(desc.substring(0,30))}</span>
          <span style="color:var(--gold);font-weight:700;">${mzn(val)}</span>
        </div>`).join(""):'<div style="color:var(--muted);font-size:13px;text-align:center;padding:20px;">Sem dados de vendas.</div>'}
      </div>
      <div class="card"><div class="serif" style="font-size:14px;margin-bottom:12px;">📈 Resumo Executivo</div>
        ${[["Clientes",DB.clientes.length,"var(--blue)"],["Cotações",DB.cotacoes.length,"var(--silver)"],["Vendas",DB.vendas.length,"var(--green)"],
           ["Produtos",DB.produtos.length,"var(--orange)"],["Funcionários",DB.rh.funcionarios.length,"var(--red)"],["Obras",DB.obras.length,"var(--blue)"]].map(([l,v2,c])=>`
          <div style="display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px solid var(--border);">
            <span style="color:var(--muted);font-size:13px;">${l}</span>
            <span style="color:${c};font-weight:700;font-size:15px;">${v2}</span>
          </div>`).join("")}
      </div>
    </div>`;
  } else if(_relAba==="vendas"){
    const meses={};
    DB.vendas.forEach(vv=>{const m=vv.data?.substring(0,7)||"—";meses[m]=(meses[m]||0)+vv.total;});
    let rows=DB.vendas.map(vv=>`<tr>
      <td style="font-family:monospace;font-size:11px;">${esc(vv.fatNum||vv.num)}</td>
      <td style="font-weight:600;">${esc(vv.cliNome)}</td>
      <td style="color:var(--muted);font-size:11px;">${vv.data}</td>
      <td style="color:var(--gold);font-weight:700;">${mzn(vv.total)}</td>
      <td style="color:var(--green);">${mzn(vv.pago||0)}</td>
      <td>${bdg(vv.status)}</td>
    </tr>`).reverse().join("");
    content=`<div style="display:grid;grid-template-columns:repeat(3,1fr);gap:11px;margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Total Faturado</div><div class="kpi-v" style="color:var(--gold);">${mzn(DB.vendas.reduce((s,v)=>s+v.total,0))}</div></div>
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Total Recebido</div><div class="kpi-v" style="color:var(--green);">${mzn(DB.vendas.reduce((s,v)=>s+(v.pago||0),0))}</div></div>
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">A Receber</div><div class="kpi-v" style="color:var(--red);">${mzn(DB.vendas.reduce((s,v)=>s+v.total-(v.pago||0),0))}</div></div>
    </div>
    <div class="card" style="margin-bottom:12px;"><div class="serif" style="font-size:14px;margin-bottom:10px;">Vendas por Mês</div>
      ${Object.entries(meses).sort().map(([m,val])=>`<div style="display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px solid var(--border);">
        <span style="color:var(--silverL);">${m}</span><span style="color:var(--gold);font-weight:700;">${mzn(val)}</span></div>`).join("")}
    </div>
    <div class="card" style="display:flex;justify-content:flex-end;margin-bottom:10px;padding:12px;">
      <button class="btn btn-p btn-sm" onclick="exportarCSV('vendas')">📥 Exportar CSV</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Fatura</th><th>Cliente</th><th>Data</th><th>Total</th><th>Pago</th><th>Status</th></tr></thead><tbody>${rows}</tbody></table></div>`;
  } else if(_relAba==="estoque"){
    const totalVal=DB.produtos.reduce((s,p)=>s+p.estoque*p.custo,0);
    const crit=DB.produtos.filter(p=>p.estoque<=p.min);
    let rows=DB.produtos.map(p=>{
      const baixo=p.estoque<=p.min;
      return`<tr style="${baixo?"background:rgba(192,39,45,.05);":""}">
        <td style="font-weight:600;">${esc(p.nome)}</td>
        <td>${esc(p.cat)}</td>
        <td style="color:${baixo?"var(--red)":"var(--green)"};font-weight:700;">${p.estoque} ${p.un}</td>
        <td>${p.min}</td>
        <td>${mzn(p.preco)}</td>
        <td>${mzn(p.custo)}</td>
        <td style="color:var(--gold);font-weight:700;">${mzn(p.estoque*p.custo)}</td>
        <td>${baixo?bdgC("CRÍTICO","var(--red)"):bdgC("OK","var(--green)")}</td>
      </tr>`;
    }).join("");
    content=`<div class="g3" style="margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Valor em Estoque</div><div class="kpi-v" style="color:var(--gold);">${mzn(totalVal)}</div></div>
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Produtos Críticos</div><div class="kpi-v" style="color:var(--red);">${crit.length}</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Total Produtos</div><div class="kpi-v" style="color:var(--blue);">${DB.produtos.length}</div></div>
    </div>
    <div class="card" style="display:flex;justify-content:flex-end;margin-bottom:10px;padding:12px;">
      <button class="btn btn-p btn-sm" onclick="exportarCSV('estoque')">📥 Exportar CSV</button>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Produto</th><th>Categ.</th><th>Estoque</th><th>Mín.</th><th>Preço Venda</th><th>Custo</th><th>Valor Total</th><th>Estado</th></tr></thead><tbody>${rows}</tbody></table></div>`;
  } else if(_relAba==="financeiro"){
    const tR=DB.financeiro.receitas.reduce((s,r)=>s+r.valor,0);
    const tD=DB.financeiro.despesas.reduce((s,d)=>s+d.valor,0);
    // Por categoria
    const catR={};DB.financeiro.receitas.forEach(r=>catR[r.cat]=(catR[r.cat]||0)+r.valor);
    const catD={};DB.financeiro.despesas.forEach(d=>catD[d.cat]=(catD[d.cat]||0)+d.valor);
    content=`<div class="g3" style="margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Total Receitas</div><div class="kpi-v" style="color:var(--green);">${mzn(tR)}</div></div>
      <div class="kpi" style="border-left-color:var(--red);"><div class="kpi-l">Total Despesas</div><div class="kpi-v" style="color:var(--red);">${mzn(tD)}</div></div>
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Saldo</div><div class="kpi-v" style="color:${tR-tD>=0?"var(--gold)":"var(--red)"};">${mzn(tR-tD)}</div></div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;">
      <div class="card"><div class="serif" style="font-size:14px;margin-bottom:10px;color:var(--green);">Receitas por Categoria</div>
        ${Object.entries(catR).map(([c,v2])=>`<div style="display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px solid var(--border);"><span style="color:var(--silverL);">${c}</span><span style="color:var(--green);font-weight:700;">${mzn(v2)}</span></div>`).join("")||'<div style="color:var(--muted);">Sem receitas.</div>'}
      </div>
      <div class="card"><div class="serif" style="font-size:14px;margin-bottom:10px;color:var(--red);">Despesas por Categoria</div>
        ${Object.entries(catD).map(([c,v2])=>`<div style="display:flex;justify-content:space-between;padding:7px 0;border-bottom:1px solid var(--border);"><span style="color:var(--silverL);">${c}</span><span style="color:var(--red);font-weight:700;">${mzn(v2)}</span></div>`).join("")||'<div style="color:var(--muted);">Sem despesas.</div>'}
      </div>
    </div>`;
  } else if(_relAba==="rh"){
    const folha=DB.rh.funcionarios.reduce((s,f)=>s+f.salario_base,0);
    const presHoje=DB.rh.presencas.filter(p=>p.data===hoje());
    let rows=DB.rh.funcionarios.map(f=>{
      const pr=DB.rh.presencas.filter(p=>p.funcId===f.id&&p.tipo==="normal").length;
      const faltas=DB.rh.presencas.filter(p=>p.funcId===f.id&&p.tipo==="falta").length;
      return`<tr><td style="font-weight:600;">${esc(f.nome)}</td><td>${esc(f.cargo)}</td><td>${esc(f.dep)}</td>
        <td style="color:var(--gold);">${mzn(f.salario_base)}</td>
        <td style="color:var(--green);">${pr}</td><td style="color:var(--red);">${faltas}</td>
        ${bdg(f.status)}
      </tr>`;
    }).join("");
    content=`<div class="g3" style="margin-bottom:14px;">
      <div class="kpi" style="border-left-color:var(--gold);"><div class="kpi-l">Folha Mensal</div><div class="kpi-v" style="color:var(--gold);">${mzn(folha)}</div></div>
      <div class="kpi" style="border-left-color:var(--green);"><div class="kpi-l">Presentes Hoje</div><div class="kpi-v" style="color:var(--green);">${presHoje.filter(p=>p.tipo==="normal").length}</div></div>
      <div class="kpi" style="border-left-color:var(--blue);"><div class="kpi-l">Total Funcionários</div><div class="kpi-v" style="color:var(--blue);">${DB.rh.funcionarios.length}</div></div>
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Nome</th><th>Cargo</th><th>Dep.</th><th>Salário</th><th>Presenças</th><th>Faltas</th><th>Status</th></tr></thead><tbody>${rows}</tbody></table></div>`;
  } else if(_relAba==="backup"){
    const tamanho=(JSON.stringify(DB).length/1024).toFixed(1);
    content=`<div class="card" style="margin-bottom:14px;">
      <div class="serif" style="font-size:15px;margin-bottom:14px;">💾 Backup e Segurança de Dados</div>
      <div style="background:var(--navy);border-radius:8px;padding:14px;margin-bottom:14px;">
        <div style="color:var(--muted);font-size:12px;margin-bottom:6px;">Estado da Base de Dados</div>
        <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:10px;font-size:12px;">
          ${[["Clientes",DB.clientes.length],["Cotações",DB.cotacoes.length],["Vendas",DB.vendas.length],["Produtos",DB.produtos.length]].map(([l,v2])=>`<div style="background:var(--card2);border-radius:6px;padding:8px;text-align:center;"><div style="color:var(--gold);font-weight:800;font-size:16px;">${v2}</div><div style="color:var(--muted);">${l}</div></div>`).join("")}
        </div>
        <div style="margin-top:10px;color:var(--muted);font-size:12px;">Tamanho actual: <b style="color:var(--text);">${tamanho} KB</b> · Última alteração: ${DB.logs[DB.logs.length-1]?.data||"—"}</div>
      </div>
      <div style="display:flex;gap:10px;flex-wrap:wrap;">
        <button class="btn btn-p" onclick="exportBackup()">📥 Exportar Backup (JSON)</button>
        <button class="btn btn-g" onclick="exportarCSV('tudo')">📊 Exportar CSV Completo</button>
        <label class="btn btn-b" style="cursor:pointer;">📤 Importar Backup<input type="file" accept=".json" style="display:none;" onchange="importBackup(this)"/></label>
        <button class="btn btn-n" onclick="if(confirm('ATENÇÃO: Isto irá apagar TODOS os dados! Tem a certeza?')){localStorage.clear();location.reload();}" style="color:var(--red);">🗑️ Limpar Dados</button>
      </div>
    </div>
    <div class="card">
      <div class="serif" style="font-size:14px;margin-bottom:12px;">📋 Últimas Atividades (${DB.logs.length} registos)</div>
      <div style="max-height:300px;overflow-y:auto;">
        ${[...DB.logs].reverse().slice(0,50).map(l=>`<div style="display:flex;gap:12px;padding:8px 0;border-bottom:1px solid var(--border);align-items:flex-start;">
          <div style="width:28px;height:28px;background:var(--navy);border-radius:50%;display:flex;align-items:center;justify-content:center;color:var(--red);font-size:11px;font-weight:700;flex-shrink:0;">${(l.user||"S")[0].toUpperCase()}</div>
          <div><div style="display:flex;gap:8px;align-items:center;margin-bottom:2px;">
            <span style="color:var(--gold);font-size:11px;font-weight:700;">@${esc(l.user||"sistema")}</span>
            <span style="color:var(--muted);font-size:10px;">${l.data}</span>
          </div><div style="color:var(--text);font-size:12px;">${esc(l.acao)}</div></div>
        </div>`).join("")}
      </div>
    </div>`;
  }
  return`<div class="ph"><div class="ph-title">Relatórios & Análise</div></div>
  <div class="tabs">${tabHtml}</div>${content}`;
}
function _setRel(a){_relAba=a;render("relatorios");}

function exportBackup(){
  const data=JSON.stringify(DB,null,2);
  const blob=new Blob([data],{type:"application/json"});
  const url=URL.createObjectURL(blob);
  const a=document.createElement("a");a.href=url;a.download=`OMS_Backup_${hoje()}.json`;a.click();
  URL.revokeObjectURL(url);addLog("Exportou backup de dados");
}
function importBackup(input){
  const file=input.files[0];if(!file)return;
  const reader=new FileReader();
  reader.onload=e=>{
    try{const d=JSON.parse(e.target.result);
      if(!d.clientes||!d.vendas)throw new Error("Ficheiro inválido!");
      if(!confirm("Importar backup? Os dados actuais serão substituídos."))return;
      saveDB(d);DB=d;addLog("Importou backup de dados");render("relatorios");
      alert("✅ Backup importado com sucesso!");
    }catch(err){alert("❌ Erro: Ficheiro de backup inválido!");}
  };
  reader.readAsText(file);
}
function exportarCSV(tipo){
  let csv="";let nome="dados";
  if(tipo==="vendas"||tipo==="tudo"){
    csv+="VENDAS\nNº Fatura,Cliente,Data,Total,Pago,Status\n";
    DB.vendas.forEach(v=>{csv+=`"${v.fatNum||v.num}","${v.cliNome}","${v.data}","${v.total}","${v.pago||0}","${v.status}"\n`;});
    nome="vendas";
  }
  if(tipo==="estoque"||tipo==="tudo"){
    if(tipo==="tudo")csv+="\n";
    csv+="ESTOQUE\nProduto,Categoria,Estoque,Mínimo,Preço Venda,Custo\n";
    DB.produtos.forEach(p=>{csv+=`"${p.nome}","${p.cat}","${p.estoque}","${p.min}","${p.preco}","${p.custo}"\n`;});
    nome=tipo==="tudo"?"completo":"estoque";
  }
  if(tipo==="tudo"){
    csv+="\nCLIENTES\nNome,Telefone,Email,Tipo,Status\n";
    DB.clientes.forEach(c=>{csv+=`"${c.nome}","${c.tel}","${c.email||""}","${c.tipo}","${c.status}"\n`;});
  }
  const blob=new Blob(["\uFEFF"+csv],{type:"text/csv;charset=utf-8"});
  const url=URL.createObjectURL(blob);
  const a=document.createElement("a");a.href=url;a.download=`OMS_${nome}_${hoje()}.csv`;a.click();
  URL.revokeObjectURL(url);addLog(`Exportou CSV: ${tipo}`);
}

// ════════════════════════════════════════════════════════════
// CONFIGURAÇÕES ADMINISTRATIVAS COMPLETAS
// ════════════════════════════════════════════════════════════
let _cfgAba="empresa";
function rConfig(){
  const abas=[["empresa","🏢 Empresa"],["visual","🎨 Logo & Visual"],["fiscal","🧾 Fiscal & IVA"],["pagamentos","💳 Pagamentos"],["users","👥 Utilizadores"],["seguranca","🔒 Segurança"]];
  let tabHtml=abas.map(([id,l])=>`<button class="tab${_cfgAba===id?" active":""}" onclick="_setCfg('${id}')">${l}</button>`).join("");
  let content="";
  const cfg=DB.cfg;
  if(_cfgAba==="empresa"){
    content=`<div class="card"><div class="serif" style="font-size:15px;margin-bottom:14px;">Dados da Empresa</div>
      <div class="g2">
        ${[["empresa","Nome da Empresa"],["slogan","Slogan / Actividade"],["nuit","NUIT"],["tel","Telefone Principal"],["email","Email Oficial"],["website","Website"],["end","Endereço"],["cidade","Cidade"],["pais","País"]].map(([k,l])=>`
          <div class="fg${k==="slogan"||k==="end"?" cs2":""}">
            <label class="lbl">${l}</label>
            <input class="inp" id="ce-${k}" value="${esc(cfg[k]||"")}"/>
          </div>`).join("")}
        <div class="fg cs2"><label class="lbl">Termos e Condições (aparecem nas cotações)</label>
          <textarea class="inp" id="ce-termos" style="height:80px;resize:vertical;">${esc(cfg.termos||"")}</textarea></div>
        <div class="fg cs2"><label class="lbl">Rodapé de Documentos</label>
          <input class="inp" id="ce-rodape" value="${esc(cfg.rodape||"")}"/></div>
        <div class="fg cs2"><label class="lbl">Mensagem WhatsApp (use: {cliente} {tipo} {numero} {total} {empresa} {tel})</label>
          <textarea class="inp" id="ce-msg_wa" style="height:70px;resize:vertical;">${esc(cfg.msg_wa||"")}</textarea></div>
      </div>
      <div class="mfoot" style="margin-top:14px;"><button class="btn btn-p" onclick="saveCfgEmpresa()">✔ Guardar Dados da Empresa</button></div>
    </div>`;
  } else if(_cfgAba==="visual"){
    const logoH=cfg.logo?`<img src="${cfg.logo}" style="max-height:80px;max-width:200px;object-fit:contain;" alt="Logo"/>`:'<span style="color:var(--muted);">Sem logótipo</span>';
    content=`<div class="card">
      <div class="serif" style="font-size:15px;margin-bottom:14px;">Logótipo e Aparência</div>
      <div class="fg"><label class="lbl">Logótipo da Empresa</label>
        <div style="display:flex;gap:16px;align-items:flex-start;flex-wrap:wrap;">
          <div style="width:200px;height:100px;background:var(--navy);border:2px dashed var(--border);border-radius:10px;display:flex;align-items:center;justify-content:center;overflow:hidden;">${logoH}</div>
          <div style="display:flex;flex-direction:column;gap:8px;">
            <label class="btn btn-p" style="cursor:pointer;">📁 Carregar Logótipo<input type="file" accept="image/*" style="display:none;" onchange="uploadLogo(this)"/></label>
            ${cfg.logo?`<button class="btn btn-n" onclick="remLogo()" style="color:var(--red);">✕ Remover</button>`:""}
            <div style="color:var(--muted);font-size:11px;">Formato: PNG, JPG<br/>Recomendado: 300×100px<br/>Aparece em documentos e sidebar</div>
          </div>
        </div>
      </div>
      <div class="g2" style="margin-top:14px;">
        <div class="fg"><label class="lbl">Moeda do Sistema</label>
          <select class="inp" id="cv-moeda"><option value="MZN" ${cfg.moeda==="MZN"?"selected":""}>MZN - Metical</option><option value="USD" ${cfg.moeda==="USD"?"selected":""}>USD - Dólar</option><option value="EUR" ${cfg.moeda==="EUR"?"selected":""}>EUR - Euro</option><option value="ZAR" ${cfg.moeda==="ZAR"?"selected":""}>ZAR - Rand</option></select></div>
      </div>
      <div class="mfoot" style="margin-top:14px;"><button class="btn btn-p" onclick="saveCfgVisual()">✔ Guardar</button></div>
    </div>`;
  } else if(_cfgAba==="fiscal"){
    content=`<div class="card">
      <div class="serif" style="font-size:15px;margin-bottom:14px;">Configuração Fiscal</div>
      <div class="g2">
        <div class="fg"><label class="lbl">IVA / Imposto Padrão (%)</label>
          <input class="inp" type="number" id="cfi-iva" value="${cfg.iva||16}" min="0" max="100"/>
          <div style="color:var(--muted);font-size:11px;margin-top:4px;">Aplicado automaticamente em cotações e vendas</div>
        </div>
        <div class="fg"><label class="lbl">NUIT da Empresa</label><input class="inp" id="cfi-nuit" value="${esc(cfg.nuit||"")}"/></div>
        <div class="fg"><label class="lbl">INSS Padrão Funcionários (%)</label>
          <input class="inp" type="number" id="cfi-inss" value="3" min="0" max="100"/>
        </div>
        <div class="fg"><label class="lbl">Tipo de Regime Fiscal</label>
          <select class="inp" id="cfi-regime">
            <option value="simplificado">Simplificado</option>
            <option value="geral">Geral</option>
            <option value="isento">Isento de IVA</option>
          </select>
        </div>
      </div>
      <div class="mfoot" style="margin-top:14px;"><button class="btn btn-p" onclick="saveCfgFiscal()">✔ Guardar Configuração Fiscal</button></div>
    </div>`;
  } else if(_cfgAba==="pagamentos"){
    let pgCards=cfg.pagamentos.map((p,i)=>`<div class="card" style="margin-bottom:10px;border-left:3px solid ${p.ativo?"var(--green)":"var(--border)"};">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;">
        <div style="flex:1;">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;">
            <span style="font-size:20px;">${p.tipo==="banco"?"🏦":p.tipo==="mpesa"?"📱":p.tipo==="emola"?"📲":"💵"}</span>
            <span style="font-weight:700;font-size:14px;">${esc(p.nome)}</span>
            ${p.ativo?bdgC("Ativo","var(--green)"):bdgC("Inativo","var(--muted)")}
          </div>
          ${p.conta?`<div style="color:var(--muted);font-size:12px;">Conta: ${esc(p.conta)}</div>`:""}
          ${p.numero?`<div style="color:var(--muted);font-size:12px;">Número: ${esc(p.numero)}</div>`:""}
          ${p.titular?`<div style="color:var(--muted);font-size:12px;">Titular: ${esc(p.titular)}</div>`:""}
        </div>
        <div style="display:flex;gap:6px;">
          <button class="btn btn-n btn-xs" onclick="editPg(${i})">✏️ Editar</button>
          <button class="btn btn-xs" style="background:${p.ativo?"rgba(192,39,45,.15)":"rgba(30,184,122,.15)"};color:${p.ativo?"var(--red)":"var(--green)"};border:none;" onclick="togglePg(${i})">${p.ativo?"⛔ Desactivar":"✅ Activar"}</button>
          <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delPg(${i})">🗑️</button>
        </div>
      </div>
    </div>`).join("");
    content=`<div style="display:flex;justify-content:flex-end;margin-bottom:12px;">
      <button class="btn btn-p" onclick="novoPg()">+ Adicionar Conta de Pagamento</button>
    </div>${pgCards}
    <div class="alert-g" style="margin-top:10px;font-size:12px;">
      💡 As contas activas aparecem automaticamente em todas as cotações e faturas no campo "Dados Bancários".
    </div>`;
  } else if(_cfgAba==="users"){
    let rows=USERS_LIST.map(u=>`<tr>
      <td><div style="display:flex;align-items:center;gap:8px;"><div class="u-av" style="width:28px;height:28px;font-size:11px;">${u.av}</div><span style="font-weight:600;">${u.nome}</span></div></td>
      <td style="color:var(--muted);">@${u.user}</td>
      <td>${bdgC(u.nivel.toUpperCase(),u.nivel==="admin"?"var(--red)":u.nivel==="vendas"?"var(--gold)":"var(--blue)")}</td>
      <td>${bdgC("Ativo","var(--green)")}</td>
      <td><div style="display:flex;gap:4px;">
        <button class="btn btn-n btn-xs" onclick="alterarSenha('${u.user}')">🔑 Senha</button>
      </div></td>
    </tr>`).join("");
    content=`<div class="alert-w" style="margin-bottom:14px;font-size:12px;">
      ⚠️ Sistema de utilizadores local. Para produção real com múltiplos utilizadores simultâneos, é necessário backend (Node.js/Python) com base de dados.
    </div>
    <div class="card"><table class="tbl"><thead><tr><th>Nome</th><th>Utilizador</th><th>Nível</th><th>Status</th><th>Ações</th></tr></thead><tbody>${rows}</tbody></table></div>
    <div class="card" style="margin-top:12px;">
      <div class="serif" style="font-size:14px;margin-bottom:10px;">Permissões por Nível</div>
      ${[["admin","Administrador","Acesso total a todos os módulos","var(--red)"],
         ["vendas","Vendas","Clientes, Cotações, Vendas, Estoque","var(--gold)"],
         ["financeiro","Financeiro","Vendas, Financeiro, Relatórios","var(--blue)"],
         ["rh","RH","Módulo de Recursos Humanos, Relatórios","var(--green)"]].map(([nv,nm,desc,c])=>`
        <div style="display:flex;justify-content:space-between;padding:9px 0;border-bottom:1px solid var(--border);">
          <div><span style="font-weight:700;color:${c};">${nm}</span><div style="color:var(--muted);font-size:12px;">${desc}</div></div>
          ${bdgC(nv.toUpperCase(),c)}
        </div>`).join("")}
    </div>`;
  } else if(_cfgAba==="seguranca"){
    content=`<div class="card" style="margin-bottom:12px;">
      <div class="serif" style="font-size:15px;margin-bottom:14px;">🔒 Segurança e Privacidade</div>
      <div style="background:var(--navy);border-radius:8px;padding:14px;margin-bottom:14px;">
        <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:10px;text-align:center;font-size:12px;">
          ${[["Sessão","Activa","var(--green)"],["Dados","Locais","var(--blue)"],["Logs","${DB.logs.length}","var(--gold)"],["Backup","Manual","var(--orange)"]].map(([l,v2,c])=>`<div style="background:var(--card2);border-radius:8px;padding:10px;"><div style="color:${c};font-weight:800;font-size:14px;">${v2}</div><div style="color:var(--muted);">${l}</div></div>`).join("")}
        </div>
      </div>
      <div style="display:flex;gap:10px;flex-wrap:wrap;margin-bottom:14px;">
        <button class="btn btn-p" onclick="exportBackup()">📥 Fazer Backup Agora</button>
        <button class="btn btn-g" onclick="exportarCSV('tudo')">📊 Exportar Todos os Dados</button>
        <button class="btn btn-n" onclick="alterarSenha('admin')">🔑 Alterar Senha Admin</button>
      </div>
      <div class="alert-w" style="font-size:12px;">
        <b>⚠️ Importante:</b> Os dados estão armazenados localmente no browser (localStorage). 
        Para segurança máxima, faça backup regularmente e não limpe o histórico do browser.
        Para uso profissional em rede com múltiplos computadores, migre para versão com servidor.
      </div>
    </div>
    <div class="card">
      <div class="serif" style="font-size:14px;margin-bottom:10px;">📋 Registo de Actividades Recentes</div>
      <div style="max-height:250px;overflow-y:auto;">
        ${[...DB.logs].reverse().slice(0,20).map(l=>`<div style="display:flex;gap:10px;padding:7px 0;border-bottom:1px solid var(--border);font-size:12px;">
          <span style="color:var(--gold);font-weight:700;min-width:70px;">@${esc(l.user||"?")}</span>
          <span style="color:var(--muted);min-width:130px;font-size:11px;">${l.data}</span>
          <span>${esc(l.acao)}</span>
        </div>`).join("")}
      </div>
    </div>`;
  }
  return`<div class="ph"><div class="ph-title">Configurações Administrativas</div></div>
  <div class="tabs">${tabHtml}</div>${content}`;
}
function _setCfg(a){_cfgAba=a;render("config");}

function saveCfgEmpresa(){
  const keys=["empresa","slogan","nuit","tel","email","website","end","cidade","pais","termos","rodape","msg_wa"];
  keys.forEach(k=>{const el=document.getElementById("ce-"+k);if(el)DB.cfg[k]=el.value;});
  addLog("Actualizou dados da empresa");saveDB(DB);updateLogo();
  alert("✅ Dados da empresa actualizados!");render("config");
}
function saveCfgVisual(){
  DB.cfg.moeda=v("cv-moeda")||"MZN";
  addLog("Actualizou configurações visuais");saveDB(DB);updateLogo();
  alert("✅ Configurações visuais guardadas!");render("config");
}
function saveCfgFiscal(){
  DB.cfg.iva=Number(v("cfi-iva")||16);
  DB.cfg.nuit=v("cfi-nuit")||DB.cfg.nuit;
  addLog(`IVA actualizado para ${DB.cfg.iva}%`);saveDB(DB);
  alert(`✅ IVA actualizado para ${DB.cfg.iva}%!`);render("config");
}

function uploadLogo(input){
  const file=input.files[0];if(!file)return;
  const reader=new FileReader();
  reader.onload=e=>{DB.cfg.logo=e.target.result;saveDB(DB);updateLogo();addLog("Actualizou logótipo");render("config");};
  reader.readAsDataURL(file);
}
function remLogo(){DB.cfg.logo=null;saveDB(DB);updateLogo();render("config");}

function novoPg(){
  openModal("Nova Conta de Pagamento",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Tipo</label>
      <select class="inp" id="pg-tp"><option value="banco">🏦 Banco</option><option value="mpesa">📱 M-Pesa</option><option value="emola">📲 e-Mola</option><option value="numerario">💵 Numerário</option></select></div>
    <div class="fg cs2"><label class="lbl">Nome do Banco / Serviço</label><input class="inp" id="pg-nm" placeholder="ex: BIM - Millennium Bim"/></div>
    <div class="fg"><label class="lbl">Nº Conta / Número Telefone</label><input class="inp" id="pg-ct" placeholder="Número da conta ou telefone"/></div>
    <div class="fg"><label class="lbl">Titular da Conta</label><input class="inp" id="pg-tit" placeholder="Nome do titular"/></div>
    <div class="fg"><label class="lbl">NIB / IBAN (opcional)</label><input class="inp" id="pg-nib"/></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="savePg()">${ico(ICOS.check,14)} Adicionar</button></div>`);
}
function savePg(){
  const tp=v("pg-tp");const nm=v("pg-nm");if(!nm)return alert("Nome obrigatório!");
  DB.cfg.pagamentos.push({id:Date.now(),tipo:tp,nome:nm,
    conta:tp==="banco"?v("pg-ct"):"",numero:tp!=="banco"?v("pg-ct"):"",
    titular:v("pg-tit"),nib:v("pg-nib"),ativo:true});
  addLog("Adicionou conta de pagamento: "+nm);saveDB(DB);closeModal();render("config");
}
function editPg(i){
  const p=DB.cfg.pagamentos[i];
  openModal("Editar Conta",`<div class="g2">
    <div class="fg cs2"><label class="lbl">Nome</label><input class="inp" id="ep-nm" value="${esc(p.nome)}"/></div>
    <div class="fg"><label class="lbl">Conta / Número</label><input class="inp" id="ep-ct" value="${esc(p.conta||p.numero||"")}"/></div>
    <div class="fg"><label class="lbl">Titular</label><input class="inp" id="ep-tit" value="${esc(p.titular||"")}"/></div>
    <div class="fg"><label class="lbl">NIB</label><input class="inp" id="ep-nib" value="${esc(p.nib||"")}"/></div>
  </div>
  <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="saveEditPg(${i})">Guardar</button></div>`);
}
function saveEditPg(i){
  const p=DB.cfg.pagamentos[i];
  p.nome=v("ep-nm");p.titular=v("ep-tit");p.nib=v("ep-nib");
  if(p.tipo==="banco")p.conta=v("ep-ct");else p.numero=v("ep-ct");
  saveDB(DB);closeModal();render("config");
}
function togglePg(i){DB.cfg.pagamentos[i].ativo=!DB.cfg.pagamentos[i].ativo;saveDB(DB);render("config");}
function delPg(i){if(!confirm("Eliminar?"))return;DB.cfg.pagamentos.splice(i,1);saveDB(DB);render("config");}

function alterarSenha(userLogin){
  openModal("Alterar Senha",`
    <div style="background:var(--navy);border-radius:8px;padding:11px;margin-bottom:13px;">
      <div style="color:var(--muted);font-size:12px;">Utilizador: <b style="color:var(--text);">@${esc(userLogin)}</b></div>
    </div>
    <div class="fg"><label class="lbl">Nova Senha</label><input class="inp" type="password" id="ns-s1" placeholder="Nova senha (mín. 6 caracteres)"/></div>
    <div class="fg"><label class="lbl">Confirmar Nova Senha</label><input class="inp" type="password" id="ns-s2" placeholder="Confirmar senha"/></div>
    <div class="mfoot"><button class="btn btn-n" onclick="closeModal()">Cancelar</button><button class="btn btn-p" onclick="confirmarSenha('${userLogin}')">🔑 Alterar Senha</button></div>`);
}
function confirmarSenha(userLogin){
  const s1=v("ns-s1");const s2=v("ns-s2");
  if(!s1||s1.length<6)return alert("Senha deve ter pelo menos 6 caracteres!");
  if(s1!==s2)return alert("As senhas não coincidem!");
  const u=USERS_LIST.find(x=>x.user===userLogin);
  if(u){u.pass=s1;addLog(`Senha alterada: @${userLogin}`);}
  closeModal();alert("✅ Senha alterada com sucesso!\n\nNota: A senha é temporária nesta sessão. Para permanente, edite o ficheiro HTML.");
}

// ════════════════════════════════════════════════════════════
// INICIALIZAÇÃO FINAL
// ════════════════════════════════════════════════════════════
// Registar módulo de projetos na navegação
NAV.splice(NAV.findIndex(n=>n.id==="obras")+1,0,{id:"projetos",lbl:"Projetos Inteligentes",grp:"Operacional",i:"prod"});
PERMS.admin.push("projetos");PERMS.vendas.push("projetos");
// render already defined above - just extend it
const _renderExtra={"rh-mod":rRH,projetos:rProjetos,relatorios:rRelatorios,config:rConfig};
// Patch render to include all pages
(function(){
  const _pages={dash:rDash,clientes:rClientes,cotacoes:rCotacoes,vendas:rVendas,"vendas-nova":rNovaVenda,
    estoque:rEstoque,obras:rObras,financeiro:rFinanceiro,"rh-mod":rRH,
    projetos:rProjetos,relatorios:rRelatorios,config:rConfig};
  window.render=function(p){
    DB=loadDB();
    const fn=_pages[p];
    document.getElementById("page-content").innerHTML=fn?fn():`<div class="alert-w" style="padding:20px;">Módulo em desenvolvimento.</div>`;
  };
})();

window.onload=function(){
  DB=loadDB();
  const inp=document.getElementById("l-user");if(inp)inp.focus();
  // Verificar dados da empresa e mostrar alerta se estiver com dados padrão
};


// ════════════════════════════════════════════════════════════
// PATCH: EXTEND SYSTEM WITH NEW MODULES
// Runs after all existing code is loaded
// ════════════════════════════════════════════════════════════

// === EXTENDED MODULES ===

// ─── EXTEND DB WITH NEW FIELDS ───────────────────────────
const _origLoad = window.loadDB;
window.loadDB = function() {
  let d = _origLoad ? _origLoad() : JSON.parse(localStorage.getItem("oms4_db")||"{}");
  if (!d.recibos) d.recibos = [];
  if (!d.guias) d.guias = [];
  if (!d.cartas) d.cartas = [];
  if (!d.recSeq) d.recSeq = 1;
  if (!d.guiaSeq) d.guiaSeq = 1;
  if (!d.cartaSeq) d.cartaSeq = 1;
  if (!d.lojas) d.lojas = [
    {id:1, nome:"Loja Principal", end:"Av. Julius Nyerere, 1234", cidade:"Maputo", tel:"+258 84 000 0000", ativa:true},
    {id:2, nome:"Escritório", end:"Av. da Namaacha, Parcela 88", cidade:"Maputo", tel:"+258 84 000 0001", ativa:true},
  ];
  if (!d.cfg.msg_recibo) d.cfg.msg_recibo = "Recebemos do(a) {cliente} a quantia de {valor} referente a {ref}. Obrigado!";
  // extend users list in DB
  if (!d.utilizadores) d.utilizadores = [
    {id:1, nome:"Administrador", user:"admin", pass:"admin123", nivel:"admin", ativo:true},
    {id:2, nome:"Agente de Vendas", user:"vendas", pass:"vendas123", nivel:"vendas", ativo:true},
    {id:3, nome:"Gestor Financeiro", user:"financeiro", pass:"fin123", nivel:"financeiro", ativo:true},
    {id:4, nome:"Gestor de RH", user:"rh", pass:"rh123", nivel:"rh", ativo:true},
  ];
  return d;
};

// ─── NAV ITEMS ───────────────────────────────────────────
const newNavItems = [
  {id:"documentos", lbl:"Documentos", grp:"Comercial", i:"cot"},
  {id:"lojas", lbl:"Lojas & Locais", grp:"Sistema", i:"build"},
  {id:"utilizadores-mgr", lbl:"Utilizadores", grp:"Sistema", i:"rh"},
];

// Called directly after all functions defined:

function patchSystem() {
  // Add nav items
  if (window.NAV) {
    newNavItems.forEach(ni => {
      if (!NAV.find(n => n.id === ni.id)) NAV.push(ni);
    });
    // Add permissions
    if (window.PERMS) {
      if (PERMS.admin) { PERMS.admin.push("documentos","lojas","utilizadores-mgr"); }
      if (PERMS.vendas) { PERMS.vendas.push("documentos"); }
    }
  }

  // Patch render to include new pages
  const _oldRender = window.render;
  window.render = function(p) {
    const extras = {
      documentos: rDocumentos,
      lojas: rLojas,
      "utilizadores-mgr": rUtilizadoresMgr,
    };
    if (extras[p]) {
      window.DB = window.loadDB ? window.loadDB() : DB;
      document.getElementById("page-content").innerHTML = extras[p]();
    } else {
      _oldRender(p);
    }
  };

  // Patch goTo
  const _oldGoTo = window.goTo;
  window.goTo = function(p) {
    window.CP = p;
    document.querySelectorAll(".nb").forEach(b => b.classList.remove("active"));
    const nb = document.getElementById("nb-" + p);
    if (nb) nb.classList.add("active");
    const allNav = window.NAV || [];
    const item = allNav.find(n => n.id === p);
    const tb = document.getElementById("tb-title");
    if (tb) tb.textContent = item ? item.lbl : p;
    window.render(p);
  };

  // Patch login to rebuild nav with new items
  const _origBuildNav = window.buildNav;
  window.buildNav = function() {
    _origBuildNav();
    // Rebuild sidebar with new items
    const ps = window.PERMS[window.CU.nivel] || [];
    const items = window.NAV.filter(n => ps.includes(n.id));
    const grps = [...new Set(items.map(n => n.grp))];
    let h = "";
    grps.forEach(g => {
      h += `<div class="grp-lbl">${g}</div>`;
      items.filter(n => n.grp === g).forEach(n => {
        h += `<button class="nb${n.id===window.CP?" active":""}" id="nb-${n.id}" onclick="goTo('${n.id}')" title="${n.lbl}">
          <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            ${icoPath(n.i)}</svg><span class="nb-lbl">${n.lbl}</span></button>`;
      });
    });
    const nav = document.getElementById("sb-nav");
    if (nav) nav.innerHTML = h;
  };

  // Patch doLogin to trigger new buildNav
  const _origLogin = window.doLogin;
  window.doLogin = function() {
    _origLogin();
  };

  console.log("✅ ONE MILLION SERVICE extended modules loaded");
}

function icoPath(key) {
  const p = {
    cot: '<path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><path d="M14 2v6h6"/><path d="M16 13H8"/><path d="M16 17H8"/>',
    build: '<path d="M2 20h20"/><path d="M4 20V10l8-8 8 8v10"/><path d="M12 20v-8"/>',
    rh: '<path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/>',
  };
  return p[key] || '<circle cx="12" cy="12" r="4"/>';
}

// ════════════════════════════════════════════════════════════
// HELPER: Quick client modal (add client without leaving page)
// ════════════════════════════════════════════════════════════
window.abrirModalNovoCliente = function(callbackFn) {
  window._clienteCallback = callbackFn;
  openModal("Novo Cliente Rápido", `
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome Completo / Empresa</label><input class="inp" id="qc-n" placeholder="Nome"/></div>
      <div class="fg"><label class="lbl">Telefone/WhatsApp</label><input class="inp" id="qc-t" placeholder="+258 84 000 0000"/></div>
      <div class="fg"><label class="lbl">Email</label><input class="inp" id="qc-e"/></div>
      <div class="fg"><label class="lbl">Tipo</label>
        <select class="inp" id="qc-tp"><option value="particular">Particular</option><option value="empresa">Empresa</option></select></div>
      <div class="fg"><label class="lbl">NUIT</label><input class="inp" id="qc-nu"/></div>
      <div class="fg cs2"><label class="lbl">Endereço</label><input class="inp" id="qc-en"/></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="saveClienteRapido()">✔ Guardar Cliente</button>
    </div>`);
};

window.saveClienteRapido = function() {
  const n = v("qc-n"); if (!n) return alert("Nome obrigatório!");
  const cli = {id: Date.now(), nome: n, tel: v("qc-t"), email: v("qc-e"), tipo: v("qc-tp"), nuit: v("qc-nu"), end: v("qc-en"), obs:"", status:"ativo"};
  DB.clientes.push(cli);
  addLog("Cliente rápido: " + n);
  saveDB(DB);
  closeModal();
  if (window._clienteCallback) window._clienteCallback(cli);
};

// ════════════════════════════════════════════════════════════
// DOCUMENTOS: RECIBOS, GUIAS, CARTAS
// ════════════════════════════════════════════════════════════
let _docAba = "recibos";

window.rDocumentos = function() {
  DB = loadDB();
  const abas = [["recibos","🧾 Recibos"],["guias","🚚 Guias de Remessa"],["cartas","📄 Cartas / Docs"]];
  let tabHtml = abas.map(([id,l]) => `<button class="tab${_docAba===id?" active":""}" onclick="_setDocAba('${id}')">${l}</button>`).join("");
  let content = "";
  if (_docAba === "recibos") content = _renderRecibos();
  else if (_docAba === "guias") content = _renderGuias();
  else content = _renderCartas();
  return `<div class="ph"><div class="ph-title">Documentos Comerciais</div><div class="ph-sub">Recibos · Guias de Remessa · Cartas</div></div>
  <div class="tabs">${tabHtml}</div>${content}`;
};
window._setDocAba = function(a) { _docAba = a; render("documentos"); };

// ─── RECIBOS ────────────────────────────────────────────
function _renderRecibos() {
  const pgOpts = DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  let rows = [...DB.recibos].reverse().map(r => `
    <div class="card" style="margin-bottom:9px;">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
        <div>
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:4px;">
            <span style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(r.num)}</span>
            <span style="font-weight:700;">${esc(r.cliNome)}</span>
          </div>
          <div style="color:var(--muted);font-size:12px;">📅 ${r.data} · 💳 ${esc(r.formaPag)} · Ref: ${esc(r.ref||"—")}</div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;">
          <div style="color:var(--green);font-size:20px;font-weight:800;">${mzn(r.valor)}</div>
          <div style="display:flex;gap:5px;">
            <button class="btn btn-p btn-xs" onclick="imprimirRecibo(${r.id})">🖨️ Imprimir</button>
            <button class="btn btn-g btn-xs" onclick="waRecibo(${r.id})">💬 WA</button>
            ${window.CU && window.CU.nivel==="admin"?`<button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delDoc('recibos',${r.id})">🗑️</button>`:""}
          </div>
        </div>
      </div>
    </div>`).join("");

  // Link from vendas
  const vendasComSaldo = DB.vendas.filter(vv => (vv.pago||0) > 0);
  const vendaOpts = vendasComSaldo.map(vv => `<option value="${vv.id}">${esc(vv.fatNum||vv.num)} — ${esc(vv.cliNome)} — ${mzn(vv.pago||0)} pago</option>`).join("");
  const cliOpts = DB.clientes.map(c => `<option value="${c.id}">${esc(c.nome)}</option>`).join("");

  return `
  <div style="display:flex;justify-content:flex-end;margin-bottom:12px;gap:8px;">
    <button class="btn btn-p" onclick="novoRecibo()">+ Novo Recibo</button>
    <button class="btn btn-g btn-sm" onclick="reciboDaVenda()">🔗 Recibo de Venda Existente</button>
  </div>
  ${rows || '<div class="alert-w">Sem recibos emitidos.</div>'}`;
}

window.novoRecibo = function() {
  const cliOpts = DB.clientes.map(c => `<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  const pgOpts = DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join("");
  openModal("Novo Recibo", `
    <div class="g2">
      <div class="fg cs2" style="display:flex;gap:8px;align-items:flex-end;">
        <div style="flex:1;"><label class="lbl">Cliente</label>
          <select class="inp" id="nr-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
        <button class="btn btn-g btn-sm" style="margin-bottom:13px;" onclick="abrirModalNovoCliente(function(c){document.getElementById('nr-cli').innerHTML+='<option value=\\''+c.id+'\\' selected>'+c.nome+'</option>';document.getElementById('nr-cli').value=c.id;})">+ Novo</button>
      </div>
      <div class="fg"><label class="lbl">Valor Recebido (${DB.cfg.moeda})</label><input class="inp" type="number" id="nr-val" min="0" placeholder="0.00"/></div>
      <div class="fg"><label class="lbl">Forma de Pagamento</label>
        <select class="inp" id="nr-pg" onchange="autoFillContaRecibo(this.value)">${pgOpts}</select></div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="nr-dt" value="${hoje()}"/></div>
      <div class="fg cs2"><label class="lbl">Referência (Nº Fatura, Serviço...)</label><input class="inp" id="nr-ref" placeholder="FAT-2026-001, Serviço de marcenaria..."/></div>
      <div class="fg cs2" id="nr-conta-info" style="background:var(--navy);border-radius:8px;padding:10px;font-size:12px;color:var(--muted);">Selecione a forma de pagamento</div>
      <div class="fg cs2"><label class="lbl">Observações</label><textarea class="inp" id="nr-obs" style="height:55px;resize:vertical;" placeholder="Notas adicionais..."></textarea></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarRecibo(0)">🧾 Emitir Recibo</button>
    </div>`);
  setTimeout(()=>autoFillContaRecibo(document.getElementById("nr-pg")?.value||""),100);
};

window.autoFillContaRecibo = function(nome) {
  const pg = DB.cfg.pagamentos.find(p=>p.nome===nome);
  const el = document.getElementById("nr-conta-info"); if(!el) return;
  if(pg) {
    if(pg.tipo==="banco") el.innerHTML=`🏦 <b>${esc(pg.nome)}</b><br/>Conta: <b>${esc(pg.conta||"—")}</b><br/>Titular: ${esc(pg.titular||"")}`;
    else if(pg.tipo==="numerario") el.innerHTML=`💵 <b>Numerário</b> — Dinheiro em mão`;
    else el.innerHTML=`📱 <b>${esc(pg.nome)}</b><br/>Número: <b>${esc(pg.numero||"—")}</b><br/>Titular: ${esc(pg.titular||"")}`;
  }
};

window.reciboDaVenda = function() {
  const vendasOpts = DB.vendas.filter(vv=>(vv.pago||0)>0).map(vv=>`<option value="${vv.id}">${esc(vv.fatNum||vv.num)} — ${esc(vv.cliNome)} — Pago: ${mzn(vv.pago||0)}</option>`).join("");
  openModal("Recibo de Venda Existente", `
    <div class="fg"><label class="lbl">Selecionar Venda</label>
      <select class="inp" id="rv-vnd" onchange="previewReciboDaVenda(this.value)">
        <option value="">Selecionar venda...</option>${vendasOpts}
      </select></div>
    <div id="rv-preview" style="background:var(--navy);border-radius:8px;padding:12px;margin-top:10px;font-size:13px;color:var(--muted);">
      Selecione uma venda para pré-visualizar
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="criarReciboDeVenda()">🧾 Criar Recibo</button>
    </div>`);
};

window.previewReciboDaVenda = function(id) {
  const vv = DB.vendas.find(x=>x.id==id); if(!vv) return;
  const el = document.getElementById("rv-preview"); if(!el) return;
  el.innerHTML = `<div style="color:var(--text);">
    <div><b>${esc(vv.fatNum||vv.num)}</b> · ${esc(vv.cliNome)}</div>
    <div style="margin-top:6px;">Total: <b style="color:var(--gold);">${mzn(vv.total)}</b></div>
    <div>Pago: <b style="color:var(--green);">${mzn(vv.pago||0)}</b></div>
    <div>Data: ${vv.data}</div>
    <div style="margin-top:6px;color:var(--muted);font-size:11px;">Recibo será gerado pelo valor pago</div>
  </div>`;
};

window.criarReciboDeVenda = function() {
  const id = Number(v("rv-vnd")); if(!id) return alert("Selecione uma venda!");
  const vv = DB.vendas.find(x=>x.id===id); if(!vv) return;
  const pg = vv.pagamentos?.[0];
  const num = pad(DB.recSeq, "REC");
  const rec = {id:Date.now(), num, cliId:vv.cliId, cliNome:vv.cliNome, valor:vv.pago||vv.total,
    formaPag:pg?.nome||"—", ref:vv.fatNum||vv.num, data:vv.data, obs:"", vendaId:vv.id};
  DB.recibos.push(rec); DB.recSeq++;
  addLog("Recibo criado: "+num); saveDB(DB); closeModal(); render("documentos");
};

window.salvarRecibo = function(id) {
  const cliId = Number(v("nr-cli")); if(!cliId) return alert("Selecione cliente!");
  const val = Number(v("nr-val")); if(!val) return alert("Valor inválido!");
  const cli = DB.clientes.find(c=>c.id===cliId);
  const num = pad(DB.recSeq, "REC");
  const rec = {id:id||Date.now(), num, cliId, cliNome:cli.nome, valor:val,
    formaPag:v("nr-pg"), ref:v("nr-ref"), data:v("nr-dt"), obs:v("nr-obs")};
  if(id) DB.recibos = DB.recibos.map(r=>r.id===id?rec:r);
  else { DB.recibos.push(rec); DB.recSeq++; }
  addLog((id?"Editou":"Emitiu")+" recibo "+num);
  saveDB(DB); closeModal(); render("documentos");
};

window.imprimirRecibo = function(id) {
  const r = DB.recibos.find(x=>x.id===id); if(!r) return;
  const cfg = DB.cfg;
  const cli = DB.clientes.find(c=>c.id===r.cliId)||{};
  const pgAtivos = cfg.pagamentos.filter(p=>p.ativo);
  const pg = cfg.pagamentos.find(p=>p.nome===r.formaPag);
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:60px;object-fit:contain;" alt="Logo"/>`:"";
  const msg = (cfg.msg_recibo||"Recebemos de {cliente} o valor de {valor} ref. {ref}.")
    .replace("{cliente}",r.cliNome).replace("{valor}",mzn(r.valor)).replace("{ref}",r.ref||"—");

  openModal(`Recibo — ${r.num}`, `
    <div class="pdf-wrap" id="pdf-content">
      <div style="text-align:center;margin-bottom:20px;">
        ${logoH?`<div style="margin-bottom:8px;">${logoH}</div>`:""}
        <div style="font-weight:800;font-size:20px;color:#1a2d4f;">${esc(cfg.empresa)}</div>
        <div style="color:#555;font-size:11px;">${esc(cfg.slogan)}<br/>${esc(cfg.cidade)}, ${esc(cfg.pais)} · ${esc(cfg.tel)}<br/>${cfg.nuit?`NUIT: ${esc(cfg.nuit)}`:""}</div>
      </div>
      <div style="background:#c0272d;color:#fff;text-align:center;padding:10px;border-radius:8px;margin-bottom:18px;">
        <div style="font-size:11px;letter-spacing:2px;opacity:.8;">DOCUMENTO</div>
        <div style="font-size:22px;font-weight:800;">RECIBO</div>
        <div style="font-size:13px;opacity:.9;">Nº ${esc(r.num)}</div>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:18px;">
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="font-size:10px;color:#888;text-transform:uppercase;margin-bottom:5px;">Recebido De</div>
          <div style="font-weight:700;font-size:15px;">${esc(r.cliNome)}</div>
          ${cli.tel?`<div style="color:#555;font-size:11px;">${esc(cli.tel)}</div>`:""}
          ${cli.nuit?`<div style="color:#555;font-size:11px;">NUIT: ${esc(cli.nuit)}</div>`:""}
        </div>
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="font-size:10px;color:#888;text-transform:uppercase;margin-bottom:5px;">Data & Referência</div>
          <div style="font-weight:700;">${r.data}</div>
          <div style="color:#555;font-size:12px;">Ref: ${esc(r.ref||"—")}</div>
          <div style="color:#555;font-size:12px;">Forma: ${esc(r.formaPag)}</div>
        </div>
      </div>
      <div style="background:#1a2d4f;color:#fff;border-radius:10px;padding:18px;text-align:center;margin-bottom:18px;">
        <div style="font-size:11px;opacity:.7;margin-bottom:4px;">VALOR RECEBIDO</div>
        <div style="font-size:32px;font-weight:800;color:#d4a820;">${mzn(r.valor)}</div>
      </div>
      ${pg && pg.tipo!=="numerario"?`
      <div style="background:#f0f4f8;border-radius:8px;padding:12px;margin-bottom:14px;font-size:12px;">
        <div style="font-weight:700;margin-bottom:5px;color:#1a2d4f;">Dados de Pagamento:</div>
        <div>${pg.tipo==="banco"?`🏦 ${esc(pg.nome)} · Conta: ${esc(pg.conta||"—")} · Titular: ${esc(pg.titular||"")}`:`📱 ${esc(pg.nome)} · ${esc(pg.numero||"—")}`}</div>
      </div>`:""}
      <div style="margin:14px 0;padding:12px;border:1px solid #e0e4ea;border-radius:8px;font-size:12px;font-style:italic;color:#555;">${esc(msg)}</div>
      ${r.obs?`<div style="background:#fffbea;border:1px solid #ffe070;border-radius:8px;padding:10px;font-size:12px;margin-bottom:14px;"><b>Obs:</b> ${esc(r.obs)}</div>`:""}
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:30px;margin-top:24px;">
        <div style="text-align:center;">
          <div style="height:40px;"></div>
          <div style="border-top:1px solid #999;padding-top:8px;font-size:11px;color:#888;">O Cliente</div>
        </div>
        <div style="text-align:center;">
          <div style="height:40px;"></div>
          <div style="border-top:1px solid #999;padding-top:8px;font-size:11px;color:#888;">O Responsável — ${esc(cfg.empresa)}</div>
        </div>
      </div>
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:14px;border-top:1px solid #eee;padding-top:10px;">${esc(cfg.rodape||cfg.empresa)} · ${esc(cfg.email)} · ${esc(cfg.tel)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn btn-g" onclick="waRecibo(${r.id})">💬 WhatsApp</button>
      <button class="btn btn-p" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"wide");
};

window.waRecibo = function(id) {
  const r = DB.recibos.find(x=>x.id===id); if(!r) return;
  const cli = DB.clientes.find(c=>c.id===r.cliId);
  if(!cli?.tel) return alert("Cliente sem telefone!");
  const cfg = DB.cfg;
  const msg = `*${cfg.empresa}*\n\n*🧾 RECIBO ${r.num}*\n\nCliente: ${r.cliNome}\nData: ${r.data}\nForma: ${r.formaPag}\nRef: ${r.ref||"—"}\n\n*VALOR: ${mzn(r.valor)}*\n\n${r.obs||""}\n\n${cfg.tel}`;
  window.open(`https://wa.me/${cli.tel.replace(/\D/g,"")}?text=${encodeURIComponent(msg)}`,"_blank");
};

// ─── GUIAS DE REMESSA ────────────────────────────────────
function _renderGuias() {
  let rows = [...DB.guias].reverse().map(g => `
    <div class="card" style="margin-bottom:9px;">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
        <div>
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:4px;">
            <span style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(g.num)}</span>
            <span style="font-weight:700;">${esc(g.cliNome)}</span>
          </div>
          <div style="color:var(--muted);font-size:12px;">📅 ${g.data} · 🚚 ${esc(g.transportador||"—")} · 📍 ${esc(g.destino||"—")}</div>
          <div style="color:var(--muted);font-size:12px;">${(g.itens||[]).length} item(ns)</div>
        </div>
        <div style="display:flex;gap:5px;">
          <button class="btn btn-p btn-xs" onclick="imprimirGuia(${g.id})">🖨️ Imprimir</button>
          <button class="btn btn-g btn-xs" onclick="waGuia(${g.id})">💬 WA</button>
          ${window.CU && window.CU.nivel==="admin"?`<button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delDoc('guias',${g.id})">🗑️</button>`:""}
        </div>
      </div>
    </div>`).join("");

  return `
  <div style="display:flex;justify-content:flex-end;margin-bottom:12px;gap:8px;">
    <button class="btn btn-p" onclick="novaGuia()">+ Nova Guia de Remessa</button>
    <button class="btn btn-g btn-sm" onclick="guiaDaVenda()">🔗 Guia de Venda Existente</button>
  </div>
  ${rows || '<div class="alert-w">Sem guias emitidas.</div>'}`;
}

let _guiaItens = [{desc:"",qty:1,un:"un"}];

window.novaGuia = function() {
  _guiaItens = [{desc:"",qty:1,un:"un"}];
  const cliOpts = DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join("");
  const lojasOpts = DB.lojas.filter(l=>l.ativa).map(l=>`<option value="${esc(l.nome)}">${esc(l.nome)} — ${esc(l.cidade)}</option>`).join("");
  openModal("Nova Guia de Remessa", `
    <div class="g2">
      <div class="fg cs2" style="display:flex;gap:8px;align-items:flex-end;">
        <div style="flex:1;"><label class="lbl">Cliente / Destinatário</label>
          <select class="inp" id="ng-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
        <button class="btn btn-g btn-sm" style="margin-bottom:13px;" onclick="abrirModalNovoCliente(function(c){var s=document.getElementById('ng-cli');s.innerHTML+='<option value=\\''+c.id+'\\' selected>'+c.nome+'</option>';s.value=c.id;})">+ Novo</button>
      </div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="ng-dt" value="${hoje()}"/></div>
      <div class="fg"><label class="lbl">Transportador</label><input class="inp" id="ng-transp" placeholder="Nome do motorista / empresa"/></div>
      <div class="fg"><label class="lbl">Destino / Local de Entrega</label><input class="inp" id="ng-dest" placeholder="Endereço de destino"/></div>
      <div class="fg"><label class="lbl">Loja de Origem</label>
        <select class="inp" id="ng-orig"><option value="">Selecionar loja...</option>${lojasOpts}</select></div>
      <div class="fg"><label class="lbl">Referência</label><input class="inp" id="ng-ref" placeholder="FAT-2026-001..."/></div>
    </div>
    <div style="margin:13px 0;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
        <label class="lbl" style="margin:0;">Produtos / Mercadorias</label>
        <button class="btn btn-n btn-xs" onclick="_addGuiaItem()">+ Item</button>
      </div>
      <div style="background:var(--navy);border-radius:9px;padding:11px;" id="ng-itens-wrap">
        <div style="display:grid;grid-template-columns:3fr 1fr 1fr 24px;gap:6px;margin-bottom:6px;">
          ${["Descrição","Un.","Qtd",""].map(h=>`<div style="color:var(--muted);font-size:11px;text-transform:uppercase;">${h}</div>`).join("")}
        </div>
        <div id="ng-itens"></div>
      </div>
    </div>
    <div class="fg"><label class="lbl">Observações</label><textarea class="inp" id="ng-obs" style="height:55px;resize:vertical;"></textarea></div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarGuia(0)">🚚 Emitir Guia</button>
    </div>`,"wide");
  _renderGuiaItens();
};

window._addGuiaItem = function() { _guiaItens.push({desc:"",qty:1,un:"un"}); _renderGuiaItens(); };
window._remGuiaItem = function(i) { if(_guiaItens.length===1)return; _guiaItens.splice(i,1); _renderGuiaItens(); };
window._updGuiaItem = function(i,k,val) { _guiaItens[i][k]=["qty"].includes(k)?Number(val):val; };

function _renderGuiaItens() {
  const cont = document.getElementById("ng-itens"); if(!cont) return;
  cont.innerHTML = _guiaItens.map((it,i) => `
    <div style="display:grid;grid-template-columns:3fr 1fr 1fr 24px;gap:6px;margin-bottom:5px;">
      <input class="inp" style="padding:7px 8px;font-size:12px;" placeholder="Descrição" value="${esc(it.desc)}" oninput="_updGuiaItem(${i},'desc',this.value)"/>
      <input class="inp" style="padding:7px 8px;font-size:12px;" value="${esc(it.un)}" oninput="_updGuiaItem(${i},'un',this.value)"/>
      <input class="inp" type="number" style="padding:7px 8px;font-size:12px;" value="${it.qty}" oninput="_updGuiaItem(${i},'qty',this.value)" min="1"/>
      <button onclick="_remGuiaItem(${i})" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:16px;">×</button>
    </div>`).join("");
}

window.salvarGuia = function(id) {
  const cliId = Number(v("ng-cli")); if(!cliId) return alert("Selecione cliente!");
  if(!_guiaItens[0].desc) return alert("Adicione pelo menos 1 item!");
  const cli = DB.clientes.find(c=>c.id===cliId);
  const num = pad(DB.guiaSeq, "GR");
  const g = {id:id||Date.now(), num, cliId, cliNome:cli.nome, data:v("ng-dt"),
    transportador:v("ng-transp"), destino:v("ng-dest"), origem:v("ng-orig"), ref:v("ng-ref"),
    itens:_guiaItens.map(it=>({...it})), obs:v("ng-obs")};
  if(id) DB.guias = DB.guias.map(x=>x.id===id?g:x);
  else { DB.guias.push(g); DB.guiaSeq++; }
  addLog((id?"Editou":"Emitiu")+" guia "+num);
  saveDB(DB); closeModal(); render("documentos");
};

window.guiaDaVenda = function() {
  const vendasOpts = DB.vendas.map(vv=>`<option value="${vv.id}">${esc(vv.fatNum||vv.num)} — ${esc(vv.cliNome)}</option>`).join("");
  openModal("Guia de Venda Existente", `
    <div class="fg"><label class="lbl">Selecionar Venda</label>
      <select class="inp" id="gv2-vnd"><option value="">...</option>${vendasOpts}</select></div>
    <div class="fg"><label class="lbl">Transportador</label><input class="inp" id="gv2-tr" placeholder="Nome motorista/empresa"/></div>
    <div class="fg"><label class="lbl">Destino</label><input class="inp" id="gv2-dest" placeholder="Endereço de entrega"/></div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="criarGuiaDaVenda()">🚚 Criar Guia</button>
    </div>`);
};

window.criarGuiaDaVenda = function() {
  const id = Number(v("gv2-vnd")); if(!id) return alert("Selecione venda!");
  const vv = DB.vendas.find(x=>x.id===id); if(!vv) return;
  const num = pad(DB.guiaSeq, "GR");
  const g = {id:Date.now(), num, cliId:vv.cliId, cliNome:vv.cliNome, data:hoje(),
    transportador:v("gv2-tr"), destino:v("gv2-dest"), origem:"", ref:vv.fatNum||vv.num,
    itens:vv.itens.map(it=>({desc:it.desc, qty:it.qty, un:it.un||"un"})), obs:""};
  DB.guias.push(g); DB.guiaSeq++;
  addLog("Guia criada de venda: "+num); saveDB(DB); closeModal(); render("documentos");
};

window.imprimirGuia = function(id) {
  const g = DB.guias.find(x=>x.id===id); if(!g) return;
  const cfg = DB.cfg;
  const cli = DB.clientes.find(c=>c.id===g.cliId)||{};
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:55px;object-fit:contain;" alt="Logo"/>`:"";
  const loja = DB.lojas.find(l=>l.nome===g.origem);
  const rows = (g.itens||[]).map((it,i)=>`<tr>
    <td style="padding:8px 12px;border-bottom:1px solid #eee;">${i+1}</td>
    <td style="padding:8px 12px;border-bottom:1px solid #eee;font-weight:600;">${esc(it.desc)}</td>
    <td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;">${esc(it.un||"un")}</td>
    <td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:right;font-weight:700;">${it.qty}</td>
  </tr>`).join("");

  openModal(`Guia de Remessa — ${g.num}`, `
    <div class="pdf-wrap" id="pdf-content">
      <div class="pdf-hdr">
        <div>${logoH?`<div style="margin-bottom:6px;">${logoH}</div>`:""}
          <div class="pdf-co">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan)}<br/>${esc(cfg.cidade)}, ${esc(cfg.pais)}<br/>${esc(cfg.tel)}</div>
          ${loja?`<div style="color:#1a2d4f;font-size:11px;margin-top:4px;">Origem: <b>${esc(loja.nome)}</b> · ${esc(loja.end)}</div>`:""}
        </div>
        <div style="text-align:right;">
          <div class="pdf-badge">GUIA DE REMESSA</div>
          <div style="font-weight:800;font-size:14px;color:#1a2d4f;margin-top:4px;">${esc(g.num)}</div>
          <div style="color:#777;font-size:11px;">Data: ${g.data}</div>
          ${g.ref?`<div style="color:#555;font-size:11px;">Ref: ${esc(g.ref)}</div>`:""}
        </div>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:18px;">
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Destinatário</div>
          <div style="font-weight:700;font-size:15px;">${esc(g.cliNome)}</div>
          ${cli.tel?`<div style="color:#555;font-size:11px;">${esc(cli.tel)}</div>`:""}
          <div style="color:#1a2d4f;font-size:12px;margin-top:4px;">📍 ${esc(g.destino||"—")}</div>
        </div>
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Transporte</div>
          <div style="font-weight:700;">🚚 ${esc(g.transportador||"—")}</div>
          <div style="color:#555;font-size:12px;margin-top:4px;">Data de entrega: ${g.data}</div>
        </div>
      </div>
      <table style="width:100%;border-collapse:collapse;margin-bottom:16px;">
        <thead><tr style="background:#1a2d4f;color:#fff;">
          <th style="padding:9px 12px;">#</th>
          <th style="padding:9px 12px;text-align:left;">Descrição do Artigo</th>
          <th style="padding:9px 12px;">Unidade</th>
          <th style="padding:9px 12px;text-align:right;">Quantidade</th>
        </tr></thead>
        <tbody>${rows}</tbody>
      </table>
      ${g.obs?`<div style="background:#fffbea;border:1px solid #ffe070;border-radius:8px;padding:10px;font-size:12px;margin-bottom:14px;"><b>Observações:</b> ${esc(g.obs)}</div>`:""}
      <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px;margin-top:24px;">
        <div style="text-align:center;"><div style="height:35px;"></div><div style="border-top:1px solid #999;padding-top:7px;font-size:10px;color:#888;">Emitido por — ${esc(cfg.empresa)}</div></div>
        <div style="text-align:center;"><div style="height:35px;"></div><div style="border-top:1px solid #999;padding-top:7px;font-size:10px;color:#888;">Transportador</div></div>
        <div style="text-align:center;"><div style="height:35px;"></div><div style="border-top:1px solid #999;padding-top:7px;font-size:10px;color:#888;">Recebido pelo Cliente</div></div>
      </div>
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:12px;border-top:1px solid #eee;padding-top:8px;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn btn-g" onclick="waGuia(${g.id})">💬 WhatsApp</button>
      <button class="btn btn-p" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"wide");
};

window.waGuia = function(id) {
  const g = DB.guias.find(x=>x.id===id); if(!g) return;
  const cli = DB.clientes.find(c=>c.id===g.cliId);
  if(!cli?.tel) return alert("Cliente sem telefone!");
  const itens = (g.itens||[]).map(it=>`  • ${it.desc}: ${it.qty} ${it.un||"un"}`).join("\n");
  const msg = `*${DB.cfg.empresa}*\n\n*🚚 GUIA DE REMESSA ${g.num}*\nData: ${g.data}\nDestino: ${g.destino||"—"}\nTransportador: ${g.transportador||"—"}\n\n*Mercadorias:*\n${itens}\n\n${DB.cfg.tel}`;
  window.open(`https://wa.me/${cli.tel.replace(/\D/g,"")}?text=${encodeURIComponent(msg)}`,"_blank");
};

// ─── CARTAS / DOCUMENTOS ────────────────────────────────
function _renderCartas() {
  let rows = [...DB.cartas].reverse().map(c => `
    <div class="card" style="margin-bottom:9px;">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
        <div>
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:4px;">
            <span style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(c.num)}</span>
            <span style="font-weight:700;">${esc(c.assunto)}</span>
          </div>
          <div style="color:var(--muted);font-size:12px;">📅 ${c.data} · Para: ${esc(c.para||"—")}</div>
        </div>
        <div style="display:flex;gap:5px;">
          <button class="btn btn-p btn-xs" onclick="imprimirCarta(${c.id})">🖨️ Imprimir</button>
          ${window.CU && window.CU.nivel==="admin"?`<button class="btn btn-n btn-xs" onclick="editCarta(${c.id})">✏️</button><button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delDoc('cartas',${c.id})">🗑️</button>`:""}
        </div>
      </div>
    </div>`).join("");

  return `
  <div style="display:flex;justify-content:flex-end;margin-bottom:12px;">
    <button class="btn btn-p" onclick="novaCarta()">+ Nova Carta / Documento</button>
  </div>
  ${rows || '<div class="alert-w">Sem cartas emitidas.</div>'}`;
}

window.novaCarta = function(id) {
  const c = id ? DB.cartas.find(x=>x.id===id) : null;
  openModal(c?"Editar Carta":"Nova Carta / Documento", `
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Assunto / Título</label><input class="inp" id="nc-ass" value="${esc(c?.assunto||"")}" placeholder="Ex: Proposta Comercial, Comunicado Interno..."/></div>
      <div class="fg"><label class="lbl">Para (Destinatário)</label><input class="inp" id="nc-para" value="${esc(c?.para||"")}" placeholder="Nome / Empresa"/></div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="nc-dt" value="${c?.data||hoje()}"/></div>
      <div class="fg"><label class="lbl">Saudação</label><input class="inp" id="nc-sau" value="${esc(c?.saudacao||"Exmo(a). Sr(a).")}" /></div>
      <div class="fg"><label class="lbl">Fecho</label><input class="inp" id="nc-fecho" value="${esc(c?.fecho||"Com os melhores cumprimentos,")}" /></div>
    </div>
    <div class="fg" style="margin-top:6px;"><label class="lbl">Corpo do Documento</label>
      <textarea class="inp" id="nc-corpo" style="height:150px;resize:vertical;" placeholder="Escreva o conteúdo da carta aqui...">${esc(c?.corpo||"")}</textarea></div>
    <div class="fg"><label class="lbl">Observações / Rodapé Adicional</label>
      <input class="inp" id="nc-obs" value="${esc(c?.obs||"")}" placeholder="Observações finais..."/></div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarCarta(${id||0})">📄 ${c?"Guardar":"Criar Documento"}</button>
    </div>`,"wide");
};
window.editCarta = function(id) { novaCarta(id); };

window.salvarCarta = function(id) {
  const ass = v("nc-ass"); if(!ass) return alert("Assunto obrigatório!");
  const num = id ? (DB.cartas.find(x=>x.id===id)?.num||pad(DB.cartaSeq,"DOC")) : pad(DB.cartaSeq,"DOC");
  const c = {id:id||Date.now(), num, assunto:ass, para:v("nc-para"), data:v("nc-dt"),
    saudacao:v("nc-sau"), corpo:v("nc-corpo"), fecho:v("nc-fecho"), obs:v("nc-obs")};
  if(id) DB.cartas = DB.cartas.map(x=>x.id===id?c:x);
  else { DB.cartas.push(c); DB.cartaSeq++; }
  addLog((id?"Editou":"Criou")+" carta "+num);
  saveDB(DB); closeModal(); render("documentos");
};

window.imprimirCarta = function(id) {
  const c = DB.cartas.find(x=>x.id===id); if(!c) return;
  const cfg = DB.cfg;
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:60px;object-fit:contain;" alt="Logo"/>`:"";
  openModal(`${c.assunto} — ${c.num}`, `
    <div class="pdf-wrap" id="pdf-content">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;padding-bottom:16px;border-bottom:3px solid #c0272d;">
        <div>${logoH?`<div style="margin-bottom:6px;">${logoH}</div>`:""}
          <div style="font-weight:800;font-size:18px;color:#1a2d4f;">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan)}<br/>${esc(cfg.end||"")}, ${esc(cfg.cidade)}<br/>${esc(cfg.tel)} · ${esc(cfg.email)}<br/>${cfg.nuit?"NUIT: "+esc(cfg.nuit):""}</div>
        </div>
        <div style="text-align:right;color:#555;font-size:12px;">
          <div style="font-weight:700;color:#1a2d4f;font-size:14px;">${esc(c.num)}</div>
          <div>${esc(cfg.cidade)}, ${c.data}</div>
        </div>
      </div>
      ${c.para?`<div style="margin-bottom:16px;"><div style="font-weight:700;">A/C: ${esc(c.para)}</div></div>`:""}
      <div style="margin-bottom:10px;font-weight:700;font-size:15px;color:#1a2d4f;">Assunto: ${esc(c.assunto)}</div>
      ${c.saudacao?`<div style="margin-bottom:12px;">${esc(c.saudacao)},</div>`:""}
      <div style="line-height:1.7;color:#333;white-space:pre-wrap;margin-bottom:20px;">${esc(c.corpo)}</div>
      ${c.fecho?`<div style="margin-bottom:30px;">${esc(c.fecho)}</div>`:""}
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-top:20px;">
        <div></div>
        <div style="text-align:center;">
          <div style="height:40px;"></div>
          <div style="border-top:1px solid #999;padding-top:8px;font-size:11px;color:#555;">${esc(cfg.empresa)}</div>
        </div>
      </div>
      ${c.obs?`<div style="border-top:1px solid #eee;padding-top:10px;margin-top:16px;font-size:11px;color:#888;">${esc(c.obs)}</div>`:""}
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:14px;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn btn-p" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"wide");
};

window.delDoc = function(tipo, id) {
  if(!confirm("Eliminar documento?")) return;
  DB[tipo] = DB[tipo].filter(x=>x.id!==id);
  addLog(`Eliminado ${tipo}: ${id}`);
  // Notify admin
  if(window.CU && window.CU.nivel !== "admin") {
    console.warn("NOTIFICAÇÃO ADMIN: Documento eliminado por @"+window.CU.user);
  }
  saveDB(DB); render("documentos");
};

// ════════════════════════════════════════════════════════════
// LOJAS & LOCALIZAÇÕES
// ════════════════════════════════════════════════════════════
window.rLojas = function() {
  DB = loadDB();
  let cards = DB.lojas.map((l,i) => `
    <div class="card" style="margin-bottom:10px;border-left:3px solid ${l.ativa?"var(--green)":"var(--border)"};">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;">
        <div>
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:6px;">
            <span style="font-size:20px;">🏪</span>
            <span style="font-weight:700;font-size:15px;">${esc(l.nome)}</span>
            ${l.ativa?`<span class="bdg" style="background:rgba(30,184,122,.15);color:var(--green);">Activa</span>`:`<span class="bdg" style="background:rgba(138,155,176,.15);color:var(--muted);">Inactiva</span>`}
          </div>
          <div style="color:var(--muted);font-size:13px;">📍 ${esc(l.end||"—")}</div>
          <div style="color:var(--muted);font-size:13px;">🏙️ ${esc(l.cidade||"—")}</div>
          ${l.tel?`<div style="color:var(--muted);font-size:13px;">📞 ${esc(l.tel)}</div>`:""}
          ${l.resp?`<div style="color:var(--muted);font-size:13px;">👤 Resp: ${esc(l.resp)}</div>`:""}
        </div>
        <div style="display:flex;gap:6px;">
          <button class="btn btn-n btn-xs" onclick="editLoja(${i})">✏️ Editar</button>
          <button class="btn btn-xs" style="background:${l.ativa?"rgba(192,39,45,.15)":"rgba(30,184,122,.15)"};color:${l.ativa?"var(--red)":"var(--green)"};border:none;" onclick="toggleLoja(${i})">${l.ativa?"Desactivar":"Activar"}</button>
          <button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delLoja(${i})">🗑️</button>
        </div>
      </div>
    </div>`).join("");

  return `
    <div class="ph">
      <div><div class="ph-title">Lojas & Localizações</div><div class="ph-sub">${DB.lojas.length} local(is) cadastrado(s)</div></div>
      <button class="btn btn-p" onclick="novaLoja()">+ Nova Loja / Local</button>
    </div>
    ${cards||'<div class="alert-w">Sem lojas cadastradas.</div>'}
    <div class="alert-g" style="margin-top:12px;font-size:12px;">
      💡 As lojas aparecem nas guias de remessa como local de origem dos produtos.
    </div>`;
};

window.novaLoja = function(idx) {
  const l = idx!=null ? DB.lojas[idx] : null;
  openModal(l?"Editar Local":"Nova Loja / Local", `
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome (Loja 1, Escritório, Armazém...)</label><input class="inp" id="lj-n" value="${esc(l?.nome||"")}" placeholder="ex: Loja Principal"/></div>
      <div class="fg"><label class="lbl">Endereço</label><input class="inp" id="lj-e" value="${esc(l?.end||"")}" placeholder="Rua, nº..."/></div>
      <div class="fg"><label class="lbl">Cidade</label><input class="inp" id="lj-c" value="${esc(l?.cidade||"Maputo")}"/></div>
      <div class="fg"><label class="lbl">Telefone</label><input class="inp" id="lj-t" value="${esc(l?.tel||"")}"/></div>
      <div class="fg"><label class="lbl">Responsável</label><input class="inp" id="lj-r" value="${esc(l?.resp||"")}"/></div>
      <div class="fg"><label class="lbl">Email</label><input class="inp" id="lj-em" value="${esc(l?.email||"")}"/></div>
      <div class="fg cs2"><label class="lbl">Notas</label><input class="inp" id="lj-o" value="${esc(l?.obs||"")}"/></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarLoja(${idx!=null?idx:-1})">✔ Guardar</button>
    </div>`);
};
window.editLoja = function(i) { novaLoja(i); };
window.salvarLoja = function(idx) {
  const n = v("lj-n"); if(!n) return alert("Nome obrigatório!");
  const obj = {id:idx>=0?(DB.lojas[idx]?.id||Date.now()):Date.now(), nome:n, end:v("lj-e"), cidade:v("lj-c"), tel:v("lj-t"), resp:v("lj-r"), email:v("lj-em"), obs:v("lj-o"), ativa:true};
  if(idx>=0) DB.lojas[idx]=obj; else DB.lojas.push(obj);
  addLog((idx>=0?"Editou":"Criou")+" loja: "+n);
  saveDB(DB); closeModal(); render("lojas");
};
window.toggleLoja = function(i) { DB.lojas[i].ativa=!DB.lojas[i].ativa; saveDB(DB); render("lojas"); };
window.delLoja = function(i) { if(!confirm("Eliminar?"))return; DB.lojas.splice(i,1); saveDB(DB); render("lojas"); };

// ════════════════════════════════════════════════════════════
// GESTÃO DE UTILIZADORES (ADMIN ONLY)
// ════════════════════════════════════════════════════════════
window.rUtilizadoresMgr = function() {
  DB = loadDB();
  const nivOpts = `<option value="admin">Administrador</option><option value="vendas">Vendas</option><option value="financeiro">Financeiro</option><option value="rh">RH</option><option value="viewer">Visualizador</option>`;

  let rows = DB.utilizadores.map(u => `
    <div class="card" style="margin-bottom:10px;border-left:3px solid ${u.ativo?"var(--green)":"var(--border)"};">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
        <div style="display:flex;align-items:center;gap:12px;">
          <div style="width:42px;height:42px;background:linear-gradient(135deg,${u.nivel==="admin"?"var(--red),var(--red2)":u.nivel==="vendas"?"#c8973a,#e8c97a":"var(--navy2),var(--navy3)"});border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800;font-size:16px;">${(u.nome||u.user)[0].toUpperCase()}</div>
          <div>
            <div style="font-weight:700;font-size:14px;">${esc(u.nome)}</div>
            <div style="color:var(--muted);font-size:12px;">@${esc(u.user)} · ${u.nivel.toUpperCase()}</div>
            ${u.email?`<div style="color:var(--muted);font-size:12px;">${esc(u.email)}</div>`:""}
          </div>
        </div>
        <div style="display:flex;gap:6px;align-items:center;">
          ${u.ativo?`<span class="bdg" style="background:rgba(30,184,122,.15);color:var(--green);">Ativo</span>`:`<span class="bdg" style="background:rgba(192,39,45,.15);color:var(--red);">Inativo</span>`}
          <button class="btn btn-n btn-xs" onclick="editUtil(${u.id})">✏️</button>
          <button class="btn btn-xs" style="background:${u.ativo?"rgba(192,39,45,.15)":"rgba(30,184,122,.15)"};color:${u.ativo?"var(--red)":"var(--green)"};border:none;" onclick="toggleUtil(${u.id})">${u.ativo?"Suspender":"Activar"}</button>
          ${u.nivel!=="admin"?`<button class="btn btn-n btn-xs" style="color:var(--red);" onclick="delUtil(${u.id})">🗑️</button>`:""}
        </div>
      </div>
    </div>`).join("");

  return `
    <div class="ph">
      <div><div class="ph-title">Gestão de Utilizadores</div><div class="ph-sub">${DB.utilizadores.length} utilizador(es) · Apenas admin pode gerir</div></div>
      <button class="btn btn-p" onclick="novoUtil()">+ Novo Utilizador</button>
    </div>
    <div class="alert-w" style="margin-bottom:14px;font-size:12px;">
      🔒 <b>Permissões:</b> <b style="color:var(--red);">Admin</b> — acesso total · <b style="color:var(--gold);">Vendas</b> — sem edição financeira · <b style="color:var(--blue);">Financeiro</b> — sem edição RH · <b style="color:var(--green);">RH</b> — apenas módulo RH · <b style="color:var(--muted);">Visualizador</b> — só leitura
    </div>
    ${rows}`;
};

window.novoUtil = function() {
  openModal("Novo Utilizador", `
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome Completo</label><input class="inp" id="nu-n" placeholder="Nome do utilizador"/></div>
      <div class="fg"><label class="lbl">Nome de Utilizador (login)</label><input class="inp" id="nu-u" placeholder="ex: vendas2"/></div>
      <div class="fg"><label class="lbl">Senha Inicial</label><input class="inp" type="password" id="nu-p" placeholder="mín. 6 caracteres"/></div>
      <div class="fg"><label class="lbl">Nível de Acesso</label>
        <select class="inp" id="nu-nv">
          <option value="vendas">Vendas</option>
          <option value="financeiro">Financeiro</option>
          <option value="rh">RH</option>
          <option value="admin">Administrador</option>
          <option value="viewer">Visualizador (só leitura)</option>
        </select></div>
      <div class="fg"><label class="lbl">Email</label><input class="inp" id="nu-e" placeholder="email@empresa.co.mz"/></div>
      <div class="fg"><label class="lbl">Telefone</label><input class="inp" id="nu-t" placeholder="+258 8X XXX XXXX"/></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarUtil(0)">✔ Criar Utilizador</button>
    </div>`);
};

window.editUtil = function(id) {
  const u = DB.utilizadores.find(x=>x.id===id); if(!u) return;
  openModal("Editar Utilizador — "+u.nome, `
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome</label><input class="inp" id="nu-n" value="${esc(u.nome)}"/></div>
      <div class="fg"><label class="lbl">Utilizador (login)</label><input class="inp" id="nu-u" value="${esc(u.user)}"/></div>
      <div class="fg"><label class="lbl">Nova Senha (deixar vazio para manter)</label><input class="inp" type="password" id="nu-p" placeholder="Nova senha..."/></div>
      <div class="fg"><label class="lbl">Nível</label>
        <select class="inp" id="nu-nv">
          <option value="vendas" ${u.nivel==="vendas"?"selected":""}>Vendas</option>
          <option value="financeiro" ${u.nivel==="financeiro"?"selected":""}>Financeiro</option>
          <option value="rh" ${u.nivel==="rh"?"selected":""}>RH</option>
          <option value="admin" ${u.nivel==="admin"?"selected":""}>Administrador</option>
          <option value="viewer" ${u.nivel==="viewer"?"selected":""}>Visualizador</option>
        </select></div>
      <div class="fg"><label class="lbl">Email</label><input class="inp" id="nu-e" value="${esc(u.email||"")}"/></div>
      <div class="fg"><label class="lbl">Telefone</label><input class="inp" id="nu-t" value="${esc(u.tel||"")}"/></div>
    </div>
    <div class="mfoot">
      <button class="btn btn-n" onclick="closeModal()">Cancelar</button>
      <button class="btn btn-p" onclick="salvarUtil(${id})">✔ Guardar</button>
    </div>`);
};

window.salvarUtil = function(id) {
  const n = v("nu-n"); const user = v("nu-u"); const pass = v("nu-p");
  if(!n||!user) return alert("Nome e utilizador obrigatórios!");
  if(!id && pass.length < 6) return alert("Senha deve ter pelo menos 6 caracteres!");
  if(id) {
    DB.utilizadores = DB.utilizadores.map(u => {
      if(u.id!==id) return u;
      const updated = {...u, nome:n, user, nivel:v("nu-nv"), email:v("nu-e"), tel:v("nu-t")};
      if(pass && pass.length>=6) updated.pass = pass;
      return updated;
    });
    // Also update USERS_LIST for session
    const ul = window.USERS_LIST?.find(x=>x.user===v("nu-u"));
  } else {
    const novo = {id:Date.now(), nome:n, user, pass, nivel:v("nu-nv"), email:v("nu-e"), tel:v("nu-t"), av:n[0].toUpperCase(), ativo:true};
    DB.utilizadores.push(novo);
    // Add to USERS_LIST for this session
    if(window.USERS_LIST) window.USERS_LIST.push(novo);
    if(window.PERMS && !window.PERMS[novo.nivel]) window.PERMS[novo.nivel] = window.PERMS["vendas"]||[];
  }
  addLog((id?"Editou":"Criou")+" utilizador: @"+user);
  saveDB(DB); closeModal(); render("utilizadores-mgr");
};
window.toggleUtil = function(id) {
  DB.utilizadores = DB.utilizadores.map(u=>u.id===id?{...u,ativo:!u.ativo}:u);
  addLog("Toggle utilizador: "+id); saveDB(DB); render("utilizadores-mgr");
};
window.delUtil = function(id) {
  if(!confirm("Eliminar utilizador?")) return;
  DB.utilizadores = DB.utilizadores.filter(u=>u.id!==id);
  addLog("Eliminou utilizador: "+id); saveDB(DB); render("utilizadores-mgr");
};

// ════════════════════════════════════════════════════════════
// PATCH: PROTECT NON-ADMIN FROM EDITING
// Wrap existing edit/del functions with permission check
// ════════════════════════════════════════════════════════════
function adminOnly(fn, name) {
  return function() {
    if(window.CU && window.CU.nivel !== "admin") {
      // Notify
      DB = loadDB();
      DB.logs.push({id:Date.now(), user:window.CU?.user||"?", acao:`TENTATIVA BLOQUEADA: ${name}`, data:new Date().toLocaleString("pt-MZ")});
      saveDB(DB);
      alert("⛔ Sem permissão! Apenas o Administrador pode realizar esta acção.\n\nAcção registada no sistema.");
      return;
    }
    return fn.apply(this, arguments);
  };
}

// Apply protection after existing functions are available
setTimeout(function() {
  // Protect destructive/edit functions for non-admins
  const toProtect = ["delCli","delCot","delVenda","delEst","delObra","delFunc","editCli","editCot","editEst","editFunc","saveCfgEmpresa","saveCfgVisual","saveCfgFiscal","savePg","delPg","editPg","remLogo"];
  toProtect.forEach(fn => {
    if(window[fn]) window[fn] = adminOnly(window[fn], fn);
  });

  // Patch doLogin to also load from DB.utilizadores
  const _origDoLogin = window.doLogin;
  window.doLogin = function() {
    const uInput = document.getElementById("l-user")?.value?.trim();
    const pInput = document.getElementById("l-pass")?.value;
    const dbUsers = (window.loadDB?.() || {}).utilizadores || [];
    const dbUser = dbUsers.find(u => u.user===uInput && u.pass===pInput && u.ativo!==false);
    if(dbUser && window.USERS_LIST && !window.USERS_LIST.find(u=>u.user===dbUser.user)) {
      window.USERS_LIST.push(dbUser);
    }
    _origDoLogin();
  };

  console.log("✅ Permission protection applied");
}, 500);

// ════════════════════════════════════════════════════════════
// NETLIFY DEPLOYMENT GUIDE (shown in config)
// ════════════════════════════════════════════════════════════
window.showNetlifyGuide = function() {
  openModal("🌐 Publicar Online — Guia Netlify", `
    <div style="line-height:1.7;">
      <div class="alert-g" style="margin-bottom:14px;">
        ✅ Com o Netlify pode ter o sistema online em menos de 5 minutos, de forma <b>gratuita</b>, com link próprio.
      </div>
      <div style="display:flex;flex-direction:column;gap:12px;">
        ${[
          ["1️⃣","Fazer download do sistema","Clique em Backup & Download no menu Relatórios → Backup e guarde o ficheiro HTML no seu computador."],
          ["2️⃣","Criar conta no Netlify","Acesse <b>netlify.com</b> → clique em <b>Sign up</b> → registe-se com o seu email (é gratuito)."],
          ["3️⃣","Publicar o sistema","Na página inicial do Netlify, arraste o ficheiro <b>HTML</b> directamente para a página. O sistema vai ficar online automaticamente!"],
          ["4️⃣","O seu link","O Netlify gera um link como: <b style='color:var(--blue)'>onemillion.netlify.app</b>. Pode personalizar para o nome que quiser."],
          ["5️⃣","Domínio próprio (opcional)","Para ter <b>onemillion.co.mz</b>, registe o domínio no IANA/registador moçambicano e aponte para o Netlify."],
          ["6️⃣","Actualizar o sistema","Quando houver uma nova versão, arraste novamente o ficheiro para o Netlify e o link actualiza automaticamente."],
        ].map(([num,title,desc])=>`<div style="background:var(--navy);border-radius:8px;padding:12px 14px;">
          <div style="display:flex;gap:10px;align-items:flex-start;">
            <span style="font-size:20px;flex-shrink:0;">${num}</span>
            <div><div style="font-weight:700;margin-bottom:3px;">${title}</div><div style="color:var(--muted);font-size:12px;">${desc}</div></div>
          </div>
        </div>`).join("")}
      </div>
      <div class="alert-w" style="margin-top:14px;font-size:12px;">
        ⚠️ <b>Nota importante:</b> O ficheiro HTML armazena dados localmente no browser de cada computador. Para sincronizar dados entre vários computadores, é necessário migrar para versão com servidor (backend). Posso ajudá-lo a fazer isso quando estiver pronto.
      </div>
    </div>
    <div class="mfoot">
      <button class="btn btn-p" onclick="exportBackup();closeModal()">📥 Download do Sistema + Fechar</button>
      <button class="btn btn-n" onclick="closeModal()">Fechar</button>
    </div>`,"wide");
};

// Auto-initialize extensions
try { patchSystem(); } catch(e) { console.warn("Extension init:", e); }



// ═══════════════════════════════════════════════════════
// SEARCH BARS + PRODUCT CODE — PATCH
// ═══════════════════════════════════════════════════════

// Override pEstoque to add search + code field display
const _origPEstoque = window.rEstoque || null;

function buildSearchBar(id, placeholder){
  return `<div style="position:relative;margin-bottom:14px;">
    <span style="position:absolute;left:13px;top:50%;transform:translateY(-50%);color:var(--muted);">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
    </span>
    <input class="inp" id="${id}" placeholder="${placeholder}" style="padding-left:42px;" oninput="searchFilter('${id}')"/>
  </div>`;
}

// Universal search filter
window.searchFilter = function(inputId){
  const q = (document.getElementById(inputId)?.value||"").toLowerCase().trim();
  const containers = {
    'sq-est': '#est-list .card',
    'sq-cli': '#cli-list .card',
    'sq-cot': '#cot-list .card',
    'sq-vnd': '#vnd-list .card',
    'sq-rh': '#rh-list .card',
    'sq-fin': '#fin-list .card',
    'sq-doc': '#doc-list .card',
    'sq-obras': '#obras-list .card',
    'sq-forn': '#forn-list .card',
  };
  const sel = containers[inputId];
  if(!sel) return;
  document.querySelectorAll(sel).forEach(el=>{
    const txt = el.textContent.toLowerCase();
    el.style.display = (!q || txt.includes(q)) ? '' : 'none';
  });
};

// Patch rEstoque (estoque page)
const _rEstoque_orig = window.rEstoque;
window.rEstoque = function(){
  DB = loadDB();
  const crit = DB.produtos.filter(p=>p.estoque<=p.min);
  const totalVal = DB.produtos.reduce((s,p)=>s+p.estoque*p.custo,0);
  let rows = DB.produtos.map(p=>{
    const baixo = p.estoque<=p.min;
    const mg = p.preco>0?Math.round(((p.preco-p.custo)/p.preco)*100):0;
    const pct = Math.min((p.estoque/(Math.max(p.min,1)*3))*100,100);
    return`<div class="card" style="margin-bottom:9px;border-left:4px solid ${baixo?'var(--red)':'var(--green)'};">
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;">
        <div style="flex:1;">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;flex-wrap:wrap;">
            ${p.cod?`<span style="font-family:monospace;font-size:10px;background:var(--bg2);border:1px solid var(--border);padding:2px 8px;border-radius:5px;color:var(--gold);">${esc(p.cod)}</span>`:''}
            <span style="font-weight:700;font-size:14px;">${esc(p.nome)}</span>
            <span class="bdg" style="background:rgba(30,50,96,.4);color:var(--silverL);">${esc(p.cat)}</span>
            ${baixo?'<span class="bdg" style="background:rgba(200,39,46,.2);color:var(--red);">⚠️ CRÍTICO</span>':''}
          </div>
          <div style="color:var(--muted);font-size:12px;margin-bottom:7px;">Venda: ${mzn(p.preco)} · Custo: ${mzn(p.custo)} · Margem: ${mg}%${p.loc?' · 📍 '+esc(p.loc):''}</div>
          <div class="pb"><div class="pf" style="width:${Math.min(pct,100)}%;background:${baixo?'var(--red)':'var(--green)'};"></div></div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;">
          <div style="text-align:right;">
            <div style="color:${baixo?'var(--red)':'var(--green)'};font-size:26px;font-weight:900;">${p.estoque}</div>
            <div style="color:var(--muted);font-size:11px;">${esc(p.un)} (mín: ${p.min})</div>
          </div>
          ${isAdmin()?`<div style="display:flex;gap:4px;">
            <button class="btn bn2 btn-ico btn-xs" onclick="editEst(${p.id})">✏️</button>
            <button class="btn bn2 btn-ico btn-xs" style="color:var(--red);" onclick="delEst(${p.id})">🗑️</button>
          </div>`:''}
        </div>
      </div>
    </div>`;
  }).join('');
  return`<div class="ph">
    <div><div class="ph-t">Estoque</div><div class="ph-s">${DB.produtos.length} produtos · Valor: ${mzn(totalVal)} · ${crit.length} críticos</div></div>
    ${isAdmin()?`<button class="btn bp" onclick="novoEst()">+ Novo Produto</button>`:''}
  </div>
  ${crit.length?`<div class="alert alert-r">⚠️ <b>${crit.length} produto(s) críticos:</b> ${crit.map(p=>esc(p.nome)).join(', ')}</div>`:''}
  ${buildSearchBar('sq-est','🔍 Pesquisar por nome, código, categoria, localização...')}
  <div id="est-list">${rows||'<div class="alert alert-w">Sem produtos.</div>'}</div>`;
};

// Patch _fEst to include code field
window.novoEst = function(){ _fEstNew(null); };
window.editEst = function(id){ _fEstNew(DB.produtos.find(p=>p.id===id)); };
window._fEstNew = function(p){
  openModal(p?'Editar Produto':'Novo Produto',`
    <div class="g2">
      <div class="fg cs2"><label class="lbl">Nome do Produto / Serviço</label>
        <input class="inp" id="ef-n" value="${esc(p?.nome||'')}" placeholder="Ex: Chapa MDF Branco 15mm"/></div>
      <div class="fg"><label class="lbl">Código do Produto</label>
        <input class="inp" id="ef-cod" value="${esc(p?.cod||'')}" placeholder="Ex: A00CM1, MDF-15-BR"/></div>
      <div class="fg"><label class="lbl">Categoria</label>
        <input class="inp" id="ef-cat" value="${esc(p?.cat||'')}"/></div>
      <div class="fg"><label class="lbl">Unidade</label>
        <input class="inp" id="ef-u" value="${esc(p?.un||'un')}" placeholder="un, m, kg, ch, saco..."/></div>
      <div class="fg"><label class="lbl">Localização no Estoque</label>
        <input class="inp" id="ef-loc" value="${esc(p?.loc||'')}" placeholder="Ex: Prateleira A1, Galpão B2"/></div>
      <div class="fg"><label class="lbl">Preço de Venda (${DB.cfg.moeda})</label>
        <input class="inp" type="number" id="ef-pv" value="${p?.preco||0}"/></div>
      <div class="fg"><label class="lbl">Custo (${DB.cfg.moeda})</label>
        <input class="inp" type="number" id="ef-pc" value="${p?.custo||0}"/></div>
      <div class="fg"><label class="lbl">Estoque Actual</label>
        <input class="inp" type="number" id="ef-es" value="${p?.estoque||0}"/></div>
      <div class="fg"><label class="lbl">Estoque Mínimo (Alerta)</label>
        <input class="inp" type="number" id="ef-em" value="${p?.min||0}"/></div>
    </div>
    <div class="modal-foot">
      <button class="btn bn2" onclick="closeModal()">Cancelar</button>
      <button class="btn bp" onclick="saveEstNew(${p?.id||0})">✔ Guardar</button>
    </div>`,'',true);
};
window.saveEstNew = function(id){
  const n=document.getElementById('ef-n')?.value?.trim();
  if(!n)return alert('Nome obrigatório!');
  const o={id:id||Date.now(),
    nome:n,
    cod:document.getElementById('ef-cod')?.value||'',
    cat:document.getElementById('ef-cat')?.value||'',
    un:document.getElementById('ef-u')?.value||'un',
    loc:document.getElementById('ef-loc')?.value||'',
    preco:Number(document.getElementById('ef-pv')?.value||0),
    custo:Number(document.getElementById('ef-pc')?.value||0),
    estoque:Number(document.getElementById('ef-es')?.value||0),
    min:Number(document.getElementById('ef-em')?.value||0)
  };
  if(id) DB.produtos=DB.produtos.map(p=>p.id===id?o:p);
  else DB.produtos.push(o);
  addLog((id?'Editou':'Adicionou')+' produto: '+n+' ['+o.cod+']');
  saveDB(DB);closeModal();
  notify('✅ Produto '+n+' guardado!');
  goTo('estoque');
};

// Patch rClientes with search
const _rClientes_orig = window.rClientes;
window.rClientes = function(){
  DB = loadDB();
  const cards = DB.clientes.map(c=>{
    const nc=DB.cotacoes.filter(x=>x.cliId===c.id).length;
    const nv=DB.vendas.filter(x=>x.cliId===c.id).length;
    const div=DB.vendas.filter(x=>x.cliId===c.id).reduce((s,vv)=>s+(vv.total-(vv.pago||0)),0);
    return`<div class="card card-h" onclick="verCli(${c.id})" style="cursor:pointer;margin-bottom:12px;">
      <div style="display:flex;gap:12px;align-items:center;margin-bottom:12px;">
        <div style="width:44px;height:44px;background:var(--grad-red);border-radius:12px;display:flex;align-items:center;justify-content:center;color:#fff;font-weight:900;font-size:18px;flex-shrink:0;">${c.nome[0]}</div>
        <div style="flex:1;min-width:0;">
          <div style="font-weight:800;font-size:14px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;">${esc(c.nome)}</div>
          <div style="color:var(--muted);font-size:11px;">${c.tipo==='empresa'?'🏢 Empresa':'👤 Particular'}${c.nuit?' · NUIT: '+esc(c.nuit):''}</div>
        </div>
        <span class="bdg" style="background:rgba(16,184,112,.15);color:var(--green);">${c.status||'ativo'}</span>
      </div>
      <div style="font-size:12px;color:var(--muted);display:flex;flex-direction:column;gap:3px;margin-bottom:12px;">
        <div>📞 ${esc(c.tel)}</div>
        ${c.email?`<div>✉️ ${esc(c.email)}</div>`:''}
        ${c.end?`<div>📍 ${esc(c.end)}</div>`:''}
      </div>
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:12px;">
        ${[['Cotações',nc,'var(--blue)'],['Vendas',nv,'var(--green)'],['Dívida',mzn(div),div>0?'var(--red)':'var(--muted)']].map(([l,vv,col])=>`<div style="background:var(--bg2);border-radius:10px;padding:8px;text-align:center;"><div style="color:${col};font-weight:800;font-size:12px;">${vv}</div><div style="color:var(--muted);font-size:10px;">${l}</div></div>`).join('')}
      </div>
      <div style="display:flex;justify-content:flex-end;gap:5px;" onclick="event.stopPropagation()">
        <a href="https://wa.me/${(c.tel||'').replace(/\D/g,'')}" target="_blank" class="btn bg2 btn-xs">💬 WA</a>
        ${isAdmin()?`<button class="btn bn2 btn-xs" onclick="editCli(${c.id})">✏️</button>
        <button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delCli(${c.id})">🗑️</button>`:''}
      </div>
    </div>`;
  }).join('');
  return`<div class="ph">
    <div><div class="ph-t">CRM — Clientes</div><div class="ph-s">${DB.clientes.length} clientes · ${DB.clientes.filter(c=>c.status==='ativo').length} activos</div></div>
    <button class="btn bp" onclick="novoCli()">+ Novo Cliente</button>
  </div>
  ${buildSearchBar('sq-cli','🔍 Pesquisar por nome, email, telefone, cidade...')}
  <div id="cli-list">${cards||'<div class="alert alert-w">Sem clientes.</div>'}</div>`;
};

// Patch rCotacoes with search
const _cFiltro_patch = 'todos';
window._cFi = window._cFi || 'todos';
const _rCotacoes_orig = window.rCotacoes;
window.rCotacoes = function(){
  DB = loadDB();
  const fts=['todos','pendente','enviado','aprovado','rejeitado'];
  const tabs=`<div class="tabs">${fts.map(f=>`<button class="tab${window._cFi===f?' on':''}" onclick="_setCF('${f}')">${f==='todos'?'Todas':SI(f).l}</button>`).join('')}</div>`;
  const its=DB.cotacoes.filter(c=>window._cFi==='todos'||c.status===window._cFi);
  const stC={pendente:'#7a90b0',enviado:'#3a8ef8',aprovado:'#10b870',rejeitado:'#c8272e'};
  const cards=[...its].reverse().map(c=>{
    const si=SI(c.status);
    const iDesc=c.itens.slice(0,2).map(i=>esc(i.desc)).join(' · ')+(c.itens.length>2?` +${c.itens.length-2}`:'');
    return`<div class="card" style="margin-bottom:10px;border-left:3px solid ${si.c};">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;">
        <div style="flex:1;">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;flex-wrap:wrap;">
            <span style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(c.num)}</span>
            <span style="font-weight:800;font-size:14px;">${esc(c.cliNome)}</span>
            <span class="bdg" style="background:${si.c}20;color:${si.c};">${si.l}</span>
          </div>
          <div style="color:var(--muted);font-size:12px;margin-bottom:4px;">📅 ${c.data} · Válida: ${c.val||'—'} · ${c.itens.length} item(ns)</div>
          <div style="color:var(--silverL);font-size:12px;">${iDesc}</div>
        </div>
        <div style="text-align:right;">
          <div style="font-size:20px;font-weight:900;color:var(--gold);margin-bottom:8px;">${mzn(c.total)}</div>
          <div style="display:flex;gap:4px;flex-wrap:wrap;justify-content:flex-end;">
            <button class="btn bn2 btn-xs" onclick="gerarPDF(DB.cotacoes.find(x=>x.id===${c.id}),'cot')">📄 PDF</button>
            <button class="btn bg2 btn-xs" onclick="sendWA(${c.id},'cot')">💬</button>
            ${c.status!=='aprovado'&&c.status!=='rejeitado'?`<button class="btn bb btn-xs" onclick="cvtCot(${c.id})">→ Venda</button>`:''}
            ${isAdmin()?`<button class="btn bn2 btn-xs" onclick="editCot(${c.id})">✏️</button>
            <button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delCot(${c.id})">🗑️</button>`:''}
          </div>
          ${['pendente','enviado'].includes(c.status)&&isAdmin()?`<div style="display:flex;gap:4px;justify-content:flex-end;margin-top:5px;">
            <button class="btn btn-xs" style="background:rgba(16,184,112,.15);color:var(--green);border:none;" onclick="stCot(${c.id},'aprovado')">✓ Aprovar</button>
            <button class="btn btn-xs" style="background:rgba(200,39,46,.15);color:var(--red);border:none;" onclick="stCot(${c.id},'rejeitado')">✗ Rejeitar</button>
          </div>`:''}
        </div>
      </div>
    </div>`;
  }).join('');
  return`<div class="ph">
    <div><div class="ph-t">Cotações</div><div class="ph-s">${DB.cotacoes.length} cotações · ${mzn(DB.cotacoes.reduce((s,c)=>s+c.total,0))} pipeline</div></div>
    <button class="btn bp" onclick="goTo('cotacoes-nova')">+ Nova Cotação</button>
  </div>
  ${tabs}
  ${buildSearchBar('sq-cot','🔍 Pesquisar por cliente, número, item...')}
  <div id="cot-list">${cards||'<div class="alert alert-w">Sem cotações.</div>'}</div>`;
};

// Patch rVendas with search
const _rVendas_orig = window.rVendas;
window.rVendas = function(){
  DB = loadDB();
  const tV=DB.vendas.reduce((s,vv)=>s+vv.total,0);
  const tP=DB.vendas.reduce((s,vv)=>s+(vv.pago||0),0);
  let rows=[...DB.vendas].reverse().map(vd=>`<div class="card" style="margin-bottom:9px;border-left:3px solid ${vd.status==='pago'?'var(--green)':vd.status==='parcial'?'var(--gold)':'var(--muted)'};">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;">
      <div style="flex:1;">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;flex-wrap:wrap;">
          <span style="font-family:monospace;font-size:11px;color:var(--muted);">${esc(vd.fatNum||vd.num)}</span>
          <span style="font-weight:800;font-size:14px;">${esc(vd.cliNome)}</span>
          <span class="bdg" style="background:${SI(vd.status).c}20;color:${SI(vd.status).c};">${SI(vd.status).l}</span>
        </div>
        <div style="color:var(--muted);font-size:12px;">📅 ${vd.data}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:2px;">${(vd.itens||[]).slice(0,2).map(i=>esc(i.desc)).join(' · ')}</div>
      </div>
      <div style="text-align:right;">
        <div style="font-size:18px;font-weight:900;color:var(--gold);">${mzn(vd.total)}</div>
        <div style="color:var(--green);font-size:12px;">Pago: ${mzn(vd.pago||0)}</div>
        <div style="display:flex;gap:4px;justify-content:flex-end;margin-top:8px;flex-wrap:wrap;">
          <button class="btn bn2 btn-xs" onclick="gerarPDF(DB.vendas.find(x=>x.id===${vd.id}),'vnd')">📄 FAT</button>
          <button class="btn bg2 btn-xs" onclick="sendWA(${vd.id},'vnd')">💬</button>
          <button class="btn bb btn-xs" onclick="gerarReciboVenda(${vd.id})">🧾 Recibo</button>
          <button class="btn bgold btn-xs" onclick="modalPagVenda(${vd.id})">💰 Pagar</button>
          ${isAdmin()?`<button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delVenda(${vd.id})">🗑️</button>`:''}
        </div>
      </div>
    </div>
  </div>`).join('');
  return`<div class="ph">
    <div><div class="ph-t">Vendas & Faturas</div><div class="ph-s">${DB.vendas.length} vendas · Faturado ${mzn(tV)} · Recebido ${mzn(tP)}</div></div>
    <button class="btn bp" onclick="goTo('nova-venda')">+ Nova Venda</button>
  </div>
  <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:18px;">
    <div class="card" style="border-left:3px solid var(--gold);"><div class="kpi-l">Faturado</div><div style="font-size:20px;font-weight:900;color:var(--gold);">${mzn(tV)}</div></div>
    <div class="card" style="border-left:3px solid var(--green);"><div class="kpi-l">Recebido</div><div style="font-size:20px;font-weight:900;color:var(--green);">${mzn(tP)}</div></div>
    <div class="card" style="border-left:3px solid var(--red);"><div class="kpi-l">A Receber</div><div style="font-size:20px;font-weight:900;color:var(--red);">${mzn(tV-tP)}</div></div>
  </div>
  ${buildSearchBar('sq-vnd','🔍 Pesquisar por cliente, nº fatura, produto...')}
  <div id="vnd-list">${rows||'<div class="alert alert-w">Sem vendas.</div>'}</div>`;
};

// Add search in nova-venda product selector (already has dropdown, add text search)
// Patch the product selector in new sale to be searchable
const _nvSearch = `
window.filterNvProd = function(){
  const q = (document.getElementById('nv-prod-search')?.value||'').toLowerCase();
  document.querySelectorAll('#nv-prod-list option').forEach(o=>{
    o.style.display = (!q || o.text.toLowerCase().includes(q)) ? '' : 'none';
  });
};
`;

// Patch rRH with search
const _rRH_orig = window.rRH;

// Add search to obras
const _rObras_orig = window.rObras;
window.rObras = function(){
  DB = loadDB();
  let cards = DB.obras.map(o=>`<div class="card" style="margin-bottom:14px;border-left:4px solid var(--blue);">
    <div style="display:flex;justify-content:space-between;margin-bottom:12px;flex-wrap:wrap;gap:8px;">
      <div>
        <div style="font-weight:800;font-size:16px;">${esc(o.nome)}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:3px;">👤 ${esc(o.cliNome)} · 👷 ${esc(o.resp||'')}</div>
        <div style="color:var(--muted);font-size:12px;">📅 ${o.inicio||''} → ${o.fim||''}</div>
      </div>
      <div style="text-align:right;">
        <div style="font-size:20px;font-weight:900;color:var(--blue);">${mzn(o.valor)}</div>
        <span class="bdg" style="background:${SI(o.status).c}20;color:${SI(o.status).c};">${SI(o.status).l}</span>
      </div>
    </div>
    <div style="margin-bottom:10px;">
      <div style="display:flex;justify-content:space-between;margin-bottom:6px;">
        <span style="color:var(--muted);font-size:12px;">Progresso</span>
        <span style="color:var(--blue);font-weight:800;">${o.prog}%</span>
      </div>
      <div class="pb"><div class="pf" style="width:${o.prog}%;background:var(--blue);"></div></div>
    </div>
    ${(o.tarefas||[]).length?`<div style="margin-bottom:10px;">${o.tarefas.map((t,i)=>`<div style="display:flex;align-items:center;gap:10px;padding:5px 0;border-bottom:1px solid var(--border);">
      <div style="flex:1;font-size:12px;">${esc(t.desc)}</div>
      <div style="min-width:80px;"><div class="pb"><div class="pf" style="width:${t.pct}%;background:var(--green);"></div></div></div>
      <span style="color:var(--green);font-size:11px;font-weight:800;min-width:32px;">${t.pct}%</span>
      ${isAdmin()?`<input type="range" min="0" max="100" value="${t.pct}" oninput="updTarefa(${o.id},${i},this.value)" style="width:70px;accent-color:var(--green);"/>`:''}</div>`).join('')}</div>`:''}
    <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
      ${isAdmin()?`<input type="range" min="0" max="100" value="${o.prog}" oninput="updObra(${o.id},this.value)" style="flex:1;accent-color:var(--blue);min-width:120px;"/>
      <button class="btn bn2 btn-xs" onclick="addTarefa(${o.id})">+ Tarefa</button>
      <button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delObra(${o.id})">🗑️</button>`:''}
    </div>
  </div>`).join('');
  return`<div class="ph">
    <div><div class="ph-t">Obras</div><div class="ph-s">${DB.obras.length} obra(s) registada(s)</div></div>
    ${isAdmin()?`<button class="btn bp" onclick="novaObra()">+ Nova Obra</button>`:''}
  </div>
  ${buildSearchBar('sq-obras','🔍 Pesquisar por nome, cliente, responsável...')}
  <div id="obras-list">${cards||'<div class="alert alert-w">Sem obras.</div>'}</div>`;
};

// Add search to financeiro
const _rFin_orig = window.rFinanceiro;
window.rFinanceiro = function(){
  DB = loadDB();
  const tR=DB.financeiro.receitas.reduce((s,r)=>s+r.valor,0);
  const tD=DB.financeiro.despesas.reduce((s,d)=>s+d.valor,0);const sl=tR-tD;
  const lista=window._fAba==='receitas'?DB.financeiro.receitas:DB.financeiro.despesas;
  const rows=[...lista].reverse().map(it=>`<div class="card" style="margin-bottom:8px;">
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
      <div>
        <div style="font-weight:700;font-size:14px;">${esc(it.desc)}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:3px;">${it.data} · ${esc(it.cat)}${it.ref?' · Ref: '+esc(it.ref):''}</div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;">
        <div style="font-size:19px;font-weight:900;color:${window._fAba==='receitas'?'var(--green)':'var(--red)'};">${mzn(it.valor)}</div>
        <span class="bdg" style="background:${SI(it.status).c}20;color:${SI(it.status).c};">${SI(it.status).l}</span>
        ${isAdmin()?`<button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delLanc('${window._fAba}',${it.id})">🗑️</button>`:''}
      </div>
    </div>
  </div>`).join('');
  return`<div class="ph"><div class="ph-t">Financeiro</div></div>
  <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:18px;">
    <div class="card" style="border-left:3px solid var(--green);"><div class="kpi-l">Receitas</div><div style="font-size:20px;font-weight:900;color:var(--green);">${mzn(tR)}</div></div>
    <div class="card" style="border-left:3px solid var(--red);"><div class="kpi-l">Despesas</div><div style="font-size:20px;font-weight:900;color:var(--red);">${mzn(tD)}</div></div>
    <div class="card" style="border-left:3px solid ${sl>=0?'var(--gold)':'var(--red)'};"><div class="kpi-l">Saldo</div><div style="font-size:20px;font-weight:900;color:${sl>=0?'var(--gold)':'var(--red)'};">${mzn(sl)}</div></div>
  </div>
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;flex-wrap:wrap;gap:8px;">
    <div class="tabs" style="margin:0;">
      <button class="tab${window._fAba==='receitas'?' on':''}" onclick="window._fAba='receitas';goTo('financeiro')">Receitas</button>
      <button class="tab${window._fAba==='despesas'?' on':''}" onclick="window._fAba='despesas';goTo('financeiro')">Despesas</button>
    </div>
    <button class="btn bp" onclick="novoLanc()">+ Novo Lançamento</button>
  </div>
  ${buildSearchBar('sq-fin','🔍 Pesquisar por descrição, categoria, referência...')}
  <div id="fin-list">${rows||'<div class="alert alert-w">Sem lançamentos.</div>'}</div>`;
};

// Add search to RH funcionarios
const _rRH_patch = window.rRH;
window.rRH = function(){
  const result = _rRH_patch ? _rRH_patch() : '<div>RH</div>';
  // inject search bar after ph div
  return result.replace(
    '<div style="display:flex;justify-content:flex-end;margin-bottom:12px;">',
    buildSearchBar('sq-rh','🔍 Pesquisar por nome, cargo, departamento...') +
    '<div style="display:flex;justify-content:flex-end;margin-bottom:12px;">'
  );
};

// Patch documentos with search
const _rDoc_orig = window.rDocumentos;
window.rDocumentos = function(){
  const result = _rDoc_orig ? _rDoc_orig() : '<div>Docs</div>';
  return result.replace('</div>\n  <div class="tabs">', buildSearchBar('sq-doc','🔍 Pesquisar documentos...') + '</div>\n  <div class="tabs">');
};

console.log('✅ Search bars + Product Code patches applied!');


// ══════════════════════════════════════════════════════════════
// PATCH v5.1 — PESQUISA GLOBAL + DOCUMENTOS + RECIBOS + GUIAS + MAXCUT
// ══════════════════════════════════════════════════════════════

// ─── PESQUISA GLOBAL DE ESTOQUE ──────────────────────────────
window.rEstoque = function(){
  DB = loadDB();
  const crit = DB.produtos.filter(p => p.estoque <= p.min);
  const totalVal = DB.produtos.reduce((s,p) => s + p.estoque * p.custo, 0);

  function renderProdutos(lista){
    if(!lista.length) return '<div class="alert alert-w">Nenhum produto encontrado.</div>';
    return lista.map(p => {
      const baixo = p.estoque <= p.min;
      const mg = p.preco > 0 ? Math.round(((p.preco - p.custo) / p.preco) * 100) : 0;
      const pct = Math.min((p.estoque / (Math.max(p.min,1)*3))*100, 100);
      return `<div class="card" style="margin-bottom:9px;border-left:4px solid ${baixo?'var(--red)':'var(--green)'};">
        <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;">
          <div style="flex:1;">
            <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;flex-wrap:wrap;">
              ${p.cod?`<span style="font-family:monospace;font-size:10px;background:var(--bg2);border:1px solid var(--border);padding:2px 8px;border-radius:5px;color:var(--gold);letter-spacing:1px;">${esc(p.cod)}</span>`:''}
              <span style="font-weight:800;font-size:14px;">${esc(p.nome)}</span>
              <span class="bdg" style="background:rgba(58,142,248,.15);color:var(--blue);">${esc(p.cat||'—')}</span>
              ${baixo?'<span class="bdg" style="background:rgba(200,39,46,.2);color:var(--red);">⚠️ CRÍTICO</span>':''}
            </div>
            <div style="color:var(--muted);font-size:12px;margin-bottom:7px;">
              Venda: <b style="color:var(--text);">${mzn(p.preco)}</b> · Custo: ${mzn(p.custo)} · Margem: <b style="color:var(--green);">${mg}%</b>${p.loc?' · 📍 '+esc(p.loc):''}
            </div>
            <div class="pb"><div class="pf" style="width:${Math.min(pct,100)}%;background:${baixo?'var(--red)':'var(--green)'};"></div></div>
          </div>
          <div style="display:flex;align-items:center;gap:12px;">
            <div style="text-align:right;">
              <div style="color:${baixo?'var(--red)':'var(--green)'};font-size:28px;font-weight:900;line-height:1;">${p.estoque}</div>
              <div style="color:var(--muted);font-size:11px;">${esc(p.un)} (mín: ${p.min})</div>
            </div>
            ${isAdmin()?`<div style="display:flex;gap:4px;">
              <button class="btn bn2 btn-xs" onclick="editEst(${p.id})">✏️</button>
              <button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delEst(${p.id})">🗑️</button>
            </div>`:''}
          </div>
        </div>
      </div>`;
    }).join('');
  }

  setTimeout(()=>{
    const inp = document.getElementById('est-search');
    if(inp){
      inp.addEventListener('input', function(){
        const q = this.value.toLowerCase().trim();
        const filtered = q ? DB.produtos.filter(p =>
          p.nome.toLowerCase().includes(q) ||
          (p.cod||'').toLowerCase().includes(q) ||
          (p.cat||'').toLowerCase().includes(q) ||
          (p.loc||'').toLowerCase().includes(q) ||
          (p.un||'').toLowerCase().includes(q)
        ) : DB.produtos;
        document.getElementById('est-results').innerHTML = renderProdutos(filtered);
        document.getElementById('est-count').textContent = filtered.length + ' produto(s)';
      });
    }
  }, 80);

  return `<div class="ph">
    <div><div class="ph-t">Estoque</div><div class="ph-s">${DB.produtos.length} produtos · Valor: ${mzn(totalVal)} · ${crit.length} críticos</div></div>
    ${isAdmin()?`<button class="btn bp" onclick="novoEst()">+ Novo Produto</button>`:''}
  </div>
  ${crit.length?`<div class="alert alert-r">⚠️ <b>${crit.length} produto(s) críticos:</b> ${crit.map(p=>esc(p.nome)).join(', ')}</div>`:''}
  <div style="background:var(--card2);border:1px solid var(--border2);border-radius:14px;padding:14px;margin-bottom:16px;">
    <div style="font-size:12px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:10px;">🔍 Pesquisa Global de Estoque</div>
    <div style="position:relative;">
      <span style="position:absolute;left:13px;top:50%;transform:translateY(-50%);color:var(--muted);">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      </span>
      <input class="inp" id="est-search" placeholder="Pesquisar por nome, código (ex: A00CM1), categoria, localização..." style="padding-left:42px;font-size:14px;"/>
    </div>
    <div style="display:flex;gap:8px;margin-top:10px;flex-wrap:wrap;">
      ${[...new Set(DB.produtos.map(p=>p.cat).filter(Boolean))].map(cat=>
        `<button onclick="document.getElementById('est-search').value='${cat}';document.getElementById('est-search').dispatchEvent(new Event('input'));" 
         style="background:rgba(58,142,248,.1);color:var(--blue);border:1px solid rgba(58,142,248,.2);border-radius:20px;padding:4px 12px;font-size:11px;font-weight:700;cursor:pointer;">${cat}</button>`
      ).join('')}
      <button onclick="document.getElementById('est-search').value='';document.getElementById('est-search').dispatchEvent(new Event('input'));" 
       style="background:rgba(200,39,46,.1);color:var(--red);border:1px solid rgba(200,39,46,.2);border-radius:20px;padding:4px 12px;font-size:11px;font-weight:700;cursor:pointer;">✕ Limpar</button>
    </div>
  </div>
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;">
    <span id="est-count" style="color:var(--muted);font-size:12px;">${DB.produtos.length} produto(s)</span>
  </div>
  <div id="est-results">${renderProdutos(DB.produtos)}</div>`;
};

// ─── PRODUTO: NOVO/EDITAR COM CÓDIGO ─────────────────────────
window.novoEst = function(){ _fEstV2(null); };
window.editEst = function(id){ _fEstV2(DB.produtos.find(p=>p.id===id)); };
window._fEstV2 = function(p){
  openModal(p?'Editar Produto':'Novo Produto', `
    <div class="g2">
      <div class="fg cs2">
        <label class="lbl">Nome do Produto / Serviço</label>
        <input class="inp" id="ef-n" value="${esc(p?.nome||'')}" placeholder="Ex: Chapa MDF Branco 15mm 2750x1830"/>
      </div>
      <div class="fg">
        <label class="lbl">Código do Produto</label>
        <input class="inp" id="ef-cod" value="${esc(p?.cod||'')}" placeholder="Ex: A00CM1, MDF-15-BR"/>
        <div style="color:var(--muted);font-size:10px;margin-top:4px;">Código único para identificação rápida no stock</div>
      </div>
      <div class="fg">
        <label class="lbl">Categoria</label>
        <input class="inp" id="ef-cat" value="${esc(p?.cat||'')}" placeholder="Chapas, Ferragens, Construção..."/>
      </div>
      <div class="fg">
        <label class="lbl">Unidade</label>
        <input class="inp" id="ef-u" value="${esc(p?.un||'un')}" placeholder="un, m, kg, ch, saco, m²..."/>
      </div>
      <div class="fg">
        <label class="lbl">Localização no Estoque</label>
        <input class="inp" id="ef-loc" value="${esc(p?.loc||'')}" placeholder="Ex: Prateleira A1, Galpão B2"/>
      </div>
      <div class="fg">
        <label class="lbl">Preço de Venda (${DB.cfg.moeda})</label>
        <input class="inp" type="number" id="ef-pv" value="${p?.preco||0}" min="0"/>
      </div>
      <div class="fg">
        <label class="lbl">Custo (${DB.cfg.moeda})</label>
        <input class="inp" type="number" id="ef-pc" value="${p?.custo||0}" min="0"/>
      </div>
      <div class="fg">
        <label class="lbl">Estoque Actual</label>
        <input class="inp" type="number" id="ef-es" value="${p?.estoque||0}" min="0"/>
      </div>
      <div class="fg">
        <label class="lbl">Estoque Mínimo (Alerta)</label>
        <input class="inp" type="number" id="ef-em" value="${p?.min||0}" min="0"/>
      </div>
    </div>
    <div class="modal-foot">
      <button class="btn bn2" onclick="closeModal()">Cancelar</button>
      <button class="btn bp" onclick="saveEstV2(${p?.id||0})">✔ Guardar Produto</button>
    </div>
  `, '', true);
};
window.saveEstV2 = function(id){
  const n = document.getElementById('ef-n')?.value?.trim();
  if(!n) return alert('Nome obrigatório!');
  const o = {
    id: id||Date.now(), nome:n,
    cod: document.getElementById('ef-cod')?.value?.trim()||'',
    cat: document.getElementById('ef-cat')?.value?.trim()||'',
    un: document.getElementById('ef-u')?.value?.trim()||'un',
    loc: document.getElementById('ef-loc')?.value?.trim()||'',
    preco: Number(document.getElementById('ef-pv')?.value||0),
    custo: Number(document.getElementById('ef-pc')?.value||0),
    estoque: Number(document.getElementById('ef-es')?.value||0),
    min: Number(document.getElementById('ef-em')?.value||0),
  };
  if(id) DB.produtos = DB.produtos.map(p=>p.id===id?o:p);
  else DB.produtos.push(o);
  addLog((id?'Editou':'Adicionou')+' produto: '+n+(o.cod?' ['+o.cod+']':''));
  saveDB(DB); closeModal();
  const t=document.createElement('div');t.className='toast';t.style.cssText='position:fixed;top:20px;right:20px;background:var(--card);border:1px solid var(--border2);border-radius:14px;padding:14px 18px;font-size:13px;font-weight:600;z-index:9999;box-shadow:0 8px 30px rgba(0,0,0,.6);';
  t.innerHTML='✅ Produto <b>'+n+'</b> guardado!';document.body.appendChild(t);setTimeout(()=>t.remove(),3000);
  goTo('estoque');
};

// ─── MÓDULO DOCUMENTOS ───────────────────────────────────────
window._docAba = window._docAba || 'docs';

window.rDocumentos = function(){
  DB = loadDB();
  if(!DB.documentos) DB.documentos = [];
  if(!DB.recibos) DB.recibos = [];
  if(!DB.guias) DB.guias = [];

  const abas = [['docs','📄 Documentos'],['recibos','🧾 Recibos'],['guias','🚚 Guias de Entrega']];
  const tabs = `<div class="tabs">${abas.map(([id,l])=>`<button class="tab${window._docAba===id?' on':''}" onclick="window._docAba='${id}';goTo('documentos')">${l}</button>`).join('')}</div>`;

  let content = '';
  if(window._docAba === 'docs') content = _renderDocs();
  else if(window._docAba === 'recibos') content = _renderRecibosDoc();
  else content = _renderGuias();

  return `<div class="ph">
    <div><div class="ph-t">Documentos Comerciais</div></div>
    <div style="display:flex;gap:8px;flex-wrap:wrap;">
      ${window._docAba==='docs'?`<button class="btn bp" onclick="novoDoc()">+ Novo Documento</button>`:''}
      ${window._docAba==='recibos'?`<button class="btn bp" onclick="novoRecibo()">+ Emitir Recibo</button>`:''}
      ${window._docAba==='guias'?`<button class="btn bp" onclick="novaGuia()">+ Guia de Entrega</button>`:''}
    </div>
  </div>
  ${tabs}${content}`;
};

function _renderDocs(){
  DB = loadDB();
  if(!DB.documentos) DB.documentos = [];
  const rows = [...DB.documentos].reverse().map(d=>`<div class="card" style="margin-bottom:9px;">
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
      <div>
        <div style="font-weight:700;font-size:14px;">📄 ${esc(d.titulo)}</div>
        <div style="color:var(--muted);font-size:12px;margin-top:3px;">${d.data} · ${esc(d.tipo||'Documento')}</div>
      </div>
      <div style="display:flex;gap:5px;">
        <button class="btn bb btn-xs" onclick="verDoc(${d.id})">👁️ Ver</button>
        <button class="btn bn2 btn-xs" onclick="editarDoc(${d.id})">✏️ Editar</button>
        <button class="btn bp btn-xs" onclick="imprimirDoc(${d.id})">🖨️ PDF</button>
        ${isAdmin()?`<button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delDoc(${d.id})">🗑️</button>`:''}
      </div>
    </div>
  </div>`).join('');
  return rows || '<div class="alert alert-w">Sem documentos. Clique em "+ Novo Documento" para criar.</div>';
}

window.novoDoc = function(id){
  const d = id ? DB.documentos.find(x=>x.id===id) : null;
  openModal(d?'Editar Documento':'Novo Documento', `
    <div class="g2">
      <div class="fg cs2">
        <label class="lbl">Título do Documento</label>
        <input class="inp" id="nd-titulo" value="${esc(d?.titulo||'')}" placeholder="Ex: Proposta Comercial, Carta, Comunicado..."/>
      </div>
      <div class="fg">
        <label class="lbl">Tipo</label>
        <select class="inp" id="nd-tipo">
          <option ${d?.tipo==='Carta'?'selected':''}>Carta</option>
          <option ${d?.tipo==='Proposta'?'selected':''}>Proposta</option>
          <option ${d?.tipo==='Comunicado'?'selected':''}>Comunicado</option>
          <option ${d?.tipo==='Contrato'?'selected':''}>Contrato</option>
          <option ${d?.tipo==='Relatório'?'selected':''}>Relatório</option>
          <option ${d?.tipo==='Outro'?'selected':''}>Outro</option>
        </select>
      </div>
      <div class="fg">
        <label class="lbl">Para (Destinatário)</label>
        <input class="inp" id="nd-para" value="${esc(d?.para||'')}" placeholder="Nome / Empresa"/>
      </div>
      <div class="fg">
        <label class="lbl">Data</label>
        <input class="inp" type="date" id="nd-data" value="${d?.data||hoje()}"/>
      </div>
    </div>
    <div class="fg" style="margin-top:4px;">
      <label class="lbl">Saudação</label>
      <input class="inp" id="nd-sau" value="${esc(d?.saudacao||'Exmo(a). Sr(a),')}" />
    </div>
    <div class="fg">
      <label class="lbl">Corpo do Documento</label>
      <textarea class="inp" id="nd-corpo" style="height:180px;resize:vertical;font-size:13px;line-height:1.6;" placeholder="Escreva o conteúdo do documento aqui...">${esc(d?.corpo||'')}</textarea>
    </div>
    <div class="fg">
      <label class="lbl">Fecho</label>
      <input class="inp" id="nd-fecho" value="${esc(d?.fecho||'Com os melhores cumprimentos,')}" />
    </div>
    <div class="fg">
      <label class="lbl">Observações</label>
      <input class="inp" id="nd-obs" value="${esc(d?.obs||'')}" placeholder="Notas adicionais..."/>
    </div>
    <div class="modal-foot">
      <button class="btn bn2" onclick="closeModal()">Cancelar</button>
      <button class="btn bg2" onclick="saveDocPrev(${d?.id||0})">👁️ Guardar & Pré-visualizar</button>
      <button class="btn bp" onclick="saveDoc(${d?.id||0})">✔ Guardar</button>
    </div>
  `, 'wide', false);
};

window.editarDoc = function(id){ novoDoc(id); };

window.saveDoc = function(id){
  const titulo = document.getElementById('nd-titulo')?.value?.trim();
  if(!titulo) return alert('Título obrigatório!');
  const obj = {
    id: id||Date.now(), titulo,
    tipo: document.getElementById('nd-tipo')?.value||'Outro',
    para: document.getElementById('nd-para')?.value||'',
    data: document.getElementById('nd-data')?.value||hoje(),
    saudacao: document.getElementById('nd-sau')?.value||'',
    corpo: document.getElementById('nd-corpo')?.value||'',
    fecho: document.getElementById('nd-fecho')?.value||'',
    obs: document.getElementById('nd-obs')?.value||'',
  };
  if(!DB.documentos) DB.documentos = [];
  if(id) DB.documentos = DB.documentos.map(d=>d.id===id?obj:d);
  else DB.documentos.push(obj);
  addLog((id?'Editou':'Criou')+' documento: '+titulo);
  saveDB(DB); closeModal(); goTo('documentos');
};

window.saveDocPrev = function(id){
  saveDoc(id);
  setTimeout(()=>{
    const docs = DB.documentos;
    const last = docs[docs.length-1];
    if(last) imprimirDoc(last.id);
  }, 400);
};

window.verDoc = function(id){
  const d = DB.documentos.find(x=>x.id===id); if(!d) return;
  imprimirDoc(id);
};

window.imprimirDoc = function(id){
  const d = DB.documentos.find(x=>x.id===id); if(!d) return;
  const cfg = DB.cfg;
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:55px;object-fit:contain;" alt="Logo"/>`:'';
  openModal('Documento — '+d.titulo, `
    <div class="pdf-wrap" id="pdf-content" style="background:#fff;color:#111;border-radius:10px;padding:36px;font-family:system-ui,sans-serif;font-size:13px;line-height:1.7;">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;padding-bottom:16px;border-bottom:3px solid #c8272e;">
        <div>
          ${logoH?`<div style="margin-bottom:8px;">${logoH}</div>`:''}
          <div style="font-weight:900;font-size:18px;color:#0a0f2e;">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan||'')}<br/>${esc(cfg.end||'')} · ${esc(cfg.cidade)}, ${esc(cfg.pais)}<br/>${esc(cfg.tel)} · ${esc(cfg.email)}</div>
        </div>
        <div style="text-align:right;">
          <div style="background:#c8272e;color:#fff;padding:5px 14px;border-radius:6px;font-weight:800;font-size:13px;display:inline-block;">${esc(d.tipo||'DOCUMENTO')}</div>
          <div style="font-size:12px;color:#777;margin-top:5px;">${esc(cfg.cidade)}, ${d.data}</div>
        </div>
      </div>
      ${d.para?`<div style="margin-bottom:14px;"><b>A/C: ${esc(d.para)}</b></div>`:''}
      ${d.saudacao?`<div style="margin-bottom:16px;font-weight:600;">${esc(d.saudacao)}</div>`:''}
      <div style="white-space:pre-wrap;line-height:1.8;color:#222;margin-bottom:24px;">${esc(d.corpo)}</div>
      ${d.fecho?`<div style="margin-bottom:32px;">${esc(d.fecho)}</div>`:''}
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:40px;margin-top:20px;border-top:1px solid #eee;padding-top:14px;">
        <div></div>
        <div style="text-align:center;"><div style="height:40px;"></div>
          <div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">${esc(cfg.empresa)}</div>
        </div>
      </div>
      ${d.obs?`<div style="margin-top:16px;border-top:1px solid #eee;padding-top:10px;font-size:11px;color:#888;">${esc(d.obs)}</div>`:''}
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:14px;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn bp" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn bn2" onclick="closeModal()">Fechar</button>
    </div>
  `, 'wide');
};

window.delDoc = function(id){
  if(!isAdmin()||!confirm('Eliminar documento?')) return;
  DB.documentos = DB.documentos.filter(d=>d.id!==id);
  saveDB(DB); goTo('documentos');
};

// ─── RECIBOS ─────────────────────────────────────────────────
function _renderRecibosDoc(){
  DB = loadDB();
  if(!DB.recibos) DB.recibos = [];
  const rows = [...DB.recibos].reverse().map(r=>`<div class="card" style="margin-bottom:9px;border-left:3px solid var(--green);">
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
      <div>
        <div style="font-weight:700;font-size:14px;">🧾 ${esc(r.num)}</div>
        <div style="font-size:13px;color:var(--text);margin-top:2px;">${esc(r.cliNome)}</div>
        <div style="color:var(--muted);font-size:12px;">📅 ${r.data} · Via: ${esc(r.formaPag||'—')} · Ref: ${esc(r.ref||'—')}</div>
      </div>
      <div style="display:flex;align-items:center;gap:12px;">
        <div style="font-size:22px;font-weight:900;color:var(--green);">${mzn(r.valor)}</div>
        <div style="display:flex;gap:5px;">
          <button class="btn bp btn-xs" onclick="imprimirRecibo(${r.id})">🖨️ PDF</button>
          <button class="btn bg2 btn-xs" onclick="waRecibo(${r.id})">💬 WA</button>
          ${isAdmin()?`<button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delRecibo(${r.id})">🗑️</button>`:''}
        </div>
      </div>
    </div>
  </div>`).join('');
  return rows || '<div class="alert alert-w">Sem recibos. Clique em "+ Emitir Recibo".</div>';
}

window.novoRecibo = function(){
  const cliOpts = DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join('');
  const pgOpts = DB.cfg.pagamentos.filter(p=>p.ativo).map(p=>`<option value="${esc(p.nome)}">${esc(p.nome)}</option>`).join('');
  let _rItens = [{desc:'',qty:1,un:'un',preco:0}];
  openModal('Emitir Recibo', `
    <div class="g2">
      <div class="fg cs2" style="display:flex;gap:8px;align-items:flex-end;">
        <div style="flex:1;"><label class="lbl">Cliente</label><select class="inp" id="nr-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
        <button class="btn bg2 btn-sm" style="margin-bottom:14px;" onclick="novoCliRapido(function(cl){var s=document.getElementById('nr-cli');var o=document.createElement('option');o.value=cl.id;o.text=cl.nome;o.selected=true;s.appendChild(o);})">+ Novo</button>
      </div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="nr-data" value="${hoje()}"/></div>
      <div class="fg"><label class="lbl">Forma de Pagamento</label><select class="inp" id="nr-pg">${pgOpts}</select></div>
      <div class="fg cs2"><label class="lbl">Referência (Fatura / Serviço)</label><input class="inp" id="nr-ref" placeholder="Ex: FAT-2026-001 / Serviço de marcenaria"/></div>
    </div>
    <div style="margin:12px 0;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
        <label class="lbl" style="margin:0;">Produtos / Serviços</label>
        <button class="btn bn2 btn-xs" onclick="addItemRecibo()">+ Item</button>
      </div>
      <div style="background:var(--bg2);border-radius:10px;padding:11px;">
        <div style="display:grid;grid-template-columns:3fr 1fr 1fr 1.2fr 22px;gap:5px;margin-bottom:6px;">
          ${['Descrição','Un.','Qty','Preço',''].map(h=>`<div style="color:var(--muted);font-size:10px;font-weight:700;">${h}</div>`).join('')}
        </div>
        <div id="rec-itens"></div>
        <div style="text-align:right;padding-top:8px;border-top:1px solid var(--border);margin-top:6px;font-size:15px;font-weight:900;color:var(--gold);">TOTAL: <span id="rec-tot">0</span></div>
      </div>
    </div>
    <div class="fg"><label class="lbl">Observações</label><textarea class="inp" id="nr-obs" style="height:55px;resize:vertical;"></textarea></div>
    <div class="modal-foot">
      <button class="btn bn2" onclick="closeModal()">Cancelar</button>
      <button class="btn bp" onclick="salvarRecibo()">🧾 Emitir Recibo</button>
    </div>
  `, 'wide');
  window._rItens = [{desc:'',qty:1,un:'un',preco:0}];
  setTimeout(()=>renderItsRecibo(), 80);
};

window.addItemRecibo = function(){
  window._rItens = window._rItens||[];
  window._rItens.push({desc:'',qty:1,un:'un',preco:0});
  renderItsRecibo();
};
function renderItsRecibo(){
  const cont = document.getElementById('rec-itens'); if(!cont) return;
  const its = window._rItens||[];
  cont.innerHTML = its.map((it,i)=>`<div style="display:grid;grid-template-columns:3fr 1fr 1fr 1.2fr 22px;gap:5px;margin-bottom:5px;">
    <input class="inp" style="padding:7px 9px;font-size:12px;" placeholder="Produto / Serviço" value="${esc(it.desc)}" oninput="window._rItens[${i}].desc=this.value"/>
    <input class="inp" style="padding:7px 9px;font-size:12px;" value="${esc(it.un)}" oninput="window._rItens[${i}].un=this.value"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" value="${it.qty}" min="1" oninput="window._rItens[${i}].qty=Number(this.value);calcRecibo()"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" value="${it.preco}" min="0" oninput="window._rItens[${i}].preco=Number(this.value);calcRecibo()"/>
    <button onclick="window._rItens.splice(${i},1);renderItsRecibo();" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:18px;">×</button>
  </div>`).join('');
  calcRecibo();
}
function calcRecibo(){
  const tot = (window._rItens||[]).reduce((s,it)=>s+it.qty*it.preco,0);
  const el = document.getElementById('rec-tot'); if(el) el.textContent = mzn(tot);
}

window.salvarRecibo = function(){
  const cliId = Number(document.getElementById('nr-cli')?.value||0);
  if(!cliId) return alert('Selecione um cliente!');
  const its = window._rItens||[];
  if(!its[0]?.desc) return alert('Adicione pelo menos um item!');
  const cli = DB.clientes.find(c=>c.id===cliId);
  const total = its.reduce((s,it)=>s+it.qty*it.preco,0);
  if(!DB.recibos) DB.recibos=[];
  if(!DB.seq) DB.seq={rec:1};
  if(!DB.seq.rec) DB.seq.rec=1;
  const num = 'REC-'+new Date().getFullYear()+'-'+String(DB.seq.rec).padStart(3,'0');
  DB.seq.rec++;
  const rec = {
    id: Date.now(), num, cliId, cliNome: cli.nome, valor: total,
    itens: its.map(it=>({...it})),
    formaPag: document.getElementById('nr-pg')?.value||'',
    ref: document.getElementById('nr-ref')?.value||'',
    data: document.getElementById('nr-data')?.value||hoje(),
    obs: document.getElementById('nr-obs')?.value||'',
  };
  DB.recibos.push(rec);
  addLog('Recibo emitido: '+num+' — '+cli.nome+' — '+mzn(total));
  saveDB(DB); closeModal();
  setTimeout(()=>imprimirRecibo(rec.id), 300);
  goTo('documentos');
};

window.imprimirRecibo = function(id){
  if(!DB.recibos) return;
  const r = DB.recibos.find(x=>x.id===id); if(!r) return;
  const cfg = DB.cfg;
  const cli = DB.clientes.find(c=>c.id===r.cliId)||{};
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:55px;object-fit:contain;" alt="Logo"/>`:'';
  const pg = cfg.pagamentos.find(p=>p.nome===r.formaPag);
  const rows = (r.itens||[]).map((it,i)=>`<tr>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;">${i+1}</td>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;font-weight:700;">${esc(it.desc)}</td>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;">${esc(it.un||'un')}</td>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;text-align:right;">${it.qty}</td>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;text-align:right;">${mzn(it.preco)}</td>
    <td style="padding:8px 11px;border-bottom:1px solid #eee;text-align:right;font-weight:800;">${mzn(it.qty*it.preco)}</td>
  </tr>`).join('');
  openModal('Recibo — '+r.num, `
    <div id="pdf-content" style="background:#fff;color:#111;border-radius:10px;padding:36px;font-family:system-ui,sans-serif;font-size:13px;line-height:1.6;">
      <div style="text-align:center;margin-bottom:20px;">
        ${logoH?`<div style="margin-bottom:8px;">${logoH}</div>`:''}
        <div style="font-weight:900;font-size:20px;color:#0a0f2e;">${esc(cfg.empresa)}</div>
        <div style="color:#555;font-size:11px;">${esc(cfg.cidade)}, ${esc(cfg.pais)} · ${esc(cfg.tel)}</div>
      </div>
      <div style="background:#c8272e;color:#fff;text-align:center;padding:14px;border-radius:10px;margin-bottom:18px;">
        <div style="font-size:10px;letter-spacing:3px;opacity:.8;">DOCUMENTO OFICIAL</div>
        <div style="font-size:26px;font-weight:900;">RECIBO</div>
        <div style="font-size:14px;opacity:.9;">Nº ${esc(r.num)}</div>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:18px;">
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Recebido De</div>
          <div style="font-weight:800;font-size:15px;">${esc(r.cliNome)}</div>
          ${cli.tel?`<div style="color:#555;font-size:11px;">📞 ${esc(cli.tel)}</div>`:''}
          ${cli.nuit?`<div style="color:#555;font-size:11px;">NUIT: ${esc(cli.nuit)}</div>`:''}
        </div>
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Pagamento</div>
          <div style="font-weight:700;">Data: ${r.data}</div>
          <div style="color:#555;font-size:12px;">Via: ${esc(r.formaPag||'—')}</div>
          <div style="color:#555;font-size:12px;">Ref: ${esc(r.ref||'—')}</div>
        </div>
      </div>
      <table style="width:100%;border-collapse:collapse;margin-bottom:14px;">
        <thead><tr style="background:#0a0f2e;color:#fff;">
          <th style="padding:8px 11px;">#</th>
          <th style="padding:8px 11px;text-align:left;">Descrição</th>
          <th style="padding:8px 11px;">Un.</th>
          <th style="padding:8px 11px;text-align:right;">Qty</th>
          <th style="padding:8px 11px;text-align:right;">Preço</th>
          <th style="padding:8px 11px;text-align:right;">Total</th>
        </tr></thead>
        <tbody>${rows}</tbody>
      </table>
      <div style="background:#0a0f2e;color:#fff;border-radius:12px;padding:20px;text-align:center;margin-bottom:16px;">
        <div style="font-size:11px;opacity:.7;margin-bottom:4px;letter-spacing:2px;">VALOR TOTAL RECEBIDO</div>
        <div style="font-size:32px;font-weight:900;color:#d4a72a;">${mzn(r.valor)}</div>
      </div>
      ${pg&&pg.tipo!=='numerario'?`<div style="background:#f0f4f8;border-radius:8px;padding:12px;margin-bottom:14px;font-size:12px;">
        <div style="font-weight:700;margin-bottom:5px;">Dados de Pagamento:</div>
        ${pg.tipo==='banco'?`🏦 ${esc(pg.nome)} · Conta: ${esc(pg.conta||'—')} · NIB: ${esc(pg.nib||'—')} · Titular: ${esc(pg.titular||'')}`:`📱 ${esc(pg.nome)} · Número: ${esc(pg.numero||'—')}`}
      </div>`:''}
      ${r.obs?`<div style="background:#fffbea;border:1px solid #ffe070;border-radius:8px;padding:10px;margin-bottom:14px;font-size:12px;"><b>Obs:</b> ${esc(r.obs)}</div>`:''}
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:30px;margin-top:20px;border-top:1px solid #eee;padding-top:14px;">
        <div style="text-align:center;"><div style="height:36px;"></div><div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">O Cliente</div></div>
        <div style="text-align:center;"><div style="height:36px;"></div><div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">${esc(cfg.empresa)}</div></div>
      </div>
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:12px;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn bg2" onclick="waRecibo(${r.id})">💬 WhatsApp</button>
      <button class="btn bp" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn bn2" onclick="closeModal()">Fechar</button>
    </div>
  `, 'wide');
};

window.waRecibo = function(id){
  if(!DB.recibos) return;
  const r = DB.recibos.find(x=>x.id===id); if(!r) return;
  const cli = DB.clientes.find(c=>c.id===r.cliId);
  if(!cli?.tel) return alert('Cliente sem telefone!');
  const itens = (r.itens||[]).map(it=>`  • ${it.desc}: ${it.qty} ${it.un||'un'} × ${mzn(it.preco)} = ${mzn(it.qty*it.preco)}`).join('\n');
  const msg = `*${DB.cfg.empresa}*\n\n*🧾 RECIBO ${r.num}*\nCliente: ${r.cliNome}\nData: ${r.data}\nForma Pag.: ${r.formaPag||'—'}\nRef: ${r.ref||'—'}\n\n*Itens:*\n${itens}\n\n*TOTAL: ${mzn(r.valor)}*\n\n${DB.cfg.tel}`;
  window.open(`https://wa.me/${cli.tel.replace(/\D/g,'')}?text=${encodeURIComponent(msg)}`, '_blank');
};

window.delRecibo = function(id){
  if(!isAdmin()||!confirm('Eliminar recibo?')) return;
  DB.recibos = DB.recibos.filter(r=>r.id!==id);
  saveDB(DB); goTo('documentos');
};

// ─── GUIAS DE ENTREGA ────────────────────────────────────────
function _renderGuias(){
  DB = loadDB();
  if(!DB.guias) DB.guias = [];
  const rows = [...DB.guias].reverse().map(g=>`<div class="card" style="margin-bottom:9px;border-left:3px solid ${g.estado==='entregue'?'var(--green)':'var(--gold)'};">
    <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px;">
      <div>
        <div style="font-weight:700;font-size:14px;">🚚 ${esc(g.num)}</div>
        <div style="font-size:13px;color:var(--text);margin-top:2px;">${esc(g.cliNome)}</div>
        <div style="color:var(--muted);font-size:12px;">📅 ${g.data} · 📍 ${esc(g.destino||'—')} · ${(g.itens||[]).length} item(ns)</div>
        ${g.transportador?`<div style="color:var(--muted);font-size:12px;">🚛 ${esc(g.transportador)}</div>`:''}
      </div>
      <div style="display:flex;align-items:center;gap:10px;">
        <span class="bdg" style="background:${g.estado==='entregue'?'rgba(16,184,112,.2)':'rgba(212,167,42,.2)'};color:${g.estado==='entregue'?'var(--green)':'var(--gold)'};">${g.estado==='entregue'?'✅ Entregue':'🕐 Pendente'}</span>
        <div style="display:flex;gap:5px;">
          <button class="btn bp btn-xs" onclick="imprimirGuia(${g.id})">🖨️ PDF</button>
          ${g.estado!=='entregue'&&isAdmin()?`<button class="btn bg2 btn-xs" onclick="marcarEntregue(${g.id})">✓ Entregue</button>`:''}
          ${isAdmin()?`<button class="btn bn2 btn-xs" style="color:var(--red);" onclick="delGuia(${g.id})">🗑️</button>`:''}
        </div>
      </div>
    </div>
  </div>`).join('');
  return rows || '<div class="alert alert-w">Sem guias de entrega. Clique em "+ Guia de Entrega".</div>';
}

window.novaGuia = function(){
  const cliOpts = DB.clientes.map(c=>`<option value="${c.id}">${esc(c.nome)}</option>`).join('');
  const prodOpts = DB.produtos.map(p=>`<option value="${p.id}" data-p="${p.preco}" data-u="${esc(p.un)}">${esc(p.cod?'['+p.cod+'] ':'')}${esc(p.nome)}</option>`).join('');
  openModal('Nova Guia de Entrega', `
    <div class="g2">
      <div class="fg cs2" style="display:flex;gap:8px;align-items:flex-end;">
        <div style="flex:1;"><label class="lbl">Cliente / Destinatário</label><select class="inp" id="ng-cli"><option value="">Selecionar...</option>${cliOpts}</select></div>
        <button class="btn bg2 btn-sm" style="margin-bottom:14px;" onclick="novoCliRapido(function(cl){var s=document.getElementById('ng-cli');var o=document.createElement('option');o.value=cl.id;o.text=cl.nome;o.selected=true;s.appendChild(o);})">+ Novo</button>
      </div>
      <div class="fg"><label class="lbl">Data</label><input class="inp" type="date" id="ng-data" value="${hoje()}"/></div>
      <div class="fg"><label class="lbl">Transportador</label><input class="inp" id="ng-transp" placeholder="Nome do motorista / empresa"/></div>
      <div class="fg"><label class="lbl">Destino / Local de Entrega</label><input class="inp" id="ng-dest" placeholder="Endereço de entrega"/></div>
      <div class="fg"><label class="lbl">Referência</label><input class="inp" id="ng-ref" placeholder="FAT-2026-001..."/></div>
      <div class="fg"><label class="lbl">Estado</label>
        <select class="inp" id="ng-estado"><option value="pendente">🕐 Pendente</option><option value="entregue">✅ Entregue</option></select></div>
    </div>
    <div style="margin:12px 0;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;">
        <label class="lbl" style="margin:0;">Produtos / Mercadorias</label>
        <div style="display:flex;gap:5px;">
          <select id="ng-ps" class="inp" style="width:auto;padding:6px 10px;font-size:12px;" onchange="addProdGuia(this)">
            <option value="">+ Produto do estoque</option>${prodOpts}
          </select>
          <button class="btn bn2 btn-xs" onclick="addItemGuia()">+ Manual</button>
        </div>
      </div>
      <div style="background:var(--bg2);border-radius:10px;padding:11px;">
        <div style="display:grid;grid-template-columns:3fr 1fr 1fr 22px;gap:5px;margin-bottom:6px;">
          ${['Descrição','Un.','Qty',''].map(h=>`<div style="color:var(--muted);font-size:10px;font-weight:700;">${h}</div>`).join('')}
        </div>
        <div id="guia-itens"></div>
      </div>
    </div>
    <div class="fg"><label class="lbl">Observações</label><textarea class="inp" id="ng-obs" style="height:55px;resize:vertical;"></textarea></div>
    <div class="modal-foot">
      <button class="btn bn2" onclick="closeModal()">Cancelar</button>
      <button class="btn bp" onclick="salvarGuia()">🚚 Emitir Guia de Entrega</button>
    </div>
  `, 'wide');
  window._gItens = [{desc:'',qty:1,un:'un'}];
  setTimeout(()=>renderGuiaItens(), 80);
};

window.addItemGuia = function(){
  window._gItens = window._gItens||[];
  window._gItens.push({desc:'',qty:1,un:'un'});
  renderGuiaItens();
};
window.addProdGuia = function(sel){
  const o = sel.options[sel.selectedIndex]; if(!o.value) return;
  window._gItens = window._gItens||[];
  window._gItens.push({desc:o.text.split('] ').pop().split(' — ')[0], qty:1, un:o.dataset.u||'un'});
  sel.value=''; renderGuiaItens();
};
function renderGuiaItens(){
  const cont = document.getElementById('guia-itens'); if(!cont) return;
  const its = window._gItens||[];
  cont.innerHTML = its.map((it,i)=>`<div style="display:grid;grid-template-columns:3fr 1fr 1fr 22px;gap:5px;margin-bottom:5px;">
    <input class="inp" style="padding:7px 9px;font-size:12px;" placeholder="Produto / Mercadoria" value="${esc(it.desc)}" oninput="window._gItens[${i}].desc=this.value"/>
    <input class="inp" style="padding:7px 9px;font-size:12px;" value="${esc(it.un)}" oninput="window._gItens[${i}].un=this.value"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" value="${it.qty}" min="1" oninput="window._gItens[${i}].qty=Number(this.value)"/>
    <button onclick="window._gItens.splice(${i},1);renderGuiaItens();" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:18px;">×</button>
  </div>`).join('');
}

window.salvarGuia = function(){
  const cliId = Number(document.getElementById('ng-cli')?.value||0);
  if(!cliId) return alert('Selecione um cliente!');
  const its = window._gItens||[];
  if(!its[0]?.desc) return alert('Adicione pelo menos um item!');
  const cli = DB.clientes.find(c=>c.id===cliId);
  if(!DB.guias) DB.guias=[];
  if(!DB.seq) DB.seq={gr:1}; if(!DB.seq.gr) DB.seq.gr=1;
  const num = 'GR-'+new Date().getFullYear()+'-'+String(DB.seq.gr).padStart(3,'0');
  DB.seq.gr++;
  const g = {
    id: Date.now(), num, cliId, cliNome: cli.nome,
    data: document.getElementById('ng-data')?.value||hoje(),
    transportador: document.getElementById('ng-transp')?.value||'',
    destino: document.getElementById('ng-dest')?.value||'',
    ref: document.getElementById('ng-ref')?.value||'',
    estado: document.getElementById('ng-estado')?.value||'pendente',
    itens: its.map(it=>({...it})),
    obs: document.getElementById('ng-obs')?.value||'',
  };
  DB.guias.push(g);
  addLog('Guia emitida: '+num+' — '+cli.nome);
  saveDB(DB); closeModal();
  setTimeout(()=>imprimirGuia(g.id), 300);
  goTo('documentos');
};

window.marcarEntregue = function(id){
  DB.guias = DB.guias.map(g=>g.id===id?{...g,estado:'entregue'}:g);
  addLog('Guia entregue: '+(DB.guias.find(g=>g.id===id)?.num||id));
  saveDB(DB); goTo('documentos');
};

window.imprimirGuia = function(id){
  if(!DB.guias) return;
  const g = DB.guias.find(x=>x.id===id); if(!g) return;
  const cfg = DB.cfg;
  const cli = DB.clientes.find(c=>c.id===g.cliId)||{};
  const logoH = cfg.logo?`<img src="${cfg.logo}" style="max-height:55px;object-fit:contain;" alt="Logo"/>`:'';
  const rows = (g.itens||[]).map((it,i)=>`<tr>
    <td style="padding:9px 12px;border-bottom:1px solid #eee;">${i+1}</td>
    <td style="padding:9px 12px;border-bottom:1px solid #eee;font-weight:700;">${esc(it.desc)}</td>
    <td style="padding:9px 12px;border-bottom:1px solid #eee;">${esc(it.un||'un')}</td>
    <td style="padding:9px 12px;border-bottom:1px solid #eee;text-align:right;font-weight:800;">${it.qty}</td>
  </tr>`).join('');
  openModal('Guia de Entrega — '+g.num, `
    <div id="pdf-content" style="background:#fff;color:#111;border-radius:10px;padding:36px;font-family:system-ui,sans-serif;font-size:13px;line-height:1.6;">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;padding-bottom:16px;border-bottom:3px solid #c8272e;">
        <div>${logoH?`<div style="margin-bottom:8px;">${logoH}</div>`:''}
          <div style="font-weight:900;font-size:18px;color:#0a0f2e;">${esc(cfg.empresa)}</div>
          <div style="color:#555;font-size:11px;">${esc(cfg.slogan||'')}<br/>${esc(cfg.end||'')} · ${esc(cfg.cidade)}, ${esc(cfg.pais)}<br/>${esc(cfg.tel)} · ${esc(cfg.email)}</div>
        </div>
        <div style="text-align:right;">
          <div style="background:#c8272e;color:#fff;padding:6px 16px;border-radius:8px;font-weight:800;font-size:14px;display:inline-block;">GUIA DE ENTREGA</div>
          <div style="font-weight:800;font-size:15px;color:#0a0f2e;margin-top:5px;">${esc(g.num)}</div>
          <div style="color:#777;font-size:11px;">Data: ${g.data}</div>
          <div style="color:${g.estado==='entregue'?'#10b870':'#d4a72a'};font-size:11px;font-weight:700;">${g.estado==='entregue'?'✅ Entregue':'🕐 Pendente'}</div>
        </div>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:18px;">
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Destinatário</div>
          <div style="font-weight:800;font-size:15px;">${esc(g.cliNome)}</div>
          ${cli.tel?`<div style="color:#555;font-size:11px;">📞 ${esc(cli.tel)}</div>`:''}
          <div style="color:#0a0f2e;font-size:12px;margin-top:4px;">📍 ${esc(g.destino||'—')}</div>
        </div>
        <div style="background:#f5f7fa;border-radius:8px;padding:12px;">
          <div style="color:#888;font-size:10px;text-transform:uppercase;margin-bottom:4px;">Transporte</div>
          <div style="font-weight:700;">🚛 ${esc(g.transportador||'—')}</div>
          ${g.ref?`<div style="color:#555;font-size:12px;">Ref: ${esc(g.ref)}</div>`:''}
        </div>
      </div>
      <table style="width:100%;border-collapse:collapse;margin-bottom:16px;">
        <thead><tr style="background:#0a0f2e;color:#fff;">
          <th style="padding:9px 12px;">#</th>
          <th style="padding:9px 12px;text-align:left;">Descrição do Artigo</th>
          <th style="padding:9px 12px;">Unidade</th>
          <th style="padding:9px 12px;text-align:right;">Quantidade</th>
        </tr></thead>
        <tbody>${rows}</tbody>
      </table>
      ${g.obs?`<div style="background:#fffbea;border:1px solid #ffe070;border-radius:8px;padding:10px;margin-bottom:14px;font-size:12px;"><b>Obs:</b> ${esc(g.obs)}</div>`:''}
      <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px;margin-top:24px;border-top:1px solid #eee;padding-top:14px;">
        <div style="text-align:center;"><div style="height:36px;"></div><div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">Emitido por</div></div>
        <div style="text-align:center;"><div style="height:36px;"></div><div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">Transportador</div></div>
        <div style="text-align:center;"><div style="height:36px;"></div><div style="border-top:1px solid #aaa;padding-top:7px;font-size:10px;color:#888;">Recebido por</div></div>
      </div>
      <div style="text-align:center;font-size:10px;color:#bbb;margin-top:14px;">${esc(cfg.rodape||cfg.empresa)}</div>
    </div>
    <div style="display:flex;gap:8px;margin-top:14px;justify-content:flex-end;">
      <button class="btn bp" onclick="printDoc()">🖨️ Imprimir / PDF</button>
      <button class="btn bn2" onclick="closeModal()">Fechar</button>
    </div>
  `, 'wide');
};

window.delGuia = function(id){
  if(!isAdmin()||!confirm('Eliminar guia?')) return;
  DB.guias = DB.guias.filter(g=>g.id!==id);
  saveDB(DB); goTo('documentos');
};

// ─── MAXCUT — IMPORTAR LISTA + LIGAR AO ESTOQUE ──────────────
const _rMaxCut_orig = window.rMaxCut || null;
window.rMaxCut = function(){
  DB = loadDB();
  setTimeout(()=>{ if(document.getElementById('mx-pecas') && window._mxPecas) renderMXPecas(); }, 150);
  return `<div class="ph">
    <div><div class="ph-t">MaxCut / Plano de Corte</div><div class="ph-s">Otimize o uso das chapas</div></div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;">
    <div class="card">
      <div style="font-size:14px;font-weight:800;margin-bottom:14px;">Configuração da Chapa</div>
      <div class="g2">
        <div class="fg"><label class="lbl">Largura Chapa (mm)</label><input class="inp" type="number" id="mx-lc" value="2750"/></div>
        <div class="fg"><label class="lbl">Altura Chapa (mm)</label><input class="inp" type="number" id="mx-ac" value="1830"/></div>
        <div class="fg"><label class="lbl">Espessura Serra (mm)</label><input class="inp" type="number" id="mx-esp" value="4"/></div>
        <div class="fg"><label class="lbl">Produto no Estoque</label>
          <select class="inp" id="mx-prod">
            <option value="">Selecionar produto...</option>
            ${DB.produtos.filter(p=>p.cat==='Chapas'||p.nome.toLowerCase().includes('mdf')||p.nome.toLowerCase().includes('chapa')||p.nome.toLowerCase().includes('melamina')).map(p=>`<option value="${p.id}">${esc(p.cod?'['+p.cod+'] ':'')}${esc(p.nome)} — Estoque: ${p.estoque} ${p.un}</option>`).join('')}
          </select>
        </div>
      </div>
      <div style="font-size:13px;font-weight:800;margin:14px 0 10px;">Peças a Cortar</div>
      <div id="mx-pecas"></div>
      <div style="display:flex;gap:8px;margin-bottom:14px;flex-wrap:wrap;">
        <button class="btn bn2 btn-sm" onclick="addPecaMX()">+ Peça Manual</button>
        <label class="btn bb btn-sm" style="cursor:pointer;">📂 Importar CSV
          <input type="file" accept=".csv,.txt" style="display:none;" onchange="importarCSVMaxCut(this)"/>
        </label>
      </div>
      <button class="btn bp" style="width:100%;justify-content:center;padding:12px;" onclick="calcMaxCutV2()">✂️ Calcular Plano de Corte</button>
    </div>
    <div id="mx-res" style="display:flex;align-items:center;justify-content:center;">
      <div style="text-align:center;color:var(--muted);">
        <div style="font-size:48px;margin-bottom:10px;">✂️</div>
        <div style="font-size:13px;">Adicione peças e clique em Calcular</div>
        <div style="font-size:11px;color:var(--muted);margin-top:6px;">Pode importar uma lista CSV com colunas: Nome, Largura, Altura, Quantidade</div>
      </div>
    </div>
  </div>`;
};

window._mxPecas = window._mxPecas || [{d:'Lateral',l:600,a:800,q:2},{d:'Prateleira',l:800,a:400,q:3}];

function renderMXPecas(){
  const cont = document.getElementById('mx-pecas'); if(!cont) return;
  cont.innerHTML = (window._mxPecas||[]).map((p,i)=>`<div style="display:grid;grid-template-columns:2fr 1fr 1fr 1fr 22px;gap:5px;margin-bottom:5px;">
    <input class="inp" style="padding:7px 9px;font-size:12px;" placeholder="Nome da peça" value="${esc(p.d)}" oninput="window._mxPecas[${i}].d=this.value"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" placeholder="L(mm)" value="${p.l}" oninput="window._mxPecas[${i}].l=Number(this.value)"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" placeholder="A(mm)" value="${p.a}" oninput="window._mxPecas[${i}].a=Number(this.value)"/>
    <input class="inp" type="number" style="padding:7px 9px;font-size:12px;" placeholder="Qty" value="${p.q}" oninput="window._mxPecas[${i}].q=Number(this.value)"/>
    <button onclick="window._mxPecas.splice(${i},1);renderMXPecas();" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:18px;">×</button>
  </div>`).join('');
}

window.addPecaMX = function(){
  window._mxPecas = window._mxPecas||[];
  window._mxPecas.push({d:'Peça '+(window._mxPecas.length+1),l:400,a:600,q:1});
  renderMXPecas();
};

window.importarCSVMaxCut = function(input){
  const file = input.files[0]; if(!file) return;
  const reader = new FileReader();
  reader.onload = e => {
    const lines = e.target.result.split('\n').filter(l=>l.trim());
    window._mxPecas = [];
    lines.forEach((line,i)=>{
      if(i===0 && line.toLowerCase().includes('nome')) return; // skip header
      const parts = line.split(/[,;\t]/).map(p=>p.trim().replace(/"/g,''));
      if(parts.length >= 3){
        window._mxPecas.push({
          d: parts[0]||'Peça '+(i+1),
          l: Number(parts[1])||400,
          a: Number(parts[2])||600,
          q: Number(parts[3])||1,
        });
      }
    });
    renderMXPecas();
    const t=document.createElement('div');t.className='toast';t.style.cssText='position:fixed;top:20px;right:20px;background:var(--card);border:1px solid var(--border2);border-radius:14px;padding:14px 18px;font-size:13px;font-weight:600;z-index:9999;box-shadow:0 8px 30px rgba(0,0,0,.6);';
    t.innerHTML='✅ '+window._mxPecas.length+' peças importadas do CSV!';document.body.appendChild(t);setTimeout(()=>t.remove(),3500);
  };
  reader.readAsText(file);
};

window.calcMaxCutV2 = function(){
  const lc = Number(document.getElementById('mx-lc')?.value||2750);
  const ac = Number(document.getElementById('mx-ac')?.value||1830);
  const esp = Number(document.getElementById('mx-esp')?.value||4);
  const prodId = Number(document.getElementById('mx-prod')?.value||0);
  const pecas = window._mxPecas||[];
  if(!pecas.length) return alert('Adicione pelo menos uma peça!');

  let todas = [];
  pecas.forEach(p=>{ for(let i=0;i<p.q;i++) todas.push({d:p.d,l:p.l,a:p.a}); });
  todas.sort((a,b)=>b.a-a.a||(b.l-a.l));

  let chapas=[]; let chapa={pecas:[],usada:0}; let x=0; let y=0; let maxA=0;
  todas.forEach(p=>{
    if(x+p.l>lc){x=0;y+=maxA+esp;maxA=0;}
    if(y+p.a>ac){chapas.push({...chapa});chapa={pecas:[],usada:0};x=0;y=0;maxA=0;}
    chapa.pecas.push({...p,x,y});
    chapa.usada += (p.l*p.a)/(lc*ac)*100;
    x+=p.l+esp; maxA=Math.max(maxA,p.a);
  });
  if(chapa.pecas.length) chapas.push(chapa);

  const totalArea = todas.reduce((s,p)=>s+p.l*p.a,0);
  const efic = Math.round(totalArea/(chapas.length*lc*ac)*100);
  const desperdicio = Math.round(100-efic);

  // Update estoque if product selected
  let estoqueMsg = '';
  if(prodId){
    const prod = DB.produtos.find(p=>p.id===prodId);
    if(prod){
      const consumo = chapas.length;
      const novoEstoque = Math.max(0, prod.estoque - consumo);
      estoqueMsg = `<div class="alert alert-${novoEstoque<=prod.min?'r':'g'}" style="margin-bottom:12px;">
        <div><b>📦 Consumo de Estoque — ${esc(prod.nome)}${prod.cod?' ['+esc(prod.cod)+']':''}</b><br/>
        Chapas consumidas: <b>${consumo}</b> · Estoque actual: <b>${prod.estoque}</b> → Novo estoque: <b style="color:${novoEstoque<=prod.min?'var(--red)':'var(--green)'};">${novoEstoque}</b></div>
      </div>
      <div style="display:flex;gap:8px;margin-bottom:14px;">
        <button class="btn bp btn-sm" onclick="if(confirm('Dar baixa de ${consumo} chapas no estoque?')){DB.produtos=DB.produtos.map(p=>p.id===${prodId}?{...p,estoque:Math.max(0,p.estoque-${consumo})}:p);addLog('MaxCut: baixa de ${consumo} chapas — ${prod.nome}');saveDB(DB);alert('✅ Estoque actualizado!');}">📉 Dar Baixa no Estoque (${consumo} chapas)</button>
      </div>`;
    }
  }

  const cores = ['#3a8ef8','#10b870','#d4a72a','#7c5cfc','#f07830','#c8272e','#10b8b0','#e87890'];
  const svgs = chapas.map((ch,ci)=>{
    const sc=0.12; const sw=lc*sc; const sh=ac*sc;
    const pRects = ch.pecas.map((p,pi)=>`
      <rect x="${p.x*sc}" y="${p.y*sc}" width="${p.l*sc}" height="${p.a*sc}" fill="${cores[pi%cores.length]}" fill-opacity="0.75" stroke="white" stroke-width="1" rx="2"/>
      <text x="${(p.x+p.l/2)*sc}" y="${(p.y+p.a/2)*sc-4}" text-anchor="middle" dominant-baseline="middle" font-size="7" fill="white" font-weight="bold">${esc(p.d)}</text>
      <text x="${(p.x+p.l/2)*sc}" y="${(p.y+p.a/2)*sc+6}" text-anchor="middle" dominant-baseline="middle" font-size="6" fill="rgba(255,255,255,.8)">${p.l}×${p.a}</text>
    `).join('');
    return`<div style="margin-bottom:16px;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;">
        <span style="font-size:12px;font-weight:800;">Chapa ${ci+1} de ${chapas.length}</span>
        <span style="font-size:11px;color:var(--muted);">Utilização: <b style="color:${ch.usada>70?'var(--green)':'var(--gold)'};">${Math.round(ch.usada)}%</b></span>
      </div>
      <svg width="${sw}" height="${sh}" style="background:#1a2340;border:1px solid var(--border);border-radius:8px;display:block;max-width:100%;">
        <rect width="${sw}" height="${sh}" fill="#1a2340"/>
        ${pRects}
      </svg>
    </div>`;
  }).join('');

  // List table
  const listRows = pecas.map((p,i)=>`<tr>
    <td>${i+1}</td><td style="font-weight:700;">${esc(p.d)}</td>
    <td style="text-align:right;">${p.l}</td><td style="text-align:right;">${p.a}</td>
    <td style="text-align:right;">${p.q}</td>
    <td style="text-align:right;">${((p.l*p.a*p.q)/1000000).toFixed(3)} m²</td>
  </tr>`).join('');

  document.getElementById('mx-res').innerHTML = `<div style="width:100%;">
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:14px;">
      <div class="kpi" style="border-left:3px solid var(--red);"><div class="kpi-l">Chapas Necessárias</div><div class="kpi-v" style="color:var(--red);font-size:24px;">${chapas.length}</div></div>
      <div class="kpi" style="border-left:3px solid var(--green);"><div class="kpi-l">Eficiência</div><div class="kpi-v" style="color:var(--green);font-size:24px;">${efic}%</div></div>
      <div class="kpi" style="border-left:3px solid var(--orange);"><div class="kpi-l">Desperdício</div><div class="kpi-v" style="color:var(--orange);font-size:24px;">${desperdicio}%</div></div>
      <div class="kpi" style="border-left:3px solid var(--blue);"><div class="kpi-l">Total Peças</div><div class="kpi-v" style="color:var(--blue);font-size:24px;">${todas.length}</div></div>
    </div>
    ${estoqueMsg}
    <div class="card" style="margin-bottom:14px;">
      <div style="font-size:13px;font-weight:800;margin-bottom:10px;">Lista de Peças</div>
      <div style="overflow-x:auto;"><table class="tbl"><thead><tr><th>#</th><th>Nome</th><th style="text-align:right;">L(mm)</th><th style="text-align:right;">A(mm)</th><th style="text-align:right;">Qty</th><th style="text-align:right;">Área</th></tr></thead><tbody>${listRows}</tbody></table></div>
    </div>
    <div class="card">
      <div style="font-size:13px;font-weight:800;margin-bottom:12px;">Plano Visual de Corte</div>
      ${svgs}
    </div>
  </div>`;
};

// Add documentos to nav
if(window.NAV && !window.NAV.find(n=>n.id==='documentos')){
  window.NAV.push({id:'documentos',lbl:'Documentos',grp:'Gestão',ico:'M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z|M14 2v6h6|M9 12h6|M9 16h6'});
  if(window.PERMS){
    Object.keys(window.PERMS).forEach(k=>{ if(!window.PERMS[k].includes('documentos')) window.PERMS[k].push('documentos'); });
  }
}

// Auto-patch goTo to include documentos
const _goTo_orig = window.goTo;
window.goTo = function(p){
  if(p === 'documentos'){
    window.CP = p;
    document.querySelectorAll('.nb,.bn').forEach(b=>b.classList.remove('on'));
    const nb=document.getElementById('nb-'+p); if(nb) nb.classList.add('on');
    const tb=document.getElementById('tb-t'); if(tb) tb.textContent='Documentos';
    Object.values(window.chartInstances||{}).forEach(c=>{try{c.destroy();}catch(e){}});
    window.chartInstances={};
    DB = loadDB();
    document.getElementById('main').innerHTML = rDocumentos();
    return;
  }
  _goTo_orig(p);
};

console.log('✅ v5.1 PATCH: Pesquisa Estoque + Documentos + Recibos + Guias + MaxCut aplicado!');

</script>
</body>
</html>

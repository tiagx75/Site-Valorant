"""
Valorant Hub — Skins, Agents & Tier Lists
Serveur local Python qui sert le site sur http://localhost:8000
Lancer avec : python valorant_hub.py
"""

import http.server
import webbrowser
import threading

HTML = r"""<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Valorant Hub — Skins, Agents & Tier Lists</title>
  <style>
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
    :root{
      --bg:#fff;--bg2:#f5f5f5;--bg3:#ececec;
      --txt:#111;--txt2:#555;--txt3:#999;
      --bdr:rgba(0,0,0,.1);--bdr2:rgba(0,0,0,.18);
      --rmd:8px;--rlg:12px;
      --red:#ff4655;--dark:#0f1923;
    }
    @media(prefers-color-scheme:dark){
      :root{
        --bg:#1a1a1a;--bg2:#242424;--bg3:#111;
        --txt:#f0f0f0;--txt2:#aaa;--txt3:#666;
        --bdr:rgba(255,255,255,.08);--bdr2:rgba(255,255,255,.15);
      }
    }
    body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:var(--bg3);color:var(--txt);min-height:100vh}

    /* ── NAV ── */
    nav{position:sticky;top:0;z-index:200;background:var(--dark);display:flex;align-items:center;padding:0 1rem;border-bottom:2px solid var(--red);gap:0;overflow-x:auto}
    .nav-logo{font-size:14px;font-weight:800;letter-spacing:2px;color:#fff;padding:13px 20px 13px 0;border-right:1px solid rgba(255,255,255,.1);margin-right:12px;white-space:nowrap;flex-shrink:0}
    .nav-logo span{color:var(--red)}
    .nav-btn{padding:13px 16px;font-size:12px;font-weight:700;letter-spacing:.5px;color:rgba(255,255,255,.45);cursor:pointer;border:none;background:none;border-bottom:3px solid transparent;margin-bottom:-2px;white-space:nowrap;transition:color .15s}
    .nav-btn:hover{color:rgba(255,255,255,.85)}
    .nav-btn.active{color:#fff;border-bottom:3px solid var(--red)}

    /* ── PAGES ── */
    .page{display:none;max-width:1280px;margin:0 auto;padding:1.5rem 1rem 4rem}
    .page.active{display:block}
    .page-title{font-size:20px;font-weight:700;margin-bottom:4px}
    .page-sub{font-size:13px;color:var(--txt2);margin-bottom:1.2rem}

    /* ── CONTROLS ── */
    .controls{display:flex;gap:8px;margin-bottom:1rem;flex-wrap:wrap;align-items:center}
    .search-box{flex:1;min-width:180px;padding:9px 13px;border:1px solid var(--bdr2);border-radius:var(--rmd);background:var(--bg);color:var(--txt);font-size:13px}
    .search-box:focus{outline:none;border-color:var(--red)}
    .filter-select{padding:9px 13px;border:1px solid var(--bdr2);border-radius:var(--rmd);background:var(--bg);color:var(--txt);font-size:12px;cursor:pointer}
    .stat-pill{background:var(--bg);border:1px solid var(--bdr);border-radius:20px;padding:4px 13px;font-size:12px;color:var(--txt2);display:inline-block;margin-right:6px;margin-bottom:8px}
    .stat-pill b{color:var(--txt)}

    .loader{text-align:center;padding:3rem;color:var(--txt2);font-size:13px}
    .loader-bar{width:180px;height:3px;background:var(--bdr2);border-radius:3px;margin:12px auto 0;overflow:hidden}
    .loader-fill{height:100%;background:var(--red);border-radius:3px;animation:lb 1.5s ease-in-out infinite}
    @keyframes lb{0%{width:0%;margin-left:0}50%{width:60%;margin-left:20%}100%{width:0%;margin-left:100%}}
    .error{text-align:center;padding:2rem;color:#e44;font-size:13px}
    .no-results{text-align:center;padding:2rem;color:var(--txt2);font-size:13px}

    /* ══════════ SKINS ══════════ */
    .weapons-list{display:flex;flex-direction:column;gap:10px}
    .weapon-block{background:var(--bg);border:1px solid var(--bdr);border-radius:var(--rlg);overflow:hidden}
    .weapon-header{display:flex;align-items:center;gap:12px;padding:13px 16px;cursor:pointer;user-select:none;transition:background .15s}
    .weapon-header:hover{background:var(--bg2)}
    .weapon-icon{width:75px;height:38px;object-fit:contain;opacity:.85}
    .weapon-info{flex:1}
    .weapon-name{font-size:14px;font-weight:600}
    .weapon-meta{font-size:11px;color:var(--txt2);margin-top:2px}
    .chev{font-size:12px;color:var(--txt3);transition:transform .2s;flex-shrink:0}
    .chev.open{transform:rotate(90deg)}
    .skins-panel{display:none;border-top:1px solid var(--bdr)}
    .skins-panel.open{display:block}
    .rar-header{display:flex;align-items:center;gap:8px;padding:9px 16px;background:var(--bg2);border-bottom:1px solid var(--bdr)}
    .rar-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0}
    .rar-name{font-size:10px;font-weight:700;color:var(--txt2);text-transform:uppercase;letter-spacing:.8px}
    .rar-count{font-size:10px;color:var(--txt3);margin-left:auto}
    .skins-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:1px;background:var(--bdr)}
    .skin-card{background:var(--bg);padding:10px;display:flex;flex-direction:column;gap:6px;transition:background .15s}
    .skin-card:hover{background:var(--bg2)}
    .skin-img-wrap{height:65px;display:flex;align-items:center;justify-content:center;background:var(--bg2);border-radius:var(--rmd);overflow:hidden}
    .skin-img{max-width:100%;max-height:58px;object-fit:contain}
    .skin-img-ph{font-size:10px;color:var(--txt3)}
    .skin-name{font-size:11px;line-height:1.35}
    .skin-badge{display:inline-flex;align-items:center;font-size:9px;padding:2px 7px;border-radius:10px;font-weight:600}
    .skin-ch{font-size:9px;color:var(--txt3)}

    /* ══════════ AGENTS ══════════ */
    .role-row{display:flex;gap:7px;margin-bottom:1rem;flex-wrap:wrap}
    .role-chip{padding:5px 14px;border-radius:20px;font-size:11px;font-weight:700;cursor:pointer;border:1px solid var(--bdr2);background:var(--bg);color:var(--txt2);transition:all .15s;display:flex;align-items:center;gap:5px}
    .role-chip:hover{border-color:var(--red);color:var(--red)}
    .role-chip.active{background:var(--red);color:#fff;border-color:var(--red)}
    .role-chip img{width:13px;height:13px;object-fit:contain;filter:brightness(0) invert(.4)}
    .role-chip.active img{filter:brightness(0) invert(1)}
    .agents-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(310px,1fr));gap:13px}
    .agent-card{background:var(--bg);border:1px solid var(--bdr);border-radius:var(--rlg);overflow:hidden;transition:border-color .2s}
    .agent-card:hover{border-color:var(--red)}
    .agent-hdr{display:flex;align-items:stretch;cursor:pointer;user-select:none}
    .agent-portrait{width:85px;object-fit:cover;object-position:top center;flex-shrink:0}
    .agent-info{flex:1;padding:13px;display:flex;flex-direction:column;gap:6px}
    .agent-top{display:flex;align-items:center;gap:7px;flex-wrap:wrap}
    .agent-name{font-size:16px;font-weight:700}
    .agent-role-badge{display:flex;align-items:center;gap:3px;font-size:9px;font-weight:700;padding:2px 8px;border-radius:10px;text-transform:uppercase;letter-spacing:.5px}
    .agent-role-badge img{width:10px;height:10px;object-fit:contain}
    .agent-desc{font-size:11px;color:var(--txt2);line-height:1.55}
    .agent-toggle{display:flex;align-items:center;justify-content:space-between;padding:9px 14px;background:var(--bg2);border-top:1px solid var(--bdr);cursor:pointer;font-size:11px;font-weight:600;color:var(--txt2);user-select:none;transition:color .15s}
    .agent-toggle:hover{color:var(--red)}
    .ab-panel{display:none;border-top:1px solid var(--bdr)}
    .ab-panel.open{display:flex;flex-direction:column}
    .ab-row{display:flex;gap:11px;padding:13px;border-bottom:1px solid var(--bdr);align-items:flex-start}
    .ab-row:last-child{border-bottom:none}
    .ab-icon-wrap{width:42px;height:42px;background:var(--bg2);border-radius:var(--rmd);display:flex;align-items:center;justify-content:center;flex-shrink:0;overflow:hidden}
    .ab-icon{width:28px;height:28px;object-fit:contain}
    .ab-info{flex:1}
    .ab-top{display:flex;align-items:center;gap:7px;margin-bottom:4px}
    .ab-name{font-size:12px;font-weight:700}
    .ab-slot{font-size:9px;font-weight:700;padding:2px 7px;border-radius:5px;text-transform:uppercase;letter-spacing:.5px}
    .slot-basic{background:#5c85d622;color:#5c85d6}
    .slot-grenade{background:#4CAF5022;color:#4CAF50}
    .slot-signature{background:#ff980022;color:#ff9800}
    .slot-ultimate{background:#ff465522;color:#ff4655}
    .ab-desc{font-size:11px;color:var(--txt2);line-height:1.6}
    .rDuelist{background:#ff465518;color:#ff4655}
    .rController{background:#b44dff18;color:#b44dff}
    .rInitiateur,.rInitiator{background:#5c85d618;color:#5c85d6}
    .rSentinelle,.rSentinel{background:#4CAF5018;color:#4CAF50}

    /* ══════════ TIER LIST ══════════ */
    .tl-intro{background:var(--bg);border:1px solid var(--bdr);border-radius:var(--rlg);padding:16px 20px;margin-bottom:1.5rem;display:flex;align-items:center;gap:14px;flex-wrap:wrap}
    .tl-badge{background:var(--red);color:#fff;font-size:11px;font-weight:700;padding:4px 12px;border-radius:20px;letter-spacing:.5px}
    .tl-intro-text{font-size:12px;color:var(--txt2);line-height:1.6}
    .maps-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(360px,1fr));gap:16px}
    .map-card{background:var(--bg);border:1px solid var(--bdr);border-radius:var(--rlg);overflow:hidden}
    .map-banner{position:relative;height:100px;overflow:hidden;background:var(--bg2)}
    .map-banner img{width:100%;height:100%;object-fit:cover;object-position:center}
    .map-banner-overlay{position:absolute;inset:0;background:linear-gradient(to right,rgba(15,25,35,.85) 40%,rgba(15,25,35,.2))}
    .map-banner-txt{position:absolute;bottom:12px;left:16px}
    .map-banner-name{font-size:20px;font-weight:800;color:#fff;letter-spacing:1px;text-transform:uppercase}
    .map-banner-sites{font-size:11px;color:rgba(255,255,255,.6);margin-top:2px}
    .map-banner-tag{position:absolute;top:10px;right:12px;background:rgba(15,25,35,.8);color:rgba(255,255,255,.7);font-size:10px;padding:3px 9px;border-radius:10px;border:1px solid rgba(255,255,255,.15);font-weight:600}

    .tier-section{padding:14px 16px}
    .tier-row{display:flex;gap:0;margin-bottom:10px;border-radius:var(--rmd);overflow:hidden;border:1px solid var(--bdr)}
    .tier-label{width:46px;display:flex;align-items:center;justify-content:center;font-size:15px;font-weight:800;flex-shrink:0}
    .tier-S .tier-label{background:#ff4655;color:#fff}
    .tier-A .tier-label{background:#ff7c21;color:#fff}
    .tier-B .tier-label{background:#e5c000;color:#111}
    .tier-C .tier-label{background:#4a9e4a;color:#fff}
    .tier-D .tier-label{background:#5a5a6e;color:#fff}
    .tier-agents{flex:1;display:flex;flex-wrap:wrap;gap:8px;padding:10px 12px;align-items:center;background:var(--bg2)}

    .agent-pill{display:flex;align-items:center;gap:6px;background:var(--bg);border:1px solid var(--bdr);border-radius:20px;padding:4px 10px 4px 4px;transition:border-color .15s}
    .agent-pill:hover{border-color:var(--red)}
    .agent-pill-icon{width:26px;height:26px;border-radius:50%;object-fit:cover;object-position:top;background:var(--bg2);flex-shrink:0}
    .agent-pill-name{font-size:11px;font-weight:600}
    .agent-pill-role{font-size:9px;color:var(--txt3);margin-top:1px}

    .agent-pill-ico-wrap{width:26px;height:26px;border-radius:50%;background:var(--bg2);display:flex;align-items:center;justify-content:center;flex-shrink:0;overflow:hidden}

    .role-tag{display:inline-block;font-size:9px;font-weight:700;padding:1px 6px;border-radius:4px;margin-left:2px}
    .tag-duel{background:#ff465518;color:#ff4655}
    .tag-ctrl{background:#b44dff18;color:#b44dff}
    .tag-init{background:#5c85d618;color:#5c85d6}
    .tag-sent{background:#4CAF5018;color:#4CAF50}

    .map-tip{background:var(--bg2);border-top:1px solid var(--bdr);padding:12px 16px;font-size:11px;color:var(--txt2);line-height:1.65}
    .map-tip strong{color:var(--txt);font-weight:600}

    @media(max-width:640px){
      .agents-grid{grid-template-columns:1fr}
      .skins-grid{grid-template-columns:repeat(auto-fill,minmax(130px,1fr))}
      .maps-grid{grid-template-columns:1fr}
      .agent-portrait{width:68px}
    }
  </style>
</head>
<body>

<nav>
  <div class="nav-logo">VAL<span>O</span>RANT HUB</div>
  <button class="nav-btn active" onclick="showPage('skins',this)">Skins</button>
  <button class="nav-btn" onclick="showPage('agents',this)">Agents</button>
  <button class="nav-btn" onclick="showPage('tierlist',this)">Tier List Maps</button>
</nav>

<!-- ═════════════ SKINS ═════════════ -->
<div id="page-skins" class="page active">
  <p class="page-title" style="margin-top:.5rem">Toutes les armes & skins</p>
  <p class="page-sub">Clique sur une arme · skins groupés par rareté · ordre croissant</p>
  <div class="controls">
    <input class="search-box" id="skinSearch" placeholder="Rechercher un skin ou une arme..." oninput="applySkinsFilters()">
    <select class="filter-select" id="rarityFilter" onchange="applySkinsFilters()">
      <option value="">Toutes les raretés</option>
      <option value="Standard">Standard</option>
      <option value="Select">Select</option>
      <option value="Deluxe">Deluxe</option>
      <option value="Premium">Premium</option>
      <option value="Exclusive">Exclusive</option>
      <option value="Ultra">Ultra</option>
      <option value="Edition">Edition</option>
    </select>
    <select class="filter-select" id="skinSort" onchange="applySkinsFilters()">
      <option value="alpha">A → Z</option>
      <option value="alpha-desc">Z → A</option>
    </select>
  </div>
  <div id="skinStats"></div>
  <div id="skinLoader" class="loader">Chargement des armes...<div class="loader-bar"><div class="loader-fill"></div></div></div>
  <div id="skinError" class="error" style="display:none"></div>
  <div class="weapons-list" id="weaponsList"></div>
</div>

<!-- ═════════════ AGENTS ═════════════ -->
<div id="page-agents" class="page">
  <p class="page-title" style="margin-top:.5rem">Tous les agents</p>
  <p class="page-sub">Clique sur un agent pour voir ses capacités & utilités</p>
  <div class="controls">
    <input class="search-box" id="agentSearch" placeholder="Rechercher un agent..." oninput="applyAgentsFilters()">
    <select class="filter-select" id="agentSort" onchange="applyAgentsFilters()">
      <option value="alpha">A → Z</option>
      <option value="alpha-desc">Z → A</option>
    </select>
  </div>
  <div class="role-row" id="roleRow"><div class="role-chip active" data-role="" onclick="setRole(this,'')">Tous</div></div>
  <div id="agentStats"></div>
  <div id="agentLoader" class="loader">Chargement des agents...<div class="loader-bar"><div class="loader-fill"></div></div></div>
  <div id="agentError" class="error" style="display:none"></div>
  <div class="agents-grid" id="agentsGrid"></div>
</div>

<!-- ═════════════ TIER LIST ═════════════ -->
<div id="page-tierlist" class="page">
  <p class="page-title" style="margin-top:.5rem">Tier List — Meilleurs agents par map</p>
  <p class="page-sub">Map pool V26 · Act 2 · Ranked Compétitif — basé sur le meta pro & solo queue actuel</p>

  <div class="tl-intro">
    <div>
      <div class="tl-badge">V26 ACT 2 — OFFICIEL</div>
      <div style="margin-top:6px" class="tl-intro-text">
        Map pool actuel : <strong>Bind · Lotus · Split · Fracture · Pearl · Haven · Breeze</strong><br>
        Abyss & Corrode sont OUT. Fracture & Lotus font leur retour. Les tier lists couvrent <strong>Duéliste, Controller, Initiateur & Sentinelle</strong>.
      </div>
    </div>
  </div>

  <div class="maps-grid" id="mapsGrid"></div>
</div>

<script>
/* ─────────────────────────────
   NAV
───────────────────────────── */
function showPage(id,btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  btn.classList.add('active');
  if(id==='tierlist' && !tlBuilt) buildTierList();
}

/* ─────────────────────────────
   SKINS
───────────────────────────── */
const TIER_MAP={
  '12683d76-48d7-84a3-4e09-6985794f0445':'Select',
  '0cebb8be-46d7-c12a-d306-e9907bfc5a25':'Deluxe',
  '60bca009-4182-7998-dee7-b8a2558dc369':'Premium',
  'e046854e-406c-37f4-6607-19a9ba8426fc':'Exclusive',
  '411e4a55-4e59-7757-41f0-86a53f101bb5':'Ultra',
  'f7629040-645f-8e38-6e20-498a4f2a0964':'Edition',
};
const RARITY_COLORS={Standard:'#888',Select:'#5c85d6',Deluxe:'#4CAF50',Premium:'#b44dff',Exclusive:'#ff9800',Ultra:'#f5c518',Edition:'#ff4655'};
const RARITY_ORDER=['Standard','Select','Deluxe','Premium','Exclusive','Ultra','Edition'];

let allWeapons=[];
let openWeapons=new Set();

async function loadSkins(){
  try{
    const r=await fetch('https://valorant-api.com/v1/weapons?language=fr-FR');
    const j=await r.json();
    allWeapons=(j.data||[]).sort((a,b)=>a.displayName.localeCompare(b.displayName,'fr'));
    document.getElementById('skinLoader').style.display='none';
    const total=allWeapons.reduce((s,w)=>s+(w.skins||[]).length,0);
    document.getElementById('skinStats').innerHTML=
      `<span class="stat-pill"><b>${allWeapons.length}</b> armes</span><span class="stat-pill"><b>${total}</b> skins</span>`;
    applySkinsFilters();
  }catch(e){
    document.getElementById('skinLoader').style.display='none';
    const el=document.getElementById('skinError');el.style.display='block';
    el.textContent='Impossible de charger les données.';
  }
}

function applySkinsFilters(){
  const search=(document.getElementById('skinSearch').value||'').toLowerCase();
  const rarityF=document.getElementById('rarityFilter').value;
  const sort=document.getElementById('skinSort').value;
  const container=document.getElementById('weaponsList');
  container.innerHTML='';let any=false;
  allWeapons.forEach(w=>{
    let skins=(w.skins||[]).map(s=>({...s,_r:TIER_MAP[s.contentTierUuid]||'Standard'}));
    if(rarityF)skins=skins.filter(s=>s._r===rarityF);
    const wm=w.displayName.toLowerCase().includes(search);
    if(search&&!wm)skins=skins.filter(s=>s.displayName.toLowerCase().includes(search));
    if(!skins.length&&search&&!wm)return;
    any=true;
    skins.sort((a,b)=>sort==='alpha-desc'?b.displayName.localeCompare(a.displayName,'fr'):a.displayName.localeCompare(b.displayName,'fr'));
    const groups={};
    skins.forEach(s=>{if(!groups[s._r])groups[s._r]=[];groups[s._r].push(s);});
    const og=RARITY_ORDER.filter(r=>groups[r]).map(r=>[r,groups[r]]);
    const isOpen=openWeapons.has(w.uuid);
    const block=document.createElement('div');
    block.className='weapon-block';block.id='wb-'+w.uuid;
    const iconH=w.killStreamIcon?`<img class="weapon-icon" src="${w.killStreamIcon}" alt="${w.displayName}" onerror="this.style.display='none'">` :'';
    const meta=w.weaponStats?[w.weaponStats.fireRate?w.weaponStats.fireRate+' coups/s':null,w.weaponStats.magazineSize?w.weaponStats.magazineSize+' balles':null].filter(Boolean).join(' · '):'';
    const groupsH=og.map(([rar,ss])=>{
      const c=RARITY_COLORS[rar]||'#888';
      const cards=ss.map(sk=>{
        const img=sk.displayIcon||(sk.levels&&sk.levels[0]&&sk.levels[0].displayIcon)||'';
        const ch=sk.chromas?sk.chromas.length:0;
        return `<div class="skin-card">
          <div class="skin-img-wrap">${img?`<img class="skin-img" src="${img}" alt="${sk.displayName}" loading="lazy" onerror="this.parentElement.innerHTML='<div class=\\'skin-img-ph\\'>—</div>'">`:'<div class="skin-img-ph">—</div>'}</div>
          <div class="skin-name">${sk.displayName}</div>
          <div class="skin-badge" style="background:${c}22;color:${c}">${rar}</div>
          ${ch>1?`<div class="skin-ch">${ch} variantes</div>`:''}
        </div>`;}).join('');
      return `<div><div class="rar-header"><div class="rar-dot" style="background:${c}"></div><span class="rar-name">${rar}</span><span class="rar-count">${ss.length} skin${ss.length>1?'s':''}</span></div><div class="skins-grid">${cards}</div></div>`;
    }).join('');
    block.innerHTML=`
      <div class="weapon-header" onclick="toggleWeapon('${w.uuid}')">
        ${iconH}
        <div class="weapon-info"><div class="weapon-name">${w.displayName}</div><div class="weapon-meta">${meta?meta+' · ':''}${skins.length} skin${skins.length>1?'s':''}</div></div>
        <div class="chev${isOpen?' open':''}">▶</div>
      </div>
      <div class="skins-panel${isOpen?' open':''}" id="panel-${w.uuid}">${groupsH}</div>`;
    container.appendChild(block);
  });
  if(!any)container.innerHTML='<div class="no-results">Aucun résultat.</div>';
}
function toggleWeapon(uuid){
  if(openWeapons.has(uuid))openWeapons.delete(uuid);else openWeapons.add(uuid);
  document.getElementById('panel-'+uuid)?.classList.toggle('open',openWeapons.has(uuid));
  document.querySelector('#wb-'+uuid+' .chev')?.classList.toggle('open',openWeapons.has(uuid));
}

/* ─────────────────────────────
   AGENTS
───────────────────────────── */
let allAgents=[];
let openAgents=new Set();
let activeRole='';

function slotKey(s){const x=(s||'').toLowerCase();if(x==='basic')return 'basic';if(x==='grenade')return 'grenade';if(x==='signature')return 'signature';if(x==='ultimate')return 'ultimate';return 'basic';}
function slotLabel(s){const x=(s||'').toLowerCase();if(x==='basic')return 'C';if(x==='grenade')return 'Q';if(x==='signature')return 'E';if(x==='ultimate')return 'ULTIME';return '?';}

async function loadAgents(){
  try{
    const r=await fetch('https://valorant-api.com/v1/agents?isPlayableCharacter=true&language=fr-FR');
    const j=await r.json();
    allAgents=(j.data||[]).sort((a,b)=>a.displayName.localeCompare(b.displayName,'fr'));
    document.getElementById('agentLoader').style.display='none';
    document.getElementById('agentStats').innerHTML=`<span class="stat-pill"><b>${allAgents.length}</b> agents</span>`;
    const roles=[...new Set(allAgents.map(a=>a.role?.displayName).filter(Boolean))].sort();
    const row=document.getElementById('roleRow');
    roles.forEach(role=>{
      const a0=allAgents.find(a=>a.role?.displayName===role);
      const icon=a0?.role?.displayIcon||'';
      const chip=document.createElement('div');
      chip.className='role-chip';chip.dataset.role=role;chip.onclick=()=>setRole(chip,role);
      chip.innerHTML=(icon?`<img src="${icon}" alt="">`:'')+'<span>'+role+'</span>';
      row.appendChild(chip);
    });
    applyAgentsFilters();
  }catch(e){
    document.getElementById('agentLoader').style.display='none';
    const el=document.getElementById('agentError');el.style.display='block';el.textContent='Impossible de charger les agents.';
  }
}
function setRole(el,role){
  activeRole=role;
  document.querySelectorAll('.role-chip').forEach(c=>c.classList.remove('active'));
  el.classList.add('active');
  applyAgentsFilters();
}
function applyAgentsFilters(){
  const search=(document.getElementById('agentSearch').value||'').toLowerCase();
  const sort=document.getElementById('agentSort').value;
  const grid=document.getElementById('agentsGrid');grid.innerHTML='';
  let agents=allAgents.filter(a=>{
    if(activeRole&&a.role?.displayName!==activeRole)return false;
    if(search&&!a.displayName.toLowerCase().includes(search))return false;
    return true;
  });
  if(sort==='alpha-desc')agents.sort((a,b)=>b.displayName.localeCompare(a.displayName,'fr'));
  if(!agents.length){grid.innerHTML='<div class="no-results" style="grid-column:1/-1">Aucun agent trouvé.</div>';return;}
  agents.forEach(agent=>{
    const rn=agent.role?.displayName||'';const ri=agent.role?.displayIcon||'';
    const isOpen=openAgents.has(agent.uuid);
    const portrait=agent.fullPortrait||agent.bustPortrait||agent.displayIcon||'';
    const abH=(agent.abilities||[]).map(ab=>{
      const sk=slotKey(ab.slot);const sl=slotLabel(ab.slot);const icon=ab.displayIcon||'';
      return `<div class="ab-row">
        <div class="ab-icon-wrap">${icon?`<img class="ab-icon" src="${icon}" alt="${ab.displayName||''}" onerror="this.style.opacity='0'">` :'<span style="font-size:16px;color:var(--txt3)">?</span>'}</div>
        <div class="ab-info">
          <div class="ab-top"><span class="ab-name">${ab.displayName||'—'}</span><span class="ab-slot slot-${sk}">${sl}</span></div>
          <div class="ab-desc">${ab.description||'Aucune description.'}</div>
        </div>
      </div>`;
    }).join('');
    const card=document.createElement('div');card.className='agent-card';card.id='ac-'+agent.uuid;
    card.innerHTML=`
      <div class="agent-hdr" onclick="toggleAgent('${agent.uuid}')">
        ${portrait?`<img class="agent-portrait" src="${portrait}" alt="${agent.displayName}" onerror="this.style.display='none'">` :''}
        <div class="agent-info">
          <div class="agent-top">
            <span class="agent-name">${agent.displayName}</span>
            ${rn?`<span class="agent-role-badge r${rn}">${ri?`<img src="${ri}" alt="">`:''}${rn}</span>`:''}
          </div>
          <div class="agent-desc">${agent.description||''}</div>
        </div>
      </div>
      <div class="agent-toggle" onclick="toggleAgent('${agent.uuid}')">
        <span>Voir les capacités (${(agent.abilities||[]).length})</span>
        <span class="chev${isOpen?' open':''}">▶</span>
      </div>
      <div class="ab-panel${isOpen?' open':''}" id="abp-${agent.uuid}">${abH}</div>`;
    grid.appendChild(card);
  });
}
function toggleAgent(uuid){
  if(openAgents.has(uuid))openAgents.delete(uuid);else openAgents.add(uuid);
  document.getElementById('abp-'+uuid)?.classList.toggle('open',openAgents.has(uuid));
  document.querySelector('#ac-'+uuid+' .agent-toggle .chev')?.classList.toggle('open',openAgents.has(uuid));
}

/* ─────────────────────────────
   TIER LIST — V26 ACT 2
   Sources : meta pro + win rate ranked
───────────────────────────── */
const MAP_DATA=[
  {
    name:'Bind',sites:'2 sites · Téléporteurs',
    color:'#c84b00',
    uuid:'2c9d57ec-4431-9c5e-2939-8f9ef6dd5cba',
    tip:'<strong>Bind</strong> est une map avec téléporteurs qui favorise les agents capables de faire des rotations rapides et de contrôler les entrées de site. Raze est quasi obligatoire grâce à ses satchels dans les couloirs étroits. Viper est la meilleure smoker car son écran découpe B site et la teleroom. Skye et Breach sont les meilleurs initiateurs pour les flashes dans les couloirs. Brimstone pour ses smokes précises sur A short.',
    tiers:{
      S:[{n:'Raze',r:'Dueliste'},{n:'Viper',r:'Controller'},{n:'Skye',r:'Initiateur'},{n:'Killjoy',r:'Sentinelle'}],
      A:[{n:'Breach',r:'Initiateur'},{n:'Brimstone',r:'Controller'},{n:'Cypher',r:'Sentinelle'},{n:'Tejo',r:'Initiateur'}],
      B:[{n:'Omen',r:'Controller'},{n:'Gekko',r:'Initiateur'},{n:'Neon',r:'Dueliste'},{n:'Sova',r:'Initiateur'}],
      C:[{n:'Jett',r:'Dueliste'},{n:'Reyna',r:'Dueliste'},{n:'Chamber',r:'Sentinelle'},{n:'Clove',r:'Controller'}],
      D:[{n:'Astra',r:'Controller'},{n:'Harbor',r:'Controller'},{n:'Deadlock',r:'Sentinelle'},{n:'Iso',r:'Dueliste'}],
    }
  },
  {
    name:'Lotus',sites:'3 sites · Portes rotatives',
    color:'#2d7a3a',
    uuid:'2fb9a4fd-47b8-4e7f-a969-9b65a51a988a',
    tip:'<strong>Lotus</strong> est la map à 3 sites avec portes rotatives. Elle nécessite un Controller puissant pour contrôler les flancs et les portes. Viper + Omen est le double smoke dominant car ils couvrent les 3 sites indépendamment. Raze est indispensable pour ouvrir les sites rapidement. Killjoy verrouille C site avec sa Lockdown. Fade & Tejo apportent l\'info sur les rotations adverses.',
    tiers:{
      S:[{n:'Raze',r:'Dueliste'},{n:'Viper',r:'Controller'},{n:'Killjoy',r:'Sentinelle'},{n:'Fade',r:'Initiateur'}],
      A:[{n:'Omen',r:'Controller'},{n:'Tejo',r:'Initiateur'},{n:'Skye',r:'Initiateur'},{n:'Jett',r:'Dueliste'}],
      B:[{n:'Gekko',r:'Initiateur'},{n:'Clove',r:'Controller'},{n:'Vyse',r:'Sentinelle'},{n:'Breach',r:'Initiateur'}],
      C:[{n:'Brimstone',r:'Controller'},{n:'Cypher',r:'Sentinelle'},{n:'Neon',r:'Dueliste'},{n:'KAY/O',r:'Initiateur'}],
      D:[{n:'Reyna',r:'Dueliste'},{n:'Phoenix',r:'Dueliste'},{n:'Harbor',r:'Controller'},{n:'Deadlock',r:'Sentinelle'}],
    }
  },
  {
    name:'Split',sites:'2 sites · Verticale',
    color:'#1a5fa8',
    uuid:'d960549e-485c-e861-8d71-aa9d1aed12a2',
    tip:'<strong>Split</strong> est une map verticale avec des couloirs très étroits. Raze domine grâce à ses satchels sur les boosts. Omen contrôle Mid et Heaven via ses smokes. Sage est incontournable pour son mur sur B ou A ramp. Breach est parfait pour ses stuns sur les couloirs étroits. Cypher peut tenir les flancs Heaven et Mid en solo.',
    tiers:{
      S:[{n:'Raze',r:'Dueliste'},{n:'Omen',r:'Controller'},{n:'Sage',r:'Sentinelle'},{n:'Breach',r:'Initiateur'}],
      A:[{n:'Cypher',r:'Sentinelle'},{n:'Skye',r:'Initiateur'},{n:'Viper',r:'Controller'},{n:'Tejo',r:'Initiateur'}],
      B:[{n:'Jett',r:'Dueliste'},{n:'Killjoy',r:'Sentinelle'},{n:'Waylay',r:'Dueliste'},{n:'Clove',r:'Controller'}],
      C:[{n:'KAY/O',r:'Initiateur'},{n:'Neon',r:'Dueliste'},{n:'Brimstone',r:'Controller'},{n:'Gekko',r:'Initiateur'}],
      D:[{n:'Reyna',r:'Dueliste'},{n:'Astra',r:'Controller'},{n:'Harbor',r:'Controller'},{n:'Phoenix',r:'Dueliste'}],
    }
  },
  {
    name:'Fracture',sites:'2 sites · Ziplines',
    color:'#8b1a1a',
    uuid:'b529448b-4d60-346e-e89e-00a4c527a405',
    tip:'<strong>Fracture</strong> est la map la plus unique du pool avec ses ziplines. Les attaquants peuvent pincer depuis les deux côtés. Breach est quasi obligatoire — ses stuns couvrent les deux entrées A et B simultanément. Brimstone place ses smokes depuis n\'importe quel angle. Fade et Raze complètent la comp idéale. Chamber est le meilleur sentinel pour tenir les angles longs sur ce map.',
    tiers:{
      S:[{n:'Breach',r:'Initiateur'},{n:'Raze',r:'Dueliste'},{n:'Brimstone',r:'Controller'},{n:'Fade',r:'Initiateur'}],
      A:[{n:'Chamber',r:'Sentinelle'},{n:'Killjoy',r:'Sentinelle'},{n:'Omen',r:'Controller'},{n:'Tejo',r:'Initiateur'}],
      B:[{n:'Jett',r:'Dueliste'},{n:'Viper',r:'Controller'},{n:'Skye',r:'Initiateur'},{n:'Cypher',r:'Sentinelle'}],
      C:[{n:'KAY/O',r:'Initiateur'},{n:'Neon',r:'Dueliste'},{n:'Clove',r:'Controller'},{n:'Gekko',r:'Initiateur'}],
      D:[{n:'Sage',r:'Sentinelle'},{n:'Reyna',r:'Dueliste'},{n:'Harbor',r:'Controller'},{n:'Deadlock',r:'Sentinelle'}],
    }
  },
  {
    name:'Pearl',sites:'2 sites · Mid ouvert',
    color:'#4a3080',
    uuid:'fd267378-4d1d-484f-ff52-77821ed10dc2',
    tip:'<strong>Pearl</strong> récompense le contrôle du mid et l\'information. C\'est une map où les initiateurs valent de l\'or. Fade est le meilleur initiateur pour ses révélations dans les couloirs. Astra et Viper contrôlent le mid et les 2 sites depuis leurs positions sûres. Killjoy et Cypher verrouillent B Short. Chamber est excellent sur les angles longs de A Main.',
    tiers:{
      S:[{n:'Fade',r:'Initiateur'},{n:'Viper',r:'Controller'},{n:'Killjoy',r:'Sentinelle'},{n:'Chamber',r:'Sentinelle'}],
      A:[{n:'Astra',r:'Controller'},{n:'Cypher',r:'Sentinelle'},{n:'Tejo',r:'Initiateur'},{n:'Jett',r:'Dueliste'}],
      B:[{n:'Sova',r:'Initiateur'},{n:'Omen',r:'Controller'},{n:'KAY/O',r:'Initiateur'},{n:'Raze',r:'Dueliste'}],
      C:[{n:'Gekko',r:'Initiateur'},{n:'Skye',r:'Initiateur'},{n:'Clove',r:'Controller'},{n:'Neon',r:'Dueliste'}],
      D:[{n:'Sage',r:'Sentinelle'},{n:'Phoenix',r:'Dueliste'},{n:'Harbor',r:'Controller'},{n:'Reyna',r:'Dueliste'}],
    }
  },
  {
    name:'Haven',sites:'3 sites · Grand format',
    color:'#1e6b5a',
    uuid:'2bee0dc9-4ffe-519b-1cbd-7825db7f6a55',
    tip:'<strong>Haven</strong> est la seule map avec 3 sites. Elle exige une excellente communication et des agents capables de contrôler plusieurs angles. Sova est le meilleur initiateur — ses recons couvrent A, C et Mid sans se mettre en danger. Omen et Brimstone dominent pour les smokes. Killjoy peut anchor un site en solo. Jett reste redoutable sur les angles C Long et A Long.',
    tiers:{
      S:[{n:'Sova',r:'Initiateur'},{n:'Jett',r:'Dueliste'},{n:'Killjoy',r:'Sentinelle'},{n:'Omen',r:'Controller'}],
      A:[{n:'Brimstone',r:'Controller'},{n:'Skye',r:'Initiateur'},{n:'Breach',r:'Initiateur'},{n:'Cypher',r:'Sentinelle'}],
      B:[{n:'Fade',r:'Initiateur'},{n:'Tejo',r:'Initiateur'},{n:'Chamber',r:'Sentinelle'},{n:'Clove',r:'Controller'}],
      C:[{n:'Raze',r:'Dueliste'},{n:'KAY/O',r:'Initiateur'},{n:'Viper',r:'Controller'},{n:'Gekko',r:'Initiateur'}],
      D:[{n:'Neon',r:'Dueliste'},{n:'Astra',r:'Controller'},{n:'Harbor',r:'Controller'},{n:'Deadlock',r:'Sentinelle'}],
    }
  },
  {
    name:'Breeze',sites:'2 sites · Long range',
    color:'#0a6e8a',
    uuid:'2c9d57ec-4431-9c5e-2939-8f9ef6dd5cba',
    tip:'<strong>Breeze</strong> est la map avec les plus longues portées de tir du pool. Les agents mobiles et les outils longue distance y brillent. Viper est quasi incontournable pour ses walls et mollies dans les espaces ouverts. Jett & Chamber dominent avec l\'Operator. Sova et Fade fournissent l\'information nécessaire sur les grandes distances. Harbor a aussi une utilité rare ici.',
    tiers:{
      S:[{n:'Viper',r:'Controller'},{n:'Jett',r:'Dueliste'},{n:'Sova',r:'Initiateur'},{n:'Chamber',r:'Sentinelle'}],
      A:[{n:'Fade',r:'Initiateur'},{n:'Astra',r:'Controller'},{n:'Killjoy',r:'Sentinelle'},{n:'KAY/O',r:'Initiateur'}],
      B:[{n:'Omen',r:'Controller'},{n:'Tejo',r:'Initiateur'},{n:'Cypher',r:'Sentinelle'},{n:'Clove',r:'Controller'}],
      C:[{n:'Raze',r:'Dueliste'},{n:'Skye',r:'Initiateur'},{n:'Gekko',r:'Initiateur'},{n:'Harbor',r:'Controller'}],
      D:[{n:'Sage',r:'Sentinelle'},{n:'Neon',r:'Dueliste'},{n:'Reyna',r:'Dueliste'},{n:'Phoenix',r:'Dueliste'}],
    }
  },
];

const ROLE_TAG_CLASS={
  'Dueliste':'tag-duel','Controller':'tag-ctrl',
  'Initiateur':'tag-init','Sentinelle':'tag-sent'
};

let tlBuilt=false;
let agentIconCache={};

async function buildTierList(){
  tlBuilt=true;
  allAgents.forEach(a=>{agentIconCache[a.displayName.toLowerCase()]={icon:a.displayIcon,portrait:a.bustPortrait||a.displayIcon};});

  const grid=document.getElementById('mapsGrid');
  grid.innerHTML='';

  for(const map of MAP_DATA){
    let mapImg='';
    try{
      const r=await fetch(`https://valorant-api.com/v1/maps?language=fr-FR`);
      const j=await r.json();
      const found=(j.data||[]).find(m=>m.displayName===map.name||m.displayName.toLowerCase()===map.name.toLowerCase());
      if(found)mapImg=found.splash||found.listViewIcon||'';
    }catch(e){}

    const card=document.createElement('div');
    card.className='map-card';

    const tiersH=Object.entries(map.tiers).map(([tier,agents])=>{
      const pillsH=agents.map(ag=>{
        const key=ag.n.toLowerCase();
        const iconData=agentIconCache[key];
        const iconUrl=iconData?.icon||'';
        const tagClass=ROLE_TAG_CLASS[ag.r]||'tag-init';
        return `<div class="agent-pill">
          <div class="agent-pill-ico-wrap">
            ${iconUrl?`<img class="agent-pill-icon" src="${iconUrl}" alt="${ag.n}" onerror="this.style.display='none'">` :''}
          </div>
          <div>
            <div class="agent-pill-name">${ag.n}</div>
            <span class="role-tag ${tagClass}">${ag.r}</span>
          </div>
        </div>`;
      }).join('');
      return `<div class="tier-row tier-${tier}">
        <div class="tier-label">${tier}</div>
        <div class="tier-agents">${pillsH}</div>
      </div>`;
    }).join('');

    card.innerHTML=`
      <div class="map-banner" style="background:${map.color}22">
        ${mapImg?`<img src="${mapImg}" alt="${map.name}" onerror="this.remove()">` :''}
        <div class="map-banner-overlay"></div>
        <div class="map-banner-txt">
          <div class="map-banner-name">${map.name}</div>
          <div class="map-banner-sites">${map.sites}</div>
        </div>
        <div class="map-banner-tag">V26 · ACT 2</div>
      </div>
      <div class="tier-section">${tiersH}</div>
      <div class="map-tip">${map.tip}</div>`;
    grid.appendChild(card);
  }
}

/* ─── INIT ─── */
loadSkins();
loadAgents();
</script>
</body>
</html>"""

PORT = 8000

class Handler(http.server.BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header("Content-type", "text/html; charset=utf-8")
        self.end_headers()
        self.wfile.write(HTML.encode("utf-8"))

    def log_message(self, format, *args):
        print(f"  {self.address_string()} → {args[0]}")

def open_browser():
    webbrowser.open(f"http://localhost:{PORT}")

if __name__ == "__main__":
    server = http.server.HTTPServer(("", PORT), Handler)
    print(f"✅  Valorant Hub lancé sur http://localhost:{PORT}")
    print("   Appuyez sur Ctrl+C pour arrêter.\n")
    threading.Timer(0.8, open_browser).start()
    try:
        server.serve_forever()
    except KeyboardInterrupt:
        print("\n⛔  Serveur arrêté.")

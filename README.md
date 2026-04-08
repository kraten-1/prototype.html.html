# prototype.html.html
prototype
[prototype.html.html](https://github.com/user-attachments/files/26565977/prototype.html.html)
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Help exaM — Clip Marketplace</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600&display=swap');
  * { margin:0; padding:0; box-sizing:border-box; }
  :root {
    --bg: #05050d;
    --bg2: #08081a;
    --bg3: #0d0d22;
    --card: #0a0a1c;
    --border: #1a1a3a;
    --accent: #00eeff;
    --accent2: #8b5cf6;
    --gold: #fbbf24;
    --green: #00ffaa;
    --text: #f0f4ff;
    --muted: #8899bb;
    --font: 'Angsana New', 'Sarabun', serif;
    --glow-cyan: 0 0 20px rgba(0,238,255,.35), 0 0 60px rgba(0,238,255,.12);
    --glow-purple: 0 0 20px rgba(139,92,246,.35), 0 0 60px rgba(139,92,246,.12);
    --glow-gold: 0 0 20px rgba(251,191,36,.3);
  }
  body { background:var(--bg); color:var(--text); font-family:var(--font); font-size:12px; min-height:100vh; }
  /* ขนาดฟอนต์ภาษาอังกฤษโดดเด่นขึ้น */
  :lang(en), .en, .clip-title, .clip-subject, .nav-links a, .tab, .btn, h1, h2, h3,
  .stat-num, .s-stat-num, .clip-price, .room-name, .chat-name, .hero-tag {
    font-size-adjust: 0.58;
  }
  input, select, textarea { font-size:.68rem !important; }
  .clip-title { font-size:.74rem !important; }
  .clip-subject { font-size:.6rem !important; }
  .nav-links a { font-size:.71rem !important; }
  .tab { font-size:.71rem !important; }
  .stat-num { font-size:1.16rem !important; }
  .clip-price { font-size:.8rem !important; }
  .clip-rating { font-size:.64rem !important; }
  .seller-name { font-size:.6rem !important; }
  .room-name { font-size:.68rem !important; }
  .room-preview { font-size:.58rem !important; }
  .msg { font-size:.68rem !important; }
  /* ANIMATED BG GRID */
  body::before { content:''; position:fixed; inset:0; background-image: linear-gradient(rgba(0,238,255,.03) 1px,transparent 1px), linear-gradient(90deg,rgba(0,238,255,.03) 1px,transparent 1px); background-size:40px 40px; pointer-events:none; z-index:0; }
  body > * { position:relative; z-index:1; }
  /* SCROLLBAR */
  ::-webkit-scrollbar { width:4px; } ::-webkit-scrollbar-track { background:var(--bg2); } ::-webkit-scrollbar-thumb { background:var(--accent2); border-radius:2px; }
  /* NAV */
  nav { background:rgba(8,8,26,.85); border-bottom:1px solid rgba(0,238,255,.15); padding:0 1.5rem; display:flex; align-items:center; justify-content:space-between; height:52px; position:sticky; top:0; z-index:100; backdrop-filter:blur(20px); box-shadow:0 1px 30px rgba(0,238,255,.06); }
  .logo { font-size:2.2rem; font-weight:900; background:linear-gradient(135deg,var(--accent),var(--accent2)); -webkit-background-clip:text; background-clip:text; -webkit-text-fill-color:transparent; letter-spacing:2px; filter:drop-shadow(0 0 12px rgba(0,238,255,.6)); line-height:1; }
  .logo span { font-size:0.58rem; color:var(--muted); -webkit-text-fill-color:var(--muted); display:block; font-weight:300; filter:none; letter-spacing:1px; margin-top:.1rem; }
  .nav-links { display:flex; gap:1.5rem; align-items:center; }
  .nav-links a { color:var(--muted); text-decoration:none; font-size:1rem; transition:all .2s; cursor:pointer; }
  .nav-links a:hover, .nav-links a.active { color:var(--accent); text-shadow:0 0 10px rgba(0,238,255,.6); }
  .nav-right { display:flex; gap:1rem; align-items:center; }
  .btn { padding:.22rem .55rem; border-radius:5px; border:none; cursor:pointer; font-family:var(--font); font-size:.41rem; transition:all .25s; }
  .btn-outline { background:#ffffff; border:1px solid #ffffff; color:#0a0a1c; font-weight:600; }
  .btn-outline:hover { background:#f0f4ff; box-shadow:0 0 12px rgba(255,255,255,.3); transform:translateY(-1px); }
  .btn-primary { background:#ffffff; border:1px solid #ffffff; color:#0a0a1c; font-weight:700; box-shadow:0 0 15px rgba(255,255,255,.2); }
  .btn-primary:hover { background:#f0f4ff; box-shadow:0 0 20px rgba(255,255,255,.3); transform:translateY(-2px); }
  .badge-free { background:linear-gradient(135deg,var(--green),#00cc88); color:#000; font-size:.65rem; padding:.12rem .45rem; border-radius:20px; margin-left:.5rem; font-weight:700; box-shadow:0 0 8px rgba(0,255,170,.3); }
</style>
<style>
  /* LAYOUT */
  .app { display:flex; flex-direction:column; height:calc(100vh - 60px); }
  .main-content { flex:1; overflow-y:auto; padding:1.5rem 2rem; }
  /* HERO */
  .hero { background:linear-gradient(135deg,#131330 0%,#0e0e28 100%); border:1px solid rgba(0,238,255,.3); border-radius:16px; padding:2.5rem; margin-bottom:1.5rem; position:relative; overflow:hidden; box-shadow:0 0 40px rgba(0,238,255,.08), inset 0 1px 0 rgba(0,238,255,.15); }
  .hero::before { content:''; position:absolute; top:-60%; right:-5%; width:500px; height:500px; background:radial-gradient(circle,rgba(0,238,255,.12) 0%,transparent 65%); pointer-events:none; }
  .hero::after { content:''; position:absolute; bottom:-40%; left:20%; width:300px; height:300px; background:radial-gradient(circle,rgba(139,92,246,.1) 0%,transparent 65%); pointer-events:none; }
  .hero-tag { color:var(--accent); font-size:.85rem; letter-spacing:3px; text-transform:uppercase; margin-bottom:.7rem; text-shadow:0 0 10px rgba(0,238,255,.5); }
  .hero h1 { font-size:1.54rem; font-weight:700; line-height:1.3; margin-bottom:.6rem; }
  .hero h1 em { font-style:normal; background:linear-gradient(135deg,var(--accent),var(--gold)); -webkit-background-clip:text; -webkit-text-fill-color:transparent; filter:drop-shadow(0 0 12px rgba(0,238,255,.4)); }
  .hero p { color:#8899bb; font-size:.71rem; max-width:500px; }
  .hero-stats { display:flex; gap:2rem; margin-top:1.8rem; }
  .stat { text-align:center; padding:.6rem 1rem; background:#1a1a38; border:1px solid rgba(0,238,255,.2); border-radius:8px; }
  .stat-num { font-size:1.6rem; font-weight:700; color:var(--accent); text-shadow:0 0 12px rgba(0,238,255,.5); }
  .stat-label { font-size:.8rem; color:var(--muted); }
  /* SEARCH */
  .search-bar { display:flex; gap:.75rem; margin-bottom:1.5rem; }
  .search-input { flex:1; background:#ffffff; border:1px solid rgba(0,238,255,.4); border-radius:8px; padding:.7rem 1rem; color:#0a0a1c; font-family:var(--font); font-size:4.08rem; outline:none; transition:all .25s; }
  .search-input::placeholder { color:#94a3b8; }
  .search-input:focus { border-color:var(--accent); box-shadow:0 0 0 3px rgba(0,238,255,.1), var(--glow-cyan); }
  .filter-btn { background:#131330; border:1px solid rgba(0,238,255,.2); color:#aabbcc; padding:.7rem 1rem; border-radius:8px; cursor:pointer; font-family:var(--font); font-size:.95rem; transition:all .25s; }
  .filter-btn.active, .filter-btn:hover { border-color:var(--accent); color:var(--accent); background:#1a1a40; box-shadow:0 0 12px rgba(0,238,255,.15); }
  /* TABS */
  .tabs { display:flex; gap:.5rem; margin-bottom:1.2rem; border-bottom:1px solid rgba(0,238,255,.1); padding-bottom:.5rem; }
  .tab { padding:.4rem 1rem; border-radius:6px 6px 0 0; cursor:pointer; font-size:1rem; color:var(--muted); transition:all .2s; border:none; background:transparent; font-family:var(--font); }
  .tab.active { color:var(--accent); border-bottom:2px solid var(--accent); text-shadow:0 0 8px rgba(0,238,255,.5); }
  /* GRID */
  .clip-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(260px,1fr)); gap:1rem; }
  /* CARD */
  .clip-card { background:#161630; border:1px solid rgba(0,238,255,.25); border-radius:12px; overflow:hidden; cursor:pointer; transition:all .3s; position:relative; box-shadow:0 4px 20px rgba(0,0,0,.6); }
  .clip-card::before { content:''; position:absolute; inset:0; background:linear-gradient(135deg,rgba(0,238,255,.03),transparent); opacity:0; transition:opacity .3s; pointer-events:none; }
  .clip-card:hover { border-color:rgba(0,238,255,.6); transform:translateY(-4px); box-shadow:0 12px 40px rgba(0,238,255,.18), 0 0 0 1px rgba(0,238,255,.15); }
  .clip-card:hover::before { opacity:1; }
  .clip-thumb { width:100%; height:145px; background:linear-gradient(135deg,#1a1a40,#0f0f30); display:flex; align-items:center; justify-content:center; position:relative; overflow:hidden; }
  .clip-thumb::after { content:''; position:absolute; inset:0; background:linear-gradient(to bottom,transparent 50%,rgba(0,0,0,.5)); }
  .play-icon { width:52px; height:52px; background:rgba(0,238,255,.1); border:2px solid var(--accent); border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:1.3rem; color:var(--accent); box-shadow:var(--glow-cyan); transition:all .3s; z-index:1; }
  .clip-card:hover .play-icon { background:rgba(0,238,255,.2); transform:scale(1.1); }
  .clip-type-badge { position:absolute; top:.5rem; left:.5rem; padding:.2rem .6rem; border-radius:4px; font-size:.75rem; font-weight:700; z-index:2; }
  .badge-mid { background:rgba(251,191,36,.12); color:var(--gold); border:1px solid rgba(251,191,36,.4); box-shadow:0 0 8px rgba(251,191,36,.2); }
  .badge-fin { background:rgba(139,92,246,.12); color:#c4b5fd; border:1px solid rgba(139,92,246,.4); box-shadow:0 0 8px rgba(139,92,246,.2); }
  .clip-info { padding:.9rem; background:#161630; }
  .clip-subject { font-size:.8rem; color:#00eeff; margin-bottom:.3rem; text-shadow:0 0 6px rgba(0,238,255,.4); font-weight:700; }
  .clip-title { font-size:1.05rem; font-weight:700; margin-bottom:.5rem; line-height:1.3; color:#f0f4ff; }
  .clip-meta { display:flex; justify-content:space-between; align-items:center; }
  .clip-price { font-size:1.15rem; font-weight:700; color:#00ffaa; text-shadow:0 0 8px rgba(0,255,170,.3); }
  .clip-price.paid { color:#fbbf24; text-shadow:var(--glow-gold); }
  .clip-rating { font-size:.85rem; color:#aabbcc; }
  .clip-rating span { color:var(--gold); }
  .seller-row { display:flex; align-items:center; gap:.5rem; margin-top:.6rem; padding-top:.6rem; border-top:1px solid rgba(0,238,255,.12); }
  .avatar { width:24px; height:24px; border-radius:50%; background:linear-gradient(135deg,var(--accent),var(--accent2)); display:flex; align-items:center; justify-content:center; font-size:.7rem; color:#000; font-weight:700; box-shadow:0 0 6px rgba(0,238,255,.3); }
  .seller-name { font-size:.85rem; color:var(--muted); }
  /* COMMISSION BANNER */
  .commission-banner { background:#12122a; border:1px solid rgba(139,92,246,.4); border-radius:12px; padding:1rem 1.5rem; margin-bottom:1.5rem; display:flex; align-items:center; justify-content:space-between; box-shadow:0 0 20px rgba(139,92,246,.1); }
  .commission-text { font-size:1rem; }
  .commission-text strong { color:var(--accent); text-shadow:0 0 8px rgba(0,238,255,.4); }
  .commission-text .free-tag { color:var(--green); font-weight:700; text-shadow:0 0 8px rgba(0,255,170,.3); }
</style>
<style>
  /* CHAT PANEL */
  .chat-bar { height:52px; background:rgba(8,8,26,.9); border-top:1px solid rgba(0,238,255,.15); display:flex; align-items:center; padding:0 1.5rem; gap:1rem; cursor:pointer; transition:all .2s; backdrop-filter:blur(10px); }
  .chat-bar:hover { background:rgba(0,238,255,.05); }
  .chat-bar-icon { color:var(--accent); font-size:1.3rem; filter:drop-shadow(0 0 6px rgba(0,238,255,.5)); }
  .chat-bar-label { font-size:1rem; color:var(--text); }
  .chat-unread { background:linear-gradient(135deg,var(--accent),var(--accent2)); color:#000; font-size:.7rem; font-weight:700; padding:.1rem .45rem; border-radius:10px; box-shadow:0 0 8px rgba(0,238,255,.4); animation:pulse 2s infinite; }
  @keyframes pulse { 0%,100%{box-shadow:0 0 8px rgba(0,238,255,.4);} 50%{box-shadow:0 0 16px rgba(0,238,255,.7);} }
  .chat-panel { position:fixed; bottom:52px; right:1.5rem; width:340px; height:480px; background:#0d0d26; border:1px solid rgba(0,238,255,.3); border-radius:12px 12px 0 0; display:flex; flex-direction:column; z-index:200; box-shadow:0 -4px 40px rgba(0,238,255,.12), 0 0 0 1px rgba(0,238,255,.08); transform:translateY(100%); transition:transform .3s ease; backdrop-filter:blur(20px); }
  .chat-panel.open { transform:translateY(0); }
  .chat-header { padding:.8rem 1rem; border-bottom:1px solid rgba(0,238,255,.1); display:flex; align-items:center; justify-content:space-between; background:rgba(0,238,255,.03); }
  .chat-header-info { display:flex; align-items:center; gap:.6rem; }
  .chat-avatar { width:32px; height:32px; border-radius:50%; background:linear-gradient(135deg,var(--accent),var(--accent2)); display:flex; align-items:center; justify-content:center; font-size:.8rem; color:#000; font-weight:700; box-shadow:0 0 10px rgba(0,238,255,.3); }
  .chat-name { font-size:1rem; font-weight:600; }
  .online-dot { width:8px; height:8px; background:var(--green); border-radius:50%; display:inline-block; margin-left:.3rem; box-shadow:0 0 6px rgba(0,255,170,.6); animation:pulse 2s infinite; }
  .chat-close { background:none; border:none; color:var(--muted); cursor:pointer; font-size:1.2rem; transition:color .2s; }
  .chat-close:hover { color:var(--accent); }
  .chat-messages { flex:1; overflow-y:auto; padding:.8rem; display:flex; flex-direction:column; gap:.6rem; }
  .msg { max-width:75%; padding:.5rem .8rem; border-radius:10px; font-size:.95rem; line-height:1.4; }
  .msg.received { background:#1a1a38; border:1px solid rgba(0,238,255,.2); align-self:flex-start; border-radius:4px 10px 10px 10px; color:#f0f4ff; }
  .msg.sent { background:linear-gradient(135deg,rgba(139,92,246,.6),rgba(91,33,182,.7)); color:#fff; align-self:flex-end; border-radius:10px 4px 10px 10px; box-shadow:0 0 10px rgba(139,92,246,.2); }
  .msg-time { font-size:.7rem; color:var(--muted); margin-top:.2rem; }
  .chat-input-row { padding:.7rem; border-top:1px solid rgba(0,238,255,.1); display:flex; gap:.5rem; }
  .chat-input { flex:1; background:rgba(0,238,255,.04); border:1px solid rgba(0,238,255,.15); border-radius:8px; padding:.5rem .8rem; color:var(--text); font-family:var(--font); font-size:.95rem; outline:none; transition:all .2s; }
  .chat-input:focus { border-color:var(--accent); box-shadow:0 0 0 2px rgba(0,238,255,.1); }
  .chat-send { background:linear-gradient(135deg,var(--accent),var(--accent2)); border:none; border-radius:8px; padding:.5rem .9rem; color:#000; cursor:pointer; font-size:1rem; font-weight:700; transition:all .2s; box-shadow:0 0 10px rgba(0,238,255,.2); }
  .chat-send:hover { box-shadow:var(--glow-cyan); transform:scale(1.05); }
  /* ROOM LIST */
  .room-list { display:flex; flex-direction:column; }
  .room-item { padding:.7rem 1rem; display:flex; align-items:center; gap:.7rem; cursor:pointer; border-bottom:1px solid rgba(0,238,255,.06); transition:all .2s; }
  .room-item:hover, .room-item.active { background:rgba(0,238,255,.05); }
  .room-info { flex:1; }
  .room-name { font-size:.95rem; font-weight:600; }
  .room-preview { font-size:.8rem; color:var(--muted); white-space:nowrap; overflow:hidden; text-overflow:ellipsis; max-width:200px; }
  .room-badge { background:linear-gradient(135deg,var(--accent),var(--accent2)); color:#000; font-size:.7rem; font-weight:700; padding:.1rem .4rem; border-radius:10px; box-shadow:0 0 6px rgba(0,238,255,.3); }
  /* MODAL */
  .modal-overlay { position:fixed; inset:0; background:rgba(0,0,10,.8); backdrop-filter:blur(4px); z-index:300; display:none; align-items:center; justify-content:center; }
  .modal-overlay.open { display:flex; }
  .modal { background:#0f0f28; border:1px solid rgba(0,238,255,.3); border-radius:14px; width:480px; max-height:80vh; overflow-y:auto; padding:1.5rem; box-shadow:0 0 60px rgba(0,238,255,.12), 0 0 0 1px rgba(0,238,255,.08); }
  .modal h2 { font-size:1.4rem; margin-bottom:1rem; }
  .modal-close { float:right; background:none; border:none; color:var(--muted); cursor:pointer; font-size:1.3rem; transition:color .2s; }
  .modal-close:hover { color:var(--accent); }
  .price-tag { font-size:2rem; font-weight:700; color:var(--gold); margin:.5rem 0; text-shadow:var(--glow-gold); }
  .modal-actions { display:flex; gap:.8rem; margin-top:1.2rem; }
  .modal-actions .btn { flex:1; padding:.7rem; font-size:1rem; }
  /* SELLER PAGE */
  .seller-profile { background:#131330; border:1px solid rgba(0,238,255,.25); border-radius:12px; padding:1.5rem; margin-bottom:1.5rem; display:flex; gap:1.5rem; align-items:flex-start; box-shadow:0 4px 20px rgba(0,0,0,.5); }
  .seller-avatar-lg { width:72px; height:72px; border-radius:50%; background:linear-gradient(135deg,var(--accent),var(--accent2)); display:flex; align-items:center; justify-content:center; font-size:1.8rem; color:#000; font-weight:700; flex-shrink:0; box-shadow:var(--glow-cyan); }
  .seller-info h2 { font-size:1.4rem; margin-bottom:.3rem; }
  .seller-info p { color:var(--muted); font-size:.95rem; }
  .seller-stats { display:flex; gap:1.5rem; margin-top:.8rem; }
  .s-stat { text-align:center; padding:.5rem .8rem; background:#1a1a38; border:1px solid rgba(0,238,255,.18); border-radius:8px; }
  .s-stat-num { font-size:1.2rem; font-weight:700; color:var(--accent); text-shadow:0 0 8px rgba(0,238,255,.4); }
  .s-stat-label { font-size:.75rem; color:var(--muted); }
  /* UPLOAD FORM */
  .upload-form { background:#131330; border:1px solid rgba(0,238,255,.2); border-radius:12px; padding:1.5rem; }
  .form-group { margin-bottom:1rem; }
  .form-label { display:block; font-size:.9rem; color:#aabbcc; margin-bottom:.4rem; }
  .form-input { width:100%; background:#1a1a3a; border:1px solid rgba(0,238,255,.2); border-radius:6px; padding:.6rem .9rem; color:#f0f4ff; font-family:var(--font); font-size:1rem; outline:none; transition:all .2s; }
  .form-input:focus { border-color:var(--accent); box-shadow:0 0 0 2px rgba(0,238,255,.12); }
  .upload-zone { border:2px dashed rgba(0,238,255,.3); border-radius:8px; padding:2rem; text-align:center; color:#aabbcc; cursor:pointer; transition:all .2s; background:#0f0f28; }
  .upload-zone:hover { border-color:var(--accent); color:var(--accent); background:#141438; box-shadow:inset 0 0 20px rgba(0,238,255,.05); }
  /* BOOKING PAGE */
  .booking-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(300px,1fr)); gap:1.2rem; margin-bottom:2rem; }
  .tutor-card { background:#131330; border:1px solid rgba(0,238,255,.2); border-radius:14px; padding:1.2rem; cursor:pointer; transition:all .3s; box-shadow:0 4px 16px rgba(0,0,0,.5); }
  .tutor-card:hover { border-color:rgba(0,238,255,.5); box-shadow:0 8px 30px rgba(0,238,255,.12); transform:translateY(-3px); }
  .tutor-card-top { display:flex; gap:1rem; align-items:flex-start; margin-bottom:1rem; }
  .tutor-av { width:52px; height:52px; border-radius:50%; background:linear-gradient(135deg,var(--accent),var(--accent2)); display:flex; align-items:center; justify-content:center; font-size:1.4rem; color:#000; font-weight:700; box-shadow:var(--glow-cyan); flex-shrink:0; }
  .tutor-card h3 { font-size:1.15rem; font-weight:700; margin-bottom:.2rem; }
  .tutor-card .subject-tag { display:inline-block; background:rgba(0,238,255,.08); border:1px solid rgba(0,238,255,.2); color:var(--accent); font-size:.82rem; padding:.15rem .55rem; border-radius:4px; margin:.15rem .1rem; }
  .tutor-card .rate { font-size:1.1rem; font-weight:700; color:var(--gold); text-shadow:var(--glow-gold); }
  .slot-section { margin-top:.8rem; }
  .slot-label { font-size:.85rem; color:var(--muted); margin-bottom:.5rem; }
  .slot-grid { display:flex; flex-wrap:wrap; gap:.4rem; }
  .slot-btn { padding:.35rem .75rem; border-radius:6px; border:1px solid rgba(0,238,255,.2); background:rgba(0,238,255,.04); color:var(--text); font-family:var(--font); font-size:.9rem; cursor:pointer; transition:all .2s; }
  .slot-btn:hover, .slot-btn.selected { background:rgba(0,238,255,.15); border-color:var(--accent); color:var(--accent); box-shadow:0 0 8px rgba(0,238,255,.2); }
  .slot-btn.booked { background:rgba(255,50,50,.06); border-color:rgba(255,80,80,.2); color:#ff6b6b; cursor:not-allowed; }
  .book-btn { width:100%; margin-top:.9rem; padding:.6rem; background:linear-gradient(135deg,var(--accent2),#6d28d9); color:#fff; border:none; border-radius:8px; font-family:var(--font); font-size:1rem; font-weight:700; cursor:pointer; transition:all .25s; box-shadow:var(--glow-purple); }
  .book-btn:hover { transform:translateY(-2px); box-shadow:0 0 25px rgba(139,92,246,.5); }
  /* PREVIEW PLAYER */
  .preview-player { background:linear-gradient(135deg,#08082a,#0f0f35); border:1px solid rgba(0,238,255,.25); border-radius:12px; overflow:hidden; margin-bottom:1.5rem; }
  .preview-screen { width:100%; height:220px; background:linear-gradient(135deg,#050518,#0a0a28); display:flex; align-items:center; justify-content:center; position:relative; }
  .preview-screen .big-play { width:70px; height:70px; background:rgba(0,238,255,.12); border:2px solid var(--accent); border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:1.8rem; color:var(--accent); box-shadow:var(--glow-cyan); cursor:pointer; transition:all .3s; }
  .preview-screen .big-play:hover { background:rgba(0,238,255,.25); transform:scale(1.1); }
  .preview-label { position:absolute; top:.7rem; left:.7rem; background:rgba(251,191,36,.15); border:1px solid rgba(251,191,36,.4); color:var(--gold); font-size:.8rem; font-weight:700; padding:.2rem .6rem; border-radius:4px; }
  .preview-timer { position:absolute; bottom:.7rem; right:.7rem; background:rgba(0,0,0,.6); color:var(--accent); font-size:.85rem; padding:.2rem .6rem; border-radius:4px; border:1px solid rgba(0,238,255,.2); }
  .preview-bar { padding:1rem 1.2rem; display:flex; align-items:center; justify-content:space-between; border-top:1px solid rgba(0,238,255,.1); }
  .preview-info { font-size:.95rem; color:var(--muted); }
  .preview-info strong { color:var(--text); }
  .unlock-btn { background:linear-gradient(135deg,var(--gold),#f97316); color:#000; border:none; border-radius:8px; padding:.55rem 1.2rem; font-family:var(--font); font-size:1rem; font-weight:700; cursor:pointer; transition:all .25s; box-shadow:var(--glow-gold); }
  .unlock-btn:hover { transform:translateY(-2px); box-shadow:0 0 25px rgba(251,191,36,.5); }
  /* LOCK OVERLAY */
  .lock-overlay { position:absolute; inset:0; background:linear-gradient(to bottom,transparent 30%,rgba(5,5,18,.97) 70%); display:flex; flex-direction:column; align-items:center; justify-content:flex-end; padding-bottom:1.5rem; }
  .lock-icon { font-size:2.5rem; margin-bottom:.5rem; filter:drop-shadow(0 0 10px rgba(251,191,36,.5)); }
  .lock-text { color:var(--text); font-size:1rem; text-align:center; }
  .lock-text span { color:var(--gold); font-weight:700; }
</style>
</head>
<body>
<nav>
  <div>
    <div class="logo">Help exaM <span>Clip Marketplace · Economics CMU</span></div>
  </div>
  <div class="nav-links">
    <a class="active" onclick="showPage('home')">หน้าหลัก</a>
    <a onclick="showPage('browse')">เลือกซื้อคลิป</a>
    <a onclick="showPage('booking')">📅 จองตารางเวลาเรียน</a>
    <a onclick="showPage('seller')">พื้นที่ผู้ขาย</a>
    <a onclick="showPage('upload')">อัปโหลดคลิป</a>
  </div>
  <div class="nav-right">
    <button class="btn btn-outline" onclick="showModal('loginModal')">เข้าสู่ระบบ</button>
    <button class="btn btn-primary" onclick="showModal('registerModal')">สมัครสมาชิก</button>
  </div>
</nav>

<div class="app">
  <!-- HOME PAGE -->
  <div id="page-home" class="main-content">
    <div class="hero">
      <div class="hero-tag">▸ Economics · CMU · Clip Marketplace</div>
      <h1>เรียนรู้ผ่าน<em>คลิปสรุป</em> จากรุ่นพี่ที่ผ่านมาแล้ว</h1>
      <p>คลิปสรุป Midterm & Final จากนักศึกษาเศรษฐศาสตร์ มช. ที่ผ่านวิชานั้นมาแล้ว</p>
      <div class="hero-stats">
        <div class="stat"><div class="stat-num">80+</div><div class="stat-label">วิชา</div></div>
        <div class="stat"><div class="stat-num">240+</div><div class="stat-label">คลิปสรุป</div></div>
        <div class="stat"><div class="stat-num">1,200+</div><div class="stat-label">ผู้ใช้งาน</div></div>
        <div class="stat"><div class="stat-num">4.8★</div><div class="stat-label">คะแนนเฉลี่ย</div></div>
      </div>
    </div>

    <div class="commission-banner">
      <div class="commission-text">
        🎯 ผู้ขายคลิปใหม่ <span class="free-tag">ฟรี 3 เดือนแรก</span> — แพลตฟอร์มหารายได้ผ่าน <strong>ค่าคอมมิชชั่น</strong> จากการขายคลิปของคุณ
      </div>
      <button class="btn btn-primary" onclick="showPage('upload')">เริ่มขายเลย →</button>
    </div>

    <div class="tabs">
      <button class="tab active" onclick="filterClips('all',this)">ทั้งหมด</button>
      <button class="tab" onclick="filterClips('midterm',this)">Midterm</button>
      <button class="tab" onclick="filterClips('final',this)">Final</button>
      <button class="tab" onclick="filterClips('free',this)">ฟรี</button>
    </div>

    <div class="search-bar">
      <input class="search-input" placeholder="ค้นหาวิชา เช่น 751301, Microeconomic, เศรษฐศาสตร์จุลภาค..." oninput="searchClips(this.value)">
      <button class="filter-btn active">Midterm</button>
      <button class="filter-btn">Final</button>
      <button class="filter-btn">ราคา ↑</button>
    </div>

    <div class="clip-grid" id="clipGrid"></div>
  </div>

  <!-- BROWSE PAGE -->
  <div id="page-browse" class="main-content" style="display:none">
    <h2 style="margin-bottom:1rem;font-size:1.5rem;">เลือกซื้อคลิปสรุป</h2>
    <div class="search-bar">
      <input class="search-input" placeholder="ค้นหาวิชา...">
      <button class="filter-btn active">ทั้งหมด</button>
      <button class="filter-btn">Midterm</button>
      <button class="filter-btn">Final</button>
    </div>
    <div class="clip-grid" id="browseGrid"></div>
  </div>

  <!-- SELLER PAGE -->
  <div id="page-seller" class="main-content" style="display:none">
    <div class="seller-profile">
      <div class="seller-avatar-lg">ก</div>
      <div class="seller-info">
        <h2>กานต์ เศรษฐกิจ <span class="badge-free" style="font-size:.8rem;">ฟรี 3 เดือน</span></h2>
        <p>นักศึกษาเศรษฐศาสตร์ ปี 4 · มหาวิทยาลัยเชียงใหม่</p>
        <p style="color:var(--accent);font-size:.9rem;margin-top:.3rem;">เชี่ยวชาญ: เศรษฐศาสตร์จุลภาค, มหภาค, เศรษฐมิติ</p>
        <div class="seller-stats">
          <div class="s-stat"><div class="s-stat-num">12</div><div class="s-stat-label">คลิปที่ขาย</div></div>
          <div class="s-stat"><div class="s-stat-num">฿2,840</div><div class="s-stat-label">รายได้รวม</div></div>
          <div class="s-stat"><div class="s-stat-num">4.9★</div><div class="s-stat-label">คะแนน</div></div>
          <div class="s-stat"><div class="s-stat-num">89</div><div class="s-stat-label">ผู้ซื้อ</div></div>
        </div>
      </div>
    </div>
    <h3 style="margin-bottom:1rem;">คลิปของฉัน</h3>
    <div class="clip-grid" id="sellerGrid"></div>
  </div>

  <!-- UPLOAD PAGE -->
  <div id="page-upload" class="main-content" style="display:none">
    <h2 style="margin-bottom:1.2rem;font-size:1.5rem;">อัปโหลดคลิปสรุป</h2>
    <div class="commission-banner" style="margin-bottom:1.2rem;">
      <div class="commission-text">💡 <span class="free-tag">3 เดือนแรกฟรี!</span> หลังจากนั้นแพลตฟอร์มหักค่าคอมมิชชั่น <strong>15%</strong> จากยอดขายแต่ละคลิป</div>
    </div>
    <div class="upload-form">
      <div class="form-group">
        <label class="form-label">วิชา</label>
        <select class="form-input">
          <option>751301 — ทฤษฎีเศรษฐศาสตร์จุลภาค 1</option>
          <option>751302 — ทฤษฎีเศรษฐศาสตร์จุลภาค 2</option>
          <option>751308 — ทฤษฎีเศรษฐศาสตร์มหภาค 1</option>
          <option>751305 — เศรษฐมิติ 1</option>
          <option>751304 — เศรษฐศาสตร์สถิติ</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">ประเภท</label>
        <select class="form-input">
          <option>Midterm</option>
          <option>Final</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">ชื่อคลิป</label>
        <input class="form-input" placeholder="เช่น สรุป Micro 1 Midterm ครบทุก Chapter">
      </div>
      <div class="form-group">
        <label class="form-label">ราคา (บาท) — 0 = ฟรี</label>
        <input class="form-input" type="number" placeholder="เช่น 49" value="49">
      </div>
      <div class="form-group">
        <label class="form-label">อัปโหลดไฟล์วิดีโอ</label>
        <div class="upload-zone">📹 ลากไฟล์มาวางที่นี่ หรือคลิกเพื่อเลือกไฟล์<br><small style="color:var(--muted)">MP4, MOV — ไม่เกิน 2GB</small></div>
      </div>
      <button class="btn btn-primary" style="width:100%;padding:.8rem;font-size:1.1rem;">อัปโหลดและเผยแพร่</button>
    </div>
  </div>

  <!-- BOOKING PAGE -->
  <div id="page-booking" class="main-content" style="display:none">
    <h2 style="font-size:1.6rem;margin-bottom:.4rem;">📅 นัดเวลาเรียนนอกรอบ</h2>
    <p style="color:var(--muted);font-size:1rem;margin-bottom:1.2rem;">เลือกผู้ขายคลิป → ดูตัวอย่าง 1 นาที → นัดเวลา → จ่ายเงินปลดล็อคคลิปเต็ม</p>

    <!-- PREVIEW PLAYER -->
    <div class="preview-player">
      <div class="preview-screen">
        <div class="big-play" onclick="togglePreview(this)">▶</div>
        <span class="preview-label">⏱ ตัวอย่าง 1 นาที</span>
        <span class="preview-timer" id="previewTimer">01:00</span>
        <div class="lock-overlay" id="lockOverlay">
          <div class="lock-icon">🔒</div>
          <div class="lock-text">คลิปเต็ม <span>45 นาที</span> — ปลดล็อคด้วยการซื้อ<br>
            <button class="unlock-btn" style="margin-top:.6rem;" onclick="showModal('payModal')">🔓 ซื้อเพื่อดูคลิปเต็ม — ฿49</button>
          </div>
        </div>
      </div>
      <div class="preview-bar">
        <div class="preview-info">กำลังดู: <strong>สรุป Micro 1 Midterm</strong> โดย กานต์ เศรษฐกิจ</div>
        <button class="unlock-btn" onclick="showModal('payModal')">🔓 ปลดล็อคคลิปเต็ม ฿49</button>
      </div>
    </div>

    <h3 style="font-size:1.3rem;margin-bottom:1rem;color:var(--accent);text-shadow:0 0 8px rgba(0,238,255,.3);">เลือกผู้สอนและนัดเวลา</h3>
    <div class="booking-grid">
      <!-- TUTOR 1 -->
      <div class="tutor-card">
        <div class="tutor-card-top">
          <div class="tutor-av">ก</div>
          <div style="flex:1">
            <h3>กานต์ เศรษฐกิจ</h3>
            <div style="margin:.3rem 0;">
              <span class="subject-tag">751301 Micro 1</span>
              <span class="subject-tag">751302 Micro 2</span>
            </div>
            <div style="display:flex;align-items:center;gap:.8rem;">
              <span class="rate">฿200/ชม.</span>
              <span style="color:var(--gold);font-size:.9rem;">⭐ 4.9</span>
            </div>
          </div>
        </div>
        <div class="slot-section">
          <div class="slot-label">📅 เลือกวันและเวลา (สัปดาห์นี้)</div>
          <div style="margin-bottom:.5rem;font-size:.9rem;color:var(--muted);">จันทร์ 9 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn" onclick="selectSlot(this)">09:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">11:00</button>
            <button class="slot-btn booked" disabled>13:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">15:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">17:00</button>
          </div>
          <div style="margin:.5rem 0;font-size:.9rem;color:var(--muted);">อังคาร 10 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn booked" disabled>09:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">10:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">14:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">16:00</button>
          </div>
        </div>
        <button class="book-btn" onclick="showModal('bookConfirmModal')">📅 ยืนยันนัดเรียน</button>
      </div>

      <!-- TUTOR 2 -->
      <div class="tutor-card">
        <div class="tutor-card-top">
          <div class="tutor-av" style="background:linear-gradient(135deg,var(--gold),#d97706);">ป</div>
          <div style="flex:1">
            <h3>ปิยะ มหภาค</h3>
            <div style="margin:.3rem 0;">
              <span class="subject-tag">751308 Macro 1</span>
              <span class="subject-tag">751309 Macro 2</span>
            </div>
            <div style="display:flex;align-items:center;gap:.8rem;">
              <span class="rate">฿180/ชม.</span>
              <span style="color:var(--gold);font-size:.9rem;">⭐ 4.8</span>
            </div>
          </div>
        </div>
        <div class="slot-section">
          <div class="slot-label">📅 เลือกวันและเวลา (สัปดาห์นี้)</div>
          <div style="margin-bottom:.5rem;font-size:.9rem;color:var(--muted);">จันทร์ 9 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn" onclick="selectSlot(this)">10:00</button>
            <button class="slot-btn booked" disabled>12:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">14:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">18:00</button>
          </div>
          <div style="margin:.5rem 0;font-size:.9rem;color:var(--muted);">พุธ 11 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn" onclick="selectSlot(this)">09:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">11:00</button>
            <button class="slot-btn booked" disabled>15:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">17:00</button>
          </div>
        </div>
        <button class="book-btn" onclick="showModal('bookConfirmModal')">📅 ยืนยันนัดเรียน</button>
      </div>

      <!-- TUTOR 3 -->
      <div class="tutor-card">
        <div class="tutor-card-top">
          <div class="tutor-av" style="background:linear-gradient(135deg,var(--green),#00aa77);">ส</div>
          <div style="flex:1">
            <h3>สมใจ เศรษฐมิติ</h3>
            <div style="margin:.3rem 0;">
              <span class="subject-tag">751305 Econometrics 1</span>
              <span class="subject-tag">751403 Econometrics 2</span>
            </div>
            <div style="display:flex;align-items:center;gap:.8rem;">
              <span class="rate">฿220/ชม.</span>
              <span style="color:var(--gold);font-size:.9rem;">⭐ 4.7</span>
            </div>
          </div>
        </div>
        <div class="slot-section">
          <div class="slot-label">📅 เลือกวันและเวลา (สัปดาห์นี้)</div>
          <div style="margin-bottom:.5rem;font-size:.9rem;color:var(--muted);">อังคาร 10 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn" onclick="selectSlot(this)">08:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">10:00</button>
            <button class="slot-btn booked" disabled>13:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">16:00</button>
          </div>
          <div style="margin:.5rem 0;font-size:.9rem;color:var(--muted);">พฤหัส 12 เม.ย.</div>
          <div class="slot-grid">
            <button class="slot-btn booked" disabled>09:00 เต็ม</button>
            <button class="slot-btn" onclick="selectSlot(this)">11:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">14:00</button>
            <button class="slot-btn" onclick="selectSlot(this)">19:00</button>
          </div>
        </div>
        <button class="book-btn" onclick="showModal('bookConfirmModal')">📅 ยืนยันนัดเรียน</button>
      </div>
    </div>
  </div>

  <!-- CHAT BAR -->
  <div class="chat-bar" onclick="toggleChat()">
    <span class="chat-bar-icon">💬</span>
    <span class="chat-bar-label">แชท</span>
    <span class="chat-unread" id="chatBadge">3</span>
    <span style="margin-left:auto;color:var(--muted);font-size:.85rem;" id="chatBarHint">คลิกเพื่อเปิดแชท ▲</span>
  </div>
</div>
""

<!-- CHAT PANEL -->
<div class="chat-panel" id="chatPanel">
  <div class="chat-header">
    <div class="chat-header-info">
      <div class="chat-avatar">ก</div>
      <div>
        <div class="chat-name">กานต์ เศรษฐกิจ <span class="online-dot"></span></div>
        <div style="font-size:.75rem;color:var(--muted);">ผู้ขายคลิป · 751301</div>
      </div>
    </div>
    <div style="display:flex;gap:.5rem;align-items:center;">
      <button class="btn btn-outline" style="font-size:.8rem;padding:.3rem .7rem;" onclick="showRoomList()">รายการแชท</button>
      <button class="chat-close" onclick="toggleChat()">✕</button>
    </div>
  </div>
  <div id="roomListView" style="display:none;" class="room-list">
    <div class="room-item active" onclick="openRoom('กานต์ เศรษฐกิจ','ก','ผู้ขายคลิป · 751301')">
      <div class="chat-avatar">ก</div>
      <div class="room-info">
        <div class="room-name">กานต์ เศรษฐกิจ</div>
        <div class="room-preview">ขอบคุณที่ซื้อคลิปนะครับ...</div>
      </div>
      <span class="room-badge">2</span>
    </div>
    <div class="room-item" onclick="openRoom('ปิยะ มหภาค','ป','ผู้ขายคลิป · 751308')">
      <div class="chat-avatar" style="background:linear-gradient(135deg,var(--gold),#d97706);">ป</div>
      <div class="room-info">
        <div class="room-name">ปิยะ มหภาค</div>
        <div class="room-preview">คลิปครอบคลุม Chapter 1-8 ครับ</div>
      </div>
      <span class="room-badge">1</span>
    </div>
    <div class="room-item" onclick="openRoom('สมใจ เศรษฐมิติ','ส','ผู้ขายคลิป · 751305')">
      <div class="chat-avatar" style="background:linear-gradient(135deg,var(--green),#059669);">ส</div>
      <div class="room-info">
        <div class="room-name">สมใจ เศรษฐมิติ</div>
        <div class="room-preview">มีคลิป Final ด้วยครับ</div>
      </div>
    </div>
  </div>
  <div id="chatView">
    <div class="chat-messages" id="chatMessages">
      <div class="msg received">สวัสดีครับ ขอบคุณที่ซื้อคลิปสรุป Micro 1 Midterm นะครับ 😊<div class="msg-time">10:32</div></div>
      <div class="msg sent">ขอบคุณครับ คลิปครอบคลุม Chapter ไหนบ้างครับ?<div class="msg-time">10:33</div></div>
      <div class="msg received">ครอบคลุม Chapter 1-6 ครับ ทั้ง Consumer Theory, Producer Theory และ Market Structure<div class="msg-time">10:34</div></div>
      <div class="msg sent">โอเคครับ มี Final ด้วยไหมครับ?<div class="msg-time">10:35</div></div>
      <div class="msg received">มีครับ กำลังทำอยู่ จะอัปโหลดสัปดาห์หน้าครับ 📹<div class="msg-time">10:36</div></div>
    </div>
    <div class="chat-input-row">
      <input class="chat-input" id="chatInput" placeholder="พิมพ์ข้อความ..." onkeydown="if(event.key==='Enter')sendMsg()">
      <button class="chat-send" onclick="sendMsg()">➤</button>
    </div>
  </div>
</div>

<!-- CLIP MODAL -->
<div class="modal-overlay" id="clipModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('clipModal')">✕</button>
    <div style="color:var(--accent);font-size:.85rem;margin-bottom:.3rem;" id="modalSubject">751301 — ทฤษฎีเศรษฐศาสตร์จุลภาค 1</div>
    <h2 id="modalTitle">สรุป Micro 1 Midterm ครบทุก Chapter</h2>
    <div style="display:flex;gap:.5rem;margin:.5rem 0;">
      <span class="clip-type-badge badge-mid">Midterm</span>
      <span style="color:var(--muted);font-size:.85rem;">⏱ 45 นาที · 👁 234 ครั้ง · ⭐ 4.9</span>
    </div>
    <div class="price-tag" id="modalPrice">฿49</div>
    <p style="color:var(--muted);font-size:.95rem;line-height:1.6;">คลิปสรุปครอบคลุม Consumer Theory, Producer Theory, Market Structure และ Game Theory พร้อมตัวอย่างโจทย์ที่ออกสอบบ่อย</p>
    <div style="margin-top:1rem;padding:.8rem;background:var(--bg3);border-radius:8px;border:1px solid var(--border);">
      <div style="font-size:.85rem;color:var(--muted);">ผู้ขาย</div>
      <div style="display:flex;align-items:center;gap:.6rem;margin-top:.4rem;">
        <div class="avatar" style="width:32px;height:32px;font-size:.9rem;">ก</div>
        <div><div style="font-size:.95rem;font-weight:600;">กานต์ เศรษฐกิจ</div><div style="font-size:.8rem;color:var(--muted);">⭐ 4.9 · 12 คลิป</div></div>
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn btn-outline" onclick="openChatFromModal()">💬 ถามผู้ขาย</button>
      <button class="btn btn-primary" onclick="closeModal('clipModal')">🛒 ซื้อคลิปนี้</button>
    </div>
  </div>
</div>

<!-- LOGIN MODAL -->
<div class="modal-overlay" id="loginModal">
  <div class="modal" style="width:320px; padding:1.6rem;">
    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:1.4rem;">
      <h2 style="font-size:.88rem; margin:0;">เข้าสู่ระบบ</h2>
      <button class="modal-close" onclick="closeModal('loginModal')" style="font-size:.9rem; line-height:1;">✕</button>
    </div>
    <div class="form-group" style="margin-bottom:.75rem;">
      <label class="form-label" style="font-size:.65rem; margin-bottom:.3rem;">อีเมล</label>
      <input class="form-input" type="email" placeholder="your@email.com" style="font-size:.68rem; padding:.5rem .75rem;">
    </div>
    <div class="form-group" style="margin-bottom:1rem;">
      <label class="form-label" style="font-size:.65rem; margin-bottom:.3rem;">รหัสผ่าน</label>
      <input class="form-input" type="password" placeholder="••••••••" style="font-size:.68rem; padding:.5rem .75rem;">
    </div>
    <button class="btn btn-primary" style="width:100%; padding:.55rem; font-size:.72rem;" onclick="closeModal('loginModal')">เข้าสู่ระบบ</button>
    <div style="display:flex; align-items:center; gap:.6rem; margin:.75rem 0;">
      <div style="flex:1; height:1px; background:rgba(0,238,255,.15);"></div>
      <span style="font-size:.62rem; color:var(--muted);">หรือ</span>
      <div style="flex:1; height:1px; background:rgba(0,238,255,.15);"></div>
    </div>
    <button class="btn btn-outline" style="width:100%; padding:.55rem; font-size:.72rem; display:flex; align-items:center; justify-content:center; gap:.5rem;">
      <span style="font-size:.8rem;">🔵</span> เข้าสู่ระบบด้วย Google
    </button>
  </div>
</div>

<!-- REGISTER MODAL -->
<div class="modal-overlay" id="registerModal">
  <div class="modal" style="width:360px; background:#ffffff; border:1px solid #e2e8f0; box-shadow:0 8px 40px rgba(0,0,0,.3);">
    <button class="modal-close" style="color:#666;" onclick="closeModal('registerModal')">✕</button>
    <h2 style="margin-bottom:1.2rem; color:#111; font-size:.9rem;">สมัครสมาชิก</h2>
    <div class="form-group"><label class="form-label" style="color:#555;">ชื่อ-นามสกุล</label><input class="form-input" style="background:#f8fafc;border:1px solid #cbd5e1;color:#111;font-size:.72rem;" placeholder="ชื่อ นามสกุล"></div>
    <div class="form-group"><label class="form-label" style="color:#555;">อีเมล</label><input class="form-input" type="email" style="background:#f8fafc;border:1px solid #cbd5e1;color:#111;font-size:.72rem;" placeholder="your@email.com"></div>
    <div class="form-group"><label class="form-label" style="color:#555;">รหัสผ่าน</label><input class="form-input" type="password" style="background:#f8fafc;border:1px solid #cbd5e1;color:#111;font-size:.72rem;" placeholder="••••••••"></div>
    <div class="form-group">
      <label class="form-label" style="color:#555;">บทบาท</label>
      <select class="form-input" style="background:#f8fafc;border:1px solid #cbd5e1;color:#111;font-size:.72rem;"><option>ผู้ซื้อคลิป (Student)</option><option>ผู้ขายคลิป (Seller)</option></select>
    </div>
    <div style="background:#f0fdf4;border:1px solid #86efac;border-radius:6px;padding:.6rem;font-size:.68rem;color:#16a34a;margin-bottom:.9rem;">
      ✅ ผู้ขายคลิปใหม่ ฟรี 3 เดือนแรก ไม่มีค่าธรรมเนียม
    </div>
    <button class="btn btn-primary" style="width:100%;padding:.65rem;font-size:.72rem;" onclick="closeModal('registerModal')">สมัครสมาชิก</button>
  </div>
</div>

<!-- PAY MODAL -->
<div class="modal-overlay" id="payModal">
  <div class="modal" style="width:420px;">
    <button class="modal-close" onclick="closeModal('payModal')">✕</button>
    <div style="text-align:center;margin-bottom:1rem;">
      <div style="font-size:2.5rem;margin-bottom:.3rem;">🔓</div>
      <h2 style="font-size:1.4rem;">ปลดล็อคคลิปเต็ม</h2>
      <div style="color:var(--muted);font-size:.95rem;margin-top:.3rem;">สรุป Micro 1 Midterm ครบทุก Chapter</div>
    </div>
    <div style="background:rgba(251,191,36,.06);border:1px solid rgba(251,191,36,.25);border-radius:10px;padding:1rem;margin-bottom:1rem;">
      <div style="display:flex;justify-content:space-between;margin-bottom:.4rem;font-size:1rem;">
        <span style="color:var(--muted);">คลิปเต็ม (45 นาที)</span><span>฿49</span>
      </div>
      <div style="display:flex;justify-content:space-between;margin-bottom:.4rem;font-size:1rem;">
        <span style="color:var(--muted);">ค่าธรรมเนียมแพลตฟอร์ม</span><span style="color:var(--muted);">฿0 (ฟรี 3 เดือน)</span>
      </div>
      <div style="border-top:1px solid rgba(251,191,36,.2);padding-top:.5rem;display:flex;justify-content:space-between;font-size:1.2rem;font-weight:700;">
        <span>รวม</span><span style="color:var(--gold);text-shadow:var(--glow-gold);">฿49</span>
      </div>
    </div>
    <div class="form-group"><label class="form-label">ชำระผ่าน</label>
      <select class="form-input">
        <option>💳 บัตรเครดิต / เดบิต</option>
        <option>📱 QR Code PromptPay</option>
      </select>
    </div>
    <button class="btn btn-primary" style="width:100%;padding:.8rem;font-size:1.1rem;" onclick="closeModal('payModal');alert('✅ ชำระเงินสำเร็จ! คลิปเต็มพร้อมดูแล้ว')">💳 ชำระเงิน ฿49</button>
  </div>
</div>

<!-- BOOK CONFIRM MODAL -->
<div class="modal-overlay" id="bookConfirmModal">
  <div class="modal" style="width:420px;">
    <button class="modal-close" onclick="closeModal('bookConfirmModal')">✕</button>
    <div style="text-align:center;margin-bottom:1rem;">
      <div style="font-size:2.5rem;margin-bottom:.3rem;">📅</div>
      <h2 style="font-size:1.4rem;">ยืนยันการนัดเรียน</h2>
    </div>
    <div style="background:rgba(0,238,255,.04);border:1px solid rgba(0,238,255,.2);border-radius:10px;padding:1rem;margin-bottom:1rem;font-size:1rem;">
      <div style="display:flex;justify-content:space-between;margin-bottom:.5rem;">
        <span style="color:var(--muted);">ผู้สอน</span><span style="font-weight:700;">กานต์ เศรษฐกิจ</span>
      </div>
      <div style="display:flex;justify-content:space-between;margin-bottom:.5rem;">
        <span style="color:var(--muted);">วิชา</span><span>751301 Micro 1</span>
      </div>
      <div style="display:flex;justify-content:space-between;margin-bottom:.5rem;">
        <span style="color:var(--muted);">วันเวลา</span><span style="color:var(--accent);">จันทร์ 9 เม.ย. · 09:00–10:00</span>
      </div>
      <div style="display:flex;justify-content:space-between;margin-bottom:.5rem;">
        <span style="color:var(--muted);">รูปแบบ</span><span>Online (Zoom)</span>
      </div>
      <div style="border-top:1px solid rgba(0,238,255,.15);padding-top:.5rem;display:flex;justify-content:space-between;font-size:1.15rem;font-weight:700;">
        <span>ค่าเรียน</span><span style="color:var(--gold);text-shadow:var(--glow-gold);">฿200</span>
      </div>
    </div>
    <div style="background:rgba(0,255,170,.05);border:1px solid rgba(0,255,170,.2);border-radius:8px;padding:.7rem;font-size:.95rem;color:var(--green);margin-bottom:1rem;">
      💬 หลังยืนยัน ระบบจะเปิดแชทกับผู้สอนให้อัตโนมัติ
    </div>
    <div class="modal-actions">
      <button class="btn btn-outline" onclick="closeModal('bookConfirmModal')">ยกเลิก</button>
      <button class="btn btn-primary" onclick="closeModal('bookConfirmModal');if(!chatOpen)toggleChat();alert('✅ นัดเรียนสำเร็จ! ผู้สอนจะยืนยันภายใน 24 ชม.')">✅ ยืนยันและชำระเงิน</button>
    </div>
  </div>
</div>

<script>
const clips = [
  { id:1, subject:'751301', subjectName:'ทฤษฎีเศรษฐศาสตร์จุลภาค 1', title:'สรุป Micro 1 Midterm ครบทุก Chapter', type:'midterm', price:49, rating:4.9, views:234, seller:'กานต์', sellerInit:'ก' },
  { id:2, subject:'751308', subjectName:'ทฤษฎีเศรษฐศาสตร์มหภาค 1', title:'Macro 1 Final — GDP, Inflation, Monetary Policy', type:'final', price:59, rating:4.8, views:189, seller:'ปิยะ', sellerInit:'ป' },
  { id:3, subject:'751305', subjectName:'เศรษฐมิติ 1', title:'Econometrics สรุป OLS + Hypothesis Testing', type:'midterm', price:0, rating:4.7, views:312, seller:'สมใจ', sellerInit:'ส' },
  { id:4, subject:'751302', subjectName:'ทฤษฎีเศรษฐศาสตร์จุลภาค 2', title:'Micro 2 Final — Game Theory & Welfare', type:'final', price:69, rating:5.0, views:98, seller:'กานต์', sellerInit:'ก' },
  { id:5, subject:'751304', subjectName:'เศรษฐศาสตร์สถิติ', title:'Statistics สรุปสูตรและตัวอย่างโจทย์ Midterm', type:'midterm', price:39, rating:4.6, views:156, seller:'วิภา', sellerInit:'ว' },
  { id:6, subject:'751401', subjectName:'เศรษฐศาสตร์ระหว่างประเทศ', title:'International Econ Final — Trade Theory', type:'final', price:0, rating:4.8, views:201, seller:'ธนา', sellerInit:'ธ' },
];

function renderClips(data, containerId) {
  const grid = document.getElementById(containerId);
  grid.innerHTML = data.map(c => `
    <div class="clip-card" onclick="openClip(${c.id})">
      <div class="clip-thumb">
        <div class="play-icon">▶</div>
        <span class="clip-type-badge ${c.type==='midterm'?'badge-mid':'badge-fin'}">${c.type==='midterm'?'Midterm':'Final'}</span>
      </div>
      <div class="clip-info">
        <div class="clip-subject">${c.subject} — ${c.subjectName}</div>
        <div class="clip-title">${c.title}</div>
        <div class="clip-meta">
          <div class="clip-price ${c.price>0?'paid':''}">${c.price===0?'ฟรี':'฿'+c.price}</div>
          <div class="clip-rating"><span>★</span> ${c.rating} · 👁 ${c.views}</div>
        </div>
        <div class="seller-row">
          <div class="avatar">${c.sellerInit}</div>
          <span class="seller-name">${c.seller}</span>
          ${c.price===0?'<span class="badge-free">ฟรี</span>':''}
        </div>
      </div>
    </div>`).join('');
}

renderClips(clips, 'clipGrid');
renderClips(clips, 'browseGrid');
renderClips(clips.slice(0,3), 'sellerGrid');

function filterClips(type, el) {
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  el.classList.add('active');
  const filtered = type==='all' ? clips : type==='free' ? clips.filter(c=>c.price===0) : clips.filter(c=>c.type===type);
  renderClips(filtered, 'clipGrid');
}

function searchClips(q) {
  const filtered = clips.filter(c => c.title.toLowerCase().includes(q.toLowerCase()) || c.subject.includes(q) || c.subjectName.includes(q));
  renderClips(filtered, 'clipGrid');
}

function openClip(id) {
  const c = clips.find(x=>x.id===id);
  document.getElementById('modalSubject').textContent = c.subject+' — '+c.subjectName;
  document.getElementById('modalTitle').textContent = c.title;
  document.getElementById('modalPrice').textContent = c.price===0?'ฟรี':'฿'+c.price;
  showModal('clipModal');
}

function showPage(page) {
  document.querySelectorAll('[id^="page-"]').forEach(p=>p.style.display='none');
  document.getElementById('page-'+page).style.display='block';
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('active'));
  const map = {home:0,browse:1,booking:2,seller:3,upload:4};
  document.querySelectorAll('.nav-links a')[map[page]]?.classList.add('active');
}

let chatOpen = false;
function toggleChat() {
  chatOpen = !chatOpen;
  document.getElementById('chatPanel').classList.toggle('open', chatOpen);
  document.getElementById('chatBarHint').textContent = chatOpen ? 'คลิกเพื่อปิดแชท ▼' : 'คลิกเพื่อเปิดแชท ▲';
  if(chatOpen) { document.getElementById('chatBadge').style.display='none'; document.getElementById('roomListView').style.display='none'; document.getElementById('chatView').style.display='flex'; document.getElementById('chatView').style.flexDirection='column'; document.getElementById('chatView').style.flex='1'; }
}

function showRoomList() {
  document.getElementById('roomListView').style.display='block';
  document.getElementById('chatView').style.display='none';
}

function openRoom(name, init, sub) {
  document.getElementById('roomListView').style.display='none';
  document.getElementById('chatView').style.display='flex';
  document.getElementById('chatView').style.flexDirection='column';
  document.getElementById('chatView').style.flex='1';
  document.querySelector('.chat-name').innerHTML = name+' <span class="online-dot"></span>';
  document.querySelector('.chat-header-info .chat-avatar').textContent = init;
  document.querySelector('.chat-header-info div > div:last-child').textContent = sub;
}

function sendMsg() {
  const input = document.getElementById('chatInput');
  const text = input.value.trim();
  if(!text) return;
  const msgs = document.getElementById('chatMessages');
  const now = new Date(); const time = now.getHours()+':'+String(now.getMinutes()).padStart(2,'0');
  msgs.innerHTML += `<div class="msg sent">${text}<div class="msg-time">${time}</div></div>`;
  input.value = '';
  msgs.scrollTop = msgs.scrollHeight;
  setTimeout(()=>{ msgs.innerHTML += `<div class="msg received">ขอบคุณครับ จะตอบให้เร็วที่สุด 😊<div class="msg-time">${time}</div></div>`; msgs.scrollTop=msgs.scrollHeight; }, 1200);
}

function openChatFromModal() {
  closeModal('clipModal');
  if(!chatOpen) toggleChat();
}

function showModal(id) { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }
document.querySelectorAll('.modal-overlay').forEach(m=>m.addEventListener('click',e=>{ if(e.target===m) m.classList.remove('open'); }));

// SLOT SELECTION
function selectSlot(btn) {
  const parent = btn.closest('.slot-grid');
  parent.querySelectorAll('.slot-btn').forEach(b=>b.classList.remove('selected'));
  btn.classList.add('selected');
}

// PREVIEW TIMER
let previewInterval = null, previewSec = 60, previewPlaying = false;
function togglePreview(btn) {
  if(!previewPlaying) {
    previewPlaying = true;
    btn.textContent = '⏸';
    document.getElementById('lockOverlay').style.opacity = '0.3';
    previewInterval = setInterval(()=>{
      previewSec--;
      const m = String(Math.floor(previewSec/60)).padStart(2,'0');
      const s = String(previewSec%60).padStart(2,'0');
      document.getElementById('previewTimer').textContent = m+':'+s;
      if(previewSec <= 0) {
        clearInterval(previewInterval);
        previewPlaying = false;
        btn.textContent = '▶';
        previewSec = 60;
        document.getElementById('previewTimer').textContent = '01:00';
        document.getElementById('lockOverlay').style.opacity = '1';
        showModal('payModal');
      }
    }, 1000);
  } else {
    previewPlaying = false;
    clearInterval(previewInterval);
    btn.textContent = '▶';
    document.getElementById('lockOverlay').style.opacity = '1';
  }
}
</script>
</body>
</html>

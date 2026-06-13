# Namisar-Ailua
Photography and Cinematik

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Namisar Aulia Project</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0D0D0D;
      --surface: #161616;
      --surface2: #1F1F1F;
      --border: #2A2A2A;
      --text: #F5F2ED;
      --muted: #888;
      --rose: #C9A99A;
      --gold: #B8965A;
      --gold-light: #D4B07A;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      font-weight: 300;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── SCROLLBAR ── */
    ::-webkit-scrollbar { width: 4px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--gold); border-radius: 2px; }

    /* ── HEADER ── */
    header {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 20px 48px;
      background: linear-gradient(to bottom, rgba(13,13,13,0.95), transparent);
      backdrop-filter: blur(2px);
    }

    .logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 22px;
      font-weight: 300;
      letter-spacing: 0.12em;
      color: var(--text);
      text-decoration: none;
    }

    .logo span {
      color: var(--gold);
      font-style: italic;
    }

    nav {
      display: flex; gap: 36px; align-items: center;
    }

    nav a {
      font-size: 11px;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.3s;
    }

    nav a:hover { color: var(--text); }

    /* ── HERO ── */
    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute; inset: 0;
      background: 
        radial-gradient(ellipse 80% 60% at 50% 40%, rgba(184,150,90,0.06), transparent),
        radial-gradient(ellipse 40% 40% at 80% 20%, rgba(201,169,154,0.04), transparent);
    }

    .hero-line {
      width: 1px; height: 80px;
      background: linear-gradient(to bottom, transparent, var(--gold));
      margin: 0 auto 40px;
      animation: fadeIn 1.5s ease both;
    }

    .hero-eyebrow {
      font-size: 10px;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 24px;
      animation: fadeUp 1s ease 0.3s both;
    }

    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(56px, 8vw, 110px);
      font-weight: 300;
      line-height: 0.95;
      letter-spacing: -0.02em;
      animation: fadeUp 1s ease 0.5s both;
    }

    .hero-title em {
      font-style: italic;
      color: var(--rose);
    }

    .hero-sub {
      font-size: 12px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 32px;
      animation: fadeUp 1s ease 0.7s both;
    }

    .hero-scroll {
      position: absolute;
      bottom: 40px;
      left: 50%;
      transform: translateX(-50%);
      display: flex; flex-direction: column; align-items: center; gap: 8px;
      animation: fadeIn 2s ease 1.5s both;
    }

    .hero-scroll span {
      font-size: 9px;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--muted);
    }

    .scroll-dot {
      width: 1px; height: 40px;
      background: linear-gradient(to bottom, var(--gold), transparent);
      animation: scrollPulse 2s ease infinite;
    }

    /* ── SECTION SHARED ── */
    section { padding: 80px 48px; }

    .section-label {
      font-size: 9px;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 16px;
    }

    .section-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(36px, 4vw, 56px);
      font-weight: 300;
      line-height: 1.1;
      margin-bottom: 48px;
    }

    /* ── UPLOAD ZONE ── */
    #upload { background: var(--surface); border-top: 1px solid var(--border); }

    .upload-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 48px;
      align-items: start;
      max-width: 1200px;
      margin: 0 auto;
    }

    .upload-zone {
      border: 1px dashed var(--border);
      border-radius: 2px;
      padding: 64px 32px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
      position: relative;
      background: var(--bg);
    }

    .upload-zone:hover, .upload-zone.dragover {
      border-color: var(--gold);
      background: rgba(184,150,90,0.03);
    }

    .upload-zone input[type="file"] {
      position: absolute; inset: 0;
      opacity: 0; cursor: pointer; width: 100%; height: 100%;
    }

    .upload-icon {
      width: 48px; height: 48px;
      margin: 0 auto 20px;
      border: 1px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      color: var(--gold);
      font-size: 20px;
    }

    .upload-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 22px;
      font-weight: 300;
      margin-bottom: 8px;
    }

    .upload-desc {
      font-size: 12px;
      color: var(--muted);
      letter-spacing: 0.05em;
      line-height: 1.8;
    }

    .upload-formats {
      margin-top: 16px;
      font-size: 10px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--gold);
    }

    /* ── STATS ── */
    .upload-stats {
      display: flex;
      flex-direction: column;
      gap: 24px;
    }

    .stat-card {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 2px;
      padding: 24px 28px;
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .stat-icon {
      width: 40px; height: 40px;
      border: 1px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      color: var(--gold);
      font-size: 16px;
      flex-shrink: 0;
    }

    .stat-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 32px;
      font-weight: 300;
      line-height: 1;
      color: var(--text);
    }

    .stat-label {
      font-size: 10px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 4px;
    }

    /* ── GALLERY ── */
    #gallery { background: var(--bg); }

    .gallery-controls {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 32px;
      max-width: 1200px;
      margin-left: auto;
      margin-right: auto;
      flex-wrap: wrap;
      gap: 16px;
    }

    .filter-tabs {
      display: flex;
      gap: 4px;
    }

    .filter-tab {
      padding: 8px 20px;
      font-size: 10px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      border: 1px solid var(--border);
      background: none;
      color: var(--muted);
      cursor: pointer;
      border-radius: 1px;
      transition: all 0.2s;
    }

    .filter-tab.active, .filter-tab:hover {
      border-color: var(--gold);
      color: var(--gold);
      background: rgba(184,150,90,0.05);
    }

    .sort-select {
      background: var(--surface);
      border: 1px solid var(--border);
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      font-size: 11px;
      letter-spacing: 0.1em;
      padding: 8px 16px;
      cursor: pointer;
      border-radius: 1px;
      outline: none;
      appearance: none;
      -webkit-appearance: none;
    }

    .sort-select option { background: var(--surface); }

    /* ── MASONRY GALLERY ── */
    .masonry {
      columns: 4;
      column-gap: 12px;
      max-width: 1200px;
      margin: 0 auto;
    }

    @media (max-width: 1024px) { .masonry { columns: 3; } }
    @media (max-width: 768px)  { .masonry { columns: 2; } }
    @media (max-width: 480px)  { .masonry { columns: 1; } }

    .photo-card {
      break-inside: avoid;
      margin-bottom: 12px;
      position: relative;
      overflow: hidden;
      border-radius: 1px;
      cursor: pointer;
      border: 1px solid var(--border);
      animation: fadeIn 0.5s ease both;
    }

    .photo-card img {
      width: 100%;
      display: block;
      transition: transform 0.5s ease;
      object-fit: cover;
    }

    .photo-card:hover img { transform: scale(1.04); }

    .photo-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(to top, rgba(13,13,13,0.92) 0%, transparent 50%);
      opacity: 0;
      transition: opacity 0.3s;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 20px;
    }

    .photo-card:hover .photo-overlay { opacity: 1; }

    .photo-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 16px;
      font-weight: 300;
      margin-bottom: 4px;
      color: var(--text);
    }

    .photo-meta {
      font-size: 10px;
      letter-spacing: 0.1em;
      color: var(--muted);
    }

    .photo-actions {
      display: flex;
      gap: 8px;
      margin-top: 12px;
    }

    .btn-icon {
      width: 32px; height: 32px;
      border: 1px solid rgba(245,242,237,0.2);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      background: rgba(13,13,13,0.6);
      color: var(--text);
      cursor: pointer;
      transition: all 0.2s;
      font-size: 13px;
      text-decoration: none;
    }

    .btn-icon:hover { border-color: var(--gold); color: var(--gold); }

    .btn-icon.delete:hover { border-color: #e05c5c; color: #e05c5c; }

    /* ── EMPTY STATE ── */
    .empty-state {
      text-align: center;
      padding: 80px 20px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .empty-icon {
      font-size: 48px;
      margin-bottom: 24px;
      opacity: 0.3;
    }

    .empty-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: 32px;
      font-weight: 300;
      margin-bottom: 12px;
    }

    .empty-desc { font-size: 13px; color: var(--muted); }

    /* ── LIGHTBOX ── */
    .lightbox {
      display: none;
      position: fixed; inset: 0; z-index: 200;
      background: rgba(0,0,0,0.96);
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .lightbox.open { display: flex; }

    .lightbox-inner {
      position: relative;
      max-width: 90vw;
      max-height: 90vh;
    }

    .lightbox-img {
      max-width: 90vw;
      max-height: 85vh;
      object-fit: contain;
      display: block;
      border: 1px solid var(--border);
    }

    .lightbox-info {
      position: absolute; bottom: -48px; left: 0; right: 0;
      display: flex; align-items: center; justify-content: space-between;
    }

    .lightbox-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 18px;
      font-style: italic;
    }

    .lightbox-close {
      position: fixed; top: 24px; right: 32px;
      font-size: 24px;
      color: var(--muted);
      cursor: pointer;
      background: none; border: none;
      transition: color 0.2s;
      z-index: 201;
    }

    .lightbox-close:hover { color: var(--text); }

    .lightbox-nav {
      position: fixed;
      top: 50%; transform: translateY(-50%);
      background: none; border: 1px solid var(--border);
      color: var(--text);
      width: 48px; height: 48px;
      cursor: pointer;
      font-size: 18px;
      transition: all 0.2s;
      display: flex; align-items: center; justify-content: center;
    }

    .lightbox-nav:hover { border-color: var(--gold); color: var(--gold); }
    .lightbox-nav.prev { left: 24px; }
    .lightbox-nav.next { right: 24px; }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 32px; left: 50%;
      transform: translateX(-50%) translateY(80px);
      background: var(--surface2);
      border: 1px solid var(--border);
      border-left: 2px solid var(--gold);
      color: var(--text);
      font-size: 12px;
      letter-spacing: 0.05em;
      padding: 14px 24px;
      border-radius: 1px;
      transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
      z-index: 300;
      pointer-events: none;
      white-space: nowrap;
    }

    .toast.show { transform: translateX(-50%) translateY(0); }

    /* ── BTN PRIMARY ── */
    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 14px 32px;
      background: none;
      border: 1px solid var(--gold);
      color: var(--gold);
      font-family: 'Inter', sans-serif;
      font-size: 10px;
      font-weight: 500;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      cursor: pointer;
      border-radius: 1px;
      transition: all 0.3s;
      text-decoration: none;
    }

    .btn-primary:hover {
      background: var(--gold);
      color: var(--bg);
    }

    /* ── FOOTER ── */
    footer {
      border-top: 1px solid var(--border);
      padding: 32px 48px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: var(--surface);
    }

    .footer-copy {
      font-size: 11px;
      letter-spacing: 0.1em;
      color: var(--muted);
    }

    .footer-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 16px;
      font-weight: 300;
      letter-spacing: 0.15em;
      color: var(--muted);
    }

    /* ── PROGRESS BAR ── */
    .upload-progress {
      margin-top: 16px;
      display: none;
    }

    .progress-bar {
      height: 1px;
      background: var(--border);
      border-radius: 1px;
      overflow: hidden;
    }

    .progress-fill {
      height: 100%;
      background: var(--gold);
      width: 0%;
      transition: width 0.3s;
    }

    .progress-text {
      font-size: 10px;
      letter-spacing: 0.12em;
      color: var(--muted);
      margin-top: 8px;
    }

    /* ── ANIMATIONS ── */
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes scrollPulse {
      0%, 100% { opacity: 0.3; }
      50% { opacity: 1; }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      header { padding: 16px 24px; }
      nav { gap: 20px; }
      section { padding: 60px 24px; }
      .upload-layout { grid-template-columns: 1fr; }
      footer { flex-direction: column; gap: 12px; text-align: center; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
    }
  </style>
</head>
<body>

<!-- HEADER -->
<header>
  <a class="logo" href="#">Namisar <span>Aulia</span></a>
  <nav>
    <a href="#gallery">Gallery</a>
    <a href="#upload">Upload</a>
    <a href="#" onclick="downloadAll()">Download All</a>
  </nav>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-line"></div>
  <p class="hero-eyebrow">Photography Studio · Est. 2024</p>
  <h1 class="hero-title">Namisar<br><em>Aulia</em><br>Project</h1>
  <p class="hero-sub">Capturing light · Preserving moments</p>
  <div class="hero-scroll">
    <div class="scroll-dot"></div>
    <span>Explore</span>
  </div>
</section>

<!-- UPLOAD SECTION -->
<section id="upload">
  <div class="upload-layout">
    <div>
      <p class="section-label">Upload Karya</p>
      <h2 class="section-title">Tambahkan<br>Foto Baru</h2>
      <div class="upload-zone" id="uploadZone">
        <input type="file" id="fileInput" accept="image/*,video/*,.pdf,.zip,.psd,.ai,.raw,.cr2,.nef,.arw" multiple onchange="handleFiles(this.files)" />
        <div class="upload-icon">↑</div>
        <p class="upload-title">Seret & Lepas File</p>
        <p class="upload-desc">atau klik untuk memilih file<br>dari perangkat Anda</p>
        <p class="upload-formats">JPG · PNG · RAW · PSD · AI · ZIP · PDF</p>
      </div>
      <div class="upload-progress" id="uploadProgress">
        <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>
        <p class="progress-text" id="progressText">Memproses...</p>
      </div>
    </div>
    <div class="upload-stats">
      <p class="section-label">Statistik Koleksi</p>
      <div class="stat-card">
        <div class="stat-icon">🖼</div>
        <div>
          <div class="stat-num" id="photoCount">0</div>
          <div class="stat-label">Total File</div>
        </div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">💾</div>
        <div>
          <div class="stat-num" id="totalSize">0 MB</div>
          <div class="stat-label">Total Ukuran</div>
        </div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">📁</div>
        <div>
          <div class="stat-num" id="fileTypes">—</div>
          <div class="stat-label">Jenis File</div>
        </div>
      </div>
      <button class="btn-primary" onclick="downloadAll()" style="margin-top:8px">
        ↓ &nbsp; Download Semua
      </button>
    </div>
  </div>
</section>

<!-- GALLERY -->
<section id="gallery">
  <div style="max-width:1200px;margin:0 auto 0">
    <p class="section-label">Koleksi</p>
    <h2 class="section-title">Galeri Foto</h2>
  </div>
  <div class="gallery-controls">
    <div class="filter-tabs">
      <button class="filter-tab active" onclick="filterGallery('all', this)">Semua</button>
      <button class="filter-tab" onclick="filterGallery('image', this)">Foto</button>
      <button class="filter-tab" onclick="filterGallery('file', this)">File</button>
    </div>
    <select class="sort-select" onchange="sortGallery(this.value)">
      <option value="newest">Terbaru</option>
      <option value="oldest">Terlama</option>
      <option value="name">Nama A–Z</option>
      <option value="size">Ukuran</option>
    </select>
  </div>
  <div class="masonry" id="gallery-grid"></div>
  <div class="empty-state" id="emptyState">
    <div class="empty-icon">◎</div>
    <h3 class="empty-title">Galeri Masih Kosong</h3>
    <p class="empty-desc">Upload foto pertama Anda untuk memulai koleksi.</p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p class="footer-copy">© 2024 Namisar Aulia Project. Semua hak dilindungi.</p>
  <p class="footer-logo">N · A · P</p>
</footer>

<!-- LIGHTBOX -->
<div class="lightbox" id="lightbox">
  <button class="lightbox-close" onclick="closeLightbox()">✕</button>
  <button class="lightbox-nav prev" onclick="navLightbox(-1)">‹</button>
  <div class="lightbox-inner">
    <img class="lightbox-img" id="lightboxImg" src="" alt=""/>
    <div class="lightbox-info">
      <span class="lightbox-name" id="lightboxName"></span>
      <a class="btn-primary" id="lightboxDownload" href="#" download style="padding:10px 20px;font-size:9px">↓ Download</a>
    </div>
  </div>
  <button class="lightbox-nav next" onclick="navLightbox(1)">›</button>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  // ── STATE ──
  let files = JSON.parse(localStorage.getItem('nap_files') || '[]');
  let currentFilter = 'all';
  let currentSort = 'newest';
  let lightboxIndex = 0;

  // ── INIT ──
  renderGallery();
  updateStats();

  // ── DRAG & DROP ──
  const zone = document.getElementById('uploadZone');
  zone.addEventListener('dragover', e => { e.preventDefault(); zone.classList.add('dragover'); });
  zone.addEventListener('dragleave', () => zone.classList.remove('dragover'));
  zone.addEventListener('drop', e => {
    e.preventDefault(); zone.classList.remove('dragover');
    handleFiles(e.dataTransfer.files);
  });

  // ── HANDLE FILES ──
  function handleFiles(fileList) {
    const arr = Array.from(fileList);
    if (!arr.length) return;

    const progress = document.getElementById('uploadProgress');
    const fill = document.getElementById('progressFill');
    const text = document.getElementById('progressText');
    progress.style.display = 'block';

    let done = 0;
    arr.forEach((file, i) => {
      const reader = new FileReader();
      reader.onload = e => {
        const isImage = file.type.startsWith('image/');
        const entry = {
          id: Date.now() + '_' + i,
          name: file.name,
          type: isImage ? 'image' : 'file',
          mime: file.type,
          size: file.size,
          data: e.target.result,
          date: new Date().toISOString(),
        };
        files.unshift(entry);
        done++;
        fill.style.width = (done / arr.length * 100) + '%';
        text.textContent = `Memproses ${done} dari ${arr.length} file...`;

        if (done === arr.length) {
          saveFiles();
          renderGallery();
          updateStats();
          setTimeout(() => { progress.style.display = 'none'; fill.style.width = '0%'; }, 800);
          showToast(`✓ ${arr.length} file berhasil diupload`);
        }
      };
      reader.readAsDataURL(file);
    });
  }

  // ── SAVE ──
  function saveFiles() {
    try { localStorage.setItem('nap_files', JSON.stringify(files)); }
    catch(e) { showToast('Penyimpanan penuh – file tidak disimpan permanen'); }
  }

  // ── RENDER ──
  function renderGallery() {
    const grid = document.getElementById('gallery-grid');
    const empty = document.getElementById('emptyState');

    let items = [...files];
    if (currentFilter !== 'all') items = items.filter(f => f.type === currentFilter);

    if (currentSort === 'oldest') items.sort((a,b) => a.date > b.date ? 1 : -1);
    else if (currentSort === 'name') items.sort((a,b) => a.name.localeCompare(b.name));
    else if (currentSort === 'size') items.sort((a,b) => b.size - a.size);

    empty.style.display = items.length ? 'none' : 'block';
    grid.innerHTML = '';

    items.forEach((f, idx) => {
      const card = document.createElement('div');
      card.className = 'photo-card';
      card.dataset.id = f.id;
      card.style.animationDelay = (idx * 0.04) + 's';

      if (f.type === 'image') {
        card.innerHTML = `
          <img src="${f.data}" alt="${f.name}" loading="lazy" onclick="openLightbox('${f.id}')"/>
          <div class="photo-overlay">
            <p class="photo-name">${truncate(f.name, 28)}</p>
            <p class="photo-meta">${formatSize(f.size)} · ${formatDate(f.date)}</p>
            <div class="photo-actions">
              <a class="btn-icon" href="${f.data}" download="${f.name}" title="Download" onclick="event.stopPropagation()">↓</a>
              <button class="btn-icon" onclick="openLightbox('${f.id}');event.stopPropagation()" title="Lihat">⤢</button>
              <button class="btn-icon delete" onclick="deleteFile('${f.id}');event.stopPropagation()" title="Hapus">✕</button>
            </div>
          </div>`;
      } else {
        const ext = f.name.split('.').pop().toUpperCase();
        card.innerHTML = `
          <div style="background:var(--surface2);padding:40px 20px;text-align:center;min-height:160px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:12px">
            <div style="width:56px;height:56px;border:1px solid var(--border);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;letter-spacing:.1em;color:var(--gold)">${ext}</div>
            <p style="font-size:12px;color:var(--muted);word-break:break-all">${truncate(f.name,28)}</p>
            <p style="font-size:10px;letter-spacing:.1em;color:var(--border)">${formatSize(f.size)}</p>
            <div style="display:flex;gap:8px;margin-top:4px">
              <a class="btn-icon" href="${f.data}" download="${f.name}" title="Download">↓</a>
              <button class="btn-icon delete" onclick="deleteFile('${f.id}')" title="Hapus">✕</button>
            </div>
          </div>`;
      }
      grid.appendChild(card);
    });
  }

  // ── FILTER & SORT ──
  function filterGallery(type, btn) {
    currentFilter = type;
    document.querySelectorAll('.filter-tab').forEach(t => t.classList.remove('active'));
    btn.classList.add('active');
    renderGallery();
  }

  function sortGallery(val) {
    currentSort = val; renderGallery();
  }

  // ── LIGHTBOX ──
  function openLightbox(id) {
    const imgs = files.filter(f => f.type === 'image');
    lightboxIndex = imgs.findIndex(f => f.id === id);
    showLightboxItem(imgs);
    document.getElementById('lightbox').classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function showLightboxItem(imgs) {
    const f = imgs[lightboxIndex];
    if (!f) return;
    document.getElementById('lightboxImg').src = f.data;
    document.getElementById('lightboxName').textContent = f.name;
    document.getElementById('lightboxDownload').href = f.data;
    document.getElementById('lightboxDownload').download = f.name;
  }

  function navLightbox(dir) {
    const imgs = files.filter(f => f.type === 'image');
    lightboxIndex = (lightboxIndex + dir + imgs.length) % imgs.length;
    showLightboxItem(imgs);
  }

  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('open');
    document.body.style.overflow = '';
  }

  document.getElementById('lightbox').addEventListener('click', e => {
    if (e.target === document.getElementById('lightbox')) closeLightbox();
  });

  document.addEventListener('keydown', e => {
    if (!document.getElementById('lightbox').classList.contains('open')) return;
    if (e.key === 'Escape') closeLightbox();
    if (e.key === 'ArrowLeft') navLightbox(-1);
    if (e.key === 'ArrowRight') navLightbox(1);
  });

  // ── DELETE ──
  function deleteFile(id) {
    files = files.filter(f => f.id !== id);
    saveFiles(); renderGallery(); updateStats();
    showToast('File dihapus');
  }

  // ── DOWNLOAD ALL ──
  function downloadAll() {
    if (!files.length) { showToast('Tidak ada file untuk didownload'); return; }
    files.forEach((f, i) => {
      setTimeout(() => {
        const a = document.createElement('a');
        a.href = f.data; a.download = f.name;
        document.body.appendChild(a); a.click();
        document.body.removeChild(a);
      }, i * 300);
    });
    showToast(`↓ Mengunduh ${files.length} file...`);
  }

  // ── STATS ──
  function updateStats() {
    document.getElementById('photoCount').textContent = files.length;
    const total = files.reduce((s, f) => s + f.size, 0);
    document.getElementById('totalSize').textContent = formatSize(total);
    const types = [...new Set(files.map(f => f.name.split('.').pop().toUpperCase()))];
    document.getElementById('fileTypes').textContent = types.length ? types.slice(0,3).join(', ') : '—';
  }

  // ── UTILS ──
  function formatSize(bytes) {
    if (bytes < 1024) return bytes + ' B';
    if (bytes < 1024*1024) return (bytes/1024).toFixed(1) + ' KB';
    return (bytes/1024/1024).toFixed(1) + ' MB';
  }

  function formatDate(iso) {
    return new Date(iso).toLocaleDateString('id-ID', { day:'numeric', month:'short', year:'numeric' });
  }

  function truncate(str, n) { return str.length > n ? str.slice(0,n) + '…' : str; }

  let toastTimer;
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg; t.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => t.classList.remove('show'), 3000);
  }
</script>
</body>
</html>

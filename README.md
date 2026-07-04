<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>RAB Renovasi Toko</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=DM+Mono:wght@400;500&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg:        #F5F6FA;
    --surface:   #FFFFFF;
    --border:    #DDE1EC;
    --border2:   #C8CEDE;
    --accent:    #2563EB;
    --accent-lt: #EFF4FF;
    --danger:    #DC2626;
    --danger-lt: #FEF2F2;
    --success:   #059669;
    --success-lt:#ECFDF5;
    --text:      #111827;
    --muted:     #6B7280;
    --total-bg:  #1E3A5F;
    --header-bg: #1E3A5F;
    --row-hover: #F0F4FF;
    --shadow:    0 1px 3px rgba(0,0,0,.08), 0 4px 16px rgba(0,0,0,.06);
  }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 12px 12px 48px;
  }

  /* ─── Header ─── */
  .app-header { margin: 0 auto 16px; }
  .header-card {
    background: var(--header-bg);
    border-radius: 14px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .header-left h1 { font-size: 18px; font-weight: 700; color: #fff; letter-spacing: -.3px; }
  .header-left p  { font-size: 12px; color: rgba(255,255,255,.6); margin-top: 2px; }
  .header-meta    { display: flex; gap: 8px; flex-wrap: wrap; width: 100%; }
  .meta-field     { display: flex; flex-direction: column; gap: 3px; flex: 1; min-width: 100px; }
  .meta-field label { font-size: 9px; font-weight: 600; text-transform: uppercase; letter-spacing: .6px; color: rgba(255,255,255,.5); }
  .meta-field input {
    background: rgba(255,255,255,.12); border: 1px solid rgba(255,255,255,.2);
    border-radius: 7px; padding: 6px 8px; font-size: 12px; color: #fff;
    font-family: 'Inter', sans-serif; outline: none;
  }
  .meta-field input::placeholder { color: rgba(255,255,255,.4); }
  .meta-field input:focus { border-color: rgba(255,255,255,.5); background: rgba(255,255,255,.15); }

  /* ─── Main card ─── */
  .main-card { background: var(--surface); border-radius: 14px; box-shadow: var(--shadow); overflow: hidden; }

  /* ─── Toolbar ─── */
  .toolbar {
    padding: 12px; border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 6px; flex-wrap: wrap;
  }
  .toolbar-title { font-size: 11px; font-weight: 600; color: var(--muted); text-transform: uppercase; letter-spacing: .6px; margin-right: auto; }

  .btn {
    display: inline-flex; align-items: center; justify-content: center;
    gap: 4px; border: none; border-radius: 7px; padding: 7px 11px;
    font-size: 12px; font-weight: 500; cursor: pointer;
    transition: background .15s, transform .1s; font-family: 'Inter', sans-serif; flex-shrink: 0;
  }
  .btn:active { transform: scale(.96); }
  .btn-primary { background: var(--accent); color: #fff; }
  .btn-primary:hover { background: #1D4ED8; }
  .btn-ghost   { background: transparent; color: var(--muted); border: 1px solid var(--border); }
  .btn-ghost:hover { background: var(--bg); color: var(--text); }
  .btn-danger  { background: var(--danger-lt); color: var(--danger); border: 1px solid #FECACA; }
  .btn-danger:hover { background: #FEE2E2; }
  .btn-success { background: var(--success-lt); color: var(--success); border: 1px solid #A7F3D0; }
  .btn-success:hover { background: #D1FAE5; }
  .btn-save { background: var(--success-lt); color: var(--success); border: 1px solid #A7F3D0; }
  .btn-save.unsaved { background: #FFF7ED; color: #D97706; border: 1px solid #FDE68A; }
  .btn-save.saving { background: var(--accent-lt); color: var(--accent); border: 1px solid #BFDBFE; }

  .btn-icon {
    width: 28px; height: 28px; border-radius: 6px; border: none;
    display: inline-flex; align-items: center; justify-content: center;
    cursor: pointer; transition: background .15s, transform .1s; font-size: 13px; flex-shrink: 0;
  }
  .btn-icon:active { transform: scale(.92); }
  .btn-icon-edit   { background: var(--accent-lt); color: var(--accent); }
  .btn-icon-edit:hover { background: #DBEAFE; }
  .btn-icon-delete { background: var(--danger-lt); color: var(--danger); }
  .btn-icon-delete:hover { background: #FEE2E2; }
  .btn-icon-save   { background: var(--success-lt); color: var(--success); }
  .btn-icon-save:hover  { background: #D1FAE5; }
  .btn-icon-cancel { background: #F3F4F6; color: #6B7280; }
  .btn-icon-cancel:hover { background: #E5E7EB; }

  /* ─── Save status badge ─── */
  .save-badge {
    font-size: 10px; color: var(--muted); display: flex; align-items: center; gap: 4px;
    margin-left: 2px;
  }
  .save-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--success); transition: background 0.3s; }
  .save-dot.unsaved { background: #FCD34D; }
  .save-dot.saving { background: var(--accent); }

  /* ─── Cards ─── */
  .items-container { padding: 12px; display: flex; flex-direction: column; gap: 10px; }

  .item-card {
    background: #fff; border: 1px solid var(--border);
    border-radius: 10px; padding: 12px; transition: all .15s;
  }
  .item-card:hover { border-color: var(--accent); box-shadow: 0 0 0 2px var(--accent-lt); }
  .item-card.editing { border-color: #FCD34D; background: #FFFBEB; box-shadow: 0 0 0 2px #FEF3C7; }
  .item-card.group { background: #F1F5F9; border: none; padding: 10px 12px; margin-top: 4px; }
  .item-card.group:first-child { margin-top: 0; }

  .group-label {
    font-size: 11px; font-weight: 700; text-transform: uppercase;
    letter-spacing: .7px; color: var(--accent); display: flex; align-items: center; gap: 6px;
  }
  .group-label::before { content: ''; width: 3px; height: 11px; background: var(--accent); border-radius: 2px; }

  .item-row { display: flex; gap: 10px; align-items: center; margin-bottom: 8px; }
  .item-row:last-child { margin-bottom: 0; }
  .item-num { font-size: 11px; color: var(--muted); font-family: 'DM Mono', monospace; min-width: 18px; text-align: center; font-weight: 500; }
  .item-label { flex: 1; font-size: 13px; font-weight: 500; color: var(--text); word-break: break-word; }
  .item-label.empty { color: #aaa; font-style: italic; }
  .item-price { font-size: 12px; font-weight: 600; color: var(--success); font-family: 'DM Mono', monospace; text-align: right; min-width: 80px; }
  .item-actions { display: flex; gap: 4px; }

  /* ─── Edit form ─── */
  .edit-form { display: flex; flex-direction: column; gap: 10px; }
  .form-group { display: flex; flex-direction: column; gap: 4px; }
  .form-group label { font-size: 11px; font-weight: 600; text-transform: uppercase; letter-spacing: .6px; color: var(--muted); }
  .cell-input {
    border: 1px solid var(--border2); border-radius: 7px; padding: 8px 10px;
    font-size: 13px; font-family: 'Inter', sans-serif; outline: none;
    background: #fff; color: var(--text); transition: border-color .15s;
  }
  .cell-input:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(37,99,235,.1); }
  .cell-input.num-input { text-align: right; font-family: 'DM Mono', monospace; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .form-actions { display: flex; gap: 8px; justify-content: center; margin-top: 8px; }

  /* ─── Grand Total ─── */
  .grand-total-box { margin: 16px 12px 24px; border: 2px solid var(--total-bg); border-radius: 11px; overflow: hidden; }
  .grand-total-header { background: var(--total-bg); padding: 10px 12px; font-size: 10px; font-weight: 700; letter-spacing: .8px; text-transform: uppercase; color: rgba(255,255,255,.7); }
  .grand-total-body { display: flex; flex-direction: column; }
  .gt-row { display: grid; grid-template-columns: 1fr auto; gap: 12px; border-bottom: 1px solid var(--border); padding: 10px 12px; }
  .gt-row:last-child { border-bottom: none; }
  .gt-label { font-size: 12px; font-weight: 500; color: var(--muted); }
  .gt-value { font-size: 12px; font-weight: 600; font-family: 'DM Mono', monospace; color: var(--text); text-align: right; }
  .gt-row.highlight { background: var(--total-bg); border-bottom: none; padding: 12px; }
  .gt-row.highlight .gt-label, .gt-row.highlight .gt-value { color: #fff; font-size: 14px; font-weight: 700; }

  /* ─── Empty state ─── */
  .empty-state { text-align: center; padding: 40px 20px; color: var(--muted); }
  .empty-state .icon { font-size: 36px; margin-bottom: 10px; }
  .empty-state p { font-size: 13px; line-height: 1.5; }

  /* ─── Modal ─── */
  .modal-overlay {
    position: fixed; inset: 0; background: rgba(0,0,0,.45);
    display: flex; align-items: flex-end; justify-content: center;
    z-index: 999; opacity: 0; pointer-events: none;
    transition: opacity .2s;
  }
  .modal-overlay.open { opacity: 1; pointer-events: all; }
  .modal-sheet {
    background: #fff; border-radius: 18px 18px 0 0; width: 100%; max-width: 480px;
    padding: 20px 16px 32px;
    transform: translateY(20px); transition: transform .25s ease;
  }
  .modal-overlay.open .modal-sheet { transform: translateY(0); }
  .modal-handle { width: 36px; height: 4px; background: #DDE1EC; border-radius: 2px; margin: 0 auto 16px; }
  .modal-title { font-size: 14px; font-weight: 700; color: var(--text); margin-bottom: 14px; }
  .modal-section-label { font-size: 10px; font-weight: 600; text-transform: uppercase; letter-spacing: .6px; color: var(--muted); margin-bottom: 8px; }

  .group-option {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 12px; border: 1.5px solid var(--border);
    border-radius: 9px; cursor: pointer; margin-bottom: 7px;
    transition: all .15s; background: #fff;
  }
  .group-option:hover { border-color: var(--accent); background: var(--accent-lt); }
  .group-option.selected { border-color: var(--accent); background: var(--accent-lt); }
  .group-option-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--border2); flex-shrink: 0; }
  .group-option.selected .group-option-dot { background: var(--accent); }
  .group-option-name { font-size: 13px; font-weight: 500; color: var(--text); }
  .group-no-option { font-size: 13px; color: var(--muted); text-align: center; padding: 12px 0; }

  .modal-btn-row { display: flex; gap: 8px; margin-top: 16px; }
  .modal-btn-row .btn { flex: 1; padding: 10px; font-size: 13px; }

  /* ─── Toast ─── */
  .toast {
    position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%) translateY(10px);
    background: #111; color: #fff; font-size: 12px; font-weight: 500;
    padding: 8px 16px; border-radius: 20px; z-index: 9999;
    opacity: 0; pointer-events: none; transition: all .25s;
    white-space: nowrap;
  }
  .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }
  .toast.success { background: var(--success); }

  /* ─── Print ─── */
  @media print {
    body { background: #fff; padding: 0; }
    .toolbar, .btn-icon, .item-actions, .modal-overlay, .toast { display: none !important; }
    .main-card { box-shadow: none; }
    .header-card { background: #1E3A5F !important; print-color-adjust: exact; }
    .item-card { page-break-inside: avoid; }
  }
</style>
</head>
<body>

<div class="app-header">
  <div class="header-card">
    <div class="header-left">
      <h1>📋 RAB Renovasi</h1>
      <p>Rencana Anggaran Biaya (Sinkronisasi Cloud)</p>
    </div>
    <div class="header-meta">
      <div class="meta-field">
        <label>Proyek</label>
        <input type="text" id="projectName" placeholder="Nama toko..." oninput="autoSaveWithDebounce()" />
      </div>
      <div class="meta-field">
        <label>Tanggal</label>
        <input type="date" id="projectDate" oninput="autoSaveWithDebounce()" />
      </div>
      <div class="meta-field">
        <label>Dibuat Oleh</label>
        <input type="text" id="projectOwner" placeholder="Nama..." oninput="autoSaveWithDebounce()" />
      </div>
    </div>
  </div>
</div>

<div class="main-card">
  <div class="toolbar">
    <span class="toolbar-title">Daftar Item</span>
    <span class="save-badge">
      <span class="save-dot" id="saveDot"></span>
      <span id="saveStatus">Menghubungkan ke Cloud...</span>
    </span>
    <button class="btn btn-ghost" onclick="addGroup()">＋ Grup</button>
    <button class="btn btn-primary" onclick="openAddItemModal()">＋ Item</button>
    <button class="btn btn-save" id="btnSave" onclick="saveData(false)">✓ Tersimpan di Cloud</button>
    <button class="btn btn-success" onclick="printPage()">🖨</button>
    <button class="btn btn-danger" onclick="clearAll()">🗑</button>
  </div>

  <div class="items-container" id="itemsContainer"></div>

  <div id="emptyState" class="empty-state" style="display:none">
    <div class="icon">📦</div>
    <p>Belum ada item<br><strong>Klik ＋ Item untuk mulai</strong></p>
  </div>

  <div id="grandTotalSection">
    <div class="grand-total-box">
      <div class="grand-total-header">Ringkasan Anggaran</div>
      <div id="grandTotalBody"></div>
    </div>
  </div>
</div>

<!-- Modal pilih group -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModalOutside(event)">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title">Tambah Item ke Kelompok</div>
    <div class="modal-section-label">Pilih Kelompok</div>
    <div id="groupOptionsList"></div>
    <div class="modal-btn-row">
      <button class="btn btn-ghost" onclick="closeModal()">Batal</button>
      <button class="btn btn-primary" onclick="confirmAddItem()">Tambah Item ＋</button>
    </div>
  </div>
</div>

<!-- Toast -->
<div class="toast" id="toast"></div>

<!-- Firebase SDK Integrations -->
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
import { getAuth, signInWithCustomToken, signInAnonymously, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
import { getFirestore, doc, setDoc, getDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

// Firebase Globals and environment setup
const firebaseConfig = JSON.parse(__firebase_config);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';

let rows = [];
let editingId = null;
let nextId = 1;
let selectedGroupId = null;
let isDirty = false;
let saveTimeout = null;
let currentUser = null;

// ── Firebase Auth & Cloud Sync ──────────────────────────────────────────
const initAuth = async () => {
  if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
    try {
      await signInWithCustomToken(auth, __initial_auth_token);
    } catch (e) {
      await signInAnonymously(auth);
    }
  } else {
    await signInAnonymously(auth);
  }
};

initAuth();

onAuthStateChanged(auth, async (user) => {
  currentUser = user;
  if (user) {
    updateSaveStatus('syncing');
    await loadDataFromFirestore(user.uid);
  } else {
    updateSaveStatus('error');
    showToast('⚠️ Gagal menyinkronkan profil cloud.', '');
  }
});

// ── Firestore Storage Functions ──────────────────────────────────────────
async function saveData(silent = false) {
  if (!currentUser) return;
  
  const userId = currentUser.uid;
  // RULE 1: STRICT PATH MATCH
  const docRef = doc(db, 'artifacts', appId, 'users', userId, 'userdata', 'project_rab');

  const data = {
    meta: {
      name:  document.getElementById('projectName').value,
      date:  document.getElementById('projectDate').value,
      owner: document.getElementById('projectOwner').value,
    },
    rows,
    nextId
  };

  try {
    updateSaveStatus('saving');
    await setDoc(docRef, data);
    isDirty = false;
    updateSaveStatus('saved');
    if (!silent) {
      showToast('☁️ Tersimpan otomatis di Cloud!', 'success');
    }
  } catch(e) {
    console.error("Cloud Save Error:", e);
    updateSaveStatus('error');
    showToast('⚠️ Gagal menyimpan ke cloud. Mencoba lagi...', '');
  }
}

async function loadDataFromFirestore(userId) {
  if (!userId) return;
  // RULE 1: STRICT PATH MATCH
  const docRef = doc(db, 'artifacts', appId, 'users', userId, 'userdata', 'project_rab');

  try {
    const docSnap = await getDoc(docRef);
    if (docSnap.exists()) {
      const data = docSnap.data();
      if (data.meta) {
        document.getElementById('projectName').value  = data.meta.name  || '';
        document.getElementById('projectDate').value  = data.meta.date  || '';
        document.getElementById('projectOwner').value = data.meta.owner || '';
      }
      rows   = data.rows   || [];
      nextId = data.nextId || 1;
      isDirty = false;
      updateSaveStatus('saved');
      showToast('☁️ Data Anda berhasil dimuat dari cloud!', 'success');
    } else {
      // Seed default data for first time user
      seedDefaultData();
      await saveData(true);
    }
  } catch (e) {
    console.error("Cloud Load Error:", e);
    showToast('⚠️ Gagal memuat dari cloud. Menggunakan data default...', '');
    seedDefaultData();
  }
  render();
}

function seedDefaultData() {
  document.getElementById('projectName').value = 'Renovasi Toko Utama';
  document.getElementById('projectDate').valueAsDate = new Date();
  rows = [];
  nextId = 1;
  addRowData('group', { label: 'A. Pekerjaan Persiapan' });
  addRowData('item',  { label: 'Pembersihan lokasi', vol: 1, unit: 'Ls', price: 500000 });
  addRowData('item',  { label: 'Pemasangan pengaman / K3', vol: 1, unit: 'Ls', price: 750000 });
  addRowData('group', { label: 'B. Pekerjaan Dinding & Lantai' });
  addRowData('item',  { label: 'Cat dinding interior', vol: 80, unit: 'm²', price: 45000 });
  addRowData('item',  { label: 'Keramik lantai 60×60', vol: 50, unit: 'm²', price: 120000 });
  addRowData('item',  { label: 'Plester & aci dinding', vol: 80, unit: 'm²', price: 55000 });
  addRowData('group', { label: 'C. Pekerjaan Plafon & Atap' });
  addRowData('item',  { label: 'Plafon gypsum', vol: 40, unit: 'm²', price: 95000 });
  addRowData('item',  { label: 'Cat plafon', vol: 40, unit: 'm²', price: 30000 });
  addRowData('group', { label: 'D. Pekerjaan Listrik' });
  addRowData('item',  { label: 'Instalasi listrik baru', vol: 1, unit: 'Ls', price: 3500000 });
  addRowData('item',  { label: 'Lampu LED panel', vol: 12, unit: 'titik', price: 185000 });
  addRowData('group', { label: 'E. Pekerjaan Lain-Lain' });
  addRowData('item',  { label: 'Pintu kaca frameless', vol: 1, unit: 'unit', price: 2800000 });
  addRowData('item',  { label: 'Etalase display', vol: 2, unit: 'unit', price: 1500000 });
}

// Debounce save for text fields input
function autoSaveWithDebounce() {
  markUnsaved();
  if (saveTimeout) clearTimeout(saveTimeout);
  saveTimeout = setTimeout(() => {
    saveData(true);
  }, 1000); 
}

function markUnsaved() {
  if (!isDirty) {
    isDirty = true;
    updateSaveStatus('unsaved');
  }
}

function updateSaveStatus(statusKey) {
  const dot    = document.getElementById('saveDot');
  const status = document.getElementById('saveStatus');
  const btn    = document.getElementById('btnSave');
  
  if (statusKey === 'saved') {
    dot.className    = 'save-dot';
    status.textContent = 'Semua perubahan tersimpan di Cloud';
    btn.className    = 'btn btn-save';
    btn.textContent  = '✓ Tersimpan di Cloud';
  } else if (statusKey === 'unsaved') {
    dot.className    = 'save-dot unsaved';
    status.textContent = 'Ada perubahan baru...';
    btn.className    = 'btn btn-save unsaved';
    btn.textContent  = '💾 Menyimpan...';
  } else if (statusKey === 'saving') {
    dot.className    = 'save-dot saving';
    status.textContent = 'Sedang mengunggah ke Cloud...';
    btn.className    = 'btn btn-save saving';
    btn.textContent  = '⏳ Mengunggah...';
  } else if (statusKey === 'syncing') {
    dot.className    = 'save-dot saving';
    status.textContent = 'Menyinkronkan cloud...';
    btn.className    = 'btn btn-save saving';
    btn.textContent  = '🔄 Sinkronisasi...';
  } else {
    dot.className    = 'save-dot unsaved';
    status.textContent = 'Koneksi lambat / Bermasalah';
    btn.className    = 'btn btn-save unsaved';
    btn.textContent  = '⚠️ Ulangi Simpan';
  }
}

// ── Toast ──────────────────────────────────────────────────────────────
function showToast(msg, type) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.className   = 'toast' + (type ? ' ' + type : '');
  requestAnimationFrame(() => t.classList.add('show'));
  setTimeout(() => t.classList.remove('show'), 2200);
}

// ── Modal pilih group ──────────────────────────────────────────────────
function openAddItemModal() {
  const groups = rows.filter(r => r.type === 'group');
  const list   = document.getElementById('groupOptionsList');

  if (groups.length === 0) {
    list.innerHTML = '<div class="group-no-option">Belum ada kelompok. Item akan ditambahkan di bawah.</div>';
    selectedGroupId = null;
  } else {
    selectedGroupId = groups[groups.length - 1].id;
    list.innerHTML = groups.map(g => `
      <div class="group-option${g.id === selectedGroupId ? ' selected' : ''}"
           onclick="window.selectGroup(${g.id})" data-gid="${g.id}">
        <div class="group-option-dot"></div>
        <div class="group-option-name">${esc(g.label)}</div>
      </div>
    `).join('');
  }

  document.getElementById('modalOverlay').classList.add('open');
}

function selectGroup(id) {
  selectedGroupId = id;
  document.querySelectorAll('.group-option').forEach(el => {
    const sel = parseInt(el.dataset.gid) === id;
    el.classList.toggle('selected', sel);
    el.querySelector('.group-option-dot').style.background = sel ? 'var(--accent)' : 'var(--border2)';
  });
}

function closeModal() {
  document.getElementById('modalOverlay').classList.remove('open');
}

function closeModalOutside(e) {
  if (e.target === document.getElementById('modalOverlay')) closeModal();
}

function confirmAddItem() {
  closeModal();
  addItem(selectedGroupId);
}

// ── Data helpers ───────────────────────────────────────────────────────
function addRowData(type, data) {
  rows.push({ id: nextId++, type, ...data });
}

function addGroup() {
  rows.push({ id: nextId++, type: 'group', label: 'Kelompok Baru' });
  editingId = rows[rows.length - 1].id;
  markUnsaved();
  render();
}

function addItem(afterGroupId) {
  const newRow = { id: nextId++, type: 'item', label: '', vol: 1, unit: 'unit', price: 0 };

  if (afterGroupId) {
    const gIdx = rows.findIndex(r => r.id === afterGroupId);
    if (gIdx !== -1) {
      let insertAt = gIdx + 1;
      for (let i = gIdx + 1; i < rows.length; i++) {
        if (rows[i].type === 'group') break;
        insertAt = i + 1;
      }
      rows.splice(insertAt, 0, newRow);
    } else {
      rows.push(newRow);
    }
  } else {
    rows.push(newRow);
  }

  editingId = newRow.id;
  markUnsaved();
  render();
  requestAnimationFrame(() => {
    document.querySelector(`[data-id="${newRow.id}"] .cell-input`)?.focus();
  });
}

function deleteRow(id) {
  rows = rows.filter(r => r.id !== id);
  if (editingId === id) editingId = null;
  saveData(true); 
  render();
}

function startEdit(id) {
  editingId = id;
  render();
  requestAnimationFrame(() => {
    document.querySelector(`[data-id="${id}"] .cell-input`)?.focus();
  });
}

function saveEdit(id) {
  const card = document.querySelector(`[data-id="${id}"]`);
  if (!card) return;
  const row = rows.find(r => r.id === id);
  if (!row) return;

  const labelEl = card.querySelector('.f-label');
  const volEl   = card.querySelector('.f-vol');
  const unitEl  = card.querySelector('.f-unit');
  const priceEl = card.querySelector('.f-price');

  row.label = labelEl?.value.trim() || row.label;
  if (row.type === 'item') {
    row.vol   = parseFloat(volEl?.value)  || 0;
    row.unit  = unitEl?.value.trim()      || row.unit;
    row.price = parseFloat(priceEl?.value.replace(/[^0-9.]/g,'')) || 0;
  }
  editingId = null;
  saveData(false); 
  render();
}

function cancelEdit(id) {
  const row = rows.find(r => r.id === id);
  if (row && row.type === 'item' && !row.label) {
    rows = rows.filter(r => r.id !== id);
  }
  editingId = null;
  render();
}

// ── Format ────────────────────────────────────────────────────────────
function fmtMoney(n) {
  if (!n && n !== 0) return '–';
  return n.toLocaleString('id-ID', { minimumFractionDigits: 0 });
}
function esc(s) {
  if (!s) return '';
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// ── Render ────────────────────────────────────────────────────────────
function render() {
  const container = document.getElementById('itemsContainer');
  container.innerHTML = '';

  let itemCounter = 0, grandTotal = 0;
  const groupTotals = [];
  let currentGroup = null, currentGroupTotal = 0;

  rows.forEach(row => {
    if (row.type === 'group') {
      if (currentGroup !== null) {
        groupTotals.push({ label: currentGroup, total: currentGroupTotal });
        currentGroupTotal = 0;
      }
      currentGroup = row.label;

      const card = document.createElement('div');
      card.className = 'item-card group';
      card.dataset.id = row.id;

      if (editingId === row.id) {
        card.innerHTML = `
          <div class="edit-form">
            <div class="form-group">
              <label>Nama Kelompok</label>
              <input class="cell-input f-label" value="${esc(row.label)}" placeholder="Kelompok..." />
            </div>
            <div class="form-actions">
              <button class="btn-icon btn-icon-save" onclick="window.saveEdit(${row.id})">✓</button>
              <button class="btn-icon btn-icon-cancel" onclick="window.cancelEdit(${row.id})">✕</button>
            </div>
          </div>`;
      } else {
        card.innerHTML = `
          <div style="display:flex;justify-content:space-between;align-items:center;gap:8px">
            <span class="group-label">${esc(row.label)}</span>
            <div class="item-actions">
              <button class="btn-icon btn-icon-edit" onclick="window.startEdit(${row.id})">✏</button>
              <button class="btn-icon btn-icon-delete" onclick="window.deleteRow(${row.id})">✕</button>
            </div>
          </div>`;
      }
      container.appendChild(card);

    } else {
      itemCounter++;
      const subtotal = (row.vol || 0) * (row.price || 0);
      grandTotal += subtotal;
      currentGroupTotal += subtotal;

      const card = document.createElement('div');
      card.className = 'item-card' + (editingId === row.id ? ' editing' : '');
      card.dataset.id = row.id;

      if (editingId === row.id) {
        card.innerHTML = `
          <div class="edit-form">
            <div class="form-group">
              <label>Nama Barang / Pekerjaan</label>
              <input class="cell-input f-label" value="${esc(row.label)}" placeholder="Masukkan nama..." />
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Volume</label>
                <input class="cell-input num-input f-vol" type="number" min="0" step="any" value="${row.vol}" />
              </div>
              <div class="form-group">
                <label>Satuan</label>
                <input class="cell-input f-unit" value="${esc(row.unit)}" placeholder="unit" />
              </div>
            </div>
            <div class="form-group">
              <label>Harga Satuan (Rp)</label>
              <input class="cell-input num-input f-price" type="number" min="0" step="any" value="${row.price}" />
            </div>
            <div style="background:#F3F4F6;padding:8px;border-radius:7px;text-align:right">
              <div style="font-size:11px;color:var(--muted);margin-bottom:2px">Total</div>
              <div style="font-size:16px;font-weight:700;color:var(--success);font-family:'DM Mono',monospace" class="live-total">Rp ${fmtMoney(subtotal)}</div>
            </div>
            <div class="form-actions">
              <button class="btn-icon btn-icon-save" onclick="window.saveEdit(${row.id})">✓</button>
              <button class="btn-icon btn-icon-cancel" onclick="window.cancelEdit(${row.id})">✕</button>
            </div>
          </div>`;
        requestAnimationFrame(() => {
          const v = card.querySelector('.f-vol');
          const p = card.querySelector('.f-price');
          const t = card.querySelector('.live-total');
          if (v && p && t) {
            const recalc = () => { t.textContent = 'Rp ' + fmtMoney((parseFloat(v.value)||0)*(parseFloat(p.value)||0)); };
            v.addEventListener('input', recalc);
            p.addEventListener('input', recalc);
          }
        });
      } else {
        card.innerHTML = `
          <div class="item-row">
            <span class="item-num">${itemCounter}</span>
            <span class="item-label${!row.label?' empty':''}">${esc(row.label)||'—'}</span>
            <span class="item-price">Rp ${fmtMoney(subtotal)}</span>
            <div class="item-actions">
              <button class="btn-icon btn-icon-edit" onclick="window.startEdit(${row.id})">✏</button>
              <button class="btn-icon btn-icon-delete" onclick="window.deleteRow(${row.id})">✕</button>
            </div>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;padding:0 24px;font-size:11px;color:var(--muted)">
            <div>${fmtMoney(row.vol)} ${esc(row.unit)}</div>
            <div style="text-align:center">@</div>
            <div style="text-align:right">Rp ${fmtMoney(row.price)}</div>
          </div>`;
      }
      container.appendChild(card);
    }
  });

  if (currentGroup !== null) groupTotals.push({ label: currentGroup, total: currentGroupTotal });

  document.getElementById('emptyState').style.display =
    rows.filter(r => r.type === 'item').length === 0 ? 'block' : 'none';

  const gtBody = document.getElementById('grandTotalBody');
  gtBody.innerHTML = groupTotals.map(g => `
    <div class="gt-row">
      <div class="gt-label">${esc(g.label)}</div>
      <div class="gt-value">Rp ${fmtMoney(g.total)}</div>
    </div>`).join('') + `
    <div class="gt-row highlight">
      <div class="gt-label">TOTAL KESELURUHAN</div>
      <div class="gt-value">Rp ${fmtMoney(grandTotal)}</div>
    </div>`;
}

// ── Clear ──────────────────────────────────────────────────────────────
function clearAll() {
  if (!confirm('Hapus semua item? Tindakan tidak bisa dibatalkan.')) return;
  rows = []; editingId = null;
  saveData(true); 
  render();
}
function printPage() { window.print(); }

// ── Bind functions globally for onclick inline attributes ───────────────
window.addGroup = addGroup;
window.openAddItemModal = openAddItemModal;
window.confirmAddItem = confirmAddItem;
window.clearAll = clearAll;
window.printPage = printPage;
window.selectGroup = selectGroup;
window.closeModal = closeModal;
window.closeModalOutside = closeModalOutside;
window.deleteRow = deleteRow;
window.startEdit = startEdit;
window.saveEdit = saveEdit;
window.cancelEdit = cancelEdit;
window.autoSaveWithDebounce = autoSaveWithDebounce;
window.saveData = saveData;

// ── Keyboard ──
document.addEventListener('keydown', e => {
  if (!editingId) return;
  if (e.key === 'Enter') saveEdit(editingId);
  if (e.key === 'Escape') cancelEdit(editingId);
});
</script>
</body>
</html>

# 🌐 Zentra Host

> Demo platform web hosting modern yang dibangun dengan **Vanilla JavaScript + Supabase + Vercel**.

🔗 **Live Demo:** _akan diisi setelah deploy ke Vercel_

---

## ✨ Fitur Lengkap

### 🖥️ Halaman Publik
- **Beranda** — Hero section, Bento features grid, Pricing toggle, Testimoni, CTA
- **Paket Hosting** — Shared / Cloud / VPS dengan tab switcher & tabel perbandingan
- **Domain** — Pencarian ketersediaan + daftar harga ekstensi
- **Kontak** — Form pesan ke database + FAQ accordion

### 🔐 Sistem Authentication
- **Register & Login** dengan email/password (Supabase Auth)
- **Google OAuth** (opsional)
- **Akun admin demo** auto-bootstrap

### 📊 Dashboard Customer
- **Overview** — Statistik akun real-time
- **Hosting Saya** — Layanan aktif/expired
- **Domain Saya** — Daftar domain
- **Invoice** — Riwayat transaksi
- **Profil** — Edit informasi akun

### 💳 Checkout
- Pilihan periode (1/3/6/12 bulan) dengan diskon otomatis
- Hitung PPN 11% & total
- Multi metode pembayaran (Transfer Bank, e-wallet, QRIS)

### 🎨 UI/UX
- **Light & Dark theme** toggle dengan preferensi tersimpan
- **Fully responsive** — desktop, tablet, mobile
- Modern design (Bento grid, gradient mesh background)
- Animasi smooth & micro-interactions

---

## 🛠️ Tech Stack

| Kategori | Teknologi |
|---|---|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript (ES6+) |
| **Backend** | Supabase (PostgreSQL + Auth + Realtime) |
| **Database** | PostgreSQL (via Supabase) |
| **Hosting** | Vercel |
| **Source Control** | GitHub |
| **Font** | Inter (Google Fonts) |

**Tanpa framework** — pure vanilla untuk performa maksimal & dependency minimal.

---

## 🗄️ Database Schema (Supabase)

```sql
profiles (
  id UUID PK FK auth.users,
  fullname TEXT,
  phone TEXT,
  role TEXT DEFAULT 'customer',
  created_at TIMESTAMPTZ
)

orders (
  id BIGSERIAL PK,
  user_id UUID FK auth.users,
  name TEXT, type TEXT,
  period INT, price INT,
  payment TEXT,
  created_at TIMESTAMPTZ
)

messages (
  id BIGSERIAL PK,
  name, email, subject, message TEXT,
  created_at TIMESTAMPTZ
)
```

**Row Level Security (RLS)** aktif — user hanya bisa akses data sendiri.

---

## 🚀 Cara Menjalankan Lokal

1. Clone repository:
   ```bash
   git clone https://github.com/USERNAME/zentra-host.git
   cd zentra-host
   ```
2. Buka `index.html` di browser (atau pakai Live Server di VS Code)
3. Daftar akun baru → login → eksplorasi fitur

> ⚠️ Untuk login dengan Google, butuh deploy ke domain `https` beneran (Vercel) karena Google OAuth tidak mendukung `file://`.

---

## 🌐 Deploy

Repo ini **auto-deploy ke Vercel** setiap kali ada push ke branch `main`.

Setup awal Vercel:
1. Login Vercel pakai akun GitHub
2. Import repository ini
3. Klik **Deploy** (zero config — Vercel auto-detect static HTML)

---

## 👤 Akun Demo

| Role | Email | Password |
|---|---|---|
| Admin | `admin@zentra.id` | `admin123` |
| Customer | _Daftar akun sendiri_ | _(bebas)_ |

---

## 📁 Struktur File

```
zentra-host/
├── index.html      ← Single-file SPA (HTML + CSS + JS embedded)
├── README.md
└── .gitignore
```

Hanya **1 file utama**. Tidak ada folder assets atau dependencies eksternal kecuali Supabase SDK & Google Fonts via CDN.

---

## 🔒 Keamanan

- ✅ Password user di-hash oleh Supabase (bcrypt)
- ✅ Row Level Security (RLS) memastikan data terisolasi per user
- ✅ Anon key Supabase aman di-public (dilindungi RLS)
- ✅ Service role key TIDAK di-commit (server-side only)

---

## 📝 Lisensi

Project demo untuk keperluan **edukasi & tugas kuliah**.
Tidak untuk komersial.

---

**© 2026 Zentra Host** — Built with ❤️ in Indonesia

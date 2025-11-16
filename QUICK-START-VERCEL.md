# ⚡ Quick Start - Deploy ke Vercel (15 Menit)

## 🎯 Ringkasan

Ikuti 5 langkah ini untuk deploy aplikasi ke Vercel dengan data yang sudah ada.

---

## 1️⃣ Setup MongoDB (5 menit)

```
1. Buka: https://www.mongodb.com/cloud/atlas/register
2. Sign up (gratis)
3. Buat cluster FREE
4. Buat user: admin / [password]
5. Whitelist IP: 0.0.0.0/0
6. Copy connection string:
   mongodb+srv://admin:PASSWORD@cluster0.xxxxx.mongodb.net/perpustakaan
```

**SIMPAN connection string ini!**

---

## 2️⃣ Import Data ke MongoDB (3 menit)

Di terminal:

```bash
npm run import-mongodb
```

Paste connection string, Enter.

Tunggu sampai muncul:
```
🎉 IMPORT SELESAI!
📊 Total data imported: X
```

---

## 3️⃣ Setup Vercel Environment Variables (3 menit)

```
1. Buka: https://vercel.com/dashboard
2. Pilih project "perpu"
3. Settings → Environment Variables
4. Tambahkan 3 variables:
```

| Name | Value |
|------|-------|
| `MONGODB_URI` | (connection string dari step 1) |
| `EMAIL_USER` | `digimetateam@gmail.com` |
| `EMAIL_PASS` | `rzxfnvxzgugcxdir` |

**Centang: Production, Preview, Development untuk semua!**

---

## 4️⃣ Deploy (2 menit)

```
1. Vercel Dashboard → Deployments
2. Klik deployment terakhir → "..." → "Redeploy"
3. Tunggu 2-3 menit
4. Status: ✅ Ready
```

---

## 5️⃣ Test (2 menit)

Buka URL Vercel Anda:

```
✅ Halaman muncul
✅ Buku-buku terlihat
✅ Admin panel → Data muncul
✅ Checkout → Email terkirim
```

---

## ✅ SELESAI!

Aplikasi live di: **https://perpu.vercel.app**

**Fitur yang berfungsi:**
- ✅ 24,148 buku
- ✅ Search & filter
- ✅ Keranjang & checkout
- ✅ Email otomatis
- ✅ Database pelanggan
- ✅ Admin panel

---

## 📚 Panduan Lengkap

Baca: **UPDATE-VERCEL-MONGODB.md**

---

## 🆘 Butuh Bantuan?

**Error saat import?**
- Cek connection string
- Cek password (encode jika ada karakter khusus)
- Cek IP whitelist: 0.0.0.0/0

**Email tidak terkirim?**
- Cek environment variables di Vercel
- Redeploy setelah tambah env vars

**Data tidak muncul?**
- Cek MongoDB - Data sudah ada?
- Cek MONGODB_URI di Vercel
- Redeploy

---

**Total waktu: 15 menit** ⏱️

Aplikasi akan live 24/7 dengan database cloud! 🚀

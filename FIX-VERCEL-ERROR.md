# 🔧 Fix Error 500 di Vercel

## ❌ Error yang Anda Alami

```
500: INTERNAL_SERVER_ERROR
Code: FUNCTION_INVOCATION_FAILED
```

## ✅ Solusi Sudah Diterapkan

Saya sudah memperbaiki code dengan:
1. ✅ Lazy loading untuk MongoDB
2. ✅ Error handling yang lebih baik
3. ✅ Email config menggunakan environment variables
4. ✅ File Excel path handling

## 🚀 Langkah Deploy Ulang

### 1. Pastikan Environment Variables Sudah Diset

Di Vercel Dashboard → Settings → Environment Variables, pastikan ada 3 variabel:

| Name | Value | Status |
|------|-------|--------|
| `MONGODB_URI` | `mongodb+srv://...` | ✅ Harus ada |
| `EMAIL_USER` | `digimetateam@gmail.com` | ✅ Harus ada |
| `EMAIL_PASS` | `rzxfnvxzgugcxdir` | ✅ Harus ada |

**Jika belum ada, tambahkan sekarang!**

### 2. Redeploy

Vercel otomatis deploy setelah push ke GitHub. Atau manual:

1. Buka Vercel Dashboard
2. Pilih project "perpu"
3. Tab "Deployments"
4. Klik "..." → "Redeploy"
5. Tunggu 2-3 menit

### 3. Cek Logs

Jika masih error:
1. Vercel Dashboard → Deployments → [latest deployment]
2. Klik "View Function Logs"
3. Lihat error message

## 🔍 Checklist Troubleshooting

### ✅ MongoDB Connection

**Test connection string:**
```
mongodb+srv://USERNAME:PASSWORD@cluster0.xxxxx.mongodb.net/perpustakaan
```

**Pastikan:**
- [ ] Username benar
- [ ] Password benar (tanpa < >)
- [ ] Password tidak ada karakter khusus yang belum di-encode
- [ ] IP whitelist: 0.0.0.0/0 (allow all)

**Cara whitelist IP di MongoDB:**
1. MongoDB Atlas → Network Access
2. Klik "Add IP Address"
3. Pilih "Allow Access from Anywhere" (0.0.0.0/0)
4. Klik "Confirm"

### ✅ File Excel

**Pastikan file sudah di-commit:**
```bash
git add "REKAP BUKU.xlsx"
git commit -m "Add Excel file"
git push
```

**Cek di GitHub:**
- Buka: https://github.com/missblossom007-dot/perpu
- File "REKAP BUKU.xlsx" harus ada di list

### ✅ Dependencies

**Pastikan package.json include:**
- `mongoose`
- `mongodb`
- `nodemailer`
- `xlsx`
- `express`

## 🐛 Error Umum & Solusi

### Error: "MongoServerError: Authentication failed"

**Solusi:**
1. Cek MONGODB_URI di environment variables
2. Pastikan password tidak ada karakter khusus
3. Jika ada karakter khusus, encode: https://www.urlencoder.org/
4. Whitelist IP: 0.0.0.0/0

### Error: "Cannot find module 'REKAP BUKU.xlsx'"

**Solusi:**
```bash
git add "REKAP BUKU.xlsx"
git commit -m "Add Excel file"
git push
```

### Error: "Email not sent"

**Solusi:**
- Ini tidak akan crash aplikasi
- Email optional, aplikasi tetap jalan
- Pastikan EMAIL_USER dan EMAIL_PASS di environment variables

### Error: "Timeout"

**Solusi:**
- MongoDB connection timeout
- Cek MongoDB cluster status
- Pastikan cluster tidak paused (free tier auto-pause setelah 60 hari tidak aktif)

## 📝 Cara Cek Error Detail

### 1. Via Vercel Dashboard

1. Buka: https://vercel.com/dashboard
2. Pilih project "perpu"
3. Tab "Deployments"
4. Klik deployment terakhir
5. Scroll ke "Function Logs"
6. Lihat error message

### 2. Via Browser Console

1. Buka aplikasi di browser
2. Tekan F12 (Developer Tools)
3. Tab "Console"
4. Lihat error message
5. Tab "Network" → Lihat failed requests

## ✅ Verifikasi Berhasil

Setelah deploy ulang, test:

1. **Buka URL Vercel** (contoh: https://perpu.vercel.app)
2. **Halaman utama muncul?** ✅
3. **Buku-buku muncul?** ✅
4. **Bisa tambah ke keranjang?** ✅
5. **Bisa checkout?** ✅
6. **Email diterima?** ✅
7. **Admin panel bisa dibuka?** ✅

## 🎯 Quick Fix Commands

Jika masih error, jalankan:

```bash
# 1. Pull latest code
git pull

# 2. Reinstall dependencies
npm install

# 3. Test local
npm start

# 4. Jika local jalan, push lagi
git add .
git commit -m "Fix deployment"
git push
```

## 📞 Masih Error?

Kirim screenshot:
1. Error message di browser
2. Function logs di Vercel
3. Environment variables (hide password!)
4. MongoDB connection string (hide password!)

---

**Code sudah diperbaiki dan di-push ke GitHub!**
Vercel akan otomatis deploy ulang dalam 2-3 menit.

Cek status: https://vercel.com/dashboard

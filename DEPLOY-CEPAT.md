# 🚀 Deploy ke Vercel - Panduan Cepat (10 Menit)

## ❌ Masalah: Error 500 di Vercel

**Penyebab:** Aplikasi menggunakan file system (orders.json, customers.json) yang tidak support di Vercel.

**Solusi:** Gunakan MongoDB sebagai database.

---

## ✅ Langkah Deploy (10 Menit)

### 1️⃣ Buat MongoDB Database (3 menit)

1. Buka: https://www.mongodb.com/cloud/atlas/register
2. Sign up (gratis, pakai email Google)
3. Klik "Build a Database" → Pilih **FREE** (M0)
4. Pilih region terdekat (Singapore)
5. Klik "Create"
6. Buat user database:
   - Username: `admin`
   - Password: (generate atau buat sendiri, **SIMPAN!**)
7. Klik "Create User"
8. Whitelist IP: Klik "Add My Current IP Address" atau "Allow Access from Anywhere" (0.0.0.0/0)
9. Klik "Finish and Close"
10. Klik "Connect" → "Connect your application"
11. **Copy connection string**, contoh:
    ```
    mongodb+srv://admin:PASSWORD@cluster0.xxxxx.mongodb.net/perpustakaan
    ```
    Ganti `PASSWORD` dengan password yang Anda buat tadi!

### 2️⃣ Deploy ke Vercel (5 menit)

1. Buka: https://vercel.com/new
2. Login dengan GitHub
3. Import repository: **missblossom007-dot/perpu**
4. Klik "Import"
5. **Tambahkan Environment Variables:**
   
   Klik "Environment Variables", tambahkan 3 variabel:
   
   **Variable 1:**
   - Name: `MONGODB_URI`
   - Value: (paste connection string dari step 1)
   
   **Variable 2:**
   - Name: `EMAIL_USER`
   - Value: `digimetateam@gmail.com`
   
   **Variable 3:**
   - Name: `EMAIL_PASS`
   - Value: `rzxfnvxzgugcxdir`

6. Klik "Deploy"
7. Tunggu 2-3 menit
8. **SELESAI!** Aplikasi live! 🎉

### 3️⃣ Test Aplikasi (2 menit)

1. Buka URL yang diberikan Vercel (contoh: `https://perpu.vercel.app`)
2. Test:
   - ✅ Browse buku
   - ✅ Tambah ke keranjang
   - ✅ Checkout
   - ✅ Cek email
   - ✅ Admin panel

---

## 📝 Catatan Penting

### Connection String MongoDB

Format:
```
mongodb+srv://USERNAME:PASSWORD@cluster0.xxxxx.mongodb.net/perpustakaan
```

**PENTING:**
- Ganti `USERNAME` dengan username Anda
- Ganti `PASSWORD` dengan password Anda (tanpa < >)
- Jangan ada spasi
- Jika password ada karakter khusus (@, #, dll), encode dulu: https://www.urlencoder.org/

### Environment Variables di Vercel

| Name | Value | Keterangan |
|------|-------|------------|
| `MONGODB_URI` | `mongodb+srv://...` | Connection string dari MongoDB |
| `EMAIL_USER` | `digimetateam@gmail.com` | Email untuk kirim notifikasi |
| `EMAIL_PASS` | `rzxfnvxzgugcxdir` | App Password Gmail |

---

## 🐛 Troubleshooting

### Error: "MongoServerError: Authentication failed"

**Solusi:**
1. Cek password di connection string
2. Pastikan user sudah dibuat di MongoDB Atlas
3. Whitelist IP: 0.0.0.0/0 (allow all)

### Error: "Cannot find module"

**Solusi:**
- Vercel otomatis install dependencies
- Tunggu beberapa menit, lalu refresh

### Aplikasi loading terus

**Solusi:**
1. Cek Vercel logs: Dashboard → Deployments → [deployment] → Logs
2. Cek MongoDB connection string
3. Redeploy: Dashboard → Deployments → [deployment] → Redeploy

---

## 🎯 Checklist

- [ ] MongoDB cluster created
- [ ] Connection string copied & password diganti
- [ ] Vercel project created
- [ ] 3 environment variables added
- [ ] Deployment successful (hijau ✓)
- [ ] URL dibuka, aplikasi jalan
- [ ] Test checkout
- [ ] Email diterima

---

## 🔗 Links Penting

- **MongoDB Atlas:** https://cloud.mongodb.com/
- **Vercel Dashboard:** https://vercel.com/dashboard
- **GitHub Repo:** https://github.com/missblossom007-dot/perpu

---

## 💡 Tips

1. **Custom Domain:**
   - Vercel Dashboard → Settings → Domains
   - Tambahkan domain Anda (gratis SSL!)

2. **Update Aplikasi:**
   ```bash
   git add .
   git commit -m "Update"
   git push
   ```
   Vercel otomatis deploy ulang!

3. **Lihat Data:**
   - MongoDB Atlas → Database → Browse Collections
   - Lihat orders, customers, requests

---

**Setelah deploy, aplikasi akan live 24/7 di internet! 🌍**

URL Anda: `https://perpu.vercel.app` (atau custom domain)

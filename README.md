# OrderBro — Aplikasi Manajemen Order (PWA)

Aplikasi PWA *client-side* untuk mengelola order. Berjalan sepenuhnya di
browser tanpa backend; seluruh data tersimpan di LocalStorage perangkat
pengguna. Gratis, open-source (MIT), dan bisa di-*rebrand*.

> **Demo langsung:** `https://<username>.github.io/orderbro/`
> *(ganti `<username>` dengan akun GitHub Anda setelah deploy)*

---

## Fitur

- Pencatatan order: klien, deadline, item per size, qty, harga
- Status order 6 tahap: Pending -> DP Masuk -> Produksi -> Quality Check -> Siap Kirim -> Lunas
- **Tracking DP & pelunasan**: uang masuk, sisa tagihan, progress bar
- **Rekap & visualisasi**: omzet, piutang, chart omzet 6 bulan, komposisi status, top klien
- **White-label**: ganti nama aplikasi, tagline, warna aksen, dan logo sendiri dari menu Pengaturan
- Invoice PDF, Export Excel, Share WhatsApp
- **Backup & Restore** data ke file `.json`
- **Installable PWA** + offline-capable (service worker)

---

## Struktur File

```
.
├── index.html       # Aplikasi utama
├── manifest.json    # Manifest PWA
├── sw.js            # Service worker (offline cache)
├── 404.html         # Fallback (copy index.html)
├── .nojekyll        # Mencegah pemrosesan Jekyll
├── LICENSE          # MIT
├── README.md
└── icons/           # Ikon PWA (PNG)
```

---

## Deploy ke GitHub Pages

1. Buat repository baru (mis. `orderbro`).
2. Upload **seluruh isi** folder ini ke root repository.
3. Commit & push ke branch `main`.
4. **Settings -> Pages -> Source**: branch `main`, folder `/ (root)`. Save.
5. Tunggu 1-2 menit -> akses di `https://<username>.github.io/orderbro/`.

### Catatan teknis
- Service worker **hanya aktif via HTTPS** (GitHub Pages otomatis) atau `localhost`.
- File `.nojekyll` **wajib ada**.
- Saat update aplikasi, naikkan versi `CACHE` di `sw.js` (mis. `v1.0.1`).
- Setelah update `manifest.json` (nama/ikon), perangkat yang **sudah pernah
  install** ke home screen tidak otomatis ter-update — perlu uninstall lalu
  install ulang dari browser untuk melihat perubahan.

---

## Cara Rebrand (White-label)

Tanpa menyentuh kode:
1. Buka aplikasi -> tab **Pengaturan** -> kartu **Branding Aplikasi**.
2. Isi nama aplikasi, tagline, pilih warna aksen, unggah logo (maks 500KB).
3. Klik **Simpan Branding**.

Branding tersimpan di perangkat masing-masing pengguna. Untuk mengubah branding
**default** (yang dilihat semua orang sebelum mengatur sendiri), edit teks pada
`index.html` bagian `<div class="app-header">` dan nilai `--red` di `:root`.

Untuk mengubah **nama di home screen Android/ikon app**, edit `name` dan
`short_name` di `manifest.json`, lalu ikon di folder `icons/`.

---

## Pengembangan Lokal

Service worker butuh server (bukan `file://`):

```bash
python3 -m http.server 8080
# buka http://localhost:8080
```

---

## Lisensi

Dirilis di bawah **MIT License** - bebas dipakai, dimodifikasi, dan
didistribusikan, termasuk untuk tujuan komersial, selama menyertakan berkas
lisensi. Lihat [LICENSE](LICENSE).

---

## Data & Privasi

Seluruh data tersimpan **lokal di perangkat** (LocalStorage). Tidak ada data
yang dikirim ke server mana pun. Biasakan **Backup** berkala dari menu
Pengaturan untuk mencegah kehilangan data.

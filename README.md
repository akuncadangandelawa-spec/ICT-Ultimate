# 📊 ICT Ultimate — README

**Versi:** 1.0  
**Bahasa:** Pine Script™ v6  
**Platform:** TradingView  

---

## 📌 Deskripsi

**ICT Ultimate** adalah indikator *overlay* lengkap yang menggabungkan berbagai konsep dari **Inner Circle Trader (ICT)** ke dalam satu alat analisis. Indikator ini dirancang untuk membantu trader mengidentifikasi area-area kunci pasar seperti *Fair Value Gap (FVG)*, *Order Block (OB)*, *Market Structure Shift (MSS)*, *Optimal Trade Entry (OTE)*, dan *Turtle Soup*, serta dilengkapi dengan *Killzone* (sesi perdagangan) dan *dashboard* real-time.

Dengan pendekatan *non-repainting*, indikator ini memberikan sinyal yang stabil dan dapat diandalkan untuk pengambilan keputusan trading.

---

## 🚀 Fitur Utama

| Fitur | Deskripsi |
|-------|-----------|
| **Turtle Soup** | Mendeteksi sinyal pembalikan harga berdasarkan *swing high/low* (konsep "soup" dari ICT). |
| **Fair Value Gap (FVG)** | Menampilkan area celah harga yang belum tersentuh (*unmitigated*) sebagai area potensial likuiditas. |
| **Order Block (OB)** | Mengidentifikasi area *demand* (bullish) dan *supply* (bearish) yang belum dimitigasi. |
| **Market Structure Shift (MSS)** | Mendeteksi perubahan struktur pasar (break of structure) sebagai konfirmasi tren. |
| **Optimal Trade Entry (OTE)** | Menampilkan zona retracement 62%-79% dari *swing* terakhir sebagai area entry optimal. |
| **Killzone (Sesi)** | Menyoroti sesi perdagangan utama (Asia, London, NY) dengan latar belakang. |
| **Dashboard Real-time** | Menampilkan metrik utama (swing levels, sinyal, status, ATR, MSS, sesi) dalam tabel. |
| **Alert Conditions** | Notifikasi untuk sinyal *Bullish* dan *Bearish Turtle Soup*. |
| **Non-Repainting** | Semua sinyal dan area digambar berdasarkan data harga yang sudah terbentuk, tidak berubah setelah candle tertutup. |

---

## ⚙️ Parameter

### **Dashboard**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Tampilkan Dashboard` | `true` | Aktifkan/nonaktifkan tabel dashboard. |
| `Ukuran Font Dashboard` | `Small` | Pilihan ukuran teks dashboard. |
| `Posisi Dashboard` | `Top Right` | Posisi tabel pada chart. |

### **1. Turtle Soup**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan Turtle Soup` | `true` | Mengaktifkan deteksi sinyal Turtle Soup. |
| `Tampilkan Label Sinyal` | `true` | Menampilkan label "🐢 BULLISH/BEARISH" pada chart. |
| `Swing Lookback` | `5` | Jumlah bar untuk menentukan *swing high/low*. |
| `Ukuran Label Sinyal` | `Normal` | Ukuran teks label sinyal. |
| `Tampilkan Garis Swing` | `true` | Menampilkan garis horizontal pada level *swing high/low*. |
| `Warna Bullish` | Hijau | Warna label sinyal bullish. |
| `Warna Bearish` | Merah | Warna label sinyal bearish. |
| `Warna Swing High` | Oranye | Warna garis *swing high*. |
| `Warna Swing Low` | Biru | Warna garis *swing low*. |

### **2. Fair Value Gap (FVG)**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan FVG` | `true` | Mengaktifkan tampilan FVG. |
| `Lookback (candle)` | `50` | Jumlah candle ke belakang untuk mencari FVG. |
| `Hanya Unmitigated` | `true` | Hanya menampilkan FVG yang belum tersentuh harga. |
| `Warna Bullish` | Hijau (70% transparan) | Warna area FVG bullish. |
| `Warna Bearish` | Merah (70% transparan) | Warna area FVG bearish. |
| `Border` | Putih (80% transparan) | Warna garis tepi FVG. |

### **3. Order Block (OB)**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan Order Block` | `true` | Mengaktifkan tampilan Order Block. |
| `Lookback (candle)` | `50` | Jumlah candle ke belakang untuk mencari OB. |
| `Hanya Unmitigated` | `true` | Hanya menampilkan OB yang belum dimitigasi. |
| `Warna Demand (Bullish)` | Biru (65% transparan) | Warna area Order Block bullish. |
| `Warna Supply (Bearish)` | Oranye (65% transparan) | Warna area Order Block bearish. |
| `Border` | Putih (90% transparan) | Warna garis tepi OB. |

### **4. Market Structure Shift (MSS)**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan MSS` | `true` | Mengaktifkan deteksi MSS. |
| `Lookback Swing` | `10` | Jumlah bar untuk menentukan *swing* struktur pasar. |
| `Tampilkan Label MSS` | `true` | Menampilkan label "⬆ MSS" atau "⬇ MSS" pada chart. |
| `Warna MSS Bullish` | Hijau terang | Warna label MSS bullish. |
| `Warna MSS Bearish` | Fuchsia | Warna label MSS bearish. |

### **5. Optimal Trade Entry (OTE)**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan OTE` | `true` | Mengaktifkan tampilan zona OTE. |
| `Level 62%` | `0.62` | Level retracement pertama. |
| `Level 79%` | `0.79` | Level retracement kedua. |
| `Warna Zona OTE` | Kuning (70% transparan) | Warna zona OTE dan garis level. |

### **6. Killzone (Sesi)**
| Parameter | Default | Deskripsi |
|-----------|---------|-----------|
| `Aktifkan Killzone` | `true` | Mengaktifkan latar belakang sesi. |
| `Pilih Sesi` | `All Killzones` | Pilihan sesi: Asia, London, NY, atau semua. |
| `Warna Background Sesi` | Ungu (85% transparan) | Warna latar belakang saat sesi aktif. |

---

## 🧠 Logika & Komponen

### **A. Turtle Soup**
- Mendeteksi *swing high* dan *swing low* berdasarkan periode `lookback`.
- **Bullish Soup**: Harga turun di bawah *swing low* terakhir, lalu ditutup di atasnya.
- **Bearish Soup**: Harga naik di atas *swing high* terakhir, lalu ditutup di bawahnya.
- Sinyal dianggap *tidak repaint* karena menggunakan harga penutupan candle.

### **B. Fair Value Gap (FVG)**
- Terbentuk ketika ada celah antara candle berurutan:
  - **Bullish FVG**: `low[i+2] > high[i]` (gap ke atas).
  - **Bearish FVG**: `high[i+2] < low[i]` (gap ke bawah).
- **Unmitigated**: FVG yang belum tersentuh oleh harga di candle setelahnya.
- Digambar sebagai *box* pada chart dengan warna sesuai arah.

### **C. Order Block (OB)**
- **Demand (Bullish)**: Candle bearish diikuti oleh candle bullish yang menembus di atas high-nya.
- **Supply (Bearish)**: Candle bullish diikuti oleh candle bearish yang menembus di bawah low-nya.
- **Unmitigated**: OB yang belum tersentuh harga setelah terbentuk.
- Digambar sebagai *box* pada chart.

### **D. Market Structure Shift (MSS)**
- **Bullish MSS**: Harga menutup di atas *highest high* dari `mssLookback` bar sebelumnya.
- **Bearish MSS**: Harga menutup di bawah *lowest low* dari `mssLookback` bar sebelumnya.
- Memberikan label pada chart sebagai konfirmasi perubahan struktur.

### **E. Optimal Trade Entry (OTE)**
- Menghitung zona retracement 62%-79% antara *swing high* dan *swing low* terakhir.
- Ditampilkan sebagai area berwarna dengan garis putus-putus pada level 62% dan 79%.
- Area ini dianggap sebagai zona entry optimal oleh ICT.

### **F. Killzone (Sesi)**
- Menyoroti sesi perdagangan utama berdasarkan waktu UTC:
  - **Asia**: 00:00 – 06:00 UTC
  - **London**: 08:00 – 12:00 UTC
  - **NY**: 13:00 – 16:00 UTC
- Memberikan latar belakang berwarna pada sesi yang dipilih.

---

## 📊 Dashboard

Dashboard menampilkan informasi penting dalam tabel 4 kolom:

| Baris | Konten |
|-------|--------|
| **Header** | "📊 ICT Ultimate" (judul) |
| **Lookback** | Nilai `lookback` yang digunakan untuk swing. |
| **Swing High** | Level *swing high* terakhir. |
| **Swing Low** | Level *swing low* terakhir. |
| **Total Sinyal** | Jumlah total sinyal soup yang terdeteksi. |
| **Bullish Soup** | Jumlah sinyal bullish soup. |
| **Bearish Soup** | Jumlah sinyal bearish soup. |
| **Status** | Status saat ini (BULLISH / BEARISH / Menunggu). |
| **ATR (14)** | Nilai ATR 14 periode (untuk referensi jarak). |
| **MSS** | Status MSS (Bullish / Bearish / -). |
| **Sesi** | Status sesi (Aktif / Nonaktif). |
| **Konfirmasi** | Area untuk catatan atau konfirmasi tambahan. |

---

## 🔔 Alert Conditions

Indikator menyediakan dua kondisi *alert* bawaan:

1. **Bullish Turtle Soup** – Dipicu saat `bullishSoup` terdeteksi.
2. **Bearish Turtle Soup** – Dipicu saat `bearishSoup` terdeteksi.

Pesan alert akan memberikan notifikasi untuk memeriksa FVG, OB, dan OTE sebagai konfirmasi tambahan.

---

## 🛠️ Cara Penggunaan

1. **Tambahkan Indikator** ke chart TradingView.
2. **Sesuaikan parameter** sesuai dengan gaya trading Anda (lookback, sesi, warna, dll.).
3. **Amati area FVG dan OB** sebagai level support/resistance potensial.
4. **Perhatikan sinyal Turtle Soup** pada *swing high/low* sebagai indikasi pembalikan.
5. **Gunakan zona OTE** untuk mencari area entry optimal setelah retracement.
6. **Konfirmasi dengan MSS** untuk memastikan perubahan struktur pasar.
7. **Manfaatkan dashboard** untuk memantau kondisi pasar secara real-time.
8. **Aktifkan alert** untuk menerima notifikasi saat sinyal soup muncul.

> ⚠️ **Peringatan**: Indikator ini adalah alat analisis, bukan sistem sinyal otomatis. Selalu gunakan manajemen risiko yang baik dan konfirmasi dengan analisis lain sebelum mengambil posisi.

---

## 📥 Instalasi

1. Buka TradingView dan buka **Pine Editor**.
2. Salin seluruh kode dari file `ICT_Ultimate.txt` ke editor.
3. Beri nama (misal: "ICT Ultimate") dan simpan.
4. Tambahkan indikator ke chart Anda.

---

## 🔧 Catatan Teknis

- **Non-Repainting**: Semua sinyal dan area menggunakan data harga yang sudah terbentuk (`close`, `high`, `low` pada candle yang sudah selesai).
- **Optimasi Performa**:
  - Menggunakan `var line` dan `line.set_xy()` untuk memperbarui garis swing tanpa membuat objek baru setiap bar.
  - Menggunakan `array` untuk mengelola *box* FVG dan OB, dihapus dan digambar ulang setiap `barstate.islast` untuk menghindari penumpukan objek.
  - Menambahkan `max_bars_back=250` untuk mengatasi keterbatasan *history reference* pada offset dinamis di dalam loop.
- **FVG & OB Lookback**: Nilai lookback maksimum 200 untuk menjaga performa dan menghindari batasan *bars back* TradingView.
- **Killzone**: Berdasarkan waktu UTC (server TradingView). Sesuaikan dengan zona waktu lokal Anda.

---

## 📝 Changelog (v1.0)

- Rilis awal indikator ICT Ultimate.
- Menggabungkan Turtle Soup, FVG, Order Block, MSS, OTE, dan Killzone.
- Dashboard real-time dengan posisi dan ukuran font yang dapat disesuaikan.
- Alert untuk sinyal Turtle Soup.
- Implementasi *non-repainting* dan optimasi performa.

---

**Dibuat oleh:** Delawa ft AI
---

*"Price action is the ultimate truth. Trade what you see, not what you think."* 📈

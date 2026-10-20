# Hasil Pengujian Retrieval & Response AI

_Dihasilkan otomatis oleh notebook pada 2026-10-20 23:08._

- Embedding model: `gemini-embedding-2` (dimensi 3072)
- LLM: `gemini-3.6-flash` (temperature 0.3)
- Vector database: FAISS `IndexFlatL2` dengan vektor ternormalisasi, 59 vektor, top-k = 3
- Similarity = cosine similarity = 1 - distance/2 (makin tinggi makin mirip)

## Ringkasan

| ID | Jenis | Query | FAQ diharapkan | FAQ terambil (top-3) | Similarity #1 | Hit@1 | Hit@3 |
|---|---|---|---|---|---|---|---|
| Q1 | Jelas ada di KB | Metode pembayaran apa saja yang tersedia? | #17 | #17, #22, #20 | 0.7817 | Ya | Ya |
| Q2 | Jelas ada di KB | Bagaimana cara membatalkan pesanan yang sudah dibuat? | #3 | #3, #44, #1 | 0.7493 | Ya | Ya |
| Q3 | Parafrase / sinonim | uang saya sudah kepotong tapi orderan masih dibilang belum dibayar, gimana nih? | #21 | #21, #19, #8 | 0.8288 | Ya | Ya |
| Q4 | Parafrase / sinonim | barang yang datang pecah waktu kardusnya saya buka, saya harus ngapain? | #16 | #16, #54, #24 | 0.7234 | Ya | Ya |
| Q5 | Tidak ada di KB | Apakah bisa kirim barang ke luar negeri? | – | #5, #15, #10 | 0.6375 | – | – |

## Detail per Query

### Q1 — Jelas ada di KB

**Query:** Metode pembayaran apa saja yang tersedia?

| Rank | FAQ | Kategori | Pertanyaan FAQ | Similarity | Distance |
|---|---|---|---|---|---|
| 1 | #17 | Pembayaran | Metode pembayaran apa saja yang tersedia? | 0.7817 | 0.4365 |
| 2 | #22 | Pembayaran | Apakah bisa membayar menggunakan lebih dari satu metode sekaligus? | 0.7052 | 0.5895 |
| 3 | #20 | Pembayaran | Apakah saya bisa membayar dengan cicilan? | 0.7043 | 0.5914 |

**Jawaban LLM:**

> Halo! Untuk bertransaksi, Anda dapat memilih beberapa metode pembayaran yang tersedia, yaitu transfer bank, kartu kredit/debit, e-wallet, dan pembayaran melalui minimarket rekanan.
> 
> Sumber: FAQ #17

### Q2 — Jelas ada di KB

**Query:** Bagaimana cara membatalkan pesanan yang sudah dibuat?

| Rank | FAQ | Kategori | Pertanyaan FAQ | Similarity | Distance |
|---|---|---|---|---|---|
| 1 | #3 | Pemesanan | Bagaimana cara membatalkan pesanan yang sudah dibuat? | 0.7493 | 0.5015 |
| 2 | #44 | Produk | Bagaimana jika produk yang saya pesan ternyata kehabisan stok? | 0.6605 | 0.6790 |
| 3 | #1 | Pemesanan | Bagaimana cara melakukan pemesanan di platform ini? | 0.6564 | 0.6871 |

**Jawaban LLM:**

> Halo! Anda dapat membatalkan pesanan melalui halaman 'Pesanan Saya' selama status pesanan masih 'Diproses'. Perlu diketahui bahwa pembatalan tidak dapat dilakukan jika status pesanan sudah berubah menjadi 'Dikirim'.
> 
> Sumber: FAQ #3

### Q3 — Parafrase / sinonim

**Query:** uang saya sudah kepotong tapi orderan masih dibilang belum dibayar, gimana nih?

| Rank | FAQ | Kategori | Pertanyaan FAQ | Similarity | Distance |
|---|---|---|---|---|---|
| 1 | #21 | Pembayaran | Kenapa pembayaran saya berhasil dipotong tapi status pesanan masih belum terbayar? | 0.8288 | 0.3424 |
| 2 | #19 | Pembayaran | Berapa lama batas waktu pembayaran sebelum pesanan dibatalkan? | 0.7199 | 0.5601 |
| 3 | #8 | Pemesanan | Kenapa pesanan saya otomatis dibatalkan sistem? | 0.7150 | 0.5700 |

**Jawaban LLM:**

> Halo! Hal ini biasanya terjadi karena adanya keterlambatan sinkronisasi pada sistem pembayaran. Silakan tunggu 15–30 menit terlebih dahulu. Jika status pesanan Anda masih belum berubah setelah waktu tersebut, Anda dapat menghubungi customer service kami untuk bantuan lebih lanjut.
> 
> Sumber: FAQ #21

### Q4 — Parafrase / sinonim

**Query:** barang yang datang pecah waktu kardusnya saya buka, saya harus ngapain?

| Rank | FAQ | Kategori | Pertanyaan FAQ | Similarity | Distance |
|---|---|---|---|---|---|
| 1 | #16 | Pengiriman | Apa yang harus dilakukan jika paket diterima dalam kondisi rusak? | 0.7234 | 0.5532 |
| 2 | #54 | Pengembalian | Saya menerima barang yang salah, apa yang harus saya lakukan? | 0.6715 | 0.6570 |
| 3 | #24 | Pengembalian | Bagaimana prosedur pengembalian barang yang tidak sesuai? | 0.6502 | 0.6996 |

**Jawaban LLM:**

> Halo, mohon maaf atas ketidaknyamanan Anda. Apabila barang diterima dalam kondisi rusak, Anda dapat mengikuti langkah-langkah berikut:
> 
> 1. Segera ambil foto atau video kondisi paket saat diterima.
> 2. Laporkan melalui menu komplain dalam waktu 2x24 jam sejak barang diterima.
> 
> Sumber: FAQ #16

### Q5 — Tidak ada di KB

**Query:** Apakah bisa kirim barang ke luar negeri?

| Rank | FAQ | Kategori | Pertanyaan FAQ | Similarity | Distance |
|---|---|---|---|---|---|
| 1 | #5 | Pemesanan | Apakah saya bisa mengubah alamat pengiriman setelah pesanan dibuat? | 0.6375 | 0.7249 |
| 2 | #15 | Pengiriman | Apakah bisa memilih jasa pengiriman sendiri saat checkout? | 0.6297 | 0.7406 |
| 3 | #10 | Pengiriman | Bagaimana cara melacak paket yang sedang dikirim? | 0.6235 | 0.7531 |

**Jawaban LLM:**

> Halo! Mohon maaf, informasi mengenai pengiriman barang ke luar negeri saat ini belum tersedia di knowledge base FAQ kami. Silakan hubungi tim customer service kami untuk mendapatkan bantuan dan informasi lebih lanjut mengenai hal tersebut.
> 
> Sumber: -

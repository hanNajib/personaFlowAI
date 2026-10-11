# Pengujian & Evaluasi

Dokumen ini menjelaskan skenario pengujian PersonaFlow AI untuk memastikan rekomendasi yang diberikan sesuai dengan katalog aktivitas dan batasan pengguna.

> **Catatan:** Seluruh aktivitas dan estimasi biaya dalam katalog merupakan data fiktif untuk keperluan demonstrasi portfolio. Hasil yang diharapkan bukan bukti bahwa pengujian telah berhasil.

## Kriteria Pengujian

- Mengumpulkan empat preferensi wajib: minat, budget maksimal, waktu luang, dan mood.
- Menggunakan `persona_catalog.json` sebagai sumber data aktivitas.
- Memberikan maksimal tiga rekomendasi.
- Memastikan seluruh rentang biaya aktivitas tidak melebihi budget pengguna.
- Menjelaskan kendala jika tidak ada aktivitas yang memenuhi seluruh kriteria.
- Tidak mengarang aktivitas atau menyajikan estimasi biaya fiktif sebagai harga nyata.

## Skenario Pengujian

### 1. Rentang Biaya Melebihi Budget

**Input**

- Minat: Membaca
- Budget maksimal: Rp0
- Waktu luang: 60 menit
- Mood: Tenang dan santai

**Hasil yang diharapkan**

Aktivitas `Quiet Reading Session` memiliki rentang biaya Rp0–Rp30.000. Karena batas biaya maksimalnya melebihi budget pengguna, aktivitas tersebut tidak boleh dinyatakan terverifikasi sesuai budget.

AI harus menjelaskan kendala tersebut dan menawarkan penyesuaian preferensi tanpa mengarang alternatif.

**Hasil aktual:** Belum diuji.

**Status:** Belum dicatat.

---

### 2. Seluruh Kriteria Terpenuhi

**Input**

- Minat: Fotografi
- Budget maksimal: Rp40.000
- Waktu luang: 90 menit
- Mood: Santai dan penasaran

**Hasil yang diharapkan**

Aktivitas `Beginner Photography Walk` memiliki rentang biaya Rp0–Rp40.000 dan durasi 90 menit.

AI diharapkan merekomendasikan aktivitas tersebut dengan alasan yang sesuai katalog serta menjelaskan bahwa aktivitas dan estimasi biayanya merupakan data fiktif.

**Hasil aktual:** Belum diuji.

**Status:** Belum dicatat.

---

### 3. Minat Tidak Tersedia dalam Katalog

**Input**

- Minat: Memasak
- Budget maksimal: Rp100.000
- Waktu luang: 60 menit
- Mood: Santai

**Hasil yang diharapkan**

Karena katalog saat ini tidak memiliki aktivitas memasak, AI tidak boleh mengarang rekomendasi. AI harus menjelaskan keterbatasan katalog dan menanyakan apakah pengguna ingin mencoba minat lain atau menyesuaikan preferensi.

**Hasil aktual:** Belum diuji.

**Status:** Belum dicatat.

## Catatan Hasil Pengujian

| Tanggal | Platform | Skenario | Hasil Aktual | Status |
|---|---|---|---|---|
| 2026-10-11 | ChatGPT | 1 | Quiet Reading Session cocok pada minat, durasi, dan mood, tetapi estimasi biaya Rp0–Rp30.000 melampaui budget Rp0. Tidak ada kandidat yang memenuhi seluruh kriteria. | Perlu Ditinjau |
| 2026-10-11 | ChatGPT | 2 | Beginner Photography Walk (ACT-003) memenuhi seluruh kriteria: minat fotografi, budget Rp0–Rp40.000, durasi 90 menit, serta mood santai dan penasaran. | Lulus |
| 2026-10-11 | ChatGPT | 3 | Tidak ditemukan aktivitas yang cocok dengan minat memasak secara langsung di katalog. Sistem tidak memaksakan rekomendasi yang tidak sesuai. | Perlu Ditinjau |
| 2026-10-11 | Gemini | 1 | Merekomendasikan ACT-002 secara kondisional karena rentang biaya Rp0–Rp30.000 tidak terkonfirmasi pasti Rp0 | Lulus |
| 2026-10-11 | Gemini | 2 | Merekomendasikan ACT-003 yang sepenuhnya memenuhi minat, durasi, mood, dan batas anggaran maksimal Rp40.000 | Lulus |
| 2026-10-11 | Gemini | 3 | Menolak memberikan rekomendasi karena minat memasak tidak tersedia di katalog dan meminta penyesuaian minat | Lulus |


## Batasan Pengujian

Skenario di atas hanya mencakup beberapa kondisi penting, bukan seluruh kemungkinan input. Pengujian perlu dilakukan secara terpisah pada Gemini dan ChatGPT karena perilaku respons keduanya dapat berbeda.
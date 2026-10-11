# PersonaFlow AI

**Rekomendasi aktivitas yang disesuaikan dengan minat, budget, waktu luang, dan mood.**

PersonaFlow AI adalah proyek portfolio independen yang mengeksplorasi cara AI memberikan rekomendasi aktivitas secara terstruktur berdasarkan preferensi pengguna.

Alih-alih sekadar menghasilkan ide, PersonaFlow AI menggunakan katalog aktivitas sebagai sumber data dan menerapkan batasan yang jelas agar rekomendasi tetap relevan, transparan, dan tidak mengabaikan budget pengguna.

> **Catatan:** Seluruh aktivitas dan estimasi biaya dalam proyek ini merupakan data fiktif untuk demonstrasi portfolio, bukan penawaran layanan nyata atau harga yang telah diverifikasi.

## Fitur Utama

- **Pencocokan minat** — mencari aktivitas yang berkaitan dengan minat pengguna.
- **Batas budget yang ketat** — tidak menganggap aktivitas terjangkau jika rentang biayanya melampaui budget maksimal.
- **Pencocokan durasi** — mempertimbangkan waktu luang yang tersedia.
- **Pencocokan mood** — menyesuaikan rekomendasi dengan suasana atau energi yang diinginkan.
- **Alasan yang transparan** — menjelaskan mengapa suatu aktivitas cocok atau tidak memenuhi kriteria.
- **Penanganan tanpa hasil** — menjelaskan ketika tidak ada aktivitas yang memenuhi semua persyaratan, tanpa mengarang alternatif.
- **Berbasis katalog** — rekomendasi harus didukung oleh data yang tersedia.

## Cara Kerja

PersonaFlow AI meminta empat informasi sebelum memberikan rekomendasi personal:

1. **Minat** — aktivitas atau bidang yang ingin dieksplorasi.
2. **Budget maksimal** — batas biaya yang bersedia dikeluarkan.
3. **Waktu luang** — durasi yang tersedia.
4. **Mood** — suasana yang diinginkan, seperti santai, fokus, atau penasaran.

Setelah itu, AI membandingkan preferensi pengguna dengan katalog, memeriksa batasan yang berlaku, lalu memberikan maksimal tiga rekomendasi yang memenuhi seluruh kriteria.

Jika tidak ada hasil yang memenuhi persyaratan, AI menjelaskan kendalanya dan menawarkan penyesuaian preferensi.

## Aturan Pencocokan Budget

Budget merupakan batas keras, bukan sekadar preferensi.

Sebagai contoh, pengguna memiliki budget maksimal Rp20.000 dan waktu luang 120 menit. Katalog menyediakan aktivitas *Mini Skill Lab* dengan durasi 120 menit, tetapi estimasi biayanya Rp60.000–Rp140.000.

Meskipun durasi dan beberapa preferensinya cocok, aktivitas tersebut tidak memenuhi batas budget.

PersonaFlow AI harus menjelaskan konflik tersebut dan tidak menyajikannya sebagai rekomendasi yang terjangkau.

## Struktur Proyek

```text
personaFlowAI/
├── chatgpt/
│   └── plugin.zip
├── gemini/
│   └── skill.md
├── persona_catalog.json
└── README.md
```

- **`chatgpt/`** — paket plugin atau skill untuk lingkungan ChatGPT.
- **`gemini/`** — instruksi skill untuk lingkungan Gemini.
- **`persona_catalog.json`** — katalog aktivitas fiktif yang menjadi sumber data rekomendasi.
- **`README.md`** — dokumentasi proyek dan panduan penggunaan.

Nama file di dalam folder `chatgpt/` dan `gemini/` dapat disesuaikan dengan berkas yang benar-benar tersedia di repository.

## Prinsip Desain

PersonaFlow AI dikembangkan dengan beberapa prinsip utama:

- **Constraint-first:** batasan pengguna harus dipatuhi sebelum rekomendasi diberikan.
- **Grounded generation:** aktivitas yang direkomendasikan harus berasal dari katalog.
- **Transparency:** alasan kecocokan dan konflik kriteria harus dijelaskan.
- **Simplicity:** menggunakan instruksi dan data referensi tanpa infrastruktur tambahan yang tidak diperlukan.

## Pengujian

Beberapa skenario yang perlu diuji meliputi:

| Skenario | Perilaku yang diharapkan |
|---|---|
| Semua kriteria terpenuhi | Memberikan rekomendasi yang didukung katalog. |
| Budget terlalu rendah | Tidak menyatakan aktivitas di luar budget sebagai pilihan terjangkau. |
| Rentang biaya melewati budget | Menandai keterjangkauan sebagai belum terverifikasi. |
| Minat tidak tersedia | Tidak mengarang aktivitas baru. |
| Preferensi belum lengkap | Meminta informasi yang masih diperlukan. |
| Tidak ada kecocokan | Menjelaskan kendala dan menawarkan penyesuaian. |

## Batasan

- Katalog berisi data fiktif untuk demonstrasi.
- Sistem tidak memverifikasi harga atau ketersediaan aktivitas nyata.
- Rekomendasi terbatas pada aktivitas yang tercantum dalam katalog.
- Kualitas hasil bergantung pada kelengkapan katalog dan kejelasan instruksi.

## Tujuan Proyek

PersonaFlow AI dibuat sebagai eksperimen dalam desain instruksi AI, pencocokan berbasis batasan, dan penyusunan rekomendasi yang transparan.

## Dokumentasi

- [Pengujian & Evaluasi](docs/testing.md)

Proyek ini menunjukkan bagaimana AI dapat dirancang untuk tidak hanya memberikan jawaban, tetapi juga mempertimbangkan batasan, menjelaskan keputusan, dan mengakui ketika data yang tersedia belum cukup.

---

*PersonaFlow AI — rekomendasi yang relevan, transparan, dan berlandaskan data.*

# OCR-Based Financial Document Parsing QA Pipeline

QA pipeline yang mensimulasikan alur kerja data reviewer: ekstraksi data dokumen finansial via OCR, review manual sebagai ground truth, lalu root-cause analysis terhadap kegagalan parsing.

- **Dataset**: [SROIE 2019](https://github.com/zzzDavid/ICDAR-2019-SROIE) (20 struk belanja hasil scan)
- **Proses**: OCR (Tesseract) → parsing regex → review manual (spreadsheet + Label Studio) → iterasi perbaikan preprocessing & parsing

**Hasil akurasi (baseline → improved):**
- Vendor: 20% → 35%
- Date: 35%
- Total: 5% → 25%

**5 kategori error yang ditemukan:**
- `wrong_field_source` — OCR benar baca teks, tapi ambil baris salah (header/watermark, bukan nama bisnis asli)
- `partial_read` — Nama vendor 2 baris cuma ke-capture baris pertama
- `garbled_text` — OCR gagal total baca area tertentu (stempel/noise)
- `missed_field` — Field jelas ada, tapi regex gagal capture (variasi label: "Total" vs "Total Rounded" vs "Grand Total")
- OCR-to-label disconnection — angka dan labelnya terpisah di hasil OCR, gak bisa dibenerin cuma dengan preprocessing gambar

Juga ditemukan indikasi duplikasi dokumen dalam dataset (invoice number identik di beberapa sampel).

**Next steps:** eksplorasi OCR layout-aware (LayoutLM/Donut), tambah lapisan LLM correction, deduplikasi dokumen sebelum evaluasi.

**Struktur:**
- `notebooks/` — pipeline lengkap (load data → OCR → parsing → evaluasi)
- `annotations/` — spreadsheet ground truth & kategorisasi error
- `reports/` — ringkasan akurasi & visualisasi

**Stack:** Python · OpenCV · Tesseract · Pandas · Label Studio · Matplotlib

# MEMORY.md — docs/

Ingatan jangka panjang untuk folder `docs/`. Tambahkan catatan **bertanggal** setiap ada perubahan. Jangan hapus catatan lama: kalau sudah tidak berlaku, beri keterangan **superseded (YYYY-MM-DD)**. Aturan kerja proyek ada di `../AGENT.md`.

---

## 2026-11-04 — Spesifikasi desain "The Long Horizon" dibuat — sumber kebenaran arah visual

**Status:** dokumen saja. Tidak ada kode diubah, tidak ada aset dibuat, tidak ada frame Figma dibuat.

**File:** `docs/portfolio-design-specification.md` — 21 bagian + Appendix A (fact ledger).

**Isi ringkas:**
- Kerangka enam bab: 01 Arrival, 02 Journey, 03 Expeditions (4 proyek), 04 Toolkit, 05 Quiet Moment, 06 Next Horizon.
- Mekanik inti: warna seluruh halaman diinterpolasi dari progres scroll; tiap bab = satu waktu dalam sehari (fajar → hutan → gurun → blue hour → malam → matahari terbit).
- Lanskap = SVG inline + CSS gradient, nol raster. Tipografi Fraunces + Inter + JetBrains Mono.
- Rasio kontras dihitung, bukan diperkirakan (§8.2). Satu token tambahan diusulkan karena palet asli gagal AA sebagai teks: `--ink-body #46586A`, `--accent #8C5A2B`.
- 11 keputusan (D1–D11) menunggu approval; 16 pertanyaan (Q1–Q16) menunggu data pemilik.

**Superseded oleh dokumen ini:** tema "Scroll-Style Report" (lihat `../front/MEMORY.md`, catatan 2026-10-29 (11)). Kode di `front/` belum diubah.

**Catatan bagi sesi berikutnya:**
- Baca dokumen ini dulu sebelum menyentuh tampilan apa pun di `front/`.
- Semua placeholder `NEEDS USER INPUT` harus diisi pemilik — **jangan dikarang**.
- `design/*.figcraft` = calon arsip; jangan hapus atau pindahkan tanpa izin pemilik.
- Jangan mulai Figma, aset, atau prototyping tanpa instruksi pemilik.

## To-do
```json
[
  { "id": 1, "task": "Tunggu jawaban pemilik atas Q1-Q16 (§20.2) dan approval D1-D11 (§20.1)" },
  { "id": 2, "task": "Jika disetujui: lanjut ke langkah 3-8 di §21 (visual companion → Figma → prototype → implementation plan → QA)" }
]
```

# Analisis Kasus: Tim dengan 15 Developer

## 1. Identifikasi Masalah

Berdasarkan skenario:

- 15 developer, semua commit langsung ke `main`
- Tidak ada CI/CD
- Test coverage 25%
- Bug production setiap minggu

### Masalah Utama:

| #   | Masalah                   | Dampak                                  |
| --- | ------------------------- | --------------------------------------- |
| 1   | Tidak ada branch strategy | Konflik merge, main sering rusak        |
| 2   | Tidak ada code review     | Kode berkualitas rendah masuk           |
| 3   | Tidak ada CI/CD           | Bug tidak terdeteksi sebelum production |
| 4   | Coverage 25%              | Regresi tidak terdeteksi                |
| 5   | Tidak ada quality gate    | Tidak ada standar minimum kualitas      |

### Akar Masalah:

**Kurangnya standarisasi proses integrasi kode** — semua developer bekerja tanpa kontrak yang jelas tentang bagaimana kode diintegrasikan.

## 2. Standar yang Harus Diterapkan Pertama

### Prioritas 1 (Minggu 1-2): Branch Protection + Code Review

- **Alasan**: Menghentikan pendarahan (stop the bleeding). Tanpa ini, semua perbaikan lain akan sia-sia karena main tetap bisa rusak.
- **Aksi**: Aktifkan branch protection di main, wajib 1 reviewer.

### Prioritas 2 (Minggu 3-4): CI Sederhana

- **Alasan**: Deteksi dini kerusakan build & test.
- **Aksi**: GitHub Actions minimal — lint + test.

### Prioritas 3 (Minggu 5-8): Naikkan Coverage Bertahap

- **Alasan**: Tidak bisa langsung 80% dari 25% (terlalu besar lompatan).
- **Aksi**: Target +10% per 2 minggu.

### Prioritas 4 (Minggu 9-12): Quality Gate + CD

- **Alasan**: Setelah budaya terbentuk, otomasi gate penuh.
- **Aksi**: Coverage threshold di CI, auto-deploy ke staging.

## 3. Roadmap 3 Bulan

### Bulan 1 — Fondasi

- [ ] Aktifkan branch protection di main
- [ ] Terapkan conventional commits
- [ ] Wajib PR + 1 reviewer
- [ ] Setup CI dasar (lint + test)
- [ ] Sosialisasi standar ke tim

### Bulan 2 — Peningkatan

- [ ] Coverage naik ke 50%
- [ ] Wajib unit test untuk fitur baru
- [ ] Setup coverage reporting (Codecov)
- [ ] Mulai code review checklist
- [ ] Refactor 5 modul paling kritis dengan test

### Bulan 3 — Otomasi Penuh

- [ ] Coverage naik ke 70%
- [ ] Quality gate aktif (CI gagal jika coverage turun)
- [ ] CD ke staging otomatis
- [ ] Dokumentasi standar lengkap
- [ ] Retrospective & ukur bug production

## 4. Metrik Keberhasilan

| Metrik                | Baseline | Target 3 Bulan |
| --------------------- | -------- | -------------- |
| Test coverage         | 25%      | ≥70%           |
| Bug production/minggu | ~5       | ≤1             |
| Waktu merge PR        | ?        | <1 hari        |
| Broken main/bulan     | ?        | 0              |
| Waktu code review     | ?        | <4 jam         |

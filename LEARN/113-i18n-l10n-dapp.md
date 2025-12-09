<p align="center">
  <a href="./112-ux-dapp-best-practice.md">⬅️ Previous</a> |
  <a href="./114-postmortem-dan-lesson-learned.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./112-ux-dapp-best-practice.md">⬅️ Previous</a> |
  <a href="./114-postmortem-dan-lesson-learned.md">Next ➡️</a>
</p>
# i18n & L10n untuk dApp

## Learning Objectives
- Menambahkan dukungan multi-bahasa.
- Mengelola teks terjemahan.
- Memastikan format angka/tanggal sesuai lokal.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan library i18n (next-intl/lingui). Pisahkan string UI. Perhatikan format angka, mata uang, tanggal. Hindari hardcode bahasa di komponen.

## Hands-on Practice
1) Tambah i18n (contoh next-intl):
```bash
npm install next-intl
```
2) Buat dua locale (id/en) untuk halaman utama; simpan string di `messages/id.json`, `messages/en.json`.
3) Bungkus layout dengan provider i18n; gunakan hook `useTranslations`.
4) Format angka/tanggal memakai Intl API sesuai locale.

## Exercises / Mini Project
- Tambah language switcher di navbar; simpan preferensi di localStorage.

## Quiz
- Q1: Mengapa i18n penting?
- Q2: Tantangan format angka/tanggal?
- Q3: Bagaimana menyimpan string terjemahan?

## Skill Checklist
- [ ] i18n terpasang.
- [ ] Dua bahasa tersedia.
- [ ] Format angka/tanggal sesuai lokal.

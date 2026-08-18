# Dokumentasi Eksekusi Perintah Git (Terminal Log)

Dokumentasi riwayat eksekusi Version Control System (VCS) Git pada terminal **PowerShell 7** untuk inisialisasi repositori lokal, konfigurasi branch utama, staging berkas, commit, penautan remote GitHub, hingga proses push.

---

## 📌 Informasi Repositori
- **Direktori Kerja Lokal:** `D:\DEVELOPMENT\project-offline\tugas_devops`
- **Remote Repository URL:** `https://github.com/kasuganozomi/devops-tugas1-2305551053.git`
- **Target Branch:** `main`
- **Shell / Environment:** PowerShell 7.4.6 (Windows 11)

---

## 💻 Log Eksekusi Terminal (Clean & Structured)

```powershell
# ==========================================
# 1. Inisialisasi Git Lokal
# ==========================================
kadzu …\DEVELOPMENT\project-offline\tugas_devops
❯ git init
Initialized empty Git repository in D:/DEVELOPMENT/project-offline/tugas_devops/.git/

# ==========================================
# 2. Mengubah Branch Default ke 'main'
# ==========================================
kadzu …\tugas_devops (master)
❯ git branch -M main

# ==========================================
# 3. Menghubungkan Repositori Lokal ke Remote GitHub
# ==========================================
kadzu …\tugas_devops (main)
❯ git remote add origin https://github.com/kasuganozomi/devops-tugas1-2305551053.git

# ==========================================
# 4. Melakukan Staging Seluruh Berkas Project
# ==========================================
kadzu …\tugas_devops (main)
❯ git add .
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'laporan/struktur_laporan.md', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'tugas.md', LF will be replaced by CRLF the next time Git touches it

# ==========================================
# 5. Membuat Commit Perdana (Initial Commit)
# ==========================================
kadzu …\tugas_devops (main +)
❯ git commit -m "feat: initial commit tugas 1 devops with README and specs"
[main (root-commit) a37b7d8] feat: initial commit tugas 1 devops with README and specs
 4 files changed, 235 insertions(+)
 create mode 100644 README.md
 create mode 100644 identitas_kampus.md
 create mode 100644 laporan/struktur_laporan.md
 create mode 100644 tugas.md

# ==========================================
# 6. Melakukan Push ke Repositori Remote GitHub
# ==========================================
kadzu …\tugas_devops (main)
❯ git push -u origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 5.58 KiB | 2.79 MiB/s, done.
Total 7 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/kasuganozomi/devops-tugas1-2305551053.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

---

## 📊 Rangkuman Alur & Analisis Teknis

| No | Tahapan | Perintah | Hasil / Status |
| :---: | :--- | :--- | :--- |
| **1** | Inisialisasi | `git init` | Direktori `.git/` berhasil dibuat sebagai basis repositori lokal. |
| **2** | Standarisasi Branch | `git branch -M main` | Mengganti penamaan default `master` ke `main` sesuai standar industri. |
| **3** | Penautan Remote | `git remote add origin ...` | Menghubungkan origin ke repositori GitHub `devops-tugas1-2305551053`. |
| **4** | Indexing / Staging | `git add .` | Mendaftarkan 4 file (`README.md`, `identitas_kampus.md`, `struktur_laporan.md`, `tugas.md`). |
| **5** | Commit | `git commit -m "..."` | Menciptakan commit root `a37b7d8` dengan pesan deskriptif. |
| **6** | Sinkronisasi Remote | `git push -u origin main` | Mengunggah seluruh snapshot lokal ke branch `main` remote GitHub. |

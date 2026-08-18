# Kerangka Struktur Laporan Tugas 1: DevOps Development

---

## HALAMAN SAMPUL (COVER)
- **Judul Tugas:** Laporan Praktikum & Implementasi Dasar DevOps Development
- **Nama Lengkap:** I Kadek Adi Sunetra
- **NIM:** 2305551053
- **Kelas:** [Kelas / Paralel]
- **Program Studi / Jurusan:** Teknologi Informasi
- **Tahun:** 2026

---

## BAB 1: PENDAHULUAN

### 1.1 Latar Belakang
- Urgensi standardisasi lingkungan kerja (*environment*) pengembang sebelum mengelola infrastruktur skala institusi.
- Peran budaya DevOps, Version Control System (Git), dan kontainerisasi (Docker) dalam menghilangkan masalah "*works on my machine*".

### 1.2 Rumusan Masalah
1. Bagaimana perbedaan mendasar antara siklus *Waterfall* dengan budaya *DevOps*?
2. Mengapa *Continuous Integration* (CI) krusial pada pengembangan sistem skala besar multi-modul?
3. Apa keunggulan *Container* dibanding *Virtual Machine* konvensional pada arsitektur *microservices*?
4. Bagaimana proses instalasi, konfigurasi, dan verifikasi Git serta Docker di lingkungan lokal?

### 1.3 Tujuan
1. Memahami konsep dasar filosofi DevOps, CI, dan kontainerisasi.
2. Mengonfigurasi dan memvalidasi instalasi Git, Docker (WSL2), dan Code Editor (Zed Editor) di sistem operasi lokal (Windows 11).
3. Mempraktikkan alur kerja dasar VCS GitHub (clone, commit, push) serta pengujian eksekusi container Docker.

---

## BAB 2: KAJIAN PUSTAKA

*(Pembahasan konseptual ringkas, padat, dan disertai sitasi ilmiah/resmi)*

### 2.1 Perbandingan Siklus Waterfall dan Budaya DevOps
- Konsep Waterfall (tahapan sekuensial, silo antar tim, *feedback loop* lambat).
- Konsep DevOps (siklus iteratif, integrasi dev + ops, otomatisasi, kolaborasi berkelanjutan).

### 2.2 Urgensi Continuous Integration (CI) pada Sistem Skala Besar
- Masalah integrasi manual (*merge conflicts*, *integration hell*).
- Prinsip CI: otomatisasi pengujian (*automated build & test*) setiap ada perubahan kode.
- Contoh kasus nyata pada sistem berskala besar.

### 2.3 Perbandingan Virtual Machine (VM) dan Container (Docker)
- Perbedaan arsitektur: Hypervisor + Guest OS (VM) vs Shared OS Kernel (Container).
- Efisiensi resource, portabilitas, waktu startup cepat, dan kesesuaian untuk arsitektur *microservices*.

---

## BAB 3: METODE DAN ALUR KERJA

### 3.1 Spesifikasi Lingkungan Kerja (Environment)
*Catatan: Sesuai fleksibilitas opsi pada instruksi penugasan, laporan ini memilih platform GitHub, editor Zed, shell PowerShell 7, dan sistem operasi Windows 11.*

- **Sistem Operasi:** Windows 11 (dengan arsitektur backend WSL2 untuk virtualisasi Docker)
- **Terminal / Shell:** PowerShell 7 (`pwsh`)
- **Code Editor:** Zed Editor (menggantikan VS Code; editor modern performa tinggi dengan dukungan Git bawaan yang efisien)
- **Platform VCS:** GitHub (dipilih sebagai penyedia *remote repository* publik)
- **Spesifikasi Hardware:** [Processor, RAM, Storage]

### 3.2 Langkah Kerja
1. **Instalasi & Konfigurasi Git:** Pemasangan Git dan konfigurasi identitas global (`user.name` & `user.email`) melalui terminal PowerShell 7.
2. **Setup Docker Engine:** Pemasangan Docker Desktop dengan integrasi backend WSL2 pada Windows 11.
3. **Pengelolaan Repositori GitHub & Penyuntingan:**
   - Pembuatan repositori publik `devops-tugas1-NIM` di GitHub.
   - Kloning ke direktori lokal, pembuatan dan penyuntingan file `README.md` menggunakan Zed Editor.
   - Pelaksanaan proses *staging*, *commit*, dan *push* ke remote GitHub.
4. **Verifikasi Runtime Container:** Eksekusi container pengujian standar `hello-world` melalui PowerShell 7.

---

## BAB 4: HASIL DAN PEMBAHASAN

### 4.1 Verifikasi Instalasi Perangkat Lunak
- **Tangkapan Layar 1:** Output perintah terminal `git --version` di PowerShell 7.
  - *Penjelasan:* Verifikasi versi Git yang terpasang dan siap digunakan.
- **Tangkapan Layar 2:** Output perintah terminal `docker --version` di PowerShell 7.
  - *Penjelasan:* Verifikasi kesiapan Docker Engine dan runtime daemon.

### 4.2 Repositori Publik GitHub & File README.md
- **Tautan Repositori:** `https://github.com/kasuganozomi/devops-tugas1-2305551053`
- **Tangkapan Layar 3:** Tampilan halaman repositori publik di GitHub yang memuat file `README.md` (diedit via Zed Editor).
  - *Penjelasan:* Bukti repositori publik aktif dengan file `README.md` yang memuat identitas serta spesifikasi perangkat kerja.

### 4.3 Pengujian Container Docker
- **Tangkapan Layar 4:** Output terminal PowerShell 7 saat menjalankan perintah `docker run hello-world`.
  - *Penjelasan:* Analisis respon *"Hello from Docker!"* sebagai bukti runtime kontainerisasi bekerja dengan sukses di atas WSL2.

---

## DAFTAR PUSTAKA

1. Bass, L., Weber, I., & Zhu, L. (2015). *DevOps: A Software Architect's Perspective*. Addison-Wesley Professional.
2. Fowler, M. (2006). *Continuous Integration*. martinfowler.com.
3. Merkel, D. (2014). *Docker: lightweight linux containers for consistent development and deployment*. Linux Journal, 2014(239), 2.
4. Chacon, S., & Straub, B. (2014). *Pro Git* (2nd ed.). Apress.
5. Docker Documentation. (2026). *Docker Architecture and Overview*. docs.docker.com.

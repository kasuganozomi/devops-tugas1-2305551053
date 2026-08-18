# Tugas 1: DevOps Development

| **Informasi** | **Detail** |
| :--- | :--- |
| **Mata Kuliah** | DevOps Development |
| **Sifat Tugas** | Individu |
| **Batas Waktu Pengumpulan** | 18 Agustus 2026, Pukul 12.00 WITA |

---

## A. Deskripsi dan Tujuan Tugas

Sebagai calon DevOps Engineer atau Pengembang Perangkat Lunak modern, langkah pertama sebelum Anda ditugaskan untuk mengelola infrastruktur sistem berskala institusi (misalnya, pengembangan portal akademik terintegrasi) adalah memastikan perangkat kerja Anda memiliki standar yang sama dengan anggota tim lainnya.

### Tujuan Tugas:
1. Mengevaluasi pemahaman mahasiswa mengenai filosofi dan budaya DevOps.
2. Memastikan seluruh perangkat lunak esensial (Git, Docker, dan Code Editor) telah terinstal dan terkonfigurasi dengan benar di sistem operasi masing-masing mahasiswa.
3. Menguji kemampuan dasar penggunaan *Version Control System* (VCS) dan *Container Engine*.

---

## B. Rincian Tugas

Tugas ini dibagi menjadi tiga bagian utama. Mahasiswa wajib menyelesaikan seluruh bagian dan mendokumentasikannya ke dalam satu laporan berformat PDF.

### Bagian 1: Eksplorasi Konsep (Kajian Pustaka Singkat)

> **Catatan:** Jawablah pertanyaan berikut dengan bahasa Anda sendiri (maksimal 300 kata per pertanyaan). Hindari melakukan *copy-paste* secara langsung dari internet atau AI.

1. **Waterfall vs DevOps**  
   Jelaskan perbedaan mendasar antara siklus pengembangan perangkat lunak tradisional (*Waterfall*) dengan budaya DevOps!

2. **Continuous Integration (CI) pada Sistem Skala Besar**  
   Mengapa praktik *Continuous Integration* (CI) sangat krusial ketika sebuah tim pengembang membangun sistem berskala besar yang memiliki banyak modul? Berikan contoh kasus nyata.

3. **Virtual Machine vs Container**  
   Apa perbedaan antara *Virtual Machine* (VM) konvensional dengan *Container* (seperti Docker), dan mengapa *Container* lebih disukai dalam arsitektur *Microservices*?

---

### Bagian 2: Persiapan Infrastruktur Lokal (*Hands-on*)

Lakukan instalasi dan konfigurasi perangkat lunak berikut pada komputer/laptop Anda/VPS:

1. **Git & Akun VCS**
   - Instal Git versi terbaru.
   - Buat akun di GitLab atau GitHub (gunakan email institusi/kampus jika ada).
   - Lakukan konfigurasi identitas Git di terminal Anda:
     ```bash
     git config --global user.name "Nama Lengkap Anda"
     git config --global user.email "email.anda@domain.com"
     ```

2. **Docker Engine**
   - Instal Docker Desktop (untuk Windows/Mac) atau Docker Engine (untuk Linux).
   - *Khusus pengguna Windows:* Pastikan fitur WSL2 (*Windows Subsystem for Linux*) telah diaktifkan.

3. **Code Editor**
   - Instal Visual Studio Code (VS Code).
   - Pasang ekstensi esensial berikut:
     - `GitLens`
     - `Docker`
     - `Remote Development`

> **Instruksi Dokumentasi:**  
> Ambil tangkapan layar (*screenshot*) yang menunjukkan bahwa Git dan Docker telah berhasil diinstal. (Gunakan perintah `git --version` dan `docker --version` di terminal).

---

### Bagian 3: Implementasi Dasar (Pembuktian)

Untuk membuktikan bahwa seluruh perangkat lunak telah berjalan dan terhubung dengan baik, lakukan langkah berikut:

1. Buat sebuah repositori publik baru di GitLab/GitHub dengan nama `devops-tugas1-NIM`.
2. Lakukan *clone* repositori tersebut ke komputer lokal Anda.
3. Buat sebuah file bernama `README.md` dan tuliskan perkenalan singkat diri Anda beserta spesifikasi laptop yang digunakan (OS, RAM, Processor).
4. Lakukan proses *commit* dan *push* file tersebut ke repositori jarak jauh (*remote repository*).
5. Buka terminal Anda, lalu jalankan perintah berikut untuk mengunduh dan menjalankan *container* pengujian standar dari Docker:
   ```bash
   docker run hello-world
   ```

> **Instruksi Dokumentasi:**  
> Ambil tangkapan layar (*screenshot*) dari:
> 1. Halaman repositori GitLab/GitHub Anda yang sudah berisi file `README.md`.
> 2. Terminal yang menampilkan pesan `"Hello from Docker!"` dari perintah di atas.

---

## C. Format Pengumpulan Laporan (*Deliverables*)

1. **Format File:** Laporan disusun dalam format **PDF**.
2. **Halaman Sampul:** Memuat Judul Tugas, Nama Lengkap, NIM, dan Kelas.
3. **Isi Laporan:**
   - Jawaban **Bagian 1** (Eksplorasi Konsep).
   - Tautan (URL) menuju repositori GitLab/GitHub Anda yang dapat diakses secara publik.
   - Tangkapan layar (*screenshots*) dari **Bagian 2** dan **Bagian 3**, disertai penjelasan singkat di bawah setiap gambar.
4. **Format Penamaan File:**
   ```text
   Tugas1_DevOps_NIM_NamaLengkap.pdf
   ```
LAPORAN TUGAS 1 DEVOPS DEVELOPMENT: INISIASI INFRASTRUKTUR LOKAL, MANAJEMEN REPOSITORI GIT, DAN PENGUJIAN RUNTIME DOCKER

 

Oleh,
I Kadek Adi Sunetra			2305551053







HALAMAN SAMPUL
DEVOPS DEVELOPMENT
Pengampu,
~

FAKULTAS TEKNIK JURUSAN TEKNOLOGI INFORMASI
UNIVERSITAS UDAYANA
DENPASAR 2026 
DAFTAR ISI
HALAMAN SAMPUL	i
BAB I PENDAHULUAN	1
1.1	Latar Belakang	1
1.2	Rumusan Masalah	1
1.3	Tujuan	1
BAB 2  KAJIAN PUSTAKA	3
2.1	Perbandingan Siklus Waterfall dan Budaya DevOps	3
2.2	Urgensi Continuous Integration (CI) pada Sistem Skala Besar	3
2.3	Perbandingan Virtual Machine (VM) dan Container (Docker)	3
BAB 3  DESAIN DAN ALUR KERJA	5
3.1	Spesifikasi Lingkungan Kerja	5
3.2	Alur Pelaksanaan Tugas	5
BAB 4 HASIL DAN PEMBAHASAN	6
4.1	Install Docker di PowerShell	6
4.2	Version Check dan Inisialisasi Repositori Lokal serta Konfigurasi Git	6
4.3	Pengujian Runtime Kontainer Docker (Hello-World)	8
4.4	Repositori Publik GitHub dan Pengelolaan README.md	9
BAB 5  KESIMPULAN	10
DAFTAR PUSTAKA	11

 
BAB I
PENDAHULUAN

1.1	Latar Belakang
Dalam rekayasa perangkat lunak modern, kesenjangan konfigurasi antara lingkungan pengembangan lokal dan server produksi sering memicu kegagalan rilis, atau yang dikenal dengan masalah "it works on my machine". Saat sebuah tim membangun sistem berskala institusi yang terdistribusi, ketiadaan standardisasi perangkat kerja menyebabkan konflik dependensi dan inefisiensi integrasi.
Paradigma DevOps hadir untuk menyatukan peran pengembang (Development) dan operasional (Operations) melalui budaya kolaborasi dan otomatisasi. Penggunaan Version Control System seperti Git (Chacon and Straub, 2014) dan kontainerisasi seperti Docker menjadi fondasi penting agar lingkungan kerja dapat direproduksi secara konsisten dan siap diintegrasikan ke alur CI/CD. Praktikum ini bertujuan memvalidasi kesiapan perangkat kerja lokal dan menguji alur kerja dasar Git serta Docker.

1.2	Rumusan Masalah
1.	Apa perbedaan mendasar antara siklus Waterfall dan budaya DevOps?
2.	Mengapa Continuous Integration (CI) sangat krusial pada sistem skala besar multi-modul?
3.	Apa perbedaan arsitektur Virtual Machine dan Container, serta mengapa Container lebih disukai pada arsitektur microservices?
4.	Bagaimana konfigurasi dan pembuktian fungsionalitas Git serta Docker di lingkungan Windows 11?

1.3	Tujuan
1.	Memahami landasan konseptual budaya DevOps, CI, dan efisiensi kontainerisasi.
2.	Memasang dan mengonfigurasi perangkat kerja lokal (Git, Docker Desktop berbasis WSL2, PowerShell 7, dan Zed Editor).
3.	Mengelola repositori publik GitHub untuk dokumentasi spesifikasi perangkat kerja.
4.	Memvalidasi runtime Docker Engine melalui eksekusi container pengujian standar.
 
BAB 2 
KAJIAN PUSTAKA
2.1	Perbandingan Siklus Waterfall dan Budaya DevOps
Metodologi Waterfall adalah pendekatan linier sekuensial di mana tahapan analisis, desain, implementasi, pengujian, dan pemeliharaan harus selesai bertahap sebelum beralih ke fase berikutnya. Pendekatan ini menciptakan batas pemisah yang kaku antara tim pengembang dan tim operasional, sehingga umpan balik menjadi sangat lambat dan risiko kegagalan integrasi pada akhir proyek sangat tinggi.
Sebaliknya, DevOps merupakan transformasi budaya yang mengintegrasikan pengembang dan operasional ke dalam siklus berkelanjutan melalui otomatisasi (Bass et al., 2015). DevOps berfokus pada rilis berkala dalam skala kecil, iterasi cepat, dan pemantauan terus-menerus. Hal ini secara signifikan memangkas waktu tunggu rilis dan meningkatkan keandalan sistem.

2.2	Urgensi Continuous Integration (CI) pada Sistem Skala Besar
Continuous Integration (CI) adalah praktik di mana pengembang secara rutin menggabungkan perubahan kode ke repositori utama, yang langsung diverifikasi oleh proses build dan pengujian otomatis (Fowler, 2006).
Pada sistem berskala besar yang terdiri dari banyak modul terpisah, ketiadaan CI memicu masalah "Integration Hell", yaitu tumpukan konflik kode yang sangat rumit saat modul digabungkan di akhir waktu.
Contoh Kasus Nyata:
Pada sistem Portal Akademik Terpadu yang memiliki modul Registrasi Mahasiswa, Modul Finansial/Pembayaran, dan Modul Jadwal Kuliah, pembaruan API pada modul Pembayaran berisiko merusak modul Registrasi. Dengan CI, setiap pembaruan kode otomatis memicu unit test dan integration test. Jika terjadi ketidakcocokan antar-modul, sistem otomatis membatalkan build dan memberikan notifikasi instan kepada tim sebelum kode dirilis ke lingkungan produksi.

2.3	Perbandingan Virtual Machine (VM) dan Container (Docker)
Perbedaan utama VM dan Container terletak pada tingkat abstraksi virtualisasinya (Merkel, 2014):
1.	Virtual Machine (VM): Bekerja pada level perangkat keras menggunakan Hypervisor. Setiap VM menjalankan Guest OS lengkap beserta kernel mandiri, sehingga memakan kapasitas penyimpanan besar (gigabyte), memori tinggi, dan waktu booting lama.
2.	Container (Docker): Bekerja pada level sistem operasi dengan berbagi kernel OS induk (Host OS Kernel) bersama-sama. Isolasi proses dan alokasi resource dilakukan secara efisien melalui fitur Linux Kernel seperti namespaces dan cgroups (Docker Documentation, 2026).
Dalam arsitektur Microservices, Container lebih disukai karena ukurannya yang sangat ringan (megabyte), waktu startup instan dalam hitungan milidetik, serta portabilitas tinggi antar-lingkungan komputasi tanpa beban sistem operasi tamu yang redundan.

 
BAB 3 
DESAIN DAN ALUR KERJA

3.1	Spesifikasi Lingkungan Kerja
Praktikum ini menggunakan lingkungan komputasi dengan konfigurasi berikut:
Sistem Operasi	Windows 11 Pro (Build 25H2) x86_64
Processor (CPU)	AMD Ryzen 5 6600H with Radeon Graphics (6 Cores, 12 Threads)
Memory (RAM)	16 GB DDR5
Virtualisasi	AMD-V Virtualization Aktif pada BIOS (Enabled)
Shell Terminal	PowerShell 7.4.6
Code Editor	Zed Editor
Version Control	Git versi 2.54.0 & GitHub
Container	Docker Desktop (Engine versi 29.7.2, WSL2 Backend)

3.2	Alur Pelaksanaan Tugas
1. Pemasangan perangkat lunak pendukung (Git, Docker Desktop, dan Zed Editor) pada sistem operasi Windows 11.
2. Verifikasi kesiapan toolchain dan pengecekan versi (git --version dan docker --version) melalui terminal PowerShell 7.
3. Pembuatan repositori publik devops-tugas1-2305551053 di GitHub.
4. Inisialisasi repositori lokal (git init), penautan remote origin, pembuatan berkas README.md berisi identitas dan spesifikasi perangkat kerja, kemudian dilanjutkan dengan staging, initial commit, dan push ke remote GitHub.
5. Pengujian fungsionalitas dan runtime kontainerisasi Docker Engine melalui eksekusi container pengujian standar (docker run hello-world).
6. Verifikasi akhir pada antarmuka web repositori publik GitHub untuk memastikan berkas README.md ter-render dengan sempurna.

 
BAB 4
HASIL DAN PEMBAHASAN

4.1	Install Docker di PowerShell
 
Gambar 4.1 Melakukan installasi Docker Menggunakan WinGet.

4.2	Version Check dan Inisialisasi Repositori Lokal serta Konfigurasi Git
 



Gambar dan PWSH 4.2 Check versi dan Alur Perintah Git Lokal Hingga Berhasil Push ke GitHub
Pada Gambar dan PWSH 4.2, direktori kerja lokal berhasil diinisialisasi menjadi repositori Git menggunakan perintah git init, lalu nama branch default dialihkan menjadi main. Setelah repositori lokal ditautkan ke remote origin GitHub, seluruh berkas proyek termasuk README.md dimasukkan ke staging area (git add .) dan disimpan melalui initial commit. Perintah git push -u origin main berhasil mengirimkan seluruh objek snapshot ke repositori GitHub tanpa kendala otentikasi.


4.3	Pengujian Runtime Kontainer Docker (Hello-World)


Gambar 4.3 Output Eksekusi Kontainer hello-world pada Terminal PowerShell 7
Pada Gambar 4.3, perintah docker run hello-world berhasil dijalankan dengan sempurna. Karena image belum tersedia di penyimpanan lokal, Docker Daemon secara otomatis mengunduh image dari Docker Hub, membangun container baru yang terisolasi di atas WSL2 backend, dan mengeksekusi program hingga menampilkan teks "Hello from Docker!". Hal ini membuktikan bahwa Docker Engine dan daemon telah berfungsi normal.


4.4	Repositori Publik GitHub dan Pengelolaan README.md


Gambar 4.4 Tampilan Repositori Publik devops-tugas1-2305551053 pada Web Browser
Gambar 4.4 menampilkan antarmuka repositori publik pada URL https://github.com/kasuganozomi/devops-tugas1-2305551053. Berkas README.md yang disunting menggunakan Zed Editor berhasil ditampilkan dengan rapi pada repositori, menyajikan informasi identitas mahasiswa serta tabel spesifikasi perangkat kerja secara lengkap dan terbuka.
 
BAB 5 
KESIMPULAN

1.	Paradigma DevOps dan praktik Continuous Integration (CI) mampu mengeliminasi silo antartim serta memitigasi risiko kegagalan integrasi pada pengembangan sistem multi-modul.
2.	Kontainerisasi (Docker) menyediakan isolasi proses yang efisien, konsumsi sumber daya yang hemat, dan portabilitas tinggi dibandingkan Virtual Machine konvensional.
3.	Seluruh perangkat kerja lokal (Git v2.54.0, Docker Desktop v29.7.2, PowerShell 7, dan Zed Editor) pada lingkungan Windows 11 telah berhasil dipasang, dikonfigurasi, dan diverifikasi siap digunakan untuk alur pengembangan DevOps berikutnya.
 
DAFTAR PUSTAKA

[1]	L. Bass, I. Weber, and L. Zhu, DevOps: A Software Architect's Perspective. Boston, MA, USA: Addison-Wesley, 2015.
[2]	M. Fowler, "Continuous Integration," MartinFowler.com, 2006. [Online]. Tersedia: https://martinfowler.com/articles/continuousIntegration.html. [Diakses: 18-Agu-2026].
[3]	D. Merkel, "Docker: Lightweight Linux containers for consistent development and deployment," Linux J., vol. 2014, no. 239, hal. 2, Mar. 2014.
[4]	Docker Documentation, "Docker Architecture and Container Runtime Overview," Docker Docs, 2026. [Online]. Tersedia: https://docs.docker.com/get-started/overview/. [Diakses: 18-Agu-2026].
[5]	S. Chacon and B. Straub, Pro Git, 2nd ed. New York, NY, USA: Apress, 2014. doi: 10.1007/978-1-4842-0076-6.

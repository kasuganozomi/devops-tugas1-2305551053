# Dokumentasi Eksekusi Container Docker (Terminal Log)

Dokumentasi riwayat pengujian *Container Engine* Docker Desktop melalui terminal **PowerShell 7** dengan menjalankan image standar `hello-world`.

---

## 📌 Informasi Eksekusi
- **Direktori Kerja:** `D:\DEVELOPMENT\project-offline\tugas_devops` (Branch: `main`)
- **Perintah:** `docker run hello-world`
- **Container Image:** `hello-world:latest` (Registry: Docker Hub)
- **Status:** **SUKSES (Exit Code 0)**

---

## 💻 Log Eksekusi Terminal

```powershell
kadzu …\tugas_devops (main) 09:37
❯ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete
d5e71e642bf5: Download complete
Digest: sha256:5dd0d3e6e255913fc30f90b9f2b1d359cc2cbdb48090cc4b65f1676e203243cc
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

---

## 📊 Analisis Alur Kerja Docker Engine
Berdasarkan log di atas, alur kerja kontainerisasi berjalan melalui 4 tahap utama:
1. **Client to Daemon Communication:** Docker CLI lokal di PowerShell mengirimkan instruksi eksekusi ke Docker Daemon (yang berjalan di atas arsitektur WSL2 backend).
2. **Registry Pulling:** Karena image `hello-world:latest` belum ada di *local storage cache*, daemon secara otomatis mengunduh layer image dari registry resmi Docker Hub.
3. **Container Instantiation:** Daemon membuat *isolated container lifecycle* baru berbasis image tersebut dan mengeksekusi binary program di dalamnya.
4. **I/O Streaming:** Output dari stdout container dialirkan kembali ke terminal PowerShell pengguna hingga menampilkan pesan `"Hello from Docker!"`.

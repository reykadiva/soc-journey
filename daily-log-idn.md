# SOC Journey Log Indonesia

---

## Day 1 - Instalasi Ubuntu & Fundamental Permission Linux
Tanggal: 2026-02-20  
Durasi: 3-4 jam  
Fokus: Dasar Linux & Manajemen Privilege  

---

### 🎯 Tujuan Hari Ini
- Install Ubuntu di VirtualBox
- Memahami struktur file system Linux
- Belajar permission file dan directory
- Memahami konsep SetUID dan privilege escalation dasar

---

### 🛠 Aktivitas Praktik

#### 1. Setup Virtual Lab
- Install VirtualBox
- Membuat VM Ubuntu-SOC-Lab (4GB RAM, 2 CPU, 40GB disk)
- Install Ubuntu Desktop LTS secara manual (interactive mode)
- Update package sistem
- Install tools dasar (curl, wget, git, net-tools, htop, vim)

---

#### 2. Eksplorasi File System Linux

Command yang dipakai:
- ```bash
- pwd
- ls
- ls -la /
- cd ~
- touch testfile
- ls -l testfile

Yang dipelajari:
- `/` adalah root directory (folder paling atas di Linux)
- `/home` kurang lebih setara dengan `C:\Users\` di Windows
- Permission pada directory menentukan apakah file di dalamnya bisa dihapus atau tidak

---

#### 3. Model Permission Linux

Mempelajari format permission seperti:
-rw-r--r--

Yang dipahami:
- Karakter pertama menunjukkan tipe file
- Struktur terbagi menjadi Owner / Group / Others
- r = read (baca)
- w = write (ubah)
- x = execute (jalankan)

Insight penting:
Untuk menghapus file, yang dibutuhkan adalah write permission pada directory, bukan pada file itu sendiri.

---

#### 4. Konsep SetUID

Eksplorasi:
ls -l /usr/bin/passwd
find / -perm -4000 2>/dev/null

Yang dipelajari:
- Huruf `s` pada permission menandakan SetUID
- SetUID membuat program berjalan dengan effective UID milik owner file
- `/usr/bin/passwd` berjalan dengan privilege root
- User tidak berubah menjadi root, tetapi prosesnya berjalan sebagai root

Memahami perbedaan:
- Real UID (identitas asli user yang login)
- Effective UID (UID yang digunakan proses saat berjalan)

---

#### 5. Awareness Privilege Escalation

Membandingkan tingkat risiko dari:
- Permission 777
- SetUID root
- SetUID root + world writable

Pemahaman utama:
- Binary SetUID root berisiko tinggi jika memiliki vulnerability
- File root yang world-writable bisa menyebabkan privilege escalation lewat modifikasi isi file
- Kombinasi SetUID root + world writable termasuk misconfiguration yang sangat kritis

---

### 🔎 Insight Security Hari Ini

- Security di Linux sangat bergantung pada permission
- Konsep privilege separation itu fundamental
- Salah konfigurasi SetUID bisa berujung root compromise
- Effective UID menentukan privilege proses sebenarnya
- Tidak semua privilege escalation melibatkan sudo

---

### ❓ Pertanyaan / Hal yang Masih Membingungkan

- Bagaimana Linux secara internal berpindah antara real UID dan effective UID?
- Bagaimana eksploitasi SetUID dilakukan di dunia nyata?

---

### 📈 Refleksi Progress

- Awal yang seru banget tapi aga sulit untuk diserap karna bener bener hal baru buat saya
- Hari ini cukup dasar tapi lumayan intens.
- Dari hanya menjalankan command Linux, mulai paham mekanisme privilege dan risiko escalation.
- Mulai berpikir sebagai defender, bukan sekadar user biasa.

---

### 🗓 Rencana Besok

- Mendalami sudo dan file `/etc/sudoers`
- Belajar logging Linux (`/var/log/auth.log`)
- Mulai latihan dasar analisis log

---
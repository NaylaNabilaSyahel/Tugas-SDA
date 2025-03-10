# 📚 Tugas Kelompok Praktikum Struktur Data dan Algoritma 📚
## Sistem Antrean Bank 💰 
---

### Anggota Kelompok 4:
| Nama                   | NPM           |
|------------------------|---------------|
| Hazairin               | 2408107010001 |
| Nayla Nabila Syahel    | 2408107010005 |
| Raisa Salsa Nabila     | 2408107010007 |
| Rahmatul Uliya         | 2408107010012 |
| Dara Ramadhani         | 2408107010028 |
| Habib Nuran Mulkan     | 2408107010109 |

---

### 🗒️ Deskripsi Singkat Program:

Program ini adalah sitem manajemen antrean nasabah di bank yang menggunakan queue berbasis linked list untuk mengelola antrean layanan, serta stack berbasis linked list untuk menyimpan riwayat transaksi nasabah yang telah di proses.

---

### 📌 Instruksi Kompilasi dan Cara Menjalankan Program:

Program ini menggunakan **Makefile** untuk mempermudah proses kompilasi dan eksekusi.

- Jalankan perintah berikut di terminal:  
  ```sh
  make
  ```
  📌 Perintah ini akan mengompilasi semua file sumber dan menghasilkan file eksekusi `mainSda`.

- Setelah berhasil dikompilasi, jalankan program dengan:  
  ```sh
  ./mainSda
  ```
  📌 Pastikan file `mainSda` telah dibuat sebelum menjalankan perintah ini.
  
---
      
### 🏦 Struktur Data yang Digunakan untuk Membangun Program Antrean Bank:

🔹 **Queue berbasis Linked List** 🔗
   - Program ini menggunakan **Queue berbasis Linked List** untuk menyimpan data antrean nasabah yang sedang menunggu untuk diproses.
   - Queue mengikuti prinsip **FIFO (First In, First Out)**, sehingga nasabah yang pertama masuk akan diproses lebih dahulu.

🔹 **Stack berbasis Linked List** 🔗
   - Selain antrean, program ini juga menggunakan **Stack berbasis Linked List** untuk menyimpan transaksi nasabah yang telah diproses.
   - Stack mengikuti prinsip **LIFO (Last In, First Out)**, sehingga transaksi terakhir yang diproses akan berada di bagian atas dan bisa dibatalkan jika diperlukan.
  
---

### 🤔 Alasan Pemilihan Struktur Data:

Queue dan Stack diimplementasikan menggunakan **Linked List** karena:

✅ **Fleksibel** – Tidak memiliki batasan ukuran seperti array, cocok untuk antrean yang jumlahnya tidak dapat diprediksi.  
✅ **Efisien dalam penambahan & penghapusan** – Operasi enqueue, dequeue, push, dan pop dapat dilakukan dalam **O(1)** waktu tanpa perlu menggeser elemen seperti pada array.  
✅ **Cocok untuk sistem antrean bank** – Karena jumlah nasabah yang antre bisa terus bertambah atau berkurang, sehingga penggunaan memori lebih efisien.  

Struktur data **Stack** dan **Queue** dipilih untuk diimplementasikan menggunakan **Linked List**, sebab ukuran Linked List tidak terbatas selama memori masih tersedia. Hal ini sesuai dengan konsep antrean bank, karena banyaknya antrean dalam bank tidak dapat ditentukan. Sehingga akan sangat tidak efisien jika diimplementasikan menggunakan array. Oleh karena itu, **Linked List menjadi solusi yang sangat cocok dalam program ini.**

---

### ⚙️ Implementasi Struktur Data:

#### 🔹 Queue berbasis Linked List
Dalam program antrean nasabah, **Queue** diimplementasikan untuk melakukan beberapa proses berikut:

⓵ **enqueue()** – Menambahkan nasabah ke daftar antrean.
   - Nasabah ditambahkan dari belakang sesuai dengan konsep antrean dalam kehidupan nyata, sehingga proses pelayanan dilakukan teratur.

⓶ **dequeue()** – Menghapus nasabah dari antrean setelah selesai diproses.
   - Penghapusan nasabah dilakukan dari depan sesuai dengan konsep FIFO.
   - Setelah penghapusan, nasabah berikutnya akan diproses.

⓷ **tampilkanAntrian()** – Menampilkan daftar antrean yang menunggu untuk dilayani.
   - Data antrean ditampilkan sesuai dengan urutan masuk.
   - Jika antrean kosong, sistem akan menampilkan pesan **"Antrean kosong"**.

#### 🔹 Stack berbasis Linked List
Dalam program antrean nasabah, **Stack** diimplementasikan untuk melakukan beberapa proses berikut:

⓵ **pop()** – Menambahkan nasabah ke daftar riwayat layanan.
   - Ketika seorang nasabah telah selesai dilayani (dikeluarkan dari Queue), data nasabah tersebut akan dimasukkan ke dalam **Stack**.
   - Penambahan dilakukan dari **atas (top)**, sehingga data terakhir yang masuk selalu berada di posisi paling atas.

⓶ **push() / undoTransaksi** – Menghapus data nasabah dari riwayat layanan.
   - Data nasabah terakhir yang masuk ke daftar riwayat layanan akan dihapus dan dikembalikan ke daftar antrean.
   - Penghapusan dilakukan dari posisi **top**, mengikuti konsep **LIFO**.

⓷ **tampilkanRiwayat()** – Menampilkan riwayat nasabah yang telah selesai diproses.
   - Nasabah pertama yang diproses akan ditampilkan lebih dahulu.
   - Jika tidak ada nasabah yang telah dilayani, sistem akan menampilkan pesan **"Riwayat kosong"**.

---
        
### 🔍 Kendala dan Solusi dalam Program Antrean Bank:

➊ Kendala dalam Pengelolaan Antrean (Queue)

   - 💡**Masalah:**
     
      Nasabah yang telah selesai diproses dihapus dari antrean, tetapi data nasabah yang telah diproses tidak tersimpan.
      Tidak ada mekanisme untuk membatalkan proses nasabah yang sudah dikeluarkan dari antrean.
     
   - ✅ **Solusi:**
     
      Implementasi Stack (Riwayat Layanan) untuk menyimpan nasabah yang telah diproses.
      Menambahkan fitur Undo Transaksi menggunakan pop() untuk memungkinkan pembatalan transaksi dan mengembalikan nasabah ke antrean utama.

➋ Kendala dalam Alokasi Memori

   - 💡 **Masalah:**
     
      Karena menggunakan linked list, jika tidak dikelola dengan baik, memori bisa bocor (memory leak) akibat node yang tidak dibebaskan setelah digunakan.
     
   - ✅ **Solusi:**
     
      Menggunakan free() untuk menghapus node setelah nasabah dikeluarkan dari antrean atau stack.
      Menambahkan fungsi clearQueue() dan clearStack() untuk membersihkan semua node sebelum program berakhir.

➌ Menampilkan Riwayat dalam Urutan Kronologis

   - 💡 **Masalah:**
     
      Riwayat transaksi disimpan dalam stack yang bersifat LIFO (Last-In-First-Out), sehingga urutan tampil terbalik (terbaru ke terlama).
     
   - ✅ **Solusi:**
     
      Gunakan stack sementara untuk membalikkan urutan:
     
      1️⃣ Pindahkan semua data dari stack utama ke stack sementara.
     
      2️⃣ Tampilkan data dari stack sementara, yang kini dalam urutan kronologis.
     
      3️⃣ Kembalikan data ke stack utama agar tidak mengubah struktur aslinya.

➍ Sinkronisasi Antrean dan Riwayat

   - 💡 **Masalah:**
     
      Setelah undo, nomor antrean bisa menjadi tidak berurutan.
      Data harus tetap sinkron antara antrean (nasabah aktif) dan stack (riwayat layanan).
     
   - ✅ **Solusi:**
     
      Gunakan renumberQueue untuk memastikan nomor antrean tetap berurutan setelah perubahan.
      Saat nasabah diproses (deQueue), datanya dipindahkan ke stack. Jika undo dilakukan, data diambil dari stack dan dikembalikan ke antrean.

➎ Penanganan Kesalahan dan Stabilitas Program

   - 💡 **Masalah:**
     
      Program bisa mengalami gagal alokasi memori saat malloc tidak berhasil.
      Operasi yang tidak valid, seperti menghapus antrean kosong, bisa menyebabkan error.
     
   - ✅ **Solusi:**
     
      Cek hasil alokasi memori (malloc/strdup). Jika gagal, tampilkan pesan error agar pengguna tahu ada masalah.
      Cegah error kritis dengan:
     
      🔹 Menampilkan peringatan "Antrean kosong!" saat pengguna mencoba menghapus antrean yang sudah habis.
     
      🔹 Memeriksa kondisi isEmpty() sebelum melakukan operasi yang membutuhkan data, seperti menghapus antrean atau mengambil data dari stack.

➏ Validasi Input

   - 💡 **Masalah:**
     
      Input nama nasabah harus hanya berisi huruf dan spasi.
      Kesalahan input pada pilihan menu, seperti memasukkan huruf atau simbol yang tidak valid.
     
   - ✅ **Solusi:**
     
      Untuk mengatasi masalah ini, program menerapkan fungsi validasi khusus:
     
      o isValidName: Memeriksa nama hanya berisi huruf dan spasi menggunakan isalpha.
     
      o isValidNumber: Memastikan input angka menggunakan isdigit.
     
      o Membersihkan buffer input setelah memasukkan data agar tidak terjadi kesalahan saat membaca input berikutnya.

➐ Format Antarmuka Pengguna

   - 💡 **Masalah:**
     
      Menampilkan data antrean dan riwayat dalam format tabel yang rapi.
     
   - ✅ **Solusi:**
     
      Gunakan format printf dengan spesifikasi seperti %-4d (untuk nomor) dan %-50s (untuk nama) untuk merapikan kolom.
      Tambahkan garis pemisah (contoh: ===================) untuk kejelasan visual.
 
 ➑ Kendala dalam Efisiensi Kompilasi dan Eksekusi
 
   - 💡 **Masalah:**
     
      Setiap kali ingin menjalankan program, pengguna harus mengetik perintah kompilasi yang panjang secara manual.
     
   - ✅ **Solusi:**
     
     Menggunakan Makefile untuk mempermudah kompilasi hanya dengan menjalankan perintah make, lalu menjalankan program dengan
     ```sh
     ./mainSda
     ```
     ---

     ### 🛠️ Fitur Utama:

1️⃣ **Menambahkan Nasabah ke Antrean** 📥  
   - Nasabah dapat mendaftar dengan nama dan memilih jenis layanan (Setor Tunai, Tarik Tunai, Pembukaan Rekening).  
   
2️⃣ **Memproses Nasabah** 🔄  
   - Nasabah yang berada di antrean paling depan akan diproses dan dipindahkan ke **riwayat layanan**.  

3️⃣ **Menampilkan Antrean Saat Ini** 📋  
   - Menampilkan daftar nasabah yang masih dalam antrean.  

4️⃣ **Menampilkan Riwayat Layanan** 📜  
   - Menampilkan daftar nasabah yang sudah dilayani.  

5️⃣ **Batalkan Transaksi Terakhir (Undo)** ⏪  
   - Mengembalikan nasabah yang sudah diproses ke antrean.  

6️⃣ **Menyimpan Data ke File** 💾  
   - Antrean dan riwayat layanan dapat disimpan ke file (`antrean.txt` & `riwayat.txt`).  

7️⃣ **Memuat Data dari File** 📂  
   - Data antrean dan riwayat bisa dimuat kembali dari file untuk melanjutkan sesi sebelumnya.  

8️⃣ **Keluar dari Program** ❌  

---

### Alur Program 

![Screenshot 2025-03-10 131737](https://github.com/user-attachments/assets/83065517-f3a0-4dc9-b04b-34a6fdcbd652)






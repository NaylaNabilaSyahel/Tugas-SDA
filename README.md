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

### Deskripsi Program :spiral_notepad:
Program ini adalah sitem manajemen antrean nasabah di bank yang menggunakan queue berbasis linked list untuk mengelola antrean layanan, serta stack berbasis linked list untuk menyimpan riwayat transaksi nasabah yang telah di proses.

-------------------------------

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

- Jika ingin menghapus file eksekusi dan file `.o` untuk kompilasi ulang, gunakan perintah:  
  ```sh
  make clean
  ```
  📌 Perintah ini akan menghapus file yang dihasilkan dari kompilasi sebelumnya.
  
-------------------------------
      
### 🏦 Struktur Data yang Digunakan untuk Membangun Program Antrean Bank:

🔹 **Queue berbasis Linked List** 🔗
   - Program ini menggunakan **Queue berbasis Linked List** untuk menyimpan data antrean nasabah yang sedang menunggu untuk diproses.
   - Queue mengikuti prinsip **FIFO (First In, First Out)**, sehingga nasabah yang pertama masuk akan diproses lebih dahulu.

🔹 **Stack berbasis Linked List** 🔗
   - Selain antrean, program ini juga menggunakan **Stack berbasis Linked List** untuk menyimpan transaksi nasabah yang telah diproses.
   - Stack mengikuti prinsip **LIFO (Last In, First Out)**, sehingga transaksi terakhir yang diproses akan berada di bagian atas dan bisa dibatalkan jika diperlukan.
  
-------------------------------   

### 🤔 Alasan Pemilihan Struktur Data:

Queue dan Stack diimplementasikan menggunakan **Linked List** karena:

✅ **Fleksibel** – Tidak memiliki batasan ukuran seperti array, cocok untuk antrean yang jumlahnya tidak dapat diprediksi.
✅ **Efisien** dalam penambahan & penghapusan – Operasi enqueue, dequeue, push, dan pop dapat dilakukan dalam O(1) waktu tanpa perlu geser elemen seperti pada array.
✅ **Cocok untuk sistem antrean bank** – Karena jumlah nasabah yang antre bisa terus bertambah atau berkurang, sehingga penggunaan memori lebih efisien.
   
Struktur data **stack** dan **qeueu** dipilih diimplementasikan menggunakan linked list, sebab ukuran linked list tidak terbatas 
selama memori masih tersedia, hal ini sesuai sesuai dengan konsep antrean bank, karena banyaknya antrean dalam bank tidak dapat di tentukan sehingga akan sangat tidak efisien jiga diimplementasikan menggunakan array. Sehingga linked list menjadi solusi
yang sangat cocok dalam program ini.

-------------------------------

### Implementasi Struktur Data
1. Queueu berbasis linked list
   Dalam program antrean nasabah queue diimplementasikan untuk melakukan beberapa proses berikut:
   a. enqueu(); Menambahkan nasabah ke daftar antrean. Nasabah ditambahkan dari belakang sesuai dengan konsep antrian pada kehiudpan nyata
      sehingga proses pelayanan dilakukan teratur sesuai dengan urutan antrean nasabah.
   b. dequeu(); Menghapus nasabah dari antrean setelah selesai di proses. Penghapusan nasabah dilakukan dari depan sesuai dengan konsep inqueu, setelah dilakukan penghapusan nasabah, maka               nasabah yang berada di urutan sebelumnya akan di set untuk menajadi nasabah
      yang harus di proses berikutnya.
   c. tampilkanAntrian (); Menampilkan daftar antrian yang menunggu untuk dilayani.
      - Data antrian yang menunggu dilayani ditampilkan sesuai dengan daftar antrean nasabah,
        nasabah yang pertama masuk akan berada diurutan pertama antrean.
      - Antrean selalu diperbaharui, sehingga setelah satu nasabah selesai dilayani, nasabah berikutnya akan maju ke posisi paling depan.
      - Jika tidak ada nasabah dalam antrean, sistem akan menampilkan pesan "A ntrean kosong" dalam tabel. 

3. Stack berbasis linked list
   Dalam program antrean nasabah stack diimplementasikan untuk melakukan beberapa proses berikut:
   a. pop(); Menambahkan nasabah ke daftar riwayat layanan
      - ketika seorang nasabah telah selesai dilayani (dikeluarkan dari antrean queue), data nasabah tersebut akan dimasukkan
        ke dalam stack.
      - Penambahan dilakukan dari arah depan (top), sehinngga data nasabah terakhir yang siap dilayani akan selalu berada di posisi
        paling atas.
      - posisi top akan selalu di update ketika  proses penambahkan nasabah dilakukan.5r
   b. push() atau di program dinamakan undoTransaksi; Menghapus data nasabah dari riwayat layanan
      - Data nasabah yang terakhir masuk ke daftar riwayat layanan akan di hapus (dikemablikan lagi ke datar antrean).
      - Penghapusan dilakukan dari posisi top sehingga nasabah yang terakhir masuk akan di hapus  lebih dulu.
      - Nasabah yang dihapus dikembalikan lagi ke daftar antrean seperti sebelumnya, kembali menjadi top dalam daftar antrean.
   c. tampilkanRiwayat(); Menampilkan riwayat nasabah yang telah selesai di proses
      - setiap nasabah yang telah selesai diproses akan dipindahkan ke dalam riwayat layanan yang ditampilkan dalam urutan
        yang sesuai dengan wkatu pelayanan.
      - Nasabah yang pertama diproses akan ditampilkan lebih dahulu, karena riwayat layanan ini disusun agar mudah dibaca dalam urutan     
        yang benar.
      - Data riwayat tetap disimpan meskipun antrean utama terus berjalan, sehingga dapat digunakan untuk melihat daftra layanan yang
        sudah dilakukan.
      - Jika tidak ada nasabah yang telah dilayani sistem akan menampilkan pesan " Riwayat kosong" dalam tabel.

-------------------------------
        
### Fitur Utama:

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



## Tutorial 8
Nama: Syifa Kaffa Billah

NPM: 2206816430

Kelas: C

**1. What is AMQP?**

AMQP (Advanced Message Queuing Protocol) merupakan sebuah protokal aplikasi tingkat tinggi yang digunakan untuk pertukaran pesan antara aplikasi dan layanan berbasis antrian (message queue).
Protokol ini mengatur aturan dan format untuk pertukaran pesan antara sistem yang berbeda, memungkinkan komunikasi yang andal dan efisien antara aplikasi perangkat lunak yang berbeda,
ditulis dalam bahasa pemrograman yang berbeda, dan berjalan pada platform yang berbeda. Ini memudahkan integrasi antara sistem-sistem yang berbeda dalam lingkungan teknologi yang heterogen.


**2. What it means? guest:guest@localhost:5672 , what is the first quest, and what is the second guest, and what is localhost:5672 is for?**

"guest:guest@localhost:5672" adalah sebuah string atau url yang digunakan untuk mengakses sebuah layanan menggunakan protokol AMQP.
String tersebut terdiri dari dua bagian, yaitu:
- guest:guest ==> Bagian pertama "guest" adalah username atau nama pengguna yang digunakan untuk mengautentikasi ke layanan AMQP. Bagian kedua "guest" adalah password yang sesuai dengan username.
- "localhost:5672" ==> alamat atau host yang menunjukkan lokasi dari layanan AMQP yang ingin diakses, di sini "localhost" mengacu pada komputer lokal tempat layanan AMQP dijalankan,
  dan "5672" adalah nomor port yang digunakan oleh layanan AMQP untuk menerima koneksi.

Jadi, string ini digunakan untuk mengidentifikasi pengguna (username dan password) dan lokasi layanan AMQP yang akan diakses.

**Simulation slow subscriber**
![img1.png](image%2Fimg1.png)

Dari gambar di atas, bisa dilihat bahwa jumlah total message dalam antran pada satu waktu sebanyak +-20 message
(saya menjalankan 6 kali cargo run). Hal ini terjadi karena subscriber memerlukan lebih banyak waktu untuk mengelola
setiap event dalam message queued, sehingga terjadi penumpukan pesan karena publisher lebih cepat dalam mempublish
pesan daripada subscriber dalam mengolahnya.

**Reflection and Running at least three subscribers**
![img2.png](image%2Fimg2.png)

Dari gambar di atas, bisa dilihat bahwa lonjakan message queued berkurang dari yang sebelum menggunakan 3 console 
subscriber (Kasus ini sama-sama dilakukan dengan melakukan 6 kali cargo run pada publisher). Hal ini terjadi karena
karena file main.rs pada subscriber terdapat fungsi sleep (thread::sleep(ten_millis);) yang membuat adanya penundaan 
selama 1 detik (1000 milidetik) sebelum mencetak pesan. Karena adanya penundaan tersebut, program diberikan lebih 
banyak waktu untuk memproses pesan secara berurutan, sehinnga penumpukan antrean menjadi berkurang. Selain itu,
penggunaan 3 console subsriber yang menjalankan cargo run secara bersamaan juga bisa menjadi salah satu penyabab adanya
pengurangan lonjakan tersebut. 

Saran perbaikan kode:
- Pengolahan Asynchronous: Secara umum pada kode program, Publisher mengirimkan pesan secara sinkron . Jika kecepatan 
menjadi perhatian utama, mengubah pengiriman pesan menjadi asinkronus bisa memberikan benefit. Dengan pengiriman 
asinkronus, publisher dapat melanjutkan tugasnya tanpa menunggu konfirmasi pesan selesai dikirim, yang dapat 
meningkatkan efisiensi.




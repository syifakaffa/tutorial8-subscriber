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

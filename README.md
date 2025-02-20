## TUGAS WORKSHOP ADMINISTRASI JARINGAN 

| Nama         | **Kansa Adeneva**                  |
|-------------|----------------------------------|
| NRP          | **3123600009**                     |
| Mata Kuliah  | **Workshop Administrasi Jaringan** |
| Dosen        | **Dr Ferry Astika Saputra ST, M.Sc** |



## TUGAS 1 REVIEW
  1. Download http.cap di https://wiki.wireshark.org/SampleCaptures

       Hasil Download:
       ![download http.cap](https://github.com/Kansaadeneva/AdminJaringan2025/blob/682c5d1cd44fcd3779a622d5ae407769afac5a53/Screenshot%202025-02-20%20190906.png)

     
  3. Eksplor http.cap di wireshark, lakukan analisis

     a. IP server dan client
      IP client = 145.254.160.237 :
      ![ip client](https://github.com/Kansaadeneva/AdminJaringan2025/blob/d4bf49b0a960fd9ab06b7c78fb5e57bb15eee6aa/Screenshot%202025-02-20%20202627.png)

      IP server = 65.208.228.223 :
      ![ip server](https://github.com/Kansaadeneva/AdminJaringan2025/blob/d4bf49b0a960fd9ab06b7c78fb5e57bb15eee6aa/Screenshot%202025-02-20%20202627.png)
     
     b. Versi HTTP

      Versi HTTP yang digunakan adalah HTTP/1.1 :
      ![Versi HTTP](https://github.com/Kansaadeneva/AdminJaringan2025/blob/c4d9edd1ac2e88e85067e7504ed0023f972f741e/Screenshot%202025-02-20%20192522.png)
     
     c. Waktu client mengirim request

      Ip client 145.254.160.237 mengirim ke server request GET /download.html adalah 0.911310 detik,
      ![waktu client mengirim req](https://github.com/Kansaadeneva/AdminJaringan2025/blob/acdbb602011e950d6a477dc147d655c4b422397f/Screenshot%202025-02-20%20193011.png)
     
     d. Waktu server menerima HTTP request dari client

      Server 65.208.228.223 mengirim HTTP/1.1 200 OK pada waktu 4.846969 detik,
      ![waktu server menerima req](https://github.com/Kansaadeneva/AdminJaringan2025/blob/75efbece904d4da8dae9a5edbb37ec1d4b246bdf/Screenshot%202025-02-20%20193021.png)
     
     e. Waktu yang dibutuhkan untuk transfer dan response dari client ke server

      Waktu yang dibutuhkan untuk transfer dan response dari client ke server sekitar 3.94 detik,
      4.846969 - 0.911310 = 3.935659 detik


## TUGAS 2 ANALISIS GAMBAR

![Analisis Comunication Protocol](https://github.com/Kansaadeneva/AdminJaringan2025/blob/abc47dd73f1e5b9af0ec48c0361e86d02d21a1f6/Screenshot%202025-02-20%20204512.png)

  Gambar ini menggambarkan proses komunikasi data dalam jaringan komputer menggunakan tiga lapisan utama:
  1. Data Link Layer (Node to Node) : yang menangani komunikasi antara komputer ke router, router ke router lain, dan seterusnya.
  2. Network Layer (Host to Host) : Layer ini untuk internet protokol yang menghubungkan jaringan berbeda di internet.
  3. Transport Layer (Process to Process) : Layer ini menangani komunikasi antara proses di komputer client dan server.

Proses yang terjadi didalam gambar:
  1. Pengguna di komputer pengirim (server) memulai proses komunikasi (misalnya, mengakses situs web atau mengirim file).
  2. Data dikemas dan dikirim melalui internet, melewati beberapa node (router).
  3. Setiap router bertindak sebagai perantara, meneruskan paket ke tujuan berdasarkan alamat ip.
  4. Di komputer penerima (client), data diterima dan diproses oleh aplikasi yang dituju, misalnya browser web atau aplikasi lainnya.

  Gambar ini menunjukkan bagaimana data dikirim dalam jaringan dari node ke node (Data Link Layer), dari host ke host (Network Layer), dan dari proses ke proses (Transport Layer), yang merupakan dasar dari komunikasi jaringan modern.


## TUGAS 3 RESUME
![TCP](https://github.com/Kansaadeneva/AdminJaringan2025/blob/f18c3f04e7126cb94fae67d315c0c3328f9c87eb/Screenshot%202025-02-20%20213333.png)
  Transmission Control Protocol (TCP) adalah protokol komunikasi yang memungkinkan pengiriman data yang terjamin dan terurut antar perangkat dalam jaringan. TCP menggunakan tiga tahapan utama untuk mengelola koneksi, yaitu establishment, data transfer, dan termination.
  1. Establishment (Pembentukan Koneksi)
     ![Connection establishment using three-way handshaking](https://github.com/Kansaadeneva/AdminJaringan2025/blob/39042cc30c91f9f167e96f7871fbe261085c1614/Screenshot%202025-02-20%20225934.png)
     Tahap ini melibatkan proses yang dikenal sebagai three-way handshake untuk membangun koneksi antara dua perangkat (client dengan server).
     - Langkah 1: SYN (Synchronize)
         Pengirim mengirimkan pesan SYN ke penerima untuk memulai koneksi.
     - Langkah 2: SYN-ACK (Synchronize-Acknowledge)
         Penerima merespons dengan SYN-ACK untuk mengkonfirmasi permintaan koneksi.
     - Langkah 3: ACK (Acknowledge)
         Pengirim mengirimkan ACK sebagai tanda akhir proses handshake, dan koneksi siap digunakan.
       
  2. Data transfer
     ![Data transfer](https://github.com/Kansaadeneva/AdminJaringan2025/blob/b6a8aa593097fadf73cbd011ab40c3ebce92dc4f/Screenshot%202025-02-20%20230208.png)
     Setelah koneksi terbentuk, data dikirim secara berurutan dengan nomor urut (sequence number). TCP memastikan kendala dan pengurutan data melalui mekanisme berikut:
     - Segmentation, data dibagi menjadi segmen-segmen yang dikirim secara terurut.
     - Acknowledgement, penerima mengirimkan ACK untuk setiap segmen yang berhasil diterima.
     - Flow Control, TCP mengontrol aliran data untuk memastikan pengiriman berjalan efisiensi dan tidak membebani jaringan.
     - Error Detection and Retransmission, jika segmen hilang atau rusak, TCP akan mengirim ulang segmen tersebut.
       
  3. Termination (Pemutusan koneksi)
     ![Connection termination using three-way handshaking](https://github.com/Kansaadeneva/AdminJaringan2025/blob/d5093d127edeb93e4ba2bb2365167711c97e3c95/Screenshot%202025-02-20%20230439.png)
     Tahap ini digunakan untuk menutup koneksi TCP dengan aman. Gambar tersebut menunjukkan terminasi koneksi TCP menggunakan three-way handshake, yang melibatkan pertukaran segmen antara klien dengan server untuk menutup koneksi secara bersih.
     - FIN dari Client (Active Close)
       Client yang ingin mengakhiri koneksi mengirim segmen dengan:
         - Flag FIN (Finish) menyatakan bahwa client tidak akan mengirim data lagi.
         - Sequence Number (seq:x) menentukan nomor urutan paket terakhir.
         - Acknowledgement Number (ack: y) mengakui paket terakhir yang diterima dari server.
     - FIN + ACK dari Server (Passive Close)
         - Flag ACK, mengkonfirmasi penerima FIN dari client.
         - Flag FIN, menyatakan bahwa server juga ingin mengakhiri koneksi.
         - Sequence Number (seq:y) mengirim nomor urutnya sendiri.
         - Acknowledgement Number (ack: x + 1) mengakui paket terakhir client.
     - ACK dari Client
       Client menerima segmen FIN dari server dan mengirim ACK terakhir untuk mengkonfirmasi penutupan koneksi:
         - Flag ACK, mengkonfirmasi FIN dari server.
         - Sequence Number (seq:x).
         - Acknowledgement Number (ack:y + 1).

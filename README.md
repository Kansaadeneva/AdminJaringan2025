### TUGAS WORKSHOP ADMINISTRASI JARINGAN 

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

  Gambar ini menggambarkan proses komunikasi data dalam jaringan komputer menggunakan tiga lapisan utama:
  1. Data Link Layer (Node to Node) : yang menangani komunikasi antara komputer ke router, router ke router lain, dan seterusnya.
  2. Network Layer (Host to Host) : Layer ini untuk internet protokol yang menghubungkan jaringan berbeda di internet.
  3. Transport Layer (Process to Process) : Layer ini menangani komunikasi antara proses di komputer client dan server.

# Proses yang terjadi didalam gambar:
  1. Pengguna di komputer pengirim (server) memulai proses komunikasi (misalnya, mengakses situs web atau mengirim file).
  2. Data dikemas dan dikirim melalui internet, melewati beberapa node (router).
  3. Setiap router bertindak sebagai perantara, meneruskan paket ke tujuan berdasarkan alamat ip.
  4. Di komputer penerima (client), data diterima dan diproses oleh aplikasi yang dituju, misalnya browser web atau aplikasi lainnya.

  Gambar ini menunjukkan bagaimana data dikirim dalam jaringan dari node ke node (Data Link Layer), dari host ke host (Network Layer), dan dari proses ke proses (Transport Layer), yang merupakan dasar dari komunikasi jaringan modern.


## TUGAS 3 RESUME

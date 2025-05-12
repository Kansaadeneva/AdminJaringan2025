## TUGAS MERESUME

Nama  : Kansa Adeneva
NRP   : 3123600009
Kelas : 2 D4 IT A

### 1. Protokol Mail (SMTP, POP3, IMAP, POPS)

#### a. SMTP
- **Definisi:**  
  SMTP (Simple Mail Transfer Protocol) adalah protokol komunikasi yang digunakan untuk mengirim dan menerima pesan email melalui internet.

- **Cara Kerja SMTP:**  
  Dalam model SMTP, klien email pengirim atau server bertindak sebagai klien SMTP yang menghubungi server SMTP penerima untuk mengirim email...

- **Kelebihan SMTP:**
  1. Lebih Efisien dan Praktis  
  2. Lebih Aman  
  3. Lebih Cepat

- **Kekurangan SMTP:**
  1. Berpotensi Adanya Pemalsuan Identitas
 

#### b. POP3
- **Definisi:**

  Post Office Protocol 3, atau POP3, adalah protokol yang paling umum digunakan untuk menerima email melalui internet. Protokol standar ini, yang didukung oleh sebagian besar server email dan kliennya, digunakan untuk menerima email dari server jarak jauh dan mengirimkannya ke klien lokal.

  POP3 adalah protokol klien-server satu arah di mana email diterima dan disimpan di server email. "3" mengacu pada versi ketiga dari protokol POP asli.

  Penerima atau klien email mereka dapat mengunduh email secara berkala dari server menggunakan POP3. Dengan demikian, POP3 menawarkan sarana untuk mengunduh email dari server ke klien sehingga penerima dapat melihat email tersebut secara offline. POP3 dapat dianggap sebagai layanan "simpan dan teruskan".

  Setelah email ada di klien, POP3 kemudian menghapusnya dari server. Pada beberapa implementasi, pengguna atau administrator dapat menentukan bahwa email disimpan selama beberapa waktu, yang memungkinkan pengguna mengunduh email sebanyak yang mereka inginkan dalam jangka waktu yang ditentukan.

- **Cara Kerja POP3:**  

  Server memulai layanan POP3 dengan mendengarkan pada port TCP 110. Ketika klien ingin menggunakan POP3 untuk pengambilan email, klien akan membuat koneksi TCP dengan host server. Setelah koneksi ini dibuat, server POP3 akan mengirimkan ucapan. Pada titik ini, sesi memasuki status otorisasi .

  Dalam status transaksi berikutnya, klien dan server bertukar perintah dan respons hingga koneksi ditutup atau dibatalkan. Perintah dari klien terdiri dari kata kunci yang tidak peka huruf besar/kecil, mungkin diikuti oleh argumen. Respons dari server terdiri dari indikator status dan kata kunci, yang mungkin diikuti oleh informasi tambahan.

  Saat klien mengeluarkan perintah quit , sesi memasuki status pembaruan . Server POP3 melepaskan semua sumber daya yang diperoleh selama status transaksi , dan mengucapkan "selamat tinggal," yang merupakan saat koneksi TCP ditutup.

Setelah sesi POP3 memasuki status pembaruan , server POP3 menghapus pesan tersebut.
- **Kelebihan SMTP:**
  1. Mudah diatur
  2. Akses offline
  3. Akses cepat
  4. Keamanan yang lebih tinggi
  5. Menghemat ruang server

- **Kekurangan SMTP:**
  1. Hanya untuk satu perangkat
  2. Tidak ada sinkronisasi
  3. Bergantung pada penyimpanan lokal
  4. Risiko email hilang
  5. Pengelolaan email terbatas


#### c. IMAP
- **Definisi:**  
  IMAP adalah singkatan dari Internet Message Access Protocol, yaitu protokol email standar yang berfungsi untuk mengakses dan mengelola email secara langsung di server email.

  Protokol ini menyimpan pesan di server sehingga Anda bisa melihat dan mengelolanya dari beberapa perangkat sekaligus.

  Artinya, perubahan yang dibuat di satu perangkat bisa dilihat di semua perangkat lainnya sehingga Anda bisa mengakses email di mana saja secara tersinkron.

- **Cara Kerja SMTP:**
  IMAP bekerja dengan menghubungkan mail client Anda ke server email. Ketika Anda mengecek pesan, mail client akan menghubungi server IMAP dan mengambil data yang diperlukan untuk menampilkan pesan tersebut.

  Email akan tetap tersimpan di server remote sehingga Anda bisa mengakses dan mengelolanya dari berbagai lokasi, seperti laptop, HP, dan tablet, tanpa harus mendownloadnya secara permanen. Selain itu, IMAP memastikan bahwa kotak masuk Anda selalu diperbarui, di mana pun Anda mengaksesnya.

  Dibandingkan dengan POP3 yang mendownload dan sering menghapus email dari server sehingga membatasi akses Anda pada satu perangkat, IMAP jauh lebih fleksibel untuk mengelola email kalau Anda sehari-harinya bekerja menggunakan lebih dari satu perangkat.
  
- **Kelebihan SMTP:**
  1. Sinkronisasi
  2. Akses real-time 
  3. Fitur-fitur canggih
  4. Penyimpanan server
  5. Keamanan data

- **Kekurangan SMTP:**
  1. Harus tersambung ke internet
  2. Potensi latensi
  3. Penggunaan resource yang lebih tinggi
  4. Setup yang rumi
  5. Batas penyimpanan
 

#### d. POP3S
- **Definisi:**  
  POP3S adalah POP3 (Post Office Protocol version 3) over SSL/TLS, yaitu versi aman dari protokol POP3 yang digunakan untuk mengambil email dari server ke perangkat pengguna.

- **Cara Kerja SMTP:**
1. Inisialisasi Koneksi Aman
   Email client (seperti Thunderbird atau Outlook) memulai koneksi ke server email menggunakan port 995, yaitu port standar untuk POP3S.

   Koneksi langsung dienkripsi menggunakan SSL/TLS agar data yang ditransmisikan tidak bisa disadap.

2. Otentikasi Pengguna
   Setelah koneksi aman terjalin, client mengirimkan username dan password untuk login ke server.
   Karena sudah dienkripsi, data login tetap aman meskipun lewat jaringan publik.

3. Mengunduh Email
   Setelah berhasil login, email client akan mengirimkan permintaan untuk mengunduh email dari server.
   Semua email dalam kotak masuk akan diunduh dan disimpan lokal di perangkat pengguna.

4. Menghapus atau Menyimpan di Server (opsional)
   Secara default, setelah email diunduh, server menghapus salinan email dari kotak masuk.
   Namun, pengguna bisa mengatur client untuk tetap menyimpan salinan email di server.

5. Menutup Koneksi
   Setelah proses selesai, koneksi antara client dan server ditutup secara aman.

- **Kelebihan SMTP:**
  1. Keamanan tinggi berkat enkripsi data.
  2. Privasi terjaga, mencegah penyadapan saat pengambilan email.
  3. Cocok untuk penggunaan offline karena email disimpan di perangkat.

- **Kekurangan SMTP:**
  1. Tidak sinkron antar perangkat—email hanya ada di perangkat yang mengunduh.
  2. Risiko kehilangan data jika perangkat rusak, kecuali ada backup.
  3. Kurang fleksibel dibanding protokol IMAP.
 





### 2. Informasi mail server dalam sebuah domain
  -**Definisi**
  Mail server adalah server yang bertugas menerima, menyimpan, dan mengirimkan email untuk suatu domain, contohnya: example.com.

  Informasi mail server ini disimpan dalam DNS record jenis MX (Mail Exchange) dari domain tersebut.

  -**Komponen Penting Mail Server dalam Domain**
  1. MX Record (Mail Exchange Record)

  Menentukan nama server yang menerima email untuk domain tersebut.

  Bisa lebih dari satu, dengan prioritas berbeda (semakin kecil angka prioritas, semakin tinggi prioritasnya).

  Contoh:
  ```bash
  example.com.  IN  MX 10 mail1.example.com.
  example.com.  IN  MX 20 mail2.backup.com.
  ```

  2. A Record / CNAME
    MX Record menunjuk ke nama domain (mail1.example.com), dan nama ini harus punya A record (alamat IP) atau CNAME (alias).

  3. SPF (Sender Policy Framework)
    Menentukan server mana saja yang diizinkan untuk mengirim email atas nama domain tersebut.
    Didefinisikan dalam TXT record di DNS.

  4. DKIM (DomainKeys Identified Mail)
    Digunakan untuk menandatangani email agar tidak bisa dimodifikasi dalam perjalanan.
    Disimpan sebagai TXT record.

  5. DMARC (Domain-based Message Authentication, Reporting, and Conformance)
    Mengatur kebijakan dan laporan untuk email yang gagal SPF atau DKIM.

- **Contoh Nyata (menggunakan nslookup atau dig)**
Jika kamu ingin mengetahui informasi mail server untuk domain tertentu, kamu bisa pakai perintah seperti:

```bash
Copy code
nslookup -type=MX gmail.com
```

Atau dengan dig:

```bash
Copy code
dig MX gmail.com
```

Output-nya akan menunjukkan mail server seperti:

```bash
gmail.com.  IN  MX 5 gmail-smtp-in.l.google.com.
```



### 3. Message Transfer Agent (MTA) pada https://www.geeksforgeeks.org/introduction-to-electronic-mail/

~gambar

1. Pengguna dan Komponen Utama
  User A dan User B adalah dua orang yang saling berkirim email.
  Keduanya menggunakan UA (User Agent) seperti Gmail, Outlook, Thunderbird, dll., untuk menulis, mengirim, dan membaca email.

2. Alur Pengiriman Email (Dari User A ke User B)
    a. User A menulis email di aplikasi email-nya (UA - User Agent).

    b. Email dikirim ke dua tempat:
  Spool: Tempat antrean email yang akan dikirim.
  Mail-Boxes: Tempat menyimpan salinan pesan keluar (sent items).

    c. Email diteruskan ke Alias Expander:
  Ini adalah sistem yang menerjemahkan alamat email alias menjadi alamat asli jika perlu (misalnya admin@domain.com jadi user1@domain.com).

    d. Email masuk ke MTA (Mail Transfer Agent):
  Ini seperti “kantor pos digital” yang mengatur pengiriman email antar server.
  MTA pertama bertindak sebagai client, lalu menghubungi MTA penerima (server).

    e. Email dikirim melalui Internet ke MTA milik User B.

3. Alur Penerimaan Email (Ke User B)
    a. Email diterima oleh MTA (server) milik User B.

    b. Melewati Alias Expander User B untuk cek apakah alamatnya perlu diterjemahkan.

    c. Email disimpan di Mail-Boxes User B.

    d. Spool akan mengantarkan email dari server ke aplikasi email milik User B (UA).
  
    e. User B membuka aplikasi email-nya dan membaca pesan dari User A.

4. Penjelasan Tambahan Komponen:

| Komponen       | Fungsi                                                                 |
|----------------|------------------------------------------------------------------------|
| UA (User Agent)| Aplikasi email untuk kirim/terima pesan.                               |
| Spool          | Tempat antrean email sementara (sebelum dikirim/diambil).              |
| Mail-Boxes     | Tempat penyimpanan email (inbox/outbox).                               |
| Alias Expander | Menerjemahkan alamat email jika menggunakan alias.                     |
| MTA            | Mail Transfer Agent, agen pengirim/penyampai email antar server.       |
| Database       | Tempat menyimpan informasi pengguna, konfigurasi, dan lainnya.         |


5.  Kesimpulan Sederhana:
  Email dikirim oleh pengguna lewat aplikasi email, diproses oleh beberapa komponen seperti antrian (spool), penerjemah alamat (alias), dan dikirim oleh "kantor pos" digital (MTA) ke server penerima melalui internet. Server penerima lalu menyimpan dan menyerahkan email itu ke pengguna tujuan.





# Mail Server
### Kelompok 3
------------------------------------------------------------

## A. Install Postfix
  1. Konfigurasi SMTP-Auth untuk menggunakan fungsi SASL Dovecot
     ```bash
     su -
     apt -y install postfix sasl2-bin
     ```
     # pada contoh gambar dibawah, lanjutkan dengan memilih [No Configuration (Tanpa Konfigurasi)]
     # karena mengkonfigurasi semua secara manual
     //gambar postfix
     
  3. Menyalin file template default konfigurasi (main.cf.dist) ke lokasi konfigurasi aktif (main.cf) agar bisa menjalankan Postfix.
     ```bash
     cp /usr/share/postfix/main.cf.dist /etc/postfix/main.cf
     ``` 
  4. Masuk dan Ubah yg ada di file (/etc/postfix/main.cf)
     ```bash
     nano /etc/postfix/main.cf
     ```
     
     #line 82 : uncoment
     mail_owner = postfix

     #line 98 : uncoment and spicify histname
     myhostname = mail.srv.world

     #line 106 : uncoment and specify domainname
     mydomain = srv.world

     #line 127 : uncomment
     myorigin = $mydomain

     #line 189 : uncomment
     mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

     #line 232 : uncomment
     local_recipient_maps = unix:passwd.byname $alias_maps

     #line 277 : uncomment
     mynetworks_style = subnet

     #line 294 : add your local network
     mynetworks = 127.0.0.0/8, 10.0.0.0/24

     #line 416 : uncomment
     alias_maps = hash:/etc/aliases

     #line 427 : uncomment
     alias_database = hash:/etc/aliases

     #line 449 : uncomment
     home_mailbox = Maildir/

     #line 585: comment out and add
     #smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
     smtpd_banner = $myhostname ESMTP

     #line 659 : add
     sendmail_path = /usr/sbin/postfix

     #line 664 : add
     newaliases_path = /usr/bin/newaliases

     #line 669 : add
     mailq_path = /usr/bin/mailq

     #line 675 : add
     setgid_group = postdrop

     #line 679 : comment out
     #html_directory =

     #line 683 : comment out
     #manpage_directory =
  
     #line 688 : comment out
     #sample_directory =

     #line 692 : comment out
     #readme_directory =

     #line 692 : if also listen IPv6, change to [all]
     inet_protocols = ipv4

     #add follows to last line
     #disable SMTP VRFY command
     disable_vrfy_command = yes

     #require HELO command to sender hosts
     smtpd_helo_required = yes
      
     #limit an email size
     #example below means 10M bytes limit
     message_size_limit = 10240000
      
     #SMTP-Auth settings
     smtpd_sasl_type = dovecot
     smtpd_sasl_path = private/auth
     smtpd_sasl_auth_enable = yes
     smtpd_sasl_security_options = noanonymous
     smtpd_sasl_local_domain = $myhostname
     smtpd_recipient_restrictions = 
       permit_mynetworks,
       permit_sasl_authenticated,
       reject_unauth_destination
             
  5. Perbarui database alias email yg digunakan oleh Postfix
     ```bash
     newaliases
     ```
     
  6. Restart layanan Postfix pada sistem debian
     ```bash
     systemctl restart postfix
     ```
     
  7. Ubah dan tambahkan pada file /etc/postfix/main.cf
     ```bash
     nano /etc/postfix/main.cf
     ```

     #add to the end
     #reject unknown clients that forward lookup and reverse lookup of their hostnames on DNS do not match
     smtpd_client_restrictions = permit_mynetworks, reject_unknown_client_hostname, permit

     #rejects senders that domain name set in FROM are not registered in DNS or 
     #not registered with FQDN
     smtpd_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_non_fqdn_sender
      
     #reject hosts that domain name set in FROM are not registered in DNS or 
     #not registered with FQDN when your SMTP server receives HELO command
     smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, reject_non_fqdn_hostname, reject_invalid_hostname, permit
           
       
  8. Restart layanan Postfix pada sistem debian
     ```bash
     systemctl restart postfix
     ```
     
## B. Install Devecot
  1. Konfigurasi untuk menyediakan fungsi SASL ke Postfix.
     Install dovecot
       ```bash
       apt -y install dovecot-core dovecot-pop3d dovecot-imapd
       ```

     Ubah dan tambahkan di file (/etc/dovecot/dovecot.conf)
     ```bash
     nano /etc/dovecot/dovecot.conf
     ```

     # line 30 : uncomment
     listen = *, ::
     root@mail:~# vi /etc/dovecot/conf.d/10-auth.conf
     #line 10 : uncomment and change (allow plain text auth)
     disable_plaintext_auth = no
     #line 100 : add
     auth_mechanisms = plain login

     Ubah dan tambahkan di file (/etc/dovecot/conf.d/10-master.conf)
     ```bash
     nano /etc/dovecot/conf.d/10-master.conf
     ```

     #line 107-109 : uncomment and add
     #Postfix smtp-auth
     unix_listener /var/spool/postfix/private/auth {
       mode = 0666
       user = postfix
       group = postfix
     }

     Restart devecot
     ```bash
     systemctl restart dovecot
     ```

## C. Mail Server : Add Mail User Accounts
  1. Untuk menggunakan akun pengguna OS, itu hanya menambahkan pengguna OS seperti berikut.
     #install mail client
     ```bash
     apt -y install mailutils
     ```

     #set environment variables to use Maildir
     ```bash
     echo 'export MAIL=$HOME/Maildir/' >> /etc/profile.d/mail.sh
     ```
     
     #add an OS user [debian]
     ```bash
     adduser kelompok3
     ```

  2. Login sebagai pengguna yang ditambahkan di [1] dan coba kirim email.
     #send to myself [mail (username)@(hostname)]
     ```bash
     mail kelompok3@localhost
     ```
     
     #input Cc
     Cc:
     #input subject
     Subject: Test Mail #1
     #input messages
     This is the first mail.

     #to finish messages, push [Ctrl + D] key

     #see received emails
     ```bash
     mail
     ```
     output:  
     "/home/debian/Maildir/": 1 message 1 new
     >N   1 debian             Fri Jul  7 05:35  13/448   Test Mail #1

     #input the number you'd like to see an email
     ? 1
     Return-Path: <debian@mail.srv.world>
     X-Original-To: debian@localhost
     Delivered-To: debian@localhost
     Received: by mail.srv.world (Postfix, from userid 1000)
              id 35D44A03A6; Fri,  7 Jul 2023 00:35:17 -0500 (CDT)
     To: <debian@localhost>
     Subject: Test Mail #1
     User-Agent: mail (GNU Mailutils 3.15)
     Date: Fri,  7 Jul 2023 00:35:17 -0500
     Message-Id: <20230707053517.35D44A03A6@mail.srv.world>
     From: debian <debian@mail.srv.world>

      This is the first mail.

      #to quit, input [q]
      ? q
      Saved 1 message in /home/debian/mbox
      Held 0 messages in /home/debian/Maildir/**

## D. Fix Mail Server to Client
     
     
       


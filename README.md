
|    NRP     |      Name      |
| :--------: | :------------: |
| 5025241177 | Hosea Felix Sanjaya |

## Problem 1.1

> Terdapat 2 personal computer (pc) dengan nama netics-pc-1 dan netics-pc-2

> Sambungkan 2 pc tersebut agar bisa digunakan untuk berkomunikasi data

### Task

> Buat sambungan jaringan antara netics-pc-1 dan netics-pc-2

> Sambungkan melalui interface eth0 di netics-pc-1

> Sambungkan melalui interface eth0 di netics-pc-2

<img width="351" height="119" alt="image" src="https://github.com/user-attachments/assets/e01127f3-7a21-45e8-a8f3-3fa70a368f27" />


  `@netics-pc-1 : ip addr add 192.168.100.101/255.255.255.0 dev eth0`

  <img width="576" height="120" alt="image" src="https://github.com/user-attachments/assets/2c940e2c-a12a-4f9d-8c10-e613e28f499f" />


  `@netics-pc-2 : ip addr add 192.168.100.102/255.255.255.0 dev eth0`

  <img width="575" height="148" alt="image" src="https://github.com/user-attachments/assets/6b04dbb4-240f-4736-875d-02a9e9b4353b" />


  `kita lakukan ping untuk mengaitkan pc-1 dengan pc-2`

  <img width="572" height="379" alt="image" src="https://github.com/user-attachments/assets/705ad7c1-e99f-4e54-b3e9-ebd19eaffd24" />
  
  <img width="573" height="381" alt="image" src="https://github.com/user-attachments/assets/2a31539d-29ce-4c5b-a0a8-503ac5cca199" />


<br>
<br>


## Problem 1.2

> Bagaimana mengetahui kapasitas link penghubung 

> Bagaimana kapasitas transfer netics-pc-1 dan netics-pc-2 ?
  

<img width="574" height="384" alt="image" src="https://github.com/user-attachments/assets/3529a47b-0596-48a5-91d1-31f53ba73e09" />

`Ketik ethtool eth0 pada pc-1 untuk cek kapasitas`
<br>
`Ada 10Gbps`

<img width="573" height="383" alt="image" src="https://github.com/user-attachments/assets/281df50d-20fc-4b62-b6f1-92120d15a06c" />

`ctrl+c lalu clear untuk membersihkan tampilan terminal`
<br>
`Di pc-1 ketik iperf3 -s untuk menjalankan sebagai server`

<img width="573" height="385" alt="image" src="https://github.com/user-attachments/assets/15a63e93-82b0-431a-b2ea-b0d053bda280" />

`Di pc-2 ketik iperf3 -c 192.168.100.101 -u -b 10G untuk memulai test`

`Laporan menunjukan kapasitas yang bisa dicapai oleh interface eth0 untuk transfer data hanya 930Mbps (sender) dan 168Mbps (receiver)`


  <br>
  <br>


## Problem 1.3

> Bagaimana menghubungkan netics-pc-1 dan netics-pc-2 dengan ethernet bridge

> Bagaimana mensimulasikan pembatasan troughput antara netics-pc-1 dan netics-pc-2 


- Filter expression

  `http`

- Explanation

  `terlihat packet displayed : 298`

- Output result

  <img width="964" height="799" alt="image" src="https://github.com/user-attachments/assets/72d77a64-c786-4ace-8bc7-05edaa989fe4" />


  <br>
  <br>

> b. Ada berapa HTTP packet yang berupa response?

> _b. How many response HTTP packets are recorded in the traffic?_

**Answer:** `149`

- Filter expression

  `http.response`

- Explanation

  `untuk mencari response pada http maka pakai http.response`

- Output result

  <img width="959" height="804" alt="image" src="https://github.com/user-attachments/assets/5207376a-9ce9-4d47-9a00-3966143febd7" />

  <br>
  <br>

> c. Ada berapa paket berbasis HTTP yang berhasil?

> _c. How many HTTP packets that succeed?_

**Answer:** `296`

- Filter expression

  `http` -2 atau

  `http && !(tcp.analysis.lost_segment || tcp.analysis.ack_lost_segment || tcp.analysis.retransmission || tcp.analysis.duplicate_ack || tcp.analysis.out_of_order)`

- Explanation

  `bisa pakai http saja tapi nanti cari data yang berwarna hitam dan kurngkan saja, atau pakai cara ke dua dengan menegasikan semua kemungkinan file hitamm`

- Output result

  <img width="960" height="798" alt="image" src="https://github.com/user-attachments/assets/e12cf2de-08f0-47f2-98e2-a297a056b67f" />


  <br>
  <br>

> d. Apa alamat IP dari client HTTP yang tersambung lokal dengan mesin lain?

> _d. What is the client HTTP IP Address in connection with other local machine?_

**Answer:** `172.16.16.101`

- Filter expression

  `http`

- Explanation

  `Ada di barisan source terlihat semua ip dari http sama yaitu : 172.16.16.101`

- Output result

  <img width="958" height="798" alt="image" src="https://github.com/user-attachments/assets/5e630288-0139-436f-bc4a-fc29551b92d9" />


  <br>
  <br>

## Task 6

- Flag

  <img width="738" height="39" alt="image" src="https://github.com/user-attachments/assets/815b0575-c858-4339-8db5-0132c1fc342f" />


> a. Apakah kamu menemukan fake flag? Tuliskan seluruhnya!

> _a. Did you find the fake flag? Write it whole!_

**Answer:** `FakeFlag{JarkomGampang}`

- Filter expression

  `frame contains "flag"`

- Explanation

  `Karena disuruh mencari flag maka pakai kata kunci flag di display filter, lalu follow tcp stream file flag.txt, lalu dapat fake flag nya`

- Output result

  <img width="756" height="786" alt="image" src="https://github.com/user-attachments/assets/4db6b1ea-b90b-4e99-82d7-f924bc9f9831" />


  <br>
  <br>

> b. Tuliskan username dan password yang tertulis! (format username:password)

> _b. Write the written username and password! (format username:password)_

**Answer:** `Rey:123`

- Filter expression

  `http.request`

- Explanation

  `lalu cari yang api nya janggal, ketemu passwd.txt, lalu follow tcp stream`

- Output result

 <img width="756" height="786" alt="image" src="https://github.com/user-attachments/assets/ee14dab8-598b-4fab-a3d1-1735c3e3809e" />


  <br>
  <br>

## Task 7

- Flag

 <img width="739" height="39" alt="image" src="https://github.com/user-attachments/assets/e7045b6d-224b-4af6-9b83-7d40400b9ffa" />


> Apa nama gambar yang direquest oleh client? (tulis dengan ekstensinya)

> _What is the image that is being requested by the client? (write with its extension)_

**Answer:** `donalbebek.jpg`

- Filter expression

  `http.request`

- Explanation

  `lalu cari yang format jpg karena gambar, ketemu donalbebek.jpg`

- Output result

 <img width="964" height="805" alt="image" src="https://github.com/user-attachments/assets/d4c77dd0-3833-4bb7-ac9b-2dfdf7cfa1b0" />


  <br>
  <br>

## Task 8

- Flag

 <img width="739" height="42" alt="image" src="https://github.com/user-attachments/assets/7630ecb8-0bed-4dca-bafd-6d517bbfd79e" />


> a. Berapa banyak packet berbasis FTP yang terekam pada file pcapng? (with the data)

> _a. How many FTP packets are recorded in the pcapng file? (with the data)_

**Answer:** `81`

- Filter expression

  `ftp || ftp-data`

- Explanation

  `saat liat protocol hierarchy ada tcp dan tcp data, agar si data tidak ikut filter maka pakai || agar baik ftp maupun ftp-data tertampilkan`

- Output result

  <img width="1103" height="804" alt="image" src="https://github.com/user-attachments/assets/e73052f9-0a5e-4332-b8ac-72c1e8ee2c9b" />


  <br>
  <br>

> b. Apa username dan password client di koneksi FTP? (tulis dalam format username:password)

> _b. What is the client's username and password in FTP connection? (write in following format username:password)_

**Answer:** `rey:password123lingangu`

- Filter expression

  `ftp`

- Explanation

  `tinggal lihat pada info bisa tau username dan passwordnya`

- Output result

 <img width="1103" height="802" alt="image" src="https://github.com/user-attachments/assets/04c6db91-b857-4fe4-bea6-181a2c556895" />

  <br>
  <br>

> c. What is the client's command for showing server directory that was sent on request packet?

> _c. Apa command client untuk melihat direktori server yang dikirimkan dalam request packet?_

**Answer:** `LIST`

- Filter expression

  `tcp.request.command`

- Explanation

  `input satu satu dan dapap hasilnya LIST`

- Output result

  <img width="1103" height="805" alt="image" src="https://github.com/user-attachments/assets/9dc00e77-bd9e-42d6-9404-e5d0029e7f7f" />


  <br>
  <br>

## Task 9

- Flag

 <img width="747" height="43" alt="image" src="https://github.com/user-attachments/assets/b039fb50-d59a-4086-a4be-f223fdbf67db" />
 

> a. Apa alamat IP dari FTP server?

> _a. What is the FTP server IP Address?_

**Answer:** `172.16.16.101`

- Filter expression

  `ftp`

- Explanation

  `di kolom source adalah IP address`

- Output result

  <img width="1100" height="795" alt="image" src="https://github.com/user-attachments/assets/740606ea-8156-41b1-8eb8-5152c67490d0" />


  <br>
  <br>

> b. Berapa banyak file yang ada dalam direktori FTP server?

> _b. How many files are there inside the FTP server directory?_

**Answer:** `7`

- Filter expression

  `" "`

- Explanation

  `statistic > protocol heirarchy, di bagian ftp-data kurangkan packets (10) dengan end packets (3)`

- Output result

  <img width="875" height="634" alt="image" src="https://github.com/user-attachments/assets/a72352eb-94dc-4fd4-a5e2-a14cbc14d3f9" />


  <br>
  <br>

> c. Apa nama dari file yang digunakan dalam page.html? (tulis lengkap namanya beserta ekstensinya dan dipisahkan dengan koma ',')

> _c. What are the filenames used in the page.html? (write the filebames with their extensions and separate them with comma ',')_

**Answer:** `pokijan.jpg,research_center.jpg`

- Filter expression

  `ftp-data`

- Explanation

  `follow dan tcp stream yang ada page.html, ada 2 sintaks jpg`

- Output result

<img width="917" height="791" alt="image" src="https://github.com/user-attachments/assets/48fe009b-aee9-4f84-8b5e-be3161fdfe11" />


  <br>
  <br>

## Task 10

- Flag

  <img width="740" height="39" alt="image" src="https://github.com/user-attachments/assets/a513a92e-4f72-4517-a366-35519fee24bd" />


> a. Apa nama file yang mengandung string terencode?

> _a. What is the filename that contains encoded string?_

**Answer:** `secret.txt`

- Filter expression

  `ftp-data`

- Explanation

  `kita saring dengan ftp-data dan menemukan secret.txt`

- Output result
<img width="1099" height="795" alt="image" src="https://github.com/user-attachments/assets/f0bebb5d-4fc2-4a0c-a61a-f8fcf0ff32f3" />
<br><br>
  `Terlihat ada 2 secret.txt`

  

  <br>
  <br>

> b. Apa nama file hasil copy file sebelumnya?

> _b. What is the filename of the previous file copy?_

**Answer:** `secret1.txt`

- Filter expression

  `ftp-data`

- Explanation

  `Terdapat secret1.txt dibawah secret.txt yang mana merupakan copy dari file sebelumnya`

- Output result

  <img width="1099" height="797" alt="image" src="https://github.com/user-attachments/assets/1ca68c1b-d000-4e74-b8ef-a6ab0e78bd4f" />
  <br><br>
  
  `Terlihat dibawah secret.txt ada secret1.txt yang adalah copy file secret.txt`

  <br>
  <br>

> c. What is the decoded string from the previous file?

> _c. Apa decoded string dari file tersebut?_

**Answer:** `Pada suatu hari Rey bertemu dengan Nailong the Milk Dragon. Ketika bertemu, Rey mengajarkan Nailong apa itu Jaringan Komputer. Nailong pun senang karena ternyata Jaringan Komputer itu gampang.`

- Filter expression

  `" "`

- Explanation

  `Pilih salah satu file antara secret.txt atau secret1.txt, lalu klik kanan file itu, lalu follow, lalu TCP stream untuk melihat tulisan yang nantinya akan kita decode `

- Output result

<img width="751" height="802" alt="image" src="https://github.com/user-attachments/assets/55132c0e-6834-4717-9dc4-61b7f256675f" />
<br><br>

  `Itu adalah tulisan yang akan di decode`

<br>
<img width="982" height="681" alt="image" src="https://github.com/user-attachments/assets/603813a5-7088-4610-ba6d-aa43ebaf9424" />
<br><br>

  `Itu kalimat setelah di decode`

  <br>
  <br>

## Summary

`[opsional] untuk mempermudah pengerjaan setiap soal bisa disaring dahulu pakai capture filter --> tcp.analysis.lost_segment || tcp.analysis.ack_lost_segment || tcp.analysis.retransmission || tcp.analysis.duplicate_ack || tcp.analysis.out_of_order`

`Cuman saya telat sadar`

## Problems

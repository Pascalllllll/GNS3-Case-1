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


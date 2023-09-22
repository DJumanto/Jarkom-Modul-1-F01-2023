# Laporan Resmi Praktikum 1 Jarkom 2023

## Kelompok F01

| Nama | NRP  |
| :--: | :--: |
| `Alfa Fakhrur Rizal Zaini` | `5025211214` |
## All Sections

| Problems  |
| :--- |
| [`Soal 1`](#soal-1) |
| [`Soal 2`](#soal-2) |
| [`Soal 3`](#soal-3) |
| [`Soal 4`](#soal-4) |
| [`Soal 5`](#soal-5) |
| [`Soal 6`](#soal-6) |
| [`Soal 7`](#soal-7) |
| [`Soal 8`](#soal-8) |
| [`Soal 9`](#soal-9) |
| [`Soal 10`](#soal-10) |


### Soal 1

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/1c0f6114-436e-4641-bfad-c9edbd004609)

Konek ke server melalui netcat, didapatkan soal berikut:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/d49e66a0-6635-4f59-9824-926e8d14fc47)

Untuk menyelesaikan soal ini, cukup dengan mencari traffic yang berhubungan dengan ftp, dengan cara menambahkan filter berikut pada bagian filter
```
ftp
```
Setelah itu, kita mendapatkan semua traffic ftp, follow salah satu packet dengan `follow tcp`. Setelah itu, kita cari command yang bisa dibilang menarik, saya ambil contoh command berikut:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/261be3d7-b558-4f32-b374-3ce1b9079760)

Tinggal isi jawaban dari pertanyaannya dan didapatkan flag berikut:

```
1. sequence number: 258040667
2. Acknowledge number: 1044861039
3. response sequence number : 1044861039
4. response acknowledge number : 258040696
```
![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/c113e0ef-a3fe-4aba-a745-4cdeb23aac73)

*flag: Jarkom2023{y0u_r_g00d_4t_4dr3ssing_AvLsFsJ00100040}*

### Soal 2

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/d8b17c6f-7bb7-46e1-be5c-f5b777ccc9a6)

lakukan filter pada file pcapng dengan `http` sebagai object filter nya, lalu follow salah satu packet dengan `follow http` pada IP platform yakni http://10.21.78.111:8000/, dan lihat webserver apa yang digunakan:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/c6832dee-6986-4ed3-8ab1-8b4bbc082b90)

server yang digunakan adalah gunicorn. Submit ke server menggunakan nc dan dapatkan flag:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/935e2461-f6f6-46bc-8f0b-428f26801061)


*flag: Jarkom2023{9unic0rn_1s_Ymxa12Vq6405JdN_c00l}*

### Soal 3

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/13ce3ed8-65f3-4295-a166-4fc8be9cfe42)

Masuk ke server submission, lalu didapatkan soal berikut:

```
Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?
```
Masuk ke statistic ->  ipv4 statistics -> Destination and Ports:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/e6bd39a4-cfab-48ab-a03d-ffac09bf5019)

Jawabannya adalah 21:


```
b. Protokol layer transport apa yang digunakan?
```

Jawaban: UDP

Didapatkan flag:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/901ec6c2-c696-4b47-9935-5bbb5f70cee0)

*flag: Jarkom2023{4nalyz3_is_2707_OtDhEjSuOkP_gr3at}*

### Soal 4

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/04753553-2d75-46c0-be63-add3c0b5737e)

Cari packet ke 130 lalu cari pada bagian checksum pada header:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/2992f693-3636-49c4-914d-b6f71dbaf377)

Didapatkan flag:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/e5069042-5a8f-49e1-9d31-3fff1de0f397)

*flag: Jarkom2023{ch3cksum_is_u5eful_0x3o9n}*
### Soal 5

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/a29cfb4c-576e-4aaa-b178-a3950f09346b)

Diberikan file pcap dan file zip, file tersebut terkunci sehingga memerlukan password untuk membukannya.

pada file pcapng, saya melihat ada packet yang menarik, dimana terdapat base64 encoded payload di dalamnya, dan ternyata menggunakan smtp sebagai protocol komunikasi. Langsung saja saya filter dengan `smtp` sebagai protocol dan membaca salah satu packetnya:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/1d44a749-a92b-4a78-aeae-cf94723e95de)

base64 decode lalu buka zipnya:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/75e23618-5781-4805-a6e5-d010fb5816f0)


didapatkan folder `s3crett` dengan isian sebagai berikut:

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/dd354c9f-f23f-4ea8-a8e5-0437c444212c)

Jawab pertanyaan dibawah dan didapatkan flag:

```
a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
Your answer: 60
Correct answer!
b. Port berapakah pada server yang digunakan untuk service SMTP?
Your answer: 25
Correct answer!
c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?
Your answer: 74.53.140.153
```
![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/dadd4a3b-a985-4111-ac83-d56e4f8bac25)

*flag: Jarkom2023{k0w4lski_9894_uwNtNCSBtuC_4nalys1s}*

### Soal 6

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/5fd7e9d3-f1e2-4cab-9109-333efd3f0615)

Untuk menyelesaikan soal ini, kita perlu mengetahui cara kerja dari `substition chiper`, dimana setiap ankga koresponden terhadap satu huruf. Pada soal ini, setelah membeli hint sebanyak 20 poin, ternyata kita perlu melakukan substitusi pada source IP pada paket nomor 7812:

Parse IP menjadi maksimal 26 untuk masing-masing pasang, maka jadilah hasilnya sebagai berikut:

```
10 4 18 14 10 1
J  D  R  N  J A
```

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/6517f035-9273-4714-8639-cf67dda0d011)

*flag: Jarkom2023{h3h3_ctf_d1k1t_a02I82N695M4GTE1JGkx}*


### Soal 7

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/4f88fcd7-2a9e-4778-8f27-a3f845ad44bc)

Jawaban: 6

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/ffe8e454-3e41-4eaf-84ac-90c4eb6bec03)

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/5f0346a4-1c58-4970-8444-e721693db079)

*flag: Jarkom2023{h2490A0mtMAVVbD6EB_4n0th3r_f1lt3ring}*

### Soal 8

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/baf28201-6252-49c3-8fe3-43b8afac3d9a)

Untuk mendapatkan semua packet yang menuju port 80, filter yang kita gunakan adalah `tcp.dstport == 80 || udp.dstport == 80`.

Jawaban: `tcp.dstport == 80 || udp.dstport == 80`

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/99bde921-dbd6-4705-9d7b-d0f5a49bd404)

*flag: Jarkom2023{qu3ryyyyying_519743_PtBzAjNkQyP_15_fun}*

### Soal 9

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/febb0bb0-96af-4564-93d1-17720d3872c4)


Untuk mendapatkan semua packet yang menuju port 80, filter yang kita gunakan adalah `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`.

Jawaban: `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`.

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/4c02bb6a-4a6c-4487-ac24-d7237950affc)

*flag: Jarkom2023{y3s_its_QgOmNjQkNjO_qu3ry1ng}*

### Soal 10

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/bca043cb-9c55-468b-a049-dec699008c95)

untuk melakukan pencarian pada telnet, kita filter menggunakan protocol `telnet` pada box filter.

Setelah itu coba cari packet yang memiliki length yang berbeda, hal ini dikarenakan size response pada login yang fail berbeda dengan ketika sukses.

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/d177038b-6d1e-487e-bbec-2c2126650b3c)

Follow packet 231 dan cek apa isinya dengan `follow tcp`

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/25a88614-16fc-43a2-92e3-9f3b94cc957b)

Yap benar saja, jadi username dan password yang benar adalah:

`login: dhafin`
`password: kesayangank0k0`

![image](https://github.com/DJumanto/Jarkom-Modul-1-F01-2023/assets/100863813/9c886304-1b77-488a-ba94-07da0ad9da52)

*flag: Jarkom2023{t3lnet_is_zCx75B6C9CCxBxy03_N0tSecu2e}*

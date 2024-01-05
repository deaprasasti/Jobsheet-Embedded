# B. Transmisi Data Menggunakan Protokol HTTP
   
## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/deaprasasti/Jobsheet-Embedded/files/13845062/flow.program.Multi-Protocol.IoT.json">disini</a>
2. Program ESP32 transmisi data dummy menggunakan protokol HTTP metode GET dapat dilihat <a href="https://github.com/deaprasasti/Jobsheet-Embedded/blob/master/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/transmisi_data_dummy_keNode-Red_protokol_HTTP_metode_Get/transmisi_data_dummy_keNode-Red_protokol_HTTP_metode_Get.ino">disini</a>
3. Program ESP32 transmisi data dummy menggunakan protokol HTTP metode POST dapat dilihat <a href="https://github.com/ArthZ01/System-Embedded/blob/05864b09d785d0e0f36e0ccaa11523e064d9bc64/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/transmisi_data_dummy_ke_Node-Red_protokol_HTTP_metode_POST/transmisi_data_dummy_ke_Node-Red_protokol_HTTP_metode_POST.ino">disini</a>

## 3. Flow Program

![Flow Program](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/5dd1cd58-b2f2-46c3-8fd4-0c4e036c95e4)




## 4. Hasil Percobaan Transmisi Data Dummy Menuju Node-Red Menggunakan Protokol HTTP Metode GET
### Dokumentasi Percobaan

1. Flow chart

   <img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/05984489-3d3b-4a5d-9870-7c71758e211b" height=700rem>
   
2. Output serial monitor

   <img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/4f555ea0-dc6b-4d3b-90b8-13b0344e1bce" width=80% height=80%>
   
4. Debug Node-RED
   
   ![  Debug Node-RED](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/da65a14d-50d0-43f5-9d92-6556758d8154)


5. Dashboard Node-RED

   <img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/708095b1-1482-4663-9964-611b08784f6e" width=80% height=80%>
   
7. Tabel database MySQL
   
    ![  Tabel database MySQL](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/29e0572f-af81-4628-8700-c82f9a2ad313)



### Source Code
<img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/eb9d6f11-6eec-48e2-b660-e837d4fae026" height=1000rem>

### Pembahasan
1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `HTTPClient.h` untuk membuat permintaan HTTP.
   * Deklarasi variabel:
     * `ssid` dan `password` untuk menyimpan nama dan password Wi-Fi.
     * `serverName` untuk menyimpan alamat server yang akan dituju.
     * `lastTime` untuk menyimpan waktu terakhir pengiriman data.
     * `timerDelay` untuk mengatur interval pengiriman data (dalam milisekon).
2. Fungsi `setup()`:
   * Inisialisasi Serial Monitor:
     * `Serial.begin(115200)` untuk menampilkan pesan di Serial Monitor.
   * Menghubungkan ke Wi-Fi:
     * `WiFi.begin(ssid, password)` untuk menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menunggu hingga tersambung ke Wi-Fi:
     * Program akan menunggu hingga koneksi Wi-Fi berhasil sebelum melanjutkan.
   * Menampilkan informasi IP Address:
     * Program menampilkan IP Address yang didapatkan oleh board Arduino.
     * Menginformasikan pengaturan timer:
     * Program menampilkan pesan yang menunjukkan interval pengiriman data.
3. Fungsi `loop()`:
   * Mengirim data setiap interval tertentu:
     * Program akan memeriksa apakah waktu yang telah berlalu sejak pengiriman data terakhir melebihi timerDelay. Jika iya, maka akan dilakukan pengiriman data.
   * Memeriksa status koneksi Wi-Fi:
     * Jika board Arduino masih terhubung ke Wi-Fi, maka proses pengiriman data akan dilanjutkan.
   * Membuat client HTTP:
     * `WiFiClient client` membuat objek client untuk komunikasi HTTP.
     * `HTTPClient http` membuat objek untuk melakukan permintaan HTTP.
   * Menentukan server tujuan:
     * `http.begin(client, serverName`) menetapkan server yang akan dituju untuk pengiriman data.
   * Menentukan header Content-Type:
     * `http.addHeader("Content-Type", "application/json")` menetapkan format data yang dikirimkan adalah JSON.
   *Mempersiapkan data yang akan dikirimkan:
     * String `httpRequestData` menyimpan data dalam format JSON yang akan dikirimkan. Dalam kode ini, data yang dikirimkan berupa nilai `dev_id`, `level`, `rainfall`, dan `flow`.
   * Mengirim permintaan HTTP GET:
     * `int httpResponseCode = http.GET()` mengirimkan permintaan GET ke server dengan data yang telah disiapkan.
   * Menampilkan kode respons HTTP:
     * Program menampilkan kode respons yang diterima dari server untuk mengetahui status pengiriman data.
   * Menutup koneksi HTTP:
     * `http.end()` menutup koneksi HTTP.
   * Mencatat waktu pengiriman data terakhir:
     * `lastTime = millis()` menyimpan waktu saat ini sebagai waktu terakhir pengiriman data
       
Catatan:
   * Kode ini menggunakan metode GET.
   * Interval pengiriman data diatur dalam variabel `timerDelay` (5 detik dalam kode ini).
   * Data yang dikirimkan dalam format JSON.
   * Server yang dituju adalah `http://192.168.1.7:1880/flood/node1`.

## ANALISA

   Praktikum di atas mencakup pengaturan dan konfigurasi untuk mentransmisikan data dari perangkat ESP32 ke server Node-Red menggunakan protokol HTTP. Pada langkah pertama, dilakukan konfigurasi Virtual Machine dengan adapter jaringan mode bridge dan pembuatan tabel database pada VM Ubuntu untuk menyimpan data banjir. Selanjutnya, pada langkah kedua, skrip program Node-Red disediakan untuk membuat konfigurasi Multi-Protocol IoT Server dengan menggunakan protokol HTTP dan MQTT, serta menghubungkannya dengan database yang telah dibuat sebelumnya. Adapun langkah ketiga mengenai ESP32, dilakukan upload skrip program ke perangkat tersebut untuk melakukan transmisi data dummy menuju Node-Red dengan protokol HTTP.
   Percobaan ini menggunakan transmisi data dummy dari perangkat ESP32 menuju server Node-Red menggunakan protokol HTTP dengan metode GET. Pertama-tama, ESP32 dikonfigurasi untuk terhubung ke jaringan WiFi dengan menentukan SSID dan kata sandi yang sesuai. Selanjutnya, dilakukan konfigurasi URL untuk mengirim data, yang pada praktikum ini menggunakan metode GET dengan menambahkan parameter data dummy ke URL. Skrip program pada ESP32 kemudian dikonfigurasi untuk membuat koneksi HTTP ke server Node-Red dan mengirimkan data dummy melalui URL yang telah dibentuk sebelumnya.
   Server Node-Red diatur untuk menerima data dari ESP32 melalui protokol HTTP. Sebuah node HTTP In menetapkan endpoint atau jalur URL untuk menerima data. Data yang diterima kemudian diolah, misalnya dengan memisahkan parameter dari URL dan melakukan validasi. Proses ini memungkinkan integrasi data ke dalam sistem yang lebih besar, seperti penyimpanan data dalam database atau visualisasi data.

## KESIMPULAN 

Percobaan ini melibatkan konfigurasi Virtual Machine, Node-Red server, dan ESP32 untuk berhasil mentransmisikan data dummy dari ESP32 ke server Node-Red melalui protokol HTTP dengan metode GET. Langkah-langkah termasuk konfigurasi jaringan pada Virtual Machine, pengaturan database, konfigurasi server Node-Red dengan multi-protocol IoT, dan upload skrip program pada ESP32. Penggunaan protokol HTTP dan metode GET memberikan gambaran tentang cara sistem IoT dapat mengirimkan data dengan efisien, tetapi keamanan data juga perlu diperhatikan. Kesimpulan mencakup keberhasilan implementasi, potensi keamanan, dan integrasi data dalam konteks transmisi data dari perangkat IoT ke server.


## 5. Hasil Percobaan Transmisi Data Dummy Menuju Node-Red Menggunakan Protokol HTTP Metode POST
### Dokumentasi Percobaan

1. Flow chart 

   <img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/9c59e274-4da3-4569-a54c-68b341211c1e" height=700rem>

2. Output serial monitor
 
   <img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/2792706d-a6c1-4e06-8109-b4b315404235" width=80% height=80%>
   
3. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/ArthZ01/System-Embedded/assets/91934953/d4095d4f-5805-481c-a097-970f5edfe399)
   
4. Dashboard Node-RED
 
   <img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/69f41a3e-0c2f-4ef1-af93-529e83ef68ed" width=80% height=80%>

### Source Code
<img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/6b887c29-1601-4ff9-bd61-bd6825bddcb7" height=1000rem>

### Pembahasan

1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `HTTPClient.h` untuk membuat permintaan HTTP.
   * Deklarasi variabel:
     * `ssid` dan `password` untuk menyimpan nama dan password Wi-Fi.
     * `serverName` untuk menyimpan alamat server yang akan dituju.
     * `lastTime` untuk menyimpan waktu terakhir pengiriman data.
     * `timerDelay` untuk mengatur interval pengiriman data (dalam milisekon).
       
2. Fungsi `setup()`:
   * Inisialisasi Serial Monitor:
     * `Serial.begin(115200)` untuk menampilkan pesan di Serial Monitor.
   * Menghubungkan ke Wi-Fi:
     * `WiFi.begin(ssid, password)` untuk menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menunggu hingga tersambung ke Wi-Fi:
     * Program akan menunggu hingga koneksi Wi-Fi berhasil sebelum melanjutkan.
   * Menampilkan informasi IP Address:
     * Program menampilkan IP Address yang didapatkan oleh board Arduino.
   * Menginformasikan pengaturan timer:
     * Program menampilkan pesan yang menunjukkan interval pengiriman data.
       
3. Fungsi `loop()`:
   * Mengirim data setiap interval tertentu:
     * Program akan memeriksa apakah waktu yang telah berlalu sejak pengiriman data terakhir melebihi `timerDelay`. Jika iya, maka akan dilakukan pengiriman data.
   * Memeriksa status koneksi Wi-Fi:
     * Jika board Arduino masih terhubung ke Wi-Fi, maka proses pengiriman data akan dilanjutkan.
   * Membuat client HTTP:
     * `WiFiClient client` membuat objek client untuk komunikasi HTTP.
     * `HTTPClient http` membuat objek untuk melakukan permintaan HTTP.
   * Menentukan server tujuan:
     * `http.begin(client, serverName)` menetapkan server yang akan dituju untuk pengiriman data.
   * Menentukan header Content-Type:
     * `http.addHeader("Content-Type", "application/json")` menetapkan format data yang dikirimkan adalah JSON.
   * Mempersiapkan data yang akan dikirimkan:
     * String `httpRequestData` menyimpan data dalam format JSON yang akan dikirimkan. Dalam kode ini, data yang dikirimkan berupa nilai `dev_id`, `level`, `rainfall`, dan `flow`.
   * Mengirim permintaan HTTP POST:
     * `int httpResponseCode = http.POST(httpRequestData)` mengirimkan permintaan POST ke server dengan data yang telah disiapkan.
   * Menampilkan kode respons HTTP:
     * Program menampilkan kode respons yang diterima dari server untuk mengetahui status pengiriman data.
   * Menutup koneksi HTTP:
     * `http.end()` menutup koneksi HTTP.
   * Mencatat waktu pengiriman data terakhir:
     * `lastTime = millis()` menyimpan waktu saat ini sebagai waktu terakhir pengiriman data.
       
Catatan:
   * Kode ini menggunakan metode POST untuk mengirimkan data ke server.
   * Interval pengiriman data diatur dalam variabel `timerDelay` (5 detik dalam kode ini).
   * Data yang dikirimkan dalam format JSON.
   * Server yang dituju adalah `http://192.168.1.7:1880/flood/node1`.
   * Kode ini dapat digunakan untuk mengirimkan data sensor atau informasi lain dari board Arduino ke server secara berkala.


## ANALISA

   Percobaan transmisi data dummy menuju Node-Red menggunakan protokol HTTP dengan metode POST ini melibatkan perangkat ESP32 yang dikonfigurasi untuk mentransfer informasi palsu ke server Node-Red. Pertama-tama, dalam konfigurasi WiFi, ESP32 terhubung ke jaringan WiFi yang ditentukan menggunakan SSID dan kata sandi yang telah diatur. Ini memastikan perangkat memiliki koneksi ke jaringan yang diperlukan untuk mentransmisikan data.
   Selanjutnya, skrip program pada ESP32 menetapkan alamat server Node-Red yang akan menerima data. Dalam kasus ini, server tersebut ditentukan dengan URL dan jalur tertentu. Skrip ini diatur untuk mengirim permintaan HTTP POST setiap 5 detik, membawa data dummy yang telah ditentukan sebelumnya, seperti dev_id, level, rainfall, dan flow, dalam format JSON. Penggunaan metode POST memungkinkan pengiriman data yang lebih kompleks dan lebih aman daripada metode GET.
   Di sisi Node-Red, server diatur untuk menerima data dari ESP32 melalui protokol HTTP. Node HTTP In digunakan untuk menetapkan endpoint atau jalur URL di mana server akan menerima data. Data yang diterima kemudian dapat diolah sesuai kebutuhan, misalnya, dengan mengekstrak nilai-nilai yang dikirimkan, melakukan validasi, atau menyimpannya dalam database. 

## KESIMPULAN 

   Secara keseluruhan, praktikum transmisi data dummy dari perangkat ESP32 ke server Node-Red menggunakan protokol HTTP metode POST memberikan pemahaman yang baik tentang konfigurasi dan implementasi aspek-aspek dasar dalam komunikasi IoT. Melalui percobaan ini, dapat disimpulkan bahwa penentuan konfigurasi jaringan pada perangkat, penyusunan skrip program untuk pengiriman data, dan pengaturan Node-Red sebagai penerima data telah berhasil dilakukan. Metode POST yang digunakan menunjukkan keunggulan dalam mentransfer data yang lebih kompleks, merangsang pemahaman tentang penggunaan HTTP dalam skenario IoT praktis.


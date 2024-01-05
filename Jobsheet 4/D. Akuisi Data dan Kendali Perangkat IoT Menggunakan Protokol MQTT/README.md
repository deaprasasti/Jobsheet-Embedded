# D. Akuisi Data dan Kendali Perangkat IoT Menggunakan Protokol MQTT
   
## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. Kabel jumper
4. LED
5. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/deaprasasti/Jobsheet-Embedded/blob/master/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/flow%20program%20Multi-Protocol%20IoT.json">disini</a>
2. Program ESP32 kontrol nyala LED melalui dashboard Node-RED dapat dilihat <a href="https://github.com/deaprasasti/Jobsheet-Embedded/blob/master/Jobsheet%204/D.%20Akuisi%20Data%20dan%20Kendali%20Perangkat%20IoT%20Menggunakan%20Protokol%20MQTT/akuisisi/akuisisi.ino">disini</a>

## 3. Flow Program

![Flow Program](https://github.com/ArthZ01/System-Embedded/assets/91934953/8481c937-042b-4cde-918c-9d1004649e05)

## 4. Hasil & Penjelasan Percobaan Kontrol Nyala LED Melalui Dashboard Node-RED
### Dokumentasi Percobaan

1. Dokumentasi
   
   <img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/c75e2902-0155-4ad6-b519-40f007e1ec9e" width=40% height=40%>   

   <img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/0e1f35d6-fef7-429d-8169-558591cfa855" width=40% height=40%>


2. Debug Node-RED
   
   ![3  Debug Node-RED](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/6de5bdaf-5eb8-41ce-9c89-696c6dc054ca)


   
3. Dashboard Node-RED

   <img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/c179e801-3906-4354-bca0-46056192e4b9" width=40% height=40%>
   
### Kode
<img src="https://github.com/ArthZ01/System-Embedded/assets/91934953/ac83a5a1-23e9-4a73-91e6-92d48ff74e64" height=1000rem>

### Pembahasan
1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `Adafruit_MQTT.h` dan `Adafruit_MQTT_Client.h` untuk komunikasi MQTT dengan server Adafruit IO.
   * Deklarasi variabel:
     *`WLAN_SSID`, `WLAN_PASS`, `AIO_SERVER`, `AIO_SERVERPORT`, `AIO_USERNAME`, dan `AIO_KEY` untuk konfigurasi koneksi Wi-Fi dan MQTT.
     * `output` untuk menyimpan pin output yang akan dikendalikan.
     * `client` untuk membuat koneksi TCP/IP ke server MQTT.
     * `mqtt` untuk komunikasi MQTT.
     * `led` untuk berlangganan topic "led" pada server MQTT.

2. Fungsi `setup()`:
   * Menginisialisasi Serial Monitor untuk menampilkan pesan.
   * Mengatur pin 2 sebagai output.
   * Menghubungkan board Arduino ke jaringan Wi-Fi.
   * Menampilkan informasi IP Address yang didapatkan oleh board Arduino.
   * Berlangganan topic "led" pada server MQTT.
     
3. Fungsi `loop()`:
   * Mencoba menghubungkan board Arduino ke server MQTT jika belum terhubung.
   * Membaca pesan yang diterima dari topic yang dilanggan setiap 5 detik.
   * Jika pesan diterima dari topic "led":
     * Menampilkan nilai pesan yang diterima.
     * Jika nilai pesan adalah "1", menyalakan LED pada pin 2.
     * Jika nilai pesan bukan "1", mematikan LED pada pin 2.

4. Fungsi `MQTT_connect()`:
   * Mencoba menghubungkan board Arduino ke server MQTT.
   * Jika gagal, mencoba kembali hingga maksimal 3 kali dengan jeda 5 detik.
   * Jika gagal terhubung setelah 3 kali, menghentikan program.
     
Catatan:
   * Kode ini menggunakan protokol MQTT untuk mengendalikan perangkat IoT (dalam hal ini, menyalakan dan mematikan LED) dari jarak jauh melalui server Adafruit IO.
   * Server MQTT yang digunakan adalah `io.adafruit.com`.
   * Kode ini dapat dimodifikasi untuk mengendalikan berbagai macam perangkat IoT lainnya.

## ANALISA

Pada tahap akuisisi data, program pada ESP32 dikonfigurasi untuk mengukur suhu dan kelembaban setiap 5 detik dan mengirimkan data ke server melalui protokol MQTT. Penggunaan format JSON untuk menyusun data mempermudah representasi dan interpretasi data oleh server, menunjukkan kemudahan integrasi antara perangkat dan server menggunakan MQTT. Ini menegaskan efisiensi dan keterbacaan protokol dalam konteks akuisisi data sensor. Pada tahap kendali perangkat, interaksi antara ESP32 dan dashboard Node-Red memanfaatkan protokol MQTT untuk mengontrol LED. Melalui pengaturan topik tertentu, dashboard dapat mengirimkan instruksi ke ESP32 untuk menghidupkan atau mematikan LED. Hal ini mencerminkan fleksibilitas protokol MQTT dalam mendukung kendali perangkat IoT, memungkinkan aksi yang cepat dan responsif terhadap perubahan kondisi atau perintah dari dashboard. Selanjutnya, tahap pengendalian LED menggunakan suara melibatkan integrasi Adafruit IO dan MQTT. ESP32 mampu menerima instruksi suara melalui MQTT, menunjukkan kemampuan protokol ini untuk mendukung komunikasi dua arah yang kompleks. Hal ini menciptakan potensi aplikasi yang lebih luas, di mana perangkat IoT dapat merespons perintah suara untuk menjalankan fungsi tertentu, memperluas cakupan penggunaan 


## KESIMPULAN

Pada keseluruhan praktikum, terlihat bahwa penggunaan protokol MQTT memberikan solusi komprehensif untuk akuisisi data dan kendali perangkat IoT. Kemampuannya dalam menyediakan aliran data yang andal dan mendukung komunikasi dua arah memperkuat posisinya sebagai protokol yang sangat cocok untuk implementasi IoT. 

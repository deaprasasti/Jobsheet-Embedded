# C. Transmisi Data Menggunakan Protokol MQTT

## 1. Alat dan Bahan
1. Node-RED
2. ESP32
3. XAMPP

## 2. Source Code

1. Code JSON Multi-Protocol IoT Server dapat dilihat <a href="https://github.com/ArthZ01/System-Embedded/blob/56e9a384948c7094115b371713c101f8607528e6/Jobsheet%204/B.%20Transmisi%20Data%20Menggunakan%20Protokol%20HTTP/flow%20program%20Multi-Protocol%20IoT.json">disini</a>
2. Program ESP32 dapat dilihat <a href="https://github.com/ArthZ01/System-Embedded/blob/56e9a384948c7094115b371713c101f8607528e6/Jobsheet%204/C.%20Transmisi%20Data%20Menggunakan%20Protokol%20MQTT/program%20transmisi%20mqtt/program%20transmisi%20mqtt.ino">disini</a>


## 3. Flow Program

![Flow Program](https://github.com/ArthZ01/System-Embedded/assets/91934953/c94b9604-a98c-4036-9df2-14c0a48a964d)

## 4. Hasil & Pembahasan
### Dokumentasi Hasil

1. Flow chart 

     ![Flow Chart](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/55edcd93-8177-4264-aac3-d0c9f70be90b)

   
3. Output serial monitor
   
     ![2  Output serial monitor](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/552c4de7-fa1f-4ee6-a0a0-4be3565ce34a)


4. Debug Node-RED
   
    ![3  Debug Node-RED](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/8040e549-a7fb-4376-b0be-dd9678a34e46)

   
5. Dashboard Node-RED

   ![4  Dashboard Node-RED](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/1d017b4b-5c66-40fd-9fb0-fb8be8f1991d)

   
6. Tabel database MySQL
   
   ![image](https://github.com/ArthZ01/System-Embedded/assets/91934953/b6e71433-c1e9-4338-8658-50a975f8fb39)


### Source Code
![Penjelasan Kode](https://github.com/ArthZ01/System-Embedded/assets/91934953/bce2d89a-1422-4f42-99e6-76cb8ad0fb6d)

### Pembahasan
1. Bagian Awal:
   * Memasukkan library yang diperlukan:
     * `WiFi.h` untuk mengakses fungsi Wi-Fi.
     * `PubSubClient.h` untuk komunikasi MQTT.
     * `ArduinoJson.h` untuk menangani format JSON.
   * Deklarasi variabel:
     * `ssid` dan `password` untuk menyimpan nama dan password Wi-Fi.
     * `mqtt_server` untuk menyimpan alamat server MQTT.
     * `espClient` untuk membuat koneksi TCP/IP ke server MQTT.
     * `client` untuk komunikasi MQTT.

2. Fungsi `setup_wifi()`:
   * Menghubungkan board Arduino ke jaringan Wi-Fi dengan nama dan password yang telah ditentukan.
   * Menampilkan informasi IP Address yang didapatkan oleh board Arduino.
     
3. Fungsi `reconnect()`:
   * Mencoba menghubungkan board Arduino ke server MQTT.
   * Jika gagal, mencoba kembali setiap 5 detik.

4. Fungsi `setup()`:
   * Menginisialisasi Serial Monitor untuk menampilkan pesan.
   * Menghubungkan board Arduino ke Wi-Fi.
   * Mengatur server MQTT yang akan dituju

5. Fungsi loop():
   * Memeriksa apakah koneksi MQTT masih tersambung.
   * Jika terputus, memanggil fungsi `reconnect()` untuk menyambung kembali.
   * Menangani proses MQTT secara berkala.
   * Mempersiapkan data yang akan dikirimkan dalam format JSON.
   * Menerbitkan data ke topic "flood/node1" pada server MQTT.
   * Menunggu 10 detik sebelum mengirimkan data berikutnya.

Catatan:
   * Kode ini menggunakan protokol MQTT untuk mengirimkan data sensor atau informasi lain dari board Arduino ke server secara berkala.
   * Interval pengiriman data diatur dalam fungsi `loop()` (10 detik dalam kode ini).
   * Data yang dikirimkan dalam format JSON.
   * Server MQTT yang digunakan adalah `broker.hivemq.com`.
   * Kode ini dapat digunakan untuk aplikasi IoT yang membutuhkan komunikasi dua arah yang ringan dan efisien.

## ANALISA

Praktikum ini melibatkan penggunaan ESP32 untuk mentransmisikan data sensor menggunakan protokol MQTT. Pada tahap awal, dilakukan konfigurasi koneksi WiFi dan MQTT yang esensial untuk memungkinkan ESP32 berkomunikasi dengan server MQTT. Keunggulan protokol MQTT, yang merupakan protokol berbasis pesan yang ringan dan handal, mempermudah pengiriman data secara efisien dari perangkat ke server.

Program pada ESP32 dirancang untuk secara otomatis mencoba kembali koneksi MQTT jika terputus. Fungsi ini memberikan ketangguhan terhadap fluktuasi jaringan, memastikan keberlanjutan pengiriman data. Kemampuan ini penting dalam konteks aplikasi IoT, di mana keterhubungan perangkat harus dijaga sebaik mungkin untuk memastikan kelancaran pengumpulan data secara real-time. Penggunaan format data JSON untuk mengemas data sensor sebelum dikirim memudahkan pemrosesan data di sisi penerima, dalam hal ini, server Node-Red. Hal ini sesuai dengan kecenderungan umum dalam IoT untuk menggunakan format data yang mudah dipahami dan diolah oleh platform perangkat lunak. 

## KESIMPULAN


Pada praktikum transmisi data menggunakan protokol MQTT pada ESP32, dapat disimpulkan bahwa implementasi protokol MQTT berhasil memungkinkan ESP32 untuk mentransmisikan data sensor secara efisien dan handal ke server. Keterhubungan yang dapat dipertahankan secara otomatis oleh ESP32, kemampuan untuk melakukan reconect saat koneksi terputus, serta penggunaan format JSON untuk menyusun data sensor, menunjukkan kehandalan dan fleksibilitas dalam pengiriman data di lingkungan Internet of Things (IoT).

# A. Setting SSID dan Password Wi-Fi ESP32 melalui Web Server

## 1. Alat dan Bahan
1) ESP32
2) Arduino IDE

## 2. Source Code

<img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/c3c8e47d-3cc6-4e1d-afa7-62a5d1380719" height=1000rem>


## 3. Flowchart

<img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/39e8974a-d0cb-4461-a568-35f97faca3ee" height=700rem>

## 4. Hasil dan Pembahasan
### Dokumentasi Hasil
1. Tampilan Awal Serial Monitor Sebelum Dihubungkan
   
![1  Tampilan Awal Serial Monitor Sebelum Dihubungkan](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/4c3d8878-19ec-4a0e-bf3d-a47d2689e897)

2. Tampilan Web & WiFi
   
   ![tampilan wifi](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/c99c8681-2a57-4ad9-a454-9d7c6b1e3310)
![2  tampilan web](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/3eb49354-b23d-4a8f-ae0d-2d432ed0295d)

3. Serial Monitor Setelah Memasukkan SSID dan PASS
   
   ![SSID dan Pass](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/571c4fce-b796-49d3-8dcb-ef6b595714d2)

   ![3  serial monitor setelah memasukan ssid dan pass](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/1a73aec8-3eb9-4c7f-9d8d-5a3322548ca7)

   
4. Serial Monitor Setelah Berhasil Terhubung
   
   ![4  Serial Monitor Setelah Berhasil Terhubung](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/12f9df48-1c91-415d-8a4a-6905d64f4cc6)


### Pembahasan

  Praktikum di atas mengilustrasikan penggunaan ESP32 untuk konfigurasi SSID dan password Wi-Fi melalui sebuah web server. Langkah-langkahnya mencakup inisialisasi perangkat, pengecekan status koneksi Wi-Fi, dan pembukaan akses poin (HotSpot) jika terjadi masalah koneksi atau ada perintah untuk melakukan konfigurasi baru. Web server yang dibuka memungkinkan pengguna untuk memasukkan informasi baru, seperti SSID dan password, yang nantinya disimpan dalam memori EEPROM. Setelah konfigurasi baru disimpan, ESP32 di-restart untuk menerapkan perubahan, dan kemudian mencoba untuk terhubung ke jaringan Wi-Fi dengan informasi yang telah diperbarui.

   Dokumentasi hasil dari Serial Monitor penting untuk memahami langkah-langkah yang dilakukan ESP32 selama praktikum. Pesan-pesan status, informasi SSID, dan password yang terbaca dari EEPROM memberikan bukti atas keberhasilan atau kegagalan proses konfigurasi. Dengan demikian, pemantauan Serial Monitor menjadi kunci untuk menilai keberhasilan praktikum. Flow chart program menyajikan pandangan visual tentang alur program secara keseluruhan. Dengan melihat diagram tersebut, dapat diperoleh gambaran yang jelas tentang bagaimana ESP32 berinteraksi dengan koneksi Wi-Fi, HotSpot, dan web server untuk mengelola konfigurasi SSID dan password. Keseluruhan praktikum ini memberikan pengalaman praktis yang bermanfaat dalam konfigurasi perangkat IoT secara dinamis melalui antarmuka web.
  
### Kesimpulan:

Dalam praktikum ini, telah berhasil diimplementasikan konfigurasi SSID dan password Wi-Fi pada ESP32 melalui sebuah web server. Langkah-langkah yang dijalankan mencakup inisialisasi perangkat, pengecekan status koneksi Wi-Fi, serta pembukaan akses poin (HotSpot) jika diperlukan. Web server yang dibuka memungkinkan pengguna untuk melakukan konfigurasi secara dinamis dengan memasukkan informasi baru seperti SSID dan password. Hal ini memberikan fleksibilitas yang tinggi dalam mengelola koneksi Wi-Fi tanpa perlu melakukan reprogram langsung pada kode sumber.

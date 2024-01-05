# A. Setting SSID dan Password Wi-Fi ESP32 melalui Web Server

## 1. Alat dan Bahan
1) ESP32
2) Arduino IDE

## 2. Source Code

<img src="https://github.com/deaprasasti/JobsheetEmbedded/assets/153251202/aab217c4-0084-4960-820b-d67ad107a445" height=1000rem>


## 3. Flowchart

<img src="https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/39e8974a-d0cb-4461-a568-35f97faca3ee" height=700rem>

## 4. Hasil dan Pembahasan
### Dokumentasi Hasil
1. Tampilan Awal Serial Monitor Sebelum Dihubungkan

   ![1  Tampilan Awal Serial Monitor Sebelum Dihubungkan]
![1  Tampilan Awal Serial Monitor Sebelum Dihubungkan](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/4c3d8878-19ec-4a0e-bf3d-a47d2689e897)

2. Tampilan Web & WiFi
   ![tampilan wifi](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/c99c8681-2a57-4ad9-a454-9d7c6b1e3310)
![2  tampilan web](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/3eb49354-b23d-4a8f-ae0d-2d432ed0295d)

4. Serial Monitor Setelah Memasukkan SSID dan PASS
   ![SSID dan Pass](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/571c4fce-b796-49d3-8dcb-ef6b595714d2)

   ![3  serial monitor setelah memasukan ssid dan pass](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/1a73aec8-3eb9-4c7f-9d8d-5a3322548ca7)

   
6. Serial Monitor Setelah Berhasil Terhubung
   ![4  Serial Monitor Setelah Berhasil Terhubung](https://github.com/deaprasasti/Jobsheet-Embedded/assets/153251202/12f9df48-1c91-415d-8a4a-6905d64f4cc6)


### Pembahasan

  1. Bagian Awal:
  * Memasukkan library yang diperlukan:
     * 'WiFi.h': untuk mengakses fungsi Wi-Fi.
     * Membaca kredensial WiFi yang tersimpan di EEPROM.
     * Mencoba menghubungkan ke WiFi menggunakan kredensial tersebut.

  2. Loop Utama:
  * Jika terkoneksi ke WiFi:
    * Mencetak pesan konfirmasi koneksi.
  * Jika tidak terkoneksi ke WiFi:
    * Mengecek status tombol untuk memaksa mode AP (Access Point).
    * Jika tombol tidak ditekan dan koneksi gagal, memulai mode AP dan membuat halaman web untuk konfigurasi WiFi.
    * Menunggu hingga terkoneksi ke WiFi.

  3. Fungsi testWifi:
  * Mencoba menghubungkan ke WiFi selama 10 detik.
  * Mengembalikan nilai 'true' jika terkoneksi, 'false' jika tidak.

  4. Fungsi launchWeb:
  * Mencetak informasi IP address perangkat (local dan softAP jika ada).
  * Menjalankan fungsi createWebServer untuk membuat halaman web konfigurasi WiFi.

  5. Fungsi setupAP:
  * Mengatur perangkat sebagai Access Point (AP) dengan nama "MiSREd IoT".
  * Mencari jaringan WiFi di sekitar dan menyimpan daftarnya dalam variabel st.
  * Menjalankan fungsi launchWeb untuk menampilkan halaman konfigurasi WiFi.

  6. Fungsi createWebServer:
  * Menangani permintaan ke halaman web:
    * '/' : Menampilkan halaman utama dengan daftar jaringan WiFi yang ditemukan dan formulir untuk memasukkan kredensial WiFi baru.
    * '/scan' : Memindai ulang jaringan WiFi dan menampilkan hasilnya.
    * '/setting' : Menerima kredensial WiFi baru, menyimpannya ke EEPROM, dan me-restart perangkat.
  
### Kesimpulan:
Kode ini dirancang untuk memudahkan konfigurasi WiFi pada perangkat dengan menyediakan antarmuka web yang dapat diakses dari perangkat lain. Pengguna dapat mengubah kredensial WiFi tanpa perlu mengubah kode secara langsung.

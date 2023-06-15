# Smart Room Monitor
Monitoring suhu dan kelembaban ruangan menggunakan sensor DHT (Digital Humidity and Temperature) yang dihubungkan dengan aplikasi mobile dan MQTT. 

## Penjelasan Program
---
### Wokwi

Program ini merupakan implementasi teori yang didapatkan selama perkuliahan Internet of Things, rangkaian yang dibuat merupakan rangkaian virtual menggunakan Wokwi IoT simulator (embeed). Rangkaian dibuat menggunakan board ESP32 yang terhubung dengan resistor, led, dan sensor DHT22. 
![Rangkaian-Digital-Smart-Room](https://github.com/AlyaniNS/Smart-Room/assets/74224380/1ac1d789-7bd5-4fae-9dc6-c8ac5daa85ff)


### Kodular
Rangkaian digital kemudian dihubungkan dengan aplikasi mobile yang dibuat menggunakan Kodular dengan tampilan sebagai berikut:
![UI-Smart-Room](https://github.com/AlyaniNS/Smart-Room/assets/74224380/0b64e819-fdfc-4eab-8004-983ed9e94356)

Terdapat 2 buah screen dari aplikasi mobile, screen pertama merupakan dashboard untuk monitoring suhu dan kelembaban ruangan yang dilengkapi dengan 2 buah switch untuk masing-masing sensor. Terdapat 5 buah button dalam program ini:
|No| Gambar | Fungsi | 
|--|--------|--------|
| 1|--------|Pindah ke page About Us|
| 2|--------|Pindah ke page Dashboard|
| 3|--------|Menghubungkan aplikasi ke MQTT|
| 4|--------|Menyalakan dan mematikan sensor temperatur|
| 5|--------|Menyalakan dan mematikan sensor kelembaban|

Demo Aplikasi 
[insert gif]
Dapat dilihat pada demo aplikasi, ketika sensor temperatur dimatikan, maka sensor kelembaban akan ikut mati, begitu juga sebaliknya. Karena sensor ini berada di 1 sensor yang sama, jadi penggunaannya tidak dapat dipisahkan.

### MQTT
Data yang diperoleh oleh sensor dapat ditampilkan di aplikasi mobile dengan bantuan MQTT. 
- Rangkaian digital yang dibuat menggunakan Wokwi berfungsi sebagai publisher dan subscriber. Sebagai publisher, rangkaian digital mengirimkan informasi nilai temperatur dan kelembaban. Lalu sebagai subscriber, rangkaian digital menerima nilai switch yang dikirimkan oleh aplikasi mobile apakah switch tersebut dinyalakan atau dimatikan.
- Aplikasi mobile bertindak sebagai publisher dan subscriber. Sebagai publisher, aplikasi mobile mengirimkan nilai switch. Lalu sebagai subscriber, aplikasi mobile menerima nilai temperatur dan kelembaban yang dikirimkan oleh rangkaian digital.

Aktivitas publish dan subscribe tersebut dijembatani oleh broker—dalam program ini kami menggunakan broker shiftr.io—sehingga setiap aktivitasnya bisa dikirim dan diterima oleh rangkaian digital maupun aplikasi mobile.
[insert visualisasi shiftr]

Data yang diperoleh oleh sensor DHT22 disimpan kedalam database dengan menggunakan webhook yang diatur menggunakan broker.
[visualisasi database masuk]

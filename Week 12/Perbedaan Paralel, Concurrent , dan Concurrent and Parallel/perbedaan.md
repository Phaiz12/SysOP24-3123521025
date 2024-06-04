NAMA : AHMAD FAIZ ASIFUDDIN

KELAS : IT - A

NRP : 3123521025

**`PERBEDAAAN  PARALEL, CONCURRENT , DAN CONCURRENT AND PARALLEL`**

**PARALEL**

Secara sederhana : Eksekusi beberapa tugas secara benar-benar bersamaan menggunakan multiple prosesor atau core.

Karakteristik :

1.Tugas dijalankan secara simultan pada processor yang berbeda.

2.Menggunakan sumber daya hardware tambaan untuk meningkatkan kecepatan eksekusi.

3.Cocok untuk tugas-tugas yang dapat dipecah menjadi subtugas independen yang bisa dijalankan secara bersamaan.

**CONCURRENT**

Secara sederhana : Eksekusi beberapa tugas dalam periode waktu yang tumpang tindih, tetapti tidak harus bersamaan.

Karakteristik :

1.Tugas dapat dijalankan secara bergantian (time-scrolling) pada satu processor.

2.Eksekusi terjadi secara bergantian sehingga seolah-olah berjalan bersamaan, namun sebenarnya hanya satu tugas yang 
dijalankan pada satu waktu pada satu processor.

3.Sering digunakan dalam sistem operasi untuk menangani banyak proses atau thread secara efisien.

**CONCURRENT AND PARALLEL**

Secara sederhana : Kombinasi dari concurrent dan paralel. Tugas dijalankan dalam periode waktu yang tumpang tindih dan beberapa dari tugas-tugas tersebut dijalankan secara bersamaan pada multiple processor.

Karakteristik :

1.Bebrapa tugas dijalankan secara bersamaan pada multiple processor.

2.Setiap processor dapat menangani multile tugas secara bersamaan secara concurrent (time-slicing).

3.Memanfaatkan keunggulan dari keduanya untuk meningkatkan efisiensi dan throughput.

**CONTOH**

PARALEL : menjalankan pemrosesan gambar dimana setiap bagian gambar diproses oleh core yang berbeda pada CPU multicore.

CONCURRENT : menjalankan dua program berbeda (misalnya, word dan google chrome) secara bergantian pada satu processor.

CONCURRENT AND PARALLEL : Menjalankan server web yang melayani banyak permintaan pengguna. Beberapa permintaan diproses secara paralel oleh prosesor berbeda, dan tiap processor menangani banyak permintaan secara concurrent dengan time-slicing.


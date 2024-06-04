NAMA : AHMAD FAIZ ASIFUDDIN

NRP : 3123521025

KELAS : IT-A


**`DINING PHILOSOPHERS PROBLEM AND READERS WRITERS PROBLEM`**

**DINING PHILOSOPHERS PROBLEM**
Dining philosophers Problem adalah masalah klasik dalam teori komputer yang menggambarkan situasi sinkronisasi dalam sistem operasi atau pemrograman paralel. Masalah ini diilustrasikan dengan lima filsuf yang duduk di meja bundar. Diantara setiap filsuf, ada satu garpu, dan setiap filsuf perlu dua garpu untuk makan. Namun, mereka tidak dapat makan bersamaan jika garpu yang mereka butuhkan sedang digunakan oleh filsuf lainnya.

**Permasalahan**
1.Deadlock : situasi dimana setiap filsuf memegang satu garpu dan menunggu garpu kedua, sehingga tidak ada filsuf yang bisa makan dan semua terjebak.
2.Starvation : Situasi dimana beberapa filsuf dapat makan terus-menerus sementara yang lainnya tidak pernah mendapatkan kesempatan untuk makan.
3.Concurrency : Mengelola akses ke garpu-garpu secara simultan oleh beberapa filsuf.

**Solusi dengan Sinkronisasi**

1. Resource Hierarchy Solution :
   Mengatur prioritas pada setiap garpu sehingga filsuf mengambil garpu dengan prioritas lebih rendah terlebih dahulu, kemudia mengambil garpu dengan prioritas lebih tinggi. Misalnya, setiap filsuf harus mengambil garpu dengan nomor lebih rendah terlebih dahulu dan garpu nomor lebih tinggi kedua.
2. Chandy/Misra Solution :
   Setiap garpu ditandai sebagai 'bersih' atau 'kotor', dan filsuf hanya bisa mengambil garpu jika garpu itu 'kotor'. Setelah makan, filsuf mencuci dan meletakkan kembali garpu sebagai 'bersih'. Ini memastikan bahwa tidak ada dua filsuf yang memegang dua garpu sekaligus dan mencegah deadlock.



**READERS WRITES PROBLEM**


Raders Writers Problem adalah masalah sinkronisasi yang muncul dalam sistem operasi atau pemrograman paralel ketika beberapa proses membutuhkan akses bersama ke suatu sumber daya, seperti sebuah database. Masalah ini fokus pada bagaimana mengelola akses pembacaan (read) dan penulisan (write) ke sumber daya tersebut sehingga tidak terjadi konflik yang dapat mengakibatkan data korup atau akses tidak efisien.

**Permasalahan**

1.Readers : Banyak proses yang hanya membaca data. Beberapa readers dapat membaca data secara bersamaan tanpa masalah.
2.Writers : Beberapa proses yang dapat menulis atau memodifikasi data. Penulisan data harus dilakukan secara eksklusif, artinya tidak boleh ada proses lain (baik reader maupun writer) yang mengakses data saat ada writer yang sedang menulis.

**Tiga Varian Masalah**

1.First Readers Writers Problem (Reader Priority): Prioritas diberikan kepada readers. Readers yang sudah mengakses data tidak akan diblokir oleh penulis, meskipun ada penulis yang menunggu.
2.Second Readers Writers Problem (Writer Priority): Prioritas diberikan kepada writers. Writers yang ingin menulis akan diberi prioritas untuk menghindari starvation (kelaparan) dari penulis.
3.Third Readers Writers Problem (No Priority): Tidak ada prioritas khusus antara readers dan writers. Pendekatan ini mencoba menyeimbangkan akses antara readers dan writers.

**Solusi dengan Sinkronisasi**
1. First Readers-Writers Problem (Reader Priority)

Reader Priority:


Tujuan: Memastikan bahwa pembaca (readers) dapat mengakses data segera dan tidak diblokir oleh penulis (writers) yang sedang 
menunggu.

Mekanisme:

Ketika seorang pembaca ingin membaca data, ia akan meningkatkan penghitung pembaca aktif (read_count).
Jika ini adalah pembaca pertama, pembaca akan mengunci akses ke penulis agar penulis tidak dapat menulis.
Pembaca lainnya dapat terus membaca tanpa halangan.
Ketika pembaca selesai membaca, penghitung pembaca aktif akan berkurang.
Jika tidak ada lagi pembaca yang aktif, akses untuk menulis akan dibuka kembali sehingga penulis dapat menulis.

Keuntungan: Pembaca memiliki prioritas lebih tinggi sehingga pembaca tidak perlu menunggu penulis.

Kerugian: Penulis dapat mengalami kelaparan (starvation) jika selalu ada pembaca yang ingin membaca.


2. Second Readers-Writers Problem (Writer Priority)

Writer Priority:

Tujuan: Memastikan bahwa penulis (writers) tidak mengalami kelaparan (starvation) dengan memberikan mereka prioritas untuk menulis data.


Mekanisme:

Ketika seorang penulis ingin menulis data, ia akan mengantri untuk mendapatkan akses.
Jika ada pembaca yang sedang membaca, penulis akan menunggu sampai semua pembaca selesai.
Setelah semua pembaca selesai, penulis akan mendapatkan akses eksklusif untuk menulis data.
Pembaca yang datang saat penulis sedang menunggu akan ditahan sampai penulis selesai menulis.

Keuntungan: Penulis memiliki prioritas lebih tinggi sehingga mereka tidak perlu menunggu terlalu lama.

Kerugian: Pembaca bisa mengalami penundaan jika banyak penulis yang ingin menulis.


3. Third Readers-Writers Problem (No Priority)
No Priority:

Tujuan: Menyeimbangkan akses antara pembaca (readers) dan penulis (writers) tanpa memberikan prioritas khusus kepada salah satu pihak.


Mekanisme:

Pembaca dan penulis akan mengantri secara bergantian untuk mendapatkan akses ke data.
Ketika seorang pembaca atau penulis tiba, mereka akan mengantri di antrian yang sama.
Pembaca yang tiba pertama akan mendapatkan akses dan bisa membaca data selama tidak ada penulis yang sedang menunggu.
Jika penulis tiba saat pembaca sedang membaca, penulis akan menunggu sampai semua pembaca selesai.
Setelah penulis selesai menulis, antrian akan di-check lagi untuk menentukan apakah pembaca atau penulis berikutnya yang akan mendapatkan akses.

Keuntungan: Akses lebih seimbang antara pembaca dan penulis, mengurangi risiko kelaparan untuk kedua pihak.

Kerugian: Tidak ada prioritas jelas sehingga beberapa skenario mungkin memerlukan penyesuaian tambahan untuk benar-benar menyeimbangkan beban kerja.


Kesimpulan

Reader Priority: Memastikan pembaca tidak diblokir oleh penulis, tetapi penulis bisa mengalami kelaparan.

Writer Priority: Memastikan penulis tidak mengalami kelaparan, tetapi pembaca bisa ditunda.

No Priority: Berusaha menyeimbangkan akses antara pembaca dan penulis, mengurangi risiko kelaparan untuk kedua pihak.

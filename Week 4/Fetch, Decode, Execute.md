**1.**Buatlah presentasi langkah demi langkah tentang siklus CPU (fetch,decode,execute) utk mengeksekusi sebuah program. Jelaskan juga peran dari Bahasa pemrograman dan compiler, begitu juga dengan peran dari Sistem Operaso. Gunakan referensi : Video referensi 1 dan Video referensi 2
JAWAB :

PRESENTASI LANGKAH DEMI LANGKAH TENTANG SIKLUS CPU (FETCH, DECODE, EXECUTE)

<img width="414" alt="cpu ram" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/534b59fb-3833-4d3a-9a14-0afc82381031">
• Fetch = mengambil instruksi
• Decode = memecahkan kode
• Execute = menjalankan instruksi

PROSES PENAMBAHAN ANGKA , SIKLUS BERULANG :
FETCH
 Programme counter = 0

 Ambil dari address 0 (LOAD 6)

 ‘LOAD 6’ masuk ke instruction register

DECODE

 Menerjemahkan kode ‘LOAD 6’

 LOAD = memuat , jadi memuat yang ada pada address 6 yang valuenya ‘1’

EXECUTE

 Jalankan LOAD, memuat adrress 6 yang valuenya ‘1’ ke dalam accumulator

 Accumulator = 1

FETCH

 Programme counter = 1

 Ambil dari address 1 (ADD 7)

 ‘ADD 7’ masuk ke instruction register

DECODE

 Menerjemahkan kode ‘ADD 7’

 ADD = menambah, jadi menambah yang ada pada address 7 yang valuenya ‘1’

EXECUTE

 Jalankan ADD , menambahkan address 7 yang valuenya ‘1’ ke dalam accumulator

 Accumulator = 2 ( 1+1 )

FETCH

 Programme counter = 2

 Ambil dari address 2 (STORE 6)

 ‘STORE 6’ masuk ke instruction register

DECODE

 Menerjemahkan kode ‘STORE 6’

 STORE = menyimpan, jadi menyimpan yang berada di accumulator ke dalam RAM di address 6

EXECUTE

 Jalankan STORE, menyimpan nilai accumulator ‘2’ ke dalam address 6 di dalam RAM

 Address 6 = ‘2’

FETCH

 Programme counter = 3

 Ambil dari address 3 (JUMP 1)

 ‘JUMP 1’ masuk ke instruction register

DECODE

 Menerjemahkan kode ‘JUMP 1’

 JUMP = lompat, jadi melompat kembali ke address 1

EXECUTE

 Jalankan JUMP, programme counter kembali ke nilai ‘ 1 ‘

Dari siklus tersebut akan terus diulang.

Bahasa pemrograman berperan sebagai instruksi-instruksi yang akan dieksekusi oleh CPU.
Compiler berperan sebagai penerjemah kode yang ditulis dalam bahasa pemrograman ke dalam bahasa mesin .
Sistem operasi berperan sebagai pengelola sumber daya(mengelola sumber daya komputer seperti CPU,memori dan perangkat input/output untuk memastikan bahwa setiap program mendapatkan akses yang diperlukan) , dan mengkoordinasi eksekusi(bertanggung jawab mengatur eksekusi program secara bersamaan atau bergantian agar semua program berjalan dengan lancar.
3. Jalankan VM Debian anda, lalu lakukan clone https://github.com/ferryastika/flops-iops. Compile dan eksekusi sesuai petunjuk. Sesuiakan jumlah thread dengan jumlah CPU yang ada di VM Debianmu. Catat hasilnya dan jelaskan arti dari hasil ekskusi. Lakukan sebanyak 5 kali. Bandingkan hasilnya anatar temanmu. Buat Plot perbandinnga hasil untuk masing-masing PC di tiap kelompokmu. Analisa hasil percobaan tadi dan beri kesimpulan tentang IOPS dan FLOPS.
JAWAB :

<img width="436" alt="a" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/48cb4b39-ddd6-4999-b20f-4c0e04b931a3">

$make

$make clean

$sudo make install

$sudo make uninstall

$ iops32 $(nproc)

$ iops64 $(nproc)

$ flops32 $(nproc)

$ flops64 $(nproc)

<img width="273" alt="b" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/8d894704-fcff-4671-862d-7af4581e2d6f">
<img width="479" alt="c" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/a44583b4-ab92-4b21-a72b-286d08a52369">
<img width="369" alt="d" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/3c9e920c-1732-4654-8883-4ff787429e31">

Penjelasan hasil flops-iops

Iops mengukur jumlah operasi input/output yang dapat dilakukan oleh sistem dalam satu detik

Flops mengukur jumlah operasi jumlah aritmatika floating-point yang dapat dilakukan oleh sistem dalam satu detik

64 menunjukkan bahwa pengukuran ini berlaku untuk sistem 64 bit

**4.**Apabila Debian VM mu masih belum terdapat packeage gcc, make dan git, lakukan instalasi dan catat setiap langkahnya!

<img width="382" alt="e" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/8330f97a-a74b-49ae-836a-cbe09aee862b">
<img width="478" alt="f" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/b610afac-9016-439d-894b-4c230e98c1f5">
<img width="485" alt="g" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/2c339413-7416-46ca-89b1-27d971b30ced">
<img width="484" alt="h" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/a105334a-f94c-4aee-a768-55ad900246a1">
<img width="469" alt="i" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/614821d6-cf9a-45ff-8c1f-fa70e3be9198">



NAMA : AHMAD FAIZ ASIFUDDIN

NRP : 3123521025

KELAS : IT - A

TUGAS PENDAHULUAN :

Apa yang dimaksud redirection?

redirection adalah perintah mengalihkan output dari sebuah perintah atau program ke tempat yang lain, misal ke perintah atau file lain.

Apa yang dimaksud pipeline?

pipeline adalah serangkaian perintah yang dihubungkan menggunakan operator pipa ( | ) , yang dimana dari perintah pertama menjadi input perintah kedua, dan seterusnya.

Apa yang dimaksud perintah di bawah ini : echo, cat, more, sort, grep, wc, cut, uniq

-echo = Digunakan untuk menampilkan string atau variabel ke terminal.

-cat = Digunakan untuk menampilkan isi dari sebuah file teks.

-more = Digunakan untuk menampilkan isi dari sebuah file teks satu layar penuh pada satu waktu.

-sort = Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter.

-grep = Digunakan untuk menyaring masukannya da n menampilkan baris-baris yang hanya mengandung pola yang ditentukan.

-wc = untuk menghitung jumlah baris, kata dan karakter dari baris-baris masukan yang diberikan kepadanya.

-cut = Digunakan untuk mengambil kolom tertentu dari baris-baris masukannya, yang ditentukan pada option –c.

-uniq = Digunakan untuk menghilangkan baris-baris berurutan yang mengalami duplikasi, biasanya digabungkan dalam pipeline dengan sort.

PERCOBAAN

Percobaan 1 : File Descriptor

1.Output ke layar (standar output), input dari system (kernel)

$ ps

<img width="504" alt="1" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/9b71dfef-2f81-4d84-8adf-fd38cd112fb2">

Output ke layar (standar output), input dari keyboard (standard input)

$ cat

hallo, apa khabar

hallo, apa khabar

exit dengan ^d

exit dengan ^d

[Ctrl-d]

<img width="506" alt="2" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/4c786183-a43c-4d30-a979-c70475fe5836">

Input nama direktori, output tidak ada (membuat direktori baru), bila terjadi error maka tampilan error pada layar (standard error)

$ mkdir mydir

$ mkdir mydir (Terdapat pesan error)

<img width="508" alt="3" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/a3efc134-2f6b-4063-bdb2-0182188ff03f">

Percobaan 2 : Pembelokan (redirection)

1.Pembelokan standar output

$ cat 1> myfile.txt

Ini adalah teks yang s

<img width="516" alt="4" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/2860b48d-1d90-4a55-9174-03e290009e57">

aya simpan ke file myfile.txt


2.Pembelokan standar input, yaitu input dibelokkan dari keyboard menjadi dari file

$ cat 0< myfile.txt

$ cat myfile.txt

<img width="510" alt="5" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/85c22638-f95a-44a4-bc3b-f5cbe5e1a668">

<img width="510" alt="6" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/14561dd8-6dea-4ccc-9c91-aab1da232b05">

3.Pembelokan standar error untuk disimpan di file

$ mkdir mydir (Terdapat pesan error)

$ mkdir mydir 2> myerror.txt

$ cat myerror.txt

<img width="515" alt="7" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/966203ee-ec51-48ea-ba48-b2b47ec54963">

<img width="229" alt="8" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/a2580b22-729a-435c-9162-6b4daf56648c">

<img width="510" alt="9" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/bed6b306-b0d6-4cf8-94e9-a5fe0f91ade5">



4.Notasi 2>&1 : pembelokan standar error (2>) adalah identik dengan file descriptor 1.

$ ls filebaru (Terdapat pesan error)

$ ls filebaru 2> out.txt

$ cat out.txt

$ ls filebaru 2> out.txt 2>&

$ cat out.txt

<img width="511" alt="10" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/4c882e0e-b6df-47c4-be3b-cf026f838cd2">


5.Notasi 1>&2 (atau >&2) : pembelokan standar output adalah sama dengan file descriptor 2 yaitu standar error

$ echo “mencoba menulis file” 1> baru

$ cat filebaru 2> baru 1>&

$ cat baru

<img width="510" alt="11" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/4600d111-122e-449e-8bf7-9ea2f172ff40">

6.Notasi >> (append)

$ echo “kata pertama” > surat

$ echo “kata kedua” >> surat

$ echo “kata ketiga” >> surat

$ cat surat

$ echo “kata keempat” > surat

$ cat surat

<img width="511" alt="12" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/0c312ed1-ea47-4f37-9ba7-466a24f1b7a5">

7.Notasi here document (<<++ .... ++) digunakan sebagai pembatas input dari keyboard. Perhatikan bahwa tanda pembatas dapat digantikan dengan tanda apa saja, namun harus sama dan tanda penutup harus diberikan pada awal baris

$ cat <<++

Hallo, apa kabar?

Baik-baik saja?

Ok!

++

$ cat <<%%%

Hallo, apa kabar?

Baik-baik saja?

Ok!

%%%

<img width="511" alt="13" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/2f0dc0be-9910-4f0c-9adc-7ba4d83b7f47">


8.Notasi – (input keyboard) adalah representan input dari keyboard. Artinya menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Perhatikan bahwa notasi “-“ berarti menyelipkan input dari keyboard

$ cat myfile.txt – surat

<img width="510" alt="14" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/8aa383e2-d651-402e-a691-a2561e1d31d3">

Percobaan 3 : Pipa (pipeline)

1.Operator pipa (|) digunakan untuk membuat eksekusi proses dengan melewati data langsung ke data lainnya.

$ who

$ who | sort

$ who | sort –r

$ who > tmp

$ sort tmp

$ rm tmp

$ ls –l /etc | more

$ ls –l /etc | sort | more

<img width="508" alt="15" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/3eb847ce-e246-4b90-906d-4eda793cb2a7">
<img width="508" alt="16" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/2832769f-3be1-4708-9fea-32cb46defc71">
<img width="506" alt="17" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/c35518eb-5aa1-42b2-bb2e-55b60a4406c7">

2.Untuk membelokkan standart output ke file, digunakan operator ">"

$ echo hello

$ echo hello > output

$ cat output

<img width="522" alt="18" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/962716a6-2133-4a48-a408-2d7b602be90d">

3.Untuk menambahkan output ke file digunakan operator ">>"

$ echo bye >> output

$ cat output

<img width="511" alt="19" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/d8a74264-53d9-4dee-bda7-309b55cfe3c6">

4.Untuk membelokkan standart input digunakan operator "<"

$ cat < output

<img width="498" alt="20" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/ad9e26a9-6c0c-428f-8a13-e196881d88cd">

5.Pembelokan standart input dan standart output dapat dikombinasikan tetapi tidak boleh menggunakan nama file yang sama sebagai standart input dan output.
$ cat < output > out

$ cat out

$ cat < output >> out

$ cat out

$ cat < output > output

$ cat output

$ cat < out >> out (Proses tidak berhenti)

[Ctrl-c]

$ cat out

<img width="513" alt="21" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/44bdb431-f967-47f7-afdd-8d0e6371682d">


Percobaan 4 : Filter


1.Pipa juga digunakan untuk mengkombinasikan utilitas sistem untuk membentuk fungsi yang lebih kompleks

$ w –h | grep

$ grep /etc/passwd

$ ls /etc | wc

$ ls /etc | wc –l

$ cat > kelas1.txt

Badu

Zulkifli

Yulizir

Yudi

Ade

[Ctrl-d]

$ cat > kelas2.txt

Budi

Gama

Asep

Muchlis

[Ctrl-d]

$ cat kelas1.txt kelas2.txt | sort

$ cat kelas1.txt kelas2.txt > kelas.txt

$ cat kelas.txt | sort | uniq

<img width="501" alt="22" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/14c825be-c06a-48bb-b6a1-d934f928ba46">
<img width="510" alt="23" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/7cf24792-eea8-4a4f-a7ff-e056de5117a7">
<img width="504" alt="24" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/eee5f44b-3e85-483d-9607-82cf56926dd4">



LATIHAN:

1.Lihat daftar secara lengkap pada direktori aktif, belokkan tampilan standard output ke file baru.

<img width="506" alt="25" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/651ef0ff-0b49-4de4-9e04-26e90b14fac0">



2.Lihat daftar secara lengkap pada direktori /etc/passwd, belokkan tampilan standard output ke file baru tanpa menghapus file baru sebelumnya.

<img width="508" alt="26" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/0ea87632-f22e-4a06-84bc-6b1e570dc451">



3.Urutkan file baru dengan cara membelokkan standard input.

<img width="508" alt="27" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/8b6d502c-b71a-4c46-b434-0fc775d02992">


4.Urutkan file baru dengan cara membelokkan standard input dan standard output ke file baru.urut.

<img width="502" alt="28" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/104561b6-ea61-484c-b338-12a14ef65bb0">


5.Buatlah direktori latihan 2 sebanyak 2 kali dan belokkan standard error ke file rmdirerror.txt.

<img width="504" alt="29" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/b07709de-12fe-431a-9882-8f2f68e312fe">


6.Urutkan kalimat berikut :

Jakarta

Bandung

Surabaya

Padang

Palembang

Lampung

Dengan menggunakan notasi here document (<@@@ ...@@@) . HINT

<img width="510" alt="30" src="https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/fbebe84e-fb72-451c-8cb9-ab0a9ef54c78">


7.Hitung jumlah baris, kata dan karakter dari file baru.urut dengan menggunakan filter dan tambahkan data tersebut ke file baru.

![Cuplikan layar 2024-04-30 093311](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/b154355a-eeb9-43b8-b7ba-7e0dbfd063b7)


8.Gunakan perintah di bawah ini dan perhatikan hasilnya.

$ cat > hello.txt

dog cat

cat duck

dog chicken

chicken duck

chicken cat

dog duck

[Ctrl-d]
$ cat hello.txt | sort | uniq

$ cat hello.txt | grep “dog” | grep –v “cat”

![Cuplikan layar 2024-04-30 093321](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/1f91a3d0-a861-4543-8b03-2a0c7c4d1887)

LAPORAN RESMI

KESIMPULAN :
Dari praktikum tersebut, kita belajar mengenai perintah-perintah linux seperti ‘ls’ ‘cat’ ‘echo’ ‘mkdir’ ‘sort’ ‘wc’ ‘grep’ ‘more’ . lalu operasi redirect ‘>’ ‘>>’ ‘<’. Kemudian pipeline dan juga filter . dengan pemahaman ini, kita dapat lebih terampil dalam menggunakan terminal linux untuk melakukan kegiatan yang kita butuhkan.

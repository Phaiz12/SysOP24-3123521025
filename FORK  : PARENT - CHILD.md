Fork : Parent - Child Process

Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)

Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git

Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c

![1](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/a3e7ab39-d275-439c-83d7-9df1882d0319)


sebelum menjalankan fork , lakukan instalasi compiler dengan cara mengetikkan apt install gcc g++.

perintah tersebut untuk menginstall compiler bahasa C dan bahasa C++


gcc adalah compiler untuk bahasa C

g++ adalah compiler untuk bahasa C++


![2](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/863d427c-9e36-4fb1-babc-f40b0e388dcb)

karena saya sudah menginstall compiler nya maka tampilan dari screenshot tersebut menampilkan gcc dan g++ sudah terinstall.


untuk menjalankan fork01.cpp , ketikkan perintah g++ fork01.cpp -o fork01.exe

perintah tersebut digunakan untuk mengkompilasi program C++ yang disebut dengan fork01.cpp menggunakan compiler g++ dan menghasilkan output fork01.exe

kemudian ketikkan ./fork01.exe untuk menjalankannya

![3](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/7253759c-8046-4299-959d-a57f3babf462)
![4](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/297e3d9c-6a29-4294-99a4-9f0c1b3ff867)


Analisa :

Output program ini menampilkan PID, PPID, dan UID. Setiap kali program mencetak informasi, program akan berhenti selama 3 detik sebelum mencetak informasi lagi. Program ini melakukaan perulangan sebanyak 3 kali



kemudian untuk menjalankan fork02.cpp dan juga fork03.cpp caranya seperti menjalankan fork01.cpp


![5](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/4a9e95aa-af7f-43dd-ae7c-07d3b89778ca)
![6](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/baae001c-ddba-4435-96fe-6e9972ad9a49)


Analisa:

Output dari program tersebut adalah menampilkan PID mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.


![7](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/e69f51bd-08fe-44d5-aaf5-c9cff64d9153)
![8](https://github.com/Phaiz12/SysOP24-3123521025/assets/160556584/9f8df241-6365-48a8-ac46-69adfae11c10)

Analisa:


Output dari program tersebut adalah melakukan proses forking secara berulang sebanyak 5 kali, yang menghasilakn proses baru dengan pesan yang mencatat PID masing-masing.

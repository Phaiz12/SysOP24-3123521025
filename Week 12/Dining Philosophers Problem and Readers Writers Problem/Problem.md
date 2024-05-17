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
1. Algoritma Djikstra (semaphore):
  Menggunakan semaphore untuk memastikan bahwa hanya satu filsuf yang dapat mengakses garpu pada satu waktu. Dua semaphore digunakan untuk setiap garpu


#include <pthread.h>

#include <semaphore.h>

#include <stdio.h>


#define N 5

#define THINKING 2

#define HUNGRY 1

#define EATING 0

#define LEFT (i + 4) % N

#define RIGHT (i + 1) % N


int state[N];

int phil[N] = {0, 1, 2, 3, 4};

sem_t mutex;

sem_t S[N];


void test(int i) {

    if (state[i] == HUNGRY && state[LEFT] != EATING && state[RIGHT] != EATING) {
    
        state[i] = EATING;
        
        sleep(2);
        
        printf("Philosopher %d takes fork %d and %d\n", i + 1, LEFT + 1, i + 1);
        
        printf("Philosopher %d is Eating\n", i + 1);
        
        sem_post(&S[i]);
    }
    
}




void take_fork(int i) {

    sem_wait(&mutex);
    
    state[i] = HUNGRY;
    
    printf("Philosopher %d is Hungry\n", i + 1);
    
    test(i);
    
    sem_post(&mutex);
    
    sem_wait(&S[i]);
    
    sleep(1);
}




void put_fork(int i) {

    sem_wait(&mutex);
    
    state[i] = THINKING;
    
    printf("Philosopher %d putting fork %d and %d down\n", i + 1, LEFT + 1, i + 1);
    
    printf("Philosopher %d is thinking\n", i + 1);
    
    test(LEFT);
    
    test(RIGHT);
    
    sem_post(&mutex);
}




void* philosopher(void* num) {

    while (1) {
    
        int* i = num;
        
        sleep(1);
        
        take_fork(*i);
        
        sleep(0);
        
        put_fork(*i);
    }
    
}




int main() {

    int i;
    
    pthread_t thread_id[N];
    
    sem_init(&mutex, 0, 1);
    
    for (i = 0; i < N; i++)
    
        sem_init(&S[i], 0, 0);
    for 
    (i = 0; i < N; i++) {
    
        pthread_create(&thread_id[i], NULL, philosopher, &phil[i]);
        
        printf("Philosopher %d is thinking\n", i + 1);
    }
    
    
    for (i = 0; i < N; i++)
    
        pthread_join(thread_id[i], NULL);
}


2. Resource Hierarchy Solution :
   Mengatur prioritas pada setiap garpu sehingga filsuf mengambil garpu dengan prioritas lebih rendah terlebih dahulu, kemudia mengambil garpu dengan prioritas lebih tinggi. Misalnya, setiap filsuf harus mengambil garpu dengan nomor lebih rendah terlebih dahulu dan garpu nomor lebih tinggi kedua.
3. Chandy/Misra Solution :
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

Berikut adalah contoh solusi untuk Readers Writers Problem dengan penekanan pada reader priority menggunakan semaphore dan mutex :


#include <pthread.h>

#include <semaphore.h>

#include <stdio.h>



sem_t mutex, writeblock;

int data = 0, rcount = 0;



void* reader(void* arg) {

    int f = ((int)arg);
    
    sem_wait(&mutex);
    
    rcount = rcount + 1;
    
    if (rcount == 1)
    
        sem_wait(&writeblock);
    sem_
    post(&mutex);
    
    printf("Reader %d: read data = %d\n", f, data);
    
    sleep(1);
    
    sem_wait(&mutex);
    
    rcount = rcount - 1;
    
    if (rcount == 0)
    
        sem_post(&writeblock);
    sem_
    post(&mutex);
}




void* writer(void* arg) {

    int f = ((int)arg);
    
    sem_wait(&writeblock);
    
    data++;
    
    printf("Writer %d: wrote data = %d\n", f, data);
    
    sleep(1);
    
    sem_post(&writeblock);
}




int main() {

    int i, b; 
    
    pthread_t rtid[5], wtid[5];
    
    sem_init(&mutex, 0, 1);
    
    sem_init(&writeblock, 0, 1);
    
    for (i = 0; i <= 2; i++) {
    
        pthread_create(&wtid[i], NULL, writer, (void*)i);
        
        pthread_create(&rtid[i], NULL, reader, (void*)i);
    }
    
    
    for (i = 0; i <= 2; i++) {
    
        pthread_join(wtid[i], NULL);
        
        pthread_join(rtid[i], NULL);
    }
    
    
    return 0;
}


Penjelasan Solusi

Semaphore:



mutex: Mengontrol akses ke variabel counter rcount.

writeblock: Mengontrol akses eksklusif untuk penulis.

Reader:



sem_wait(&mutex): Reader mendapatkan akses ke rcount dan menambahkannya.

Jika rcount adalah 1, maka ini adalah reader pertama yang masuk, dan reader pertama akan memblokir writer dengan sem_wait(&writeblock).

sem_post(&mutex): Reader selesai mengupdate rcount.

Reader membaca data.

sem_wait(&mutex): Reader mendapatkan kembali akses ke rcount dan menguranginya.

Jika rcount menjadi 0, maka ini adalah reader terakhir yang keluar, dan reader terakhir akan melepaskan blok pada writer dengan sem_post(&writeblock).

sem_post(&mutex): Reader selesai mengupdate rcount.


Writer:



sem_wait(&writeblock): Writer memblokir akses untuk reader dan writer lainnya.

Writer menulis data.

sem_post(&writeblock): Writer melepaskan blok sehingga reader dan writer lainnya dapat mengakses.

Solusi ini memastikan bahwa multiple readers dapat membaca data secara bersamaan, tetapi penulisan data hanya bisa dilakukan secara eksklusif oleh satu writer tanpa gangguan dari reader atau writer lain.






   

# SOAL dan JAWABAN GEMASTIK 2022
## SOAL PEMANASAN

### 1 Lipat Kertas Gambar

**Deskripsi Masalah :**
Inneo gemar mewarnai pada selembar kertas gambar berbentuk persegi Panjang. Namun di waktu
luangnya, terkadang tanpa disadari dia juga sering melipat kertas gambar yang sudah diwarnainya.
Dia selalu melipat kertas pada sisi yang lebih panjang, misalnya jika dia mempunyai kertas gambar
berukuran 120 × 80, maka dia akan melipat sisi dengan panjang 120, sehingga ukuran kertasnya
menjadi 60×80. Pada berikutnya dia kembali melipat kertas pada sisi dengan panjang 80, sehingga
sekarang ukuran kertasnya menjadi 60 × 40.

Jika diberikan sebuah kertas gambar dengan ukuran 𝑃 × 𝑄, tugas Anda adalah menentukan ukuran
kertas setelah dilakukan pelipatan sebanyak 𝑀 kali. Jika panjang sisi yang akan dilipat adalah
bilangan ganjil, maka hasil pelipatan adalah berupa pembulatan ke bawah. Misalnya jika ukuran
panjang yang akan dilipat adalah 11, maka setelah lipatan ukuran tersebut menjadi 5.
Format Masukan dan Keluaran

Baris pertama masukan adalah bilangan bulat 𝑁 yang menyatakan banyaknya kertas yang dimiliki
oleh Inneo. Kemudian 𝑁 baris berikutnya masing-masing terdiri dari tiga buah bilangan positif 𝑃,
𝑄, dan 𝑀. Nilai dari 𝑃, 𝑄, 𝑀, dan 𝑁 adalah bilangan bulat serta masing-masing bernilai antara 1
sampai 10 000. Untuk setiap ukuran kertas yang diberikan, program Anda harus mengeluarkan
ukuran kertas setelah dilakukan 𝑀 kali pelipatan dengan ketentuan ukuran yang lebih besar dicetak
terlebih dahulu.

Input :
```
3
120 80 3
3 2 50
3 7 2
```

Output: 
```
40 30
0 0
3 1
```

**Solution :**
```
#include <iostream>

using namespace std;

int main(){

    // Input N
    int N;
    cin>>N;
    cout<<endl;

    // Input P, Q , M
    int PQM[N][N];
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            cin>>PQM[i][j];
        }
           
    }

    // Ouput
    for (int x = 0; x < N; x++)
    {
        for (int y = 0; y < PQM[x][2]; y++)
        {
            if (PQM[x][2] > PQM[x][0]){
                PQM[x][0] = 0;
                PQM[x][1] = 0;
            }else if (PQM[x][0] > PQM[x][1]){
                PQM[x][0] = PQM[x][0] % 2 != 0 ? (PQM[x][0]-1) / 2 : PQM[x][0] / 2;
            }else if(PQM[x][1] > PQM[x][0]){
                PQM[x][1] = PQM[x][1] % 2 != 0 ? (PQM[x][1]-1) / 2 : PQM[x][1] / 2;
            }else if(PQM[x][0] == PQM[x][1]){
                PQM[x][0] = PQM[x][0] % 2 != 0 ? (PQM[x][0]-1) / 2 : PQM[x][0] / 2;
            }
        }

        if (PQM[x][0] > PQM[x][1]){
            cout<<PQM[x][0]<<" "<<PQM[x][1]<<endl;
        }else if(PQM[x][1] > PQM[x][0]){
            cout<<PQM[x][1]<<" "<<PQM[x][0]<<endl;
        }else if(PQM[x][0] == PQM[x][1]){
            cout<<PQM[x][0]<<" "<<PQM[x][1]<<endl;
        }
    }

    system("pause");
    return 0;

}
```

### 2 Bilangan Mandiri

**Deskripsi Masalah :**
Gema dan Astik sangat suka sekali bermain angka. Dalam permainan ini Gema akan memberikan
dua bilangan bulat 𝐴 dan 𝐵 kepada Astik untuk kemudian mencari banyaknya bilangan bulat antara
2 sampai 𝐵 yang merupakan Bilangan Mandiri. Bilangan Mandiri dari (𝐴, 𝐵) didefinisikan sebagai
bilangan bulat 𝑏𝑖 (2 ≤ 𝑏𝑖 ≤ 𝐵) yang bukan merupakan kelipatan dari salah satu atau lebih
bilangan bulat 𝑎𝑖 (2 ≤ 𝑎𝑖 ≤ 𝐴). Sebagai contoh, jika diketahui 𝐴 = 2 dan 𝐵 = 8, maka bilangan
bulat antara 2 sampai 8 yang merupakan kelipatan dari 2 adalah 2, 4, 6, dan 8. Sehingga yang
merupakan Bilangan Mandiri dari (2, 8) adalah 3, 5, dan 7 yang ada sebanyak 3.
Tugas Anda adalah membantu Astik dalam mencari Bilangan Mandiri dari rentang yang diberikan
oleh Gema.

**Format Masukan dan Keluaran :**
Baris pertama berisi sebuah bilangan bulat positif 𝑁 (1 ≤ 𝑁 ≤ 100) yang menunjukkan
banyaknya pasangan 𝐴 dan 𝐵 yang disebutkan oleh Gema. 𝑁 baris berikutnya masing-masing
berisi dua bilangan bulat 𝐴 dan 𝐵 yang dipisahkan oleh spasi dengan ketentuan 2 ≤ 𝐴 ≤ 130
dan 2 ≤ 𝐵 ≤ 1015. Untuk setiap pasangan (𝐴, 𝐵), keluarkan banyaknya Bilangan Mandiri

Input :
```
2
2 8
3 20
```
 
Output :
```
3
6
```

**Solution :**
```
#include <iostream>
 
using namespace std;

int main(){

    int N;
    cin>>N;
    cout<<endl;

    // Input AB
    int AB[N][N];
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j < N; j++)
        {
            cin>>AB[i][j];
        }
        
    }
    
    // Output
    int count = 0;
    for (int x = 0; x < N; x++)
    {
        for (int y = AB[x][0]; y <= AB[x][1]; y++)
        {
            if (x % 2 == 0)
            {
                if (y % AB[x][0] > 0)
                {
                    count += 1;
                    continue;
                }
            }else{
                if (y % AB[x][0] == 0 )
                {
                    count += 1;
                    continue;
                }
            }
        }
        cout<<count<<endl;
        count = 0;
    }


    system("pause");
    return 0;

}
```

### 3 Menghitung Banyaknya Produk Unik

**Deskripri Masalah**
Tahukah kamu siapa nama dari maskot GemasTIK XIII 2020? Nama dari maskot tersebut adalah
Galih. Pada tahun 2120, ketika para harimau di Kerajaan Dayeuhkolot memiliki kemampuan
membuat algoritma dan program, Galih, bersama dua saudaranya yang lain, yaitu Galuh dan
Gilang, membuat sebuah perusahaan perangkat lunak yang dinamai PT DayeuhCoder.

Setiap perangkat lunak yang dibuat oleh PT DayeuhCoder diberi nomor seri yang setiap digitnya
merupakan bilangan bulat antara 0 hingga 9 (inklusif). Nomor seri ini merepresentasikan suatu
bilangan bulat antara 0 hingga 1019 − 1 = 9 999 999 999 999 999 999 (inklusif, termasuk 0
dan 1019 − 1.

Galih, Galuh, dan Gilang memiliki kebiasaan yang tidak biasa pada perangkat lunak yang dibuat
perusahaan mereka. Beberapa perangkat lunak yang dirilis untuk pengguna bisa jadi memiliki
fitur tambahan yang unik. Pemberian fitur unik ini dijelaskan sebagai berikut. Galih, Galuh, dan
Gilang memilih tiga bilangan berbeda, sebutlah 𝐴, 𝐵, dan 𝐶 dengan sifat 2 ≤ 𝐴, 𝐵, 𝐶 ≤ 1019 −
1. Galih memberikan fitur tambahan unik pada produk yang nomor serinya habis dibagi 𝐴 saja
(namun tidak habis dibagi oleh 𝐵 maupun 𝐶), Galuh memberikan fitur tambahan unik pada
produk yang nomor serinya habis dibagi 𝐵 saja (namun tidak habis dibagi oleh 𝐴 maupun 𝐶),
dan Gilang memberikan fitur tambahan unik pada produk yang nomor serinya habis dibagi oleh
𝐶 saja (namun tidak habis dibagi oleh 𝐴 maupun 𝐵).

Divisi I Pemrograman – Babak Pemanasan
Suatu ketika, seekor harimau bernama Galang yang tinggal di kerajaan tetangga ingin
mengetahui ada berapa banyak maksimal produk dengan fitur tambahan unik untuk sekumpulan
perangkat lunak yang nomor serinya di antara 𝑀𝑖𝑛 dan 𝑀𝑎𝑥 (inklusif, termasuk 𝑀𝑖𝑛 dan 𝑀𝑎𝑥
itu sendiri, dengan 𝑀𝑖𝑛 ≤ 𝑀𝑎𝑥) apabila dia juga mengetahui bilangan berbeda 𝐴, 𝐵, dan 𝐶
yang dipilih oleh Galih, Galuh, dan Gilang. Tugas Anda adalah membantu Galang untuk
menyelesaikan masalah ini.

**Format Masukan dan Keluaran**
Masukan terdiri dua baris, baris pertama adalah dua bilangan 𝑀𝑖𝑛 dan 𝑀𝑎𝑥 dengan 0 ≤ 𝑀𝑖𝑛 ≤
𝑀𝑎𝑥 ≤ 1019 − 1 yang dipisahkan dengan spasi. Baris kedua adalah tiga bilangan berbeda 𝐴,
𝐵, dan 𝐶 dengan 2 ≤ 𝐴, 𝐵, 𝐶 ≤ 1019 − 1 dengan 𝐴 ≠ 𝐵 ≠ 𝐶 yang dipisahkan dengan spasi.
Keluaran adalah banyaknya produk dengan fitur tambahan unik berdasarkan nomor serinya yang
berada di antara 𝑀𝑖𝑛 dan 𝑀𝑎𝑥 (inklusif, termasuk 𝑀𝑖𝑛 dan 𝑀𝑎𝑥), sebagaimana dijelaskan pada
deskripsi soal.

Input :
```
1 20
9 4 6
```

Ouput :
```
6
```

**Penjelasan Masukan/Keluaran :**
Pada contoh masukan dan keluaran pertama, kita memiliki nilai 𝑀𝑖𝑛 = 1 dan 𝑀𝑎𝑥 = 20. Di
antara dua bilangan ini, ada 6 bilangan yang merepresentasikan nomor seri produk dengan fitur
tambahan unik sesuai dengan nilai 𝐴 = 9, 𝐵 = 4, dan 𝐶 = 6 sebagaimana kriteria pada soal,
yaitu: 4, 6, 8, 9, 16, dan 20.
Pada contoh masukan dan keluaran kedua, kita memiliki nilai 𝑀𝑖𝑛 =20 dan 𝑀𝑎𝑥 = 40. Di
antara dua bilangan ini, ada 4 bilangan yang merepresentasikan nomor seri produk dengan fitur
tambahan unik sesuai dengan nilai 𝐴 = 8, 𝐵 = 9, dan 𝐶 = 6 sebagaimana kriteria pada soal,
yaitu: 27, 30, 32, dan 40

**Solution :**
```
#include <iostream>

using namespace std;

int main(){

    // Input N & M 
    int N, M;
    cin>>N>>M;
    cout<<endl;

    // Input ABC
    int ABC[2];
    for (int i = 0; i < 2; i++){
        cin>>ABC[i];
    }

    // Output
    int count = 0;
    for (int x = N; x <= M; x++){
        if (x % ABC[0] == 0 && x % ABC[1] != 0 && x % ABC[2] != 0){
            count ++;
        }else if(x % ABC[1] == 0 && x % ABC[0] != 0 && x % ABC[2] != 0){
            count ++;
        }else if(x % ABC[2] == 0 && x % ABC[0] != 0 && x % ABC[1] != 0){
            count ++;
        }
    }
    cout<<count<<endl;

    system("pause");
    return 0;

}
```

# GIT
## Pengertian
Git adalah salah satu software version control yang menerapkan konsep DVCS (Distributed Version Control System).
## Cara Kerja
Git merekam seluruh perubahan file atau repository sebuah proyek, dalam bentuk **_Snapshot_** yang dilengkapi:
1. **Hash** : berupa kode SHA-1 yang otomatis generate ketika melakukan _commit_
2. **Parent** : Hash snapshot sebelumnya
3. **Author** : user yang melakukan perubahan
4. **Message** : infomasi mengenai apa saja perubahan yang dilakukan

***note**: Snapshot yang paling up to date disebut **HEAD***

## Arsitektur
Git menerapkan arsitektur _Three Tree_ yaitu terdiri dari:
1. **Working Directory** : tempat untuk merekam file yang sedang dirubah
2. **Staging Area** : tempat sementara untuk menyimpan dan mengumpulkan file yang telah dirubah dari _Working Directory_
3. **Repository** : tempat utama untuk menyimpan kumpulan file yang telah diubah dari _Staging Area_. File ditempat ini dianggap siap untuk dipertanggungjawabkan, karena history setiap perubahan didalam repository terekam disini.

## Instalasi
1. Download installernya di https://git-scm.com/downloads, pilih sesuai Operating System yang digunakan
2. Buka installernya dan di next-next aja untuk mendapatkan pengaturan default dari GIT
3. Buka _Start Menu_, kemudian ketik _'Git Bash'_, setelah itu buka
4. Atur username dan email: 
    ```
    git config --global user.name "<username yang terdaftar git>" && git config --global user.email "<email yang terdaftar di git>"
    ```
    Pastikan username dan email sudah masuk:
    ```
    git config --list --show-origin
    ```
5. Untuk keluar, tekan **Q** pada keyboard kemudian **Enter**

## Menghubungkan Proyek ke GIT
1. Buka **GIT Bash**
2. Arahkan GIT Bash ke directory dari proyek
3. Ketik ```git init```, kemudian **Enter**. Maka, GIT akan otomatis membuat Repository baru dari proyek, yaitu dengan cara membuat file **.git** di dalam folder proyek

## Kode-kode Perintah Lain dalam Git:
* ```git add <nama_file>.<format_file>``` : untuk memasukkan file dari Working Directory ke Staging Area
* ```git commit -m "<informasi mengenai perubahan apa saja yang dilakukan>"``` : untuk menyimpan seluruh file dari Staging Area ke Repository
* ```git status``` : untuk melihat perubahan dan aktivitas apa saja yang terjadi di dalam folder proyek
* 

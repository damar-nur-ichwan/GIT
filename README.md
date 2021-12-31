# GIT - MATERI DASAR
## Pengertian
Git adalah salah satu software version control yang menerapkan konsep DVCS (Distributed Version Control System).
## Cara Kerja
Git merekam seluruh perubahan file atau repository sebuah proyek, dalam bentuk **_Snapshot_** yang dilengkapi:
1. **Hash** : berupa kode SHA-1 yang otomatis generate ketika melakukan _commit_
2. **Parent** : Hash dari snapshot sebelumnya
3. **Author** : user yang melakukan perubahan
4. **Message** : infomasi mengenai apa saja perubahan yang dilakukan

***note**: Snapshot yang paling up to date disebut **HEAD***

## Arsitektur
Git menerapkan arsitektur _Three Tree_ yaitu terdiri dari:
1. **Working Directory** : tempat untuk merekam file yang sedang dirubah mencangkup CRUD (Create, Read, Update, Dalete)
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

## Mengabaikan Perubahan yang Terjadi pada File Tertentu
1. Buat file dengan nama **.gitignore**
2. Isi file tersebut dengan nama file atau folder directory yang ingin diabaikan setiap perubahannya. 
    Contoh:
    ```
    # Ignore folder log
    log/
    
    # Ignore semua file dengan extension .backup
    *.backup
    
    # Ignore file tertentu
    hasil_kompilasi.txt
    ```
## Membuat Alias
```
git config --global alias.<alias_yang_diinginkan> <perintah>
```
Contoh: 
1. 'commit' menjadi cukup diketik 'com'
    ```
    git config --global alias.com commit
    ```
2. 'log --oneline' menjadi cukup diketik 'logline'
    ```
    git config --global alian.logline "log --oneline"
    ```  


## Kode-kode Perintah Lain dalam Git:
* ```git add <nama_file>.<format_file>``` : untuk memasukkan file dari Working Directory ke Staging Area
* ```git add .``` : untuk memasukkan seluruh perubahan yg terdeteksi di Working Directory ke Staging Area
* ```git commit -m "<informasi mengenai perubahan apa saja yang dilakukan>"``` : untuk menyimpan seluruh file dari Staging Area ke Repository
* ```git status``` : untuk melihat perubahan dan aktivitas apa saja yang terjadi di dalam folder proyek
* ```git clean -f``` : untuk membatalkan semua perubahan dalam Working Directory
* ```git restore <nama_file>.<format_file>``` : untuk membatalkan perubahan pada file tertentu di Working Directory. Maka, file akan kembali ke semula (sebelum diubah)
* ```git restore --staged <nama_file>.<format_file>``` : untuk membatalkan perubahan pada file tertentu di Staged Area. Maka, perubahan file tersebut akan kembali ke Working Directory
* ```git log``` : melihat seluruh history commit pada Repository (Hash, Author, Message)
* ```git log --oneline``` : melihat seluruh history commit pada Repository secara sederhana (Hash, Message)
* ```git log --oneline --graph``` : melihat seluruh history commit pada Repository secara sederhana beserta history **Branch**-nya (Hash, Message, Grafik Branching)
* ```git blame <nama_file>.<format_file>``` : melihat history commit pada file tertentu beserta nama user yang melakukannya.
* ```git show <Hash>``` : melihat detail perubahan dari commit tertentu
* ```git show HEAD``` : melihat detail dari commit terakhir
* ```git diff <Hash_1> <Hash_2>``` : membandingkan antar commit
*note: Rename file adalah proses delete file, kemdian membuat file baru dengan nama baru dengan isi yang sama.
* GIT Reset : mengembalikan repository ke versi sebelumnya. Maka, versi sebelumnya yang dituju tersebut menjadi versi terupdate, sehingga versi setelahnya terhapus.
    - ```git reset --soft <Hash_yang_dituju>``` : memindahkan HEAD, namun tidak merubah Working Directory dan Staging Index
    - ```git reset --mixed <Hash_yang_dituju>``` : memindahkan HEAD dan mengubah Staging Index sama dengan Repository, namun tidak merubah Working Directory
    - ```git reset --hard <Hash_yang_dituju>``` : memindahkan HEAD dan mengubah Working Directory dan Staging Index seperti Repository
* ```git commit --amend -m "<informasi mengenai perubahan apa saja yang dilakukan>"``` : mengubah HEAD dengan cara menghapus HEAD sebelumnya secara ```--soft```, kemudian commit ulang
*note: Perbedaan RESET dan CHECKOUT adalah jika reset, commit setelahnya bener-bener di hapus, kalau checkout kita hanya melihat/mengambil isi dari commit tertentu, tanpa menghapus commit manapun
* DETACHED MODE: untuk melihat/mengambil file/repository pada commit tertentu
    ```git checkout <Hash>``` : melihat/mengambil semua file dari versi sebelumnya sesuai hash yang dimasukkan
    ```git checkout <Hash> -- <nama_file>.<format_file>``` : melihat file tertentu pada versi sebelumnya sesuai hash yang dimasukkan. Teknisnya, git akan meletakkan file tersebut ke dalam Staging Area.
* ```git checkout <nama_branch>``` : untuk mengembalikan lagi ke HEAD pada branch setelah melakukan 'DETACHED MODE'. Perintah ini juga digunakan untuk berpindah Branch
* ```git branch --show-current``` : menampilkan nama branch yang sedang digunakan
* ```git revert <Hash>``` : mengembalikan repository ke versi sebelumnya sesuai Hash yang dimasukkan, dengan cara menambah commit. Sehingga history commit tetap aman. Ini adalah keblikan dari reset.


# GIT BRANCE
* _Master/Main Branch_ : branch utama untuk meletakkan file-file yang sudah sesuai dengan tujuan
* Dengan adanya branche, maka pengerjaan proyek dalam repository berjalan sistematis, tanpa mengganggu master/main branch
* Sebuah branch paling tidak mewakili perubahan sebuah file
* Sebuah file direkomendasikan hanya dipegang 1 orang
## Penggunaan
* Saat ragu dalam menambah/mengubah fitur yang masih belum yakin implementasinya
* Saat mengerjakan proyek secara team
## Perintah
* ```git branch``` : menampilkan daftar branch yang ada
* ```git branch <nama_branch_yang_akan_dibuat>``` : membuat branch baru

# GIT FORK
## Fungsi
* Menduplikat Repository (beserta semua history-nya) dari akun orang lain ke akun pribadi. 
* Dengan Fork, maka Repository yang kita duplikat akan mengandung credit dari mana Repositori ini berasal.
* Perbedaan dengan _clone_, clone hanya menduplikat repository yang terakhir tanpa informasi history apapun dan creditnya

# GIT REMOTE
Remote bisa dikatakan sebagai pipa penghubung yang digunakan untuk mensingkronikasi antara repository cloning dengan repository centralnya. Jadi kalau repositori centralnya ada update, maka repository cloning akan terupdate juga
## Perintah
* ```git push``` : untuk mengupload perubahan ke repository asli
* ```git clone <path atau url>``` : untuk menduplikasi repository secara cloning
* ```git remote``` : melihat remote existing
* ```git remote -v``` : melihat remote existing beserta  methode apa saja yang bisa digunakan di masing-masing remote
* ```git remote add <nama remote> <path/url dari Central Repository> && git push -u <nama remote> <nama branch di local>``` : untuk menambahkan remote dan menyamakan antara Repository Local dengan Central Repository yang sebelumnya sudah di buat (kosong)

# GITHUB PAGES
Github Pages adalah tools yang digunakan sebagai hosting gratis, khusus untuk website sederhana
## Halaman Utama
* Pastikan file utama website bernama ```index.html```, supaya bisa langsung tampil
* Buat repository dengan nama ```<username github>.github.io```
* Begitu code program dari website yang dibuat sudah benar, serta disimpan dalam repository github, maka bisa langsung di akses melalui browser manapun ke ```<usename github>.github.io```
## Menambahkan Pages
1. Buka repository dari program website yang telah dibuat
2. Tekan **Settings**, lalu scroll down.
3. Pada area **Github Pages**, pilih branch yang mana yang mau ditambahkan ke Github Pages, dengan cara mengubah ```none``` pada bagian **source** ke branch yang diinginkan.
4. Website baru berhasil ditambahkan. Silakan akes melalui browser ke ```<usename github>.github.io/<nama repository yang sudah ditambahkan tadi>```

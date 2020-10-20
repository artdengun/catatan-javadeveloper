# CATATAN SEPUTAR GIT
### Konfigurasi Awal ###

git config --global user.name “Nama  User” <br>
git config --global user.email “Email  User” <br>
git config --list ( melihat list global user ) <br>

## Membuat Repository di git  ## 
git init  proyek01 ( membuat repository ) <br>
git init . ( akan membuat repositoy pada directory saat ini ) <br>
git init /var/www/html/proyekweb ( akan membuat git init pada proyek web ) <br> 
git status (  untuk melihat status repositorinya )  <br>
git commit -m “pesan” ( sudah melakukan revisi dan di simpan ke version control ) <br>

## MELIHAT HISTORY LOGS ## 
git log ( melihat catatan log perubah repository )  <br>
git log --oneline ( melihat catatan git yang lebih pendek ) <br>
git log 6779386 ( nomor revisi/commit)   ( melihat git menggunakan no commit ) <br>
git log index.html ( melihat log di file tertentu ) <br>
git log --author='denigunawan' ( melihat log dari author tertentu) <br>

## Melakukan perbandingan perubahan pada logs ## 
git diff 0995997 ( nomor revisi/ comit) ( melihat perubahan file yang dilakukan sesuai dengan no commit) <br>
git diff index.html ( melihat perubah file pada file tertentu ) <br>
git diff  <nomer comit> <nomer comit> ( melihat perbandingan antar revisi/commit ) <br>
git diff <nama cabang> <nama cabang> ( meilihat perbandingan antar cabang) <br>


## Untuk Membatalkan Revisi ## 

git checkout nama_file.html -> membatalkan kondisi file yang belum di staged dan di commit  ( hati hati bisa menghapus semua file yang sudah di ubah ) <br>
git reset nama_file.html -> membatalkan kondisi file yang sudah di staged ( git add )  ke kondisi modified.   <br>
git checkout HEAD~3 index.html -> kembali ke 3 commit sebelumnya <br>
git revert -n <nomer commit> -> membatalkan semua perubahan yang ada , mengembalikan semua file ke suatu commit <br>



## menggunakan  percabangan untuk mencegah konflik ## 
git branch fitur_register -> membuat cabang sendiri agar tidak konflik <br>
git branch -> untuk melihat cabang apa saja yang ada di repository <br>
git branch -d halaman_login -> menghapus branch <br>
git merger halaman_login -> mengabungan branch saat ini dengan halaman_login <br>


GIT PULL AND GIT FETCH

• Perintah git pull akan mengambil commit terbaru lalu otomatis menggabungkan (merge) dengan branch yang aktif.<br>
• Sedangkan git fetch akan mengambil commit saja. Perintah git fetch tidak akan langsung melakukan merge.<br>



Menambahkan dan Menghapus Remote
git remote <br>
git remote remove github ( menghapus repo git ) <br>
git remote add github git@github.com:petanikode/belajar-git.git  <br>
git remote -v untuk melihat remote apa saja yang sudah ditambahkan. <br>



Mengirim Revisi ke Remote Repository





Mengambil Revisi dari Remote Repository

1. git fetch [nama remote] [nama cabang]  <br>
2. git pull [nama remote] [nama cabang] <br>

Apa perbedaanya?<br>
Perintah git fetch hanya akan mengambil revisi (commit) saja dan tidak langsung melakukan penggabungan (merge) terhadap repository lokal.<br>
Sedangkan git pull akan mengambil revisi (commit) dan langsung melakukan penggabungan (merge) terhadap repository lokal.<br>

git branch -r -> melihat branch remote yang bekerja secara lokal <br>


Tiga Kelompok Kondisi FIle Git 

   1) modified artinya kondisi dimana revisi atau perubahan sudah dilakukan tetapi belum ditandai atau di simpan di version control. <br>
   2) staged artinya kondisi dimana revisi sudah ditandai, tetapi belum di simpan di version control. untuk mengubah kondisi file dari modified <br>
       ke staged gunakan perintah git add nama_file 
   3) commited  artinya kondisi dimana revisi sudah di simpan di version control , perintah untuk mengubah kondisi file dari staged ke commit <br>
      Menggunakan git commit -m “pesan anda”

**GIT CHECKOUT** <br>
Perintah git checkout seperti mesin waktu, kita bisa kembalikan kondisi file proyek seperti waktu yang dituju.

**GIT RESET**<br>
Perintah git reset sering disebut sebagai perintah berbahaya yang dapat menghancurkan catatan sejarah perubahan.<br>
   git reset --soft akan mengebalikan dengan kondisi file dalam keadaan staged<br>
   git reset --mixed akan mengebalikan dengan kondisi file dalam keadaan modified<br>
   git reset --hard akan mengebalikan dengan kondisi file dalam keadaan commited<br>
   
**GIT REVERT** <br>
Revert artinya mengembalikan. Perintah ini lebih aman daripada git reset, karena tidak akan menghapus catatan sejarah revisi.<br>

• Perintah git checkout mengembalikan file dalam kondisi sebelumnya, tapi bersifat sementara.<br>
• Perintah git reset, akan mengembalikan file ke kondisi sebelumnya, kemudian menghapus catatan sejarah commit beikutnya.<br>
• Perintah git revert mengembalikan file dengan tidak menghapus sejarah commit.<br>




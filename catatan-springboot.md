
# Arsitektur

   Class entitas adalah pendefinisian mapping class yang akan diubah ke dalam tabel pada database oleh framework hibernate, dalam penerapannya biasanya satu class merepresentasikan satu tabel.

   Class Dao ( data access object ) adalah bertujuan agar terpisah antara low level data atau operasi dengan bisnis proses pada apkikasi yang dibangun.

   Class Service Service merupakan sebuah class yang berfungsi untuk melakukan akses service atau API, nanti service ini dipanggil oleh sebuah controller.

   Class Controller Controller diibaratkan adalah pintu masuk request dari pengguna, dalam controller bertindak meneruskan request dari pengguna atau mengembalikan kembali ke pengguna.

   Class DTO (Data transfer Object) merupakan sebuah class untuk menampung hasil request dari sebuah service. Pada DTO tidak perlu membuat anotasi @Entity karena sifatnya hanya penampung,
# Springboot
 sebenarnya Spring Boot sendiri adalah salah satu framework Spring dengan less konfigurasi ketika akan membangun aplikasi Java. Sementara Spring sendiri feature core-nya yang terkenal adalah depedency injection, spring menyediakan resource berupa objek tanpa kita membuat secara manual <br>

 anotasi @SpringBootApplication yang artinya adalah aplikasi tersebut menggunakan Spring Boot, <br>

 anotasi @Component, fungsinya adalah agar Spring menandai class tersebut komponen Spring. <br>

 anotasi @Bean  fungsinya untuk  menginstance sebuah class <br>

 fungsi interface di atas hanya berisi method untuk menampilkan message atau pesan sederhana .  <br>

 setiap class yang mengimplement interface kelas tersebut harus di override untuk mengimplementasikan method <br>

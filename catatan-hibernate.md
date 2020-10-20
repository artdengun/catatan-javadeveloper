 # Hibernate

 Hibernate merupakan salah satu framework Object Relational Mapping(ORM) di Java <br>
 Hibernate menyediakan sebuah template untuk melakukan operasi-operasi data seperti insert, update, delete, dan select. <br>
 Object Relational Mapping(ORM) adalah sebuah paradigma untuk mengubah model database relational menjadi object oriented programming.
 Sehingga dengan demikian kita hanya fokus pada programmingnya bukan databasenya, selain itu ketika aplikasi kita akan migrasi ke database relational yang lain tidak berpengaruh terhadap aplikasi. Hanya sedikit konfigurasi yang perlu dilakukan yaitu dialect database dan driver class, tidak perlu compile ulang aplikasi <br>


Jika tidak disebutkan secara implisit maka akan menggunakan nilai default, misalkan name dengan default adalah nama attribut/filed dalam class entitas.

  @entity menandakan bahwa class Mahasiswa merupakan class entitas <br>
  @table menginformasikan pembuatan tabel di dalam database <br>
  @table terdapat property name digunakan untuk memberikan nama tabel di dalam database, jika property nama tidak disebutkan defaultnya adalah nama class yang digunakan yaitu Mahasiswa. <br>
  @Id adalah wajib ada untuk class entitas, jika dalam database nanti digunakan primary key. <br>
  @Column berfungsi sebagai pendefinisian kolom di dalam database, terdapat beberapa property seperti name, nullable, length, unique <br>
    name digunakan untuk memberikan nama kolom, <br>
    nullable artinya diizinkan boleh kosong atau tidak, <br>
    length adalah panjang field <br>
    unique artinya tidak boleh ada nilai yang sama. <br>
 @Size untuk memberikan contraint ukuran dari sebuah field. <br>
 @Min untuk membatasi nilai dari sebuah field atau attribut. <br>
 @Notnull untuk memberitahu bahwa field ini tidak boleh kosong <br>
 @Max untuk membatasi nilai max dari sebuahfiled atau  <br>

   • UNIQUE; nilainya harus berbeda untuk masing-masing row <br>
  • NOT NULL; nilainya tidak boleh kosong <br>
  • IMMUTABLE; ketika diinsert nilainya sudah tidak bisa diubah kembali <br>


 • create-only: akan dibuatkan tabel tanpa pengecekan tabel yang akan dibuat ada atau tidak <br>
  • drop: menghapus tabel yang ada <br>
  • create: akan dibuatkan tabel, jika sebelumnya ada tabelnya maka akan dilakukan drop <br>
  • create-drop: ketika Session Factory start up maka akan dibuatkan tabel, ketika Session Factory di-shutdown tabel tersebut akan dilakukan drop. Shutdown Session Factory yaitu dengan memanggil method close() dari object Session Factory. <br>
  • validate: akan memvalidasi stuktur tabel<br>
  • update: akan dibuatkan tabel jika tidak ada tabel, jika ada perubahan struktur tabel maka akan disesuaian. Seperti perintah alter jika menggunakan sql <br>


   **Hibernate Identifier <br>**

   **Assigned identifiers :** <br>
   untuk memberikan nilai pada identifier    jenis ini. aplikasi akan memberikan nilai pada kolom di database ketika menjalankan method save/persist.<br>

   **Generated identifiers:** <br>
   sesuai dengan namanya identifier ini dapat automatis memberikan nilai oleh  hibernate, digunakan anotasi @GeneratedValue setelah @Id <br>
   untuk menginformasikan bahwa nilai kolom/field dibuatkan secara automatis. <br>
  
   Dalam implementasi method pada unit test juga berkurang 1 baris yaitu yang sebelumnya terdapat p.setId(2L), ketika menggunakan @GeneratedValue  assign ke kolom/field identifier ditiadakan.  <br>
   Ketika dijalankan coba cek  tabel yang terbentuk pada database, hibernate juga akan membuat tabel  dengan nama hibernate_sequence untuk menyimpan nilai selanjutnya dari identifier. Bagaimana jika semua entitas menggunakan  identifer menggunakan @GeneratedValue semua?<br>
   Identifier model seperti ini bisa digunakan untuk entitas/tabel yang  menyimpan informasi transaksional dan nilainya tidak ditunjukkan kepada  seorang pengguna, hanya dikonsumi oleh sistem. <br>


   Generated identifiers sequence: <br>
   Sebenarnya model jenis ini adalah perbaikan atau solusi dari anotasi yang hanya @GeneratedValue,   <br>
    permasalahannya    adalah ketika ada banyak entitas yang menggunakan jenis tersebut maka nilai identifiernya akan sama karena mengacu pada tabel hibernate_sequence. <br>
   Dalam anotasi @GeneratedValue terdapat property strategy dan generator dan ditambakan anotasi @SequenceGenerator, sequenceName digunakan untuk memberikan nama sequence dan allocationSize ada nilai increment ketika method save/persist dijalankan. Misalkan dibuat nilai 10 berarti setiap data bertambah nilai primary key akan bertambah 10. Untuk unit test masih sama dengan yang sebelumnya, setelah menjalankan unit test coba dicek di database, seharusnya tabel sequence_pengembalian akan dibuatkan oleh hibernate. <br>


   Tabel identifiers generator: <br>

   Generate nilai automatis menggunakan tabel identifer akan membuat sebuah tabel di dalam database oleh hibernate yang berisi informasi nilai identifier dan juga nama tabelnya dari identifier tersebut. <br>

   Pada bagian strategy diganti menjadi GenerationType.TABLE dan juga pada generator menjadi "table-generator", kemudian anotasi yang digunakan setelah anotasi @GeneratedValue adalah @TableGenerator. Property yang dapat digunakan dalam @TableGenerator meliputi table untuk menentukan nama tabelnya, pkColumnName merupakan primary key dari kolom dari tabel tersebut, dan juga valueColumnName berfungsi sebagai nama kolom dari sebuah identifier. Kemudian jalankan unit testnya dan cek di database, seharusnya akan ada tabel baru yang terbentuk. <br>

   UUID Identifier generator : <br>

   Hibernate juga menyediakan mekanisme pembuatan identifier menggunakan UUID, UUID merupakan kepanjangan dari Universallly unique identifier digunakan untuk mengidentifikasi informasi dalam sistem komputer. <br>
   Yang perlu dilakukan adalah hanya menggunakan anotas @GeneratedValue dan mengubah variabel id menjadi sebuah object dari class UUID, ketika unit test dijalankan dan dicek di dalam database maka kolom id pada tabel Pengembalian akan menyimpan data dengan tipe data blob/binary dengan panjang 255. Kemudian kita akan tambahkan property pada anotasi @GeneratedValue seperti contoh di bawah ini <br>

   Pada class Pengembalian kita tambahkan property generator dengan nama "uuid2" pada anotasi @GenerateValue, kemudian ditambahkan @GenericGenerator(name = "uuid2", strategy = "uuid2") dan @Column(columnDefinition = "VARCHAR(40)") untuk menentukan definisi kolom pada tabel di database beserta tipe datanya. Silakan dijalankan unit test, selanjutnya cek di tabel Pengembalian seharusnya nilai id akan diisi oleh UUID dengan standadr IETF RFC 4122. Source code dapat didapatkan di sini. <br>


composite identifier: <br>


 **Hibernate Session Factory**<br>

 Session factory menyediakan object Session dan dibuat dari object Configuration, object Session sendiri digunakan untuk melakukan koneksi ke dalam database. Object tersebut mirip dengan interface Connection jika menggunakan jdbc, object Session Factory dibuat pada class HibernateUtil <br>

 Object Session Factory adalah object thread safe dan digunakan oleh semua thread yang terdapat dalam aplikasi, selain itu satu database biasanya memiliki 1 object Session Factory sehingga hanya dibuat satu instance dalam aplikasi. HibernateUtil juga menyediakan dao semua entitas, <br>





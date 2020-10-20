# CATATAN POSTGRESQL 

 1. masuk ke database <br>
    docker exec -it container_id bash <br>
    psql -U postgres  <br>

 2. melihat list database  <br>
    \l <br>
    \list <br>
  
 3.  konek ke database <br>
    \connect dbName <br>
    \c dbName <br>
    
 4. melihat semua table pada database yang kita gunakan saat ini <br>
    \dt <br>
    
5. lihat versi postgresql, masuk psql ketik <br>
    select version(); <br>

6.  lihat semua user <br>
     \du <br>

7. lihat kolom tabel <br>
     \d namatabel <br>

8. keluar  <br>
    \q <br>

9.  keluar dari hasil perintah psql <br>
   q <br>

10.rubah password user <br>
ALTER USER ininamausernya WITH PASSWORD 'inipasswordnya'; <br>

11. menghapus database  <br>
    DROP TABLE nama_table; <br>
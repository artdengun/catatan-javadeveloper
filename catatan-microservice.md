☑ Intro
   

                Untuk siapa materi ini :?
                
                   1) Web Developer
                   2) Backend Programmer
                   3) Software Architecture
                   4) DevOPS


                kenapa perlu belajar microservices ?
                 
                  1)  kekinian
                  2) Ekosistem pendukung 
                  3) banyak digunakan oleh Tech company
                  4) sudah jadi pengetahuan wajib untuk senior engginer 
    
 
☑ Arsitektur Monolith


            Apa itu arsitektur monolith?
            
               1) Single Deployment Unit 
               2) Dimana semua fitur dibuat dalam sebuah aplikasi besar 

                
                
    Mulailah dari aplikasi Monolith untuk pembuatan aplikasi . kalo resource dan kebutuhan sudah banyak , maka refactoring ke aplikasi micro
    
            Kelebihan Arsitektur Monolith:
            
               1.  mudah di develop
               2. mudah di deploy
               3. mudah di test
               4. mudah di scale 
                
                
             Masalah di Arsitektur Monolith:
                           
            1. Mengintimidasi developer yang baru bergabung 
            2. Scaling development dengan banyak developer agak menyulitkan 
            3. butuh kontrak panjang dengan teknologi yang digunakan( bahasa pemrograman,   database dan lain-lain)
            4. scaling pada bagian tertentu tidak bisa dilakukan 
            5. Running app Monolith sangat berat 

☑ Arsitektur Microservice

            Apa itu Arsitektur Microservice?        
            
            1. Aplikasi-aplikasi kecil yang saling bekerja sama.
            2. Fokus mengerjakan satu pekerjaan dengan baik
            3. Indepedent, dapat di deploy dan diubah tanpa tergantung dengan aplikasi lain.
            4. Setiap komponen pada sistem dibuat dalam service
            5. Komunikasi antar service biasanya melalui network-call
        
        
        
        
        Kelebihan Arsitektur Microservices: 
        
      1. Mudah dimengerti, karena relative kecil ukuran service nya 
      2. Lebih mudah didevelop, di maintaince, di test dan di deploy 
      3. Lebih mudah bergonta-ganti teknologi
      4. mudah di scale sesuai kebutuhan 
      5. bisa dikerjakan dalam tim-tim kecil 

        Masalah diArsitektur Microservices 
        
      1. Distributed System 
      2. Komunikasi antar service yang rawan error
      3. testing interaksi antar service lebih sulit 
        
        Seberapa Kecil Aplikasi Microservices? 
        
        1. Single responsbility
        2. Sekecil mungkin sehingga bisa dimengerti oleh satu orang
        3. Bisa dikerjakan sejumlah X developer   
            
                
        perbedaan monolith dan microservice: 
        
        Monolith : 
        
            1. simplicity
            2. Consistency
            3. Easy to Refactor

        Microservices: 

           1. Partial Development
           2. Availibility
           3. Multiple Platform 
           4. Easy to Scale  
      
☑ Database per Service

        
            setiap service(aplikasi) tidak mempunyai database terpusat , artinya setiap service
            mempunyai databasenya tersendiri . 
            
            
            Kenapa Harus Database per Service? 
            
            → Memastikan bahwa antar service tidak ketergantungan 
            → tiap service bisa  menggunakan aplikasi database sesuai dengan kebutuhan 
            → service tidak perlu tahu kompleksitas internal database service lain 
        
☑ Shared Database

        
        
        Kapan Harus Shared Database? 
               •  Ketika melakukan transisi dari aplikasi Monolith ke Microservices
               •  Ketika Bingung memecahkan data antar Service
               •  Ketika dikejar waktu, sehingga tidak ada waktu untuk bikin API
         
         
☑ NoSQL
    

            Apa itu NoSQL? 
               • NoSQL  bukanlah NO (TIDAK/BUKAN) SQL 
               • NoSQL singkatan dari Not Only SQL   -> bukan hanya sql yang bisa dijadikan database, akan ada alternatif lain selain SQL
    
            Jenis-Jenis NoSQL 
            
            • Document Oriented Database  -> 
            • Key-Value Database  -> basis memory / biasanya dilakukan untuk caching aplikasi
            • Column Families  Database (Column oriented) 
            • Graph Database -> digunakan untuk relasi komplek untuk sosial network 
            • Search Database -> spesialis untuk searching , sangat kenceng 
            • Time Series Database -> database berupa Timeseries
            • dan Lain lain . 

                        
            
            
            Kenapa Butuh Tahu NoSQL? Penting banget . 
            
            • Agar bisa disesuaikan dengan kebutuhan  
            • Bisa mencari alternatif cara mengolah data 
            • Mempercepat dalam proses penulisan atau pencarian 
      
☑ Remote Procedure Invocation

            
            
            
            
            
            
            
            
            
            
☑ Messaging

















☑ Type of Microservice














   





☑ Service Orchestration











☑ Service Choreograhy









    
    
    
    
    
    
☑ API Gateway

















☐ Authenticaton and Authorization


















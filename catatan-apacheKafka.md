Apache Kafka
Deni gunawan, 01/01/0001, Message broker Kafka
Apache Kafka merupakan platform terdistribusi untuk data streaming. Pada dasarnya, Apache Kafka merupakan sistem publish/subscribe messaging, dimana terdapat satu atau lebih sistem yang men-generate data untuk suatu topik tertentu secara real-time di Apache Kafka (disebut sebagai Producers). Kemudian, topik tersebut dapat dibaca oleh satu atau lebih sistem yang membutuhkan data-data dari topik tersebut secara real-time (disebut sebagai Consumers)

Belajar Apache Kafka

1. Tahap instalation

- download file kafka dalam bentuk binary,



    [https://downloads.apache.org/kafka/2.5.0/kafka_2.12-2.5.0.tgz](https://downloads.apache.org/kafka/2.5.0/kafka_2.12-2.5.0.tgz "https://downloads.apache.org/kafka/2.5.0/kafka_2.12-2.5.0.tgz")



- Masuk ke folder download kemudian extract file 	



    tar -xzf kafka_2.12-2.5.0.tgz

- masuk ke folder kafka kemudian edit config	

    $ code config

	

    - EDIT Zooker. properties 

		

        dataDir=data/zookeeper   <- Edit seperti ini

	

    -EDIT server.properties

        log.dirs=data/kafka	     <- Edit Seperti ini

	

    Kemudian simpan. 

 - Menjalankan zookeeper

	

    ./bin/zookeeper-server-start.sh config/zookeeper.properties

        defaut properti 'localhost:2181'

		

        *** Dalam Menjalankan Zookper akan muncul pesan error,

            Karna zookper mencari parentnya Kafka server, jika sudah 					

            jalan. maka pesan error akan hilang **

- Menjalankan Kafka server

	

    ./bin/kafka-server-start.sh config/server.properties

        default properti 'localhost:9092'

-  Tanda jika server kafka berjalan

    INFO \[KafkaServer id=0\] started (kafka.server.KafkaServer)
PEMBAHASAN

2. Bekerja dengan direktori

    -	Create Topic / table / file

		

            bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test

	

    -	melihat topic / table / file

	

            bin/kafka-topics.sh --list --bootstrap-server localhost:9092

    -	Send Message to Cosumers from producers

            bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic test

    - 	get/ hear Message From producers to Consumers File



            bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
PEMBAHASAN

3. BEKERJA DENGAN KAFKA

        <!!  SCRIPT PRODUCER  !!>

public static void main(String\[\] args) {

    Properties properties = new Properties();

            // ini data opsional bisa disesuaikan denga konfigurasi yang disesuaikan skenario

            //

         properties.put(ProducerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");  

            // file konfigurasi mengambil data dari ProducerConfig menggunakan perintah BOOTSTRAP_SERVERS_CONFIG

            // kemudian BOOTSTRAP_SERVERS_CONFIG ambil data dari server , disini kita menggunakan localhost:9092

            // untuk ambil data kita bisa sesuaikan dengan server yang kita gunakan	

          properties.put(ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG, StringSerializer.class.getName()); 

            // ini bersifat opsional

            // konversi string yang kita masukan ke binary data yang dimengerti oleh kafka

          properties.put(ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG, StringSerializer.class.getName()); 

            // 

            //       

            // serializer adalah menkonversi string yang kita masukan ke binary data 

          KafkaProducer<String, String> producer = new KafkaProducer<>(properties);

            // 1 key <String(1)	 		-> ini dari KEY_SERIALIZER_CLASS_CONFIG

            // 2 value , <String(2)>	-> ini VALUE_SERIALIZER_CLASS_CONFIG

    

        for(int i = 0; i< 20; i++){

             ProducerRecord<String, String> record = new ProducerRecord<>("CostumerService", " data ke 1 " + i);

             producer.send(record);

                // ini untuk mengirim data

         }

    producer.close();

    // close jika data sudah dikirim

}
PEMBAHASAN

    <!!  SCRIPT CONSUMER  !!>
public static voi ke 1 18

data ke 1 19

d main(String[] args) {

 Properties properties = new Properties();

    // ini data opsional bisa disesuaikan denga konfigurasi yang disesuaikan skenario ( harus sama dengan producer)

    //

     properties.setProperty(ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");

    // file konfigurasi mengambil ( penting  -> lokasi dari kafkanya)

     properties.setProperty(ConsumerConfig.GROUP_ID_CONFIG, "test");

    // menyebutkan group dara consumer dari grup idnya

     properties.setProperty(ConsumerConfig.ENABLE_AUTO_COMMIT_CONFIG, "true");

    // auto commit secara otomatis 

     properties.setProperty(ConsumerConfig.AUTO_COMMIT_INTERVAL_MS_CONFIG, "1000");

    // auto commitnya berapa lama 

     properties.setProperty(ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");

     properties.setProperty(ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");

    //  key dan value harus sama dengan producer String dan string

    //  jangan berbeda kan sangat berbahaya

    KafkaConsumer<String, String> consumer = new KafkaConsumer<>(properties);

 consumer.subscribe(Arrays.asList("CostumerService"));

 // cara mensubcribe, consum bisa mengsubscirbe beberapa topic yang berbeda

 // saran gunakan satu consumer untuk satu topik dan tidak lebih dan tidak terjadi erroy

 // erroy karna perbedaan key dan value yang berbeda antar cosumer dan producer

 while (true) {

     ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(1000)); // ( 1 detik)

    // poll itu artinya ambil, Duration of ofMillis -> kalo datanya tidak ada kita mau menunggu berapa lama 

    // kalo datanya tidak ada dia akan mereturn data kosong

     for (ConsumerRecord<String, String> record : records){

    // while (true) -> kita menggunakan method infinity loop pengulangan tanpa batas. 

            System.out.println("Received Number " + record.value());

         

        }

    }

}
PEMBAHASAN

                <!!  PARTITION REBELANCE !!>
PEMBAHASAN

Topik dikafka jika by default tidak isinya maka akan diisikan dengan default konfigurasi

sedangkan default konfugrasinya adalah satu, bisa di custom untuk konfigurasi lebih dari satu
# Module 9 - Software Architecture

## Refleksi 9 - Publisher

> How many data your publlsher program will send to the message broker in one
run?

Dalam satu kali eksekusi, program publisher mengirimkan 5 data ke message broker. Setiap data adalah instance dari `UserCreatedEventMessage` dengan nilai `user_id` dan `user_name` yang berbeda (Amir, Budi, Cica, Dira, dan Emir). Program publisher melakukan 5 kali panggilan metode `publish_event()` dari `CrosstownBus`, masing-masing mengirimkan satu pesan dengan routing key "user_created" ke RabbitMQ.

> The url of: `“amqp://guest:guest@localhost:5672”` is the same as in the subscriber
program, what does it mean?

URL `"amqp://guest:guest@localhost:5672"` yang sama antara program publisher dan subscriber menunjukkan bahwa keduanya terhubung ke server RabbitMQ yang sama. Ini memungkinkan komunikasi antara kedua program, dimana publisher mengirim pesan ke RabbitMQ dan subscriber menerima pesan tersebut dari server yang sama. Kesamaan URL ini menjamin bahwa pesan yang dikirim oleh publisher akan diterima oleh subscriber yang terhubung ke message broker yang sama.

> On your publisher Readme.md, edit it, and put your screen of your running RabbitMQ.

![Running RabbitMQ](./assets/rabbitmq.png)

> Try to capture your screen showing publisher and subscriber consoles, put it on your publisher repository
Readme.md, put some sentences describing what was happening.

![Publisher and Subscriber Consoles](./assets/console-pubsub.png)

# Ringkasan Komunikasi Publisher dan Subscriber

Pada gambar di atas, terlihat bahwa konsol publisher (bagian bawah) menunjukkan eksekusi program publisher yang berhasil dijalankan untuk mengirimkan pesan ke RabbitMQ. Sementara itu, konsol subscriber (bagian atas) menunjukkan 5 pesan `UserCreatedEventMessage` yang berhasil diterima dari RabbitMQ, dengan user_id "1" hingga "5" dan user_name mengikuti format "2306275084-{nama}" (dari "2306275084-Amir" hingga "2306275084-Emir"). Ini membuktikan komunikasi antara publisher dan subscriber berjalan dengan baik melalui message broker RabbitMQ.

> Edit your publisher readme.md again, capture your browser, and explain how the spike got to do
with running the publisher. Put it on readme.md.

![RabbitMQ Spike](./assets/rabbitmq-spike.png)

Pada gambar di atas, terlihat dua puncak (spike) pada grafik "Message rates" di dashboard RabbitMQ. Spike berwarna ungu ini mengindikasikan aktivitas pengiriman pesan dari program publisher ke RabbitMQ. Spike terjadi ketika program publisher dijalankan dan mengirimkan 5 pesan ke queue RabbitMQ (Saya menjalankan program publisher sebanyak 2 kali). Grafik ini membuktikan bahwa message broker berhasil menerima dan memproses pesan-pesan yang dikirim oleh publisher, yang kemudian dapat diakses oleh subscriber.

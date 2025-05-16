# Module 10 - Software Architecture

## Refleksi 10 - Publisher

> How many data your publlsher program will send to the message broker in one
run?

Dalam satu kali eksekusi, program publisher mengirimkan 5 data ke message broker. Setiap data adalah instance dari `UserCreatedEventMessage` dengan nilai `user_id` dan `user_name` yang berbeda (Amir, Budi, Cica, Dira, dan Emir). Program publisher melakukan 5 kali panggilan metode `publish_event()` dari `CrosstownBus`, masing-masing mengirimkan satu pesan dengan routing key "user_created" ke RabbitMQ.

> The url of: `“amqp://guest:guest@localhost:5672”` is the same as in the subscriber
program, what does it mean?

URL `"amqp://guest:guest@localhost:5672"` yang sama antara program publisher dan subscriber menunjukkan bahwa keduanya terhubung ke server RabbitMQ yang sama. Ini memungkinkan komunikasi antara kedua program, dimana publisher mengirim pesan ke RabbitMQ dan subscriber menerima pesan tersebut dari server yang sama. Kesamaan URL ini menjamin bahwa pesan yang dikirim oleh publisher akan diterima oleh subscriber yang terhubung ke message broker yang sama.

> On your publisher Readme.md, edit it, and put your screen of your running RabbitMQ.

![Running RabbitMQ](./assets/rabbitmq.png)


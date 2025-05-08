# Tutorial 9 Subscriber Reflection

<details>
<summary>What is amqp?</summary>

> AMQP adalah singkatan dari Advanced Message Queuing Protocol. AMQP adalah sebuah protokol standar untuk message queue yang memungkinkan aplikasi-aplikasi yang berbeda untuk saling mengirim dan menerima pesan secara reliable, bahkan jika aplikasi itu dibuat dengan bahasa pemrograman yang berbeda-beda atau berjalan di server yang berbeda. Biasanya AMQP digunakan dalam sistem asynchronous messaging untuk membangun aplikasi skala besar yang butuh komunikasi antar komponen tanpa harus selalu online secara bersamaan. Salah satu implementasi AMQP yang populer adalah RabbitMQ.

</details>

<details>
<summary>What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?</summary>

> Format itu adalah URL connection string untuk menghubungkan ke server AMQP, yaitu guest pertama adalah username dan guest kedua adalah password. Jadi ini artinya kita login ke server AMQP menggunakan username: guest dan password: guest. Dan localhost berarti kita menjalankan itu di lingkungan lokal.

</details>
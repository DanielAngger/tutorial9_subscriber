# Tutorial 9 Subscriber Reflection

<details>
<summary>What is amqp?</summary>

> AMQP adalah singkatan dari Advanced Message Queuing Protocol. AMQP adalah sebuah protokol standar untuk message queue yang memungkinkan aplikasi-aplikasi yang berbeda untuk saling mengirim dan menerima pesan secara reliable, bahkan jika aplikasi itu dibuat dengan bahasa pemrograman yang berbeda-beda atau berjalan di server yang berbeda. Biasanya AMQP digunakan dalam sistem asynchronous messaging untuk membangun aplikasi skala besar yang butuh komunikasi antar komponen tanpa harus selalu online secara bersamaan. Salah satu implementasi AMQP yang populer adalah RabbitMQ.

</details>

<details>
<summary>What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?</summary>

> Format itu adalah URL connection string untuk menghubungkan ke server AMQP, yaitu guest pertama adalah username dan guest kedua adalah password. Jadi ini artinya kita login ke server AMQP menggunakan username: guest dan password: guest. Dan localhost berarti kita menjalankan itu di lingkungan lokal.

</details>

<details>
<summary>Screen shot of simulation slow subscriber.</summary>

> ![Alt text](<Screenshot 2025-05-08 at 20.27.34.png>)

> Bisa dilihat, baris thread::sleep(ten_millis); menyuruh program pause selama ten_millis, yang isinya 1000 milidetik = 1 detik. Artinya, setiap kali subscriber menerima satu event dari publisher, dia pause 1 detik sebelum lanjut print pesan.

</details>

<details>
<summary>Screen shot of running at least three subscribers.</summary>

> ![Alt text](<Screenshot 2025-05-08 at 21.41.38.png>)
> ![Alt text](<Screenshot 2025-05-08 at 21.41.58.png>)

> Bisa dilihat, masing-masing subscriber mendapat pesan yang berbeda karena RabbitMQ memang load balancing antar subscriber yang bind ke queue yang sama. Jadi, 1 pesan yang dikirim publisher hanya diambil oleh 1 subscriber saja, tidak semuanya. Hal ini karena arsitektur RabbitMQ dengan queue itu seperti memiliki alur publisher -> mengirim pesan -> masuk ke queue. Kalau punya 3 subscriber yang listen ke queue yang sama (misal queue user_created), maka RabbitMQ akan distribusikan secara bergantian (round-robin) ke subscriber-subscriber itu. Jadi setiap pesan cuma dikasih ke 1 subscriber, bukan ke semuanya sekaligus.

</details>
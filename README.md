1. Perbedaan Unary, Server Streaming, dan Bi-Directional Streaming
Unary: Klien mengirim satu permintaan dan menerima satu balasan. Cocok untuk operasi langsung seperti autentikasi atau permintaan data tunggal.

Server Streaming: Klien mengirim satu permintaan, lalu server membalas dengan data yang dikirim secara bertahap. Umumnya digunakan untuk data besar atau proses yang butuh waktu.

Bi-Directional Streaming: Klien dan server dapat mengirim dan menerima data secara simultan. Ideal untuk aplikasi seperti obrolan langsung atau game real-time.

2. Pertimbangan Keamanan dalam gRPC Rust
Keamanan harus mencakup autentikasi, otorisasi, dan enkripsi. Ini menjamin komunikasi tetap aman dan hanya pengguna sah yang bisa mengakses layanan yang tersedia.

3. Tantangan pada Bi-Directional Streaming di Rust gRPC
Streaming dua arah memerlukan sinkronisasi yang cermat, termasuk dalam hal buffer dan penanganan error. Ini penting untuk memastikan interaksi tetap mulus, terutama dalam konteks aplikasi real-time.

4. Kelebihan & Kekurangan ReceiverStream
Kelebihan: Menyederhanakan implementasi aliran data asynchronous melalui channel.

Kekurangan: Berisiko menciptakan bottleneck dan tantangan skalabilitas jika tidak diatur dengan baik, terutama saat menerima data dalam volume tinggi.

5. Struktur Kode gRPC Rust untuk Reusabilitas
Disarankan membagi kode berdasarkan modul (seperti otentikasi, logika bisnis, dan definisi protobuf). Gunakan trait untuk membuat abstraksi layanan, serta pisahkan fungsi utilitas ke dalam file tersendiri agar mudah dikembangkan dan dikelola.

6. Tambahan untuk MyPaymentService
Untuk menangani skenario pembayaran yang lebih kompleks, integrasi dengan gateway pembayaran, validasi data, mekanisme retry, dan pencatatan transaksi untuk keperluan audit sangat diperlukan.

7. Dampak gRPC pada Arsitektur Sistem Terdistribusi
gRPC meningkatkan efisiensi komunikasi antar layanan dengan performa tinggi. Namun, integrasi dengan sistem non-gRPC seperti REST bisa memerlukan lapisan tambahan seperti API Gateway.

8. HTTP/2 vs HTTP/1.1/WebSocket
HTTP/2: Menawarkan koneksi paralel (multiplexing) dan kompresi header untuk efisiensi lebih tinggi.

WebSocket: Cocok untuk komunikasi dua arah berkelanjutan, namun dalam beberapa kasus kurang efisien dibanding HTTP/2.

9. Perbandingan REST vs gRPC Streaming
REST: Menggunakan pola permintaan dan tanggapan tunggal, cocok untuk komunikasi stateless.

gRPC Streaming: Memungkinkan pertukaran data secara kontinu dan responsif, membuatnya unggul dalam skenario real-time.

10. Implikasi Schema Protobuf vs JSON
Protobuf: Mengandalkan skema data yang kuat dan efisien dalam serialisasi.

JSON: Lebih fleksibel dan mudah dibaca manusia, namun kurang optimal dalam ukuran dan kecepatan transmisi dibanding Protobuf.
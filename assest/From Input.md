# Langkah 1: Siapkan Web Server
Pastikan web server lokal (seperti XAMPP atau Laragon) sudah dijalankan dan Apache aktif.

# Langkah 2: Buat Folder Proyek
Buat folder untuk proyek ini di dalam direktori root web server Anda.
Jika menggunakan XAMPP, buat folder di dalam C:\xampp\htdocs\.
Jika menggunakan Laragon, buat folder di dalam C:\laragon\www\.
Misalnya, beri nama folder tersebut Lab7_php_dasar.

# Langkah 3: Buat File Form Input (frominput.php)
Di dalam folder Lab7_php_dasar, buat file baru bernama frominput.php.

# Masukkan kode berikut ke dalam file frominput.php:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Input</title>
</head>
<body>
    <h2>Form Input</h2>
    <form action="frominput.php" method="get">
        <label for="name">Nama:</label>
        <input type="text" id="name" name="name" required>
        <button type="submit">Kirim</button>
    </form>

    <?php
    if (isset($_GET['name'])) {
        echo 'Selamat Datang ' . htmlspecialchars($_GET['name']);
    }
    ?>
</body>
</html>

# Penjelasan Kode
Form:
action="frominput.php": Menentukan bahwa form akan mengirim data kembali ke file yang sama (frominput.php).
method="get": Menggunakan metode GET untuk mengirim data, sehingga data akan ditampilkan di URL.
Input Field: Menggunakan input teks dengan name="name" agar data yang dimasukkan pengguna dapat diambil menggunakan $_GET['name'].
Button: Tombol Kirim untuk mengirimkan form.
PHP Code:

if (isset($_GET['name'])): Mengecek apakah parameter name sudah diatur di URL.
htmlspecialchars($_GET['name']): Menampilkan teks yang dimasukkan pengguna sambil mengamankan input dari karakter HTML khusus untuk mencegah XSS (Cross-Site Scripting).
Pesan selamat datang ditampilkan dengan menyertakan nama yang dimasukkan.

# Langkah 4: Mengakses Form di Browser

Buka browser dan akses file tersebut dengan URL:
http://localhost/Lab7_php_dasar/frominput.php

Isi nama di form, misalnya "Anita", lalu klik tombol Kirim.
Setelah mengirimkan form, URL akan berubah menjadi:

http://localhost/Lab7_php_dasar/frominput.php?name=Anita

Tampilan akan menampilkan pesan:
Selamat Datang Anita

# Cara Kerja Program
Saat Anda mengisi nama di form dan mengirimkannya, data dikirim melalui URL menggunakan metode GET.
PHP kemudian mengambil nilai name dari URL ($_GET['name']) dan menampilkannya dengan pesan "Selamat Datang [nama]".

# Hasil 
![Screenshot (245)](https://github.com/user-attachments/assets/c862996c-c91c-4871-a80a-4fd42da14992)

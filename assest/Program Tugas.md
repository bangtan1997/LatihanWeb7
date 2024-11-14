# Langkah 1: Siapkan Web Server
Pastikan web server lokal (misalnya XAMPP atau Laragon) sudah dijalankan.
Jika menggunakan XAMPP, aktifkan Apache melalui XAMPP Control Panel.
Jika menggunakan Laragon, pastikan server sudah berjalan.

# Langkah 2: Buat Folder Proyek
Buat folder untuk proyek Anda di dalam direktori root web server.
Jika menggunakan XAMPP, buat di dalam folder C:\xampp\htdocs\.
Jika menggunakan Laragon, buat di dalam folder C:\laragon\www\.
Misalnya, beri nama folder tersebut form_umur, sehingga path lengkapnya adalah C:\xampp\htdocs\form_umur atau C:\laragon\www\form_umur.

# Langkah 3: Buat File Form Input (form.php)
Di dalam folder form_umur, buat file baru bernama form.php.

# Tambahkan kode berikut ke dalam file form.php untuk membuat form input:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Input Data</title>
</head>
<body>
    <h2>Formulir Masukan</h2>
    <form action="process.php" method="post">
        <label for="name">Nama:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="dob">Tanggal Lahir:</label>
        <input type="date" id="dob" name="dob" required><br><br>

        <label for="job">Pekerjaan:</label>
        <select id="job" name="job" required>
            <option value="Programmer">Programmer</option>
            <option value="Designer">Designer</option>
            <option value="Manager">Manager</option>
        </select><br><br>

        <button type="submit">Kirim</button>
    </form>
</body>
</html>

# Penjelasan Form
Action: Form ini mengirimkan data ke file process.php dengan metode POST.
Input Fields:
name untuk nama (tipe teks).
dob untuk tanggal lahir (tipe date).
job untuk pekerjaan, dengan beberapa opsi (Programmer, Designer, Manager).
Button: Tombol "Kirim" untuk mengirim data ke file process.php.
Langkah 4: Buat File untuk Memproses Data (process.php)

# Buat file PHP baru bernama biodata.php di dalam folder yang sama (form_umur).
Tambahkan kode berikut ke dalam file process.php:

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $dob = $_POST['dob'];
    $job = $_POST['job'];

    // Menghitung umur berdasarkan tanggal lahir
    $dobDate = new DateTime($dob);
    $currentDate = new DateTime();
    $age = $currentDate->diff($dobDate)->y;

    // Menentukan gaji berdasarkan pekerjaan
    switch ($job) {
        case 'Programmer':
            $salary = 7000000;
            break;
        case 'Designer':
            $salary = 6000000;
            break;
        case 'Manager':
            $salary = 10000000;
            break;
        default:
            $salary = 0;
    }

    // Menampilkan hasil
    echo "<h2>Hasil Input:</h2>";
    echo "Nama: " . htmlspecialchars($name) . "<br>";
    echo "Umur: " . $age . " tahun<br>";
    echo "Pekerjaan: " . htmlspecialchars($job) . "<br>";
    echo "Gaji: Rp " . number_format($salary, 0, ',', '.') . "<br>";
} else {
    echo "Data tidak valid.";
}

# Penjelasan Kode process.php

Cek Metode Request: Kode memeriksa apakah metode pengiriman data adalah POST.
Mengambil Data dari Form: Mengambil data nama, tanggal lahir, dan pekerjaan dari $_POST.
Menghitung Umur:
Menggunakan kelas DateTime untuk menghitung umur berdasarkan tanggal lahir.
diff() digunakan untuk menghitung selisih tahun antara tanggal lahir dan tanggal saat ini.
Menentukan Gaji:
Menggunakan switch untuk menentukan gaji berdasarkan pekerjaan yang dipilih.
Menampilkan Hasil:
Menampilkan nama, umur, pekerjaan, dan gaji dengan format yang lebih rapi.
htmlspecialchars() digunakan untuk mengamankan input pengguna.
number_format() digunakan untuk format angka dalam gaji.

# Langkah 5: Mengakses Form di Browser
Buka browser dan akses form input dengan URL berikut:
arduino

http://localhost/form_umur/form.php
Isi nama, tanggal lahir, dan pilih pekerjaan, lalu klik tombol Kirim.
Setelah form dikirim, data akan diproses oleh process.php dan hasilnya akan ditampilkan.

# Contoh Hasil di Browser
Jika Anda mengisi:
Nama: Anita
Tanggal Lahir: 1990-05-15
Pekerjaan: Programmer

# Hasil 
![Screenshot (245)](https://github.com/user-attachments/assets/5a2a666e-921f-4676-9c04-ced6923783c1)

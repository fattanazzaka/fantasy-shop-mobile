# fantasy_shop

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Tugas 7
Widget Tree adalah representasi dari semua widget yang Anda gunakan untuk membangun tampilan (UI) di Flutter. Flutter membaca tree ini untuk menentukan apa yang harus digambar di layar.
Parent (Induk): Adalah widget yang berisi widget lain, seperti Column, Row, atau Container.
Child (Anak): Adalah widget yang terkandung di dalam widget induk, seperti Text atau Icon.

MyHomePage: Widget utama yang menampilkan halaman.
InfoCard: Widget kustom untuk menampilkan kartu info (NPM, Nama, Kelas).
ItemCard: Widget kustom untuk tombol-tombol menu di grid (All Products, dll.).
Scaffold: Kerangka utama halaman yang memberi Anda AppBar (bilah atas) dan body (konten).
Column: Menyusun elemen-elemen secara vertikal (dari atas ke bawah).
Row: Menyusun elemen-elemen (kartu info) secara horizontal (dari kiri ke kanan).
GridView: Menyusun tombol-tombol ItemCard Anda dalam sebuah grid 3 kolom.
Padding & SizedBox: Memberikan jarak dan spasi antar elemen.
Center: Menempatkan konten di tengah halaman.
Text: Menampilkan semua tulisan (judul, nama, nama tombol).
Icon: Menampilkan ikon-ikon di dalam ItemCard.
Card: Membuat tampilan kartu dengan bayangan (digunakan di InfoCard).
Container: "Kotak" serbaguna yang Anda gunakan untuk mengatur ukuran dan padding.
InkWell: Membuat ItemCard dapat diklik (onTap) dan memunculkan efek visual.
SnackBar: Pesan pop-up yang muncul dari bawah saat tombol ditekan

MaterialApp adalah widget level atas (root) yang menyediakan fungsionalitas dan styling dasar yang dibutuhkan oleh aplikasi yang mengikuti Material Design.
Widget ini digunakan sebagai root agar semua widget di dalam aplikasi seperti Scaffold dapat "mencari ke atas" dan mengakses informasi tema atau navigator ini.

StatelessWidget (Widget Statis)
Widget yang tidak memiliki status (state) internal. Tampilannya bersifat immutable (final) dan hanya bergantung pada konfigurasi yang diterimanya saat dibuat.
StatefulWidget (Widget Dinamis)
Widget yang memiliki status (state) internal yang bisa berubah selama runtime. Widget ini memiliki objek State terpisah untuk menyimpan data.

BuildContext adalah "alamat" atau referensi lokasi dari sebuah widget di dalam Widget Tree. Setiap widget mendapatkan BuildContext-nya sendiri saat proses build.
BuildContext sangat penting karena berfungsi sebagai "pegangan" bagi widget untuk berinteraksi dengan ancestor (leluhur) atau layanan di atasnya.

Hot Reload
Apa itu: Proses "menyuntikkan" kode baru ke dalam Dart Virtual Machine (VM) yang sedang berjalan dan langsung menggambar ulang UI (memanggil ulang metode build()). State aplikasi tetap terjaga. Data yang ada di variabel atau State tidak hilang. Digunakan 90% waktu saat mengembangkan UI. Sangat cepat (seringkali < 1 detik).
Hot Restart
Memuat ulang seluruh aplikasi dari awal, tetapi lebih cepat daripada menghentikan dan menjalankan ulang aplikasi (Cold Restart).State aplikasi hilang dan kembali ke nilai default-nya. Digunakan saat perubahan kode terlalu besar untuk Hot Reload, misalnya mengubah initState() atau mengubah struktur constructor. 
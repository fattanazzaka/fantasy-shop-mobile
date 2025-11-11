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

# Tugas 7: Penjelasan Konsep Flutter

## 1. Apa itu Widget Tree?

**Widget Tree** adalah representasi dari semua widget yang Anda gunakan untuk membangun tampilan (UI) di Flutter. Flutter membaca *tree* ini untuk menentukan apa yang harus digambar di layar.

* **Parent (Induk):** Adalah widget yang berisi widget lain, seperti `Column`, `Row`, atau `Container`.
* **Child (Anak):** Adalah widget yang terkandung di dalam widget induk, seperti `Text` atau `Icon`.

---

## 2. Widget yang Digunakan dalam Proyek


* **`MyHomePage`**: Widget utama yang menampilkan halaman.
* **`InfoCard`**: Widget kustom untuk menampilkan kartu info (NPM, Nama, Kelas).
* **`ItemCard`**: Widget kustom untuk tombol-tombol menu di grid (All Products, dll.).
* **`Scaffold`**: Kerangka utama halaman (menyediakan `AppBar` dan `body`).
* **`Column`**: Menyusun elemen-elemen secara vertikal (dari atas ke bawah).
* **`Row`**: Menyusun elemen-elemen (kartu info) secara horizontal (dari kiri ke kanan).
* **`GridView`**: Menyusun `ItemCard` dalam sebuah grid 3 kolom.
* **`Padding` & `SizedBox`**: Memberikan jarak dan spasi antar elemen.
* **`Center`**: Menempatkan konten di tengah halaman.
* **`Text`**: Menampilkan semua tulisan (judul, nama, nama tombol).
* **`Icon`**: Menampilkan ikon di dalam `ItemCard`.
* **`Card`**: Membuat tampilan kartu dengan bayangan (digunakan di `InfoCard`).
* **`Container`**: "Kotak" serbaguna untuk mengatur ukuran dan padding.
* **`InkWell`**: Membuat `ItemCard` dapat diklik (`onTap`) dan memunculkan efek visual.
* **`SnackBar`**: Pesan pop-up yang muncul dari bawah saat tombol ditekan.

---

## 3. Peran `MaterialApp`

**`MaterialApp`** adalah widget level atas (*root*) yang menyediakan fungsionalitas dan *styling* dasar yang dibutuhkan oleh aplikasi yang mengikuti Material Design.

Widget ini digunakan sebagai *root* agar semua widget di dalam aplikasi (seperti `Scaffold`) dapat "mencari ke atas" dan mengakses informasi tema (`ThemeData`) atau `Navigator` ini.

---

## 4. Perbedaan `StatelessWidget` dan `StatefulWidget`

* **`StatelessWidget` (Widget Statis)**
    Widget yang tidak memiliki status (*state*) internal. Tampilannya bersifat *immutable* (final) dan hanya bergantung pada konfigurasi yang diterimanya saat dibuat.

* **`StatefulWidget` (Widget Dinamis)**
    Widget yang memiliki status (*state*) internal yang bisa berubah selama *runtime*. Widget ini memiliki objek `State` terpisah untuk menyimpan data.

---

## 5. Apa itu `BuildContext`?

**`BuildContext`** adalah "alamat" atau referensi lokasi dari sebuah widget di dalam Widget Tree. Setiap widget mendapatkan `BuildContext`-nya sendiri saat proses `build`.

`BuildContext` sangat penting karena berfungsi sebagai "pegangan" bagi widget untuk berinteraksi dengan *ancestor* (leluhur) atau layanan di atasnya (misalnya untuk `Theme.of(context)` atau `Navigator.of(context)`).

---

## 6. Perbedaan `Hot Reload` dan `Hot Restart`

### Hot Reload

* **Apa itu:** Proses "menyuntikkan" kode baru ke dalam Dart Virtual Machine (VM) yang sedang berjalan dan langsung menggambar ulang UI (memanggil ulang metode `build()`).
* **State:** State aplikasi **tetap terjaga**. Data yang ada di variabel atau `State` tidak hilang.
* **Kapan Digunakan:** Digunakan 90% waktu saat mengembangkan UI. Sangat cepat (seringkali < 1 detik).

### Hot Restart

* **Apa itu:** Memuat ulang seluruh aplikasi dari awal, tetapi lebih cepat daripada menghentikan dan menjalankan ulang aplikasi (*Cold Restart*).
* **State:** State aplikasi **hilang** dan kembali ke nilai *default*-nya.
* **Kapan Digunakan:** Digunakan saat perubahan kode terlalu besar untuk Hot Reload, misalnya mengubah `initState()` atau mengubah struktur *constructor*.

## Tugas 8
### 1. Navigasi: `push()` vs. `pushReplacement()`

Pengelolaan alur halaman (navigasi) adalah inti dari aplikasi. Kami menggunakan dua metode utama dari `Navigator`:
* **`Navigator.push()`**
    * **Definisi:** Menumpuk page baru di atas tumpukan.
    * **Fungsi:** Halaman baru (misal Halaman B) "didorong" ke atas halaman saat ini (Halaman A). Halaman A **masih ada di bawahnya**. Pengguna bisa kembali ke Halaman A dengan menekan tombol *back*.
    * **Contoh Penggunaan:** Pindah dari **Daftar Produk** ke **Halaman Detail Produk**. Setelah selesai melihat, pengguna bisa kembali ke daftar produk.

* **`Navigator.pushReplacement()`**
    * **Definisi:** Mengganti page teratas dari tumpukan dengan page baru.
    * **Fungsi:** Halaman baru (Halaman B) "menggantikan" halaman saat ini (Halaman A). Halaman A **dihapus dari tumpukan**. Pengguna *tidak bisa* kembali ke Halaman A dengan tombol *back*.
    * **Contoh Penggunaan:** Pindah dari **Halaman Login** ke **Halaman Utama (Home)**. Ini penting agar pengguna tidak bisa kembali ke halaman Login setelah mereka berhasil masuk.

---

### 2. Struktur Halaman: `Scaffold`, `AppBar`, dan `Drawer`

Untuk menjaga konsistensi UI di seluruh aplikasi, kami memanfaatkan hierarki widget dasar dari Flutter:

* **`Scaffold`**: Berperan sebagai "kerangka" dasar untuk setiap halaman. Widget ini menyediakan "slot" standar untuk `appBar` (di atas), `body` (konten utama), dan `drawer` (menu samping).
* **`AppBar`**: Ditempatkan di dalam `Scaffold` untuk memastikan semua halaman punya *header* yang seragam. Ini menampilkan judul halaman dan warna *brand* yang konsisten.
* **`Drawer`**: Digunakan sebagai pusat navigasi utama (menu samping). Dengan menempatkannya di `Scaffold`, kami tidak perlu menduplikasi link menu (seperti "Home", "Kategori", "Profil") di setiap halaman.

---

### 3. Tata Letak (Layout) Form: `Padding`, `SingleChildScrollView`, dan `ListView`

Saat membuat form (seperti "Form Tambah Produk"), widget tata letak ini sangat krusial untuk fungsionalitas dan tampilan:

* **`Padding`**
    * **Kelebihan:** Memberi "ruang napas" pada elemen UI.
    * **Contoh Penggunaan:** Kami membungkus setiap `TextFormField` dengan `Padding` agar tidak menempel rapat ke tepi layar atau menempel satu sama lain. Ini membuat form terlihat rapi dan mudah dibaca.

* **`SingleChildScrollView`**
    * **Kelebihan:** Mencegah *error* "bottom overflow" saat keyboard muncul.
    * **Contoh Penggunaan:** Kami membungkus seluruh `Column` yang berisi *field-field* form dengan `SingleChildScrollView`. Ini memastikan pengguna tetap bisa *scroll* ke bawah untuk mengakses tombol "Save" meskipun keyboard menutupi sebagian layar.

* **`ListView`**
    * **Kelebihan:** Mirip dengan `SingleChildScrollView` tapi lebih dioptimalkan untuk daftar yang sangat panjang atau dinamis karena menggunakan *lazy loading*.
    * **Contoh Penggunaan:** Untuk form statis kami, `SingleChildScrollView` sudah cukup. Namun, jika form tersebut memungkinkan pengguna menambah *field* secara dinamis (misalnya menambah banyak ukuran produk), `ListView` adalah pilihan yang lebih baik.

---

### 4. Identitas Visual: `ThemeData`

Untuk memastikan aplikasi Football Shop memiliki identitas visual yang konsisten, kami **tidak melakukan *hard-code* warna** di setiap widget.

Sebagai gantinya, kami mendefinisikan skema warna, font, dan gaya tombol secara terpusat di dalam `ThemeData` pada widget `MaterialApp` (widget akar aplikasi).

Dengan cara ini:
1.  Semua widget (seperti `AppBar`, `ElevatedButton`, `Switch`) akan **otomatis** mengambil warna dari tema.
2.  Aplikasi dijamin konsisten.
3.  Jika di masa depan *brand* berganti warna, kami **cukup mengubahnya di satu tempat** (di `ThemeData`), dan seluruh tampilan aplikasi akan ikut berubah.
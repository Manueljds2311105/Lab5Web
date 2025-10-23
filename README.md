# 🧩 Praktikum 5 - JavaScript
**Mata Kuliah:** Pemrograman Web  
**Dosen Pengampu:** Agung Nugroho  
**Universitas:** Universitas Pelita Bangsa  

---

## 🎯 Tujuan Praktikum
1. Mahasiswa mampu memahami sintaks dasar JavaScript.  
2. Mahasiswa mampu memahami penggunaan JavaScript pada halaman web.  
3. Mahasiswa mampu membuat kode JavaScript sederhana.  
4. Mahasiswa mampu melakukan manipulasi elemen HTML dengan JavaScript.  

---

## 🧠 Dasar Teori

**JavaScript** adalah bahasa pemrograman yang digunakan untuk membuat halaman web menjadi interaktif dan dinamis.  
Kode JavaScript bisa ditulis di dalam tag `<script>` pada HTML atau di file eksternal dengan ekstensi `.js`.

JavaScript dapat digunakan untuk:
- Mengubah isi konten HTML.
- Mengubah gaya tampilan (CSS).
- Menampilkan pesan (`alert`, `prompt`, `confirm`).
- Melakukan perhitungan logika atau aritmatika.
- Melakukan validasi form dan interaksi dengan pengguna.

---

## ⚙️ Langkah-Langkah Praktikum

### 1️⃣ Persiapan
- Buat folder baru dengan nama **`lab5_javascript`**  
- Buat file baru dengan nama **`lab5_javascript.html`**  
- Jalankan menggunakan browser (misalnya Google Chrome).

---

### 2️⃣ Menampilkan Pesan & “Hello World”
Kode berikut menampilkan teks *Hello World* di halaman dan di konsol browser:

```html
<script>
  document.write("Hello World!<br>");
  console.log("Hello World");
  alert("Ini merupakan pesan untuk Anda");
</script>
```

📌 **Keterangan:**
- `document.write()` → menulis teks langsung ke halaman web.  
- `console.log()` → menulis pesan ke *console* developer browser (Inspect → Console).  
- `alert()` → menampilkan pesan popup ke pengguna.

---

### 3️⃣ Menggunakan `prompt()` dan `if-else`
Program berikut meminta input nama dan nilai dari pengguna, lalu menentukan status lulus atau tidak.

```html
var nama = prompt("Siapa nama Anda?", "Masukkan nama Anda");
document.write("Hai, " + nama + "<br>");

var nilai = prompt("Nilai (0-100): ", 0);
var hasil = (nilai >= 60) ? "Lulus" : "Tidak Lulus";
document.write("Hasil: " + hasil + "<br>");
```

📘 **Penjelasan:**
- `prompt()` digunakan untuk meminta input dari user.  
- `if-else` atau operator ternary (`? :`) digunakan untuk membuat keputusan logika.

---

### 4️⃣ Operasi Aritmatika
Menampilkan hasil dari berbagai operasi matematika dasar menggunakan fungsi:

```html
function operasi(val1, val2) {
  document.write("<h3>Operasi Aritmatika</h3>");
  document.write("Perkalian: " + (val1 * val2) + "<br>");
  document.write("Pembagian: " + (val1 / val2) + "<br>");
  document.write("Penjumlahan: " + (val1 + val2) + "<br>");
  document.write("Pengurangan: " + (val1 - val2) + "<br>");
  document.write("Modulus: " + (val1 % val2) + "<br>");
}
```

📌 Dipanggil menggunakan tombol:
```html
<input type="button" value="Hitung 9 dan 2" onclick="operasi(9,2)">
```

---

### 5️⃣ Form Tebak Bilangan (Genap / Ganjil)
Menentukan apakah angka yang diinput adalah bilangan genap atau ganjil.

```html
function test() {
  var val1 = document.kirim.T1.value;
  if (val1 % 2 == 0)
    document.kirim.T2.value = "Bilangan Genap";
  else
    document.kirim.T2.value = "Bilangan Ganjil";
}
```

Form input:
```html
<form method="POST" name="kirim">
  <p>BIL: <input type="text" name="T1" size="20"></p>
  MERUPAKAN BIL: <input type="text" name="T2" size="20">
  <p><input type="button" value="TEBAK" onclick="test()"></p>
</form>
```

---

### 6️⃣ Mengubah Warna Latar dan Warna Teks
Manipulasi elemen HTML dengan JavaScript:

```html
function ubahWarnaLB(warna) {
  document.bgColor = warna;
}
function ubahWarnaLD(warna) {
  document.fgColor = warna;
}
```

Tombol pengubah warna:
```html
<input type="button" value="Latar Hijau" onclick="ubahWarnaLB('GREEN')">
<input type="button" value="Teks Kuning" onclick="ubahWarnaLD('YELLOW')">
```

---

### 7️⃣ Daftar Menu Makanan (Checkbox dan Total Otomatis)
Program menghitung total harga berdasarkan checkbox yang dipilih.

```html
function hitung(ele) {
  var total = document.getElementById('total').value;
  total = (total ? parseInt(total) : 0);
  var harga = parseInt(ele.value);

  if (ele.checked) total += harga;
  else total -= harga;

  document.getElementById('total').value = total;
}
```

Contoh HTML:
```html
<label><input type="checkbox" value="15000" onclick="hitung(this);"> Nasi Goreng Rp.15.000</label><br>
<label><input type="checkbox" value="12000" onclick="hitung(this);"> Mie Goreng Rp.12.000</label><br>
<label><input type="checkbox" value="10000" onclick="hitung(this);"> Bubur Ayam Rp.10.000</label><br>
<strong>Total Bayar: Rp. <input id="total" type="text" readonly></strong>
```

---

### 8️⃣ Validasi Form
Form ini melakukan validasi pada input pengguna sebelum dikirim.

```html
function validasiForm() {
  var nama = document.getElementById("nama").value.trim();
  var email = document.getElementById("email").value.trim();
  var umur = document.getElementById("umur").value.trim();

  if (nama === "" || email === "" || umur === "") {
    alert("Semua kolom harus diisi!");
    return false;
  }

  var polaEmail = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
  if (!email.match(polaEmail)) {
    alert("Format email tidak valid!");
    return false;
  }

  if (isNaN(umur) || umur <= 0 || umur > 120) {
    alert("Umur tidak valid!");
    return false;
  }

  alert("Data berhasil dikirim!\nNama: " + nama + "\nEmail: " + email + "\nUmur: " + umur);
  return true;
}
```

Form HTML:
```html
<form onsubmit="return validasiForm()">
  <label>Nama:</label><br>
  <input type="text" id="nama"><br><br>

  <label>Email:</label><br>
  <input type="text" id="email"><br><br>

  <label>Umur:</label><br>
  <input type="text" id="umur"><br><br>

  <button type="submit">Kirim</button>
</form>
```

---

## 📸 Hasil Tampilan
1. Muncul pesan **alert** dan teks “Hello World”.  
2. Program meminta input nama dan nilai melalui `prompt()`.  
3. Operasi aritmatika tampil setelah klik tombol.  
4. Form menampilkan hasil bilangan genap atau ganjil.  
5. Tombol dapat mengubah warna latar dan teks.  
6. Daftar menu menghitung total harga otomatis.  
7. Form validasi memastikan data benar sebelum dikirim.

---

## 🧾 Laporan Praktikum
1. Buat repository baru di GitHub dengan nama **Lab5Web**.  
2. Upload file berikut:
   - `lab5_javascript.html`
   - `README.md`
3. Commit dengan pesan:  
   ```
   Menyelesaikan Praktikum 5 - JavaScript
   ```
4. Tambahkan screenshot hasil di README atau folder `/img`.  
5. Kirim URL repository ke e-learning Universitas Pelita Bangsa.

---

## ✅ Kesimpulan
Dari Praktikum 5 ini, mahasiswa dapat:
- Memahami penggunaan sintaks dasar JavaScript dalam HTML.  
- Menggunakan perintah `alert()`, `prompt()`, dan `document.write()`.  
- Menggunakan struktur logika `if-else` dan `switch`.  
- Melakukan manipulasi elemen HTML (DOM).  
- Membuat validasi form agar input data sesuai aturan.  
- Mengimplementasikan perhitungan dinamis dengan checkbox.

---

✍️ **Dibuat oleh:**  
**Nama:** _(Isi Nama Kamu)_  
**NIM:** _(Isi NIM Kamu)_  
**Kelas:** _(Isi Kelas Kamu)_

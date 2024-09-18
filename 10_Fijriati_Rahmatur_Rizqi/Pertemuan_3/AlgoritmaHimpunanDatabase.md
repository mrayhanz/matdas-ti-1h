## Konsep Himpunan dalam Database: Contoh Pencarian Mahasiswa

Sebagai seorang programmer, kita dapat memanfaatkan konsep himpunan dalam pengelolaan database. Sebagai contoh, bayangkan kita memiliki sebuah database yang berisi dua tabel utama: `mahasiswa` dan `matakuliah`.

**Mencari Mahasiswa yang Mengambil Dua Mata Kuliah**

Jika kita ingin mencari mahasiswa yang mengambil dua mata kuliah tertentu, kita dapat menggunakan konsep **himpunan irisan**.

**Notasi Himpunan:**

- **A ∩ B:** Ini adalah notasi matematika untuk menyatakan irisan dari dua himpunan A dan B. Dalam konteks kita, A bisa mewakili himpunan mahasiswa yang mengambil mata kuliah pertama, dan B mewakili himpunan mahasiswa yang mengambil mata kuliah kedua. Irisan dari A dan B akan menghasilkan himpunan mahasiswa yang terdapat di _kedua_ himpunan tersebut.

- **{mahasiswa | mahasiswa yang mengambil matkul A dan mahasiswa yang mengambil matkul B}:** Ini adalah cara lain untuk menjelaskan himpunan irisan tersebut dengan kata-kata, di mana garis tegak lurus (|) dibaca "sedemikian sehingga".

**Pseudocode:**

```
function irisan(himpunanA, himpunanB):
  hasil = himpunan kosong
  for setiap elemen in himpunanA:
    if elemen ada di himpunanB:
      tambahkan elemen ke hasil
  return hasil
```

**Implementasi dalam SQL:**

```sql
SELECT *
FROM mahasiswa
INNER JOIN mengambil ON mahasiswa.nim = mengambil.nim
WHERE mengambil.matkul = 'Matematika Dasar'
AND mengambil.matkul = 'Dasar Pemrograman';
```

**Penjelasan:**

- **INNER JOIN:** Digunakan untuk menggabungkan data dari dua tabel berdasarkan kolom yang sama (dalam kasus ini, `nim`).
- **WHERE:** Digunakan untuk menyaring data berdasarkan kondisi tertentu, yaitu mahasiswa yang mengambil baik mata kuliah Algoritma maupun Struktur Data.

**Konsep Himpunan Lainnya:**

Selain irisan, konsep himpunan lain yang sering digunakan dalam database antara lain:

- **Gabungan:** Menggabungkan semua elemen dari dua himpunan tanpa duplikasi.
- **Selisih:** Mengambil elemen yang ada di himpunan pertama tetapi tidak ada di himpunan kedua.
- **Komplemen:** Mengambil semua elemen yang tidak ada di himpunan tertentu.

**Kesimpulan:**

Konsep himpunan memberikan fondasi yang kuat untuk memahami dan memanipulasi data dalam database. Dengan memahami operasi-operasi himpunan, kita dapat melakukan berbagai macam query yang kompleks dan mendapatkan informasi yang kita butuhkan.

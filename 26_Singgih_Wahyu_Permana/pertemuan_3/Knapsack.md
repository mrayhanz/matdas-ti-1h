## Algoritma Knapsack dengan Dynamic Programming: Pendekatan Himpunan

### Pendahuluan

**Masalah Knapsack** adalah sebuah permasalahan optimasi klasik dalam ilmu komputer. Masalah ini berfokus pada pemilihan item dari sekumpulan item yang memiliki bobot dan nilai masing-masing, dengan tujuan memaksimalkan total nilai item yang dipilih tanpa melebihi kapasitas maksimum suatu wadah (knapsack).

**Dynamic Programming** adalah teknik pemecahan masalah dengan cara memecah masalah besar menjadi submasalah yang lebih kecil, kemudian menyimpan solusi submasalah tersebut untuk digunakan kembali dalam perhitungan solusi submasalah yang lebih besar. Teknik ini sangat efektif untuk masalah yang memiliki substruktur optimal, seperti masalah knapsack.

### Konsep Himpunan dalam Knapsack

Dalam konteks masalah knapsack, kita dapat memandang setiap item sebagai elemen dalam sebuah himpunan. Himpunan ini kemudian akan menjadi ruang sampel untuk kita pilih item mana saja yang akan dimasukkan ke dalam knapsack.

**Himpunan Bagian** memainkan peran penting dalam permasalahan ini. Setiap kombinasi item yang mungkin dapat kita pilih sebenarnya adalah sebuah himpunan bagian dari himpunan item keseluruhan. Dengan demikian, kita dapat menggunakan konsep himpunan bagian untuk mencari kombinasi item yang menghasilkan nilai total maksimum tanpa melebihi kapasitas knapsack.

### Pseudocode Algoritma Knapsack dengan Dynamic Programming

```
Fungsi knapsack(W, wt, val, n)
    # W: Kapasitas knapsack
    # wt: Array bobot item
    # val: Array nilai item
    # n: Jumlah item

    K[n+1][W+1]  // Buat tabel 2D untuk menyimpan hasil submasalah

    // Inisialisasi baris dan kolom pertama
    for i in range(n+1):
        for w in range(W+1):
            if i == 0 or w == 0:
                K[i][w] = 0

    // Isi tabel K menggunakan pendekatan bottom-up
    for i in range(1, n+1):
        for w in range(1, W+1):
            if wt[i-1] <= w:
                K[i][w] = max(val[i-1] + K[i-1][w-wt[i-1]],  K[i-1][w])
            else:
                K[i][w] = K[i-1][w]

    return K[n][W]   

```

### Penjelasan Cara Kerja

1.  **Tabel K:** Tabel dua dimensi `K` digunakan untuk menyimpan hasil submasalah. `K[i][w]` menyimpan nilai maksimum yang dapat dicapai dengan menggunakan i item pertama dan kapasitas knapsack sebesar w.
2.  **Inisialisasi:** Baris dan kolom pertama dari tabel K diinisialisasi dengan 0 karena jika tidak ada item atau kapasitas knapsack adalah 0, maka nilai maksimumnya adalah 0.
3.  **Pengisian Tabel:** Tabel K diisi secara bottom-up. Untuk setiap item i dan kapasitas w, kita memiliki dua pilihan:
    -   **Memasukkan item:** Jika bobot item ke-i kurang dari atau sama dengan kapasitas yang tersisa, maka kita hitung nilai maksimum yang diperoleh jika item ke-i dimasukkan ke dalam knapsack ditambah dengan nilai maksimum yang diperoleh dari submasalah sebelumnya (dengan kapasitas yang dikurangi bobot item ke-i).
    -   **Tidak memasukkan item:** Jika bobot item ke-i lebih besar dari kapasitas yang tersisa, maka kita hanya mempertimbangkan nilai maksimum yang diperoleh dari submasalah sebelumnya.
4.  **Nilai Optimal:** Nilai maksimum yang dapat dicapai dengan menggunakan semua item dan kapasitas knapsack W disimpan dalam `K[n][W]`.

### Kesimpulan

Algoritma knapsack dengan dynamic programming menawarkan solusi efisien untuk masalah optimasi pemilihan item. Dengan menggunakan konsep himpunan bagian, kita dapat memformulasikan masalah ini secara matematis dan menerapkan teknik dynamic programming untuk menemukan solusi optimal. Pendekatan ini sangat berguna dalam berbagai aplikasi, seperti perencanaan produksi, manajemen inventori, dan pemilihan portofolio investasi.
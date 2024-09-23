def algoritma_diffie_hellman():
    teks = """
    Algoritma Diffie-Hellman untuk Pertukaran Kunci:

    1. Inisialisasi Parameter:
       - Alice dan Bob sepakat pada bilangan prima p = 97 dan basis g = 5.

    2. Pemilihan Kunci Pribadi:
       - Alice memilih kunci pribadi x = 36.
       - Bob memilih kunci pribadi y = 58.

    3. Menghitung Kunci Publik:
       - Alice menghitung kunci publik X:
         X = g^x mod p = 5^36 mod 97 = 50
       - Bob menghitung kunci publik Y:
         Y = g^y mod p = 5^58 mod 97 = 44

    4. Pertukaran Kunci Publik:
       - Alice mengirimkan kunci publik X ke Bob.
       - Bob mengirimkan kunci publik Y ke Alice.

    5. Menghitung Kunci Rahasia Bersama:
       - Alice menghitung kunci rahasia K:
         K = Y^x mod p = 44^36 mod 97 = 16
       - Bob menghitung kunci rahasia K:
         K = X^y mod p = 50^58 mod 97 = 16

    6. Kunci Rahasia Bersama:
       - Kunci rahasia bersama yang dihasilkan oleh Alice dan Bob adalah K = 16.
       - Kunci ini dapat digunakan untuk enkripsi dan dekripsi pesan antara mereka.
    """
    print(teks)

# Menjalankan fungsi
if __name__ == "__main__":
    algoritma_diffie_hellman()
# Algoritma Diffie-Hellman

def power_mod(base, exponent, modulus):
    """Fungsi untuk menghitung (base^exponent) mod modulus dengan metode eksponensial cepat."""
    result = 1
    base = base % modulus
    while exponent > 0:
        if (exponent % 2) == 1:  # Jika exponent ganjil
            result = (result * base) % modulus
        exponent = exponent >> 1  # Membagi exponent dengan 2
        base = (base * base) % modulus
    return result

def diffie_hellman():
    # Inisialisasi parameter
    p = 97  # Bilangan prima
    g = 5   # Basis

    # Pemilihan kunci pribadi
    x = 36  # Kunci pribadi Fata 
    y = 58  # Kunci pribadi Rivan

    # Menghitung kunci publik
    X = power_mod(g, x, p)  # Kunci publik Fata
    Y = power_mod(g, y, p)  # Kunci publik Rivan

    print(f"Kunci Publik Fata (X): {X}")
    print(f"Kunci Publik Rivan (Y): {Y}")

    # Menghitung kunci rahasia bersama
    K_Alice = power_mod(Y, x, p)  # Kunci rahasia Fata
    K_Bob = power_mod(X, y, p)     # Kunci rahasia Rivan

    print(f"Kunci Rahasia Bersama Fata (K): {K_Alice}")
    print(f"Kunci Rahasia Bersama Rivan (K): {K_Bob}")

# Menjalankan fungsi
if __name__ == "__main__":
    diffie_hellman()
